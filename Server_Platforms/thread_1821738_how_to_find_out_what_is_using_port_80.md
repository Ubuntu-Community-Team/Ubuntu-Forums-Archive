---
title: "how to find out what is using port 80"
date: 2011-08-09
forum: Server Platforms
---

### Post by vanspud on 2011-08-09
Hi,

I have an Ubuntu 11.04 server with lighttpd installed as my web server. It was working fine, but now when I restart it it gives me the following error...

"can't bind to port:  80 Address already in use"

Is there a way for me to find out what is using port 80 in it's place?

Many thanks.

---

### Post by haqking on 2011-08-09
> **vanspud said:**
> Hi,

I have an Ubuntu 11.04 server with lighttpd installed as my web server. It was working fine, but now when I restart it it gives me the following error...

"can't bind to port:  80 Address already in use"

Is there a way for me to find out what is using port 80 in it's place?

Many thanks.

netstat | less

---

### Post by vanspud on 2011-08-09
Thanks for that, but the output doesn't mention port 80.

---

### Post by bhaverkamp on 2011-08-09
netstat -an | grep ":80"

A normal desktop system would not have anything on port 80.

---

### Post by haqking on 2011-08-09
> **vanspud said:**
> Thanks for that, but the output doesn't mention port 80.

try

lsof -i :80

---

### Post by haqking on 2011-08-09
> **vanspud said:**
> Hi,

I have an Ubuntu 11.04 server with lighttpd installed as my web server. It was working fine, but now when I restart it it gives me the following error...

"can't bind to port:  80 Address already in use"

Is there a way for me to find out what is using port 80 in it's place?

Many thanks.

there seems to be a ton of stuff on google referencing that exact error and message and lighttpd

some changed the port lighttpd was using to say port 81 and there is a bug report [https://bugs.launchpad.net/ubuntu/+source/lighttpd/+bug/551211](https://bugs.launchpad.net/ubuntu/+source/lighttpd/+bug/551211)

---

### Post by vanspud on 2011-08-09
Thanks for that. I got back the following, not sure what it means...

tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN 

How can disable whatever it?

---

### Post by hawkmage on 2011-08-09
Use either:
```
sudo lsof -i :80
```
or:
```
sudo netstat -lnp | grep ':80 '
```

---

### Post by vanspud on 2011-08-09
Thanks, will try that.

---

### Post by ajlee on 2012-09-02
Decided this should really be a new thread... sorry.

---

