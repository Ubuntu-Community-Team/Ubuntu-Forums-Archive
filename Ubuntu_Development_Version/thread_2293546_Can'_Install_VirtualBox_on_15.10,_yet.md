---
title: "Can' Install VirtualBox on 15.10, yet"
date: 2015-09-05
forum: Ubuntu Development Version
---

### Post by ping-wu on 2015-09-05
This is simply a heads up; I am unable, yet, to install VirtualBox (5.0.2, from Oracle PPA) in Ubuntu 15.10 beta1.

If there is any change of status, please someone kindly post a notice at his/her earliest convenience.  Thanks.

---

### Post by ajgreeny on 2015-09-05
Are you saying that the problem is because the ppa is not yet available, or is that you can not install the 5.0.2 version of VBox in 15.10 even if you download it direct from the Oracle site?

---

### Post by flocculant on 2015-09-05
here I get this. Of course VBox always plays catch up, anyone trying to do anything remotely not normal is accountable to the vagaries of the 3rd part system, Ubuntu, Canonical and the forum.

screenshot system fails with png - regardless of how I upload

had to download to desktop in order to upload to forum

suggest the files and filetypes for upload are revisted - tiny png's are so last decade ...

---

### Post by keithy on 2015-09-26
This works:

wget [http://launchpadlibrarian.net/199480915/libvpx1_1.3.0-3ubuntu1_amd64.deb](http://launchpadlibrarian.net/199480915/libvpx1_1.3.0-3ubuntu1_amd64.deb)

sudo dpkg -i libvpx1_1.3.0-3ubuntu1_amd64.deb

virtualbox now installs (and runs!!)

HTH

---

### Post by fjgaude on 2015-09-26
I'll give it a try... thanks!

---

### Post by dino99 on 2015-09-27
That was reported some times ago

[https://bugs.launchpad.net/ubuntu/+source/libvpx/+bug/1486456](https://bugs.launchpad.net/ubuntu/+source/libvpx/+bug/1486456)

---

### Post by keithy on 2015-09-27
> **dino99 said:**
> That was reported some times ago

[https://bugs.launchpad.net/ubuntu/+source/libvpx/+bug/1486456](https://bugs.launchpad.net/ubuntu/+source/libvpx/+bug/1486456)

I know, but its still not fixed.  I was just providing a solution I couldn't find anywhere else to help people out

---

### Post by shivam5 on 2015-11-16
[http://www.techierush.com/linux/how-to-install-virtual-box-5-in-ubuntu-all-versions/](http://www.techierush.com/linux/how-to-install-virtual-box-5-in-ubuntu-all-versions/)

this is how to install virtual box in any of ubuntu 15.10 or 15.04 or other . worked for me

---

### Post by cariboo on 2015-11-16
Old thread, nothing to do with Xenial. Thread Closed.

---

