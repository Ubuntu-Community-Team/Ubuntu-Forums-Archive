---
title: "Accidentally uninstalled kernel"
date: 2014-03-28
forum: Ubuntu Development Version
---

### Post by zeke2135 on 2014-03-28
OK, I'm confused and in trouble at the same time:
I have been running Trusty development branch for awhile that I updated from saucy using the update manager. I thought I would be running kernel 3.13.x. It turns out I am running 3.11.x. That's the confusing part. 

Now, here's the in trouble part: On one machine I did a really really stupid thing that I wouldn't normally do. Basically I uninstalled 3.11 thinking it was an old version (I told you it was stupid.). So, now the machine boots straight into memtest since there's nothing else to boot to.

Is there any way I can recover from this situation short of starting over? I can boot the machine into trusty from a flash drive. 

My way lower priority question is why is the trusty upgrade not running kernel 3.13 as I thought?

---

### Post by ventrical on 2014-03-28
On some machines we have to run synaptic  to install kernels. Why? I don't know.

 If you have a USB startup then why not try a fresh install? If you want  to save all of your files and bookmarks then just choose 'something else' from Ubiquity and do not format the drive. Then it will do a fresh install and still have all your  files and bookmarks but you will still have to enter your username and pswd again.

---

### Post by coffeecat on 2014-03-28
@zeke2135, what I would do if I found myself with a kernel-less installation is to boot up with a live USB/CD, chroot into the problem installation, then apt-get update and install/re-install the kernel metapackages (which will pull in all the kernel packages you need) in the chroot environment. You'd also need to run update-grub in the chroot as a last measure. Since you were running the development branch, I'm sure you've followed the principle of this, but do you need any help with the details?

---

### Post by grahammechanical on 2014-03-28
How long have you been running a saucy upgraded to trusty? How many times have you removed kernels. I am thinking that there may be an even earlier kernel that you can boot into from Advanced options. Or may be 3.12

This will tell you the present kernel being used

```
uname -r
```

This will change directory to the boot directory/folder 

```
cd /boot
```

This will list every file in the boot folder including kernels

```
ls
```

Regards.

---

### Post by zeke2135 on 2014-03-28
> **coffeecat said:**
> @zeke2135, what I would do if I found myself with a kernel-less installation is to boot up with a live USB/CD, chroot into the problem installation, then apt-get update and install/re-install the kernel metapackages (which will pull in all the kernel packages you need) in the chroot environment. You'd also need to run update-grub in the chroot as a last measure. Since you were running the development branch, I'm sure you've followed the principle of this, but do you need any help with the details?
Thanks, this sounds promising. So if I have my normal (now kernel-less) boot disk mounted at /data, do I do "chroot /data" ?

---

### Post by zeke2135 on 2014-03-28
> **grahammechanical said:**
> How long have you been running a saucy upgraded to trusty? How many times have you removed kernels. I am thinking that there may be an even earlier kernel that you can boot into from Advanced options. 


 
Thanks, I don't think I removed a kernel previously. I'll check. I'm not sure I understand your suggestion completely, but  I don't get a prompt when I boot and I don't see anything other than memtest  in the grub.cfg file as far as I can identify.

---

### Post by coffeecat on 2014-03-28
> **zeke2135 said:**
> Thanks, this sounds promising. So if I have my normal (now kernel-less) boot disk mounted at /data, do I do "chroot /data" ?

It's a bit more complicated than that.

I would normally mount the root partition of the system I want to chroot into to /mnt, with:

```
sudo mount /dev/sda6 /mnt
```

Assuming that the system is on sda6 - adjust as necessary. If you've already mounted it on a custom mountpoint /data, that should be OK, simply substitute /data for /mnt in the following set of commands:

```
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /sys /mnt/sys
sudo cp -L /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt /bin/bash
```

You will end up with a # prompt denoting root privileges in a chroot in your kernel-less system. If you look around the forum, you'll see variations on the above for getting into a chroot, but that should do for what you want. Thereafter, I've thought of a few ifs and buts about apt-getting the kernel files you need. See what you can achieve, and in the meanwhile, I'll look at my Trusty system and see if I can come up with something definite.

