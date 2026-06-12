---
title: "Server Frequently drops all connections :-("
date: 2005-04-26
forum: Server Platforms
---

### Post by mjpowersjr on 2005-04-26
hello, 

I am using hoary as a home file server. Overall I am thrilled w/ hoary. I have two hoary clients (connecting via nfs), and one winxp client (samba). At seemingly random times   my server will drop all connections for about 10 seconds, and then come right back online. this happens w/ samba, nfs, ssh, telnet, apache, bind, etc. I cannot ping the server during this time. dmesg shows nothing during this time and syslog has nothing to help diagnose the problem. I am at a loss as where start diagnosing the problem from this point. Is their other system logs too look at, or a way to turn on more diagnostic logs? thanks.

also btw, these problems have existed ever since installing hoary (before setting up nfs,bind,apache,etc.)

---

### Post by dataw0lf on 2005-04-27
Sounds, more than likely, like a hardware issue.  Have you examined the interfaces on both sides during the drop ? (physically and with mii-tool)

---

### Post by mjpowersjr on 2005-05-10
ITS FIXED!!!!!!!!!!!!!!!!!!!
BUT>>>>>>>>>
yes yes, theres always a but ;-)


the problem was as follows:
I was using a netgear 4 port router as a switch by disabling dhcp server and assigning it a static ip address other than 192.168.0.1 so it wouldnt fight my linksys router. we'll apparenlty i set the netgear "switch" it to 192.168.0.2, as well as my server. (i setup the netgear over a year ago) so it was a dup ip issue. the thing that concerns me is that the issue is never logged anywhere in ubuntu :-( . I'm heading over to bugzilla now, dup is address should def. be logged / reported somewhere. then again maybe im stupid and not looking in the right place? syslog? dmesg?

anyway thanks for those who have taken the time to respond to my plea for help. 

-mike

---

