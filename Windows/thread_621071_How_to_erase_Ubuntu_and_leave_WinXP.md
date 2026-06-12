---
title: "How to erase Ubuntu and leave WinXP?"
date: 2007-11-23
forum: Windows
---

### Post by Zdravko on 2007-11-23
On my notebook there is WinXP and Ubuntu dual booting. There is another separate partition FAT32 for... dunno what for. Anyway.
I want to completely erase Ubuntu and somehow add its partition to the WinXP or the FAT32. How do I do that?

---

### Post by Don1500 on 2007-11-23
Use Gparted (available online, live CD), delete the Ubuntu partition and extend the size of the WIN-XP partition.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

When you boot WIN-XP it will do an automatic Fdisk, just let it run. Then you're done.

---

### Post by dasunst3r on 2007-11-23
You can also pop in the Windows XP installation CD, go into recovery console, and use the *fixmbr* command.  After that, go into Control Panel -> Administrative Tools -> Computer Management to resize your Windows partition to take up the whole disk.

---

### Post by Zdravko on 2007-11-23
I don't want to lose any WinXP data! It is very important!
How do I use gparted, when I will be erasing all of Ubuntu?

---

### Post by timcredible on 2007-11-23
wrt to the data, run a backup before you do anything

wrt running gparted, run it from a livecd, as the previous poster stated and supplied the link for it

---

### Post by Zdravko on 2007-11-23
what is wrt?

---

### Post by SpyLikeMe on 2007-11-23
> **Zdravko said:**
> what is wrt?


With Regards To:

---

### Post by Zdravko on 2007-11-23
Uuh... I am so frightened... Is there a chance I might screw everything?

---

### Post by markusf21 on 2007-11-23
There is always that chance just make sure u back-up anything important

---

### Post by GavinZac on 2007-11-23
> **Zdravko said:**
> Uuh... I am so frightened... Is there a chance I might screw everything?

Thats pretty much a feature of Windows XP ;)

if you want to avoid losing any day, just reformat the ext3 partition to NTFS and it will show up in windows as a new, blank disc.

---

### Post by Zdravko on 2007-11-23
> **GavinZac said:**
> Thats pretty much a feature of Windows XP ;)

if you want to avoid losing any day, just reformat the ext3 partition to NTFS and it will show up in windows as a new, blank disc.
Hey, that's a clever idea! How do I do that?

---

### Post by RebounD11 on 2007-11-23
Delete the partition and create a new one in-its-stead using the WinXP disc without installing Windows.

When you reboot in WinXP you right-click and format it as NTFS.

Why would U give up Linux?

---

### Post by Zdravko on 2007-11-23
Are you sure I can delete a Linux partition from a Windows CD?

---

### Post by GavinZac on 2007-11-23
> **Zdravko said:**
> Hey, that's a clever idea! How do I do that?

in gparted, edit the ext3 partition and change it to NTFS.

Alternatively, delete the ext3 partition and create a new NTFS one. :)

do keep an eye on ubuntu though and hopefully someday you'll feel like giving it another go.
> **Zdravko said:**
> Are you sure I can delete a Linux partition from a Windows CD?

i dont think that will work with installing some stuff in windows first. the gparted cd is perhaps the easiest way

---

### Post by overdrank on 2007-11-23
> **Zdravko said:**
> Are you sure I can delete a Linux partition from a Windows CD?

