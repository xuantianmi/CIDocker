FROM openjdk:8-jdk-alpine
# 由于 Spring Boot 使用内置的Tomcat容器，Tomcat 默认使用/tmp作为工作目录。
# 此命令的效果是：在宿主机的/var/lib/docker目录下创建一个临时文件并把它链接到容器中的/tmp目录
VOLUME /tmp
# 拷贝文件并且重命名
ADD spring-boot-docker-1.0.jar app.jar
# 为了缩短 Tomcat 的启动时间，添加java.security.egd的系统属性指向/dev/urandom
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]


# mvn package docker:build
# 对应pom.xml中的docker-maven-plugin配置, 及application.properties
# docker run -d --name cidocker -p 8080:8080 -t phoenix/spring-boot-docker