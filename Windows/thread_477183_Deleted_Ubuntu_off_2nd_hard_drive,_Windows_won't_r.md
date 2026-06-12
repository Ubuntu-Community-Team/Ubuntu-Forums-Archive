---
title: "Deleted Ubuntu off 2nd hard drive, Windows won't recognize it"
date: 2007-06-18
forum: Windows
---

### Post by Libertine on 2007-06-18
Hello everyone, I had a dual-booting system going for awhile (Windows on one hard drive, Ubuntu on the other) until for whatever reason I decided to delete Ubuntu and use the 2nd hard drive for extra storage. I successfully removed Ubuntu on the 2nd hard drive using the LiveCD and removed all partitions on it, but the drive isn't showing in the Windows Disk Management Tool or the Device Manager. My BIOS and the LiveCD do recognize it though.

Any help on how I can get this drive showing in Windows? Thanks! :KS

---

### Post by renzokuken on 2007-06-18
you will have to reformat it as ntfs/fat32, as windows doesnt recognise the linux filesystems by default......

gparted live cd is a good way of formatting drives

---

### Post by Libertine on 2007-06-19
> **renzokuken said:**
> you will have to reformat it as ntfs/fat32, as windows doesnt recognise the linux filesystems by default......

gparted live cd is a good way of formatting drives

I formatted it to NTFS using GParted, but Windows still isn't recognizing it...:o

---

### Post by renzokuken on 2007-06-19
weird.....

in XP click on the start menu, then RIGHT click on My Computer and select **Manage**.

when the window comes up, select Disk Management on the left. do your all your drives/partitions show up in there?

---

### Post by Libertine on 2007-06-20
> **renzokuken said:**
> weird.....

in XP click on the start menu, then RIGHT click on My Computer and select **Manage**.

when the window comes up, select Disk Management on the left. do your all your drives/partitions show up in there?

Only the drive that Windows is installed on shows...

---

### Post by karellen on 2007-06-20
try with partition magic. it never failed me. I formated ext3 to fat32/ntfs, merged partiions, redistribute free space and windows recognized all the changes without any problem

---

### Post by smoker on 2007-06-20
hi, you could try going to the support site of your hard drive manufacturer and download a bootable version of their diagnostic tool, with these you can normally do what used to be called a 'low level format', it will also probably check the drives smart attributes, etc, and let you know the drive is working fine or not,

best of luck

---

### Post by Libertine on 2007-06-20
> **karellen said:**
> try with partition magic. it never failed me. I formated ext3 to fat32/ntfs, merged partiions, redistribute free space and windows recognized all the changes without any problem
I just tried with Partition Magic but it doesn't recognize the drive either. :(

[QUOTE=smoker]hi, you could try going to the support site of your hard drive manufacturer and download a bootable version of their diagnostic tool, with these you can normally do what used to be called a 'low level format', it will also probably check the drives smart attributes, etc, and let you know the drive is working fine or not,

best of luck
[/QUOTE]
This also didn't recognize my drive...I'm starting to think I should just install Ubuntu on it again.

---

### Post by smoker on 2007-06-20
> **Libertine said:**
> I just tried with Partition Magic but it doesn't recognize the drive either. :(

This also didn't recognize my drive...I'm starting to think I should just install Ubuntu on it again.

it's beginning to look like the drive is 'fubar' despite the live-cd being able to detect it. can i ask why you deleted ubuntu, eg, were you having problems with it, which may be connected to a failing drive?

anyway, some stuff to try, and i'm assuming your drives are IDE, on the same IDE channel? even though both drives show up in the bios, double check that the 'master drive is at the end of the ide connecter, and the 'slave' drive is attached to the middle of the cable. check that the jumper settings on each drive is set correctly to master and slave. if all is ok in this regard, and the drive is still not detected by the diagnostic app, or windows, then change the jumper settings in both drives to CS (cable select), and try again.

