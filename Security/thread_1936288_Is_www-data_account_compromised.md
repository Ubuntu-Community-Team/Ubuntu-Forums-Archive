---
title: "Is www-data account compromised?"
date: 2012-03-05
forum: Security
---

### Post by wjrhee77 on 2012-03-05
Hello,

I'm hoping someone can help me sleep a bit better tonight.

```

$sudo /var/log/auth.log
....
Mar  5 11:15:44 dev su[6211]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/2 ruser=www-data rhost=  user=root
Mar  5 11:15:47 dev su[6211]: pam_authenticate: Authentication failure
Mar  5 11:15:47 dev su[6211]: [COLOR="Red"]FAILED su for root by www-data[/COLOR]
Mar  5 11:15:47 dev su[6211]: - /dev/pts/2 www-data:root
...

```

So it seems www-data has been trying to su into root.  From my understanding www-data is used by apache daemon.  Does this mean someone already has access to www-data, and trying to su into root????   

Any pointers/advices/experiences would be greatly appreciated.

I'm running 10.04.3 LTS 64bit as VM on ESXi 4.1.0 on Dell PE 2950, LAMP setup.

matt_symes has been helping me from this link : [http://ubuntuforums.org/showthread.php?t=1936143](http://ubuntuforums.org/showthread.php?t=1936143)

---

### Post by Ms. Daisy on 2012-03-05
Until the cavalry arrives, have you read the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812") in this forum (scroll down to the Running Servers section and then the Forensics section)?

And you can look at the [Did I Just Get Owned]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned") wiki for signs of compromise in your logs.

---

### Post by Dangertux on 2012-03-05
You are correct in assuming that this is not normal behavior. You are also correct in assuming that that www-data is used by Apache.

This is highly indicative of a compromise, however there are a few unanswered questions.

1 - Are you the only one with physical access to this machine/ do you have physical access to this machine?

2 - Can you please post the output of the following commands. (these should be performed with root privileges)

```

grep "1=1" /var/log/apache2/access_log
grep -i "[a-z]=[a-z]" /var/log/apache2/access_log
grep -i "and" /var/log/apache2/access_log
grep -i "insert" /var/log/apache2/access_log

```

```

grep www-data /var/log/auth.log

``````

grep "Invalid user" /var/log/auth.log

``````

grep "www-data" /etc/passwd

```
3 - What other internet facing services are running on this system (I assume SSH is it using keys? Or do you have strong passwords?)


Hope this helps.

---

### Post by Diametric on 2012-03-06
Hmmm....while I am still very much learning about how various system process frequently log in as root, what is the difference between what the OP submitted, and the following from my own auth.log file?

Mar  6 03:10:33 my-box su[19363]: Successful su for nxpgsql by root
Mar  6 03:10:33 my-box su[19363]: + ??? root:nxpgsql
Mar  6 03:10:33 my-box su[19363]: pam_unix(su:session): session opened for user nxpgsql by (uid=0)
Mar  6 03:10:33 my-box su[19363]: pam_unix(su:session): session closed for user nxpgsql



Thank you!

---

### Post by wjrhee77 on 2012-03-06
> **Dangertux said:**
> 
1 - Are you the only one with physical access to this machine/ do you have physical access to this machine?

I do have physical access to this machine.  Two other users have access.

> **Dangertux said:**
> 
3 - What other internet facing services are running on this system (I assume SSH is it using keys? Or do you have strong passwords?)

This is internet facing web server having Apache, FTP, webmin, and SSH(not using keys, however) accessible. I've blocked SSH from outside which seemed to have stopped brute force attacks for now.  Website is PHP5 based using javascripts and ajaxy.  

For #2, I will post up some results of those commands in a bit.
Feeling happier already knowing people are willing to help.  Thank you thank you!

---

### Post by spynappels on 2012-03-06
I would seriously look at the PHP code and check for exploits which could be used to get a shell as www-data which then is used to try and elevate privileges. This is especially the case if you use a MySQL database in the backend, think SQL injection attack.

---

### Post by Dangertux on 2012-03-06
> **spynappels said:**
> I would seriously look at the PHP code and check for exploits which could be used to get a shell as www-data which then is used to try and elevate privileges. This is especially the case if you use a MySQL database in the backend, think SQL injection attack.

Yeah this is my guess of what happened (hence some of the search strings I asked about).

I'm thinking what probably happened was 

SQL injection of php shelll , trigger it with with curl enjoy interactive shell... That's pretty common these days.

Still there is no conclusive evidence to support this yet...

---

### Post by wjrhee77 on 2012-03-06
Following up on #2 from Dangertux

> **Dangertux said:**
> 
2 - Can you please post the output of the following commands. (these should be performed with root privileges)


```

grep "1=1" /var/log/apache2/access.log

No results

```


```

grep -i "[a-z]=[a-z]" /var/log/apache2/access.log

Results are long.  Looking over, everything seems ok, not too sure.
Timestamps are normal, within business hours not in the middle of the night.  

```


```

grep -i "and" /var/log/apache2/access.log.1

...
199.21.99.116 - - [27/Feb/2012:21:57:49 -0800] "GET /robots.txt HTTP/1.1" 404 550 "-" "Mozilla/5.0 (compatible; YandexBot/3.0; +http://yandex.com/bots)"
199.21.99.116 - - [28/Feb/2012:03:34:29 -0800] "GET / HTTP/1.1" 302 522 "-" "Mozilla/5.0 (compatible; YandexBot/3.0; +http://yandex.com/bots)"
199.21.99.116 - - [28/Feb/2012:03:34:32 -0800] "GET /new/index.php HTTP/1.1" 302 556 "-" "Mozilla/5.0 (compatible; YandexBot/3.0; +http://yandex.com/bots)"
199.21.99.116 - - [28/Feb/2012:03:34:34 -0800] "GET /login.php HTTP/1.1" 302 316 "-" "Mozilla/5.0 (compatible; YandexBot/3.0; +http://yandex.com/bots)"
199.21.99.116 - - [28/Feb/2012:03:34:36 -0800] "GET /mlogin.php HTTP/1.1" 200 1581 "-" "Mozilla/5.0 (compatible; YandexBot/3.0; +http://yandex.com/bots)"
...

Nothing that stands out for me...  
But there are several results from yandex(?) shown above.
It seems like Russian search engine bots(?)
Mr Putin after me!?

```


```

grep -i "insert" /var/log/apache2/access.log
grep -i "insert" /var/log/apache2/access.log.1

No results

```

```

grep www-data /var/log/auth.log.1

...
Feb 28 00:53:29 dev sshd[8817]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=70.34.198.82  user=www-data
Feb 28 00:53:31 dev sshd[8817]: Failed password for www-data from 70.34.198.82 port 33926 ssh2
Feb 29 04:43:58 dev sshd[30035]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=177.99.189.162  user=www-data
Feb 29 04:44:00 dev sshd[30035]: Failed password for www-data from 177.99.189.162 port 34688 ssh2
Feb 29 04:44:02 dev sshd[30037]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=177.99.189.162  user=www-data
Feb 29 04:44:04 dev sshd[30037]: Failed password for www-data from 177.99.189.162 port 35128 ssh2
Mar  2 11:57:55 dev su[885]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  2 11:57:58 dev su[885]: FAILED su for root by www-data
Mar  2 11:57:58 dev su[885]: - /dev/pts/0 www-data:root
Mar  2 11:57:58 dev su[889]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  2 11:58:00 dev su[889]: FAILED su for root by www-data
Mar  2 11:58:00 dev su[889]: - /dev/pts/0 www-data:root
Mar  2 11:58:00 dev su[890]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  2 11:58:02 dev su[890]: FAILED su for root by www-data
Mar  2 11:58:02 dev su[890]: - /dev/pts/0 www-data:root
Mar  2 11:58:02 dev su[891]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  2 11:58:04 dev su[891]: FAILED su for root by www-data
...

"FAILED su for root by www-data" goes on and on

```

```

grep www-data /var/log/auth.log
...
Mar  4 11:41:30 dev su[24462]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  4 11:41:32 dev su[24462]: FAILED su for root by www-data
Mar  4 11:41:32 dev su[24462]: - /dev/pts/0 www-data:root
Mar  4 11:41:32 dev su[24463]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  4 11:41:34 dev su[24463]: FAILED su for root by www-data
Mar  4 11:41:34 dev su[24463]: - /dev/pts/0 www-data:root
Mar  4 11:41:35 dev su[24464]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  4 11:41:36 dev su[24464]: FAILED su for root by www-data
Mar  4 11:41:36 dev su[24464]: - /dev/pts/0 www-data:root
Mar  5 01:38:01 dev CRON[29947]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Mar  5 01:38:01 dev CRON[29947]: pam_unix(cron:session): session closed for user www-data
Mar  5 01:39:01 dev CRON[30026]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Mar  5 01:39:01 dev CRON[30026]: pam_unix(cron:session): session closed for user www-data
Mar  5 01:40:01 dev CRON[30098]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Mar  5 01:40:01 dev CRON[30098]: pam_unix(cron:session): session closed for user www-data
Mar  5 01:41:01 dev CRON[30126]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Mar  5 01:41:01 dev CRON[30126]: pam_unix(cron:session): session closed for user www-data
Mar  5 01:42:01 dev CRON[30134]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Mar  5 01:42:01 dev CRON[30134]: pam_unix(cron:session): session closed for user www-data
Mar  5 01:43:01 dev CRON[30165]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Mar  5 01:43:01 dev CRON[30165]: pam_unix(cron:session): session closed for user www-data
...

Then I started seeing "dev CRON: pam_unix(cron:session)..."
Is this normal??  I do have some cron jobs but not sure why www-data account would be accessing it, and so many sessions.
:confused:


```

```

grep "Invalid user" /var/log/auth.log & auth.log.1

...
ar  4 11:26:08 dev sshd[24157]: Invalid user tester from 209.105.244.144
Mar  4 11:26:12 dev sshd[24159]: Invalid user testing from 209.105.244.144
Mar  4 11:26:24 dev sshd[24163]: Invalid user postgres from 209.105.244.144
Mar  4 11:26:28 dev sshd[24165]: Invalid user student from 209.105.244.144
Mar  4 11:26:30 dev sshd[24167]: Invalid user student from 209.105.244.144
Mar  4 11:26:33 dev sshd[24169]: Invalid user postgres from 209.105.244.144
Mar  4 11:26:37 dev sshd[24171]: Invalid user linux from 209.105.244.144
Mar  4 11:26:40 dev sshd[24173]: Invalid user upload from 209.105.244.144
Mar  4 11:26:47 dev sshd[24177]: Invalid user cyrus from 209.105.244.144
Mar  4 11:26:50 dev sshd[24179]: Invalid user test1 from 209.105.244.144
Mar  4 11:26:54 dev sshd[24181]: Invalid user test1 from 209.105.244.144
Mar  4 11:26:58 dev sshd[24184]: Invalid user test1 from 209.105.244.144
Mar  4 11:27:01 dev sshd[24186]: Invalid user nagios from 209.105.244.144
Mar  4 11:27:05 dev sshd[24188]: Invalid user prueba from 209.105.244.144
Mar  4 11:27:09 dev sshd[24190]: Invalid user ftpuser from 209.105.244.144
Mar  4 11:27:12 dev sshd[24192]: Invalid user webadmin from 209.105.244.144
Mar  4 12:37:08 dev sshd[24835]: Invalid user sjobeck from 91.205.189.27
Mar  4 12:37:16 dev sshd[24839]: Invalid user asterisk from 91.205.189.27
Mar  4 16:32:09 dev sshd[26329]: Invalid user zt from 219.140.165.85
....

lots and lots of invalid user attemtps from several different ip
:(

```

```

grep "www-data" /etc/passwd

www-data:x:33:33:www-data:/var/www:/bin/sh


```

Well, hope this can provide some light on whats going on... Worst case scenario, at least i can learn from it.

Again, I appreciate your eyes on this.  Thank you, Thank you.

---

### Post by wjrhee77 on 2012-03-06
> **spynappels said:**
> I would seriously look at the PHP code and check for exploits which could be used to get a shell as www-data which then is used to try and elevate privileges. This is especially the case if you use a MySQL database in the backend, think SQL injection attack.

In this case, even tho I've blocked SSH access, I am still vunerable.  There are thousands of lines of code...  Where or how do I start checking for PHP exploits?  My eyes are getting blurry just thinking about how to go about this.  ](*,)

---

### Post by Dangertux on 2012-03-06
> **wjrhee77 said:**
> Following up on #2 from Dangertux



```

grep "1=1" /var/log/apache2/access.log

No results

```
```

grep -i "[a-z]=[a-z]" /var/log/apache2/access.log

Results are long.  Looking over, everything seems ok, not too sure.
Timestamps are normal, within business hours not in the middle of the night.  

```
```

grep -i "and" /var/log/apache2/access.log.1

...
199.21.99.116 - - [27/Feb/2012:21:57:49 -0800] "GET /robots.txt HTTP/1.1" 404 550 "-" "Mozilla/5.0 (compatible; YandexBot/3.0; +http://yandex.com/bots)"
199.21.99.116 - - [28/Feb/2012:03:34:29 -0800] "GET / HTTP/1.1" 302 522 "-" "Mozilla/5.0 (compatible; YandexBot/3.0; +http://yandex.com/bots)"
199.21.99.116 - - [28/Feb/2012:03:34:32 -0800] "GET /new/index.php HTTP/1.1" 302 556 "-" "Mozilla/5.0 (compatible; YandexBot/3.0; +http://yandex.com/bots)"
199.21.99.116 - - [28/Feb/2012:03:34:34 -0800] "GET /login.php HTTP/1.1" 302 316 "-" "Mozilla/5.0 (compatible; YandexBot/3.0; +http://yandex.com/bots)"
199.21.99.116 - - [28/Feb/2012:03:34:36 -0800] "GET /mlogin.php HTTP/1.1" 200 1581 "-" "Mozilla/5.0 (compatible; YandexBot/3.0; +http://yandex.com/bots)"
...

Nothing that stands out for me...  
But there are several results from yandex(?) shown above.
It seems like Russian search engine bots(?)
Mr Putin after me!?

```
```

grep -i "insert" /var/log/apache2/access.log
grep -i "insert" /var/log/apache2/access.log.1

No results

``````

grep www-data /var/log/auth.log.1

...
Feb 28 00:53:29 dev sshd[8817]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=70.34.198.82  user=www-data
Feb 28 00:53:31 dev sshd[8817]: Failed password for www-data from 70.34.198.82 port 33926 ssh2
Feb 29 04:43:58 dev sshd[30035]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=177.99.189.162  user=www-data
Feb 29 04:44:00 dev sshd[30035]: Failed password for www-data from 177.99.189.162 port 34688 ssh2
Feb 29 04:44:02 dev sshd[30037]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=177.99.189.162  user=www-data
Feb 29 04:44:04 dev sshd[30037]: Failed password for www-data from 177.99.189.162 port 35128 ssh2
Mar  2 11:57:55 dev su[885]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  2 11:57:58 dev su[885]: FAILED su for root by www-data
Mar  2 11:57:58 dev su[885]: - /dev/pts/0 www-data:root
Mar  2 11:57:58 dev su[889]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  2 11:58:00 dev su[889]: FAILED su for root by www-data
Mar  2 11:58:00 dev su[889]: - /dev/pts/0 www-data:root
Mar  2 11:58:00 dev su[890]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  2 11:58:02 dev su[890]: FAILED su for root by www-data
Mar  2 11:58:02 dev su[890]: - /dev/pts/0 www-data:root
Mar  2 11:58:02 dev su[891]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  2 11:58:04 dev su[891]: FAILED su for root by www-data
...

"FAILED su for root by www-data" goes on and on

``````

grep www-data /var/log/auth.log
...
Mar  4 11:41:30 dev su[24462]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  4 11:41:32 dev su[24462]: FAILED su for root by www-data
Mar  4 11:41:32 dev su[24462]: - /dev/pts/0 www-data:root
Mar  4 11:41:32 dev su[24463]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  4 11:41:34 dev su[24463]: FAILED su for root by www-data
Mar  4 11:41:34 dev su[24463]: - /dev/pts/0 www-data:root
Mar  4 11:41:35 dev su[24464]: pam_unix(su:auth): authentication failure; logname= uid=33 euid=0 tty=/dev/pts/0 ruser=www-data rhost=  user=root
Mar  4 11:41:36 dev su[24464]: FAILED su for root by www-data
Mar  4 11:41:36 dev su[24464]: - /dev/pts/0 www-data:root
Mar  5 01:38:01 dev CRON[29947]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Mar  5 01:38:01 dev CRON[29947]: pam_unix(cron:session): session closed for user www-data
Mar  5 01:39:01 dev CRON[30026]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Mar  5 01:39:01 dev CRON[30026]: pam_unix(cron:session): session closed for user www-data
Mar  5 01:40:01 dev CRON[30098]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Mar  5 01:40:01 dev CRON[30098]: pam_unix(cron:session): session closed for user www-data
Mar  5 01:41:01 dev CRON[30126]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Mar  5 01:41:01 dev CRON[30126]: pam_unix(cron:session): session closed for user www-data
Mar  5 01:42:01 dev CRON[30134]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Mar  5 01:42:01 dev CRON[30134]: pam_unix(cron:session): session closed for user www-data
Mar  5 01:43:01 dev CRON[30165]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Mar  5 01:43:01 dev CRON[30165]: pam_unix(cron:session): session closed for user www-data
...

Then I started seeing "dev CRON: pam_unix(cron:session)..."
Is this normal??  I do have some cron jobs but not sure why www-data account would be accessing it, and so many sessions.
:confused:


``````

grep "Invalid user" /var/log/auth.log & auth.log.1

...
ar  4 11:26:08 dev sshd[24157]: Invalid user tester from 209.105.244.144
Mar  4 11:26:12 dev sshd[24159]: Invalid user testing from 209.105.244.144
Mar  4 11:26:24 dev sshd[24163]: Invalid user postgres from 209.105.244.144
Mar  4 11:26:28 dev sshd[24165]: Invalid user student from 209.105.244.144
Mar  4 11:26:30 dev sshd[24167]: Invalid user student from 209.105.244.144
Mar  4 11:26:33 dev sshd[24169]: Invalid user postgres from 209.105.244.144
Mar  4 11:26:37 dev sshd[24171]: Invalid user linux from 209.105.244.144
Mar  4 11:26:40 dev sshd[24173]: Invalid user upload from 209.105.244.144
Mar  4 11:26:47 dev sshd[24177]: Invalid user cyrus from 209.105.244.144
Mar  4 11:26:50 dev sshd[24179]: Invalid user test1 from 209.105.244.144
Mar  4 11:26:54 dev sshd[24181]: Invalid user test1 from 209.105.244.144
Mar  4 11:26:58 dev sshd[24184]: Invalid user test1 from 209.105.244.144
Mar  4 11:27:01 dev sshd[24186]: Invalid user nagios from 209.105.244.144
Mar  4 11:27:05 dev sshd[24188]: Invalid user prueba from 209.105.244.144
Mar  4 11:27:09 dev sshd[24190]: Invalid user ftpuser from 209.105.244.144
Mar  4 11:27:12 dev sshd[24192]: Invalid user webadmin from 209.105.244.144
Mar  4 12:37:08 dev sshd[24835]: Invalid user sjobeck from 91.205.189.27
Mar  4 12:37:16 dev sshd[24839]: Invalid user asterisk from 91.205.189.27
Mar  4 16:32:09 dev sshd[26329]: Invalid user zt from 219.140.165.85
....

lots and lots of invalid user attemtps from several different ip
:(

``````

grep "www-data" /etc/passwd

www-data:x:33:33:www-data:/var/www:/bin/sh


```Well, hope this can provide some light on whats going on... Worst case scenario, at least i can learn from it.

Again, I appreciate your eyes on this.  Thank you, Thank you.


I'm not going to lie, unless you (or one of the other individuals attempted to sudo from www-data... You're probably compromised.

One more command

```

grep "Mar 1" /var/log/auth.log

```

---

### Post by wjrhee77 on 2012-03-06
> **Dangertux said:**
> I'm not going to lie, unless you (or one of the other individuals attempted to sudo from www-data... You're probably compromised.

One more command

```

grep "Mar 1" /var/log/auth.log

```

Yea nothing comes up.  Those days are missing.  I thought that was kind of weird.

More definite answer...

```

won@dev:/etc/apache2$ sudo netstat -tap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:saft                  *:*                     LISTEN      870/inetd
tcp        0      0 *:mysql                 *:*                     LISTEN      851/mysqld
tcp        0      0 *:webmin                *:*                     LISTEN      12865/perl
tcp        0      0 *:www                   *:*                     LISTEN      5508/apache2
tcp        0      0 *:ssh                   *:*                     LISTEN      798/sshd
tcp        0      0 localhost:smtp          *:*                     LISTEN      967/master
tcp        0      0 dev.mydomain.com:ssh   192.168.0.254:49625     ESTABLISHED 6888/sshd: won [pri
tcp        0     52 dev.mydomain.com:ssh   192.168.0.254:61331     ESTABLISHED 2990/sshd: won [pri
tcp        0      0 dev.mydomain.com:webmin 192.168.0.254:58178     ESTABLISHED 19727/perl
tcp        0      0 dev.mydomain.com:44233 wei80.weightfinerhy:www ESTABLISHED 15547/httpd
tcp        0      0 dev.mydomain.com:webmin 192.168.0.254:58173     ESTABLISHED 19721/perl
tcp        0      0 dev.mydomain.com:33245 89.44.111.22:www        ESTABLISHED 13348/klogd -x
tcp        0      0 dev.mydomain.com:mysql 181.164.132.206.s:39119 TIME_WAIT   -
tcp        0      0 dev.mydomain.com:webmin 192.168.0.254:58179     ESTABLISHED 19728/perl
tcp        0      1 dev.mydomain.com:42058 ns1.leoburnett.ro:www   SYN_SENT    14474/httpd
tcp        0      0 dev.mydomain.com:33442 wei80.weightfinerhy:www ESTABLISHED 5460/httpd
tcp        0      0 dev.mydomain.com:51883 coliseum-shop.co:telnet ESTABLISHED 17114/httpd
tcp        0      0 dev.mydomain.com:40411 static.104.68.40.1:ircd ESTABLISHED 15698/httpd -DSSL


```

Yuk... Bunch of ****

Thank you for walking me through this.
Now, the daunting task of trying to figure out where the exploits are.  This is a dev server so not too much damage but really need to fix it since almost identical codes are available to public.  

Thank

---

### Post by Dangertux on 2012-03-06
Yeah... That's owned...

Sorry :-(

Might I suggest a web application firewall like mod-security in the future? Obviously correcting insecure code is by far the best option, however a backup plan is always a good idea.

Good luck!

---

### Post by Porcini M. on 2012-03-07
May I suggest subjecting your site to analysis by the "w3af" tool? It's in the ubuntu repositories. It barrages it with a slew of known exploits & reports the vulnerabilities.

---

### Post by spynappels on 2012-03-07
> **Porcini M. said:**
> May I suggest subjecting your site to analysis by the "w3af" tool? It's in the ubuntu repositories. It barrages it with a slew of known exploits & reports the vulnerabilities.

I was going to recommend using Backtrack to test for vulnerabilities, but the above package may be easier! 

Some sort of vulnerability analysis is definitely required along with the Apache module Dangertux recommended.

---

### Post by OpSecShellshock on 2012-03-07
Sorry this happened, but I would caution that you should probably check out other servers and possibly workstations in your environment as well. This seems to have been a non-production server, which is a relief, but the fact is that it was accessible from the web. Are there others which are similar? They should be checked out. Is it possible, even if only on the internal network, to communicate with production servers or other servers directly from this development server? If so then I think you have to assume someone would have tried. Checking for that will be trickier because since it's all internal it will all appear normal. Would be a good idea to check your internal communications for access attempts coming from the development server and going to other machines on your network.

If the only compromised account was www-data and they couldn't escalate from there, it may decrease the risk a bit, but if the www-data user account was trying to authenticate to other devices that would be suspicious anyway.

---

### Post by Dangertux on 2012-03-07
In line with what OpSec said...There is another problem here.

By default www-data should not have a shell, the snippet from your passwd file indicates that it does have a shell (/bin/sh)

Did you add this?

If not there is the potential a higher level account was compromised.

Hope this helps.

---

### Post by Grenage on 2012-03-07
> **Dangertux said:**
> By default www-data should not have a shell, the snippet from your passwd file indicates that it does have a shell (/bin/sh)

My default install does?

---

### Post by Lars Noodén on 2012-03-07
> **Grenage said:**
> 
Quote:
Originally Posted by Dangertux View Post
By default www-data should not have a shell, the snippet from your passwd file indicates that it does have a shell (/bin/sh)

My default install does?

I've checked several fresh installs of 12.04 and by default www-data does have the shell /bin/sh.  It's not the way I would do it but it is there.  If it's worth filing a bug report, I'll add my 'me, too' to it.

---

### Post by matt_symes on 2012-03-07
Hi

:( Best you know though from the people who do this for a living.

EDIT: Just re-read my post. They don't compromise systems they protect them. Must make that one clear.

Kind regards

---

### Post by Diametric on 2012-03-07
I followed the grep command and have some similar output - can anyone reply with what specifically points to the box being compromised?

Thanks!

---

### Post by Ms. Daisy on 2012-03-07
> **Diametric said:**
> I followed the grep command and have some similar output - can anyone reply with what specifically points to the box being compromised?

Thanks!
I'll give this a shot, (counting on the experts to correct me if I'm wrong)

Signs of compromise:

"FAILED su for root by www-data" goes on and on
followed by successful logons by www-data

lots and lots of invalid user attempts from several different ips

missing log files from the time of the compromise

established ssh connection to/from anywhere you didn't authorize

---

### Post by Diametric on 2012-03-07
> **Ms. Daisy said:**
> I'll give this a shot, (counting on the experts to correct me if I'm wrong)

Signs of compromise:

"FAILED su for root by www-data" goes on and on
followed by successful logons by www-data

lots and lots of invalid user attempts from several different ips

missing log files from the time of the compromise

established ssh connection to/from anywhere you didn't authorize

Thanks for your reply - I appreciate it.  However, I thought it was established that www-data has access to a shell.

I'd post the output of my file, but I've shut the box down and am going to wipe it.  Suffice it to say, I had several services running on the box that I did not monitor...sql...apache etc.  They only port I opened up was 22 for my ssh sessions.  So, I am unsure how access was obtained.  Yikes.

---

### Post by Ms. Daisy on 2012-03-07
> **Diametric said:**
> Thanks for your reply - I appreciate it.  However, I thought it was established that www-data has access to a shell.

I'd post the output of my file, but I've shut the box down and am going to wipe it.  Suffice it to say, I had several services running on the box that I did not monitor...sql...apache etc.  They only port I opened up was 22 for my ssh sessions.  So, I am unsure how access was obtained.  Yikes.
If your logs show tons of failed su attempts, then it's probably a malicious attack. I assume that any legitimate service is not going to brute force your password by default. And no legit service will delete your logs, right?

Check out the [security sticky]("http://ubuntuforums.org/showthread.php?t=510812") for securing ssh. 

> The two most common cracks posted on these forums are ssh and vnc, both running with password authentication.[B] If you wish to run these services, please secure them.

[LIST]
[*]In the case of ssh, use keys (and disable password  authentication) and either configure iptables or use a service such as  denyhosts or fail2ban (both are in the repositories).
[LIST=1]
[*][[COLOR=darkred]Ubuntu Wiki configure SSH[/COLOR]]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")
[*][[COLOR=darkred]Ubuntu wiki SSH Keys[/COLOR]]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")
[*][[COLOR=darkred]DenyHosts[/COLOR]]("http://denyhosts.sourceforge.net/")
[*][[COLOR=darkred]Fail2Ban[/COLOR]]("http://www.fail2ban.org/wiki/index.php/Features")
[*][[COLOR=darkred]bodhi.zazen's iptables primer[/COLOR]]("http://bodhizazen.net/Tutorials/iptables/")
[/LIST]
 
[/LIST]
[/B]

---

### Post by Diametric on 2012-03-07
Thanks for the links - I appreciate your time in replying to my questions.  I found the "did I just get owned" link particularly helpful.  I think I'm going to review all my log files before I re-install to see if I can determine what happened.  

Thanks again...

---

