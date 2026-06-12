---
title: "[HOW-TO] Install/migrate Ubuntu on F2FS"
date: 2014-08-25
forum: Ubuntu Development Version
---

### Post by vinibali on 2014-08-25
So, it's my first tutorial on ubuntuforums!
Samsung's F2FS [was introduced at 05 October 2012]("http://lkml.iu.edu//hypermail/linux/kernel/1210.0/03173.html") and merged into [Linux at version 3.8]("http://www.phoronix.com/scan.php?page=news_item&px=MTMwNTQ"). Its generally developed for NAND based systems, like smartphones and computers with ssd.
After almost 2 years of the announcement, theres still no support in Ubuntu Installer.

So, first of all, its better if you will make a clear install and/or make a backup from your existing system.

**_Trusty_** has an updated util-linux package since 22-09-2014!
Ignore add-apt step if the output is at least 2.25 for the followint terminal command:

```
blkid -v
```

**---IGNORE---**[I]

If you are running from the LiveCD/USB(this package will go to the installed system too) or a working system, install one of the newer package of util-linux from Ivan Larinov's PPA:

```
sudo add-apt-repository ppa:xeron-oskom/util-linux
```

Update your repos:

```
sudo apt-get update
```

If you get error, you should modify the distro value to "trusty"!

Install the util-linux(currently 2.25) and f2fs-tools, gparted packages. Just the "newerthan2.20util-linux" is able to get the uuid at F2FS partition. I use Ivan's repo, works like charm!

[/I]*```
sudo apt-get install util-linux --reinstall
```***---IGNORE---**[I]

```
sudo apt-get install f2fs-tools gparted
```[/I]

Install the system (ignore this step if you have a working one), **_you must have a separated EXT2/3/4 (i have EXT2 and 200MB) boot partition and a normal ROOT (I had a 32GB EXT4, but it could be anything)!_**

Boot you fresh distro, and add the f2fs module to intramfs: add "f2fs" after the #(in a new row at the end of the text file).

```
sudo gedit /etc/initramfs-tools/modules
```

Update your initramfs

```
sudo update-initramfs -u
```

Now your distro is able to boot any F2F2 partition. You can check it with adding an F2FS entry at the fstab. (Ignore this step if you want to have you f2fs system ASAP)

Make a new partition at gparted, format with f2fs file-system(for this you must have f2fs-tools) and add a new line to the fstab:

```
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxxx     /media/f2fs             f2fs          rw,relatime,background_gc=on,user_xattr,acl,active_logs=6    0 0
```

You can get the UUID at gparted or run the blkid as root, make sure you have the /media/f2fs directory!

Now start another distro or a live system and copy your existing system to somewhere, mostly i use ramdisk for that kind of procedures. Gparted, util-linux(blkid) 2.25 and f2fs-tools are helpful!

```
sudo mkdir /media/ext4
sudo mount /dev/sdxx /media/ext4
sudo cp -a /media/ext4/* /media/ramdisk
```

After the partition save, unmount the volume at gparted.
Format you ex-root partition with gparted to f2fs file-system and check for the UUID(double click on the freshly-formatted f2fs system or run blkid as root).

Mount, than copy the already f2fs capable system.

```
sudo mkdir /media/f2fs
sudo mount /dev/sdx /media/f2fs
sudo cp -a /media/ramdisk/* /media/f2fs
```

Check your mounted f2fs directory, maybe you have to cut-paste the content to the root of the /media/f2fs partiton.

So probably, now you have a f2fs formatted partition with a bootable system, now you have to edit the fstab

```
sudo gedit /media/f2fs/etc/fstab
```

Writeover the existing / row with the following one:

```
[CODE]UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxxx     /            f2fs          rw,relatime,background_gc=on,user_xattr,acl,active_logs=6    0 0
```[/CODE]

Its a normal, fstab entry from a working arch. Later you can edit the options, now just replace the UUID "double click on the freshly-formatted f2fs system or run blkid as root" as we did.

After you already format, than copy the partition and edited the fstab, just have to update the boot partition.
Mostly i use chroot for this, but first mount the boot volume too!

```
sudo mount /dev/sdx /media/f2fs/boot
sudo mount --bind /dev /media/f2fs/dev
sudo mount --bind /proc /media/f2fs/proc
sudo mount --bind /sys /media/f2fs/sys
sudo chroot /media/f2fs
```

Now you have chrooted the F2FS system, just update the grub:

```
sudo update-grub
```

Probably, you will able to boot up your F2FS powered Ubuntu now. Dont worry, maybe one(many) or you grub options have gone, but after the F2FS system boots, rerun the update-grub command.

After this very crazy-safe tutor, i hope i dont miswrite any of the rows, and many of you(us) will happy to use the F2FS powered system.
In generally the system boot feels to have the same speed as a tweaked EXT4(on my Samsung 840 non-EVO 120GB drive), but forex: the Libreoffice loads faster :p!
[ATTACH=CONFIG]255822[/ATTACH]

---

### Post by ekerazha on 2014-08-27
Good job!

Don't forget to sustain the ticket to add F2FS support to the Ubuntu installer: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1261175](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1261175)

---

### Post by vinibali on 2014-09-24
post updated, util-linux 2.25 on the way

---

### Post by vinibali on 2014-10-22
post updated, fine tunes

---

### Post by alexan on 2015-06-12
Thanks to this guide I've successfully installed Lubuntu with f2fs; but now I got a problem when update the kernel **to** 3.19.0-20 **from** 3.19.0-15

on 3.19.0-15 Lubuntu boots fine, but from3.19.0-20 it drops me on busybox with initramfs.

I've run sudo update-initramfs -u (which shows only "*update-initramfs: Generating /boot/initrd.img-3.19.0-20-generic*" without any errors) but problem seems to persist

---

### Post by cariboo on 2015-06-12
This has nothing to do with wily.Closed

---

