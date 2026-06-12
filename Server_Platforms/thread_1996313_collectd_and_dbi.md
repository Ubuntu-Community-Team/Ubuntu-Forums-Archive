---
title: "collectd and dbi"
date: 2012-06-04
forum: Server Platforms
---

### Post by Mimou on 2012-06-04
Hi everybody!

I have a little issue with collectd and the dbi plugin.
I'm trying to execute a little query:

```
SELECT VARIABLE_VALUE AS temp_tab FROM global_status WHERE VARIABLE_NAME = 'Created_tmp_disk_tables'
```

But when I'm trying to restart the collectd daemon I have this error in the syslog file:

```
Jun  4 12:16:02 devBox collectd[8820]: dbi plugin: cdbi_init: dbi_initialize failed with status -1.
Jun  4 12:16:02 devBox collectd[8820]: Initialization of plugin `dbi' failed with status -1. Plugin will be unloaded.

```

Impossible to execute my query.

And here this is my configuration:

```

<Plugin dbi>
       <Query "num_of_temptab">
                Statement "SELECT VARIABLE_VALUE AS temp_tab FROM global_status WHERE VARIABLE_NAME = 'Created_tmp_disk_tables'"
                <Result>
                        Type "gauge"
                        ValuesFrom "temp_tab"
                </Result>
        </Query>

        <Database "mysqlTest">
                Driver "mysql"
                DriverOption "host" "192.168.111.233"
                DriverOption "username" "collectd"
                DriverOption "password" "password"
                DriverOption "dbname" "information_schema"
                SelectDB "information_schema"
                Query "num_of_temptab"
        </Database>
</Plugin>

```

Maybe I forgive something.

Last informations. I'm using Ubuntu 12.04 and collectd 4.10.
The libdi is installed.

If somebody can help me :)
Thanks!

LaCap

---

### Post by Mimou on 2012-06-05
Never mind.
I find what was wrong.

The MySQL DBI was missing.
After the installation everything was OK.

FYI, you need to install this package: libdbd-mysql

---