---

### Post by coffeecat on 2014-03-28
> **coffeecat said:**
> I'll look at my Trusty system and see if I can come up with something definite.

Since I'm not quite clear what kernels you had installed originally, and what exactly has happened to bring you to this state, I'm about 90% confident that this will bring in all the latest kernel packages.

Once you've chrooted into your problem system, you'll have a # root prompt so you won't need sudo for the following. First:

```
apt-get update
```

Then:

```
apt-get install --reinstall linux-generic linux-headers-generic linux-image-generic
```

If that brings in and installs a number of dependent packages for the 3.13.0-19.40 kernel package set you should be OK. In which case:

```
update-grub
```

To get a grub entry for the newly installed latest kernel. Then:

```
exit
exit
exit
```

To exit the chroot and close the terminal.

---

### Post by zeke2135 on 2014-03-28
Thanks, I also found the same advice about getting network, maybe from you in another forum! I was able to get the kernel installed, and the system boots, but I think I lack some drivers, like mouse, and the display comes up in low-res. I am going to try reinstalling the nvidia driver.

This worked. Thanks very much for your help.

---

### Post by Cavsfan on 2014-03-28
Glad you got it back. Just a tip for what it's worth. Whatever kernel you install will be the kernel it boots into. E.g. if you install an older kernel like 3.13.0-18-generic then that will be the one it boots into even if you have 3.13.0-19-generic installed. 
It goes by the last one installed. Also when you remove an older kernel it just removes these parts: 
```
sudo apt-get purge linux-headers-3.13.0-18 linux-headers-3.13.0-18-generic linux-image-3.13.0-18-generic linux-image-extra-3.13.0-18-generic
```

However if you uninstall the latest kernel say the 3.13.0-19-generic kernel it will also remove these 3 ```
linux-generic linux-headers-generic linux-image-generic
```

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get purge linux-headers-3.13.0-19 linux-headers-3.13.0-19-generic linux-image-3.13.0-19-generic linux-image-extra-3.13.0-19-generic
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-generic* linux-headers-3.13.0-19* linux-headers-3.13.0-19-generic* linux-headers-generic* linux-image-3.13.0-19-generic* linux-image-extra-3.13.0-19-generic* linux-image-generic*
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 270 MB disk space will be freed.
Do you want to continue? [Y/n] 
```

So if you did I guess like you did and removed the only kernel this command should get it back:

```
sudo apt-get install linux-generic linux-headers-3.13.0-19 linux-headers-3.13.0-19-generic linux-headers-generic linux-image-3.13.0-19-generic linux-image-extra-3.13.0-19-generic linux-image-generic
```

I take a lot of notes for future reference myself. Just my 2 half pence. :)

---

### Post by zeke2135 on 2014-03-28
Cavsfan, thanks for the comments. I wasn't aware that the last (not the newest) kernel is used. I did uninstall the only kernel. To recover, I'm pretty sure I just installed linux-generic, which brought in all the other packages. The trick was booting from usb and using chroot (never used this before, but I will definitely remember it!), getting network in that environment, and finally reinstalling the video driver after installing the kernel.

---

### Post by Cavsfan on 2014-03-28
> **zeke2135 said:**
> Cavsfan, thanks for the comments. I wasn't aware that the last (not the newest) kernel is used. I did uninstall the only kernel. To recover, I'm pretty sure I just installed linux-generic, which brought in all the other packages. The trick was booting from usb and using chroot (never used this before, but I will definitely remember it!), getting network in that environment, and finally reinstalling the video driver after installing the kernel.

You're welcome! If say you remove the previous kernel than the one you're on and re-install it, that kernel will be the one you boot into. 
It is always the most recently installed one and not the highest numbered one that gets loaded. On a just released beta or final you probably have only one kernel.
We've all been there and done that though; that is how you learn. I take lots of notes.
One time I did the same thing and removed my latest kernel but the bad thing was I rebooted to a grub rescue prompt. But that too is fixable with a live CD, internet and some knowledge usually from this forum. 

There is always someone here who knows a lot about any particular problem and they're willing to share their knowledge.

Cheers! :)

---

