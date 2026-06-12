---
title: "Openssh bandwith per user basis"
date: 2009-12-12
forum: Server Platforms
---

### Post by tedwilder on 2009-12-12
Hello
I've been spending lots of time to search for something that record openssh session bandwith usage per user but didnt find anything. they are 2-3 threads on this forum but outdated and without good replies.
I use a server as a "proxy" for ssh tunneling. I have a limited bandwith usage/per month for the server and so I need to check wich user use the most of it.
I dont firewall anything , and thats not the point. All I need is a log that tells me : user abc used 20go, user def used 30go etc. Of course having 1 ip for each user would be a solution but too expensive so pointless.
 
It seems they are patchs for openssh that log bandwith per user but I wasnt able to find any. If you have urls for thoses patchs or know software like nethogs but far better, that would be appreciate. thank you.

---

### Post by Lars Noodén on 2009-12-13
One way would be to use iptables, but that will only limit what goes out from the machine.  But it can monitor both what leaves and arrives.  

See Limit:
[http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html#LIMITMATCH](http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html#LIMITMATCH)

An upcoming version of OpenSSH will have some ability to limit transfer rates, but it may be some while before that trickles down to Ubuntu or Ubuntu-backports.

---

