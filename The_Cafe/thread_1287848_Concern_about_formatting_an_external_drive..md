---
title: "Concern about formatting an external drive."
date: 2009-10-10
forum: The Cafe
---

### Post by kajman on 2009-10-10
Is there any danger involved in formating an external drive to a NTFS file system? I'm talking about an external 600gb usb hard drive. It came formatted to FAT32, but recently (while some data was being written to it) I accidentally pulled the usb cable (not entirely but enough) and it resulted in massive data corruption. I tried to repair the file allocation table using CHKDSK (which was a very bad idea), but it destroyed even more of data, and even more of directory's changed to files without an extension, and of 32kb in size. 

So my idea is to change the file system to NTFS, but my concern is that it may corrupt the drive (for e.g. the driver which is responsible for transferring the data through the usb cable may not understand this kind of file system and may be unable to transfer any data correctly). 

I need to use this disk in a way that Windowses like XP or Vista (or even 7) would understand, but also to prevent such massive data losses. I think that if I use NTFS it would be less prone to this kind of failures in future.

PS I know this may not be the best kind of forum, to ask such a general question, but there are many helpful people here so I thought its worth a try :)

Thanks for any help and advice,
kajman

---

### Post by dragos240 on 2009-10-10
that disconnected it, any disconnection of ANY volume of media WILL result in corruption.

---

### Post by kajman on 2009-10-10
I'm aware of that. You didn't answer my question at all.

---

### Post by Bachstelze on 2009-10-10
I think what dragos240 meant was that making it NTFS probably won't prevent data corruption if the cable is pulled, but to answer your question, the drive should still work if you format it as NTFS.

---

### Post by xpod on 2009-10-10
I have a 250G external drive here that wont allow me to format to quite a number of filesystems, including ntfs.
[ATTACH]131517[/ATTACH]

If i remove the standard 2.5" sata drive though and stick it in a laptop it can be formatted to whatever i want just fine.Likewise, if i stick another 2.5" drive in the external drive housing it`s exactly as shown above.

---

### Post by kajman on 2009-10-10
I think that, when the data will get corrupted it is easier to recover it when the drive is formatted to NTFS than to FAT, but I don't know too much about it. Also it would be more convenient this way, because it would be possible to store files bigger than 4gb.

But the biggest concern is the health of my drive, I don't want to damage it this way. It would be too expensive to experiment if I'm not sure that it will work. For e.g. I've heard that formatting usb memory sticks to NTFS is not a a very good idea.

---

### Post by Bachstelze on 2009-10-10
> **kajman said:**
> 
But the biggest concern is the health of my drive, I don't want to damage it this way. It would be too expensive to experiment if I'm not sure that it will work. For e.g. I've heard that formatting usb memory sticks to NTFS is not a a very good idea.

USB memory sticks are Flash memory, it's totally different from hard drives.

---

### Post by kajman on 2009-10-10
Well, I think I'll try to format it to NTFS ans see what happens to it. Wish me luck :)

---

