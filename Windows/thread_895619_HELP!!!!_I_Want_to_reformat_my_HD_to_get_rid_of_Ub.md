---
title: "HELP!!!! I Want to reformat my HD to get rid of Ubuntu"
date: 2008-08-20
forum: Windows
---

### Post by mdshaver on 2008-08-20
I tried Ubuntu 8.04 because I didn't have a copy of Windows after replacing my HD. It seemed to have a user-friendly look but I have found that it is not for those whom are not computer saavy. I would love to learn more about it but I simply don't have the time at the moment (in the middle of my PhD qualifying exams). I have a burned copy of XP with legit license but can't boot from the disc with Ubuntu. I just want to get reformat the drive to get rid of it and put XP back on but don't know how. Ubuntu has given me problems with my wireless card, avi playback, deleting write-protected files, occasional freezing, and a hell of time booting up. I don't have the time to figure out these things that should be very simple.

Please HELP!!!!! I am not computer savvy so please dumb it down for me and take me through step by step.

Thank you so much in advance!

---

### Post by Flyingjester on 2008-08-20
if you have the xp disk it should be as easy as restarting the computer with the disk in... if it's not, then you have to change your bios settings to boot from CD first

---

### Post by Paqman on 2008-08-20
Just boot from your XP disk and when it gets to the part showing the partitions just hit "D" on all of them and it'll delete them. You'll also need to format your drive back to NTFS. 

Then when you install Windows it'll be as if Ubuntu was never there.

Is there anything we can help you with on Ubuntu before you take such a drastic step?

---

### Post by mlentink on 2008-08-20
Boot up with your legitimate copy of Windows XP. You can do this by pressing the boot-options key at bootup time (shortly after you have switched on your machine) The exact key depends on the make of your machine, and could be e.g. F11. It will allow you to boot from cd. As soon as the XP-installer starts up, you can let it do its lengthy song and dance...

---

### Post by Canis familiaris on 2008-08-20
Are you installing Windows XP or VIsta?

Anyway irrespective of whicever Windows you use, here is your way:

1) Insert the Ubuntu Live CD.
2) Go to System->Administration->Partition Editior
3) Right Click Each of the Partition and Click Delete
4) Click on the Apply Button (with a green arrow).
5) The operations would them start and complete.
6) Restart and install Windows
7) Best of Luck

---

### Post by madcow72 on 2008-08-20
mdshaver,  as FlyingJester said, start up your computer with the XP disk in.  If it doesn't boot automatically, then your BIOS isn't configured to boot from the CD.  If that's the case, try hitting "Delete" during the boot up screen, or watch the screen when you turn on the computer for instructions like, for example "F11  Settings", in which case, hit F11.

Once there, change the Boot Startup menu so that it first boots from CD Rom and then your hard drive.

Once you boot into the Windows CD, it should ask you straight-forward questions like "Do you want a Fresh Install"  "Which hard drive/partition?"  You should be able to choose your entire hard drive and format it to NTFS for the install.  After that, it's a walk in the park...(Until you want to actually USE Windows, of course... ;)

---

### Post by mlentink on 2008-08-20
> **Anurag_panda said:**
> 
3) Right Click Each of the Partition and Click Delete

GParted will not allow such an operation on a mounted partition. You need to unmount the partition first.

---

### Post by Gannon8 on 2008-08-20
I don't think the LiveCD mounts partitions on the hard drive automatically, except the swap partition, but it will not automount that, so you just unmount that and your good.

---

### Post by mdshaver on 2008-08-20
Thanks for your quick reply! I changed my BIOS setting to place my cd/dvd drive as the first in the sequence but it still won't boot. I know the disk is good because it reads fine in Ubuntu. Any more idea? Please!

---

### Post by mlentink on 2008-08-20
Just out of curiosity: what exactly do you see when you insert that disk while running under Ubuntu? Does it perhaps shou one big .iso file?
I suspect that cd is not bootable...

---

### Post by mdshaver on 2008-08-20
No, it's not simply an .iso file. All the standard folders can be viewed within the XP directory (e.g., DOCS, i386, SUPPORT, VALUEADD, etc.). Additionally, I double-clicked on the setup.exe file and it boots to the windows installer within Ubuntu but it will not allow you to get past that screen, presumably, because I am within Ubuntu.

---

### Post by xouns on 2008-08-20
Yes, probably.

Reboot, wait, and when the computer says

"Press a key to boot from CD"

Press a key!
Follow all, simple as that. Enjoi

ps; it might not be a good idea to delete all partitions, I expect you have a data/ backup partition. Just delelte the partition with either unkown or Ext2/3 format and format that one.

---

### Post by mdshaver on 2008-08-20
I have already tried to boot from cd even with the correct BIOS boot sequence. For whatever reason, it will not boot from cd.

---

