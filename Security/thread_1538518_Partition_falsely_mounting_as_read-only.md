---
title: "Partition falsely mounting as read-only"
date: 2010-07-25
forum: Security
---

### Post by Mariane on 2010-07-25
I bought a "My Passport" external disk, brand = WD. 
This mounts as 2 partitions
/dev/sdb1 -> /media/sdb1
/dev/sr1 -> /media/sr1

The sdb1 is normal and can be accessed with gparted. sr1 is mounted as read-only. Umounting it and typing 
sudo mount -f /dev/sr1 /media/sr1
returns without error and I can apparently write to it (still no error) but it does not in fact write to this partition. 

I tried other tools, fdisk, u3-tool and fsdisk. They all say the partition is read-only. But it is not physically read-only, WD offers firmware upgrades to the stuff in this partition: 

[http://www.wdc.com/wdproducts/wdsmartwareupdate/step1.asp?id=wdfMP_Essential&os=win](http://www.wdc.com/wdproducts/wdsmartwareupdate/step1.asp?id=wdfMP_Essential&os=win)

It looks to me as if WD has found a way to make my computer believe this partition is physically read-only, while in fact it is not. 

What I want to do is get rid of this partition and of all the window junk on it. Any idea, please?

Mariane

---

### Post by OpSecShellshock on 2010-07-25
Well that's interesting. The "sr" construction is used by cd/dvd devices which under most circumstances can't be written to on the fly. I wonder if that has something to do with it? I'm not sure about the Western Digital stance on whether people own the things they buy or not. On the other hand, given that it's generally expected these things will be used with Windows, it may just have an image of what would ordinarily be the "installation cd-rom" that tends to be packaged with consumer hardware. What I mean is, instead of actually shipping the drives with CDs containing Windows drivers, they may have put an image of the CD onto the disk itself in a different partition, such that it continues to think it's a CD. Even that would be dumb, though, since those installation disks aren't ever necessary.

Anyway, when in doubt, zero out.

---

### Post by Mariane on 2010-07-25
I think it must be something like that. 
And this fake install cd-rom is set to autorun, which means that simply plugging in the disk into a windows machine will launch the .net spyware. 

How do I know it has some spyware on it? Well, before doing the firmware upgrade WD website says you have to disable any anti-spyware software you may have on your machine. 

Mariane

---

### Post by CharlesA on 2010-07-25
> **Mariane said:**
> I think it must be something like that. 
And this fake install cd-rom is set to autorun, which means that simply plugging in the disk into a windows machine will launch the .net spyware. 

How do I know it has some spyware on it? Well, before doing the firmware upgrade WD website says you have to disable any anti-spyware software you may have on your machine. 

Mariane

When you do anything involving firmware or the BIOS you always turn off any antivirus/antispyware programs, since they can interfere with the update.

It's a bit of a leap to think that doing a firmware upgrade on a hard drive will automagically install spyware on your machine.

On all the external drives I've bought (some WD, some not) they all came as one large partition.

---

### Post by Mariane on 2010-07-25
> **CharlesA said:**
> 
you always turn off any antivirus/antispyware programs, since they can interfere with the update.


Precisely. They can stop the update from reporting home. And what they report about is anyone's guess... As it is hidden your point of view and my point of view solely depend upon how willing we are to trust multinationals...

---

### Post by CharlesA on 2010-07-25
> **Mariane said:**
> Precisely. They can stop the update from reporting home. And what they report about is anyone's guess... As it is hidden your point of view and my point of view solely depend upon how willing we are to trust multinationals...

The reason you disable antivirus/antispyware is because the update rewrites the firmware on the device and an AV may think that it's a virus doing so. If the update is interrupted, you've just bricked the device.

Think what you like though. :)

As for the OP: Just wipe the drive with DBAN or dd.

---

### Post by Mariane on 2010-07-26
dd didn't work, it said the file system was read-only. u3-tool said the same, and so did fdisk and sfdisk... :( 

Following your advice I am now running DBAN since yesterday. It says it is going to take 22 hours to complete, I just hope it works... 

