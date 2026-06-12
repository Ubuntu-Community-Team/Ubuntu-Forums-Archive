---
title: "Restore win xp boot files"
date: 2006-11-27
forum: Windows
---

### Post by rejser on 2006-11-27
My computer won't boot from sata drive, so I have an old ide drive in my box. 
Win XP needs to install boot files on first hard-drive for some reason. So Messing around with Mac OS X86 it for some reason wiped this drive clean. 
The Question:
Is there a quick easy way to reinstall these files to the same new created partition?
Would like to not to have to reinstall XP. 

I have never used XP as a primary os so feel a little at lost.

---

### Post by cilynx on 2006-11-27
Couple of options...

You can install GRUB or LILO on the MBR and chain load XP.  XP will still have the proper boot information to chain load on the front of its partition.  It's just the MBR that OSX took over.  

The other option is if you have an XP install CD you can use the "Repair" option.  This will rewrite all of your system files on the partition and reclaim the MBR.  Keep in mind, this will make XP the only bootable OS from the hard drive and if you need otherwise, you'll need another way to boot into whatever other OS you've got.

---

### Post by rejser on 2006-11-27
Thanks. 

Yes, grub I reinstalled at once, Setting it so I could boot osx, kubu, and winxp. 
But its not the mbr that is in question, it's that if you install xp on another drive than the first it still want's to install netldr.exe and a bunch of other files on the first harddrive for some reason. Which was done. 
Maybe the repair option and another grub-install

---

### Post by cilynx on 2006-11-27
Ok, I gotcha.  Sorry I didn't fully comprehend the situation first time around.  Yes, I think doing a repair and then grub-install should take care of you.

---

### Post by AllenGG on 2006-11-27
Use extreme caution with the Win XP repair disk. If it came from the manufacturer, say Dell, it might work, but it might wipe out your files. They will be restorable, I've done it for people in the past but it's slow.
I've used Knoppix to read files as well. Try something like that first.

---

