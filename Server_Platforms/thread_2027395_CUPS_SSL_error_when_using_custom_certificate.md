---
title: "CUPS SSL error when using custom certificate"
date: 2012-07-16
forum: Server Platforms
---

### Post by AnrDaemon on 2012-07-16
The only thread I've found on subject is [http://ubuntuforums.org/showthread.php?t=818298](http://ubuntuforums.org/showthread.php?t=818298) and it's not much of a help.
Googling in the wild internet doesn't help either.

The issue is: when I replace "SnakeOil" certificate with a custom certificate from my own CA, CUPS deny to establich SSL connection, arguing that "encrypt_client: Could not negotiate a supported cipher suite."

```
# ls -l /etc/cups/ssl/
total 0
lrwxrwxrwx 1 root root 34 2012-07-02 19:09 server.crt -> /etc/ssl/certs/user.td-art.lan.pem
lrwxrwxrwx 1 root root 36 2012-07-02 19:09 server.key -> /etc/ssl/private/user.td-art.lan.key
# ls -l /etc/ssl/*/user.td-art.lan.*
-rw-r--r-- 1 root root     4696 2012-07-02 18:49 /etc/ssl/certs/user.td-art.lan.pem
-rw-r----- 1 root ssl-cert 1011 2012-07-02 18:13 /etc/ssl/private/user.td-art.lan.key
```

Both "SnakeOil" and my own certificate are RSA1024, I can show headers, if you're interested.
Apache and Webmin (perl miniserver) works fine with the same certificate.
Do certificate need any special OIDs to work for CUPS?

P.S.
Hardy and Lucid both exhibit the same issue.

---

### Post by AnrDaemon on 2012-07-20
Noone have ideas? Should I address it to CUPS community? >.>

---

