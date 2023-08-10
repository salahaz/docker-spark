FROM bde2020/spark-base:3.3.0-hadoop3.3

LABEL maintainer="Gezim Sejdiu <g.sejdiu@gmail.com>, Giannis Mouchakis <gmouchakis@gmail.com>"

COPY master.sh /

ENV SPARK_MASTER_PORT 7077
ENV SPARK_MASTER_WEBUI_PORT 8080
ENV SPARK_MASTER_LOG /spark/logs

EXPOSE 8080 7077 6066

ENV MAVEN_VERSION=3.9.3
ENV MAVEN_HOME=/usr/lib/mvn
ENV PATH=$MAVEN_HOME/bin:$PATH

RUN wget http://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz \
    && tar -zxvf apache-maven-$MAVEN_VERSION-bin.tar.gz \
    && rm apache-maven-$MAVEN_VERSION-bin.tar.gz \
    && mv apache-maven-$MAVEN_VERSION /usr/lib/mvn \
    && cd ~ \
    && wget https://github.com/vesoft-inc/nebula-exchange/releases/download/v3.5.0/nebula-exchange_spark_3.0-3.5.0.jar \
    && pip3 install pipenv 

CMD ["/bin/bash", "/master.sh"]
