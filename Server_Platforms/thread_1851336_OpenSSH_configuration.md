---
title: "OpenSSH configuration"
date: 2011-09-28
forum: Server Platforms
---

### Post by djtarki on 2011-09-28
Hello everyone,

I am experiencing something weird. I have installed openssh server in a fresh installation of Ubuntu Server 10.04 64 bits. 

**I can connect to it from PCs running Windows XP and Ubuntu** (so it is not a problem with the network, firewalls, etc). However **I can barely connect from Windows 7** (not even with the firewall disabled).  **It connects from time to time** **and the rest of the times it shows "connection timeout"** (using Putty or other similar clients).

I do not know if it is related to the configuration of the openssh (/etc/ssh/ssh_config) or, on the contrary, is a problem with Windows 7 only. I have been looking up and I did not found any hint about this problem in the Internet.

Any ideas please?

Thanks in advance.

Best regards.

---

### Post by HugoSerrano on 2011-09-28
Hello!

Change from windows to Ubuntu :-P (joking)

Do you have dhcp or static IP on your network? try to see if you got same IP address in 2 different machines.

Regards

---

### Post by Jonathan L on 2011-09-28
> **djtarki said:**
> Hello everyone,

I am experiencing something weird. I have installed openssh server in a fresh installation of Ubuntu Server 10.04 64 bits. 

**I can connect to it from PCs running Windows XP and Ubuntu** (so it is not a problem with the network, firewalls, etc). However **I can barely connect from Windows 7** (not even with the firewall disabled).  **It connects from time to time** **and the rest of the times it shows "connection timeout"** (using Putty or other similar clients).

I do not know if it is related to the configuration of the openssh  (/etc/ssh/ssh_config) or, on the contrary, is a problem with Windows 7  only. I have been looking up and I did not found any hint about this  problem in the Internet.

Any ideas please?

Thanks in advance.

Best regards.

Hi

My guess is the same as Hugh's: same IP address on two  different machines and either the W7 machine or the server is getting  its ARP table messed up.

I'd try pinging W7 from server and look  at the arp caches on both machines with arp -an; the giveaway is if  something keeps changing.  

Or try using an ethernet monitoring program such as wireshark or tcpdump to see what you're getting on the wire.

If  you're connecting with routers in the way, then it's likely to be  something more tricky, then I'd definitely try wireshark on the server.   Given you have ssh working from other clients, I'd guess the client W7  machine is where the fix lies, rather than the server.

Hope that helps
Jonathan

---

### Post by djtarki on 2011-09-28
> **HugoSerrano said:**
> 
Change from windows to Ubuntu :-P (joking)



I whish I could only use Linux ;)

> **HugoSerrano said:**
> 
Do you have dhcp or static IP on your network? try to see if you got same IP address in 2 different machines.


Static IP's. I have *pinged* from **two **PCs Windows 7 64 bits to the server (Ubuntu Server 10.04 64) and some of the pings are randomly lost (1 out of 4 very often). 

Thanks for answering HugoSerrano.

---

### Post by djtarki on 2011-09-28
> **Jonathan L said:**
> Hi

My guess is the same as Hugh's: same IP address on two  different machines and either the W7 machine or the server is getting  its ARP table messed up.

I'd try pinging W7 from server and look  at the arp caches on both machines with arp -an; the giveaway is if  something keeps changing.  

Or try using an ethernet monitoring program such as wireshark or tcpdump to see what you're getting on the wire.

If  you're connecting with routers in the way, then it's likely to be  something more tricky, then I'd definitely try wireshark on the server.   Given you have ssh working from other clients, I'd guess the client W7  machine is where the fix lies, rather than the server.

Hope that helps
Jonathan

I have been testing two other Windows 7 (laptops now) using WIFI (instead of LAN cable) through the same router. They work perfect :???::???::???:

Thus, it seems to be a problem with the router when working with 4 wires at the same time. I will keep on investigating this.

So, it is not a Linux problem! :)

**Thanks for your time! **;)

---

### Post by Jonathan L on 2011-09-28
> **djtarki said:**
> I have been testing two other Windows 7 (laptops now) using WIFI (instead of LAN cable) through the same router. They work perfect :???::???::???:

Thus, it seems to be a problem with the router when working with 4 wires at the same time. I will keep on investigating this.


Excellent: I'll bet on the cables or the RJ45 sockets somewhere, rather than anything load-related.  Try swapping cables around and see if the problem moves from one W7 to another.

Kind regards
Jonathan

---

### Post by djtarki on 2011-09-28
> **Jonathan L said:**
> Excellent: I'll bet on the cables or the RJ45 sockets somewhere, rather than anything load-related.  Try swapping cables around and see if the problem moves from one W7 to another.

Kind regards
Jonathan

I will try new cables. Thank you all for your help!

---

