---
title: "Cant boot new installed virtual machine on kvm, hangs on &quot;booting hard disk&quot;"
date: 2016-01-12
forum: Virtualisation
---

### Post by hierstehtnormaleinname on 2016-01-12
Hello,

I installed a new virtual machine with Ubuntu 14.4.03 LTS virtual headers with virt-manager (KVM) after my last virtual webserver had a crash.

Now everything is set up right in this machine and also I did several reboots yesterday.
Today the virt-managers stops at "booting hard disk &#8230;"

So I already loaded the installation with the Ubuntu 14.4.03 LTS server iso image and took "repair broken system". I than mounted /dev/vda1 &#8211; everything is on the right place.
I guess that there must be a problem with the grub bootloader than.

I did remove a newer kernel yesterday since there is a bug with using virtual headers extra only referencing an older version. However, after that I updated group.
This was all I did and the disk worked well for hours and several reboots. But after a reboot of the whole machine today the virtual machine won't start up anymore.

I already tried to grub install and --recheck within the rescue mode. But this gives me the error that "grub-install: warning: File system `ext2' doesn't support embedding. (...) blocksize (...)"

Do you have any ideas how I can fix my system. I unwillingly like to install and configurate everthing a 3rd time aside all files exist only a boot problem appears :P


Additional info &#8211; this is the error what I receive by trying to fix the grub  
[IMG]http://www.wepartner.at/boot_repair.png[/IMG]

---

### Post by MAFoElffen on 2016-01-12
That is because you installed grub2 to the first partition on disk vda = vda1 ... instead of to the root of vda.

Remove the "1" so that your command looks like:
```

grub-install --bootdirectory=/mnt/boot/ dev/vda

```
[COLOR=#ff0000]But you do that after a chroot into your installed system[/COLOR]... so really, look at the second-half of post #3 of my Graphics Resolution Sticky. Link in my sigline, for detailed instructions on a mounting and chrooting into an installed sys from a LiveCD... then do that command.

---

### Post by hierstehtnormaleinname on 2016-01-13
Thanks, I oversaw that there is a EXT2 boot partition :P anyway it even not works with correct path.
I guess I screwed things up while removing unused kernels.

Well I quit now and started adapting an old backup.
However, after all this problems I feel really insecure using KVM. Maybe I just caused the problems all on my own but I never had such problems with virtualbox before.

Soi I hope the webserver will run stable now :P

---

### Post by MAFoElffen on 2016-01-14
What are using using for getting to your VM's? 

I do KVM here... And I have a lot of faith in KVM.

---

