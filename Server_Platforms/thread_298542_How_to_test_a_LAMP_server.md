---
title: "How to test a LAMP server"
date: 2006-11-12
forum: Server Platforms
---

### Post by satimis on 2006-11-12
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64


I have the said server installed and configured.  The server is now running.

$ ps -ef | egrep '/mysql|postfix|portmap|apache2'```

daemon    3513     1  0 09:56 ?        00:00:00 /sbin/portmap -i
127.0.0.1
root      4022     1  0 09:56 ?        00:00:00 /bin/sh
/usr/bin/mysqld_safe
mysql     4086  4022  0 09:56 ?        00:00:00 /usr/sbin/mysqld
--basedir=/usr --datadir=/var/lib/mysql --user=mysql
--pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306
--socket=/var/run/mysqld/mysqld.sock
root      4254     1  0 09:56 ?        00:00:00 /usr/sbin/saslauthd -m
/var/spool/postfix/var/run/saslauthd -a pam
root      4255  4254  0 09:56 ?        00:00:00 /usr/sbin/saslauthd -m
/var/spool/postfix/var/run/saslauthd -a pam
root      4256  4254  0 09:56 ?        00:00:00 /usr/sbin/saslauthd -m
/var/spool/postfix/var/run/saslauthd -a pam
root      4257  4254  0 09:56 ?        00:00:00 /usr/sbin/saslauthd -m
/var/spool/postfix/var/run/saslauthd -a pam
root      4258  4254  0 09:56 ?        00:00:00 /usr/sbin/saslauthd -m
/var/spool/postfix/var/run/saslauthd -a pam
root      4430     1  0 09:56 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  4468  4430  0 09:56 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  4469  4430  0 09:56 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  4470  4430  0 09:56 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  4471  4430  0 09:56 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  4472  4430  0 09:56 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
satimis   4906  4836  0 10:35 pts/2    00:00:00 grep -E
/mysql|postfix|portmap|apache2

```

$ sudo iptables --list```

Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
TCPMSS     tcp  --  anywhere             anywhere            tcp
flags:SYN,RST/SYN tcpmss match 1400:1536 TCPMSS clamp to PMTU

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```



Please advise how to test this server?  Where can I find appropriate
documents on testing a LAMP server?

1)
Self test


2)
Testing with a workstation

I don't have router so I'll install an additional network card on the
server and connect it with a  Cat5 cable to the workstation (one network
card on workstation).  OR is there any other suggestions?  TIA


3)
Testing on Internet.

I don't have Domain nor Static IP.  I'll register a free Domain later
for this test and use Dynamic IP.


Now my problem is I have only on broadband.  Connecting the workstation to Internet via a modem?  I have modem available.


Advice will be appreciated.  Tks.


B.R.
satimis

---

### Post by moephan on 2006-11-12
I'm not 100% certain what you are trying to test. The most basic thing is that you can navigate your browser to [http://127.0.0.1/](http://127.0.0.1/). This is always the ip address of your local machine. If Apache is running, you should get a default page.

Cheers, Rick

---

### Post by satimis on 2006-11-12
Hi Rick,

Tks for your advice.

> The most basic thing is that you can navigate your browser to [http://127.0.0.1/](http://127.0.0.1/). This is always the ip address of your local machine. If Apache is running, you should get a default page.

On firefox ran "http://127.0.0.1/".  It hung there for prolonged time without the default page popup.


$ ps -ef | egrep /apache2```

root      5064     1  0 11:26 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  5066  5064  0 11:26 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  5067  5064  0 11:26 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  5068  5064  0 11:26 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  5069  5064  0 11:26 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  5070  5064  0 11:26 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
satimis   5077  4836  0 11:30 pts/2    00:00:00 grep -E /apache2

```

$ sudo /etc/init.d/apache2 restart```

 * Forcing reload of apache 2.0 web server... apache2: Could not
determine the server's fully qualified domain name, using 127.0.1.1 for
ServerName
apache2: Could not determine the server's fully qualified domain name,
using 127.0.1.1 for ServerName
                                                                       
      [ ok ]
```


Apache2 is running.

Also tried "http://127.0.1.1/", still the same only hanging.


B.R.
satimis

---

### Post by rickyjones on 2006-11-13
Did you test "127.0.0.1" on the SERVER or on your WORKSTATION? Because obviously it won't work on your workstation. Do you have switch to use at your house? Because if you do then you could connect both PC's (if you have two, that is) to the LAN and test that way...

---

### Post by satimis on 2006-11-13
Hi rickyjones,

> Did you test "127.0.0.1" on the SERVER or on your WORKSTATION?
On the server.  At the first stage of testing, I haven't connected the server to a workstation yet.

$ ps -ef | egrep /apache2```

root      5064     1  0 11:26 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  5066  5064  0 11:26 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  5067  5064  0 11:26 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  5068  5064  0 11:26 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  5069  5064  0 11:26 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
www-data  5070  5064  0 11:26 ?        00:00:00 /usr/sbin/apache2 -k
start -DSSL
satimis   5077  4836  0 11:30 pts/2    00:00:00 grep -E /apache2

```

Apache is running.


$ cat /var/log/apache2/error.log```

....
[Thu Oct 19 03:36:00 2006] [notice] caught SIGTERM, shutting down
[Thu Oct 19 03:36:57 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2
configured -- resuming normal operations
[Thu Oct 19 03:39:44 2006] [notice] caught SIGTERM, shutting down
[Thu Oct 19 03:40:41 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2
configured -- resuming normal operations
[Thu Oct 19 03:41:42 2006] [notice] caught SIGTERM, shutting down
[Thu Oct 19 03:42:39 2006] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.2
configured -- resuming normal operations
[Thu Oct 19 04:01:11 2006] [notice] caught SIGTERM, shutting down

```

$ cat /etc/apache2/ports.conf```

Listen 80
Listen 44

```


Are there other basic tests on Apache2?  TIA

> Do you have switch to use at your house? Because if you do then you could connect both PC's (if you have two, that is) to the LAN and test that way...
No.  Neither I have a router.  On the second stage of testing I'll install an additional network card on the server and then connect it to the workstation with a CAT-5 cable,  Hoping that this arrangement can solve my problem.

Tks.

B.R.
satimis

---

### Post by Ride Jib on 2006-11-13
ensure apache is actually listening:
```

netstat -ptan | grep apache

```

---

### Post by satimis on 2006-11-13
Hi Ride,

> ensure apache is actually listening:
```

netstat -ptan | grep apache

```

$ sudo netstat -ptan | grep apache```

tcp6       0      0 :::44                   :::*                    LISTEN     4430/apache2
tcp6       0      0 :::80                   :::*                    LISTEN     4430/apache2

```

$ sudo netstat -ptan | grep apache2```

Password:
tcp6       0      0 :::44                   :::*                    LISTEN     4430 /apache2
tcp6       0      0 :::80                   :::*                    LISTEN     4430 /apache2

```

The same.

Tks.

satimis

---

