---
title: "Disk full error"
date: 2012-02-18
forum: Server Platforms
---

### Post by thunder63cs on 2012-02-18
ok so I ma doing the upgrades and get the error to run apt-get -f install so I log into putty and run that and I get this error
 
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main linux-server amd 64 3.0.0.16.19 [1,726 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main linux-image-3.0. 0-16-server amd64 3.0.0-16.28 [37.1 MB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main linux-image-serv er amd64 3.0.0.16.19 [2,512 B]
Fetched 37.2 MB in 35s (1,048 kB/s)
(Reading database ... 330753 files and directories currently installed.)
Preparing to replace linux-server 3.0.0.15.17 (using .../linux-server_3.0.0.16.1 9_amd64.deb) ...
Unpacking replacement linux-server ...
Selecting previously deselected package linux-image-3.0.0-16-server.
Unpacking linux-image-3.0.0-16-server (from .../linux-image-3.0.0-16-server_3.0. 0-16.28_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.0.0-16-server_3.0.0 -16.28_amd64.deb (--unpack):
failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.0. 0-16-server': No space left on device
No apport report written because the error message indicates a disk full error
dp kg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-16-server /boot/ vmlinuz-3.0.0-16-server
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-16-server /boot/v mlinuz-3.0.0-16-server
Preparing to replace linux-image-server 3.0.0.15.17 (using .../linux-image-serve r_3.0.0.16.19_amd64.deb) ...
Unpacking replacement linux-image-server ...
Errors were encountered while processing:
/var/cache/apt/archives/linux-image-3.0.0-16-server_3.0.0-16.28_amd64.deb
Failed to open connection to "system" message bus: Failed to connect to socket / var/run/dbus/system_bus_socket: Connection refused
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
 
any help on how to fix this would be great. my system shows that I have:
 
**Real memory**1.71 GB total, 879.90 MB used[IMG]https://99.112.166.26:13354/images/red.gif[/IMG][IMG]https://99.112.166.26:13354/images/blue.gif[/IMG]**Virtual memory**5.01 GB total, 32.21 MB used[IMG]https://99.112.166.26:13354/images/red.gif[/IMG][IMG]https://99.112.166.26:13354/images/blue.gif[/IMG]**Local disk space**288.45 GB total, 27.36 GB used
 
so no clue where it is getting a disk full error.

---

### Post by drs305 on 2012-02-18
Take a look at this guide. It has both GUI and terminal methods of determining why a partition has become full.

Often it is backkups made to the wrong partition (to / instead of another partition, which wasn't mounted when the backup was made), large log files, or unemptied Trash Bins (yours and root's).

[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

To quickly gain a bit of space you can run:
```
sudo apt-get clean
```
which will removed previously downloaded packages.

---

### Post by thunder63cs on 2012-02-18
I only have one partition that is 288 gb and only 27 gb used? just find that weird
 
 
just looked and it is the /boot that is showing 100% full

---

### Post by thunder63cs on 2012-02-19
so what is the kcore file for?  it seems to be the one that is taking all the space up at the moment? itis showing /proc/kcore 
 
but on the other side tried to use the guide to do the expansion and I can't update or any thing else with the boot mount full and is it safe to unmount and remount this as it is with out doing the update and installing ntfsprogs ?   can't install do to disk full.... big circle... lol

---

### Post by SeijiSensei on 2012-02-20
1)  Are you positive /boot is not in a separate small partition? Having a separate /boot partition is pretty common, especially on multi-boot setups.

2)  Items in /proc are not real files and are stored in memory not on the disk.  /proc is created afresh on each boot by the kernel to store the information the kernel needs to run the OS.

3)  Run the command "df" at a prompt to see a list of each mounted filesystem, its mount point, and its usage.  If there is no /boot, and only one big filesystem mounted at /, and that filesystem is 100% full, you need to figure out where the large files are concentrated.  Run "cd /; du -s *" to get a listing of disk usage by major directory.  

4)  If you're having problems booting, try booting from an older kernel in the list and use "recovery mode".  If you can't boot at all, boot from the installation CD, pick "Try Ubuntu" and go from there.  Your hard drive will not be mounted, but you can open a Terminal and mount the drive some place temporarily like /mnt for diagnosis.

---

### Post by thunder63cs on 2012-02-20
booting up is no problem tryign to upgrade everything is .. 
 
 
when I do the df command it does list /boot
 
and it is at 100% 
 
and now some how I managed to get putty wherer the connection is being refused.... 
 
the more I look at it looks likek the ssh server is not starting up even when I go in and tell it too it says that it did but when I look at it again shows that it didn't

---

### Post by SeijiSensei on 2012-02-20
Is /boot on the same partition as /?  If there's a separate entry for /boot, it's almost certainly on its own partition. Please rerun df and post the entire results inside [noparse]```

```[/noparse] tags.

This problem arises when there's not much space allocated to /boot, and your kernel is repeatedly upgraded.  Each new instance of the kernel creates a new set of files in /boot.  Unfortunately the update manager doesn't delete stale kernel versions, so the /boot partition can fill up.  If you have a number of files named "kernel-something" in /boot, try deleting the oldest set (kernel-something, initrd-something, System.map-something, etc.) to free up space, then run "sudo dpkg --configure -a" to complete the failed installation.

You really only need the current kernel and the previous working version to use if there's a problem with the new kernel.  All the other ones are stale and can be removed.  You should edit /boot/grub/grub.cfg and remove the associated menuentry stanzas as well for consistency.  You'd need to edit this with sudo, and you'd need to make the file writable by root.  If this doesn't make sense, don't worry.  Just delete an old kernel or two and their associated files from /boot.

---

### Post by hawkmage on 2012-02-21
To remove old kernels I usually feel safer using apt-get to remove them instead of deleting files from /boot and editing the grub.cfg

To print  a list of what kernels are installed I usually use the following commnd:
```
dpkg -l linux-* | awk '/^ii/{ print $2 }'
```

Here is a command I recently used to remove all of the 2.6* Linux kernels from an Ubuntu test system I have:
```
dpkg -l linux-* | awk '/^ii/{ print $2 }' | grep "\-2.6." | xargs sudo apt-get --dry-run remove
```
TO actually have it do the removal take out the "--dry-run" option and old run it if you have a 3.* version of the kernel installed.

---

### Post by SeijiSensei on 2012-02-21
Thanks so much, hawkmage.  I knew there had to be an "official" way of doing this, but I generally just tend to improvise.  

I just wish the updater would remove the (n-2)th kernel during installation.  I've got four kernel images on my 10.10 system dating back to October of 2010.

---

### Post by thunder63cs on 2012-02-23
ok tried to clr that and got * produced to many options use "more" or "less"

---

### Post by thunder63cs on 2012-02-23
I can't get on where I can copy and paste the results now cause the ssh server on the box quit working now and I can not shell into it so I have to goto the box and type everything atm

---

