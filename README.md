Repository to go along with the *The Four Types Of Prometheus Metrics* article
at [tomgregory.com](https://www.tomgregory.com).

It contains an application that has 4 controllers to simulate the 4
different types of Prometheus metric:

* Counter - hit [/hello](http://localhost:8080/hello) to increment the *request_count* counter
* Gauge - hit [/push](http://localhost:8080/push) to increment the *queue_size* gauge and [/pop](http://localhost:8080/pop) to decrement it
* Histogram - hit [/wait](http://localhost:8080/wait) to record the response time in the `request_duration` histogram
* Gauge - hit  [/waitSummary](http://localhost:8080/waitSummary) to record the response time in the `request_duration_summary` summary

All metrics are exposed at [/actuator/prometheus](http://localhost:8080/actuator/prometheus).

This repository also contains a configuration for Prometheus, which scrapes the application. 
Both the application and Prometheus are brought up using Docker Compose.

## Pre-requisites

* Docker (unless you just want to run the application)

## Running

`./gradlew build docker dockerComposeUp`

## Stopping

`docker-compose down`

(unfortunately the Palantir Gradle plugin doesn't provide a *dockerComposeDown* task
so we have to run the *docker-compose* command directly)

## Ref
- [Youtube](https://www.youtube.com/watch?v=nJMRmhbY5hY)
- [Blog](https://tomgregory.com/the-four-types-of-prometheus-metrics/)
- [Github](https://github.com/tkgregory/metric-types)