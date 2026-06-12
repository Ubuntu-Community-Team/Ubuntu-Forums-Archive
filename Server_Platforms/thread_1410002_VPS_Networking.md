---
title: "VPS Networking"
date: 2010-02-18
forum: Server Platforms
---

### Post by stoneheart on 2010-02-18
I'm a total newbie to server administration.  I just signed up for a VPS from a hosting company.  They gave me an IP address to use for my account.  I can SSH into the account successfully but no networking is set up since I cannot update sources using apt-get update.

Can someone tell me what I need to configure?  I looked at the Server docs ([https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)) but I'm a bit confused.  Are these directions what I need to follow?

---

### Post by gombadi on 2010-02-18
> 
I can SSH into the account successfully but no networking is set up since I cannot update sources using apt-get update.


If you can ssh into the vps then networking must be up and running.
What problem are you getting when you try and update your system - connection timed out, can't find host etc - the more details you can give the better.

---

### Post by stoneheart on 2010-02-18
The error from apt-get is "cannot resolve host archives.ubuntu.com".  As it turned out, it's an error in the Ubuntu image configuration.  Using the VPS control panel, I switched the OS to CentOS and now the default Apache page shows up perfectly.  Also tried a yum command and it worked.

Sigh.  I know little about Ubuntu administration and even less about CentOS.

---

