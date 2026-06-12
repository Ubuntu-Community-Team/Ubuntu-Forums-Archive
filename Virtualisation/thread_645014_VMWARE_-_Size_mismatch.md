---
title: "VMWARE - Size mismatch"
date: 2007-12-19
forum: Virtualisation
---

### Post by s-lime on 2007-12-19
I'm running Win XP on VmWare...  The problem is that virutal machine on disk is actually bigger than one displayed in windows..

Size of wmdk virtual machine image file: 6.7 GB
Size actually displayed in windows: 4.8 GB

So, when I look for size in ubuntu, it is 6.7 GB, and when I look on running win, it only displays 4.8 GB.

The main problem is that my disk is very small and every MB is important to me.


Thanks for help!

---

### Post by fjgaude on 2007-12-19
How are you measuring the disk size when in Windows?

---

### Post by s-lime on 2007-12-20
Yes, I checked disk size in Ubuntu and in virtualised Windows. They are not the same as they should be...

Windows XP Professional.vmdk - 6.7 GB
C:\ - 4.8 GB

I measured:

My Computer > C: > Properites...

---

### Post by fjgaude on 2007-12-20
I'm thinking that the whole vmdk file is not loaded in the virtual space that the C: drives shows. There are lots of things in that vmdk that is not used by Windows but is used by VMware.

That's the best I can do... maybe others have a more detailed explanation.

---

### Post by s-lime on 2007-12-21
Anyone?

---

### Post by Portable_Jim on 2007-12-21
> **s-lime said:**
> I'm running Win XP on VmWare...  The problem is that virutal machine on disk is actually bigger than one displayed in windows..

Size of wmdk virtual machine image file: 6.7 GB
Size actually displayed in windows: 4.8 GB

So, when I look for size in ubuntu, it is 6.7 GB, and when I look on running win, it only displays 4.8 GB.

The main problem is that my disk is very small and every MB is important to me.


Thanks for help!
Could it be that there is a partition, so there is a bit you cannot access. (could also have something to do with NTFS).

---

### Post by jjthomas on 2007-12-21
> **s-lime said:**
> Anyone?

Did you look in the Windows Control Panel to see what the partition size is? Goto Control Panel, then Administrative Tools, then select Computer Management and finally select Disc Management.  That will bring up a graphic representation of your hard drive.  

IMPORTANT NOTE: Be very careful in this screen.  If you change your partition size while in this screen you will loose all your Windows data

-JJ

---

