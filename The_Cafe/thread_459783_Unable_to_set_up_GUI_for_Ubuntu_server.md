---
title: "Unable to set up GUI for Ubuntu server"
date: 2007-05-31
forum: The Cafe
---

### Post by Surendra on 2007-05-31
Hi Guy's,
I am new to Ubuntu server. I installed Ubuntu Server on my laptop. I am trying to get the GUI mode on this.
I am getting below error when i execute the command.

[B][COLOR="Red"]root@ubuntu:~# sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-desktop
root@ubuntu:~#
[/COLOR][/B]

How do i set up the GUI on this?
Is it any other way to set up the GUI on Ubuntu Server?

Thanks

---

### Post by Adrenal on 2007-05-31
Tru sudo apt-get update first

---

### Post by tamays on 2007-06-13
before attempting to install desktop "sudo apt-get insatall ubuntu-desktop", run an update "sudo apt-get update". After the update is finished you should be able to install the desktop  "sudo apt-get insatall ubuntu-desktop".

---

