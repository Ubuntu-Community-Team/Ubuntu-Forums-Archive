---
title: "Separate media partition?"
date: 2009-05-24
forum: The Cafe
---

### Post by Vostrocity on 2009-05-24
Right now I have a double-boot with 90% bricked Vista and 10% Jaunty on a 120GB. :D When I get time this summer I plan on moving it over to a 320GB and have a triple-boot with Win7, Jaunty, and OSx86. I plan on using all three OSses more or less equally (being that all three are awesome) so I was wondering if I should create a separate partition to store all my personal files (music, pictures, videos, documents) so that all three OSses can access it. And also I need to know what disk system works best with all three.

---

### Post by celticbhoy on 2009-05-24
Could be wrong, but is win 7 not NTFS?

---

### Post by Vostrocity on 2009-05-24
> **celticbhoy said:**
> Could be wrong, but is win 7 not NTFS?

No you are right, but it doesn't answer my question. :o

---

### Post by Bölvaður on 2009-05-24
yes definitely have your data on a separate partition, I do.
I don't know how windows is nowdays but I would guess if you use the old fat32 it should be good for everyone. Only linux is good of those 3 OSes in my opinion with filesystems.. so if you'd remove the other two you could have much better filsystems :P

---

### Post by zobcat on 2009-05-24
I think a separate external hard drive is the way to go. It works great for me between Jaunty and Win7. It's formatted to ext3. You don't have to, but I prefer to since I use ubuntu more often than not. Windows doesn't recognize it on it's own, but there's a piece of software called ext2ifs that assigns a drive letter to it. I've never had a problem with it over the past 4 years. The best thing about the external is clean installs are a breeze since I don't save anything important on my internal.

---

### Post by Vostrocity on 2009-05-24
Ok thanks for the replies. I just looked it up on good ol' Wikipedia, and it happens that NTFS-3G (the driver thing that let's Ubuntu see Windows partitions) also has a Mac version! Yay that means I'll probably use NTFS since I hate the size limitations with FAT32. :)

Can't wait to get it. Having a Windows/Linux/Mac triple-boot will be epic! :D

---

### Post by Xbehave on 2009-05-24
You'll want media on a shared drive but its probably best to keep your ~/ s  separate as the performance on ntfs isn't brilliant

---

### Post by mamamia88 on 2009-05-24
+1 for external drive for media.  that way it works in all 3 operating systems for sure and if you have other computers or an xbox 360 or ps3 you can connect it up and play it on there too

---

### Post by Vostrocity on 2009-05-24
Actually I was thinking of a separate partition, not a separate drive. I have a 750GB external but it's loud and slow. And it's a laptop so I prefer having everything on the internal.

---

### Post by calrogman on 2009-05-24
I'd use NTFS, for starters, all 3 OS's support reading from it.  If you install NTFS-3G on OSx86 (EDIT: NTFS-3G has only been tested on Intel and PPC based machines, you could break something), it should also support writing to it.

Use NTFS.

---

### Post by ghindo on 2009-05-24
Probably the best filesystem for those three OSs to access would probably be NTFS.  Windows natively reads it, Ubuntu comes with NTFS-3G preinstalled, and OS X can use NTFS-3G as well.

---

### Post by CJ Master on 2009-05-24
I would personally just use dropbox. :)

---

### Post by Vostrocity on 2009-05-24
> **calrogman said:**
> NTFS-3G has only been tested on Intel and PPC based machines, you could break something
Good thing I have an C2D. ;)


> **CJ Master said:**
> I would personally just use dropbox. :)
I'm sure 2GB is enough for all my videos and music. :)

---

### Post by kc3 on 2009-05-24
> **celticbhoy said:**
> Could be wrong, but is win 7 not NTFS?
 
Well, I've used Windows 7 and had it for a while BUT I think it actualy gives you the option of using NTFS and there's another filesystem also. At least it gave me the option on my non-system drive but I can't remember about the system drive.

---

### Post by CJ Master on 2009-05-24
> **Vostrocity said:**
> Good thing I have an C2D. ;)



I'm sure 2GB is enough for all my videos and music. :)

It would be enough for all mine, but I guess I'm prety frugal. :P If you have a spare laptop you can use it as a file server.

---