### Post by philinux on 2008-08-20
How did you burn the disk. If the source was an iso file it needs to be burned as an image.

It sounds like it's not bootable.

---

### Post by mdshaver on 2008-08-20
No, no. The disc is definitely good. It belongs the department at my university and has been used on several computers. It reads fine in Ubuntu but I can't boot from it. Is it possible that Ubuntu is somehow interfering with my ability to boot from the disc. I know this doesnt seem likely but I dont know how else to explain it.

---

### Post by philinux on 2008-08-20
> **mdshaver said:**
> No, no. The disc is definitely good. It belongs the department at my university and has been used on several computers. It reads fine in Ubuntu but I can't boot from it. Is it possible that Ubuntu is somehow interfering with my ability to boot from the disc. I know this doesnt seem likely but I dont know how else to explain it.

Ok so that clears that up.

What happens with this disc inserted, does grub just pop up and load ubuntu completely ignoring the disk. Even though your boot order is cdrom first?

---

### Post by perlluver on 2008-08-20
A good burn of Windows XP, should be able to boot, even with Ubuntu on the drive, I have done it plenty.  Seems like the disk isn't bootable.  You will need another copy, or will have to make sure it gets direct burned from the other copy.  e.g., copy disc to disc.  Sorry can't be of more help.

---

### Post by linuxguymarshall on 2008-08-20
Why would you want to get rid of Ubuntu?

---

### Post by mdshaver on 2008-08-20
> **philinux said:**
> Ok so that clears that up.

What happens with this disc inserted, does grub just pop up and load ubuntu completely ignoring the disk. Even though your boot order is cdrom first?

Yes, after selecting to boot from the CD drive, grub pops up and loads Ubuntu

---

### Post by Titan8990 on 2008-08-20
He explained that in his initial post...


OP: Get a real XP disc and not a burnt one. If you computer will boot to the Ubuntu disk but not the Windows then there is a problem with the burnt Windows CD.

---

### Post by xouns on 2008-08-20
> **perlluver said:**
> A good burn of Windows XP, should be able to boot, even with Ubuntu on the drive

Hmmm, I'm putting my money on a wrong boot order. Have you saved after editing the boot order (usually F12)?

---

### Post by mlentink on 2008-08-20
Just another question. What happens when you boot your Ubuntu Live CD?

---

### Post by perlluver on 2008-08-20
> **mdshaver said:**
> Yes, after selecting to boot from the CD drive, grub pops up and loads Ubuntu

Most definitely sounds like a bad burn, you will need an original copy of Windows.

---

### Post by mdshaver on 2008-08-20
I have saved my settings after changes the BIOS sequence. I have triple-checked this. I am still skeptical that it is a bad burn for previously stated reasons.

---

### Post by Titan8990 on 2008-08-20
If one disc will boot and another will not then the disc is bad and that is all there is to it.

---

### Post by perlluver on 2008-08-20
Ok, even though the CD shows up in Ubuntu, and has been used before, it may have lost it's ability to boot from the CD, when it was copied to another CD.  Microsoft, has a built in burn proof feature, where the disc can be copied, but when it is, it loses the boot portion.  I have no better way to explain it.

---

### Post by xeth_delta on 2008-08-20
> **linuxguymarshall said:**
> Why would you want to get rid of Ubuntu?

I believe that he stated he does not have time to learn about it right now, even though he would like to.

Don't get me wrong, I love Linux and cannot stand working on Windows (which I practically never do anymore), but every person should use what they prefer and feel more comfortable with :)

That said, I do see your point, in that he could use dual boot to facilitate the transition by having both OSs installed. ;)

---

### Post by xeth_delta on 2008-08-20
To the OP. Is it only the Windows XP CD that cannot boot? Have you tried, for example another Windows CD or an Ubuntu CD?

---

### Post by mlentink on 2008-08-20
> **Titan8990 said:**
> If one disc will boot and another will not then the disc is bad and that is all there is to it.

Exactly! That's why I asked to try and boot the Ubuntu Live CD (or another cd that you know will boot on ***your*** system)

---

### Post by tuxxy on 2008-08-20
>  Ubuntu has given me problems with my wireless card, avi playback, deleting write-protected files

Did you read the wirelss howto? 
did you install the correct driver package for video playback? 
did you setup your user with admin privs?

---

### Post by xouns on 2008-08-20
Agree with Titan and perlluver.

---

### Post by mekgp on 2008-08-20
Just because you can "read" whats on a Windows CD doesn't mean it will boot from it.  Usually, burning a WinCD doesn't include the hidden files because of anti-piracy methods built in from Windows.  
Just skip the hate-hell-and-discontent and get a legit, licensed, boxed version of XP somewhere and boot off of it.  
I'll put the office box of donuts to bet the burnt copy is nothing more then a coaster for other then viewing/copying files from....  :-k :neutral:

