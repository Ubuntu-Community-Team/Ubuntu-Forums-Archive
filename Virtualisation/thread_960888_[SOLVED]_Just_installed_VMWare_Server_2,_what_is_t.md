---
title: "[SOLVED] Just installed VMWare Server 2, what is the password?"
date: 2008-10-27
forum: Virtualisation
---

### Post by Deathray on 2008-10-27
This is a bit embarassing and stupid to ask, but what is the username and password for the VMware infrastructure Web access page? I tried my own username and password but it wont work! I went through all of the documentation I could get my hands on at there site but it simply wont say anything.
SOLVED!:
[http://www.howtoforge.com/how-to-install-vmware-server-2-on-an-ubuntu-8.04-desktop]("http://www.howtoforge.com/how-to-install-vmware-server-2-on-an-ubuntu-8.04-desktop")
> 
If you have accepted all default values during the installation, root is now the VMware Server login name. On Ubuntu, root has no password by default, therefore we create a password now:

sudo passwd root


---

