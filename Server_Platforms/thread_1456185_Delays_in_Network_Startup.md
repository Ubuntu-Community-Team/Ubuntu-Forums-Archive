---
title: "Delays in Network Startup"
date: 2010-04-16
forum: Server Platforms
---

### Post by zalondek on 2010-04-16
I am attempting to switch over from Red Hat to Ubuntu, and I need some help configuring how Ubuntu starts its networking services.  

All of my machines are connected to a Cisco 2900 switch, and the switch can take up to 35 seconds after an interface comes up before it will pass traffic.  During these 35 seconds, however, Ubuntu will believe that the network is up and will start all of its various network services.  Unfortunately, some of them will fail because the network really isn't up yet.

What is the correct way in Ubuntu to build a delay into networking startup?  I have tried a few things, such as:

1) placing a "post-up sleep 35" in /etc/network/interfaces

This works fine when you "sudo /etc/init.d/networking start", but during the boot up sequence the sleep seems to be ignored - it doesn't delay the starting of services that depend on networking to be up.

2) placing a "sleep 35" inside the /etc/init.d/networking script itself.

This is pretty hack-ish, but it definitely works in server 8.04.  It doesn't work in server 9 versions, however, because /etc/init.d/networking doesn't appear to be run at startup since it's been converted to upstart.

So - what's the "right" way to block other services from starting while the switch hardware comes up?

-Kev

---

### Post by renny666 on 2010-04-16
Maybe you could just cron a network restart?

---

### Post by Iowan on 2010-04-16
I still haven't studied how upstart works - I presume there is some way to inject a wait into the upstart version of networking startup.

---

### Post by zalondek on 2010-04-17
I can rewrite all my daemons to deal with the network not coming up right away, but I can't realistically change NFS - In the next few days I'll see if NFS clients that mount in fstab die horribly or not.

-Kev

---

### Post by BobVila on 2010-04-19
Maybe you should come at this from the switch side and try enabling spanning-tree portfast on the server's port to cut down this delay...

---

