---
title: "new 200 line Kernel Patch does wonders"
date: 2010-11-17
forum: Server Platforms
---

### Post by bmullan on 2010-11-17
Very cool news on a small patch that apparently works wonders with the linux scheduler.

[Click here to see Phoronix testing of new 200 line Linux Kernel Patch shows it does wonders for performance]("http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1")

---

### Post by Protocol84 on 2010-11-18
I have been trying to figure out how to compile a kernel with this patch.

I am rather new to linux but have been on it for about a year, so I figure this is a perfect time to learn

---

### Post by James78 on 2010-11-18
Thanks for the link. I downloaded the latest stable kernel from the kernel archives, and I'm going to compile it with this patch. I might come back to reply with how much better my desktop is! ;)

---

### Post by kwhatcher on 2010-11-18
I've never compiled my own kernel. Might be the excuse I've been looking for! After all, this is what VirtualBox is for!

Could someone suggest an easy howto link for applying the patch and compiling? 

Thanks,
Kerry

---

### Post by Protocol84 on 2010-11-18
I am in the same train of thought as you. 

I am currently researching it and if I find anything I will post it (or a link to it) here.

---

### Post by James78 on 2010-11-20
Get latest kernel. Extract.
[http://www.kernel.org/](http://www.kernel.org/)
Alternatively, get the kernel source for your kernel version.
```
apt-get source linux-image-`uname -r`
```

Install deps.
```
# The line after this might work instead of installing the dependencies manually, or it might not, I don't know. However, installing it manually, that is, all the lines in this box (which excludes the line directly below this comment), should work, as it worked for me.
sudo apt-get build-dep --no-install-recommends linux-image-`uname -r`

sudo apt-get install fakeroot build-essential crash kexec-tools makedumpfile kernel-wedge
sudo apt-get build-dep linux
sudo apt-get install git-core libncurses5 libncurses5-dev libelf-dev asciidoc binutils-dev
```

Then
```
# copy kernel configuration and use it
cp -vi /boot/config-`uname -r` .config
make menuconfig
#then select load alternative config, press enter to load .config
```

[http://marc.info/?l=linux-kernel&m=128985638523271&w=2](http://marc.info/?l=linux-kernel&m=128985638523271&w=2) <-- newer version of patch than is listed in the article linked to from this topic (I haven't tried it!)
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)
Other good sources of information: [http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+compile+kernel&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+compile+kernel&ie=utf-8&oe=utf-8)

---

