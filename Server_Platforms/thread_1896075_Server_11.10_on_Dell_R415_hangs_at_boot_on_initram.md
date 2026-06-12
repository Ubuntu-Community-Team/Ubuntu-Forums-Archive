---
title: "Server 11.10 on Dell R415 hangs at boot on initramfs"
date: 2011-12-16
forum: Server Platforms
---

### Post by tomakCZ on 2011-12-16
Unless ctrl+d is pressed or exit is typed to hidden initramfs console in the backround, the server wouldn't boot. It waits on
```
sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 >
sd 6:1:0:0: [sda] Got wrong page
sd 6:1:0:0: [sda] Assuming drive cache: write through
sd 6:1:0:0: [sda] Attached SCSI disk
```
and on ctrld+d or exit it continues normal booting.

ANyone met this behaviour ? 

I am thinking of trying 10.04 if still unsuccessful, maybe 11.10 is not fully fit ... ?

---

### Post by SeijiSensei on 2011-12-16
I wonder if you're having the same problem as this fellow did:  [http://ubuntuforums.org/showthread.php?t=1889191](http://ubuntuforums.org/showthread.php?t=1889191)

What controller is in the machine?  Is it the SAS RAID controller that the other poster discussed? 

I installed Ubuntu Server 10.04 LTS successfully on an R410 with this card, though I've since switched to using CentOS 6 because it has better support for some applications I'm running.  If you don't want to switch distributions, try 10.04 LTS and see if that works better than 11.10.

LTS releases are always a good idea on servers.

---

### Post by tomakCZ on 2011-12-19
yes, it is SAS and I fixed that after some proper googling by adding rootdelay=190 to grub/kernel, they say there *'SCSI drives can take longer to spool up than most non-SCSI...'*, though, dunno why ubuntu is unprepared for it.

I will definitely install 10.04 in paralel - I have a partition ready for that, I just wanted to have 11.10 for comparison with the newest apps versions.

---

