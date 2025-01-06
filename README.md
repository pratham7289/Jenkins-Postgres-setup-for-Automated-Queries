# Jenkins and PostgreSQL Setup for Automated Queries

## Objective

This repository contains the setup for integrating **Jenkins** with **PostgreSQL** to automate the execution of SQL queries. The setup allows Jenkins to execute SQL commands (e.g., create tables, insert data, update records) on a PostgreSQL database hosted on a separate server. This can be useful for continuous integration and testing scenarios that require database operations.

---

## Prerequisites

- **Two Servers**:  
  One server for Jenkins and another for PostgreSQL. Both servers should have network connectivity between them.

- **RHEL Server** or any RHEL-based system for both servers.

- **Java 11 or later** for Jenkins to run.

- **PostgreSQL** installed and configured on the PostgreSQL server.

---

## Steps to Set Up Jenkins and PostgreSQL

### 1. **Install Jenkins on the Jenkins Server**

- **Install Java**:  
  Jenkins requires Java to run. Install **Java 11** or later.

- **Add Jenkins Repository**:  
  Jenkins is not available by default in RHEL's YUM repositories, so we need to add the Jenkins repository.

- **Install Jenkins**:  
  Once the repository is added, you can install Jenkins via YUM.

- **Start Jenkins Service**:  
  After installation, start the Jenkins service and configure it to start automatically on system boot.

- **Allow Jenkins Port in Firewall**:  
  By default, Jenkins runs on port 8080. Open this port in the firewall.

- **Access Jenkins Web Interface**:  
  Open the Jenkins web interface on your browser and retrieve the initial admin password.

---

### 2. **Install PostgreSQL on the PostgreSQL Server**

- **Install PostgreSQL**:  
  Install PostgreSQL and its contrib packages on the PostgreSQL server.

- **Initialize PostgreSQL Database**:  
  After installation, initialize the PostgreSQL database.

- **Start PostgreSQL Service**:  
  Start the PostgreSQL service and enable it to start on boot.

- **Configure PostgreSQL for Remote Connections**:  
  If you need remote access to the PostgreSQL database, modify its `pg_hba.conf` configuration file to allow connections from the Jenkins server.

- **Secure PostgreSQL**:  
  Change the default `postgres` user password for better security.

- **Allow PostgreSQL Port in Firewall**:  
  Ensure that port 5432 is open on the firewall to allow connections from the Jenkins server.

---

### 3. **Create PostgreSQL Database and Table on PostgreSQL Server**

- **Login to PostgreSQL**:  
  Access the PostgreSQL shell on the PostgreSQL server to interact with the database.

- **Create a Database**:  
  Create a new database (e.g., `my_database`).

- **Create a Table**:  
  Within the database, create a table (e.g., `users`) to store data.

- **Insert Data into Table**:  
  Insert some sample data into the table for testing.

- **Verify Data**:  
  Query the table to ensure that the data has been inserted correctly.

---

### 4. **Jenkins Pipeline for PostgreSQL Queries**

- **Create a Jenkins Pipeline**:  
  On the Jenkins server, create a new pipeline job to execute SQL queries on the PostgreSQL database hosted on the PostgreSQL server.

- **Configure Remote Database Connection**:  
  In the Jenkins pipeline, use the PostgreSQL server's IP address and credentials to connect to the database. You will need to install the appropriate PostgreSQL JDBC driver and reference it in the pipeline script.

- **Use Jenkins Credentials**:  
  To securely store and use the PostgreSQL username and password, use Jenkins' credentials management system. Add the credentials to Jenkins and reference them in the pipeline.

- **Write SQL Queries**:  
  The pipeline should include steps to run SQL queries, such as creating a table, inserting data, or querying the database.

---

### 5. **Test the Jenkins Pipeline**

- **Run the Pipeline**:  
  After setting up the pipeline, run it to ensure that the SQL queries are executed correctly on the PostgreSQL server.

- **Check for Errors**:  
  Review the Jenkins job console output to check for any errors during execution.

- **Verify Database Changes**:  
  After the pipeline completes, verify that the changes (such as new tables or records) were applied to the PostgreSQL database.

---

## Conclusion

By following the steps in this setup, you will be able to automate database interactions via Jenkins, with PostgreSQL hosted on a separate server. This is particularly useful for automating database migrations, testing database changes, or continuously integrating database-related tasks with your application development pipeline.

