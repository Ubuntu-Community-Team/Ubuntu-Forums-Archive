---
title: "Boot to Grub after update (12.04)"
date: 2012-06-07
forum: Server Platforms
---

### Post by Skyflyer4life on 2012-06-07
Just ran apt-get upgrade this morning and now booting into grub only.  I thought this only happened with beta releases.  Had to pull server from server room to hook it up to monitor to find out what was going on.  Anyone have any suggestions?

Asus P8Z68 Mobo (uefi bios)
Server 12.04

---

### Post by LHammonds on 2012-06-07
At any point during the upgrade, did it ask if you wanted to install  grub2 with a pop-up (ascii) window?  Did it warn you that it may not be  able to boot if you do not configure it?

I have seen this issue in the past on 10.04 servers but have yet to see the same issue with 12.04 (knocking on wood!)

The  solution to keep it from having an issue was to not reboot it  immediately but instead issue the following commands BEFORE rebooting:

```
sudo grub-install /dev/sd**[COLOR=Red]X[/COLOR]**
sudo grub-update
```Replace **[COLOR=Red]X[/COLOR]** with the correct hard disk (for most single disk scenarios, it should be /dev/sda).  Use **sudo fdisk -l** if you are not sure which disk it should be.

However,  if you rebooted and you are staring at a grub boot prompt, you will  need to issue some grub-fu commands...of which I have only been  successful in reviving a server once....but could not remember what I  did the 1st time.

I used some google-fu and found a ton of  articles about the issue but many did not have the specific info I  needed to make the system boot except for one article...which I could  not find again later when I needed.

It was something to the effect that you have to select the correct hard drive, then the boot partition and install grub.

There  were other suggestions to boot from the 12.04 live CD and perform a  system repair...basically mounting the root partition and issuing the  grub commands mentioned above...but that did not help my particular  situation but may help with yours.

Sorry I could not be much help.

LHammonds

---

### Post by wilee-nilee on 2012-06-07
Run this command set from a live ubuntu cd, and then open home and copy and paste all the text from the results.txt to a reply. While the reply is still open highlight all the text and click on the # then submit reply.
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```

---

### Post by wilee-nilee on 2012-06-07
> **LHammonds said:**
> At any point during the upgrade, did it ask if you wanted to install  grub2 with a pop-up (ascii) window?  Did it warn you that it may not be  able to boot if you do not configure it?

I have seen this issue in the past on 10.04 servers but have yet to see the same issue with 12.04 (knocking on wood!)

The  solution to keep it from having an issue was to not reboot it  immediately but instead issue the following commands BEFORE rebooting:

```
grub-install /dev/sda
grub-update
```However,  if you rebooted and you are staring at a grub boot prompt, you will  need to issue some grub-fu commands...of which I have only been  successful in reviving a server once....but could not remember what I  did the 1st time.

I used some google-fu and found a ton of  articles about the issue but many did not have the specific info I  needed to make the system boot except for one article...which I could  not find again later when I needed.

It was something to the effect that you have to select the correct hard drive, then the boot partition and install grub.

There  were other suggestions to boot from the 12.04 live CD and perform a  system repair...basically mounting the root partition and issuing the  grub commands mentioned above...but that did not help my particular  situation but may help with yours.

Sorry I could not be much help.

LHammonds

Please change the command to.
```
sudo grub-install /dev/sdX
```
You do not know that sda is correct and this command could be be run by another user not really knowing what this does, and mess up their setup.

**A installation could be on any HD.**

The proper way a HD would be ascertained is by running first.
```
sudo fdisk -l 
```

To confirm the HD first.

---

### Post by Skyflyer4life on 2012-06-08
Back to working on this again today.  Pretty pissed off that my server is out of commission.  I'm used to this happening with 12.04 Beta testing that I did but not now.  After sleeping on this last night, I do remember that after running the apt-get upgrade I did get one error which I've never seen before.  It squawked about an error with Linux Kernel upgrade or something along those lines.  It looked pretty serious and strange that I would have a error with a Linux upgrade (i think to x.24 or something) but I figured I would reboot and try again.  Nope... I'm guessing that the linux kernel got hosed.  

Is there a way to just install the kernel, or run apt-get upgrade again from a chroot?  I like how I had the server set up and don't want to set it up all over again for sake of saving my precious time.

---

### Post by Skyflyer4life on 2012-06-08
Ok, made some progress.  Using the Ubuntu 12.04 Server usb stick I created, I ran the "rescue a broken system" option which brought me to a command prompt of the /root system.  I ran apt-get update and apt-get upgrade and here is what I got:

#Reading package list... Done
#Building dependency tree
#Reading state information... Done
#0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
#1 not fully installed or removed
#After this operation, 0 B of additional disk space will be used
#Do you want to continue (Y/n)? Y
#Can not write log, openpty () failed (/dev/pts not mounted?)
#Setting up linux-image-3.2.0-24-generic (3.2.0-24.39) ...
#Running depmod
#update-initramfs: deferring update (hook will be called later)
#Failed to symbolic-link /boot/initrd.img-3.2.0-24-generic (--configure):
#Subprocess installed post-installation script returned error exit status 17
#Errors were encountered while processing:
#linux-image-3.2.0-24-generic
#E: Sub-process /usr/bin/dpkg returned an error code (1)


Why is this happening, why did this happen and what should I do about it?
Thanks.

---

### Post by Skyflyer4life on 2012-06-08
After having a cocktail and doing a bit of googling... I've managed to get back to a working system.... (still checking it out though).

I ran the following commands:
#apt-get install linux-image-3.2.0-24-generic
#update-initramfs -cv -k all
#update-grub


the first command kicked back the same errors I've been getting which I documented in the previous post.  The second command (which I'm not familiar with) did a whole bunch of stuff. Can someone shed some light on what I did?

Running apt-get update/upgrade now.  Only one package to upgrade (sudo) but still listing (1 not fully installed or removed).  Before I select [Y] I will wait for further instruction.  In the meantime I will put the server back into production.

---

### Post by wilee-nilee on 2012-06-08
> **Skyflyer4life said:**
> After having a cocktail and doing a bit of googling... I've managed to get back to a working system.... (still checking it out though).

I ran the following commands:
#apt-get install linux-image-3.2.0-24-generic
#update-initramfs -cv -k all
#update-grub


the first command kicked back the same errors I've been getting which I documented in the previous post.  The second command (which I'm not familiar with) did a whole bunch of stuff. Can someone shed some light on what I did?

Running apt-get update/upgrade now.  Only one package to upgrade (sudo) but still listing (1 not fully installed or removed).  Before I select [Y] I will wait for further instruction.  In the meantime I will put the server back into production.

Can you boot in with the kernel before this one, I would do that then you are at a cli that is mounted and online. You can rm the bad kernel and work from there.

---

### Post by Skyflyer4life on 2012-06-09
```
login as:
*@192.168.1.206's password:
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-24-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sat Jun  9 08:36:38 EDT 2012

  System load:  0.01              Processes:           104
  Usage of /:   8.5% of 22.36GB   Users logged in:     0
  Memory usage: 4%                IP address for eth1: 192.168.1.206
  Swap usage:   0%

  Graph this data and manage this system at https://landscape.canonical.com/

