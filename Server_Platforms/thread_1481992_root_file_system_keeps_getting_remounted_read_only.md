---
title: "root file system keeps getting remounted read only"
date: 2010-05-13
forum: Server Platforms
---

### Post by atconc on 2010-05-13
Hi All

I have a 9.04 64bit Ubuntu server that I use for a home file server and for downloading duties, every few days the root filesystem gets remounted as read only, usually requiring a reboot and fsck to get everything running again.  The box is tucked away in the roof space to keep the noise down so it's a bit of a pain to keep pulling it out to get console access.

Can anyone help troubleshoot what might be causing this?

/ is on a raid 1 array on 2 8GB usb sticks 

last few lines of DMESG 

EXT3-fs error (device md3): ext3_journal_start_sb: Detected aborted journal

```
[632280.290419] journal_bmap: journal block not found at offset 23180 on md3
[632280.290470] Aborting journal on device md3.
[632280.582145] ext3_abort called.
[632280.582173] EXT3-fs error (device md3): ext3_journal_start_sb: Detected aborted journal
[632280.582227] Remounting filesystem read-only
```


Also on a sideline but related, are there any solutions to get console access via LAN when the box isn't starting up properly (I assume no but worth asking?)

Thank

---

### Post by arrrghhh on 2010-05-13
> **atconc said:**
> Also on a sideline but related, are there any solutions to get console access via LAN when the box isn't starting up properly (I assume no but worth asking?)

There's no way to do this with software.  You'd need a DRAC (Dell Remote Access Controller) or something similar.  KVM, something like that.

As for the main problem... I'm not too sure.  It seems there may be something bad on those USB sticks... I've never setup RAID1 on USB sticks, I must apologize I will be no help here.

---

### Post by atconc on 2010-05-13
> **arrrghhh said:**
> There's no way to do this with software.  You'd need a DRAC (Dell Remote Access Controller) or something similar.  KVM, something like that.

As for the main problem... I'm not too sure.  It seems there may be something bad on those USB sticks... I've never setup RAID1 on USB sticks, I must apologize I will be no help here.

Thanks for the reply, I thought so about the remote access - can't run any software without the OS running :)

I used a usb stick for the O/S to keep it separate from the file storage but was worried about how reliable it would be so I went for RAID 1.  It shouldn't look any different to a normal drive I don't think

---

### Post by arrrghhh on 2010-05-13
I do the same, separate the file storage from the OS - but I do it with traditional hard drives.  Never had a problem with that setup, albeit the USB key solution is interesting.  

I just worry about the inhernet issues with flash memory and frequent re-writes on the same section of the flash board.  This is the issue you *may* be running into, but obviously it's just pure speculation at this point.  How long has this server been running with this configuration?

---

### Post by atconc on 2010-05-13
> **arrrghhh said:**
> I do the same, separate the file storage from the OS - but I do it with traditional hard drives.  Never had a problem with that setup, albeit the USB key solution is interesting.  

I just worry about the inhernet issues with flash memory and frequent re-writes on the same section of the flash board.  This is the issue you *may* be running into, but obviously it's just pure speculation at this point.  How long has this server been running with this configuration?

I don't have any free HD bays left :) another reason for using the USB.

I guess it's been running like this for about 9months these problems only started the last few weeks.  I'm inclined to think the flash drives are wearing out (no real problem, they were cheap and  I thought this would happen eventually) but would like to prove it before going through the effort of replacing them.

---

### Post by arrrghhh on 2010-05-13
How about try and replacing one?  


Hopefully someone with more experience chimes in, I am not going to be much help here.  Sorry.

---

### Post by soltanis on 2010-05-13
If you installed a journaling file system on the Flash drives, that might've been a bad idea. Journaling will only wear down the read/write cycles on the disks faster. Maybe for your next drives, you should try ext2?

As for starting up the computer remotely, you can use Wake On Lan (WOL) which can be enabled in the BIOS. So long as your computer is connected to a power supply (and you know its MAC Address) you should be able to start it up with a magic packet.

---

### Post by arrrghhh on 2010-05-13
> **soltanis said:**
> If you installed a journaling file system on the Flash drives, that might've been a bad idea. Journaling will only wear down the read/write cycles on the disks faster. Maybe for your next drives, you should try ext2?

As for starting up the computer remotely, you can use Wake On Lan (WOL) which can be enabled in the BIOS. So long as your computer is connected to a power supply (and you know its MAC Address) you should be able to start it up with a magic packet.

He's not looking to start the computer remotely, but manage it remotely when it fails to boot :D

As for the non-journaling FS that seems like a bad idea... but I guess on flash drives it's not?  Not sure how that works... what do most people do that run the OS on a flash key?

---

### Post by atconc on 2010-05-20
I have an update

I removed the 2 flash drives that were running as the boot drive and managed to cram an old IDE drive into the case.

Did a fresh install to ubuntu server 10.04 and ext4, today I have a similar problem again

[17339.914571] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[17339.914891] ata1.01: waking up from sleep
[17339.915089] ata1: soft resetting link
[17340.141271] ata1.01: configured for UDMA/100
[17340.141283] ata1: EH complete
[17342.034468] end_request: I/O error, dev sda, sector 25480216
[17342.034699] Aborting journal on device sda1-8.
[17342.054366] EXT4-fs error (device sda1): ext4_journal_start_sb: Detected aborted journal
[17342.054754] EXT4-fs (sda1): Remounting filesystem read-only


However this is a really old IDE drive I found in a cupboard so it could be a bad drive and a coincidence I guess?

Any ideas

---

### Post by arrrghhh on 2010-05-20
Honestly sounds like a bad drive... Do you have any boot disks like hiren's or UBCD that can check the HDD health?

---

