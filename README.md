# Try8 & Dagster Setup Guide

## Local Setup

### Build the demo container
```
docker build -t dagster-ecomm .
```

### Run the demo container
```
docker run -it -p 13000:13000 -p 15000:15000 dagster-ecomm /bin/bash
```

### Clone Project

In the demo container run
```
git clone https://github.com/try8ai/dagster-ecomm-demo-wip && cd dagster-ecomm-demo-wip
```

### Start Dagster Server
```
dagster dev -h 0.0.0.0 -p 13000 > /dev/null 2>&1 &
```

### Materialize assets

* In your browser, navigate to [localhost:13000](http://localhost:13000)
* Select *Assets*
* Select *View global asset lineage*
* Select *Materialize All*

### Run dbt
```
dbt run
```

### Run superset
```
cd /home/dagster/superset && superset run -h 0.0.0.0 -p 15000 > /dev/null 2>&1 &
```

### Launch the superset UI

* In your browser, navigate to [localhost:15000](http://localhost:15000)
* Login Credentials: `admin:admin`
* Click the '+' icon in top right
* Select `Data` -> `Connect database`
* Type is "Other"
* SQLAlchemy URI: `duckdb:////home/dagster/dagster-ecomm-demo-wip/duckdb.duckdb`

From here you are able to create visualizations of the data
