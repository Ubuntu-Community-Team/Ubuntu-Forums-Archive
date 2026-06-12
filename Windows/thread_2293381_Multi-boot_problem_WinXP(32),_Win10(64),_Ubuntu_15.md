---
title: "Multi-boot problem: WinXP(32), Win10(64), Ubuntu 15.04(64)"
date: 2015-09-04
forum: Windows
---

### Post by raen on 2015-09-04
Hello, all.

I'm triple-booting (or trying to) on two hard drives: one has XP (32-bit) and 10 (64-bit) and one has Ubuntu 15.04 (64-bit). I followed all of the advice in setting it up and smoothing it out: I disconnected the Linux drive, created a partition and installed XP, installed 7 on the remaining partition, upgraded to 10. Could boot just fine into XP or 10. Disconnected the Windows drive, installed 15.04. Repaired the GRUB via the live USB after encountering
```

error: file not found.
grub rescue> _

```

I connected both drives and I am able to boot into Ubuntu or 10, but when I try to boot into XP, the whole system just restarts (possibly twice). As an experiment, I disconnected the Linux drive but when I turned on my computer, I got this:
```

error: no such device: 7d0a9ca8-f0b2-4089-899a-b0eefb93040d.
Entering rescue mode...
grub rescue> ls 
(hd0) (hd0,msdos2) (hd0,msdos1)
grub rescue>

```

I re-connected the Linux drive and successfully booted into 10, where I am now.

I can see the XP file system just fine (10 calls it "Local Disk (D:)" and Ubuntu calls it "90GB Volume"), but for some reason I just can't boot into it.

I assume this part is within normal parameters, but for the sake of full information, this is what my GRUB looks like:
```

GNU GRUB version 2.02~beta2-22ubuntu1
---
Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sdb1)

```

If I select Windows 7, it takes me to the Windows side where I can select via GUI whether I want Windows 10 or Earlier version of Windows, which had at one point took me into XP.

Can anyone help me fix this, please?
Thank you,
raen

---

### Post by yancek on 2015-09-04
Best to go to the site below and download and run boot repair from Ubuntu which will hopefully answer a lot of questions.  Select the option to Create a Bootinfo Summary, do not try to make any repairs and post the output here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Which drive is set to first boot priority in the BIOS?
What were you trying to do when you got the 'file not found' message?  Boot Ubuntu, windows?
Your Grub 'ls' output only shows one drive and you should have two drives with boot files?
The 'error no such device' is looking for a UUID (the long letter/number combination) which doesn't exist.  Probably changed sometime.
The Grub information you posted doesn't help as it is nothing but the menu shown on boot.  The boot repair will show more detailed output including drive/partition and boot files as well as there location.

> If I select Windows 7, it takes me to the Windows side where I can  select via GUI whether I want Windows 10 or Earlier version of Windows,  which had at one point took me into XP.


That's the way it generally works.     windows bootloaders are backward compatible so a newer release will boot an older but the reverse isn't true so if you installed 7 after xp it should boot.  Don't know what impact upgrading to 10 would have but if you could boot xp from the windows 7 boot menu, that might be the problem.

---

### Post by raen on 2015-09-04
> **yancek said:**
> Best to go to the site below and download and run boot repair from Ubuntu which will hopefully answer a lot of questions.  Select the option to Create a Bootinfo Summary, do not try to make any repairs and post the output here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Which drive is set to first boot priority in the BIOS?
What were you trying to do when you got the 'file not found' message?  Boot Ubuntu, windows?
Your Grub 'ls' output only shows one drive and you should have two drives with boot files?
The 'error no such device' is looking for a UUID (the long letter/number combination) which doesn't exist.  Probably changed sometime.
The Grub information you posted doesn't help as it is nothing but the menu shown on boot.  The boot repair will show more detailed output including drive/partition and boot files as well as there location.

That's the way it generally works.     windows bootloaders are backward compatible so a newer release will boot an older but the reverse isn't true so if you installed 7 after xp it should boot.  Don't know what impact upgrading to 10 would have but if you could boot xp from the windows 7 boot menu, that might be the problem.

That's the boot repair I used to fix the GRUB problem I mentioned in my original post. I had run the recommended repair and generated this URL: [http://paste.ubuntu.com/12259350](http://paste.ubuntu.com/12259350)   
The boot info summary is here: [http://paste.ubuntu.com/12277581/](http://paste.ubuntu.com/12277581/)

When I turn my computer on and spam F11, I get the following:
```

Please select boot device
---
SATA: ST1500DL003-9VT16L
SATA: ST1500DL003-9VT16L
Built-in EFI Shell
SATA: HL-DT-ST DVDRAM GH22NS90

```

The 'file not found' happened when I turned the computer on during an experiment in which I disconnected the Linux drive. Once I re-connected the drive, I was able to boot normally.

The GRUB 'ls' output was when I had experimented with disconnecting the Linux drive.

Is it possible the UUID was the disconnected drive?

I don't think I booted into XP while I was working on the 7 installation. I assume it's labeled '7' as a holdover of some kind. I really don't care what the label reads as long as it gets me where I want to go.

Thank you,
raen

---

### Post by yancek on 2015-09-04
> The 'file not found' happened when I turned the computer on during an  experiment in which I disconnected the Linux drive. Once I re-connected  the drive, I was able to boot normally.

That won't work because all your Ubuntu boot files are on the Linux drive and you have Grub boot code in the MBR of both drives.

> The GRUB 'ls' output was when I had experimented with disconnecting the Linux drive.

The info you posted earlier is correct.  It shows:  (hd0) (hd0,msdos2) (hd0,msdos1) 

The (hd0) is the MBR, the msdos1 and msdos2 entries are the first and second partitions of that drive.  The first partition is xp, the second is windows 10.  Note that the boot files on the first partition contain both xp and windows 10 boot files.  The xp files are different than vista and anything newer.

> s it possible the UUID was the disconnected drive?

Definitely is based on what you posted in your initial post, the UUID.  if you look in the boot repair output under Device  UUID you will see that is the first partition on the Ubuntu drive which contains the Ubuntu filesystem.

Do you have the Ubuntu drive set to first boot priority?

Scroll down in the boot repair output until you see this:    
sda1/boot/grub/grub.cfg

If you then scroll down the file, you will see an entry for windows 7 and at the end of the entry you will see "chainloader +1".  What that means is the
Grub bootloader is pointing to the IPL on the windows partition and from there, the window bootloader takes over.  Grub doesn't directly boot windows. 
 Your windows bootloader is the problem.  I don't use windows so all I can suggest is that you try some windows forum on how to boot xp from 10.

---

### Post by raen on 2015-09-04
All right, thank you. I'll take this to the Windows Ten forums.

---

