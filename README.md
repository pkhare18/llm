# llm


Running elasticsearch


docker run -it \
  --name elasticsearch \
  -p 9200:9200 \
  -p 9300:9300 \
  -e "discovery.type=single-node" \
-e "xpack.security.enabled=false" \
docker.elastic.co/elasticsearch/elasticsearch:8.4.3

ES was shutting down again and again and client index was giving error.
Below coonfig fixed it.

docker run -d --name elasticsearch \
-p 9200:9200 \
-p 9300:9300 \
-e "discovery.type=single-node" \
-e "xpack.security.enabled=false" \
-e "ES_JAVA_OPTS=-Xms1g -Xmx1g" \
docker.elastic.co/elasticsearch/elasticsearch:8.4.3