Hi I would recommend
 [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Zdravko on 2007-11-24
Okay, okay. Let's summarize up to here:
1. First,I have to delete somehow the GRUB part of MBR and restore the original Windows boot loader.
2. Then, I have to erase the whole Ubuntu partition (including SWAP?) and reformat it in NTFS.
3. Finally, under WinXP I have to "join" the new NTFS partition to the old one.
Can someone explain each step nicely?
Currently I have a WinXP CD. I also own an old Ubuntu LiveCD. Dunno if it might be of any help. The given link says, I should use a thing called "LiveGParted CD", or something like that. What is that? Please, explain me! I wonder why has nobody written a crystal clear How-to about this issue!

---

### Post by vishzilla on 2007-11-24
You can use the WinXP CD. When the CD boots, select the Repair Option and FIXMBR. and restart the computer. WIndows XP will load, and then in Control Panel, find Computer Management, I guess it will b under Maintenance. There under Disk Management you can delete the Linux Partition and you can reformat the same into a NTFS partition

---

### Post by Zdravko on 2007-11-24
How does the WinXP CD boot? Do I have to press a key to invoke it during the system start-up?
Are you sure there will be a way to reformat the Ubuntu partition under WinXP? Its partition is not visible!

---

### Post by ad1066 on 2007-11-24
First, you'll want to go to your BIOS, and check the boot order settings, make sure that CD-ROM is set before HDD. Then if you have the CD in the drive when the PC boots, it will attempt to boot from the CD first (you might get a "Press any key to boot from CD" type prompt).

Running FIXMBR restores the original WinXP MBR, which will knock out GRUB and allow XP to boot normally.

Once you're back in XP, going to Control Panel > Administative Tools > Disk Management will show you the other partitions (they'll probably just come up as "Non-DOS Partitions". From there you can reformat them as you like.

-- Ben

---

### Post by GavinZac on 2007-11-24
> **Zdravko said:**
>  I wonder why has nobody written a crystal clear How-to about this issue!
Hippocratic principle? :D

---

### Post by Zdravko on 2007-11-24
> **ad1066 said:**
> First, you'll want to go to your BIOS, and check the boot order settings, make sure that CD-ROM is set before HDD. Then if you have the CD in the drive when the PC boots, it will attempt to boot from the CD first (you might get a "Press any key to boot from CD" type prompt).

Running FIXMBR restores the original WinXP MBR, which will knock out GRUB and allow XP to boot normally.

Once you're back in XP, going to Control Panel > Administative Tools > Disk Management will show you the other partitions (they'll probably just come up as "Non-DOS Partitions". From there you can reformat them as you like.

-- Ben
There is no Disc management option there! :confused:

---

### Post by RebounD11 on 2007-11-24
> **Zdravko said:**
> Are you sure I can delete a Linux partition from a Windows CD?

Yes, I have done it myself.

---

### Post by Zdravko on 2007-11-24
Then tell me how!

---

### Post by RebounD11 on 2007-11-24
Fisrt yoou boot from the WinXP disk.

When you get to the part where you have to choose the partition where to install it to, you will se the Linux partitions marked as unknown type (anyway different from the NTFS and FAT ones).

Once here you delete them (can't really remember the keys sth with D and L :D I believe you know how, anyway it tells you how frm what I remember). Then create a new partition (without formating it or anything).

You don't go on any further from here you just exit the installer and reboot. Once in Windows you will see a raw partition in My Computer which you can format NTFS from the right-click menu.


I hope I have been helpful and coherent enough :D
If not say sth and I'll polish my explanations. 


PS I haven't used Windows in more than 2 years now, but I don't believe much has changed in XP (tried Vista for a couple of weeks but it doesn't count, just as I don't count the one week long Mandriva 2007 install).

---

### Post by Zdravko on 2007-11-25
This ain't good advice. If I delete the Ubuntu partition first, the GRUB won't load properly and WinXP won't start at all.

---

### Post by LaRoza on 2007-11-25
> **Zdravko said:**
> On my notebook there is WinXP and Ubuntu dual booting. There is another separate partition FAT32 for... dunno what for. Anyway.
I want to completely erase Ubuntu and somehow add its partition to the WinXP or the FAT32. How do I do that?

You will need: Windows XP install disk, or the Super Grub Disk (see the link in my sig)

First, I would use the Super Grub Disk to restore the Windows MBR. Reboot the computer, only Windows should boot.

Then go to computer management, disk management and delete the unwanted partitions and expand the Windows partition.

The FAT32 is mostly the restore partition.

This way, you are doing from within Windows and you know your stuff is safe. If the Super Grub Disk fails, you will still be able to use the computer as normal, but it shouldn't fail.

---

### Post by LaRoza on 2007-11-25
> **Zdravko said:**
> This ain't good advice. If I delete the Ubuntu partition first, the GRUB won't load properly and WinXP won't start at all.

I remedied that, as you posted this.

---

### Post by Zdravko on 2007-11-25
For the second time I tell you I can't find computer management, disk management!!!

---

### Post by KiwiNZ on 2007-11-25
> **Zdravko said:**
> For the second time I tell you I can't find computer management, disk management!!!
 
 
Are you using Win XP Professional or Home

---

### Post by LaRoza on 2007-11-25
> **Zdravko said:**
> For the second time I tell you I can't find computer management, disk management!!!

Where did you look?

I assumed you used google or help first: [http://support.microsoft.com/kb/308423](http://support.microsoft.com/kb/308423)

Did you use the Super Grub Disk to restore the MBR?

---

### Post by Zdravko on 2007-11-25
I have WinXP SP2 Professional.
Aah, I found it!
It is right here: Start -> Control Panel -> Administrative Tools -> Computer Management -> Disc Management.
However, I use another PC now. I have to test this on the notebook.
BTW, I plugged in the WinXP CD and in the BIOS I changed the boot order. The CD boots and starts loading Windows drivers. Then I press the R key to start the recovery console. Here I have to choose the Windows installation (in my case only '1'). Then I have to type my administrator password. I seem to have forgotten here. I am allowed to try only 3 times. Then the notebook is restarted!

---

### Post by Zdravko on 2007-11-25
Okay! I managed it! I mean I remembered the password and ran fixmbr. Then I booted back to Windows. Let's see what I can do there....

---

### Post by Zdravko on 2007-11-25
There is only one option in the Disc management: Delete logical partition. There are 2 unknown - maybe the second one is the swap, 'cause it is much smaller (nearly 1 GB). How should I proceed next?

---

### Post by LaRoza on 2007-11-25
If you don't want the other partitions, swap and the ext (unknow) file systems are useless on WIndows, delete them, and extend the Windows partition after that.

---

### Post by Zdravko on 2007-11-25
I will try to do that...

---

### Post by Zdravko on 2007-11-25
First I deleted the logical drives (the only thing I was allowed to do). The partitions then united into a free space. I then deleted the partition. Now it is unallocated. What should I do next to expand the C: partition into the new one?

---

### Post by dips_xe on 2007-11-25
why don't you understand directions? 4 pages to get rid of ubuntu?

...

---

### Post by Zdravko on 2007-11-25
No one gives directions! I ask a simple question. And nobody answers it.
I am stuck at the Computer management panel. There is no option to "join" 2 partitions...

BTW, I (as the original OP here) am preparing a HOW-TO for this issue. The faster you help me, the better.

---

### Post by dips_xe on 2007-11-25
a how-to isn't necessary, and this thread isn't necessary. you could have just searched on ubuntuforums for something like "erase ubuntu" or "fixmbr" or whatever...

---

### Post by dips_xe on 2007-11-25
in fact, i did it for you, and i found one in a minute!! wow!!

[http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

---

### Post by Zdravko on 2007-11-25
I searched. And I couldn't find anything that would help me in any way. BTW, the mods here will decide whether my How-to is useful. You are not going to prevent me from uncovering the mystery of joining 2 partitions under WinXP!

---

### Post by Zdravko on 2007-11-25
> **dips_xe said:**
> in fact, i did it for you, and i found one in a minute!! wow!!

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)
Nope, this one is outdated. It uses gparted. Here several people said to use WinXP to expand the NTFS partition.

---

### Post by dips_xe on 2007-11-25
> **Zdravko said:**
> Nope, this one is outdated. It uses gparted. Here several people said to use WinXP to expand the NTFS partition.

perhaps there are several ways to do it? gparted is the preferred and most popular method. and how could this be outdated, it's like 4 months old..

---

### Post by Zdravko on 2007-11-25
What if I don't have gparted? A new how-to must be written for this case.

---

### Post by dips_xe on 2007-11-25
you have gparted if you have a ubuntu disc. if you want to remove ubuntu from your computer, i'll assume you have or had had one at one point.

---

### Post by Zdravko on 2007-11-25
Really? Even an alternate one?

---

### Post by dips_xe on 2007-11-25
> **Zdravko said:**
> Really? Even an alternate one?

i don't know, are you trying to trap me or something? i'm sure fdisk or something is there if gparted isn't. but if you NEED gparted, in that case, i would download gparted and burn it. but do you not have a cd burner either?

---

### Post by Zdravko on 2007-11-25
If you don't know, you should help me investigate that case. Now you see, there is real need for this How-to.
On the current PC, I am working now, there is no CD ROM at all. I wouldn't use the notebook's CD-DVD-ROM to burn additional software.

---

### Post by RebounD11 on 2007-11-25
> **Zdravko said:**
> This ain't good advice. If I delete the Ubuntu partition first, the GRUB won't load properly and WinXP won't start at all.

It has never done that for me, and I always installed Grub in the MBR... Anyway there's always SuperGrub and I managed to use that successfully from the first time I tried.

---

### Post by LaRoza on 2007-11-25
> **RebounD11 said:**
> It has never done that for me, and I always installed Grub in the MBR... Anyway there's always SuperGrub and I managed to use that successfully from the first time I tried.

Grub isn't really in the  MBR (it is too large), if you delete the Ubuntu partition, grub won't be able to work.

---

### Post by LaRoza on 2007-11-25
> **Zdravko said:**
> No one gives directions! I ask a simple question. And nobody answers it.
I am stuck at the Computer management panel. There is no option to "join" 2 partitions...

BTW, I (as the original OP here) am preparing a HOW-TO for this issue. The faster you help me, the better.

Click on the C: drive, and you should get the option to expand it.

I recommend downloading GParted Live CD (see the link in my sig), it really is faster and more convenient than the alternatives.

You can't join partitions, if space "unallocated" it means it isn't a partition so you can expand an existing partition to fill the space. Partitioning can be confusing, I hope this helped.

---

### Post by Zdravko on 2007-11-26
> **LaRoza said:**
> Click on the C: drive, and you should get the option to expand it.

I recommend downloading GParted Live CD (see the link in my sig), it really is faster and more convenient than the alternatives.

You can't join partitions, if space "unallocated" it means it isn't a partition so you can expand an existing partition to fill the space. Partitioning can be confusing, I hope this helped.
Nope. There is no such option. See the attached screenshot for available actions:

---

### Post by KiwiNZ on 2007-11-26
Check the Ubuntu site 
Use Google there is many tutorials re this out there

---

