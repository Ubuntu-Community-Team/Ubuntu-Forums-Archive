---
title: "Samba connection error"
date: 2012-07-26
forum: Server Platforms
---

### Post by brent1975 on 2012-07-26
I have ubuntu 12.04 running samba with a few shares for my windows desktops in the house.  The server name is iso-world. 

I have had no issues mapping the drives to my windows machines. In fact it has worked really well for the last few years.. Today I went to go access a file that sits on the server and good ol windows is showing and nasty red X over my mapped drives. I did some testing and I have access to the server. I tried mapping to a folder using IP such as \\192.168.2.105\brent and it works perfect. However the previous drives were mapped  like \\ISO-WORLD\brent 

Has anyone come across this before?

---

### Post by papibe on 2012-07-28
Hi brent1975.

It looks like a name resolution problem.

My first thought:
Check if the Netbios broadcasting service is up and running on your server:
```
ps aux | grep nmbd
```
If it is not up, start it:
```
sudo service nmbd start
```

Another course of action:

Have you change how your machines resolve addresses? Like upgrading your router, or subscribing to a Open DNS service?

Regards.

---

### Post by brent1975 on 2012-07-29
> **papibe said:**
> Hi brent1975.
 
It looks like a name resolution problem.
 
My first thought:
Check if the Netbios broadcasting service is up and running on your server:
```
ps aux | grep nmbd
```
If it is not up, start it:
```
sudo service nmbd start
```
 
Another course of action:
 
Have you change how your machines resolve addresses? Like upgrading your router, or subscribing to a Open DNS service?
 
Regards.
 
Hello and thanks for the reply. I have checked that the service was running. I started restarted the service many times. What I basically did was change the name to a different one. from iso-world to LINUX-MASTER. The only thing I can think of is the router had the same name and was causing conflicts even though it had been working for years with the same setup. So for now it is working. 
 
Thanks,

---

