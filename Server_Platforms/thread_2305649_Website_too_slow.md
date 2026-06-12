---
title: "Website too slow"
date: 2015-12-08
forum: Server Platforms
---

### Post by alfirdaous on 2015-12-08
Hello everybody,

Sometimes my website takes a long time to load, from different pages,  different devices and browsers, it takes more than a minute, sometimes  it show the content and sometimes 500 Internal Error, and other website  are displayed, this happens while using PHPMyAdmin as well.



  I uploaded the website in 2 different servers, it is the same thing, and the servers are mine, no other websites hosted.
  I can get theses errors from error.log:

```


105.151.122.22 - - [25/Nov/2015:07:08:21 +0300] "-" 408 0 "-" "-"
105.151.122.22 - - [25/Nov/2015:07:08:21 +0300] "-" 408 0 "-" "-"
105.151.122.22 - - [25/Nov/2015:07:08:22 +0300] "-" 408 0 "-" "-"
105.151.122.22 - - [25/Nov/2015:07:08:22 +0300] "-" 408 0 "-" "-"
105.151.122.22 - - [25/Nov/2015:07:08:22 +0300] "-" 408 0 "-" "-"
::1 - - [25/Nov/2015:07:08:25 +0300] "OPTIONS * HTTP/1.0" 200 110 "-" "Apache/2.4.12 (Ubuntu) (internal dummy connection)"

```


and theses from access.log:

```


[Wed Nov 25 07:09:13.008575 2015] [:error] [pid 14972] [client 105.151.122.22:55678] PHP Stack trace:
[Wed Nov 25 07:09:13.008608 2015] [:error] [pid 14972] [client 105.151.122.22:55678] PHP   1. {main}() /home/alfirdaouscom/www/index.php:0
[Wed Nov 25 07:09:13.008645 2015] [:error] [pid 14972] [client 105.151.122.22:55678] PHP   2. require_once() /home/alfirdaouscom/www/index.php:6170

```

```


Hence while is not loading, I can access the server via SSH and I can upload files easily.



```


```
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

```


Thanks in advance

---

### Post by Bucky Ball on 2015-12-08
*Thread moved to **Server Platforms**.*

---

### Post by alfirdaous on 2015-12-08
Thanks [**[COLOR=#C61919][B]Bucky Ball**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=504316")

---

### Post by SeijiSensei on 2015-12-09
There are so many possible reasons for this that you'll need to do some troubleshooting.

First, create a simple HTML page with no PHP.  Something like:

```

<html>
<body>
<h2>Hello, world!</h2>
</body>
</html>

```
Can you access that without delay?

Next create a page that runs the phpinfo() function like this:
```
echo '<?php phpinfo() ?>' > /path/to/site/info.php
```
How long does it take to display that?

If both of these come up right away, I'm guessing that either you have some issues in your PHP code, or you have links to non-existent objects.

---

### Post by alfirdaous on 2015-12-09
Both are displayed on the same time, less than a minute, but my problem  is happening from time to time, not always I loaded my pages

---

### Post by SeijiSensei on 2015-12-10
Are you extracting records from a database?  Since you mention MySQL I suspect that's the case.  If so, I'd check to make sure the database has a sufficient number of indexes to match all the queries in your PHP code.  If you do a SELECT with a qualifier, especially a complex qualifier that relies on multiple fields, they can be very slow unless you have an index that jointly includes all the fields used in any WHERE clauses.

---

### Post by alfirdaous on 2015-12-10
Sometimes I faced this problem while opening ONLY phpMyAdmin, without opening the website

---

### Post by alfirdaous on 2015-12-15
I placed a phpinfo() code into my server1, and while the website cannot  load, this page cannot be opened as well, I tested the same with another  server (server2 is using the server1 databse), I tested the same, when  the website in server1 is not loaded the page in server2 is loaded, I  checked the apache2 version, they have different one:

server1:
```

apachectl -V
Server version: Apache/2.4.12 (Ubuntu)
Server built:   Feb  4 2015 14:21:10
Server's Module Magic Number: 20120211:41
Server loaded:  APR 1.5.2, APR-UTIL 1.5.4
Compiled using: APR 1.5.1, APR-UTIL 1.5.3
Architecture:   64-bit
Server MPM:     prefork
  threaded:     no
    forked:     yes (variable process count)
Server compiled with....
 -D APR_HAS_SENDFILE
 -D APR_HAS_MMAP
 -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
 -D APR_USE_SYSVSEM_SERIALIZE
 -D APR_USE_PTHREAD_SERIALIZE
 -D SINGLE_LISTEN_UNSERIALIZED_ACCEPT
 -D APR_HAS_OTHER_CHILD
 -D AP_HAVE_RELIABLE_PIPED_LOGS
 -D DYNAMIC_MODULE_LIMIT=256
 -D HTTPD_ROOT="/etc/apache2"
 -D SUEXEC_BIN="/usr/lib/apache2/suexec"
 -D DEFAULT_PIDLOG="/var/run/apache2.pid"
 -D DEFAULT_SCOREBOARD="logs/apache_runtime_status"
 -D DEFAULT_ERRORLOG="logs/error_log"
 -D AP_TYPES_CONFIG_FILE="mime.types"
 -D SERVER_CONFIG_FILE="apache2.conf"

```


server2: 
```

$ apachectl -V
/usr/sbin/apachectl: line 87: ulimit: open files: cannot modify limit: Operation not permitted
Server version: Apache/2.2.22 (Ubuntu)
Server built:   Jul 24 2015 17:25:42
Server's Module Magic Number: 20051115:30
Server loaded:  APR 1.4.6, APR-Util 1.3.12
Compiled using: APR 1.4.6, APR-Util 1.3.12
Architecture:   64-bit
Server MPM:     Prefork
  threaded:     no
    forked:     yes (variable process count)
Server compiled with....
 -D APACHE_MPM_DIR="server/mpm/prefork"
 -D APR_HAS_SENDFILE
 -D APR_HAS_MMAP
 -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
 -D APR_USE_SYSVSEM_SERIALIZE
 -D APR_USE_PTHREAD_SERIALIZE
 -D SINGLE_LISTEN_UNSERIALIZED_ACCEPT
 -D APR_HAS_OTHER_CHILD
 -D AP_HAVE_RELIABLE_PIPED_LOGS
 -D DYNAMIC_MODULE_LIMIT=128
 -D HTTPD_ROOT="/etc/apache2"
 -D SUEXEC_BIN="/usr/lib/apache2/suexec"
 -D DEFAULT_PIDLOG="/var/run/apache2.pid"
 -D DEFAULT_SCOREBOARD="logs/apache_runtime_status"
 -D DEFAULT_LOCKFILE="/var/run/apache2/accept.lock"
 -D DEFAULT_ERRORLOG="logs/error_log"
 -D AP_TYPES_CONFIG_FILE="mime.types"
 -D SERVER_CONFIG_FILE="apache2.conf"

```

---

