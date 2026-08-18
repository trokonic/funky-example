FROM maven:3.8.4-openjdk-17 AS build
WORKDIR /app
COPY pom.xml .




COPY src ./src
RUN mvn clean package -DskipTests

FROM eclipse-temurin:17-jre-noble
WORKDIR /app
COPY --from=build /app/target/demo-0.0.1-SNAPSHOT.jar .
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app/demo-0.0.1-SNAPSHOT.jar"]