---
title: "Ubuntu 12.10 wget wordpress not working"
date: 2013-01-09
forum: Server Platforms
---

### Post by lodo on 2013-01-09
Hello,

I've been trying to wget wordpress.

It starts downloading, and after 5 - 10 seconds it stops.

I either get a timeout or a retry.

Does anyone know what might cause this?

Resolving wordpress.org (wordpress.org)... 72.233.56.139, 72.233.56.138
Connecting to wordpress.org (wordpress.org)|72.233.56.139|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-gzip]
Saving to: `latest.tar.gz'

    [             <=>                       ] 3,409,284   --.-K/s
    [                     <=>               ] 3,409,284   --.-K/s

---

### Post by volkswagner on 2013-01-09
Please post the entire command you are using.

---

### Post by lodo on 2013-01-09
> **volkswagner said:**
> Please post the entire command you are using.

su [USER] 
cd /home/[USER]/www
wget [http://wordpress.org/latest.tar.gz](http://wordpress.org/latest.tar.gz) (<---DOESN'T WORK) 
tar -zxvf latest.tar.gz
mv wordpress/* /home/[USER]/www/
rmdir wordpress

---

