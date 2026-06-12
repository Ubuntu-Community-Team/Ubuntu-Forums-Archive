---
title: "Dual Boot Broken, Windows 7 won't Boot"
date: 2020-03-04
forum: Windows
---

### Post by jetman350 on 2020-03-04
Hey guys, I didn't take good notes so bear with me.  

Dual Boot Fix Optiplex 9010 SFF:  My assumption is that Windows 7 needs to be added to grub because I don't see it there.  But honestly it's been a long time since I had to fix a dual boot with windows.
 
This all started when I changed the CMOS Battery.  I think I made the mistake of inserting more RAM at the same time, never want to do too many things at once right, well I did.  
Number One Channel had two 4GB Chips and channel Two was empty.  I put two matching 8GB Chips in Channel Two, not same brand but matching.  Started the machine and went into the BIOS and Set the Time.  I then tried to boot but Windows 7 would not boot.  I rebooted and was able to boot Kubuntu from Grub.  Kubuntu sees all the RAM, but I removed the extra ram just to narrow down what went wrong.  I will try to list all the things I've done but my memory is not good. 

[LIST=1]
[*]Tried to Update Grub:
[*]Used Boot-Repair:  I ran the Standard fix first.  When that didn't work I ran the Fix MBR, when that didn't help I did the standard repair again.
[*]I've always used this to fix MBR first then go back and Repair Grub but this time it did not work.  And now I have Two Windows 7 Entries in Grub but 7 still won't boot.
[*]At one point I lost the ability to boot Kubuntu but fixed it somehow.
[*]I looked to the best of my knowledge in Grub and don&#8217;t see a Windows 7 Entry.  etc/default/grub
[*]At some point I also did a Windows 7 startup repair, ran it three times.  And rebuilt the boot sector at at least once using these links.
[/LIST]
[https://www.sevenforums.com/tutorials/104341-bootmgr-missing-fix.html](https://www.sevenforums.com/tutorials/104341-bootmgr-missing-fix.html)

When that didn't work I did this one.
[https://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](https://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
They both seemed to be succesful and this machine has had no problems in the past.

[Here is my boot-repair pastebin]("http://paste.ubuntu.com/p/BBVxY2gNCY/")

Got to go for now.  Hopefully someone will teach me to understand how grub works a little better.

---

### Post by oldfred on 2020-03-04
Changing CMOS battery reset many or most UEFI/BIOS settings. As does an update to UEFI or BIOS.
So you need to redo those settings. I update UEFI regularly so keep a list of several required and optional settings that I want.

Boot-Repair typically copies the main Windows boot files from its boot partition to main "c: drive" partition as users have deleted the boot partition not realizing it is required.

Update to grub then has found both sda1 & sda2 as bootable Windows.

Grub only boots working Windows, so if chkdsk or other repairs needed grub will not boot it.
And you may have to temporarily restore a Windows boot loader or use you Windows repair disk to fix Windows.

Note that Windows 7 has expired and you really need either upgrade it or remove it.
You do have newer UEFI system, but installs are in older BIOS boot mode.
Microsoft has required vendors to install Windows in UEFI boot mode since  when Windows 8 was released. A few Windows 7 systems were installed in UEFI boot mode.

Have you updated UEFI to latest version available?

---

### Post by jetman350 on 2020-03-04
oldfred, good to see you again.  I did look at the BIOS Settings and they all appear to be the same.  Gotta leave now, will be back later gotta go.  Didn't get an email for your post so need to look at my notifcations.

---

### Post by jetman350 on 2020-03-04
BIOS is up to date

I already repaired windows bootloader as you can see in my first post, twice.

I don't think it is a Functional UEFI System.  I thought some of the late Windows 7 computers came with somewhat neutered UEFI Systems.  Either way it is not is use so what is the issue?

I'm keeping this Windows 7 Install.  I have other computers, and clearly I have Kubuntu on this one also.  

Do you have any fixes, because I don't see any so far.

---

### Post by jetman350 on 2020-03-04
I'm not getting email notifications from this forum?

---

### Post by oldfred on 2020-03-04
I do not use email notifications. I just use search & my username.
There should be a setting somewhere.

You should update to newest available UEFI.
Spectre virus, repoline
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 


Not sure what issue you still have. 
Grub shows Windows.

---

### Post by jetman350 on 2020-03-04
I'm getting notifications now.  I reviewed all my settings but it was already set for me to get notifications from this forum, don't know why it wasn't the first time?
 
I said BIOS is all up to date!  And I don't' believe in all the Spectre Hype/Fear Mongering.  I have multiple computers without those patches and they all been free of any attacks.


> **jetman350 said:**
> And now I have Two Windows 7 Entries in Grub but 7 still won't boot.

This has nothing to do with UEFI, Spectre or Ditching Windows 7.  It is a Dual Boot Fix Question.  I have the Windows 7 Entries but it won't boot.  I can't imagine needing to run chkdsk or anything else on a pristine windows 7 install, new WD Black Drive (purchased directly from WD) and a new install of Kubuntu.  My only fault was not imaging stuff.

---

### Post by mastablasta on 2020-03-05
this is a windows issue. GRUB is before windows boot. so first it's BIOS, then grub, which only directs the PC where to boot from, then it hands over to Windows boot loader. 

so let's assume GRUB directs the boot to windows boot loader, what does windows say when it tried to boot? what does it mean windows does not boot? any error messages? are you saying that windows boots normally after you fix the windows master boot record?

pastebin is blocked where i work. is windows 7 on separate disk? if so, will it boot if you disconnect or disable linux disk drive? if it's not on separate disk, then when you fix the MBR form windows that action usually overwrites GRUB and then PC boots windows only.

---

### Post by oldfred on 2020-03-05
The disadvantage of BIOS dual booting is that when Windows needs repairs and then grub does not boot it, you have to temporarily restore the Windows boot loader to MBR to directly boot it. Then after fixing Windows restore grub to MBR.

With newer UEFI, it is like having multiple MBR, even with one drive. Then you can directly boot install of choice from UEFI. And then when grub will not boot Windows, you can boot it from UEFI.

Windows 7 is not supported by Microsoft anymore. You may need updated drivers or other updates that were in a previous install, but not in an older install DVD.

---

### Post by jetman350 on 2020-03-06
Not getting Notifications again, grrrrggggg haha.

Yes, I've repaired MBR First in the past, once windows boots then run the boot-repair tool and all was fixed.  

Every tool I've run says it is successful but still no 7 boot.  
I'm trying this now, #5
[https://askubuntu.com/questions/618326/how-do-i-manually-add-windows-7-to-grub-list](https://askubuntu.com/questions/618326/how-do-i-manually-add-windows-7-to-grub-list)

Windows 7 was a clean install with a Retail image that is known to be good over dozens of installs, and all updates have been accepted.  I'll keep plugging along because this was the Windows 7 Install that I wanted to keep around.  At the same time would love to run Linux off the same pc, but if I could just get Windows to boot I would be happy with just that.

Repeat, the guys on the Dell Forum told me this BIOS Does Not Support UEFI!  Though I have not tested that advice I will eventually.

Thanks

---

### Post by jetman350 on 2020-03-06
> **mastablasta said:**
> what does windows say when it tried to boot? what does it mean windows does not boot? any error messages? are you saying that windows boots normally after you fix the windows master boot record?

pastebin is blocked where i work. 

is windows 7 on separate disk? 
Sorry, I missed your post!

I get that screen that wants me to do a Startup Repair every time, but no matter how many times I do it still no Windows 7 Boot.

I can copy some of pastebin for you if you tell me which part you would like to see. 

Windows 7 is on same disk as Kubuntu and Before Kubuntu, as in installed before Kubuntu. 

I've successfully repaired MBR more than once, and don't think there was in issue with it to start with.

---

### Post by jetman350 on 2020-03-06
Here is what my etc/grub.d/40_custom looks like now as followed by this link, #5
[https://askubuntu.com/questions/618326/how-do-i-manually-add-windows-7-to-grub-list](https://askubuntu.com/questions/618326/how-do-i-manually-add-windows-7-to-grub-list)

```
[COLOR=#000000][FONT=&quot]#!/bin/sh[/FONT][/COLOR][COLOR=#000000][FONT=&quot][COLOR=#000080][COLOR=#000000]exec tail -n +3 $0[/COLOR][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=#000080][COLOR=#000000]# This file provides an easy way to add custom menu entries. Simply type the[/COLOR][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=#000080][COLOR=#000000]# menu entries you want to add after this comment. Be careful not to change[/COLOR][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=#000080][COLOR=#000000]# the 'exec tail' line above.[/COLOR][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=#000080][COLOR=#000000]menuentry "Windows 7 (loader) (on /dev/sda1)" {[/COLOR][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=#000080][COLOR=#000000]insmod part_msdos[/COLOR][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=#000080][COLOR=#000000]insmod ntfs[/COLOR][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=#000080][COLOR=#000000]set root='(hd0,msdos1)'[/COLOR][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot][COLOR=#000080][COLOR=#000000]chainloader +1[/COLOR][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]}[/FONT][/COLOR]
```

I'm still trying things, so if you want me to stop and follow some directions just say so.

I also implemented a script into grub that allows the last OS that was booted to boot again automatically next time computer is turned on.  I think I will remove that for now.

---

### Post by CelticWarrior on 2020-03-06
The most important question is still unanswered: Does ***windows boots normally after you fix the windows master boot record?***

If it does then reinstalling Grub should be enough to boot Windows and Ubuntu. If it doesn't then something else is wrong with that Windows and Grub obviously won't solve it, Grub can only boot working Windows.

And again, STOP using Windows 7.

---

### Post by jetman350 on 2020-03-06
[I][B][COLOR=#000000]"The most important question is still unanswered: Does [/COLOR]windows boots normally after you fix the windows master boot record?"
[/B][/I]It has been answered multiple times? NO, NO, NO.  Windows 7 goes to the black screen that asks to do a Startup Repair or Start Windows normally.

[I][B]"And again, STOP using Windows 7"
[/B][/I]Please refrain from telling me to "STOP" using Windows 7, it's annoying, unhelpful and has nothing to do with the issue.

I've Run chkdsk /r from install media also and there were no issues.

---

### Post by CelticWarrior on 2020-03-06
> **jetman350 said:**
> It has been answered multiple times? NO, NO, NO.  Windows 7 goes to the black screen that asks to do a Startup Repair or Start Windows normally.

So you MUST, MUST, MUST repair it by booting Windows installation media. Specific instructions for that can an should be obtained from specialized Windows support resources. Ubuntu Forums certainly ISN'T one of those resources. 
This problem is entirely Windows. Again, **Grub can only boot working Windows**, Grub will NOT and CANNOT fix your Windows 7 corruption, you need to repair or reinstall it. Then, and only then, you should reinstall Ubuntu or just Grub. Are we clear now?


> Please refrain from telling me to "STOP" using Windows 7, it's annoying, unhelpful and has nothing to do with the issue.
I won't, it's for your own and everybody else's good.
Obsolete OSes without security updates are very dangerous if used connected to the internet. Even running it in a VM isn't recommended but at least it's a little more contained and snapshots are easy to use if you must recover a working system after a problem that is not a question of "if", it's a question of "when", happens.

In summary, I hope you realize you're asking us to solve a problem that is completely foreign to Ubuntu and on top of that is about an obsolete version of Windows!

---

### Post by jetman350 on 2020-03-06
Okay, here is the fdisk outcome.  Look at where the boot loader is, on Windows 7 C Drive!


Just noticed this also, is this normal?  HPFS/NTFS/exFAT


I'll have to boot my other dual boot and see.


Also, in Terminal this is all in RED, the line at the bottom:  [COLOR=#ff0000]Partition 4 does not start on physical sector boundary.


[/COLOR]```
[COLOR=#000000][FONT=&quot]Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors[/FONT][/COLOR][COLOR=#000000][FONT=&quot]Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xf3ed0f9d

Device Boot Start End Sectors Size Id Type
/dev/sda1 2048 206847 204800 100M 7 HPFS/NTFS/exFAT
/dev/sda2 * 206848 314785791 314578944 150G 7 HPFS/NTFS/exFAT
/dev/sda3 314785792 364785663 49999872 23.9G 83 Linux
/dev/sda4 364787710 564785151 199997442 95.4G 5 Extended
/dev/sda5 364787712 564785151 199997440 95.4G 83 Linux

Partition 4 does not start on physical sector boundary.[FONT=monospace]
[/FONT]
[/FONT][/COLOR]

```

---

### Post by oldfred on 2020-03-06
Linux does not tell which type of Windows format it is.

Phyiscal sector boundary is a requirement for newer 4K drives.  Most now are gpt so if you have that message with a gpt partition drive it is an issue.
But with MBR, you cannot write into the extended partition, only primary & logical partitions. So you get an error on the extended partition and can ignore it. 

Still only a Windows issue. A Windows 7 install disk is probably obsolete as it would do many updates online. But now that it is not supported, you do not get those updates. May be drivers, or just fixes to various issues. 

Since really Windows moving to Windows sub-forum.

---

### Post by CelticWarrior on 2020-03-06
> **jetman350 said:**
> Look at where the boot loader is, on Windows 7 C Drive!


Just noticed this also, is this normal?  HPFS/NTFS/exFAT

Yes, pretty normal.
No, not a bootloader problem. When the OS starts the bootloader (or chain of bootloaders) already did its job correctly. If problems arise at this stage like the ones you already mentioned that mean a problem in that OS' system partition, nothing to do with bootloaders, certainly not with Grub that merely chainloads to the Windows bootloader, and likely not with the Windows bootloader itself because it points to the correct location and Windows starts.
[B]Whatever happens after the bootloaders release control to a given OS, it's exclusively the fault of that OS.

[/B]This has been explained multiple times and in different ways: **It's a Windows problem.** You need to boot Windows installation media and use the recovery environment to try to repair Windows or, failing that, reinstall.

---

### Post by jetman350 on 2020-03-06
I understand, but just can't imagine how Windows got messed up just from changing the CMOS and Adding RAM?

Most Windows guys don't know about Dual Booting so I'm not to hopeful they will help.  And I ran chkdsk C: /r and no errors.  I guess I need to poke around further, maybe run sfc /scannow.  I would really like to recover this system as I have so much time into it.  I will forever Image it after this...Doh!

---

### Post by jetman350 on 2020-03-06
> **oldfred said:**
> Linux does not tell which type of Windows format it is.

Phyiscal sector boundary is a requirement for newer 4K drives.  Most now are gpt so if you have that message with a gpt partition drive it is an issue.
But with MBR, you cannot write into the extended partition, only primary & logical partitions. So you get an error on the extended partition and can ignore it. 

Still only a Windows issue. A Windows 7 install disk is probably obsolete as it would do many updates online. But now that it is not supported, you do not get those updates. May be drivers, or just fixes to various issues. 

Since really Windows moving to Windows sub-forum.
Got it!

Thanks, it is MBR

Your moving this?  I see, you already moved it haha.  Okay, hope I can get er fixed at some point.  No rush as I have more computers but I have lots of time in this and was wanting to keep using Windows 7 offline for as long as possible.  I always preach to others to Image, Image, Image.  But I couldn't imagine this happening to me lol.

---

### Post by oldfred on 2020-03-06
Old since BIOS boot, but shows how BIOS & Windows boots.

[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html](http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html)

---

### Post by jetman350 on 2020-04-24
Sorry, but I had forgot about this thread.  I was able to fix it by switching from RAID to AHCI.  Removing the CMOS was the culprit, and I forgot Dell uses RAID by default on the old optiplex's.

---

