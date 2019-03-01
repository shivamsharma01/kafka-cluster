docker-compose up -d --build

docker-compose ps

docker stop $(docker ps -q)

docker-compose exec XXX bash


docker-compose rm broker
docker-compose rm zookeeper
docker-compose rm connect

docker exec -it broker /bin/bash
cd usr/bin

kafka-console-consumer --topic streams-wordcount-output --from-beginning --bootstrap-server localhost:9092 --property print.key=true --property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer

kafka-console-producer --broker-list localhost:9092 --topic streams-plaintext-input

create topic
docker-compose exec zookeeper-1 bash /usr/bin/kafka-topics --create --zookeeper localhost:2181 --replication-factor 3 --partitions 9 --topic qrcode-dev

kafka-topics --list --zookeeper zookeeper:2181

kafka-topics --describe --topic Hello-Kafka --zookeeper localhost:2181
