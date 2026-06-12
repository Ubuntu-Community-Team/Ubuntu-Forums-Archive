---
title: "[SOLVED]ubuntu 14.04.3 guest network connectivity issue on vmware exsi"
date: 2015-11-19
forum: Server Platforms
---

### Post by theowilde on 2015-11-19
Hi Guys, 

I have a problem but can't figure it out.
I have a Ubuntu server 14.04.3 on a vmware ESXI host 5.5, but for some reason the network stops working after a while.
If i restart the network cards   **sudo ifdown eth0 && sudo ifup eth0 **its fine for a few minutes, but for some reason the network stops working after a while. 
I have tried different Nic' s E1000 and VMXNET3 but no change. 
If i use a arp -a command or a tcpdump i regain network connection but after a few minutes its gone again.

/var/log/syslog  --> no errors only messages about the network card when i restart it.
/var/log/dmesg --> also no errors or information about the network cards.

I even tried to migrate the VM to a other esxi host but same problem.

Kind regards,

UPDATE: After 1,5 day of searching and trying i made a huge mistake, it appears  that my colleague made around the same time a windows server with the  same ip.
But because he has his windows firewall on, i could not ping the server so i thought the ip was still free, my bad..

---

