---
title: "Problem running Windows in Virtualbox"
date: 2008-11-04
forum: Virtualisation
---

### Post by J03y on 2008-11-04
Hello, I have a problem with virtualbox. Everytime I try to install the bootable windows xp iso file in virtualbox it gets stuck for a while in copying files. Yesterday, I left the virtualbox running to see if Windows would install but when it comes to the copying file part it never gets past 2% and then it freezes for like 5 minutes and then says aborted. Why does this happen and how do I fix this problem? :confused:

---

### Post by handydan918 on 2008-11-04
> **J03y said:**
> Hello, I have a problem with virtualbox. Everytime I try to install the bootable windows xp iso file in virtualbox it gets stuck for a while in copying files. Yesterday, I left the virtualbox running to see if Windows would install but when it comes to the copying file part it never gets past 2% and then it freezes for like 5 minutes and then says aborted. Why does this happen and how do I fix this problem? :confused:

I dunno. Is your .vdi file (virtual drive) large enough? Is it fat32 or ntfs? ( rather than ext2/3?)

---

### Post by J03y on 2008-11-04
> **handydan918 said:**
> I dunno. Is your .vdi file (virtual drive) large enough? Is it fat32 or ntfs? ( rather than ext2/3?)o.O, what u mean by large enough? And its fat, but I get an option to convert it to ntfs and thats what i try to do, convert it.

---

### Post by TyTiger on 2008-11-04
> **J03y said:**
> o.O, what u mean by large enough? And its fat, but I get an option to convert it to ntfs and thats what i try to do, convert it.

Did you make the virtual drive large enough. (E.G 10GB. etc..)
When creating a new virtual drive, it asks you what you want the size of the drive to say it is to the Guest OS (Windows running on Virtual Box in this case)
If you made it to small then you will have to delete that Virtual drive and make a new one using a decent size. 10GB is the normal default. I suggest selecting the expandable disk image option, (selected by default) so that it doesnt end up atcually using 10GB of your hard drive up front before the install and only uses whats atcually being used up by real data. (please note the fact it's expandable does'nt mean you can make it bigger later.)

---

### Post by TyTiger on 2008-11-04
> **J03y said:**
> o.O, what u mean by large enough? And its fat, but I get an option to convert it to ntfs and thats what i try to do, convert it.

Oh PS. Try NOT converting it.

---

### Post by J03y on 2008-11-04
> **TyTiger said:**
> Did you make the virtual drive large enough. (E.G 10GB. etc..)
When creating a dew virtual drive, it asks you what you want the size of the drive to say it is to the Guest OS (Windows running on Virtual Box in this case)
If you made it to small then you will have to delete that Virtual drive and make a new one using a decent size. 10GB is the normal default. I suggest selecting the expandable disk image option, (selected by default) so that it doesnt end up atcually using 10GB of your hard drive up front before the install and only uses whats atcually being used up by real data. (please note the fact it's expandable does'nt mean you can make it bigger later.)Oh yeah, its 10gb but I marked the dynamic option.

---

### Post by TyTiger on 2008-11-04
> **J03y said:**
> Oh yeah, its 10gb but I marked the dynamic option.

Interesting... Try not converting it to a different file system and leaving it as it is (fat32 in this case)

Also check you have write permissions on the disk image (diskimage.vdi) normally these are saved under your home directory 
/home/you/.virutalbox/

---

### Post by linux6994 on 2008-11-04
Some tips that might help.

The virtual disks for virtualbox are located in the /home/user/.virtualbox

Once you do get your virtual machine installed you can take the .virtualbox folder and copy it out for safe keeping. This method also allows you to copy the virtual machines from one PC to another. Build it once and spread it around.

Are you running OSE or via the website and installing the .deb? [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by J03y on 2008-11-04
> **TyTiger said:**
> Interesting... Try not converting it to a different file system and leaving it as it is (fat32 in this case)

Also check you have write permissions on the disk image (diskimage.vdi) normally these are saved under your home directory 
/home/you/.virutalbox/But this problem happens in both file systems, even in the quick alternative.

---

### Post by J03y on 2008-11-04
> **linux6994 said:**
> Some tips that might help.

The virtual disks for virtualbox are located in the /home/user/.virtualbox

Once you do get your virtual machine installed you can take the .virtualbox folder and copy it out for safe keeping. This method also allows you to copy the virtual machines from one PC to another. Build it once and spread it around.

Are you running OSE or via the website and installing the .deb? [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)I downloaded from that same website. I have Ubuntu Gutsy. I'm planning on installing hardy, but I need to burn the iso file ina cd with a good cd rom driver. Mine doesn't work. =P

---

### Post by TyTiger on 2008-11-04
> **J03y said:**
> I downloaded from that same website. I have Ubuntu Gutsy. I'm planning on installing hardy, but I need to burn the iso file ina cd with a good cd rom driver. Mine doesn't work. =P

you dont have to upgrade ubuntu from a CD... youc an do an online upgrade by going to system > Administration > update manager, it normally says theres a new version available.

If you insist on using some form of iso. try searching on mounting ISO's Virtually. this saves you CD's :)

---

