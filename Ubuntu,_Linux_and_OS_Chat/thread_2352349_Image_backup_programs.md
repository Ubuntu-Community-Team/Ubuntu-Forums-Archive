---
title: "Image backup programs"
date: 2017-02-11
forum: Ubuntu, Linux and OS Chat
---

### Post by raleigh3 on 2017-02-11
I  am looking for recommendations from users of a program that can do image backups.

I used Redo Backup, but found that it is not always reliable.

Thanks.

---

### Post by wildmanne39 on 2017-02-11
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by bearlake on 2017-02-11
> **raleigh3 said:**
> I  am looking for recommendations from users of a program that can do image backups.

I used Redo Backup, but found that it is not always reliable.

Thanks.

Hi,

Been using [Clonezilla]("http://clonezilla.org/downloads.php") for years now without any issues.

---

### Post by raleigh3 on 2017-02-11
Thanks for the recommendation.

---

### Post by TheFu on 2017-02-12
clonezilla, partimage, fsarchiver, dd, ddrescue, gddrescue. Each with pros/cons.

**fsarchiver** is the most flexible, because it allows restores to a different sized partition while still using compression of the saved partition data.

Using google with 1 known program and "vs" in the search will show options.   "**fsarchivers vs**" would be the search term.  alternativeTo.net is another place to look.

Don't forget file-based backups. These are usually 1000x more efficient and with just 2 grub commands, a system can be up and running quickly again using the more efficient backup methods.

---

### Post by jamesr on 2017-02-12
I would also like to recommend another backup program called **MondoArchive** and available  from [www.mondorescue.org](www.mondorescue.org). you can save to dvd's, usb keys and usb hard drives. 
One can control
a) want you to backup
b) amount of compression
It can used to do bare-metal recovery if necessary or if you require recover only certain files you can do that as well.

---

### Post by raleigh3 on 2017-02-13
Many thanks for the other recommendations.

Linux is so much more stable than Windows that I used in the past. :-)

---

### Post by yoshii on 2017-02-21
I have had good results with Clonezilla.  
I had some bad results with a native Linux installed program; I forget the name, but it installed a bunch of downloaded junk I didn't agree to.  
Clonzilla is pretty straightforward and can be used for non-Linux stuff.  
With Clonezilla and gParted for other stuff, it's a good combo.

---

