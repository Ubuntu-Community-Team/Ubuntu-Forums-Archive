---
title: "Squid ACL src IP address range help"
date: 2008-10-13
forum: Security
---

### Post by DarkGreen16 on 2008-10-13
Hey,

I need help setting up an ACL in squid to allow all ip's within a range. For example i'm trying to set one up that will let me allow 123.123.x.x. I was able to figure out how to allow 123.123.123.x but I can't figure out how to allow it to be any number in the third octet.

Any help is appreciated

acl allowed_ips src ????

---

### Post by Zeosa on 2008-10-13
123.123.0.0/16 will result in an ip range of 123.123.0.1 - 123.123.255.254

---

### Post by DarkGreen16 on 2008-10-13
I won't be able to try it until tomorrow. I appreciate the reply - thanks

---

### Post by puppywhacker on 2008-10-14
you also need to set the http_access allow. And in your original question you asked only the last byte to be the host part, so your netmask is /24 ... /16 will allow a large range so it will work too

acl allowed_ips src 123.123.123.0/24
http_access allow allowed_ips

---

