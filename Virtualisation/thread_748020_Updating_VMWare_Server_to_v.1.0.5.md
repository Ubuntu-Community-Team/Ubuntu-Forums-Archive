---
title: "Updating VMWare Server to v.1.0.5"
date: 2008-04-07
forum: Virtualisation
---

### Post by batkosta on 2008-04-07
Dear Experts,

I'm a complete linux newbie so I appreciate your patience and understanding.

I've installed VMWare Server Console 1.0.4 on 32bit Ubuntu 7.10 Gnome desktop by launching the installer script and accepting the default settings which all went smoothly. However, version 1.0.5 of VMWare Server is out now and I would like to update to this version but not sure what steps I need to take in order to make the updating process as safe as possible. I've seen some people mentioning vmware any-any update which is even more confusing for me.

Any suggestions would be much appreciated.


K.

---

### Post by fjgaude on 2008-04-07
Okay, first you have to completely remove the 1.0.4 version before you can install the 1.0.5 one. If you originally installed from the Ubuntu repos then go to Synaptic and use the Search for vmware, and click on the Completely Removal option of vmware server, etc.

If you downloaded the server from their web site, vmware.com, then find the vmware-uninstall.pl file by using the locate command in a terminal. Then cd to that location and execute the command.

Let us know how you are doing.

BTW, the 1.0.5 version has no new features, just three or four security updates.

---

### Post by batkosta on 2008-04-08
Thanks fjgaude, it all worked fine.

K.

---

### Post by fjgaude on 2008-04-08
Let us know if you have any issues with things in vmware server. We would like to help if we can.

---

