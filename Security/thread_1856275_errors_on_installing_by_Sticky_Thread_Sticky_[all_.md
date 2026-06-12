---
title: "errors on installing by Sticky Thread Sticky: [all variants] Network Intrusion Detect"
date: 2011-10-07
forum: Security
---

### Post by Karottenbaum on 2011-10-07
i was trying to install snort but allready expected troubles...
further down this quote are some strange results/errors like **"sudo: postgres: command not found"**

```
 * Starting PostgreSQL 8.4 database server                                                                                                          [ OK ] 
Setting up postgresql (8.4.8-0ubuntu0.11.04) ...
Setting up snort-common-libraries (2.8.5.2-7) ...
Setting up snort-rules-default (2.8.5.2-7) ...
Setting up libprelude2 (1.0.0-1ubuntu1) ...
Setting up snort-pgsql (2.8.5.2-7) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline

/etc/snort/db-pending-config file found
Snort will not start as its database is not yet configured.
Please configure the database as described in
/usr/share/doc/snort-pgsql/README-database.Debian
and then remove /etc/snort/db-pending-config
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@acer:~# sudo su postgres
postgres@acer:/root$ createdb snort_db
could not change directory to "/root"
postgres@acer:/root$ exit
exit
root@acer:~# sudo postgres
sudo: postgres: command not found
root@acer:~# su  postgres
postgres@acer:/root$ createdb snort_db
could not change directory to "/root"
createdb: database creation failed: ERROR:  database "snort_db" already exists


```

i had this line which gave me an error

> #output database: alert, postgresql, user=snort dbname=snortso i quoted it  out with **#** and just tryed to put in your line:

> output database: alert, postgresql, user=snort dbname=snort_db password=snort_password host=localhostbut same error with this:

> root@acer:/etc/snort# sudo snort -c /etc/snort/snort.conf -T
Running in Test mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file "/etc/snort/snort.conf"
PortVar 'HTTP_PORTS' defined :  [ 80 ]
PortVar 'SHELLCODE_PORTS' defined :  [ 0:79 81:65535 ]
PortVar 'ORACLE_PORTS' defined :  [ 1521 ]
PortVar 'FTP_PORTS' defined :  [ 21 ]
Tagged Packet Limit: 256
Loading dynamic engine /usr/lib/snort_dynamicengine/libsf_engine.so... done
Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/...
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dce2_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssl_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//lib_sfdynamic_preprocessor_example.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... done
  Finished Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/
database: must enter host in configuration file


USAGE: database plugin

 output database: [log | alert], [type of database], [parameter list]

 [log | alert] selects whether the plugin will use the alert or
 log facility.

 For the first argument, you must supply the type of database.
 The possible values are mysql, postgresql, odbc, oracle and
 mssql 
 The parameter list consists of key value pairs. The proper
 format is a list of key=value pairs each separated a space.

 The only parameter that is absolutely necessary is "dbname".
 All other parameters are optional but may be necessary
 depending on how you have configured your RDBMS.
root@acer:/etc/snort# sudo nano -B /etc/snort/snort.conf
root@acer:/etc/snort# sudo snort -c /etc/snort/snort.conf -T
Running in Test mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file "/etc/snort/snort.conf"
PortVar 'HTTP_PORTS' defined :  [ 80 ]
PortVar 'SHELLCODE_PORTS' defined :  [ 0:79 81:65535 ]
PortVar 'ORACLE_PORTS' defined :  [ 1521 ]
PortVar 'FTP_PORTS' defined :  [ 21 ]
Tagged Packet Limit: 256
Loading dynamic engine /usr/lib/snort_dynamicengine/libsf_engine.so... done
Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/...
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dce2_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ftptelnet_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_smtp_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssl_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dcerpc_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_ssh_preproc.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//lib_sfdynamic_preprocessor_example.so... done
  Loading dynamic preprocessor library /usr/lib/snort_dynamicpreprocessor//libsf_dns_preproc.so... done
  Finished Loading all dynamic preprocessor libs from /usr/lib/snort_dynamicpreprocessor/
database: must enter database name in configuration file


USAGE: database plugin

 output database: [log | alert], [type of database], [parameter list]

 [log | alert] selects whether the plugin will use the alert or
 log facility.

 For the first argument, you must supply the type of database.
 The possible values are mysql, postgresql, odbc, oracle and
 mssql 
 The parameter list consists of key value pairs. The proper
 format is a list of key=value pairs each separated a space.

 The only parameter that is absolutely necessary is "dbname".
 All other parameters are optional but may be necessary
 depending on how you have configured your RDBMS.

 dbname - the name of the database you are connecting to

 host - the host the RDBMS is on

 port - the port number the RDBMS is listening on

 user - connect to the database as this user

 password - the password for given user

 sensor_name - specify your own name for this snort sensor. If you
        do not specify a name one will be generated automatically

 encoding - specify a data encoding type (hex, base64, or ascii)

 detail - specify a detail level (full or fast)

 ignore_bpf - specify if you want to ignore the BPF part for a sensor

              definition (yes or no, no is default)

 FOR EXAMPLE:
 The configuration I am currently using is MySQL with the database
 name of "snort". The user "snortusr@localhost" has INSERT and SELECT
 privileges on the "snort" database and does not require a password.
 The following line enables snort to log to this database.

 output database: log, mysql, dbname=snort user=snortusr host=localhost

ERROR: Fatal Error, Quitting..i really have no idea whats going on, im very new t linux and allready tyred of configuring or at least trying to... i need to go sleep!

good night!

---

### Post by Karottenbaum on 2011-10-09
bump

---

### Post by bodhi.zazen on 2011-10-11
You need to substitue your actual database name, user name, and password in the line

"user=snort dbname=snort_db password=snort_password"

---

