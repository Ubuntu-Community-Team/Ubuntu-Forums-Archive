---
title: "Issues connecting"
date: 2010-07-26
forum: Server Platforms
---

### Post by LJNS on 2010-07-26
Alright using the Ubuntu with Gnome installed here are my issues
 
Have everything setup have DSL through a Westell A90-750014-07. I have all my settings good, I have a block of ip's through my isp and have the router to assign ip's to each device, that works my laptop desktop and server all have the last digit of the ip diffrent. My FTP works if i am connecting from my desktop ip to my server ip and laptop. If i go to a outside my network it won't even ping.
 
Also how do i set up were a user can edit its /home/user file but not see nor edit other /home/ files?

---

### Post by triunenature on 2010-07-26
If i am correct, you will need to connect to your routers ip, and then have it port forward to your servers ip.

Though i have never dealt with multiple ip addresses.

---

### Post by brettg on 2010-07-27
You need to edit /etc/sysctl.conf and uncomment the line that says;

```
net.ipv4.ip_forward=1
```

Your clients will need to use the internal interface on your router as their default gateway.

---

