---
title: "mysql ssl won't enable"
date: 2009-04-10
forum: Server Platforms
---

### Post by reverendryan on 2009-04-10
I'm trying to get SSL enabled for MySQL on one of my servers. I have it enabled on my other server and it was easy enough to do. But for whatever reason, mysqld on this server just won't cooperate. Here's what 

	```
show variables like "%ssl%";
``` gives me:
```

+---------------+-----------------------+
| Variable_name | Value                 |
+---------------+-----------------------+
| have_openssl  | DISABLED              |
| have_ssl      | DISABLED              |
| ssl_ca        | /etc/mysql/ca.crt     |
| ssl_capath    |                       |
| ssl_cert      | /etc/mysql/server.crt |
| ssl_cipher    | DHE-RSA-AES256-SHA    |
| ssl_key       | /etc/mysql/server.key |
+---------------+-----------------------+

```

I've tried verifying my certificate:
```

$ openssl verify -verbose  -CAfile ca.crt server.crt
server.crt: OK

```

And I've tried copying the keys and ssl config to the other server (it works). 

Here's the relevant section of my.cnf:
```

#ssl
ssl-ca=/etc/mysql/ca.crt
ssl-cert=/etc/mysql/server.crt
ssl-key=/etc/mysql/server.key
ssl-cipher=DHE-RSA-AES256-SHA

```

I've tried uncommenting the top "ssl" line but it has no effect. I know this will turn out to be some silly little thing that's been staring me in the face, and any hints, tips, or trick will be greatly appreciated.

---

### Post by BkkBonanza on 2009-04-10
Have a look in the mysql log or post relevant parts here. If it's failing then there should be reasons logged there.

---

### Post by reverendryan on 2009-04-10
I'd been watching /var/log/mysql.err and it's always been empty, but I just noticed a comment in my.cnf saying it would be in the syslog...

Here's what I found: 
```

localhost mysqld[14787]: SSL error: Unable to get certificate from '/etc/mysql/server.crt'
localhost mysqld[14787]: 090409 22:36:59 [Warning] Failed to setup SSL
localhost kernel: [12505738.400344] audit(1239340107.624:15): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/etc/mysql/ca.crt" pid=14206 profile="/usr/sbin/mysqld" namespace="default"
localhost kernel: [12506321.504917] audit(1239340691.683:18): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/etc/mysql/server.crt" pid=14406 profile="/usr/sbin/mysqld" namespace="default"

```

My first thought was that it's a permissions problem, but I don't think so:
```

$ ls -lZ ca.crt server.crt
-rw-r--r--  1 mysql users ? 2431 2009-03-29 00:23 ca.crt
-rw-r--r--  1 mysql users ? 2049 2009-03-29 00:23 server.crt
```

The error almost sounds like an SELinux context issue, but SELinux doesn't seem to be installed.

---

### Post by reverendryan on 2009-04-10
Turns out it was apparmor that was doing it. 

Here's my /etc/apparmor.d/usr.sbin.mysqld, my changes bolded

```

/usr/sbin/mysqld {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/mysql>

  capability dac_override,
  capability setgid,
  capability setuid,

  /etc/hosts.allow r,
  /etc/hosts.deny r,

  /etc/group              m,
  /etc/passwd             m,

  /etc/mysql/*.pem r,
  [B]/etc/mysql/*.crt r,
  /etc/mysql/*.key r,[/B]
  /etc/mysql/conf.d/ r,
  /etc/mysql/conf.d/* r,
  /etc/mysql/my.cnf r,
  /usr/sbin/mysqld mr,
  /usr/share/mysql/** r,
  /var/lib/mysql/ r,
  /var/lib/mysql/** rwk,
  /var/log/mysql/ r,
  /var/log/mysql/* rw,
  /var/run/mysqld/mysqld.pid w,
  /var/run/mysqld/mysqld.sock w,
}
```

---

### Post by BkkBonanza on 2009-04-10
I wonder if that's something new. I've always put my certs in /var/local/ssl/certs and never had any apparmor issues. This could just because you wanted to put them in /etc/mysql and that's now protected. I don't know much about apparmor so just guessing.

---

### Post by angelomadnato on 2009-12-07
I had the same problem and found the ssl-cipher setting I was using was the problem. I'm posting in case anyone else runs into this problem.

```
show variables like "%ssl%";
```for me also resulted in:

```

+---------------+----------------------------+
| Variable_name | Value                      |
+---------------+----------------------------+
| have_openssl  | DISABLED                   |
| have_ssl      | DISABLED                   |
| ssl_ca        | /etc/mysql/ca-cert.pem     |
| ssl_capath    |                            |
| ssl_cert      | /etc/mysql/server-cert.pem |
| ssl_cipher    | ALL                        |
| ssl_key       | /etc/mysql/server-key.pem  |
+---------------+----------------------------+

```Out of desperation I commented out different combinations of the ssl-* settings. When I commented out the ssl-cipher=ALL line (which I copied from MySQL.com), lo and behold SSL works.

My current settings (note commented out ssl-cipher=ALL
```

[mysqld]
...
ssl-ca=/etc/mysql/ca-cert.pem
ssl-cert=/etc/mysql/server-cert.pem
ssl-key=/etc/mysql/server-key.pem
#ssl-cipher=ALL

```My current show variables like "%ssl%" results:

```
+---------------+----------------------------+
| Variable_name | Value                      |
+---------------+----------------------------+
| have_openssl  | YES                        |
| have_ssl      | YES                        |
| ssl_ca        | /etc/mysql/ca-cert.pem     |
| ssl_capath    |                            |
| ssl_cert      | /etc/mysql/server-cert.pem |
| ssl_cipher    |                            |
| ssl_key       | /etc/mysql/server-key.pem  |
+---------------+----------------------------+
```

---

### Post by wesamly on 2010-09-07
In my case it was apparmor, and my certificates was placed in sub folder, so I added the ```
full path:
/etc/mysql/sub/*.pem r,
  /etc/mysql/sub/*.crt r,
  /etc/mysql/sub/*.key r,
```
Also, I don't have ssl-cipher in my.cnf

Thank you :D

---

### Post by kedaar on 2011-09-26
I had the exact same problem, rather than editing the apparmor config, I moved the .pem files to /etc/mysql and it works.

---

### Post by Fuxy on 2012-02-06
Thanks that apparmor tip saved the day. I never even knew something like apparmor existed.

---

### Post by chmac on 2012-10-05
I tried everything here on Ubuntu 12.04 Precise, no joy. In the end, the problem turned out to be with SSL. First, key files needed to have RSA in the header and footer line, and second, openssl on [12.04 is incompatible with mysql on 12.04]("http://bugs.mysql.com/bug.php?id=64870").

---

