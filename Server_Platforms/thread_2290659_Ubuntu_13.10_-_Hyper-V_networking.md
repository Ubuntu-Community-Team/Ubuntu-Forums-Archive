---
title: "Ubuntu 13.10 - Hyper-V networking"
date: 2015-08-14
forum: Server Platforms
---

### Post by springs1 on 2015-08-14
Hi all,

I've recently moved a personal server over from VMWare over to Hyper-V. I've got 4 VM's installed where 2 are windows and the other 2 are linux.

one of the linux servers worked without a hitch which is an older CentOS server.

The ubuntu server is up and running but won't connect back to the network. Eth0 was down and i can bring this up and it's showing the correct MAC address that i gave it in hyper-v but it won't talk back to the DHCP server to get an ip address. I've read online and can see a few things about the hyper-v integration services for linux which i have enabled. the other thing i can see if to create a separate network port on the hyper-v switch for internal access and then perform internet connection sharing on it.

My host is Server 2012 Hyper-v so i have limited access to make changes without working out the power shell commands. 

does anyone know a good work around to get my server back up and running?

---

### Post by Bucky Ball on 2015-08-14
*Thread moved to **Server Platforms**.*

I can't help with your issues but I can bump your thread to advise that 13.10 is no longer supported. If you're running a server, suggest you upgrade to the current long-term support release, 14.04 LTS.

Upgrade the Ubuntu server as the 13.10 repos are no longer. Your server is probably dated and hasn't got the latest security updates and other things. :)

---

### Post by volkswagner on 2015-08-15
Do you have a file /etc/udev/rules.d/70-persistent-net.rules?

I'm not sure of the state of udev rules. Older systems used to have such a file, but I don't see one on my 14.04 install.

If there is a file, you may need to edit the mac address to match.

How did you migrate/clone the system?

---

