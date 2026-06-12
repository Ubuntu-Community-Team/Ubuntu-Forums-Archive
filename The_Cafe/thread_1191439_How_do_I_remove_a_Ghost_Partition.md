---
title: "How do I remove a Ghost Partition?"
date: 2009-06-19
forum: The Cafe
---

### Post by MasterNetra on 2009-06-19
I have a Dell Latitude D530 which I got through my school and they have a ghost image on it which takes up 114GB out of 180GB! ANd would like to remove it as I'm not a complete noob to computers and can well enough use Dell's default recovery CD's if need be, (Or Just Ubuntu :p).

---

### Post by xuCGC002 on 2009-06-19
Boot up an Ubuntu liveCD (or other distro with a partition editor), and go to System>Administration>Partition editor. Then find the ghost partition, and remove it by right clicking and selecting "Delete". Then click apply. Then resize your main partition to fill the space by right clicking on it and selecting "Resize"(or make a new one. Whatever you want). Be sure to click "Apply" after resizing/deleting.

---

### Post by H2SO_four on 2009-06-19
Exorcist.

Partition editor should do the job.

---

### Post by MasterNetra on 2009-06-19
No, Partition Editor doesn't even see it. I maybe in error by calling it a partition, its probably a image.

---

### Post by lisati on 2009-06-19
Suggestion: do a backup of important data and then do a fresh install using the entire disk.

---

### Post by MasterNetra on 2009-06-19
> **lisati said:**
> Suggestion: do a backup of important data and then do a fresh install using the entire disk.

Doesn't work. Ubuntu just doesn't see it at all! Its a symantic ghost image..

---

### Post by anystupidname on 2009-06-19
> **MasterNetra said:**
> No, Partition Editor doesn't even see it. I maybe in error by calling it a partition, its probably a image.

Post the output of "sudo fdisk -l /dev/sda" and "sudo du -a / | sort -n -r | head -n 10" please

Incidentally, Symantec Ghost images should have a .gho extension or possibly .v2i so you can also try "sudo find / -name *.gho"

---

### Post by MasterNetra on 2009-06-19
> **anystupidname said:**
> Post the output of "sudo fdisk -l /dev/sda" please

Can't do, had to regretfully restore winxp so I can properly use magicjack, would of VMed it but I've been hearing problems with that all over that place and I really don't currently have another means of making phone calls, tied in to the fact I need to use CS3 anyway. But meh. The XP restore wipes drive in the process I'd like to get access to this addtional 114GB so I may better dual-boot. Well I do know that past looks at my drive via Ubuntu only showed the remaining memory. Thus far the 114GB has been untouchable, Only shown at recovery using the restore CD.

---

### Post by lidex on 2009-06-19
Check out this blog:
[http://www.kenst.com/2008/07/deleting-your-q1-eisa-partition.html]("http://www.kenst.com/2008/07/deleting-your-q1-eisa-partition.html")

---

### Post by MasterNetra on 2009-06-19
> **lidex said:**
> Check out this blog:
[http://www.kenst.com/2008/07/deleting-your-q1-eisa-partition.html]("http://www.kenst.com/2008/07/deleting-your-q1-eisa-partition.html")

Amazingly enough still nothing x.x Not even XP sees it.

---

### Post by H2SO_four on 2009-06-19
if it is an image file, you should be able to find it.  Either use a disk usage analyzer.

Also, by wiping the drive, you will wipe out anything within the drive as well.  The image file should go the way of the dodo with a clean install if it is not its own partition.

---

### Post by lisati on 2009-06-19
> **MasterNetra said:**
> Can't do, had to regretfully restore winxp so I can properly use magicjack, would of VMed it but I've been hearing problems with that all over that place and I really don't currently have another means of making phone calls, tied in to the fact I need to use CS3 anyway. But meh. The XP restore wipes drive in the process I'd like to get access to this addtional 114GB so I may better dual-boot. Well I do know that past looks at my drive via Ubuntu only showed the remaining memory. Thus far the 114GB has been untouchable, Only shown at recovery using the restore CD.

If you have a "Live CD" available to boot from you could do the fdisk stuff from there.

---

### Post by LookTJ on 2009-06-19
You can use DBAN to wipe the drive.

---

### Post by anystupidname on 2009-06-19
You could do all that we asked via liveCD or using [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256965](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256965) 

Regarding your statements about VM problems, I don't know what you are referring to. I have had a box running VMware workstation at work on my production machine (Ubuntu host) for several years without any hiccups. It is rigged so that the XP install runs virtually in VMware and is on a real partition instead of a virtual disk so that I can dual boot to XP if all hell breaks loose.

---

### Post by LookTJ on 2009-06-19
Also make sure you download the beta of DBAN.

---

### Post by MasterNetra on 2009-06-19
> **anystupidname said:**
> You could do all that we asked via liveCD or using [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256965](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=256965) 

Regarding your statements about VM problems, I don't know what you are referring to. I have had a box running VMware workstation at work on my production machine (Ubuntu host) for several years without any hiccups. It is rigged so that the XP install runs virtually in VMware and is on a real partition instead of a virtual disk so that I can dual boot to XP if all hell breaks loose.

I was refering to Magicjack's behavior in a VM not XP.

---

### Post by lidex on 2009-06-19
Perhaps then you should boot with a hard drive utility disk and low-level format. Should wipe everything.

---

### Post by H2SO_four on 2009-06-19
> **taylor said:**
> you can use dban to wipe the drive.

+1

---

### Post by MasterNetra on 2009-06-19
Tryed it, and it didn't even see it. x.x I wonder if dell set it up on some kind of independent recovery disc thats built into the labtop x.x, because its looking like it maybe the case...I just always figured it was a stealthed Image... I also tried asking a rep in there chat, and was directed to a department who only has a phone # not a email address, and atm I don't have access to a phone. (Got Magic Jack but not phone to attach to it yet >.<)

---

### Post by anystupidname on 2009-06-19
There must be some kind of DDO type thing in place if a chunk of hard drive is just missing from everything like that... You already check the BIOS for an option to unhide recovery area or enable install mode or something like that?

---

### Post by MasterNetra on 2009-06-19
> **anystupidname said:**
> There must be some kind of DDO type thing in place if a chunk of hard drive is just missing from everything like that... You already check the BIOS for an option to unhide recovery area or enable install mode or something like that?

Not yet, but I will.

Tried it, apparently the BIOS doesn't either. Dell must REALLY not want you to access it anyway except via restoring... curious as to how only the restore CD can connect to the restore area...regardless still be nice to get a hold of it :/

*Update* Got to school and one of the techs have the same labtop and he said it was directly from the DVD itself. Hmm...prehaps though the image is 114GB the actual data is DVD size?... Oh well :/

---

