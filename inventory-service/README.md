# Inventory Service


## Configuration

Create a file named `.env` at the root of this project with the following content:

```shell
SURREAL_URL=
SURREAL_DB=
SURREAL_NS=
SURREAL_USER=
SURREAL_PW=

KAFKA_BROKER=
KAFKA_TOPIC=
```

As an example with the local dev stack (cf: docker-compose.yaml), you can copy paste the following configuration:
```shell
SURREAL_URL=127.0.0.1:8000
SURREAL_DB=ecommerce
SURREAL_NS=foo
SURREAL_USER=root
SURREAL_PW=root

KAFKA_BROKER=localhost:9092
KAFKA_TOPIC=stock_update
```

Then initialize service database:
```shell
docker cp ./init.surql event-driven-rust-and-golang-surrealdb-1:/
docker exec -it event-driven-rust-and-golang-surrealdb-1 /surreal import --conn http://localhost:8000 --user root --pass root --ns foo --db ecommerce ./init.surql
```

