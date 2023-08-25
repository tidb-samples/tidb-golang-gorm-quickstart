# How to Connect to TiDB Using GORM

[![Go](https://github.com/tidb-samples/tidb-golang-gorm-quickstart/actions/workflows/go.yml/badge.svg)](https://github.com/tidb-samples/tidb-golang-gorm-quickstart/actions/workflows/go.yml)

English | [中文](/README-zh.md)

This is an example project by PingCAP for connecting to TiDB using the GORM.

> TiDB is a MySQL-compatible database. [GORM](https://gorm.io/index.html) is a popular open-source Golang ORM framework, and GORM supports TiDB's features like `AUTO_RANDOM`. TiDB is also the [default supported database](https://gorm.io/zh_CN/docs/connecting_to_the_database.html#TiDB) for GORM.

## Prerequisites

- Recommended [Golang](https://go.dev/) version is **1.20** or above.
- [Git](https://git-scm.com/downloads).
- TiDB cluster. If you don't have a TiDB cluster yet, you can create one using the following methods:
  - (Recommended) Refer to [Create TiDB Serverless Cluster](https://docs.pingcap.com/tidbcloud/dev-guide-build-cluster-in-cloud) to create your own TiDB Cloud cluster.
  - Refer to [Deploy a Local Testing TiDB Cluster](https://docs.pingcap.com/tidb/stable/quick-start-with-tidb#deploy-a-local-testing-cluster) or [Deploy a Production TiDB Cluster](https://docs.pingcap.com/tidb/stable/production-deployment-using-tiup) to create a local cluster.

## Getting Started

### 1. Clone the Example Code Repository to Your Local Machine

```shell
git clone https://github.com/tidb-samples/tidb-golang-gorm-quickstart.git
cd tidb-golang-gorm-quickstart
```

### 2. Configure Connection Information

<details open>
<summary><b>(Option 1) TiDB Serverless</b></summary>

1. In the TiDB Cloud console, open the [Clusters](https://tidbcloud.com/console/clusters) page, select your TiDB Serverless cluster, go to the **Overview** page, and click the **Connect** button in the upper right corner.
2. Ensure that the configuration in the window matches your runtime environment.
    - **Endpoint Type** is **Public**
    - **Connect With** is **General**
    - Operating System matches your runtime environment
    > If you are running in Windows Subsystem for Linux (WSL), switch to the corresponding Linux distribution.
3. Click **Generate password** to generate a password.
    > If you have generated a password before, you can use the original password or click **Reset Password** to generate a new one.
4. Run the following command to copy and rename `.env.example` to `.env`:

    ```shell
    cp .env.example .env
    ```

5. Copy and paste the corresponding connection string into `.env`. Change the example results as follows.

    ```properties
    TIDB_HOST='{gateway-region}.aws.tidbcloud.com'
    TIDB_PORT='4000'
    TIDB_USER='{prefix}.root'
    TIDB_PASSWORD='{password}'
    TIDB_DB_NAME='test'
    USE_SSL='true'
    ```

    Replace placeholders `{}` with values obtained from the **Connect** window.

    TiDB Serverless requires the use of a secure connection, so the value of `USE_SSL` should be set to `true`.

6. Save the file.

</details>

<details>

<summary><b>(Option 2) TiDB Dedicated</b></summary>

1. In the TiDB Cloud Web Console, select your TiDB Dedicated cluster, go to the **Overview** page, click the **Connect** button in the upper right corner. Click **Allow Access from Anywhere**.
    > For more configuration details, refer to [TiDB Dedicated Standard Connection Guide](https://docs.pingcap.com/tidbcloud/connect-via-standard-connection).

2. Run the following command to copy and rename `.env.example` to `.env`:

    ```shell
    cp .env.example .env
    ```

3. Copy and paste the corresponding connection string into `.env`. Change the example results as follows.

    ```properties
    TIDB_HOST='{host}.clusters.tidb-cloud.com'
    TIDB_PORT='4000'
    TIDB_USER='{prefix}.root'
    TIDB_PASSWORD='{password}'
    TIDB_DB_NAME='test'
    USE_SSL='false'
    ```

    Replace placeholders `{}` with values obtained from the **Connect** window, and configure the certificate path downloaded in previous steps.

4. Save the file.

</details>

<details>
<summary><b>(Option 3) Self-Hosted TiDB</b></summary>

1. Run the following command to copy and rename `.env.example` to `.env`:

    ```shell
    cp .env.example .env
    ```

2. Copy and paste the corresponding connection string into `.env`. Change the example results as follows.

    ```properties
    TIDB_HOST='{tidb_server_host}'
    TIDB_PORT='4000'
    TIDB_USER='root'
    TIDB_PASSWORD='{password}'
    TIDB_DB_NAME='test'
    USE_SSL='false'
    ```

    Replace placeholders `{}` with values corresponding to your TiDB setup. If you are running TiDB on your local machine, the default Host address is `127.0.0.1`, and the password is empty.

3. Save the file.

</details>

### 3. Run the Example Code

```shell
make
```

### 4. Expected Output

[Expected Output](/Expected-Output.txt)

## Notes

For more usage details and information about **GORM**, you can refer to the [official GORM documentation](https://gorm.io/zh_CN/docs/index.html).

## Next Steps

- You can continue reading the developer documentation to gain more knowledge about TiDB. For example: [Insert Data](https://docs.pingcap.com/tidb/stable/dev-guide-insert-data), [Update Data](https://docs.pingcap.com/tidb/stable/dev-guide-update-data), [Delete Data](https://docs.pingcap.com/tidb/stable/dev-guide-delete-data), [Read from a Single Table](https://docs.pingcap.com/tidb/stable/dev-guide-get-data-from-single-table), [Transactions](https://docs.pingcap.com/tidb/stable/dev-guide-transaction-overview), [SQL Performance Optimization](https://docs.pingcap.com/tidb/stable/dev-guide-optimize-sql-overview).
- If you prefer a structured learning approach, we provide professional course for application developers: [Learn SQL with TiDB](https://eng.edu.pingcap.com/catalog/info/id:235).
