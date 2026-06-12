---
title: "Mail server"
date: 2012-10-31
forum: Server Platforms
---

### Post by Sinke on 2012-10-31
Greetings.
I'm new to this forum, and I'm pretty new to using Linux, so I apologize in advance for some obvious mistakes, if any ...

I need a little help. Thus, the situation is as follows. In my company they wanted to have their own server on Linux. I said, okay, no problem, we'll do. For distribution I chose Ubuntu Server 12.04.1. Installation went without a hitch, I installed everything you need to run a mail server: Dovecot IMAP/POP3 Server and Postfix mail server, and some additional packages for safety, such as spam filters and anti-virus packages. I also installed SQL Server, because I read that this is the way the authorization of users are easy going, as far as mail concerns. I also installed BIND DNS server, Webmin and ISPConfig, and to access email from another computer SquirrelMail and / or Thunderbird.
For now, this is all just locally, but when extensive testing finish and I make sure that everything is okay, it will be the main mail server.
Now, I configured the DNS server, the name can resolve fine from Thunderbird (which is on another computer) so it can connect to the server with no problems. The problem arises when you need to authenticate the user. I tried in all ways, first with the MySQL database server. When this option is active, all you get is "Waiting for the authentication process to respond."
I then tried to change (using webmin) to authorize users via standard unix user the database. Then I get a response from Squirrelmail "Connection dropped by the IMAP server" or that the user or password is wrong, the same thing from Thunderbird. I figured as much when this option is active, when I add a user in Ubuntu, he should be able to automatically log in to the mail? I looked at the forums, mostly I've found that the problem is somewhere with the authorization of users, however, have not found anything useful.
Now I still want to try it with the PostgreSQL database server, however, I do not know how to configure it, and how to add users ... If anyone can help, I would be very grateful.

---

### Post by duesentriebchen on 2012-10-31
Hy there.
 
I do not use the SQL database because i am not in a large virtual user environement.
 
But, it seems that you either have a authentication issue or a user issue.
 
**_[COLOR=red]EDIT[/COLOR]_**
 
Could you bee so kind to post the outputs of
```
sudo lsof -nPi | grep LISTEN
```
```
ls -la /home
```
```
cat /var/log/mail.log
```
```
cat /var/log/mail.err
```
```
ls -la /var/mail
```
```
ls -la /var/spool/mail
```
```
ls -la /var/spool/postfix
```
 
Please look in /var/log for the postfix log file!!! Because i am using exim4, i do not know the postfix.log file, but i am pretty sure it will be some kind of /var/log/postfix.log
 
Have you tried
```
telnet localhost 25
```
and then 
```
ehlo localhost 
```
 
You can also do 
```
telnet localhost imap
```

and 
 
```
netcat mail.example.com 143
```

Post the output of the last four commands.
 
