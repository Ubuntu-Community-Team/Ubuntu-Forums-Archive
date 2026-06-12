---
title: "Migrating system to RAID1"
date: 2015-02-16
forum: Server Platforms
---

### Post by Chrigi on 2015-02-16
Hello

I am trying to work out how I can migrate my current Ubuntu 14.04 Server with LVM running one one HD to a RAID1 array.
I found one tutorial which seemed promising [https://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub2-configuration-ubuntu-11.10](https://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub2-configuration-ubuntu-11.10) and simulated it on my Virtual Box install of Ubuntu 14.04 Server.
I extracted the following steps from the tutorial (+ a little boot fix):
```

[COLOR=#333333][FONT=Consolas]# apt-get install initramfs-tools mdadm[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# reboot[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# sfdisk -d /dev/sda | sfdisk --force /dev/sdb[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# fdisk /dev/sdb[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- t[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- 1[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- fd[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- t[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- 5[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- fd[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- w[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# mdadm --create /dev/md0 --level=1 --raid-disks=2 missing /dev/sdb1 --metadata=0.9[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# mdadm --create /dev/md1 --level=1 --raid-disks=2 missing /dev/sdb5 --metadata=0.9[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# mkfs.ext2 /dev/md0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# pvcreate /dev/md1[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# vgdisplay[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]VG Name: ubuntu-vserv-vg[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# vgextend ubuntu-vserv-vg /dev/md1[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf_orig[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# mdadm --examine --scan >> /etc/mdadm/mdadm.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# nano /etc/fstab[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]Duplicate boot line, comment it out, change UUID part to /dev/md0 on duplicate[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# nano /etc/mtab[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]Change /dev/sda1 to /dev/md0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]------- Does not seem to be able to boot from this, but works even if this step is ignored[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# cp /etc/grub.d/40_custom /etc/grub.d/09_swraid1_setup[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# uname -r[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]3.13.0-44-generic[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# nano /etc/grub.d/09_swraid1_setup[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]Add the following:[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]menuentry 'Ubuntu, raid' --class ubuntu --class gnu-linux --class gnu --class os {[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]recordfail[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]load_video[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]insmod gzio[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]insmod raid[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]insmod mdraid[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]insmod part_msdos[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]insmod ext2[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]set root='(md/0)'[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]linux /vmlinuz-3.13.0-44-generic root=/dev/mapper/ubuntu--vserv--vg-root ro nomdmonddf nomdmonisw[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]initrd /initrd.img-3.13.0-44-generic[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]}[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]-------[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# nano /etc/default/grub[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]uncomment GRUB_DISABLE_LINUX_UUID=true[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# nano /etc/initramfs-tools/conf.d/mdadm[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]add BOOT_DEGRADED=true[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# update-grub[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# update-initramfs -u[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# pvmove -i 2 /dev/sda5 /dev/md1[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# vgreduce ubuntu-vserv-vg /dev/sda5[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# pvremove /dev/sda5[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# fdisk /dev/sda[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- t[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- 5[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- fd[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- w[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# mdadm --add /dev/md1 /dev/sda5[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# watch cat /proc/mdstat[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# mkdir /mnt/md0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# mount /dev/md0 /mnt/md0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# cd /boot[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# cp -dpRx . /mnt/md0[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# grub-install /dev/sda[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# grub-install /dev/sdb[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# reboot[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# df -h[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]should show /dev/md0 as /boot[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# fdisk /dev/sda[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- t[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- 1[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- fd[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]- w[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# mdadm --add /dev/md0 /dev/sda1[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# cp /etc/mdadm/mdadm.conf_orig /etc/mdadm/mdadm.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# mdadm --examine --scan >> /etc/mdadm/mdadm.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]-------[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# rm -f /etc/grub.d/09_swraid1_setup[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]-------[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# wget [https://gist.githubusercontent.com/rarylson/da6b77ad6edde25529b2/raw/33dfde10655718c4b32cbfc23306064965ee9e72/00_header_patched](https://gist.githubusercontent.com/rarylson/da6b77ad6edde25529b2/raw/33dfde10655718c4b32cbfc23306064965ee9e72/00_header_patched)[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# mv /etc/grub.d/00_header /etc/grub.d/00_header.orig[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# mv 00_header_patched /etc/grub.d/00_header[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# chmod -x /etc/grub.d/00_header.orig[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# chmod +x /etc/grub.d/00_header[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# update-grub[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# update-initramfs -u[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# grub-install /dev/sda[/FONT][/COLOR]
[COLOR=#333333][FONT=Consolas]# grub-install /dev/sdb[/FONT][/COLOR]

```

As you can see there is a step where I should create a new grub entry and then boot from that. But that boot entry (tried to adapt it to Ubuntu 14.04) is not working and I can't boot from it. But it still seems to work fine without that step. Rebooting with the normal boot entry and then checking with df -h if /boot is on /md0 looks fine. Now my questions are:
[LIST=1]
[*]Do these steps seem sane or are they missing something, breaking something I did not notice?
[*]Can I safely ignore the grub entry step?
[/LIST]

---

### Post by darkod on 2015-02-16
Hmmm... it looks good but I would do it slightly differently. But note that I am not real expert...

First, I don't like it that they add the md1 to the LVM and then move content from sda5. If something gets messed up regardless of tests you did?

Why not create whole new LVM and copy the data, leaving the original data on sda5 until you are sure it's working good? That probably means creating new VG because you have to have the old and new VG active to copy data and I guess it won't allow the same VG name.

What is your setup right now? sda1 for /boot and sda5 for LVM? How many LVs do you have?

If root is not separated from the data, you can use this migration and do a separate LV for root and separate for the data. Just an idea...

In general, creating the new VG would be like:
1. Create the md0 and md1 like you did.
2. Create new VG using md1.
3. Create necessary LVs (organize it how you prefer).
4. From current old OS or from live mode (ubuntu desktop cd), copy all data from sda1 to md0 and from old LVM to the root LV (and data LV if you have one).
(NOTE: When copying be careful to save ownership and permissions; depending on the command you like to use it's copy -ax or rsync -av; if in doubt, ask)
5. After that is done you can boot the old OS and update grub. It should pick up the "new" OS and make an entry in the menu.
6. Try booting it and see how it goes (you might need to update initramfs from inside the new OS.

If it works fine, you can install its grub on the MBRs which will make grub pointing to it. Start booting it by default and see how it goes. If all works well after a while you can add sda to the raid, effectively deleting the data on it.

There might be bits and pieces missing, but as a general idea I would try this.

---

