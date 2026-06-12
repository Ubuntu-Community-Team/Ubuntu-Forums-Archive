---
title: "Nagios Ubuntu 14.04 New user unable to authenticate htpasswd.users"
date: 2014-09-30
forum: Server Platforms
---

### Post by lingpanda on 2014-09-30
Hello,

     Nagiosadmin can log in fine. When I create a new user with 

```
htpasswd /usr/local/nagios/etc/htpasswd.users newuser
```

This user is unable to authenticate with nagios/apache to log in. I receive the following in access.log

```
127.0.0.1 - - [30/Sep/2014:09:45:30 -0400] "GET / HTTP/1.0" 200 11783 "-" "check_http/v2.0.3 (nagios-plugins 2.0.3)"
172.16.232.30 - - [30/Sep/2014:09:48:49 -0400] "GET /nagios/ HTTP/1.1" 401 725 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko"
127.0.0.1 - - [30/Sep/2014:09:48:51 -0400] "GET / HTTP/1.1" 200 11783 "-" "check_http/v1.5 (nagios-plugins 1.5)"
172.16.232.30 - newuser [30/Sep/2014:09:48:54 -0400] "GET /nagios/ HTTP/1.1" 401 725 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko"
```

With nagiosadmin this

```
127.0.0.1 - - [30/Sep/2014:09:50:30 -0400] "GET / HTTP/1.0" 200 11783 "-" "check_http/v2.0.3 (nagios-plugins 2.0.3)"
172.16.232.30 - - [30/Sep/2014:09:52:25 -0400] "GET /nagios/ HTTP/1.1" 401 725 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko"
172.16.232.30 - nagiosadmin [30/Sep/2014:09:52:35 -0400] "GET /nagios/ HTTP/1.1" 200 792 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko"
172.16.232.30 - nagiosadmin [30/Sep/2014:09:52:35 -0400] "GET /nagios/side.php HTTP/1.1" 200 1363 "http://172.16.232.27/nagios/" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko"
172.16.232.30 - nagiosadmin [30/Sep/2014:09:52:35 -0400] "GET /nagios/main.php HTTP/1.1" 200 3565 "http://172.16.232.27/nagios/" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko"
172.16.232.30 - nagiosadmin [30/Sep/2014:09:52:35 -0400] "GET /nagios/cgi-bin/statusjson.cgi?query=programstatus HTTP/1.1" 200 1341 "http://172.16.232.27/nagios/main.php" "Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; rv:11.0) like Gecko"
```

What am I missing? Thanks.


** Fixed by setting the correct file permissions on htpasswd.users and running the command. I inadvertently set the permissions after running the command.

---

