---
title: "Local Ubuntu Repository"
date: 2006-09-26
forum: Server Platforms
---

### Post by mweichert on 2006-09-26
Hi,

I want to create a server that I can add to the apt-get sources for each Ubuntu client that I have to have a central server for management updates. Can this be done, or does any one have any tips on how I might implement this?

Thanks,
Mike

---

### Post by Jussi Kukkonen on 2006-09-26
If you're mostly looking for bandwidth savings, take a look at apt-proxy. Simple, easy and effective.

Keeping a local repo is possible if you want to screen the updates, I'm not sure how it's done though. One pretty nice hack I've seen is to make /var/cache/apt in your clients a NFS mount point. Your server then NFS-serves that directory -- that way you don't ever have to run *apt-get update* from clients, just *upgrade*...

---

### Post by daller on 2006-09-30
When I try to connect to the server (192.168.0.111) I get an error:

Connection Refused!

Maybe it's my router that fsck's it up? - It's a D-link DI-514

It it a "PORT" problem? - Could I use another "standard" port?

Connecting to an IP that doesn't exist (i.e. 192.168.0.112) gives me other errors, so I know that 192.168.0.111 is the right address!

BTW: It works fine on the local machine! (localhost:9999)

---

