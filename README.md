## Links

- [Kafka simulator](https://softwaremill.com/kafka-visualisation/) 
- [Rabbit MQ Simulator](http://tryrabbitmq.com/) 
- [Kafka Images for Arm](https://github.com/arm64-compat/confluent-platform
)

## Criar tópico
```bash
docker-compose exec kafka kafka-topics --bootstrap-server localhost:9092 --create --if-not-exists --topic topico-teste --partitions=3
```


## Consumir tópico

```bash
docker-compose exec schema-registry kafka-avro-console-consumer \
--bootstrap-server kafka:29092 \
--property schema.registry.url="http://localhost:8081" \
--topic topico-teste \
--property print.key=true \
--property print.value=true \
--value-deserializer io.confluent.kafka.serializers.KafkaAvroDeserializer \
--key-deserializer org.apache.kafka.common.serialization.StringDeserializer \
--consumer-property group.id=group-id-test
```