---
title: "Upgraded to SATA, installed ok but wont boot. 'Error 15'"
date: 2008-06-07
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-06-07
I have just recieved my new SATA pci card and SATA drive. I had ubuntu installed already and i plugged it in and everything was picked up fine by the OS.
I reinstalled ( as obviously I want the OS on the SATA drive ) and everything went fine.
It popped the CD out when done, i took it out and it rebooted.
During the boot up screen I get this..

Verifying DMI Pool Data....
Boot from CD:
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 15

I definitely don't have the CD in and the bios seems o.k. 
There was an option to set 'hard disk boot priority' and I rearranged the 2 options so 'Bootable Add-in Cards is number 1, but same error.
The first boot device is CD then Hard Disk then floppy and 'boot other devices' is enabled.

Any ideas n e 1? Maybe there's a problem with grub? Maybe because my IDE drive is still set at master?

---

### Post by garethsimpsonuk on 2008-06-07
anyone?

---

### Post by quelx on 2008-06-07
[http://ubuntuforums.org/showpost.php?p=4587202&postcount=9](http://ubuntuforums.org/showpost.php?p=4587202&postcount=9)

---

### Post by garethsimpsonuk on 2008-06-07
i dont understand how that's supposed to work if i cant get into the grub menu to do run the commands

---

### Post by quelx on 2008-06-07
Try booting from the liveCD

[http://ubuntuforums.org/showpost.php?p=116936&postcount=1](http://ubuntuforums.org/showpost.php?p=116936&postcount=1)

This should not hurt a server install since you are not installing any packages.  Well, maybe a kernel, but that's easy to fix.

---

### Post by garethsimpsonuk on 2008-06-07
ok there must be a compatibility issue or something as I'm not having no luck with anything I've found. The drive doesn't show up in bios but the Ubuntu installer ( and windows ) sees and installs to it fine but I guess I see now, if the bios can't see it it cant boot it.
I've never done bios flashing, I bought the pc off someone and I don't know what mobo it's got. 
I know in windows you can view the mobo info but without an OS on what do I do? I don't know the model number or anything of the box so how do I know which bios to flash with? 
I've read of 4 popular bios flashing programs, each designed for a particular family of mobos. I guess these will be .exe's. Does that mean I have to install windows just to flash the bios? I've taken the floppy drives out of all my towers except the server so I don't think I can flash with floppies. Any pointers would be greatly appreciated as I've been doing this all day!
It might not even be a bios problem it might just be that the bootloader isn't set up right. Any help would be very useful.

Cheers

edit:yea, i was thinking of booting from a live cd to try and install grub again, just gotta find out how to do it.
i tried with the server install cd and made a dedicated partition for the boot files. then when booting i got an error about the drive sectors heads or summink is too big for the bios to support. i also read that there is a way to manually set the boot files at the start and make the exact start to get it to work. I just need some more advice before i choose the first possible ( hopefully the only ) solution.

---

### Post by garethsimpsonuk on 2008-06-07
come on guys n e ideas? im getting to the point where i feel like using an ide drive and just using the sata drive for storage but then it was pointless buying the sata controller

---

### Post by quelx on 2008-06-07
What is the exact layout of the drives in your system, physical drives and partitions?
What are the partition's mount points?
Is the boot partition on the SATA card?
Where is grub installed?
Show us your */etc/fstab* and */boot/grub/menu.lst*.

You may need to boot the live CD to get some of this info.

---

### Post by garethsimpsonuk on 2008-06-07
ok cheers, I'm just putting it back together now. Then I'll boot a live cd. This is what I had done:

Installed SATA PCI Controller and plugged 200GB SATA drive into it.

Left the 40GB IDE where it was, primary master I think, didnt change the jumpers. CD is secondary master. ( i will probably add more IDE drives when running )

Partitioned 8 GB for / 
2 GB for swap
the rest for home ( 192 GB )
all on sata drive

Everything went fine then it rebooted after install and I recieved the error above. 
I beleived it was a grub issue so I reinstalled and set a dedicated 10MB partition for grub. This time I recieved an error about the BIOS not supporting the head size. I read somewhere that you should either update BIOS ( which I dont know how to do ) or set the grub partition to be an exact size ... ( which i dont know how to do )
When I first bought it I tested it on the same box with ubuntu desktop and I could mount the drive no problem

Thanks for your help

---

### Post by quelx on 2008-06-07
I'll bet grub is installed on the IDE drive but pointing to the SATA for it's configuration (or maybe the otherway around)

Is the IDE drive doing anything in the system right now?
Is there anything installed on the drive?

While you are diggin' at the machine's innards remove the IDE drive and see if the system can boot the SATA alone, it may fail, but it should be obvious that it's trying to boot the drive.

Also check your BIOS settings for a boot add-on card, SCSI card or some such option.  It's probably in a boot order/priority menu.  If you want to use the SATA drive as the boot drive you'll need that set, since it's attached to a PCI card.

---

### Post by garethsimpsonuk on 2008-06-07
Yea I 4got to say I tried installing with just the sata drive and everything went fine during the install. Upon boot I get the 'Disk boot failure insert system disk' or words to that effect.
In my bios I have no option to set scsi in boot order but there is another 'boot priority' option with 'add in card' inside. I rearranged so 'add in card' was 1. and CD was 2. ( they were the only 2 options )but that didn't work either. 
If grub wasn't set up up right surely doing manual partitoning and setting a dedicated partition on the SATA would make sure grub is on the SATA drive.
I'm stuck, I cant think of anymore possibilities apart from what I mentioned above!

---

### Post by garethsimpsonuk on 2008-06-07
ok i'm still having issues if anyones out there what do you think to this:

*That's the bad news. The good news is that once the linux kernel loads, it kisses those bios limitations goodbye. From that point on, all hardware detection is controlled by the kernel. The kernel that's loaded at boot time resides in /boot. Accordingly, you should be able to install mandriva by creating a small /boot partition on your IDE drive, 200MB should be more than enough, and install everything else on your sata drive. You would also need to direct the installation routine to install the bootloader to the IDE drive. Then at boot time, your bios would see the bootloader on the ide drive and load it and the bootloader would see the kernel in /boot and load, after which the rest of your installation would be seen on the sata drive.*

It seems that this is a common problem ( trying to boot from SATA on a PCI card ) and this looks like a workaround.

Can someone with more experience confirm my interpretation is correct.

- install everything but /boot to SATA.
- Install /boot to an IDE partition
- somehow go into grub and point to the SATA os

I know how to do the first 2 but editing the grub settings is past me.

Any help would be really really appreciated!

---

### Post by logos34 on 2008-06-07
> **garethsimpsonuk said:**
> Yea I 4got to say I tried installing with just the sata drive and everything went fine during the install. Upon boot I get the 'Disk boot failure insert system disk' or words to that effect.
In my bios I have no option to set scsi in boot order but there is another 'boot priority' option with 'add in card' inside. I rearranged so 'add in card' was 1. and CD was 2. ( they were the only 2 options )but that didn't work either. 
If grub wasn't set up up right surely doing manual partitoning and setting a dedicated partition on the SATA would make sure grub is on the SATA drive.
I'm stuck, I cant think of anymore possibilities apart from what I mentioned above!

I hate to say it, but it sounds like you're, well, SOL.  If you can't boot from the sata pci card/disk when it alone is connected, where grub obviously installed on that drive's mbr (otherwise you would have gotten an 'fatal error' message), then booting from the ide is not going to help.  Maybe your bios just doesn't support that feature (but then what does 'add-in card' refer to?).  Or maybe the pci card doesn't support boot. There might be a bios update adding that capability but I doubt it.  

Check the documentation at the board and pci card manufacturer website.

hardware info:

sudo lshw

sudo dmidecode

---

### Post by garethsimpsonuk on 2008-06-08
thanx 4 ur reply logo. You've just made me remember something I don't think I set the grub partition to be on the MBR as I set my root first on the drive and then grub. 
Maybe I done it wrong ( i assumed setup would let me know or automatically install grub on the MBR I guess I the setup doen't hold your hand as much as I thought ).
I did install ubuntu on both disks and at the grub multi boot menu I was given the option to boot from the one on the SATA but it wouldn't work.

I accept defeat and will use the the SATA for my Home and swap instead. I suppose my data will load quicker on the SATA so all is not lost...Well it maybe as I now recieve this ( quoted from my other post in the general help )

> yea thanx logos it was driving me mad last night! i don't know why but know when I boot up, during post I see

Verifying DMI Pool Data....
Boot from CD:..
|B`e-$|B`e-$_

I've tried to copy it exactly but there's some strange symbols that aren't on the keboard. Such as the first vertical dash ( which is again repeated before the B )has a kinda small line coming out of the left in the middle so it's a bit like this -| but they connect and he horizontal line is much shorter. The underscore isn't really an underscore more like a cursor as it's blinking and the accent is directly over the e.

Anyway whatever it is it's hard to search for the problem when I can't even copy the display so I'm stumped. I reset the bios and it's still there, and disabled anything and eveything in different combnations and still no luck. I even disconnected the CD drive altogether. ( I think I recieved a boot disk error that time )
Why is it trying to boot from CD and what is that strange set of characters. It's like it's waiting for something due to the blinking cursor but never gets anywhere.

Anyway anyone got any ideas for a very very annoyed ( with myself ) ubuntu user?

Thanks

oh and thanx 4 ur post logos, I expect you've gone now though 

When and if i get rid of this I will quite happily just use the SATA for storage but how do I get rid of this.

Thanx again for your posts logos

---

### Post by garethsimpsonuk on 2008-06-08
bump

---

### Post by logos34 on 2008-06-08
> **garethsimpsonuk said:**
> thanx 4 ur reply logo. You've just made me remember something I don't think I set the grub partition to be on the MBR as I set my root first on the drive and then grub. 
Maybe I done it wrong ( i assumed setup would let me know or automatically install grub on the MBR I guess I the setup doen't hold your hand as much as I thought ).

actually, grub by default/automatically goes on the mbr.  

> I accept defeat and will use the the SATA for my Home and swap instead. I suppose my data will load quicker on the SATA so all is not lost

yep, separate /home and /swap on separate disk will speed things up a little.  Ideally, though, you also want root on a fast drive--your applications and programs will load quicker, faster boot too

Not sure why it's trying to boot from cd drive--even when disconnected!  Maybe check the bios boot order again.

---

