---
title: "Freeradius MYSQL log Problem"
date: 2016-01-22
forum: Server Platforms
---

### Post by adem_darguner on 2016-01-22
Hi Everyone,

We use Ubuntu 15.10 Server (32-bit)

We have problem Freeradius + MYSQL log problem.We cannot see Access-Accept , Access-Reject Log in the /var/log/freeradius/
We see only the MYSQL requests to Freeradius log. We want see Access-Accept  and Access-Reject log in the /var/log/Freeradius.

What is problem?
Thank you

Regards

---

### Post by MAFoElffen on 2016-01-22
If you look at your radias.conf file, it probably looks like this default version:
```

log {
    destination = files
    file = ${logdir}/radius.log
[COLOR=#ff0000]#   requests = ${logdir}/radiusd-%{%{Virtual-Server}:-DEFAULT}-%Y%m%d.log[/COLOR]
    syslog_facility = daemon
    stripped_names = no
    auth = no
    auth_badpass = no
    auth_goodpass = no
#   msg_goodpass = ""
#   msg_badpass = ""
}

```
See the line above, that I highlighted in Red? Uncomment that line and it should start logging requests. The Requests Log, is not on by by default.

---

### Post by adem_darguner on 2016-01-24
Hi [**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1044547")

Thank you for your response. This feature is already open.
I want to see username >> Access-accept and username >> Access-Reject logs. I only see MYSQL request.
Have you got a different idea?

Thank you.




root@tokenserver:/var/log/freeradius# **radtest adem 00000000066186770941821001 localhost 0 freeradiussecret**
Sending Access-Request of id 100 to 127.0.0.1 port 1812
        User-Name = "adem"
        User-Password = "00000000066186770941821001"
        NAS-IP-Address = 127.0.1.1
        NAS-Port = 0
        Message-Authenticator = 0x00000000000000000000000000000000
rad_recv: Access-Accept packet from host 127.0.0.1 port 1812, id=100, length=20
root@tokenserver:/var/log/freeradius#







**MYSQL Reguest in the /var/log/freeradius/**

drwxr-x---  2 freerad freerad  4096 Jan 24 06:48 .
drwxrwxr-x 14 root    syslog   4096 Jan 24 06:48 ..
-rw-r--r--  1 freerad freerad  1267 Jan 24 16:12 radius.log
-rw-r--r--  1 freerad freerad 10888 Jan 24 06:48 radius.log.1
-rw-r--r--  1 freerad freerad   900 Jan 17 06:38 radius.log.2.gz
-rw-r--r--  1 freerad freerad  1774 Jan 11 06:28 radius.log.3.gz
-rw-r--r--  1 freerad freerad   336 Jan  3 06:30 radius.log.4.gz
-rw-r--r--  1 freerad freerad     0 Dec 30 09:08 radwtmp


[B]
radius.log.1 [/B]

Sun Jan 17 06:38:07 2016 : Info: Loaded virtual server inner-tunnel
Mon Jan 18 13:05:16 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Mon Jan 18 13:05:16 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Mon Jan 18 13:05:16 2016 : Info: rlm_sql (sql): Connected new DB handle, #4
Mon Jan 18 13:05:16 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #3
Mon Jan 18 13:05:16 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #3
Mon Jan 18 13:05:16 2016 : Info: rlm_sql (sql): Connected new DB handle, #3
Mon Jan 18 13:07:03 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #2
Mon Jan 18 13:07:03 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #2
Mon Jan 18 13:07:03 2016 : Info: rlm_sql (sql): Connected new DB handle, #2
Mon Jan 18 13:07:25 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #1
Mon Jan 18 13:07:25 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #1
Mon Jan 18 13:07:25 2016 : Info: rlm_sql (sql): Connected new DB handle, #1
Mon Jan 18 13:07:25 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Mon Jan 18 13:07:25 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Mon Jan 18 13:07:25 2016 : Info: rlm_sql (sql): Connected new DB handle, #0
Tue Jan 19 10:41:29 2016 : Info: Signalled to terminate
Tue Jan 19 10:41:29 2016 : Info: Exiting normally.
Tue Jan 19 10:41:29 2016 : Info: rlm_sql (sql): Closing sqlsocket 4
Tue Jan 19 10:41:29 2016 : Info: rlm_sql (sql): Closing sqlsocket 3
Tue Jan 19 10:41:29 2016 : Info: rlm_sql (sql): Closing sqlsocket 2
Tue Jan 19 10:41:29 2016 : Info: rlm_sql (sql): Closing sqlsocket 1
Tue Jan 19 10:41:29 2016 : Info: rlm_sql (sql): Closing sqlsocket 0
Tue Jan 19 10:42:16 2016 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Tue Jan 19 10:42:16 2016 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Tue Jan 19 10:42:16 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Tue Jan 19 10:42:16 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Tue Jan 19 10:42:16 2016 : Info: rlm_sql (sql): Connected new DB handle, #0
Tue Jan 19 10:42:16 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #1
Tue Jan 19 10:42:16 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #1
Tue Jan 19 10:42:16 2016 : Info: rlm_sql (sql): Connected new DB handle, #1
Tue Jan 19 10:42:16 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #2
Tue Jan 19 10:42:16 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #2
Tue Jan 19 10:42:16 2016 : Info: rlm_sql (sql): Connected new DB handle, #2

---

### Post by adem_darguner on 2016-01-24
Dear All,

This problem or question is solved. How?

So,

I want to see the Access-Accept and Access-Reject message.If you do the normal config , yes worked.But i if you do not see these messages are integrated with MySQL.
/var/log /FreeRadius/radacct is not write these messages this file. Because you used MYSQL inegrated for Freeradius;

Solutions;

This posts MYSQL, author radpostauth table.

You can see:

**mysql> select * from radpostauth;**


+----+---------------+----------------------------+---------------+---------------------+
| id | username      | pass                       | reply         | authdate            |
+----+---------------+----------------------------+---------------+---------------------+
|  1 | admin             | admin123                   | Access-Accept | 2016-01-03 15:21:20 |
|  2 | admin             | admin123                   | Access-Accept | 2016-01-03 15:23:09 |
|  3 | abcdef            | admin123                   | Access-Accept | 2016-01-19 15:58:39 |
**|  4 | abcdef            | abc123                       | Access-Reject | 2016-01-24 21:55:36 |**
+----+---------------+----------------------------+---------------+---------------------+

If you do not see the Access-Reject message, do the following changes to the file.


Edit File: **etc/freeradius/sites-available/default**

----------------------------------------------------
**Original File:  (Remove "#" for sql )**

post-auth {
     Post-Auth-Type REJECT {
#         sql
         attr_filter.access_reject


[B]Change File:

[/B]post-auth {
     Post-Auth-Type REJECT {
         sql
         attr_filter.access_reject


----------------------------------------------------

Enjoy..

---

### Post by MAFoElffen on 2016-01-24
@ adem... Please go back to your posts > edit > go advanced > highlight the text to your code and/or output segments (one at a time) > press the "**#**" icon.

That will enclose you code into codes tags. They get touchy about the that here. Besides saving space by adding scroll bars, it also makes it easier to read.

Sorry, missed that part of what you were trying to do:
```

#  Log passwords with the authentication requests.
#  auth_badpass  - logs password if it's rejected
#  auth_goodpass - logs password if it's correct
#
#  allowed values: {no, yes}
#
auth_badpass = yes
auth_goodpass = yes

``` 
for the log to log password attemptes... 
 
Then in MySQL to query radpostauth...
```

select username, min(authdate) 
from radpostauth 
group by username
having min(authdate) > NOW() - INTERVAL 24 HOUR

```

Are you looking to do something like that?

---

### Post by adem_darguner on 2016-01-25
Hello Again,

Unfortunately, This option is enable. I tried to this. Writing for MySQL enough for me. I wrote above.

Thank you for your help.


```
   #  Log passwords with the authentication requests.
        #  auth_badpass  - logs password if it's rejected
        #  auth_goodpass - logs password if it's correct
        #
        #  allowed values: {no, yes}
        #
        auth_badpass = yes
        auth_goodpass = yes
```

```
/var/log/freeradius/radius.log


Sun Jan 24 06:48:24 2016 : Info: HUP - loading modules
Sun Jan 24 06:48:24 2016 : Info:  Module: Reloaded module "suffix"
Sun Jan 24 06:48:24 2016 : Info:  Module: Reloaded module "attr_filter.access_reject"
Sun Jan 24 06:48:24 2016 : Info:  Module: Reloaded module "attr_filter.accounting_response"
Sun Jan 24 06:48:24 2016 : Info:  Module: Reloaded module "radutmp"
Sun Jan 24 06:48:24 2016 : Info:  Module: Reloaded module "files"
Sun Jan 24 06:48:24 2016 : Info:  Module: Reloaded module "detail"
Sun Jan 24 06:48:24 2016 : Info:  Module: Reloaded module "pap"
Sun Jan 24 06:48:24 2016 : Info:  Module: Reloaded module "mschap"
Sun Jan 24 06:48:24 2016 : Info: Loaded virtual server <default>
Sun Jan 24 06:48:24 2016 : Info: Loaded virtual server inner-tunnel
Sun Jan 24 16:12:02 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sun Jan 24 16:12:02 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sun Jan 24 16:12:02 2016 : Info: rlm_sql (sql): Connected new DB handle, #0
Sun Jan 24 16:12:02 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Sun Jan 24 16:12:02 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Sun Jan 24 16:12:02 2016 : Info: rlm_sql (sql): Connected new DB handle, #4
Sun Jan 24 17:49:06 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #3
Sun Jan 24 17:49:06 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #3
Sun Jan 24 17:49:06 2016 : Info: rlm_sql (sql): Connected new DB handle, #3
Sun Jan 24 17:49:06 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #2
Sun Jan 24 17:49:06 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #2
Sun Jan 24 17:49:06 2016 : Info: rlm_sql (sql): Connected new DB handle, #2
Sun Jan 24 18:03:39 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #1
Sun Jan 24 18:03:39 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #1
Sun Jan 24 18:03:39 2016 : Info: rlm_sql (sql): Connected new DB handle, #1
Sun Jan 24 18:03:39 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sun Jan 24 18:03:39 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sun Jan 24 18:03:39 2016 : Info: rlm_sql (sql): Connected new DB handle, #0
Sun Jan 24 18:25:28 2016 : Info: Signalled to terminate
Sun Jan 24 18:25:28 2016 : Info: Exiting normally.
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Closing sqlsocket 4
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Closing sqlsocket 3
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Closing sqlsocket 2
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Closing sqlsocket 1
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Closing sqlsocket 0
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Driver rlm_sql_mysql (module rlm_sql_mysql) loaded and linked
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Attempting to connect to radius@localhost:/radius
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #0
Sun Jan 24 18:25:28 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #0
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Connected new DB handle, #0
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #1
Sun Jan 24 18:25:28 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #1
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Connected new DB handle, #1
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #2
Sun Jan 24 18:25:28 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #2
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Connected new DB handle, #2
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #3
Sun Jan 24 18:25:28 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #3
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Connected new DB handle, #3
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Attempting to connect rlm_sql_mysql #4
Sun Jan 24 18:25:28 2016 : Info: rlm_sql_mysql: Starting connect to MySQL server for #4
Sun Jan 24 18:25:28 2016 : Info: rlm_sql (sql): Connected new DB handle, #4
Sun Jan 24 18:25:28 2016 : Info: Loaded virtual server <default>
Sun Jan 24 18:25:28 2016 : Info: Loaded virtual server inner-tunnel
Sun Jan 24 18:25:28 2016 : Info:  ... adding new socket proxy address * port 37768
Sun Jan 24 18:25:28 2016 : Info: Ready to process requests.
Sun Jan 24 18:42:58 2016 : Info: Signalled to terminate
Sun Jan 24 18:42:58 2016 : Info: Exiting normally.
Sun Jan 24 18:42:58 2016 : Info: rlm_sql (sql): Closing sqlsocket 4
Sun Jan 24 18:42:58 2016 : Info: rlm_sql (sql): Closing sqlsocket 3
Sun Jan 24 18:42:58 2016 : Info: rlm_sql (sql): Closing sqlsocket 2
Sun Jan 24 18:42:58 2016 : Info: rlm_sql (sql): Closing sqlsocket 1
```

---

### Post by MAFoElffen on 2016-01-25
The log looks like it is making the connection to MySQL but you say it is not populating the Table9s)... Hmmm.

I did a little research to see if I could find anything related to that:
[http://wiki.freeradius.org/guide/SQL-HOWTO#Create_MySQL_Database](http://wiki.freeradius.org/guide/SQL-HOWTO#Create_MySQL_Database)
[http://techtots.blogspot.com/2010/01/installing-and-configuring-freeradius.html](http://techtots.blogspot.com/2010/01/installing-and-configuring-freeradius.html)
[http://www.serveradminblog.com/2011/12/freeradius-install-howto-4-populating-tables/](http://www.serveradminblog.com/2011/12/freeradius-install-howto-4-populating-tables/)

---

