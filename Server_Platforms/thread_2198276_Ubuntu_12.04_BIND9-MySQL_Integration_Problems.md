---
title: "Ubuntu 12.04 BIND9-MySQL Integration Problems"
date: 2014-01-08
forum: Server Platforms
---

### Post by ozmedicdoc on 2014-01-08
Hello all,
I have been struggling with BIND9, trying to get it to work with MySQL for the zones. I have tried about 20 different tutorials, some of the several times, trying to debug myself.
Among the tutorials, I tried this: [http://ubuntuforums.org/showthread.php?t=823578&p=5675119#post5675119](http://ubuntuforums.org/showthread.php?t=823578&p=5675119#post5675119)

It gives me this error, stating that I have undefined references to sdlzh stuff:
```
.libs/dlz_mysql_driver.o: In function `.L33':
dlz_mysql_driver.c:(.text+0x400): undefined reference to `sdlzh_build_querystring'
.libs/dlz_mysql_driver.o: In function `mysql_destroy':
dlz_mysql_driver.c:(.text+0x114c): undefined reference to `sdlzh_destroy_sqldbinstance'
.libs/dlz_mysql_driver.o: In function `mysql_create':
dlz_mysql_driver.c:(.text+0x1225): undefined reference to `sdlzh_get_parameter_value'
dlz_mysql_driver.c:(.text+0x124c): undefined reference to `sdlzh_get_parameter_value'
dlz_mysql_driver.c:(.text+0x1325): undefined reference to `sdlzh_destroy_sqldbinstance'
dlz_mysql_driver.c:(.text+0x1463): undefined reference to `sdlzh_build_sqldbinstance'
dlz_mysql_driver.c:(.text+0x14b5): undefined reference to `sdlzh_build_sqldbinstance'
dlz_mysql_driver.c:(.text+0x158f): undefined reference to `sdlzh_get_parameter_value'
dlz_mysql_driver.c:(.text+0x15fe): undefined reference to `sdlzh_get_parameter_value'
dlz_mysql_driver.c:(.text+0x166b): undefined reference to `sdlzh_get_parameter_value'
dlz_mysql_driver.c:(.text+0x16d8): undefined reference to `sdlzh_get_parameter_value'
dlz_mysql_driver.c:(.text+0x16f7): undefined reference to `sdlzh_get_parameter_value'
.libs/dlz_mysql_driver.o:dlz_mysql_driver.c:(.text+0x1716): more undefined references to `sdlzh_get_parameter_value' follow
collect2: ld returned 1 exit status
make[3]: *** [named] Error 1
make[3]: Leaving directory `/home/mad3ngineer/bind/bind9-9.8.1.dfsg.P1/bin/named'
make[2]: *** [subdirs] Error 1
make[2]: Leaving directory `/home/mad3ngineer/bind/bind9-9.8.1.dfsg.P1/bin'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/home/mad3ngineer/bind/bind9-9.8.1.dfsg.P1'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2

```

Any workarounds, or proper tools for bind9/MySQL/Ubuntu 12.04? I have struggled for hours... If anyone could spare 15 minutes to give me a good link or write instructions, I would be most grateful...

It would be hilarious to me if there is an apt-get for bind with DLZ already packaged in it, since I have spent so much time on it.

Thanks in advance for any help.

---

### Post by ozmedicdoc on 2014-01-08
Ok,
I was able to compile bind9 properly with it, and now I am having problems with it starting:

Output on bind9 restart:
```
$ sudo service bind9 restart
 * Stopping domain name service... bind9                                        rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [ OK ]
 * Starting domain name service... bind9                                 [[COLOR=#ff0000]fail[/COLOR]]
```


Syslog output:
```
Jan  8 13:39:23 M3SERVER named[2046]: Inc. (ISC), a non-profit 501(c)(3) public-benefit
Jan  8 13:39:23 M3SERVER named[2046]: corporation.  Support and training for BIND 9 are
Jan  8 13:39:23 M3SERVER named[2046]: available at https://www.isc.org/support
Jan  8 13:39:23 M3SERVER named[2046]: ----------------------------------------------------
Jan  8 13:39:23 M3SERVER named[2046]: adjusted limit on open files from 4096 to 1048576
Jan  8 13:39:23 M3SERVER named[2046]: found 2 CPUs, using 2 worker threads
Jan  8 13:39:23 M3SERVER named[2046]: using 2 UDP listeners per interface
Jan  8 13:39:23 M3SERVER named[2046]: using up to 4096 sockets
Jan  8 13:39:23 M3SERVER named[2046]: loading configuration from '/etc/bind/named.conf'
Jan  8 13:39:23 M3SERVER named[2046]: /etc/bind/named.conf:13: open: /etc/bind/rndc.key: permission denied
Jan  8 13:39:23 M3SERVER named[2046]: loading configuration: permission denied
Jn  8 13:39:23 M3SERVER named[2046]: /etc/bind/named.conf:13: open: /etc/bind/rndc.key: permission denied
n  8 13:39:23 M3SERVER named[2046]: exiting (due to fatal error)
```

Here is my named.conf:
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";

include "/etc/bind/rndc.key";
    controls {
    inet 127.0.0.1 port 953
    allow { 127.0.0.1; } keys { "rndc-key"; };
};

transfer-source*;
```

So it appears to be a problem with bind9 being unable to open named.conf, and rndc.key... How can I allow bind9 to use these files without doing chmod?

---

### Post by SeijiSensei on 2014-01-08
Bind9 runs as user bind and needs to be able to write into /etc/bind.  On my 13.10 system, /etc/bind is owned by root:bind with the sgid bit set.  Most of the files in that directory are also owned by root:bind except for rndc.key which is owned by bind:bind and has 640 permissions.

You probably do need to fix some permissions with chmod to accomodate this pattern of ownership.

```

Seiji@GhostWorld:/etc$ ls -l | grep bind
drwxr-sr-x  2 root bind      4096 Oct 10 08:07 bind

Seiji@GhostWorld:/etc$ ls -ltr /etc/bind
total 52
-rw-r--r-- 1 root root 1317 Jul 26 23:16 zones.rfc1918
-rw-r--r-- 1 root bind  165 Jul 26 23:16 named.conf.local
-rw-r--r-- 1 root bind  490 Jul 26 23:16 named.conf.default-zones
-rw-r--r-- 1 root bind  463 Jul 26 23:16 named.conf
-rw-r--r-- 1 root root 3048 Jul 26 23:16 db.root
-rw-r--r-- 1 root root  270 Jul 26 23:16 db.local
-rw-r--r-- 1 root root  353 Jul 26 23:16 db.empty
-rw-r--r-- 1 root root  237 Jul 26 23:16 db.255
-rw-r--r-- 1 root root  271 Jul 26 23:16 db.127
-rw-r--r-- 1 root root  237 Jul 26 23:16 db.0
-rw-r--r-- 1 root root 2389 Jul 26 23:16 bind.keys
-rw-r----- 1 bind bind   77 Sep 28 08:33 rndc.key
-rw-r--r-- 1 root bind  890 Sep 28 08:33 named.conf.options

```

This is pretty much unchanged from the defaults.

---

### Post by ozmedicdoc on 2014-01-09
I had to reinstall it several times, thus the file permissions being messed up. Anyway, after fixing the file permissions for rndc.key and named.conf.local, it will run the same lines in command prompt, and here is what I have for syslog output:
```

Jan  8 15:47:47 M3SERVER named[2123]: ----------------------------------------------------
Jan  8 15:47:47 M3SERVER named[2123]: BIND 9 is maintained by Internet Systems Consortium,
Jan  8 15:47:47 M3SERVER named[2123]: Inc. (ISC), a non-profit 501(c)(3) public-benefit
Jan  8 15:47:47 M3SERVER named[2123]: corporation.  Support and training for BIND 9 are
Jan  8 15:47:47 M3SERVER named[2123]: available at https://www.isc.org/support
Jan  8 15:47:47 M3SERVER named[2123]: ----------------------------------------------------
Jan  8 15:47:47 M3SERVER named[2123]: adjusted limit on open files from 4096 to 1048576
Jan  8 15:47:47 M3SERVER named[2123]: found 2 CPUs, using 2 worker threads
Jan  8 15:47:47 M3SERVER named[2123]: using 2 UDP listeners per interface
Jan  8 15:47:47 M3SERVER named[2123]: using up to 4096 sockets
Jan  8 15:47:47 M3SERVER named[2123]: loading configuration from '/etc/bind/named.conf'
Jan  8 15:47:47 M3SERVER named[2123]: reading built-in trusted keys from file '/etc/bind/bind.keys'
Jan  8 15:47:47 M3SERVER named[2123]: initializing GeoIP Country (IPv4) DB
Jan  8 15:47:47 M3SERVER named[2123]: GEO-106FREE 20120103 Build
Jan  8 15:47:47 M3SERVER named[2123]: initializing GeoIP Country (IPv6) DB
Jan  8 15:47:47 M3SERVER named[2123]: GEO-106FREE 20120103 Build
Jan  8 15:47:47 M3SERVER named[2123]: GeoIP City (IPv4) DB: neither revision available
Jan  8 15:47:47 M3SERVER named[2123]: GeoIP City (IPv6) DB: neither revision available
Jan  8 15:47:47 M3SERVER named[2123]: GeoIP Region DB: neither revision available
Jan  8 15:47:47 M3SERVER named[2123]: GeoIP ISP DB not available
Jan  8 15:47:47 M3SERVER named[2123]: GeoIP Org DB not available
Jan  8 15:47:47 M3SERVER named[2123]: GeoIP AS DB not available
Jan  8 15:47:47 M3SERVER named[2123]: GeoIP AS DB not available
Jan  8 15:47:47 M3SERVER named[2123]: GeoIP Domain DB not available
Jan  8 15:47:47 M3SERVER named[2123]: GeoIP NetSpeed DB not available
Jan  8 15:47:47 M3SERVER named[2123]: using default UDP/IPv4 port range: [1024, 65535]
Jan  8 15:47:47 M3SERVER named[2123]: using default UDP/IPv6 port range: [1024, 65535]
Jan  8 15:47:47 M3SERVER named[2123]: listening on IPv6 interfaces, port 53
Jan  8 15:47:47 M3SERVER named[2123]: listening on IPv4 interface lo, 127.0.0.1#53
Jan  8 15:47:47 M3SERVER named[2123]: listening on IPv4 interface eth0, 192.168.1.10#53
Jan  8 15:47:47 M3SERVER named[2123]: generating session key for dynamic DNS
Jan  8 15:47:47 M3SERVER named[2123]: sizing zone task pool based on 6 zones
Jan  8 15:47:47 M3SERVER named[2123]: Loading 'Mysql zone' using driver mysql
Jan  8 15:47:47 M3SERVER named[2123]: mysql driver failed to create database connection after 4 attempts
Jan  8 15:47:47 M3SERVER named[2123]: SDLZ driver failed to load.
Jan  8 15:47:47 M3SERVER named[2123]: DLZ driver failed to load.
Jan  8 15:47:47 M3SERVER named[2123]: loading configuration: failure
Jan  8 15:47:47 M3SERVER named[2123]: exiting (due to fatal error)
Jan  8 15:50:25 M3SERVER named[2180]: starting BIND 9.10.0a1 -u bind

```
So, I made sure the info for MySQL was correct in named.conf.local:
```

zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192";
};

