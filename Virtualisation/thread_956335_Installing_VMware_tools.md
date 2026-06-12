---
title: "Installing VMware tools"
date: 2008-10-23
forum: Virtualisation
---

### Post by rmcellig on 2008-10-23
I'm new to Ubuntu 8.04 switching from Mac OS X. How do I install VMware Tools?

I have a folder on my desktop called vmware-tools-distrib with some files in it. Where do I go from here?

This folder is from the vmware tools CD image that is on my desktop.

---

### Post by CadetD on 2008-10-23
My VMware is down due to 8.04 upgrade (but that's a different story). 
What files do you have in that folder? Don't remember off the top of my head. 

If they are .deb files, then you can
sudo dpkg -i xxxxx.deb   (where xxxxx.deb is the file from the folder) and that will install it. 

if there is a .sh file then 
sudo sh ./xxxxx.sh

---

### Post by CadetD on 2008-10-23
My VMware is down due to 8.04 upgrade (but that's a different story). 
What files do you have in that folder? Don't remember off the top of my head. 

If they are .deb files, then you can
sudo dpkg -i xxxxx.deb   (where xxxxx.deb is the file from the folder) and that will install it. 

if there is a .sh file then 
sudo sh ./xxxxx.sh

---

### Post by lkness on 2008-10-23
VMware as instructions at: 

[http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html](http://www.vmware.com/support/ws55/doc/ws_newguest_tools_linux.html)

---