ps: And NOT an upgrade version of Windoze...unless of course you've a copy of some previous Windoze version like 2k, ME, 95 which doesn't appear the case.  :(

---

### Post by mdshaver on 2008-08-20
Thanks for all the responses.

I think (but am not 100% sure) that my burnt copy of Ubuntu will boot. As one previous poster mentioned, a burnt copy (although legit), may lose its boot capabilities but will not affect its ability to upgrade from other Windows OS's. I have figured out how to change write-protection status on files (Thanks Ubuntu for non-geeks) but it seems unnecessarily cumbersome. As far as the playback of avis, they work at first but then do nor resume playback once paused and restarted. My wireless connection can detect signal strength and even connect to my neighbor's unsecured wireless (only doing this as a test) but will not allow internet access. I believe I have an Intel Broadcom card and I have seen that it is quite difficult to get it setup (beyond my present knowledge). My biggest concern at this point is that my computer will not start with Ubuntu when I first start it each day unless I first enter setup (F12) and then exit. It also reboots and freezes sometime. Is this a compatibility issue with my hardware of did i get a bad burn of the software when installing?

---

### Post by philinux on 2008-08-20
Well try your live cd. If it boots you'll have your answer

---

### Post by xeth_delta on 2008-08-20
Concerning write permissions, if the files are in your home directory you should be able to access and modify them without any needed changes.
By the other hand, if you are talking about files located elsewhere in the filesystem (except /tmp and /var/tmp), you are actually not supposed to be able to write to them as a regular user. It is part of the security model (and one that works pretty well, IMHO), and only the root/admin account has the right to modify them. In Ubuntu you use sudo for temporary administrative purposes.

I don't really think you need F12 to boot. Linux is not that fragile, as I can testify after many years of using it.

The freezes, well that's another issue, and driver related, most likely. If you want help on that, let us know, and someone will most likely chime in and help you out. Of course, you will need to be more specific regarding the hardware you use. :)

---

### Post by Titan8990 on 2008-08-20
> My biggest concern at this point is that my computer will not start with Ubuntu when I first start it each day unless I first enter setup (F12) and then exit. It also reboots and freezes sometime. Is this a compatibility issue with my hardware of did i get a bad burn of the software when installing?

If F12 is your boot menu (usually is) then you just need to move your HDD up in your boot order.

---

### Post by mekgp on 2008-08-20
> **mdshaver said:**
> Thanks for all the responses.

..... It also reboots and freezes sometime. Is this a compatibility issue with my hardware of did i get a bad burn of the software when installing?

Is this computer you're battling with use an ATI video card?  If so, the driver more then likely installed when you setup Ubuntu is bad.  It has to do with the 3D acceleration of graphics.  There is discussion of this issue already in the forums.  Check this thread out when you've got a minute...

[http://ubuntuforums.org/showthread.php?t=888268](http://ubuntuforums.org/showthread.php?t=888268)

That is of course you decide to keep using Ubuntu Linux, which is ALWAYS a good choice! ;) ;)

---

### Post by madcow72 on 2008-08-20
Because the disk is not bootable, doesn't mean you can't install from it.  You'll need a disk that IS bootable to start, and then you can get this going.  Not sure what your computer looks like, (how many CD/DVD drives, floppy, etc.)  But check out [bootdisk.com]("http://www.bootdisk.com") to download an iso of a boot cd.  If you're still in Ubuntu, open Burn one of 'em, it shouldn't really matter, as long as it contains CD support.  Then, with this cd in the bootable drive, restart your computer.  Load into DOS, then type (for example):
```
e:
```  (where "e" is the drive letter of your second drive containing the Windows CD.)
Once at the prompt for the Windows CD, do:
```
cd i386\
winnt
```

This will start the Windows install.  If it asks for Smartdrive (will greatly speed up the install.)  I have attached it (44kb) to this post.

Good luck!

---

### Post by alecz20 on 2008-08-20
I just want to add some argument to the (legit) Windows CD not being boot-able.

Our University (McGill) gives Windows Licenses to students in our department for free. I ordered one, and I chose to "pick-up" the CD instead of downloading the .ISO image.

I got the CD (a copy) from the school, and could not boot. My friend got the .ISO, and burnt it; that booted well.

So even though the Windows copy was licensed and given by the university, and whatnot, it may not be Boot-able.

If you were able to install Ubuntu from the live CD, and did not change any BIOS settings after that, then any Original Windows CD will work.

As far as your wireless connecting and not giving internet, can you ping the router?
Usually for Dlink:
```

ping 192.168.0.1

```
or 
Usually for Linksys:
```

ping 192.168.1.1

```

I wonder how many of your problems will be solved by installing XP.

Also note that installing XP on computers "Designed for Vista" may prove very hard since XP does not always have SATA drivers for the HDD.

Good luck, and we're here to help!

---

