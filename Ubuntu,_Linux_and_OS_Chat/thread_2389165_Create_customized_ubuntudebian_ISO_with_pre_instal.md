---
title: "Create customized ubuntu/debian ISO with pre installed third party packages"
date: 2018-04-12
forum: Ubuntu, Linux and OS Chat
---

### Post by spbhalekar on 2018-04-12
How to create customized ISO for ubuntu/debian with pre installed third party packages.

---

### Post by BslBryan on 2018-04-12
You can use Remastersys to create a bootable ISO of your current machine.

---

### Post by rsteinmetz70112 on 2018-04-12
I've been wondering about this as well. I'd like to create a live ISO with some additional packages for use as a repair disk. 
I can't create one from any of my existing machines they have too much additional configuration. 
Also every time I create a live DVD or USB stick it ends up being a read only filesystem so I can't add packages.

---

### Post by &amp;KyT$0P# on 2018-04-12
[https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization")
[https://linuxconfig.org/legacy-bios-uefi-and-secureboot-ready-ubuntu-live-image-customization]("https://linuxconfig.org/legacy-bios-uefi-and-secureboot-ready-ubuntu-live-image-customization")

---

### Post by latifshaikh7 on 2018-04-13
+1 
I searched on the internet a lot regarding making custom Debian ISO.


These are my requirement.


1. we install some of debs packages after OS installations as like mysql, mongodb, haproxy, docker. We did some changes in configuration files. We need to install the same process on different platform hardware like Dell, HP, Vmware and Oracle Virtual box.


2. We want to customize ISO which will install Ubuntu/Debian with our customized packages on different platform hardware.

---

### Post by wildmanne39 on 2018-04-13
Hello and welcome to the forum latifshaikh7, please start your own thread and do not hijack another users thread.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by mc4man on 2018-04-13
Have a look here, never used myself
[https://launchpad.net/cubic](https://launchpad.net/cubic)

---

### Post by spbhalekar on 2018-04-13
Thanks [BslBryan]("https://ubuntuforums.org/member.php?u=797010")[COLOR=#000000]  for help me.  Will this create live iso for particular system or will clone system(with installed third party packages) from which i can install it on various type of hardware.[/COLOR]

---

### Post by sudodus on 2018-04-13
A persistent live USB drive might be an alternative.

It is much easier to create and I think it is likely to work for you.

If you want others to use it, you can make it in a fairly small USB pendrive (for example 8 GB), and create a compressed image of it, and then distribute the compressed image (which can be a 'dd image' or a 'clonezilla image'). The image must be extracted to a drive of at least the same size, not one single byte smaller, so the user must look out for 'undersized' USB pendrives with less than the nominal size.

See these links describing how to install mkusb and how to use it to create a persistent live drive.

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by spbhalekar on 2018-04-28
This link worked for me:
[https://codeghar.wordpress.com/2011/12/14/automated-customized-debian-installation-using-preseed/](https://codeghar.wordpress.com/2011/12/14/automated-customized-debian-installation-using-preseed/)

---

