---
title: "2 security questions"
date: 2010-08-19
forum: Security
---

### Post by mastablasta on 2010-08-19
I just erased WinXp and installed Ubuntu on old laptop. I intend to use it later ot connect to public Wi-Fi.
 
Do i need to install a firewall GUI and make any special settings?
 
I didn't encrypt home folder during installation. I probably should have done it. But i am already low on system resources (224MB ram, 1.2Ghz CPU). Would that use up any additional resources? Would it make computer run slower?
 
Can i still encrypt the home folder after i installed the system?

---

### Post by Bachstelze on 2010-08-19
Encrypting your whole home directory might indeed be a bit too heavy on such a low-resource machine.  What you can do, if you have sensitive data on this laptop, is create an encrypted private directory that you can mount/unmount when you need it (as opposed to the whole home directory, which must always be mounted).

---

### Post by JustChris21 on 2010-08-21
If you do not know how to configure iptables through the command line then dowload guarddog its a good GUI for iptables. 

#sudo apt-get install guarddog

To run it though, open up a terminal and type '#sudo guarddog' as it needs to be run as root.

---

### Post by cariboo on 2010-08-21
Guarddog hasn't been updated since 2007, things have changed since then. We recommend using ufw which installed by default, or gufw if you need a gui.

---

