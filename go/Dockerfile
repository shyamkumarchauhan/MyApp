# go/Dockerfile
FROM golang:1.17 as builder

WORKDIR /app

# Fetch dependencies.
COPY go.* .

RUN go mod tidy
RUN go build -o app

FROM gcr.io/distroless/base-debian10

WORKDIR /app

COPY --from=builder /app/app /app/app

CMD ["/app/app"]
