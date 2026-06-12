---
title: "Backup of Windows XP partition"
date: 2006-10-21
forum: Windows
---

### Post by buntolith on 2006-10-21
On my laptop I run Win XP Pro, Ubuntu and Kubuntu. Each one of them are on a different partition. I would like to make a full backup of my Windows partition to use when everything goes wrong. I don't want to spend $40 on Northon Ghost or something like that so I was thinking if it is possible to do the backup from Ubuntu or Kubuntu? 

Does it work to just start up Kubuntu, mount the Windows partition and copy and paste the whole drive into a backup folder on an external harddrive? And the other way around. Would it work to format the c: or hda1 with GetParted and then just copy the backup back onto hda1 from Ubuntu or Kubuntu?

Would Windows XP start after an operation like this?

Is it also possible to do a backup of Kubuntu from Ubuntu in the same way?

Thanks for your help!

---

### Post by podunk on 2006-10-22
I was wondering the same thing. Actually thinking about giving it a go - I have a windows partition with no data on it.

A good free (as in coffee not free free) XP backup solution is here:
[http://www.runtime.org/dixml.htm](http://www.runtime.org/dixml.htm)

---

### Post by podunk on 2006-10-22
I copied my windows drive to a USB fat32 USB hard drive with no problems - the XP OS read every file I tested just fine.

I also copied the XP drive to a folder on /home (which was *very* fast) then copied the files to a fat32 drive (which was much slower) and once again every file I tested was fine.

I'm going to try partimage next. :-)

---

### Post by ago on 2006-10-23
boot from Linux and use dd or partimage, both will create a file. Probably I would suggest partimage to begin with. It is text mode but fairly straightforward. The image is an ordinary file that you can move wherever you want. You use the same program to "unzip" the image into its original partition..

---

### Post by buntolith on 2006-10-24
Offcourse, this is the way to do it. Partimage created 4 nice 2GB files with everything on it. Nice. Now I don't have to reinstall windows again when it all crashes.

Thanks

---

