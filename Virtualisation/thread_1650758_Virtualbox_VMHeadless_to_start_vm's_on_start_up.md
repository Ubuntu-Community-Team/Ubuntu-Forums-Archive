---
title: "Virtualbox VMHeadless to start vm's on start up"
date: 2010-12-22
forum: Virtualisation
---

### Post by hawk2010 on 2010-12-22
Hi All,

I currently have two VM's on virtuabox 3.2 running on Ubuntu 10.04 LTS server edition. I want to know how to get these VM"s to start up when ever the server reboots. I hope someone can tell me how it can be accomplished.

Thanks

---

### Post by Jose Catre-Vandis on 2010-12-22
CharlesA's startup script might point you in the right direction

[http://ubuntuforums.org/showpost.php?p=10187368&postcount=6](http://ubuntuforums.org/showpost.php?p=10187368&postcount=6)

---

### Post by CharlesA on 2010-12-23
Hi,

The script that Jose Catre-Vandis linked to is for Ubuntu Desktop. I also have a script written up for Ubuntu Server (with no GUI).

Do you have the VMs "powered off" or in a "saved" state after the reboot?

---

### Post by WalkingMist on 2011-01-08
Hi,

So how can I start all my VBox VMs on host system start up just like other services?

Thanks.

---

### Post by CharlesA on 2011-01-08
As far as I know, you'd run to write up a script, or use someone else's.

he one I use will restore any VM that is in the 'saved' state.

---

