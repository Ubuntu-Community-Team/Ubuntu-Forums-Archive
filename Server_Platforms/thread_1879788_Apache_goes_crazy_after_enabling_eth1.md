---
title: "Apache goes crazy after enabling eth1"
date: 2011-11-12
forum: Server Platforms
---

### Post by januzi on 2011-11-12
Hi

I have got a problem with Apache. Everything was fine with eth0 (public ip). Now, I have got eth1 (192.168.x.x). That local connection is used for the backup purposes. As soon as the backup script connects to the local backup server Apache starts to spawn multiple child processes. At this point I have to restart Apache, because it doesn't respond to the http requests. 

There is one thing that may point to the solution. Both eth0 and eth1 are working on the same gateway.

---

### Post by volkswagner on 2011-11-12
What to do you have in ports.conf.

If you have

```
Listen 80
```

Perhaps change that to 

```
Listen 192.170.2.1:80
```

Replacing the above ip with eth0 ip.  This of course will require static ip.

You will also need to change any name virtualhost files to use the full ip.

like:

```
<VirtualHost 192.170.2.1:80>
```

and not

```
<VirtualHost *:80>
```

---

### Post by januzi on 2011-11-12
Thanks for the tip. I'll give it a try.

---

### Post by januzi on 2011-11-15
Nope. It didn't help.

---

### Post by volkswagner on 2011-11-15
You mention you have the same gateway for each NIC.  Are they both on the same subnet as well?

What is the output of 

```
ifconfig
```

---

