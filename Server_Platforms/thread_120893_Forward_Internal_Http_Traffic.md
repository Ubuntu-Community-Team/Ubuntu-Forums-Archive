---
title: "Forward Internal Http Traffic"
date: 2006-01-23
forum: Server Platforms
---

### Post by agillesp on 2006-01-23
I'm using Firestarter as my firewall but am having a small problem.  I have my firewall with an external interface and an internal interface with 192.168.1.1.  I have an Apache server on another machine whose address is 192.168.1.2.  Now Firestarter correctly routes external http traffic, however internal http traffic is not getting routed correctly (unless I use the internal IP address of the Apache server - 192.168.1.2).

The scenario goes like this:
1.  ping external-IP ... ok, works fine.
2.  load webpages with [http://192.168.1.2/](http://192.168.1.2/) ... ok, works fine.
3.  load webpages with [http://external-IP/](http://external-IP/) ... nope, cannot connect.

With Firestarter you can put custom Iptables rules in the "user-pre" and "user-post" files.  So, if anyone knows what the correct rule looks like, I can shove it into one of the user files.

Thanks for any help!
-Abe

---

### Post by Peter76 on 2006-01-27
You have to set up your apache machine as 192.168.2.1 ( so not 192.168.1.2 ) Then activate internet sharing in firestarter. Now somewhere in the firestarter gui you can do port forwarding. Don't know where anymore, don't have it installed anymore, but it is really easy to find

---

### Post by agillesp on 2006-01-27
My firewall machine is on 192.168.1.1 and my Apache machine is on 192.168.1.2.  I do have internet connection sharing on and the firewall forwards port 80 traffic to 192.168.1.2.  Are you saying the Apache machine *must* be on a different subnet?

Thanks.
-Abe

---

### Post by Peter76 on 2006-01-27
I'm using another tool now for forwarding, and that only works with different subnets; so the answer is yes imo. Give it a try. Good luck

---

