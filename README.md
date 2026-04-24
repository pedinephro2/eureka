# Eureka — Service Discovery

Netflix Eureka server for the Nephro Platform. All microservices register themselves here on startup and use it to discover each other by name instead of hardcoded hostnames.

## Tech Stack

- Java 17, Spring Boot
- Spring Cloud Netflix Eureka Server

## Port

`8761`

## Dashboard

The Eureka web dashboard is available at `http://localhost:8761` and shows all registered service instances and their health status.

## How It Works

Each microservice includes the Eureka client dependency and sets:

```properties
eureka.client.serviceUrl.defaultZone=http://eureka:8761/eureka
```

On startup, the service registers its hostname and port. The gateway and other services resolve `lb://service-name` URIs through Eureka.

## Running Locally

```bash
mvn spring-boot:run
```

## Docker

```bash
docker build -t azizos07/eureka:latest .
docker run -p 8761:8761 azizos07/eureka:latest
```

## Health Check

```bash
curl http://localhost:8761/actuator/health
```
