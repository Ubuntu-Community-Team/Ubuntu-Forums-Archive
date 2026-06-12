---
title: "Back to Windows, and all it's bull spit"
date: 2007-09-14
forum: Windows
---

### Post by Ripfox on 2007-09-14
I am doing a reinstall for a friend, and need to boot and install Win2k. This is an IBM Thinkpad with NO floppy drive. So...short of going and buying a usb floppy drive, how can I do this?

Thanks

Rip

---

### Post by rfruth on 2007-09-14
CD or DVD ?

---

### Post by Ripfox on 2007-09-14
Cd

---

### Post by buzzmandt on 2007-09-14
insert disk, start computer, follow on screen directions

---

### Post by Ripfox on 2007-09-14
bump

---

### Post by Ripfox on 2007-09-14
No, that will not work as Windows XP is installed now, and it throws an error message that setup will be disabled due to the fact that it is an older OS than XP. Normally you would boot to 4 floppies then the 2k cd  for a fresh install, but as I said earlier there is no floppy drive on this machine.

---

### Post by rfruth on 2007-09-14
W2K on floppies only (how many ?)

---

### Post by Ripfox on 2007-09-14
It usually requires 4 to start the installation but then it boots to the windows 2000 CD for the rest of the install. You see my delimma?

---

### Post by Ripfox on 2007-09-14
What is the equivilent to CD (change directory) in DOS?

---

### Post by Ripfox on 2007-09-14
Ah...it seems it IS cd. :lolflag:

---

### Post by buzzmandt on 2007-09-14
never had that problem, have it boot from cd as first option in bios and it should work if it's a win2k install disk, i've gone back and forth between xp  and 2000 before with any issues.  I didn't have the 4 floppies you mentioned tho, so  don't know what kinda install disc you have

---

### Post by psusi on 2007-09-14
Delete the partition then.  If the win2k cd won't do it ( and it should ), you can use the ubuntu livecd or the winxp cd.

---

### Post by BoyOfDestiny on 2007-09-14
> **ripfox said:**
> No, that will not work as Windows XP is installed now, and it throws an error message that setup will be disabled due to the fact that it is an older OS than XP. Normally you would boot to 4 floppies then the 2k cd  for a fresh install, but as I said earlier there is no floppy drive on this machine.

Hmm what are the floppies for? Just to partition or what? I mean can you use an Ubuntu Live CD to do that, then install win2k (or better yet Ubuntu ;) )

The other option, do you have a machine that can read the floppies? Make an img file (never done it to be honest, but I've downloaded floppy images to do BIOS updates...) and then you can convert the img file and burn as a bootable cd (preferably a CDRW)

mkisofs floppy.img > bootable.iso

Then burn that iso to CD, and it would work as the floppy would.

---

### Post by Ripfox on 2007-09-16
> **BoyOfDestiny said:**
> Hmm what are the floppies for? Just to partition or what? I mean can you use an Ubuntu Live CD to do that, then install win2k (or better yet Ubuntu ;) )

The other option, do you have a machine that can read the floppies? Make an img file (never done it to be honest, but I've downloaded floppy images to do BIOS updates...) and then you can convert the img file and burn as a bootable cd (preferably a CDRW)

mkisofs floppy.img > bootable.iso

Then bloadurn that iso to CD, and it would work as the floppy would.

THAT is what I was looking for. Thank you...

I have ALWAYS had to use the four floppies to get the win2k cd to begin installation. They are not to format, they load drivers ect then it asks for the disk.
As a matter of fact, the program "makeboot" is contained in the win2k cd and it asks for 4 floppies to make the boot disks.

---

### Post by kelvin spratt on 2007-09-16
ive got a genuine windows 2000 install disc it has never asked for boot floppies to install onto any computer ive installed on are you using an a over an already installed system disc as that is not a proper install disc and can give a really bad OS. the proper install disk partitions format installs drivers and OS by default no floppies req.

---

### Post by Ripfox on 2007-09-18
Well, there is still a program on the "proper" win2k install disk called "makeboot" which makes those same four floppy bootdisks, so its there for some reason I guess.

Anyway, I just wound up putting another OS on it for those guys.
Thanks for the help....too many installs these days. I guess I shouldn't complain, it keeps me busy!
If only they would all listen to me and install Ubuntu...

---

