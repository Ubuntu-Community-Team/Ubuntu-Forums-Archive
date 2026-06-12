---
title: "Proliant &quot;Grub Error 18&quot; with 2TB boot partition"
date: 2011-08-02
forum: Server Platforms
---

### Post by crmanski on 2011-08-02
Hello,
I have an ML570 G4 with a P400 array card. Ubuntu server 10.04. I added more drives and extended the size of the partition to 2048gb. Now on boot I get Grub  Error 18. The live cd sees the partition I just cannot boot it. I've googled around quit a bit, but have not found much that is relevant. I believe I am going to be adding a smaller boot partition to the beginning of the drive to fix this. Anyone have any ideas or advice?
Thanks

---

### Post by crmanski on 2011-08-02
After some toiling around I was able to get the server up with by reinstalling grub from a livecd...
```
sudo grub-setup -d /media/<UUID Here>/boot/grub /dev/cciss/c0d0p
```

This gave me a grub_rescue prompt on reboot.
With that I was able to boot by entering these commands...
```
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod normal
normal
set
ls /boot
insmod linux
linux /boot//boot/vmlinuz-2.6.32-33-generic-pae root=/dev/cciss/c0d0p1 ro
initrd /boot/initrd.img-2.6.32-33-generic-pae
boot
```

Now after logging in and checking grub's version it says...
grub (GNU GRUB 0,97)

I'm thinking that I need to do this...
apt-get install grub-pc
...since it did not happen when I did a 8.04->10.04 upgrade last month.

---

### Post by crmanski on 2011-08-02
Fixed...
```
apt-get update && apt-get dist-upgrade
apt-get install grub-pc
```
Chose the volume (not the partition!)
The install complete successfully. I Checked the grub.cfg files and it looked good. Just tweaked the /etc/default/grub file and removed the quiet & splash options.

Thanks to the folks who put together this comprehensive documentation...
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

