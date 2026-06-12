---
title: "Can't execute update-grub on mdadm RAID 1"
date: 2017-04-14
forum: Server Platforms
---

### Post by themg2 on 2017-04-14
Short backstory: I have never done anything with mdadm before and am in charge of maintaining an ubuntu 16.04 server with a software RAID 1 based on mdadm. Recently I updated grub and was prompted to select which disks grub should be installed on.  
I chose to install it on both /dev/sda and /dev/sdb because I have read that it does not matter to mdadm and is better to install GRUB on both disks.


Currently I am trying to update the linux image, but I get the following error during the post installation script, more specifically when it executes update-grub:

```
grub-probe: error: disk `mduuid/[uuid here]' not found.
```


The installation fails after this message.


This is the complete output of the post installation script:


```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
grub-probe: error: disk `mduuid/[uuid here]' not found.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-72-generic.postinst line 1052.

```

The output of update-grub itself is the following:
```
Generating grub configuration file ...
grub-probe: error: disk `mduuid/[uuid here]' not found.

```
I have no idea how to fix this and can't seem to find anything after hours of googling. Please also note that I didn't ever reboot the server after the first grub update which was mentioned before.

---

### Post by themg2 on 2017-05-12
This was caused by /dev/sdb not being recognised anymore by Linux. It worked again after reboot but I am not sure what might have caused this.


However, I had to boot the server from rescue mode since grub was not correctly installed before.


These were the commands I used in grub rescue mode for booting the server:

```
set root=(md/1)
set prefix=(md/2)/usr/lib/grub
insmod normal
normal
linux /vmlinuz-4.4.0-70-generic root=/dev/md2
initrd /initrd.img-4.4.0-70-generic
boot
```

---

