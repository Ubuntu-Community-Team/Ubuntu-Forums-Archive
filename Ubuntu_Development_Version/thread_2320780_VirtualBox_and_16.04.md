---
title: "VirtualBox and 16.04"
date: 2016-04-17
forum: Ubuntu Development Version
---

### Post by v3.xx on 2016-04-17
It use to be (for years) that the vBox download from the site would just work better (and I have heard others say the same).

For about the last six months I have used the download from the repositories and have not had one failure.

Now I wonder if this no longer applies and the ubuntu repository install is just as good.

---

### Post by sudodus on 2016-04-17
I'm also using VirtualBox from the repos in Xenial, and it works well :-)

---

### Post by ajgreeny on 2016-04-17
I have been running VBox 5.0.# (now 5.0.16-r105871) on Trusty for some time now, which appears to be the same version (more or less) that is in the repos for xenial.
However, to get that version in Trusty I had to enable the Oracle-vbox repositories by following the instructions at the VBox website, or download and install it manually.  The VBox repos are no longer needed for Xenial it would appear; you automatically get the latest version automatically.

---

### Post by v3.xx on 2016-04-18
Yes, it would seem no longer any problem.  Thanks for the input.

---

### Post by howefield on 2016-04-18
The one reason that kept me using the virtualbox.org package rather than the one from the Ubuntu repositories was that they were current, seems that there is less delta these days between the two. With the maturing of virtualbox seems a little less important to have the "latest", for me anyway.

Not sure what the differences are but one obvious one is the vnc extension that is installed with the Ubuntu repository package.

---

### Post by makitso on 2016-04-18
I am confused, happens a lot :-)  

For a long time I have always downloaded VB from the VB site.  However, on 16.04 it would not install due to some library comparability problem.  So, I installed from the repository.  It seems to work OK but I have not been able to make USB support work, even when configured correctly.

---

### Post by ajgreeny on 2016-04-18
> **makitso said:**
> I am confused, happens a lot :-)  

For a long time I have always downloaded VB from the VB site.  However, on 16.04 it would not install due to some library comparability problem.  So, I installed from the repository.  It seems to work OK but I have not been able to make USB support work, even when configured correctly.
Have you installed the guest additions in the guest OS?

---

### Post by hvbakel on 2016-04-18
Do any of you have issues starting virtualbox after the recent kernel upgrade to 4.4.0-20? On my installation the vboxdrv kernel module no longer loads, with the following error: "modprobe: ERROR: could not insert 'vboxdrv': Required key not available". It looks like it may be related to secure boot.

---

### Post by sudodus on 2016-04-19
Sorry, my system is installed in BIOS mode, so I am not affected by secure boot issues.

---

### Post by izznogooood on 2016-04-19
Try and reinstall VirtualBox and see if the kernelmod builds correctly, if that does not help you could always load your prior kernel under advanced options during boot.

PS: I just updated and theres an update to virtualbox, it rebuilt the kernelmods so i think this will solve your issue.

---

### Post by hvbakel on 2016-04-19
The issue I ran into is related to a recent kernel update that enabled validation of signed modules during the secureboot process. See the following bug report for more details and an explanation of how to disable the validation process to allow loading of dkms modules: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566221](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566221)

---

### Post by ptn107 on 2016-04-19
5.0.18 was released yesterday. It no longer requires you to fetch libvpx2 from wily to install properly.  It correctly uses libvpx3 from xenial.

[virtualbox-5.0.18 (64 bit) for Ubuntu 16.04]("http://download.virtualbox.org/virtualbox/5.0.18/virtualbox-5.0_5.0.18-106667~Ubuntu~xenial_amd64.deb")

[virtualbox-5.0.18 (32 bit) for Ubuntu 16.04]("http://download.virtualbox.org/virtualbox/5.0.18/virtualbox-5.0_5.0.18-106667~Ubuntu~xenial_i386.deb")

---

### Post by howefield on 2016-04-20
> **ptn107 said:**
> 5.0.18 was released yesterday. It no longer requires you to fetch libvpx2 from wily to install properly.  It correctly uses libvpx3 from xenial.

[virtualbox-5.0.18 (64 bit) for Ubuntu 16.04]("http://download.virtualbox.org/virtualbox/5.0.18/virtualbox-5.0_5.0.18-106667~Ubuntu~xenial_amd64.deb")

[virtualbox-5.0.18 (32 bit) for Ubuntu 16.04]("http://download.virtualbox.org/virtualbox/5.0.18/virtualbox-5.0_5.0.18-106667~Ubuntu~xenial_i386.deb")

..and amazingly is also available in the Ubuntu xenial repositories. Seem to be much smarter these days in keeping the Ubuntu repositories virtualbox package current.

---

