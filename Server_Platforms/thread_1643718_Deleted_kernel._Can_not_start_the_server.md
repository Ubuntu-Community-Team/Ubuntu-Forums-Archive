---
title: "Deleted kernel. Can not start the server"
date: 2010-12-12
forum: Server Platforms
---

### Post by skink260 on 2010-12-12
Hi,

I installed ubuntu server 10.10. Everything was working perfect until i deleted one of the two kernels that showed in the grub menu at startup.

I thought the other kernel "the one that used to be highlihted" would still work when i delete the other, but it is not working. I can not start the server. Please help.

Now, at startup grub comes like this

grub>

and when i type "boot" it says "no loaded kernel"

Below is what i last did via ssh.

Any help is appreciated.





```
root@robot:~# uname -r
2.6.35-23-generic-pae
root@robot:~# apt-get remove --purge 2.6.35-22-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-backports-modules-alsa-2.6.35-22-generic' for regex '2.6.35-22-*'
Note, selecting 'linux-image-2.6.35-22-generic' for regex '2.6.35-22-*'
Note, selecting 'linux-backports-modules-alsa-2.6.35-22-generic-pae' for regex '2.6.35-22-*'
Note, selecting 'linux-image-2.6.35-22-generic-pae' for regex '2.6.35-22-*'
Note, selecting 'linux-headers-lbm-2.6.35-22-generic' for regex '2.6.35-22-*'
Note, selecting 'linux-headers-lbm-2.6.35-22-generic-pae' for regex '2.6.35-22-*'
Note, selecting 'linux-backports-modules-net-2.6.35-22-generic' for regex '2.6.35-22-*'
Note, selecting 'linux-backports-modules-net-2.6.35-22-generic-pae' for regex '2.6.35-22-*'
Note, selecting 'linux-backports-modules-wireless-2.6.35-22-generic' for regex '2.6.35-22-*'
Note, selecting 'linux-backports-modules-wireless-2.6.35-22-generic-pae' for regex '2.6.35-22-*'
Note, selecting 'linux-headers-2.6.35-22' for regex '2.6.35-22-*'
Note, selecting 'linux-headers-2.6.35-22-generic' for regex '2.6.35-22-*'
Note, selecting 'linux-headers-2.6.35-22-generic-pae' for regex '2.6.35-22-*'
Note, selecting 'linux-headers-2.6.35-22-virtual' for regex '2.6.35-22-*'
Note, selecting 'linux-image-2.6.35-22-virtual' for regex '2.6.35-22-*'
Note, selecting 'linux-tools-2.6.35-22' for regex '2.6.35-22-*'
Package linux-backports-modules-alsa-2.6.35-22-generic is not installed, so not removed
Package linux-backports-modules-alsa-2.6.35-22-generic-pae is not installed, so not removed
Package linux-backports-modules-net-2.6.35-22-generic is not installed, so not removed
Package linux-backports-modules-net-2.6.35-22-generic-pae is not installed, so not removed
Package linux-backports-modules-wireless-2.6.35-22-generic is not installed, so not removed
Package linux-backports-modules-wireless-2.6.35-22-generic-pae is not installed, so not removed
Package linux-headers-lbm-2.6.35-22-generic is not installed, so not removed
Package linux-headers-lbm-2.6.35-22-generic-pae is not installed, so not removed
Package linux-headers-2.6.35-22 is not installed, so not removed
Package linux-headers-2.6.35-22-generic is not installed, so not removed
Package linux-headers-2.6.35-22-generic-pae is not installed, so not removed
Package linux-headers-2.6.35-22-virtual is not installed, so not removed
Package linux-image-2.6.35-22-generic is not installed, so not removed
Package linux-image-2.6.35-22-virtual is not installed, so not removed
Package linux-tools-2.6.35-22 is not installed, so not removed
The following packages will be REMOVED:
  linux-image-2.6.35-22-generic-pae*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 107MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 81007 files and directories currently installed.)
Removing linux-image-2.6.35-22-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-22-generic-pae /boot/vmlinuz-2.6.35-22-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-22-generic-pae /boot/vmlinuz-2.6.35-22-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-23-generic-pae
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.35-22-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-22-generic-pae /boot/vmlinuz-2.6.35-22-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-22-generic-pae /boot/vmlinuz-2.6.35-22-generic-pae
root@robot:~# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-23-generic-pae
done

```

---

### Post by drs305 on 2010-12-12
I don't know if you can use a LiveCD or not, so here is something to try from the command prompt:

```
ls  # See what drives, partitions Grub recognizes. Identify your Ubuntu install
ls (hdX,Y)/boot  # Substitute X,Y values of Ubuntu partition found above. Do you see an "initrd.img" and "vmlinuz"
ls (hdX,Y)/boot/grub  # Do you see lots of *.mod files
set prefix=(hdX,Y)/boot/grub
root=(hdX,Y)
insmod (hdX,Y)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sdXY ro  # If you found vmlinuz & initrd.img in Command #2.  XY should be a1, a5, b1, etc
linux (hdX,Y)/boot/vmlinuz-2.6.35-23-generic-pae  root=/dev/sdXY ro  # If you didn't
initrd /initrd.img
initrd (hdX,Y)/boot/initrd.img-2.6.35-23-generic-pae  # If you didn't have 'vmlinuz' & 'initrd.img'
boot
```
If it boots, run "sudo update-grub".

---

### Post by skink260 on 2010-12-12
grub> ls
(hd0,msdos5) (hd0,msdos1) (fd0)

and 

grub> ls (hd0,1) /boot
        Partition hd0,1: Filesystem type ext2 - Last modification time...,UUID ..........

It used to be ext4.

Thanks anyway

---

### Post by elico on 2010-12-12
what you can do is to boot the machine with the installation cd in rescue mode and then change the root environment to the local one and install the another kernel.
cause what you did was to erase the kernel completely.

do you now how to mount and stuff?

you will boot , mount the dev and proc and then get into the local root env.

mkdir /mnt/newroot

#/dev/xxx (the root partition, you must now your partitioning schema in order to make it work
if you dont now you must make sure before you do something.)

mount /dev/xxx /mnt/newroot
mount -t proc none /mnt/newroot/proc
mount -o bind /dev /mnt/newroot/dev
chroot /mnt/newroot /bin/bash
env-update

export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

now you wiil get your local root environment and you can just use your normal apt-get commands.
so just use the command opposite to the one that you used.
apt-get install --reinstall 2.6.35-22-*

this will make your life east.

 (thanks for the open information in gentoo site !! so nice to see the source sometimes)

---

### Post by skink260 on 2010-12-12
Thank you very much elico. I can start the server now :)

---

