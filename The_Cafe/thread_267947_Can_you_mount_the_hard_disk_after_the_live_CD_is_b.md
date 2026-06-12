---
title: "Can you mount the hard disk after the live CD is booted."
date: 2006-09-29
forum: The Cafe
---

### Post by GarethMB on 2006-09-29
Is this possible?

If so how can it be done. (I have a friend windows user, who is facing a reinstall, who would like to rescue her data if possible)

---

### Post by raublekick on 2006-09-29
yes it is very possible

in the terminal just use the mount command, i forget exactly what to use and i can't check to documentation right now. just check the man page by typing "man mount" in the terminal and it should be kinda easy to figure out.

---

### Post by GarethMB on 2006-09-29
Surely I need edit fstab first.

---

### Post by raublekick on 2006-09-29
no, you don't need to (and don't call me shirley! :p ). fstab is mostly just for having drives mounted automatically. 

the basic gist of what you need to do is this:
sudo mkdir /media/myoldinstall 
(named this so that you don't confuse the live CD directories and the HD directories)
sudo mount /dev/hda1 /media/myoldinstall
 (where /dev/hda1 is the path to the hard drive device)

check the man page though, cus i can't confirm that that is exactly what you need.

---

### Post by maniacmusician on 2006-09-29
when I was using the Xubuntu live CD, I remember that all I had to do was use the disk manager. either disks-admin or you can go to Appications > System > Disk Manager. and you could choose the drive you want, and mount it wherever you want. thats if you prefer a graphical method of course, i'm sure raublekick's method would work too.

---

### Post by GarethMB on 2006-09-29
It did work. Her PC is currently (slowly) making archives of the data she doesn't want to lose. Although she told me her hard disk wasn't partitioned, which it appears it is. So it's probably pointless anyways.:KS

---

### Post by DoctorMO on 2006-09-29
I like your avitar by the way GarethMB, a good film I thought.

OK back onto topic, the way disks are mounted on the live CD could be improved in Edgy by creating links on the desktop perhaps and auto generating an fstab so disks can be mounted automaticly.

maniacmusician thanks I never knew you could do that.

---

