---
title: "VirtualBox kernel not installed"
date: 2008-02-17
forum: Virtualisation
---

### Post by WkenCouser on 2008-02-17
Hello All,
I have VirtualBox installed and when I try and start my Windows XP virtual disk I get an the error -1908

I have tried to reinstall the virtual box ose and no joy.

I am running Ubuntu and Gutsy Gibson.

Thanks,
ken :-)

---

### Post by Jose Catre-Vandis on 2008-02-17
You may have a permissions problem. From the command line, try running:
```
sudo chmod 666 /dev/vboxdrv
```
or

Alternatively the OSE version is known to give these errors. If you can bear to use the non-free free version, uninstall the OSE version and download from Virtualbox.org here:[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

or

Try running from command line to see what messages it gives up, something like:
```
VBoxManage startvm xp
```
(replace xp with the name of your vm)

---