Dangerous stuff this DBAN (Full name is "Darik's Boot And Nuke). Anyone else reads this because they have the same problem, be very careful not to wipe out your computer's hard disk. If you don't see a line with "My Passport" or whatever the name of the external disk you want to wipe is, you can type "verbose" (without the quotes, just the word). It did the trick for me. I'll report back to say whether it worked or not, in 7 hours and 44 minutes at least. 

Mariane

---

### Post by OpSecShellshock on 2010-07-26
Wow, I've done some looking into this, and the thing sure is tricky. Lots of people seem to have similar question. Turns out that yes, it is a virtual CD, that it's actually in the firmware of the disk itself, and that in order to remove it in the way approved by WD you'd need to update the firmware and use their own little utility which is Windows and OSX only (and appears to have a EULA of all things).  Evidently some of the Mac users have suggested that the virtual CD can be prevented from mounting by editing fstab, and if that's the case I'm sure it would work in Linux as well. That still wouldn't make it go away (since it's embedded in the firmware), but it wouldn't show up all the time. Reformatting would, of course, wipe the whole thing out, and is the best course of action anyway for those who prefer to have ext3/4 across all file systems.

Another possible thing: some people are saying that the interface between the disk and the case is non-standard. At first I just kind of rolled my eyes at the proprietary nonsense, but it occurs to me that it's possible they'd put something in the firmware that makes it essential in order for the disk and case to work together.

---

### Post by Mariane on 2010-07-26
I opened the case. There is a small hard disk cellotaped (literally) to one of these green "motherboard-type" cards with thingies. Sorry I don't know what these are called in English, please tell me. The disk has 2 unused set of connectors. There is nothing between the disk and the socket. 

Some people say you have to mount the drive as sata to clean it, I guess that would mean using one of the unused set of connectors. That would also mean opening up my computer, and though I'm willing to fiddle with the external disk I'm much less willing to fiddle with my computer. I'll only try if I get desperate. 

The good news is that it is easy to remove the casing from the "My Passport" - someone even posted a video on YouTube of him doing it with only one hand - and it is easy to put the disk back in it's casing exactly the way it was before.

5 hours and 15 minutes to go for DBAN.

---

### Post by CharlesA on 2010-07-26
Interesting that it seems to be hardcoded into the firmware. I did find a [page]("http://superuser.com/questions/44318/how-do-i-remove-a-mybooks-wd-smartware-virtual-cd-from-my-desktop") explaining how to remove the VCD by using Windows or Mac. What a pain in the butt.

Hopefully DBAN will wipe the whole drive out, including the VCD portion.

As a sidenote: I disconnect all other drives that I don't want wiped when I run DBAN, that way, I won't screw up and wipe my main drive.

---

### Post by Mariane on 2010-07-26
Thank you. Interesting that a winXP install disk did the job. I wonder whether a Ubuntu install disk would also do it. I'll try that once DBAN has finished if the VCD is still there.

---

### Post by Mariane on 2010-07-26
DBAN didn't work and Ubuntu install CD only offers sda as an install medium. 

Any more suggestions, please?

---

### Post by CharlesA on 2010-07-26
The only other thing I can think of is installing Windows either in a VM or on a spare machine, updating the firmware on the external drive and then remove the VCD.

---

### Post by Mariane on 2010-07-26
The text on the link seemed to say windows xp would delete the vcd on install. So I'll try tomorrow to remove the hard disk on my old machine and connect the WD disk in its place. After that I'll try to install win xp.

---

### Post by CharlesA on 2010-07-26
If that doesn't work, go ahead and install Windows on that old machine and update the firmware and crap then wipe it again.

---

### Post by Mariane on 2010-07-27
Installing win XP didn't work. It said: "Setup did not find any hard disk drives installed in your computer" :( .

---

### Post by CharlesA on 2010-07-27
Wow that sucks. I'll make a note not to get one of those WD drives.. what a pain.

Don't know what else you can do. :(

---

### Post by Mariane on 2010-07-27
I tried again and got a bit further. I could not boot with the disk plugged in because it stopped the win XP install disk from booting up. Even after in setup I specifically excluded this disk from the boot order. So I was plugging the usb disk connector after xp setup had booted, but I was doing it too late and xp setup missed it. 

I turned on the laptop and when I got the blinking cursor, before xp setup said it was examining my system, I plugged in the usb cable to the disk. xp saw it but won't install on it. It can only see the fat32 partition and not the whole disk. It says "Your computer's startup program cannot gain access to the disk containing the partition or free space you chose. Setup cannot install Windows XP on this hard disk"  :( . 

Anyway, even if it did install it looks like it would install on the sdb1 partition and not on the whole disk... 

I read about other people's attempts to make a bootable disk out of one My Passport Essential and failing because the vcd partition got in the way. That person said a win xp install cd did the trick, but they had connected theirs via the SATA connectors and not via usb.

---

### Post by Mariane on 2010-07-27
It's not all for nothing, this laptop's case had not been opened for 3 years and it was full of fluff. Opening it to remove my HDD before the xp attempt gave me a chance to clean it. 

After reinserting my laptop's HDD I rebooted before removing the win xp cd. And panicked when I realised what I had done. I immediately turned off the computer and reached for my pin. Stupid system, this, to need a pin to open a cd drive. I once lost a pin in my bed because of that, and only found it again when I tried to sleep on it. But now the computer is OK, no harm done, I haven't lost a single screw and no small but important thing has vanished with a "ping!" into a dark corner :) .

---

### Post by CharlesA on 2010-07-27
That's good to hear.

I wonder why they make it so hard to remove a stupid virtual CD, for people who don't give a crap about backup applications and junk.

I know the seagate drives I have came with manuals and junk but they were on the hard drive, not on a VCD.

---

### Post by Mariane on 2010-07-29
bump

---

