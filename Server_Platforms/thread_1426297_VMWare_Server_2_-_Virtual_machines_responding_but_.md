---
title: "VMWare Server 2 - Virtual machines responding but not physical host"
date: 2010-03-10
forum: Server Platforms
---

### Post by Exca on 2010-03-10
Good morning everybody,
 
I'm looking on several forum for people having the same problem of me, I very feel alone ! lol
 
I've installed Ubuntu Server 8.04 LTS on my new quad-core server (3 Ghz, 5 Go RAM, 1To DD in RAID 1, etc...). I've configured Open SSH on this physical server and installed VMWare Server 2.
I've installed 3 virtual machines on this server, all the machines are responding at ping and I can connect by SSH to them.
 
I regularly have problem when I'm connected on the physical host machine. SSH connection is ofen refused by the server, and when I can connect on it, less than 5 minutes later the connection doex not respond anymore.
Whereas I cannot connect on the physical host, I can ping it ! And while I can't connect by SSH, any other network protocol isn't responding, VMWare web infrastructure isn't responding also.
 
My Network controller is a RTL8111, I've downloaded the latest driver and compiled it for my kernel (2.6.24-24-server), but the problem persists.
 
The most strange thing is that my virtual machine are always responding, even if the host doesn't !
 
Do someone have encountered the same situation ? Or have some ideas where I can find more information, logs, etc. to diagnostic that problem ?
 
Thanks in advance for your help, and sorry for my not perfect english ! ;)
 
Exca.

---

### Post by samosamo on 2010-03-10
At first glance it seems like a network issue.  Please post your network topology.

---

### Post by Exca on 2010-03-10
As I've said, I can connect SHH to my VMs even if I can't connect on my Host (but it's still responds to ping). I do everything from my laptop, on a wired network.
 
My network looks like that : 
[IMG]http://sychlora.dvrdns.org/images/vmw_vmnet1.png[/IMG]
 
I've first tried to change sshd priority to with a 'renice -15 ????(pid)', but the SSH cuts persists on the host.

---

### Post by Exca on 2010-03-12
Hey samosamo, that's it !
 
The big mistake i've ever made on a network ! lol ](*,)
 
I had a virtual machine with the same IP address than my host !!!
Now it's ok, no more disconnections !
 
Thank's !

---