if none of that works, disconnect your windows drive, set the spare drive to 'master' and connect to the end of the ide ribbon, and boot from the hard drive manufacturers app and see if the drive is detected then! if still not detected, i would try the drive as a slave in another computer, if not detected there, then i think it is scrap. if it is detected, then you may be looking at a problem on your motherboard.

best of luck

ps - if your drives are sata post back.

---

### Post by Libertine on 2007-06-21
> **smoker said:**
> it's beginning to look like the drive is 'fubar' despite the live-cd being able to detect it. can i ask why you deleted ubuntu, eg, were you having problems with it, which may be connected to a failing drive?

anyway, some stuff to try, and i'm assuming your drives are IDE, on the same IDE channel? even though both drives show up in the bios, double check that the 'master drive is at the end of the ide connecter, and the 'slave' drive is attached to the middle of the cable. check that the jumper settings on each drive is set correctly to master and slave. if all is ok in this regard, and the drive is still not detected by the diagnostic app, or windows, then change the jumper settings in both drives to CS (cable select), and try again.

if none of that works, disconnect your windows drive, set the spare drive to 'master' and connect to the end of the ide ribbon, and boot from the hard drive manufacturers app and see if the drive is detected then! if still not detected, i would try the drive as a slave in another computer, if not detected there, then i think it is scrap. if it is detected, then you may be looking at a problem on your motherboard.

best of luck

ps - if your drives are sata post back.

Thanks for the advice, my Windows drive is IDE and my spare drive is SATA. I removed Ubuntu basically because I was using it to experiment with and then my Windows drive began to fill up. I needed the extra storage to...store all my stuff, especially my music :D

Converting completely to Ubuntu isn't an option at the moment though due to my need for Photoshop/CS:S/Battlefield 2, however I will consider it once I get my new Nvidia video card (I currently have a Radeon X800 Pro and I can't get 3d acceleration working with it). I'm sure if I learn the GIMP and find a few other games to play then I won't have a problem converting fully. :KS

---

### Post by smoker on 2007-06-21
> **Libertine said:**
> Thanks for the advice, my Windows drive is IDE and my spare drive is SATA...

that may well be where the problem lies, usually when installing windows to a SATA drive, on the install, you get to a stage near the beginning when you have to press F6, halt the install, and then install SATA or RAID drivers, after which windows will recognize the drive and continue the install.

windows may not 'see' the sata drive as it does not have these drivers. i would try and find these drivers and install them, then perhaps your sata drive will be recognized by windows. the drivers are usually on the motherboard driver disk, but you should also be able to download them from your motherboard support website, along with instructions how to install.

i have two sata drives, and when i had windows installed, i had to install the drivers as explained above, but ubuntu recognized both sata drives instantly:D

i can't explain why the bootable app from your hard drive manufacturer didn't pick up the drive, did you download the correct bootable version, and have it load sata drivers when booting (if this was an option)?

best of luck

---

### Post by OhioLen on 2008-03-28
I'm sure this incident was resolved a long time ago, but I had something similar happen about a year ago and here's what fixed it for me:

Boot to a floppy, CD or flash drive that has the Win98SE OEM Emergency Boot Floppy image on it. If you don't have or can't make one, the image can be gotten for free at Bootdisk.com [[Link]]("http://www.bootdisk.com/bootdisk.htm").

At the command prompt, type FDISK /MBR and hit enter. This removes any residual parts of GRUB left in the Master Boot Record. There will be no screen output, you'll just get a new prompt after a moment. Your data is in no danger unless you're a complete novice, in which case you shouldn't be trying this sort of thing anyway.

Remove the boot media and restart the machine. If you're lucky, it might boot from the HDD normally. If not, then you need to boot with your Windows installation CD and use the "Emergency Repair" option to rewrite the boot sector for Windows use. Use the console ONLY IF YOU KNOW HOW; let the software do it automatically if you don't. This looks scarier than it actually is! Boot to Windows normally, then go to Windows Update to make sure everything's current and you should be good to go.

---

