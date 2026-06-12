---
title: "I keep loosing abilitly to remotely connect"
date: 2011-07-22
forum: Server Platforms
---

### Post by DUSTING23 on 2011-07-22
I am running:
 
System hostname Server
Operating system Ubuntu Linux 11.04
Webmin version 1.550
Time on system Fri Jul 22 09:23:44 2011
Kernel and CPU Linux 2.6.38-10-generic on i686
Processor information Genuine Intel(R) CPU 2160 @ 1.80GHz, 2 cores
 
Every couple of hours I am unable to ssh or vnc in to my system or anything else. I can remote into another PC on my LAN and everything works fine. The only things that fixes the problem is restarting the system. Could someone point me in the right dirrection to start trouble shooting this problem? I am still learning where all the log files are and I am generally new to linux
 
Thanks.

---

### Post by SlugSlug on 2011-07-22
> **DUSTING23 said:**
> I am running:
 
System hostname Server
Operating system Ubuntu Linux 11.04
Webmin version 1.550
Time on system Fri Jul 22 09:23:44 2011
Kernel and CPU Linux 2.6.38-10-generic on i686
Processor information Genuine Intel(R) CPU 2160 @ 1.80GHz, 2 cores
 
Every couple of hours I am unable to ssh or vnc in to my system or anything else. I can remote into another PC on my LAN and everything works fine. The only things that fixes the problem is restarting the system. Could someone point me in the right dirrection to start trouble shooting this problem? I am still learning where all the log files are and I am generally new to linux
 
Thanks.


Is the server on a static IP? 
/etc/network/interfaces


should look somthing like:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
nameserver 192.168.0.1

---

### Post by DUSTING23 on 2011-07-22
Thank you very much for your help.  My IP settings looked nothing like yours although I thought I had setup a static already.  My server has been up for 6 hours now and I have maintained access to it the entire time.  Thanks for your help!!!!!!!!

---

