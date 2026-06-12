---
title: "Migrating Windows to a HDD already populated by Linux, possible?"
date: 2013-11-06
forum: Windows
---

### Post by Werne on 2013-11-06
Well, I got faced with this one today, I intend to sell my old 320GB HDD that has Windows 7 on it, so I need to migrate it to my new 1TB HDD that already has Ubuntu installed on it, my wife needs Windows for work.

I was thinking of shrinking the home partition down to some 600GB and placing Windows in front of it so the exact partition order (in GParted from left to right) would be like so:

/dev/sda3 - System Reserved
/dev/sda4 - Windows
/dev/sda1 - /home
/dev/sda2 - /

Thought I should use simple copy/paste in GParted, that thing never failed me so far. 

However, all the "migrate Windows to new HDD" tutorials mention moving Windows to a clean HDD (where System Reserved is /dev/sda1 and HDD has nothing on it prior to the move), but mine already has Linux on it. I haven't found one of them mentioning migrating Windows to a HDD that already has a Linux (or any kind of OS/partition) on it, so I'm not even sure if this'll work.

That's why I need help, I got no idea on how to proceed on this and will Windows even be able to boot after I transfer it. Linux is simple, copy/paste in GParted, mount root, run grub-install --root-directory=/path/to/mountpoint /dev/sdwhatever and voila, it works. Windows, never did anything like this. Did anyone even have any experience with something like this? And will this even work as I imagined it (I kinda have my doubts)?

All help on getting this thing moved is appreciated. :-)

---

### Post by oldfred on 2013-11-06
I might try Windows backup software as it may recognize more of the details. Windows may have serial numbers in MBR, in the sectors after the MBR for DRM software and needs a Windows 7 PBR or partition boot sector. And Windows BCD has to have the correct partition as it uses something like UUIDs.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Werne on 2013-11-06
Your post made me think. Even though the procedure that thread explains is meant to restore Windows on a HDD on which it's been installed already, my intention is to move it over to a new HDD on which it was never installed. The cloning procedure explained there is the same as I had in mind - copy/paste the boot and OS partitions onto a new drive - but the boot partition is unable to find the OS partition when it gets chainloaded by GRUB. So I tried the "bootrec /rebuildbcd" which does detect Windows on my new HDD as D:\Windows, however once I choose to rebuild BCD it gives me "Element not found".

I'm pretty sure if I manage to rebuild the BCD, I'd be able to chainload Windows trough GRUB, I just need to find a way to make that happen.

---

### Post by oldfred on 2013-11-06
Did you run chkdsk?
Chkdsk also resets PBR to have correct start & size of NTFS partition and which boot loader to use ntldr for XP or bootmgr for Vista/7/8 in BIOS mode. Size info must match partition table sizes.

---

### Post by Werne on 2013-11-06
Already ran chkdsk, had no effect on the outcome. Tried running "Repair my computer" thinking Microsoft's own automated utility may be able to solve it. Was grinding my teeth hoping it won't mess things up, and it actually did manage to fix things to boot Win7, on the fifth run. Startrep is slow as sloth and I prefer CLI over GUI when it comes to fiddling with the system, but it did get the job done without messing with Linux and GRUB.\\:D/

And people say Linux is complicated... if I were transferring Linux I'd be done hours ago and be relaxing with my fourth beer. :roll: Speaking of which, I think I deserve a beer.

Thanks for the help man. :D I'd send you a cold one too but I'm afraid it can't fit through my ethernet port. :(

---

### Post by oldfred on 2013-11-06
Glad you got it working. :)

I am not one to turn down a beer. I will stop in next time I am in town.

---

