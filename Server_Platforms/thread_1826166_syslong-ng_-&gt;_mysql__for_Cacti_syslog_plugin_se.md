---
title: "syslong-ng -&gt; mysql  for Cacti syslog plugin setup."
date: 2011-08-16
forum: Server Platforms
---

### Post by mangloid on 2011-08-16
I guess with major changes to syslog-ng, php-syslog going to licensing cost, and major overhaul to the syslog plugin with cacti - alot of documention was either disjointed, outdated or I just couldn't find it.

this was performed on an 11.04 Ubuntu Server install. I already had Cacti up and running and just needed to make it also a syslog collector.


This guide assumes you already have mysql running, and cacti is already in place. If something looks wrong - please correct me. I am doing this from memory - trying to remember what all I had to do, and not a super admin.


**Required ubuntu install packages:**

libdbd-mysql syslog-ng


**cacti install packages:**

syslog 1.21 + 
[http://docs.cacti.net/plugin:syslog](http://docs.cacti.net/plugin:syslog)



**syslog-ng configuration:**

Stop syslog-ng if you want. Changes should not take effect until you restart it.

Should save the default syslog-ng configuration if you want to be safe. Below is the absolute minimum you need to get this working.
Configuration on ubuntu is location in /etc/syslog/syslog-ng.conf Also make sure you fill in the proper username and password for mysql.

```
@version: 3.1
#Bare minimum syslog-ng configuration

options { long_hostnames(off); flush_lines(0); use_dns(no); use_fqdn(no);
          owner("root"); group("adm"); perm(0640); stats_freq(0);
          bad_hostname("^gconfd$");
};

# we are using udp, and this is a collector for net traffic only
#
source s_all {
        udp();
#        internal();
#        unix-stream("/dev/log");
#        file("/proc/kmsg" log_prefix("kernel: "));
};

destination d_mysql {
        sql(type(mysql)
        host("localhost") username("xxxxx") password("xxxxxxx")
        database("syslog")
        table("syslog_incoming")
        columns("facility", "priority", "date", "time", "host", "message")
        values("$FACILITY", "$PRIORITY", "$YEAR-$MONTH-$DAY",  "$HOUR:$MIN:$SEC", "$HOST_FROM", "$MSG")
        indexes("facility", "priority", "date", "time", "host", "msg"));
};

log {
source(s_all);
destination(d_mysql);
};


```

In your cacti plugins directory(default if you used ubuntu cacti packages: /usr/share/cacti/site/plugins )

```
tar -xvzf "/path /to /syslog-v1.21-1.tgz"
cd syslog
```

edit the config.php and change:

```
$use_cacti_db = true;
```

to 

```
$use_cacti_db = false;
```

Also, you need to modify this section with your correct information:

```
if (!$use_cacti_db) {
        $syslogdb_type     = 'mysql';
        $syslogdb_default  = 'syslog';
        $syslogdb_hostname = 'localhost';
        $syslogdb_username = 'xxxxx';
        $syslogdb_password = 'xxxxx';
        $syslogdb_port     = 3306;
```


**Mysql syslog database creation**

run these commands still from the syslog plugin directory.

```

shell# mysql -u root -p #or whatever user you use with proper privileges

mysql> create database syslog;
mysql> use syslog;
mysql> source syslog.sql;
mysql> quit;
```



You should be able to now restart syslog-ng. Go to your Cacti plugins list and install and enable the plugin. By default you should be able to just accept the setup without modifying any options. 

If all is good you can point devices to your server ( udp, 514 is the setup this uses ) and start to see the syslog.

Hopefully I did not miss a step.

[IMG]http://i.imgur.com/IrwAP.png[/IMG]

---

### Post by jayakumar_mk on 2011-08-30
Hi bro,

i tried a lot with the steps given by you to get syslog plugin in cacti which is installed on ubuntu. But its not coming. Kindly help me. plz give me one by one step procedure to install the same.


Thanks 
Jayakumar

---

