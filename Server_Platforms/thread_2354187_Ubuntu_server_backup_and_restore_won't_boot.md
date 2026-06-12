---
title: "Ubuntu server backup and restore won't boot"
date: 2017-02-28
forum: Server Platforms
---

### Post by hpapagaj on 2017-02-28
[COLOR=#111111][FONT=Ubuntu]I followed the guide on the [help.ubuntu.com]("https://help.ubuntu.com/community/BackupYourSystem/TAR") to make a full backup of my Ubuntu server.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Backup part:
[/FONT][/COLOR]
sudo tar -cvpzf backup.tar.gz
–exclude=/dev/*
–exclude=/lost+found/*
–exclude=/media/*
–exclude=/mnt/*
–exclude=/proc/*
–exclude=/sys/*
–exclude=/tmp/*
–exclude=/var/cache/apt/*

[COLOR=#111111][FONT=Ubuntu]The problem is with the restore part.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]1, Boot from Live cd
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]1a, First, I created partitions on the new drive, as was on my old hdd. Root and Swap.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]1b,[/FONT][/COLOR]
sudo chown ubuntu:ubuntu -R /media/whatever
tar -xvpzf /path/to/backup.tar.gz -C /media/whatever --numeric-owner

[COLOR=#111111][FONT=Ubuntu]Files were restored.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
1c, To find new UUID's I used blkid and I edited /etc/fstab to change the old UUID.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
1d,[/FONT][/COLOR]
mkdir /proc /sys /mnt /media 
[COLOR=#111111][FONT=Ubuntu]
2, GRUB[/FONT][/COLOR]

sudo -s
for f in dev dev/pts proc ; do mount --bind /$f /media/whatever/$f ; done
chroot /media/whatever
dpkg-reconfigure grub-pc
[COLOR=#111111][FONT=Ubuntu]
I installed GRUB into /dev/sdb (I also had /dev/sdb1 option)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Here I got some weird error:[/FONT][/COLOR]

root@ubuntu:/# dpkg-reconfigure grub-pc
device node not found
device node not found
...
device node not found
Installing for i386-pc platform.
device node not found
device node not found
...
Installation finished. No error reported.
Generating grub configuration file ...
device node not found
...
Found linux image: /boot/vmlinuz-3.13.0-77-generic
Found initrd image: /boot/initrd.img-3.13.0-77-generic
device node not found
...
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
device node not found
...
Cannot find list of partitions!  (Try mounting /sys.)
done
[COLOR=#111111][FONT=Ubuntu]
After restart I see the GRUB, Ubuntu starts, but it is stopping here:[/FONT][/COLOR]
 
init: plymouth-upstart-bridge main process ended, respawning
 random: nonblocking pool is initialized
[COLOR=#111111][FONT=Ubuntu]
Yes, I did search already, and I [found this article]("http://blog.jamesrhall.com/2014/04/ubuntu-server-1404-fun.html"), saying that I need to set nomodeset as boot option.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Unfortunately it is not helped. Any other idea?

[/FONT][/COLOR]Some more error messages:


[https://f001.backblazeb2.com/file/mihalkodropshare/Screen-Shot-2017-02-28-21-21-25.png](https://f001.backblazeb2.com/file/mihalkodropshare/Screen-Shot-2017-02-28-21-21-25.png)

---

