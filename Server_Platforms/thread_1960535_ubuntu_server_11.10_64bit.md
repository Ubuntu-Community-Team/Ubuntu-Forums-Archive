---
title: "ubuntu server 11.10 64bit"
date: 2012-04-17
forum: Server Platforms
---

### Post by crashdogy on 2012-04-17
OK followed this tutorial [https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3](https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3)   But I have one problem when i reboot the server it dos not restart forwarding i have to run this command echo 1 > /proc/sys/net/ipv4/ip_forward and every thing works ?

---

### Post by crashdogy on 2012-04-17
bump

---

### Post by oldos2er on 2012-04-17
Moved to Server Platforms. Please don't bump your post more than once in 24 hours.

---

### Post by Jonathan L on 2012-04-17
Hi crashdogy

I'd suggest you check you sysctl.conf file per that tutorial. My guess would be a typo in that file.

Kind regards,
Jonathan.
[

---

### Post by crashdogy on 2012-04-17
Thanks for the reply double and triple check its weird   you where right but i had to make it like this to work 
net.ipv4.ip_forward=1 this is working perfectlyit should be this net.ipv4.ip_forwarding=1    right ?

---

### Post by sj1410 on 2012-04-18
this line should exist and should be uncommented in /etc/sysctl.conf 

net.ipv4.ip_forward=1

---

### Post by Doug S on 2012-04-18
So, it seems the tutorial needs to be fixed.
I checked all combinations of:```
echo 1 or 0 > /proc/sys/net/ipv4/ip_forward
echo 1 or 0 > /proc/sys/net/ipv4/conf/default/forwarding

```and indeed, the ip_forward one updates both, but the forwarding one does not.
I will edit the tutorial, so that the next person that uses it, hopefully, has less troubles.

---