Down below you find some extrainfo that could help you
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)
[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts)
[http://www.postfix-tutorial.com/](http://www.postfix-tutorial.com/)
[http://manpages.ubuntu.com/manpages/dapper/man5/mysql_table.5.html](http://manpages.ubuntu.com/manpages/dapper/man5/mysql_table.5.html)
 
A normal system user is added with ```
adduser
```
[http://manpages.ubuntu.com/manpages/jaunty/man8/adduser.8.html](http://manpages.ubuntu.com/manpages/jaunty/man8/adduser.8.html)
 
Kind regards ;)

---

### Post by mlentink on 2012-11-01
You might want to read through this: [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-12.04-lts) 

I used it for my own server. Works like a breeze

---

### Post by Sinke on 2012-11-02
Well, first of all, thank you for your effort to solve my problem. 
Most of them I already tried, with same results as now, except I forgot to look at the log files. :)
Nevertheless, this is what I get when I run those commands:


```
sudo lsof -nPi | grep LISTEN
```

```
smbd        560         root   27u  IPv4   8193      0t0  TCP *:445 (LISTEN)
smbd        560         root   28u  IPv4   8195      0t0  TCP *:139 (LISTEN)
cupsd       677         root    9u  IPv6  15503      0t0  TCP [::1]:631 (LISTEN)
cupsd       677         root   10u  IPv4  15504      0t0  TCP 127.0.0.1:631 (LISTEN)
sshd        772         root    3r  IPv4   8894      0t0  TCP *:22 (LISTEN)
sshd        772         root    4u  IPv6   8898      0t0  TCP *:22 (LISTEN)
dovecot    1050         root   17u  IPv4   9483      0t0  TCP *:110 (LISTEN)
dovecot    1050         root   18u  IPv6   9484      0t0  TCP *:110 (LISTEN)
dovecot    1050         root   19u  IPv4   9485      0t0  TCP *:995 (LISTEN)
dovecot    1050         root   20u  IPv6   9486      0t0  TCP *:995 (LISTEN)
dovecot    1050         root   24u  IPv4   9493      0t0  TCP *:143 (LISTEN)
dovecot    1050         root   25u  IPv6   9494      0t0  TCP *:143 (LISTEN)
dovecot    1050         root   26u  IPv4   9495      0t0  TCP *:993 (LISTEN)
dovecot    1050         root   27u  IPv6   9496      0t0  TCP *:993 (LISTEN)
mysqld     1072        mysql   10u  IPv4   9806      0t0  TCP 127.0.0.1:3306 (LISTEN)
named      1118         bind   20u  IPv6   9751      0t0  TCP *:53 (LISTEN)
named      1118         bind   21u  IPv4   9756      0t0  TCP 127.0.0.1:53 (LISTEN)
named      1118         bind   22u  IPv4   9762      0t0  TCP 192.168.1.43:53 (LISTEN)
named      1118         bind   23u  IPv4   9769      0t0  TCP 127.0.0.1:953 (LISTEN)
named      1118         bind   24u  IPv6   9770      0t0  TCP [::1]:953 (LISTEN)
amavisd    1749       amavis    5u  IPv4  11491      0t0  TCP 127.0.0.1:10024 (LISTEN)
postgres   1779     postgres    3u  IPv4  11776      0t0  TCP 127.0.0.1:5432 (LISTEN)
amavisd    1824       amavis    5u  IPv4  11491      0t0  TCP 127.0.0.1:10024 (LISTEN)
amavisd    1825       amavis    5u  IPv4  11491      0t0  TCP 127.0.0.1:10024 (LISTEN)
master     2290         root   12u  IPv4  12584      0t0  TCP *:25 (LISTEN)
master     2290         root   13u  IPv6  12585      0t0  TCP *:25 (LISTEN)
master     2290         root  107u  IPv4  12679      0t0  TCP 127.0.0.1:10025 (LISTEN)
apache2    2395         root    3u  IPv4  12862      0t0  TCP *:80 (LISTEN)
apache2    2395         root    4u  IPv4  12865      0t0  TCP *:8081 (LISTEN)
apache2    2395         root    5u  IPv4  12867      0t0  TCP *:8080 (LISTEN)
apache2    2426     www-data    3u  IPv4  12862      0t0  TCP *:80 (LISTEN)
apache2    2426     www-data    4u  IPv4  12865      0t0  TCP *:8081 (LISTEN)
apache2    2426     www-data    5u  IPv4  12867      0t0  TCP *:8080 (LISTEN)
apache2    2427     www-data    3u  IPv4  12862      0t0  TCP *:80 (LISTEN)
apache2    2427     www-data    4u  IPv4  12865      0t0  TCP *:8081 (LISTEN)
apache2    2427     www-data    5u  IPv4  12867      0t0  TCP *:8080 (LISTEN)
apache2    2430     www-data    3u  IPv4  12862      0t0  TCP *:80 (LISTEN)
apache2    2430     www-data    4u  IPv4  12865      0t0  TCP *:8081 (LISTEN)
apache2    2430     www-data    5u  IPv4  12867      0t0  TCP *:8080 (LISTEN)
miniserv.  2445         root    6u  IPv4  13050      0t0  TCP *:10000 (LISTEN)
/usr/sbin  3887         root    5u  IPv4  16848      0t0  TCP 127.0.0.1:783 (LISTEN)
spamd      3888         root    5u  IPv4  16848      0t0  TCP 127.0.0.1:783 (LISTEN)
spamd      3889         root    5u  IPv4  16848      0t0  TCP 127.0.0.1:783 (LISTEN)
apache2    9898     www-data    3u  IPv4  12862      0t0  TCP *:80 (LISTEN)
apache2    9898     www-data    4u  IPv4  12865      0t0  TCP *:8081 (LISTEN)
apache2    9898     www-data    5u  IPv4  12867      0t0  TCP *:8080 (LISTEN)
apache2    9901     www-data    3u  IPv4  12862      0t0  TCP *:80 (LISTEN)
apache2    9901     www-data    4u  IPv4  12865      0t0  TCP *:8081 (LISTEN)
apache2    9901     www-data    5u  IPv4  12867      0t0  TCP *:8080 (LISTEN)
apache2    9902     www-data    3u  IPv4  12862      0t0  TCP *:80 (LISTEN)
apache2    9902     www-data    4u  IPv4  12865      0t0  TCP *:8081 (LISTEN)
apache2    9902     www-data    5u  IPv4  12867      0t0  TCP *:8080 (LISTEN)
apache2    9903     www-data    3u  IPv4  12862      0t0  TCP *:80 (LISTEN)
apache2    9903     www-data    4u  IPv4  12865      0t0  TCP *:8081 (LISTEN)
apache2    9903     www-data    5u  IPv4  12867      0t0  TCP *:8080 (LISTEN)
apache2    9904     www-data    3u  IPv4  12862      0t0  TCP *:80 (LISTEN)
apache2    9904     www-data    4u  IPv4  12865      0t0  TCP *:8081 (LISTEN)
apache2    9904     www-data    5u  IPv4  12867      0t0  TCP *:8080 (LISTEN)
apache2    9905     www-data    3u  IPv4  12862      0t0  TCP *:80 (LISTEN)
apache2    9905     www-data    4u  IPv4  12865      0t0  TCP *:8081 (LISTEN)
apache2    9905     www-data    5u  IPv4  12867      0t0  TCP *:8080 (LISTEN)
apache2    9906     www-data    3u  IPv4  12862      0t0  TCP *:80 (LISTEN)
apache2    9906     www-data    4u  IPv4  12865      0t0  TCP *:8081 (LISTEN)
apache2    9906     www-data    5u  IPv4  12867      0t0  TCP *:8080 (LISTEN)
pop3-logi 10511     dovenull    7u  IPv4   9483      0t0  TCP *:110 (LISTEN)
pop3-logi 10511     dovenull    8u  IPv6   9484      0t0  TCP *:110 (LISTEN)
pop3-logi 10511     dovenull    9u  IPv4   9485      0t0  TCP *:995 (LISTEN)
pop3-logi 10511     dovenull   10u  IPv6   9486      0t0  TCP *:995 (LISTEN)
```

```
ls -la /home
```

```

total 16
drwxr-xr-x  4 root          root         4096 Lis 24 10:52 .
drwxr-xr-x 22 root          root         4096 Lis 24 10:13 ..
drwxr-xr-x 25 xxxxx@xxx.xx  xxxxx@xxx.xx 4096 Lis 29 13:47 xxxxx@xxx.xx
drwxr-xr-x  2 xxxxxx@xxx.xx users        4096 Lis 24 10:47 xxxxx@xxx.xx

```

mail.log is somewhat large, and logs just repeat itself, so I did not copy everything, just a few sessions, hope it is ok.

```
cat /var/log/mail.log
```
```
Nov  2 12:59:04 ubuntu postfix/cleanup[8048]: warning: proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf lookup 

error for "xxxxx@xxx.xx"
Nov  2 12:59:04 ubuntu postfix/cleanup[8048]: warning: B161FC0010: virtual_alias_maps map lookup problem for 

xxxxx@xxx.xx -- deferring delivery
Nov  2 13:00:02 ubuntu postfix/smtpd[10779]: error: unsupported dictionary type: mysql
Nov  2 13:00:02  postfix/smtpd[10779]: last message repeated 4 times
Nov  2 13:00:02 ubuntu postfix/smtpd[10779]: connect from localhost[127.0.0.1]
Nov  2 13:00:02 ubuntu dovecot: imap-login: Disconnected (no auth attempts): rip=127.0.0.1, lip=127.0.0.1, secured
Nov  2 13:00:02 ubuntu dovecot: auth: Fatal: sql: driver not set in configuration file /var/lib/mysql/Mail
Nov  2 13:00:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 13:00:02 ubuntu postfix/smtpd[10779]: fatal: no SASL authentication mechanisms
Nov  2 13:00:03 ubuntu postfix/master[2290]: warning: process /usr/lib/postfix/smtpd pid 10779 exit status 1
Nov  2 13:00:03 ubuntu postfix/master[2290]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Nov  2 13:00:04 ubuntu postfix/pickup[8047]: warning: A06CCC0702: message has been queued for 8 days
Nov  2 13:00:04 ubuntu postfix/pickup[8047]: A06CCC0702: uid=0 from=<root>
Nov  2 13:00:04 ubuntu postfix/cleanup[8048]: A06CCC0702: message-id=<20121102120004.A06CCC0702@ubuntu.vst.hr>
Nov  2 13:00:04 ubuntu postfix/proxymap[9330]: warning: mysql:/etc/postfix/mysql-virtual_forwardings.cf is 
unavailable. unsupported dictionary type: mysql
Nov  2 13:00:04 ubuntu postfix/cleanup[8048]: warning: proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf lookup 

error for "xxxxx@xxx.xx"
Nov  2 13:00:04 ubuntu postfix/cleanup[8048]: warning: A06CCC0702: virtual_alias_maps map lookup problem for 
xxxxx@xxx.xx -- deferring delivery
Nov  2 13:00:37 ubuntu dovecot: pop3-login: Error: Timeout waiting for handshake from auth server. my pid=10780, 

input bytes=0

```

This one is even bigger...


```
cat /var/log/mail.err
```
```
Nov  2 12:11:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 12:11:32 ubuntu dovecot: pop3-login: Error: Timeout waiting for handshake from auth server. my pid=9059, 

input bytes=0
Nov  2 12:12:02 ubuntu dovecot: pop3-login: Error: Timeout waiting for handshake from auth server. my pid=9059, 

input bytes=0
Nov  2 12:12:02 ubuntu dovecot: auth: Fatal: sql: driver not set in configuration file /var/lib/mysql/Mail
Nov  2 12:12:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 12:12:37 ubuntu dovecot: pop3-login: Error: Timeout waiting for handshake from auth server. my pid=9059, 

input bytes=0
Nov  2 12:13:02 ubuntu dovecot: auth: Fatal: sql: driver not set in configuration file /var/lib/mysql/Mail
Nov  2 12:13:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 12:15:02 ubuntu postfix/smtpd[9187]: error: unsupported dictionary type: mysql
Nov  2 12:15:02  postfix/smtpd[9187]: last message repeated 4 times
Nov  2 12:15:02 ubuntu dovecot: auth: Fatal: sql: driver not set in configuration file /var/lib/mysql/Mail
Nov  2 12:15:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 12:15:02 ubuntu postfix/smtpd[9187]: fatal: no SASL authentication mechanisms
Nov  2 12:15:37 ubuntu dovecot: pop3-login: Error: Timeout waiting for handshake from auth server. my pid=9188, 

input bytes=0
Nov  2 12:16:02 ubuntu dovecot: auth: Fatal: sql: driver not set in configuration file /var/lib/mysql/Mail
Nov  2 12:16:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 12:16:32 ubuntu dovecot: pop3-login: Error: Timeout waiting for handshake from auth server. my pid=9188, 

input bytes=0
Nov  2 12:17:02 ubuntu dovecot: pop3-login: Error: Timeout waiting for handshake from auth server. my pid=9188, 

input bytes=0
Nov  2 12:17:02 ubuntu dovecot: auth: Fatal: sql: driver not set in configuration file /var/lib/mysql/Mail
Nov  2 12:17:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 12:17:37 ubuntu dovecot: pop3-login: Error: Timeout waiting for handshake from auth server. my pid=9188, 

input bytes=0
Nov  2 12:18:02 ubuntu dovecot: auth: Fatal: sql: driver not set in configuration file /var/lib/mysql/Mail
Nov  2 12:18:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 12:20:01 ubuntu postfix/smtpd[9324]: error: unsupported dictionary type: mysql
Nov  2 12:20:01 ubuntu postfix/proxymap[9330]: error: unsupported dictionary type: mysql
Nov  2 12:20:01  postfix/proxymap[9330]: last message repeated 2 times
Nov  2 12:20:01 ubuntu postfix/smtpd[9324]: error: unsupported dictionary type: mysql
Nov  2 12:20:02  postfix/smtpd[9324]: last message repeated 3 times
Nov  2 12:20:02 ubuntu dovecot: auth: Fatal: sql: driver not set in configuration file /var/lib/mysql/Mail
Nov  2 12:20:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 12:20:02 ubuntu postfix/smtpd[9324]: fatal: no SASL authentication mechanisms
Nov  2 12:20:36 ubuntu dovecot: pop3-login: Error: Timeout waiting for handshake from auth server. my pid=9325, 

input bytes=0
Nov  2 12:21:02 ubuntu dovecot: auth: Fatal: sql: driver not set in configuration file /var/lib/mysql/Mail
Nov  2 12:21:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 12:21:32 ubuntu dovecot: pop3-login: Error: Timeout waiting for handshake from auth server. my pid=9325, 

input bytes=0
Nov  2 12:22:02 ubuntu dovecot: pop3-login: Error: Timeout waiting for handshake from auth server. my pid=9325, 

input bytes=0
Nov  2 12:22:02 ubuntu dovecot: auth: Fatal: sql: driver not set in configuration file /var/lib/mysql/Mail
Nov  2 12:22:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 12:22:37 ubuntu dovecot: pop3-login: Error: Timeout waiting for handshake from auth server. my pid=9325, 

input bytes=0
Nov  2 12:23:02 ubuntu dovecot: auth: Fatal: sql: driver not set in configuration file /var/lib/mysql/Mail
Nov  2 12:23:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 12:25:01 ubuntu postfix/smtpd[9453]: error: unsupported dictionary type: mysql
Nov  2 12:25:02  postfix/smtpd[9453]: last message repeated 4 times
Nov  2 12:25:02 ubuntu dovecot: auth: Fatal: sql: driver not set in configuration file /var/lib/mysql/Mail
Nov  2 12:25:02 ubuntu dovecot: master: Error: service(auth): command startup failed, throttling
Nov  2 12:25:02 ubuntu postfix/smtpd[9453]: fatal: no SASL authentication mechanisms
```

```
ls -la /var/mail
```

```
total 12
drwxrwsr-x  2 root         mail 4096 Lis 24 10:51 .
drwxr-xr-x 16 root         root 4096 Lis 29 16:06 ..
-rw-rw----  1 xxxxx@xxx.xx mail  445 Lis 24 10:51 xxxxx
```

```
ls -la /var/spool/postfix
```
```
total 80
drwxr-xr-x 20 root    root     4096 Lis 22 11:17 .
drwxr-xr-x 11 root    root     4096 Lis 23 15:11 ..
drwx------  2 postfix root     4096 Lis 24 10:51 active
drwx------  2 postfix root     4096 Lis 19 15:55 bounce
drwx------  2 postfix root     4096 Lis 19 15:55 corrupt
drwx------  2 postfix root     4096 Lis 19 15:55 defer
drwx------  2 postfix root     4096 Lis 19 15:55 deferred
drwxr-xr-x  2 root    root     4096 Stu  2 08:11 dev
drwxr-xr-x  3 root    root     4096 Stu  2 08:11 etc
drwx------  2 postfix root     4096 Lis 19 15:55 flush
drwx------  2 postfix root     4096 Lis 19 14:07 hold
drwx------  2 postfix root     4096 Stu  2 13:04 incoming
drwxr-xr-x  3 root    root     4096 Stu  2 08:11 lib
drwx-wx--T  2 postfix postdrop 4096 Lis 24 14:28 maildrop
drwxr-xr-x  2 root    root     4096 Lis 24 10:51 pid
drwx------  2 postfix root     4096 Stu  2 08:11 private
drwx--s---  2 postfix postdrop 4096 Stu  2 08:11 public
drwx------  2 postfix root     4096 Lis 19 15:55 saved
drwx------  2 postfix root     4096 Lis 19 14:07 trace
drwxr-xr-x  3 root    root     4096 Lis 19 15:41 usr

```

There is no log file from Postfix, this is everything that is in the /var/log


```
alternatives.log    btmp.1        dmesg.3.gz      ispconfig              mail.err        mysql.log.3.gz      samba              syslog.7.gz
alternatives.log.1  clamav        dmesg.4.gz      ispconfig_install.log  mail.err.1      mysql.log.4.gz      speech-dispatcher  udev
apache2             ConsoleKit    dpkg.log        jockey.log             mail.log        mysql.log.5.gz      syslog             ufw.log
apt                 cups          dpkg.log.1      jockey.log.1           mail.log.1      mysql.log.6.gz      syslog.1           unattended-upgrades
auth.log            dist-upgrade  faillog         kern.log               mysql           mysql.log.7.gz      syslog.2.gz        upstart
auth.log.1          dmesg         fontconfig.log  kern.log.1             mysql.err       news                syslog.3.gz        wtmp
boot                dmesg.0       fsck            landscape              mysql.log       pm-powersave.log    syslog.4.gz        wtmp.1
boot.log            dmesg.1.gz    hp              lastlog                mysql.log.1.gz  pm-powersave.log.1  syslog.5.gz        Xorg.0.log
btmp                dmesg.2.gz    installer       lightdm                mysql.log.2.gz  postgresql          syslog.6.gz        Xorg.0.log.old

```

```
telnet localhost 25
```

```
xxxxx@xxx.xx@ubuntu:/var/log$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
```


```
ehlo localhost
```
It says command not found, which is strange as I know I tried it before, and it worked...?

This one just hangs, tried it before, same thing now.

```
telnet localhost imap
```
```
root@ubuntu:/var/log# telnet localhost imap
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK Waiting for authentication process to respond..
* BYE Disconnected for inactivity.
Connection closed by foreign host.
```

Netcat command isn`t working, it just hangs and hangs, and after some time new line appears like nothing was issued.

When I use adduser command, new user appears in the system, but when I tried to log with that credentials through Squirrelmail, it just says unknown user or password is not correct.

It seems nothing works... :)
Maybe to start all over, format the disc, new installation and use mlentink link for the tutorial...

---

