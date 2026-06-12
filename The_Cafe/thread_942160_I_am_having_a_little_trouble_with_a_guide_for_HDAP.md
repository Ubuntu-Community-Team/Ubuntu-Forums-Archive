---
title: "I am having a little trouble with a guide for HDAPS on a thinkpad T43"
date: 2008-10-08
forum: The Cafe
---

### Post by Lord Xeb on 2008-10-08
Okay, I used this guide: [http://ubuntuforums.org/archive/index.php/t-535759.html](http://ubuntuforums.org/archive/index.php/t-535759.html)

And did the following
```
Preparing the kernel

Needed files:
sudo aptitude install build-essential fakeroot kernel-package libncurses5-dev wget bzip2 linux-source

Source package dependencies are extra, and I can't say if you'll need something more for those. You can usually figure it out from ./configure output, though.

First, we'll unpack the kernel source, make a symlink, then apply the hdaps_protect patch.
cd /usr/src
sudo su
aptitude install linux-source
tar xjf linux-source-2.6.20.tar.bz2
ln -s /usr/src/linux-source-2.6.20 /usr/src/linux
wget [http://cache.gmane.org//gmane/linux/drivers/hdaps/devel/1379-001.bin]("http://cache.gmane.org//gmane/linux/drivers/hdaps/devel/993-001.bin")
cd /usr/src/linux
patch -p1 -l < ../993-001.bin

make clean
make oldconfig
fakeroot make-kpkg clean

fakeroot make-kpkg --append-to-version=.hdapscustom kernel_image --initrd binary

``` then got the follow in the attached .txt file. What do you think went wrong?

---

