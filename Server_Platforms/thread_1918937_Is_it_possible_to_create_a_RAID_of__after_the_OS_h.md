---
title: "Is it possible to create a RAID of / after the OS has been installed?"
date: 2012-02-01
forum: Server Platforms
---

### Post by diablo75 on 2012-02-01
So I was wondering if it might be possible to do a "normal" install of a Linux OS on a single drive and then add a second drive later that just happens to be identical, partition it with the same layout as the original drive and turn the two into a RAID 1 array.  This is actually a generic Linux question that I wanted to post here because this forums rocks and people respond fast.

What I'm actually trying to setup is CentOS 5 with a software RAID.  I was previously successful in doing this with Ubuntu 10.04 LTS but unfortunately the third party software I needed to install after setting the OS up required a package that's no longer available in the repositories (I couldn't tell you which dependency; the actual software end of this is someone elses responsibility and they subsequently recommended trying CentOS because they know from their own experience that it works for their purposes).  Problem is that when I try to install CentOS following their instructions (which are easy to follow), the installer locks up while partitioning/formatting and stays that way for days and days.  I believe both OS's use mdadm as their software RAID controller.

---

### Post by iiiears on 2012-02-02
Hello,

Was this what you were looking for?

[http://ubuntuforums.org/showthread.php?t=713936](http://ubuntuforums.org/showthread.php?t=713936)

---

### Post by rubylaser on 2012-02-02
These [directions]("http://www.pinguin-systeme.net/faq/linux_installation_configuration/how-can-i-convert-my-running-system-to-a-raid-1-system/") will work fine.  You'll want to do the grub portion per the [Ubuntu wiki]("https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles#Boot_Loader").

---

### Post by diablo75 on 2012-02-02
> **rubylaser said:**
> These [directions]("http://www.pinguin-systeme.net/faq/linux_installation_configuration/how-can-i-convert-my-running-system-to-a-raid-1-system/") will work fine.  You'll want to do the grub portion per the [Ubuntu wiki]("https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles#Boot_Loader").

This looks like it'll work for me but I have a question.  Step four says:

"Change the partition type on all partitions of /dev/sdb to 0xfd (Linux raid autodetect)"

But it doesn't show how to do that; what command to type.  Am I overlooking something?

Before I try this I'm going to make one more attempt at installing CentOS as I have been in the past, but failed for a stupid reason:  I've been skipping the command at the beginning of the guides (dd if=/dev/zero of=/dev/sda bs=512 count=64
&& dd if=/dev/zero of=/dev/sdb bs=512 count=64) because I had a bad feeling it was going to take forever to execute.  So I'll give one more go without taking shortcuts and let you know if that makes a difference.

---

### Post by rubylaser on 2012-02-03
> **diablo75 said:**
> This looks like it'll work for me but I have a question.  Step four says:

"Change the partition type on all partitions of /dev/sdb to 0xfd (Linux raid autodetect)"

But it doesn't show how to do that; what command to type.  Am I overlooking something?

Before I try this I'm going to make one more attempt at installing CentOS as I have been in the past, but failed for a stupid reason:  I've been skipping the command at the beginning of the guides (dd if=/dev/zero of=/dev/sda bs=512 count=64
&& dd if=/dev/zero of=/dev/sdb bs=512 count=64) because I had a bad feeling it was going to take forever to execute.  So I'll give one more go without taking shortcuts and let you know if that makes a difference.

To flag the paritions properly, you'd do something like this.

```
fdisk /dev/sdb
```
You'd just change them with fdisk like this.
```
root@debian:~# fdisk /dev/sdb

Command (m for help): t
Partition number (1-5): 5
Hex code (type L to list codes): fd
Changed system type of partition 5 to fd (Linux raid autodetect)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
```

---

