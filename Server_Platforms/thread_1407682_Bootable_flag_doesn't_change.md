---
title: "Bootable flag doesn't change"
date: 2010-02-15
forum: Server Platforms
---

### Post by apkatt on 2010-02-15
Hi.

A week or two ago I installed Ubuntu Server 9.10 on a Intel DG945SEJT-based machine with two WD RE2-drives. I used unetbootin-windows-408.exe to to prepare a USB stick with the 32 bit version of the server version of Ubuntu. The installation went smooth without any problems.

Now when I'm trying to do the exact same thing to an almost identical server (larger HDD:s) I can't change the bootable flag to "on" on the physical raid partitions I create to host /.

I use the the following partition scheme: 10 GB /, 4 GB swap and the rest as /home. They're all on software-RAID1. Last time I did this (and many times before that) I was able to set the flag to "on".

When I press enter it just shows "updating filsystem.." etc. for some second but then nothing happens, the parameter is still on "off". This causes the whole installation to fail in the end due to an error when installing GRUB -> "can not install grub in /dev/sda "fatal error"".

My only conclusion is that the installer downloads some new files from the internet which causes this problem, as I said - nothing else is different except the harddrives (WD RE4-GP).

Anyone has any idea of what can be wrong?

Thanks in advance!

---

### Post by elfortunawe on 2010-10-25
Having the same problem installing Server 10.04 on LaCie NAS. The LaCie is supposed to take 64 bit, could that be the problem?

Apologies if this is a stupid question, I have no experience with these kinds of servers.

---

### Post by xoxbet on 2010-10-30
At the moment I am installing Ubuntu server with RAID1 using this guide:
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

And I also cannot change bootable flag for / partition. Any ideas? 64bit, 10.10...

Found it as bug:
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/477167](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/477167)

More than year ago submited and still not fixed?

---

### Post by chideock on 2010-10-30
I have been using 10.04.1 and 10.10 server installs. Just experimenting with an old computer installing RAID 0 and RAID 1. I found the same issue. However I finally decided to ignore that step and move on with the installs. It all worked without setting the flag.

If those are the versions you are using (I assume the desktop is the same) just ignore that step.

It would seem GRUB2 sets its own flag when it installs

---

### Post by cucu007 on 2010-11-15
> **chideock said:**
> I have been using 10.04.1 and 10.10 server installs. Just experimenting with an old computer installing RAID 0 and RAID 1. I found the same issue. However I finally decided to ignore that step and move on with the installs. It all worked without setting the flag.

If those are the versions you are using (I assume the desktop is the same) just ignore that step.

It would seem GRUB2 sets its own flag when it installs


I was in the process of installing this in a server i386 today and the damm bootable flag would not change to "on", can someone integrate this long-time bug into the actual release, I hope GRUB is able to pick up the /boot partition when I am done installing. Thank you. I will report back when I am done installing.

---

### Post by chideock on 2010-11-15
It seems that setting the boot flag is no longer required on recent Ubuntu versions. Ignor that step and proceed with the install.

I found that when I set my "/" to more than 15gig the install completed correctly. I was using 40 gig drives.

I would suggest the 4gig swap on a 10gig drive is too much. What is your RAM size? Use that size but even then 1gig for swap should be enough.

---