1 package can be updated.
0 updates are security updates.

Last login: Fri Jun  8 20:29:28 2012 from 192.168.1.246
*@Saturn:~$ uname -a
Linux Saturn 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```Running "apt-get upgrade" is still listing "1 not fully installed or removed".  How do I find out what the "1" is and how to I remove it or prevent it from being installed?

---

### Post by Skyflyer4life on 2012-06-09
After doing a bit of searching and reading on "initramfs" I came across something that looks like it fixed it (after a leap of faith running the command)

#sudo dpkg --configure -a

Below is the code output.  Can anyone confirm that this was the correct approach and safe to do?  I'm not showing "1 not fulling installed or removed" anymore and i looks like I've gone from 0-24.37 to 0-24.39 successfully.  I'm still curious why I encountered an error initially while upgrading from 37 to 39 which caused the system to fail to boot.  At least it was a simple fix but I've yet to reboot the machine to confirm.  

```
*@Saturn:~$ sudo dpkg --configure -a
Setting up linux-image-3.2.0-24-generic (3.2.0-24.39) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled
(3.2.0-24.37 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(3.2.0-24.37 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
done

``````
*@Saturn:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  sudo
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 288 kB of archives.
After this operation, 16.4 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main sudo amd64 1.8.3p1-1ubuntu3.3 [288 kB]
Fetched 288 kB in 0s (626 kB/s)
(Reading database ... 54774 files and directories currently installed.)
Preparing to replace sudo 1.8.3p1-1ubuntu3.2 (using .../sudo_1.8.3p1-1ubuntu3.3_amd64.deb) ...
Unpacking replacement sudo ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up sudo (1.8.3p1-1ubuntu3.3) ...
Installing new version of config file /etc/pam.d/sudo ...
*@Saturn:~$
```

---

### Post by drs305 on 2012-06-09
Yes, that was the correct command. It allows installation processes which were not completed to run to conclusion.

You can read the full description  of what command switches do with:
```
man <command>
```
Example: man dpkg

---

