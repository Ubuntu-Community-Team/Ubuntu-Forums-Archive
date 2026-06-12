---
title: "Ubuntu server lost connection after storm"
date: 2012-03-25
forum: Server Platforms
---

### Post by bestdayever on 2012-03-25
So after a storm my file server lost the ability to connect to the internet. The PCI ehternet card I put in still seems to be connected and I can even ping the router but any attempts to ssh connect to a different address (the server is 192.168.1.74 but connection attempts are made through 192.168.1.81). The router correctly identifies the server but machines can't connect/ssh into it. Is my ethernet card fried or did some settings somehow get flubbed in the crash?  Server is running 10.04 using SAMBA server to transfer files.

---

### Post by lisati on 2012-03-25
My first thought is that maybe the settings in your router need to be reviewed, e.g. is it assigning the "correct" address to your server, and is it forwarding the requests to the correct address?

---

### Post by CharlesA on 2012-03-25
> **lisati said:**
> My first thought is that maybe the settings in your router need to be reviewed, e.g. is it assigning the "correct" address to your server, and is it forwarding the requests to the correct address?
That was my thought as well.

Are you able to ping the router?

---

### Post by bestdayever on 2012-03-31
> **CharlesA said:**
> That was my thought as well.

Are you able to ping the router?

Currently no, and the router sees the server as being up it just can't ping it.

---

### Post by CharlesA on 2012-04-01
> **bestdayever said:**
> Currently no, and the router sees the server as being up it just can't ping it.
My bet would be a fried network card. Have you tried a different port on the router?

---

