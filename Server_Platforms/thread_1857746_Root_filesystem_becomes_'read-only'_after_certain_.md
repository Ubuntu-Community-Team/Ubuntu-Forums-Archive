---
title: "Root filesystem becomes 'read-only' after certain period of time"
date: 2011-10-10
forum: Server Platforms
---

### Post by Xeijin on 2011-10-10
Hi There,

Having a frustrating problem with Ubuntu 10.04 LTS at the moment. I have a minimal install running LAMP, OpenSSH, SAMBA along with Sabnzbd+, SickBeard & Couchpotato, Webmin and 4 2TB Samsung Hard Drives configured in an LV Group. It is also acting as a TimeMachine backup for my Mac using the netatalk package.

I should note at this point that Ubuntu is installed to and run from a USB Flash Drive with a decent write speed.

Everything works fine when the server first boots, and it continues to work well for a few hours. However usually about a day later, when I try to perform an operation that typically requires a write I get errors.

Upon further investigation (via. SSH) I find that I am unable to perform any write-related task, simply trying to create a directory yields a 'mkdir: cannot create directory `test': Read-only file system' error.

The frustrating thing is that I am not able to track the problem down. I am not aware of the server rebooting, afaik it just suddenly seems to switch to a read-only file-system. I am still able to write to the volume group containing the 4 2TB Samsung drives, and my Backups to Timemachine (on a separate 750GB hard drive) also complete without issue. So it seems to be a problem with the root filesystem (i.e. the one which runs from the USB stick)

I have re-formatted the box twice now and I am still getting the same problem.

Anyone have any ideas/know any logs I can check for problems?

---

### Post by papibe on 2011-10-10
How big is the flash drive?
Did you create partitions on it?
Could it be possible that the drive is running out of space?

Regards.

---

### Post by ian dobson on 2011-10-11
Hi,

What do you see in dmesg / syslog. Sounds as if the usb stick is dropping out or having write errors.

Regards
Ian Dobson

---

### Post by Xeijin on 2011-10-11
> **papibe said:**
> How big is the flash drive?
Did you create partitions on it?
Could it be possible that the drive is running out of space?

Regards.

It's a 16GB Flash Drive and the whole thing is dedicated to the ubuntu install, I let ubuntu automatically partition it during the install.

> **ian dobson said:**
> Hi,

What do you see in dmesg / syslog. Sounds as if the usb stick is dropping out or having write errors.

Regards
Ian Dobson

Here is the contents of dmesg and syslog, apologies for the length of each but I'm not sure how to interpret the information.

**[Contents of dmesg]("http://pastebin.com/0AJFyqiB")**

[B][Contents of syslog]("http://pastebin.com/DdApdb9y")

[/B]I've also included the contents of the 'mount' command below, to aid in interpreting the above logs:

**[Contents of mount]("http://pastebin.com/bCsJNPEn")**

Thanks,

---

### Post by papibe on 2011-10-11
There are several errors like this
```
[76357.046480] Buffer I/O error on device sdf1, logical block 9333
[76357.046586] lost page write due to I/O error on sdf1
```
And finally:
```
[76357.053571] Aborting journal on device sdf1-8.
[76357.053774] EXT4-fs error (device sdf1): ext4_journal_start_sb: Detected aborted journal
[76357.054041] EXT4-fs (sdf1): Remounting filesystem read-only
```
I'm not an expert on disks, but that sound like a hardware problem. May be you could boot into safemode and check the disk with 'fdisk'.

Another idea would be to take the USB stick and plug it to another Linux machine for external checking.

Just some thoughts,
Regards.

---

### Post by Xeijin on 2011-10-12
> **papibe said:**
> There are several errors like this
```
[76357.046480] Buffer I/O error on device sdf1, logical block 9333
[76357.046586] lost page write due to I/O error on sdf1
```And finally:
```
[76357.053571] Aborting journal on device sdf1-8.
[76357.053774] EXT4-fs error (device sdf1): ext4_journal_start_sb: Detected aborted journal
[76357.054041] EXT4-fs (sdf1): Remounting filesystem read-only
```I'm not an expert on disks, but that sound like a hardware problem. May be you could boot into safemode and check the disk with 'fdisk'.

Another idea would be to take the USB stick and plug it to another Linux machine for external checking.

Just some thoughts,
Regards.

Yes, certainly it seems clear the USB flash drive is at fault here. I think rather than going through the hassle of testing I will just dig up an old SATA drive and install Ubuntu to that instead of messing around with any more flash disks. Thanks for your help.

---

### Post by Xeijin on 2011-10-15
Just a quick post to say thanks, installed it on to a spare SATA hard disk and it's been running without issues for a couple of days now.

---

