# Introduction

This project provides connectors for Kafka Connect to read and write data to Redshift.

# Documentation

Documentation on the connector is hosted on Confluent's
[docs site](https://docs.confluent.io/current/connect/kafka-connect-aws-redshift/).

Source code is located in Confluent's
[docs repo](https://github.com/confluentinc/docs/tree/master/connect/kafka-connect-aws-redshift). If changes
are made to configuration options for the connector, be sure to generate the RST docs (as described
below) and open a PR against the docs repo to publish those changes!

# Configs

Documentation on the configurations for each connector can be automatically generated via Maven.

To generate documentation for the sink connector:
```bash
mvn -Pdocs exec:java@sink-config-docs
```

# Compatibility Matrix:

This connector has been tested against the following versions of Apache Kafka
and Redshift:

|                          | AK 1.0             | AK 1.1        | AK 2.0        |
| ------------------------ | ------------------ | ------------- | ------------- |
| **Redshift v1.0.8360**   |                    |               |               |

# Integration Tests

To run ITs in your local environment, please export the REDSHIFT_CREDS environment variable to
 the path of your credentials file, which must be in a JSON format.
```bash
export REDSHIFT_CREDS=path/to/your/creds.json
```

An example credentials file:
```$xslt
{
  "creds": {
    "domain": <your_domain>,
    "port": <your_port>,
    "user": <your_user>,
    "password": <your_password>,
    "database_name": <your_database_name>
  }
}
```

You can run `vault kv get v1/ci/kv/connect/redshift_it` to obtain Redshift credentials that 
can be used to populate a credentials file.