#options {
#default-key "rndc-key";
#default-server 127.0.0.1;
#default-port 953;
#};

controls {
inet * port 953 allow { any; } keys { "rndc-key"; };
#inet * port 53 allow { any; } keys { "rndc-key"; };
};



logging {
    channel query.log {
        file "/var/bind9";
        // Set the severity to dynamic to see all the debug messages.
        severity dynamic;
    };

    category queries { query.log; };
};

dlz "Mysql zone" {
   database "mysql
   {host=localhost port=3306 dbname=bind9_dlz user=bind password=**********}
   {SELECT zone FROM dns_records WHERE zone = '$zone$'}
   {SELECT ttl, type, mx_priority, IF(type = 'TXT', CONCAT('\"',data,'\"'), data) AS data
    FROM dns_records
    WHERE zone = '$zone$' AND host = '$record$' AND type <> 'SOA' AND type <> 'NS'}
   {SELECT ttl, type, data, primary_ns, resp_person, serial, refresh, retry, expire, minimum
    FROM dns_records
    WHERE zone = '$zone$' AND (type = 'SOA' OR type='NS')}

```

The database is mysql, on the same machine, has a user bind with the same password as it is in the file, and the database is bind9_dlz. I tried turning off the database to see if it would give different error message, but it was the same. Just can't connect.

If this is a problem with file permissions like with the socket, what would I have to do to fix it?


In addition, I am getting this nasty error:
```

Jan  8 22:27:58 M3SERVER named[8346]: Could not open '/var/run/named/named.pid'.
Jan  8 22:27:58 M3SERVER named[8346]: Please check file and directory permissions or reconfigure the filename.
Jan  8 22:27:58 M3SERVER named[8346]: could not open file '/var/run/named/named.pid': Permission denied
Jan  8 22:27:59 M3SERVER named[8346]: generating session key for dynamic DNS
Jan  8 22:27:59 M3SERVER named[8346]: Could not open '/var/run/named/session.key'.
Jan  8 22:27:59 M3SERVER named[8346]: Please check file and directory permissions or reconfigure the filename.
Jan  8 22:27:59 M3SERVER named[8346]: could not open file '/var/run/named/session.key': Permission denied
Jan  8 22:27:59 M3SERVER named[8346]: could not create /var/run/named/session.key
Jan  8 22:27:59 M3SERVER named[8346]: failed to generate session key for dynamic DNS: permission denied
.
.
.
Jan  8 22:27:59 M3SERVER named[8346]: command channel listening on 0.0.0.0#953
Jan  8 22:27:59 M3SERVER named[8346]: /etc/bind/named.conf:15: couldn't add command channel 127.0.0.1#953: address in use
Jan  8 22:27:59 M3SERVER named[8346]: isc_stdio_open '/var/bind9' failed: permission denied
Jan  8 22:27:59 M3SERVER named[8346]: configuring logging: permission denied
Jan  8 22:27:59 M3SERVER named[8346]: loading configuration: permission denied
Jan  8 22:27:59 M3SERVER named[8346]: exiting (due to fatal error)

```

So, looks like I am having problems with the command channel, and problems with /var/bind9 files...

Help? I am grateful if somene can help me with either of my problems!

---

