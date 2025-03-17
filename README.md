# 🐟 Spring Boot + 💳 PostgreSQL + 🚢 Docker Example

## 🌟 Project Overview
This is a simple Spring Boot REST API that connects to a PostgreSQL 📂 using Docker.
The API allows you to **➕ add**, **📈 view**, **🔄 update**, and **🗑️ delete** employees.

- Backend: Spring Boot (👷‍♂️ Java)
- Database: 💳 PostgreSQL
- ORM: Spring Data JPA + Hibernate
- Containerization: 🚢 Docker (for PostgreSQL)

---

## 🔧 Prerequisites

Make sure you have the following installed:

- ☕ Java 11+
- 📚 Maven 3.6+
- 🚢 Docker & Docker Compose
- 🔐 IntelliJ IDEA Ultimate (optional but recommended)

---

## 🚧 Set Up and Run

### 1. 👀 Start PostgreSQL using Docker

```bash
docker run --name postgresqldb -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres -e POSTGRES_DB=employeedb -p 5432:5432 -d postgres
```

- PostgreSQL running at: `localhost:5432`
- 📂 Database: `employeedb`
- 👤 Username: `postgres`
- 🔑 Password: `postgres`

### 2. 🔢 Configure `application.properties`

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/employeedb
spring.datasource.username=postgres
spring.datasource.password=postgres

spring.jpa.hibernate.ddl-auto=create
spring.jpa.show-sql=true
spring.jpa.generate-ddl=true
```

> 🔹 `ddl-auto=create` will auto-create tables every time. For production, use `update`.

### 3. 🏃‍♂️ Build and Run the Spring Boot App

```bash
mvn clean install
mvn spring-boot:run
```

or run `SpringPostgresDockerApplication.java` from IntelliJ IDEA.

---

## 🔗 API Endpoints

| 🌐 Method | 📄 Endpoint | 📈 Description |
|:------|:---------|:------------|
| POST 💌 | `/api/employees` | ➕ Add new employee |
| GET 💌 | `/api/employees` | 👁️ View all employees |
| GET 💌 | `/api/employees/{id}` | 👤 View by ID |
| PUT 💌 | `/api/employees/{id}` | 🔄 Update employee |
| DELETE 💌 | `/api/employees/{id}` | 🗑️ Delete employee |

### 🛋️ Example cURL Commands

**➕ Add Employee:**
```bash
curl -X POST http://localhost:8080/api/employees \
-H "Content-Type: application/json" \
-d '{"name": "John Doe"}'
```

**👁️ Get All Employees:**
```bash
curl http://localhost:8080/api/employees
```

**👤 Get Employee by ID:**
```bash
curl http://localhost:8080/api/employees/1
```

**🔄 Update Employee:**
```bash
curl -X PUT http://localhost:8080/api/employees/1 \
-H "Content-Type: application/json" \
-d '{"name": "Jane Doe"}'
```

**🗑️ Delete Employee:**
```bash
curl -X DELETE http://localhost:8080/api/employees/1
```

---

## 🌐 Access the Database Manually

Connect using TablePlus, DBeaver, or psql CLI:

| 🛋️ Parameter | 🔹 Value |
|:----------|:------|
| Host | localhost |
| Port | 5432 |
| Database | employeedb |
| User | postgres |
| Password | postgres |

---

## 💡 Notes

- 🚢 **Docker Tip:**
    - Stop container: `docker stop postgresqldb`
    - Start container: `docker start postgresqldb`
    - Remove container: `docker rm -f postgresqldb`

- ☕ **Spring Boot Tip:**
    - To preserve data, use `spring.jpa.hibernate.ddl-auto=update`.

- 🔐 **Security Tip:**
    - Never hardcode DB credentials. Use environment variables.

---


