FROM ubuntu:14.04
WORKDIR /opt/jboss
RUN groupadd -r jboss -g 1200 && useradd -u 1200 -r -g jboss -m -d /opt/jboss -s /sbin/nologin -c "Jboss Application Server User" jboss
RUN apt-get update
RUN apt-get install openjdk-7-jdk -y
RUN apt-get install wget -y
RUN apt-get install unzip -y
ENV JAVA_HOME /usr/lib/jvm/java-7-openjdk-amd64
ENV WILDFLY_VERSION 8.2.0.Final
RUN cd $HOME && curl -O http://download.jboss.org/wildfly/$WILDFLY_VERSION/wildfly-$WILDFLY_VERSION.zip && unzip wildfly-$WILDFLY_VERSION.zip && mv $HOME/wildfly-$WILDFLY_VERSION $HOME/wildfly && rm wildfly-$WILDFLY_VERSION.zip
ENV JBOSS_HOME /opt/jboss/wildfly
EXPOSE 8080 9990
CMD ["/opt/jboss/wildfly/bin/standalone.sh", "-c", "standalone-full.xml", "-b", "0.0.0.0"]
