---
title: "Removing a kernel vs update-grub"
date: 2017-03-30
forum: Server Platforms
---

### Post by DigiAngel on 2017-03-30
So recently there was a snaffu with doing an upgrade where I could only boot to a grub> prompt.  I could set the kernel and initrd and boot and it was fine and booted with the newest installed kernel.  So, I ran update-grub and rebooted, same thing...grub> prompt.  So on a hunch, I apt-get removed an older kernel, which causes grub to do...."something".  And that's my question...what's the apt process when you remove or add a kernel?  I'd like to get the commands so in the event this happens again I can just run the commands.  Thank you.

---

### Post by oldfred on 2017-03-30
I thought just removing a kernel caused grub to run updates to menu.
sudo update-grub

That that would only resolve issues if an issue in the grub menu. 
I have had typo in my 40_custom that caused issues booting & building menu.

Often easiest way to repair is to run Boot-Repair and a full uninstall/reinstall of grub. That resets everything grub related. And you can choose to download latest kernel if you do not have it. But you need a live installer of the same version as your server as server is not a bootable live system that you can add boot repair into.

I have posted these as a set of repair commands after you choot into your system. # is comment

 #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get autoremove
# fix Broken packages -f 
apt-get -f install
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
dpkg --configure -a 
   sudo update-initramfs -k all -c
sudo update-grub 


 [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

