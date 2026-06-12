---
title: "Eth0 is missing"
date: 2011-09-18
forum: Server Platforms
---

### Post by Gideon2 on 2011-09-18
Encountered missing eth0 from my Ubuntu Server after changing hostname.

changed the following 

/etc/hosts
/etc/hostname

both via sudo vim

rebooted the server -> sudo shutdown -r now

after rebooting tried to restart the network

>sudo /etc/init.d/networking restart

encountered error

"cannot read interface file"

checked the file, the owner and access are ok...

still cannot see eth0 after executing ifconfig eth0

---

### Post by HermanAB on 2011-09-19
Have a look in /etc/udev/rules.d/ and fix the persistent network rules file?

---

### Post by viperce on 2011-09-19
nano /etc/udev/rules.d/70-persistent-net.rules

remove interfaces reboot it should re detect the interface card as eth0

---

### Post by Gideon2 on 2011-09-20
> **viperce said:**
> nano /etc/udev/rules.d/70-persistent-net.rules
 
remove interfaces reboot it should re detect the interface card as eth0
 
Where do I remove the interfaces reboot?

---

### Post by Gideon2 on 2011-09-20
> **HermanAB said:**
> Have a look in /etc/udev/rules.d/ and fix the persistent network rules file?
 
I just did.
 
I tried to swap the eth0 and eth1...
 
but, same error when executing the command > sudo /etc/init.d/networking restart
 
"cannot read interface file", even though I have root account.

---

### Post by Azdour on 2011-09-21
Hi,

With the error "cannot read interface file" is any part of the error that gives a line number, could it be a problem in reading the contents? Could you post the contents of /etc/network/interfaces.

---

