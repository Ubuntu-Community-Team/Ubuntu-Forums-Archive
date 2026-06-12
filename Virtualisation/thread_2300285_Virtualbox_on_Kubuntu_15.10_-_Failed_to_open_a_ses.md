---
title: "Virtualbox on Kubuntu 15.10 - Failed to open a session for the virtual machine"
date: 2015-10-24
forum: Virtualisation
---

### Post by Treshan_Remolano on 2015-10-24
I recently upgrade to Kubuntu 15.04 to 15.10 yesterday. And after the upgrade, I installed VirtualBox, and I created the virtual machine "Windows XP". I configured this virtual machine and I started this virtual machine and it failed to boot. I have these error messages:
[ATTACH=CONFIG]265147[/ATTACH][ATTACH=CONFIG]265148[/ATTACH]

How can I solve this problem?

---

### Post by recepserit on 2015-11-02
Will you try the following commands?



> 
sudo apt-get install linux-headers-generic build-essential dkms
sudo apt-get remove --purge virtualbox-dkms
sudo reboot
sudo apt-get install virtualbox-dkms

Also i found this in forum: **[http://ubuntuforums.org/showthread.php?t=1885936&page=10](http://ubuntuforums.org/showthread.php?t=1885936&page=10)**

---

### Post by SeijiSensei on 2015-11-02
Are you using the version of VirtualBox in the repositories?  I suggest following the instructions for "[Debian-based Linux distributions]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian_based_Linux_distributions")" on the VirtualBox site and using the Oracle repository.  Always works for me.

---

