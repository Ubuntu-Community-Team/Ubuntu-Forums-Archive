---
title: "Setting Up Proxy in Ubuntu"
date: 2006-07-10
forum: Server Platforms
---

### Post by ExMachina on 2006-07-10
How do i do it?

My school has a horrible firewall. Block 80% of thr LEGIT stuff.. I need to do reseacha dn i cant. So I want to install Ubuntu proxy at home and do a HTML page to use it. How do i go about this?

I have no worrie abotu bandwidth.

Any tips?

---

### Post by lamego on 2006-07-10
You could install squid, there is a nice doc on how to install/configure [squid]("https://help.ubuntu.com/community/SquidGuard") on the wiki .

---

### Post by lawngn0mex on 2006-07-10
If you can ssh to your box from school you can install tinyproxy on your machine at home. Set it up to listen on 127.0.0.1 port 8888. The config file should be in /etc/tinyproxy/tinyproxy.conf

from there, you can just make an ssh tunnel.. 

```
 ssh -L 8888:localhost:8888 -N -l user ip

```

Then just go into your browser preferences and setup a proxy connection as localhost port 8888

You can be really slick and generate private keys on your remote computer (if it's YOUR computer i.e. laptop) 

```
 ssh-keygen -t rsa 
```

then just put the contents of id_rsa.pub from your remote computer into ~/.ssh/authorized_keys on the machine you'll be sshing to. ;) That'll let you background the ssh tunnel by trailing it with an &

---

### Post by houstonbofh on 2006-07-10
If you SSH in with an Xserver running on your client, you can just run firefox on your home system and display locally.

---

