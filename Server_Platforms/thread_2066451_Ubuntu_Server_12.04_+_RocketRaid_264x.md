---
title: "Ubuntu Server 12.04 + RocketRaid 264x"
date: 2012-10-04
forum: Server Platforms
---

### Post by djroketboy on 2012-10-04
I am trying to figure out why I can not get a kernel module to load on boot-up. I am running a RocketRaid 264x card. It had been running fine on 3.2-23, but I need to upgrade my kernel to 3.2-31.

I had followed [CharlesA]("http://ubuntuforums.org/showpost.php?p=12014967&postcount=8")'s post and that worked flawlessly for 3.2-23, but now I can not get the new kernel to load the module during boot. From reading the wiki I should only need to run ```
sudo dkms build -k 3.2.0-31-generic -m rr264x -v 1.5
sudo dkms install -k 3.2.0-31-generic -m rr264x -v 1.5
``` 
and it should build and load for the new kernel. I have also tried to manually build the kernel, but it just will not detect with the 3.2-31 kernel. I get no errors during any build, everything seems clean. I have created new initramfs files, updated grub. I'm stumped.

I am having two problems actually, this one is just an annoyance. Grub 1.99, adding "noquiet nosplash" to the command line boot-up sequence doesn't seem to always work. Sometimes I still get a black screen. I don't want a black screen, I would like to see the verbose output during boot. Any idea's?


Here is the output from what I've run.
```
 $sudo dkms build -k 3.2.0-31-generic -m rr264x -v 1.5

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-31-generic -C product/rr2640/linux KERNDIR=/lib/modules/3.2.0-31-generic/build.....
cleaning build area....

DKMS: build completed.
``````
$ sudo dkms install -k 3.2.0-31-generic -m rr264x -v 1.5

rr26xx:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/3.2.0-31-generic/updates/dkms/

depmod.......

Backing up initrd.img-3.2.0-31-generic to /boot/initrd.img-3.2.0-31-generic.old-dkms
Making new initrd.img-3.2.0-31-generic
(If next boot fails, revert to initrd.img-3.2.0-31-generic.old-dkms image)
update-initramfs........

DKMS: install completed.
``````
$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
done
``````
$ dkms status 
rr264x, 1.5, 3.2.0-23-generic, x86_64: installed
rr264x, 1.5, 3.2.0-31-generic, x86_64: installed
```

---

