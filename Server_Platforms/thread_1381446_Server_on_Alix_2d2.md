---
title: "Server on Alix 2d2"
date: 2010-01-14
forum: Server Platforms
---

### Post by Powderking on 2010-01-14
Hi all

I tried to install Ubuntu Server on an Alix2d2 board: [http://www.pcengines.ch/alix2d2.htm](http://www.pcengines.ch/alix2d2.htm)
It has a CF card connected with an IDE interface and no vga output. The processor is a AMD Geode. I'm aware that I need a 386 kernel as described in the german wiki: [http://wiki.ubuntuusers.de/Alix](http://wiki.ubuntuusers.de/Alix)


What I did so far:

Installed imedia linux PCengines Alix build ([http://www.imedialinux.com/](http://www.imedialinux.com/)) on an other Ubuntu machine with usb cf interface. This worked but I don't know how I can install Ubuntu from imedia linux.

Installed Ubuntu Server on the same Ubuntu machine. Installed the 386 kernel and changed the grub config file to enable the serial output to a terminal and updated grub ([http://wiki.ubuntuusers.de/Alix#GRUB-2](http://wiki.ubuntuusers.de/Alix#GRUB-2)). I created the file /etc/init/ttyS0.conf that the serial interface still works after the bootloader ([http://wiki.ubuntuusers.de/Alix#Konsole-auf-Ubuntu-ab-9-10](http://wiki.ubuntuusers.de/Alix#Konsole-auf-Ubuntu-ab-9-10)).
Unfortunately the alix board writes only "GRUB loading." and some empty lines.

Tried to boot with Tftpd32.exe by Ph. Jounin following this guide: [http://www.tausch.it/tutorials/index.html](http://www.tausch.it/tutorials/index.html). But a wrong file is requested.
So I set up a TFPT server following this german wiki: [http://wiki.ubuntuusers.de/PXE-Installation](http://wiki.ubuntuusers.de/PXE-Installation)
As advised changed /etc/inetd.conf and /etc/default/tftpd-hpa, prepared the boot image and the DHCP server. This should be enough on the server. I have to write N over the serial port to the board while it performs memory test to enable PXE boot. This was partly successful: it gets an IP adress but afterwards nothing happens. I can't find any error message in the syslog.
I attached my configuration files. As boot image I used [http://de.archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/netboot.tar.gz](http://de.archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/netboot.tar.gz) and used the following commands to bring it into the right place:
```
sudo tar -xvzf netboot.tar.gz -C /var/lib/tftpboot/
sudo chown -R nobody:nogroup /var/lib/tftpboot
```I hope you can help me installing Ubuntu Server with PXE or from the other machine to the CF card or even directly from imedia linux.

---

### Post by Powderking on 2010-01-16
I finally found a way to install:

1. Install iMedia Linux to a partition at the end of the disk to install GRUB.
2. Copied the Ubuntu Server iso, vmlinuz and initrd.gz from here [http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current//images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current//images/hd-media/) to the disk:
  - /ubuntu-9.10-server-i386.iso
  - /boot/vmlinuz
  - /boot/initrd.gz
3. Changed /boot/grub/grub.conf to
```
default=0
timeout=2
hiddenmenu
serial --unit=0 --speed=38400 --word=8 --parity=no --stop=1
terminal --timeout=2 console serial

title iMedia
    root (hd0,8)
    kernel /boot/vmlinuz ro root=LABEL=imedia console=ttyS0,38400,8n1 vga=normal splash=verbose      i8042.noloop i8042.nokbd 
    initrd /boot/initrd.gz
```
4. Insert the CF card into Alix board, boot it and install Ubuntu Server :-D

---

### Post by Powderking on 2010-01-17
I was able to install and log in but when I restarted the server it didn't work anymore. So I installed again and before restarting did the following ([https://help.ubuntu.com/community/SerialConsoleHowto):](https://help.ubuntu.com/community/SerialConsoleHowto):)

1. Changed  /etc/init/ttyS0.conf to
```
# ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty -L 38400 ttyS0 vt102
```

2. Changed /etc/default/grub to
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
 
GRUB_DEFAULT=0
GRUB_TIMEOUT=1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="console=tty0 console=ttyS0,38400n8"
 
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=serial
GRUB_SERIAL_COMMAND="serial --speed=38400 --unit=0 --word=8 --parity=no --stop=1"
 
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
 
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true
```

3. Updated the bootloader: update-grub

---

### Post by Powderking on 2010-01-17
Now I have unexpected incosistency error after some restarts. :-(

I reinstalled and changed to the i386 kernel with no luck.

On startup I get this message:
```
fsck from util-linux-ng 2.16
alix-boot: Superblock last write time is in the future.
        (by less than a day, probably due to bad system clock last boot).  FIXED
.
alix-boot: clean, 164/32128 files, 17778/64228 blocks
fsck from util-linux-ng 2.16
alix-root: Superblock last mount time (Sun Jan 17 20:39:33 2010,
        now = Sat Jan  1 01:00:19 2000) is in the future.


alix-root: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
mountall: fsck / [406] terminated with status 4
mountall: Filesystem has errors: /
init: mountall main process (276) terminated with status 3
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
bash: groups: command not found
bash: dircolors: command not found
```


When I run fsck I get this message:
```
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
alix-boot: 164/32128 files (2.4% non-contiguous), 17778/64228 blocks
```


Does anybody have an idea?

---

### Post by Powderking on 2010-01-18
Hi all

I have posted my problem in the Installation and Upgrade forum. But nobody seems to have an answer there. So I wanted to move the thread to here or rename it because it describes the headless installation with a serial terminal as well but wasn't able to do it.
The original thread is here: [http://ubuntuforums.org/showthread.php?t=1381446](http://ubuntuforums.org/showthread.php?t=1381446)


I want to install Ubuntu server to an embedded board (Alix2d2 with 500 MHz AMD Geode LX800 processor, 256 MB DDR DRAM, a CompactFlash socket connected over IDE and no VGA port: [http://www.pcengines.ch/alix2d2.htm](http://www.pcengines.ch/alix2d2.htm))

The installation is successful and I can login and do stuff with it. But after a restart I have UNEXPECTED INCONSISTENCY on the ext2 filesystem. I tried to switch to the linux-386 kernel right after another clean installation but it was too late or is not the right solution because the problem shows up again.

Can I try the alternate installer to choose the 386 kernel right at the beginning? Or is it a CF card problem? I have read of people who use them that's why I suppose it should be no problem.

I'd appreciate any suggestions :)

---

### Post by Powderking on 2010-01-18
Ok, a little update:

This time I powered off the board right after the installation before it started into the fresh installed system.
I put the CF card into a PC with a USB CF card adapter and booted the PC with it and get no errors. I can restart it several times without any errors.
When I put the card into the Alix board I get the error again. Putting the card afterwards into the PC there's no error.

This seems to me that the problem isn't kernel related...


I definitively don't know what to check next :confused:

---

### Post by Powderking on 2010-01-18
I found a post here [http://forums.imedialinux.com/index.php?topic=139.0](http://forums.imedialinux.com/index.php?topic=139.0)

The thread title is: "System time resets to Jan 1 2000 on reboot..."
> Even though this specifies and loads ntpd, it never seems to actually *hit* any time server to update the system clock, ever, so all my files show up as created or modified in 2000.Because I get this message:
> **Powderking said:**
> On startup I get this message:
```
alix-root: Superblock last mount time (Sun Jan 17 20:39:33 2010,
        now = Sat Jan  1 01:00:19 2000) is in the future.
```
I think his solution should work for me too:
> The solution was to add a script file (I called it M01-ntpdate) to the /etc/rcS.d directory to use /usr/sbin/ntpdate to set the system clock.But I have no clue what to write exactly into that file. Hope someone can help.

---

### Post by cariboo on 2010-01-19
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Powderking on 2010-01-19
> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your two threads.

Thx!

I wasn't able to rename it to something using a serial terminal or moving it.
Sorry I knew I'm making myself unpopular ;)

---

### Post by Powderking on 2010-01-19
After adding a battery for the RTC it seems to work fine now :-)


I did the instructions for the LEDs from here: [http://wiki.ubuntuusers.de/Alix#LEDs-ansteuern](http://wiki.ubuntuusers.de/Alix#LEDs-ansteuern)

Then I added the modules to the file /etc/modules

I wrote a script /etc/init.d/alix-heartbeat
```
#! /bin/sh
echo heartbeat > /sys/class/leds/alix\:2/trigger
```then "update-rc.d alix-heartbeat defaults" and "chmod +x alix-heartbeat".


But the command for IDE load doesn't work. Maybe I'll find the problem sometimes but I can live without it.

---

### Post by MountainX on 2010-06-06
Thanks for all your posts. I'm going to try the same thing with the Alix 3d3 board.

---

### Post by Powderking on 2010-06-09
Wish you all the best with it!

My board is running 24/7 without any problems now :)

---

