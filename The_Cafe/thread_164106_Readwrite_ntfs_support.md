---
title: "Read/write ntfs support"
date: 2006-04-22
forum: The Cafe
---

### Post by Hanj on 2006-04-22
I just came across [this]("http://www.ntfs-linux.com/") site - a company offering a (non-free) driver that provides read/write access to ntfs partitions from linux.
Now, this might be a stupid question, but I always thought writing to ntfs partitions was "experimental" in linux because microsoft wouldn't give out details about their file system, so that linux hackers had to sit with hex editors and try to figure it out themselves. Then how come this company could make this driver? Or are they paying microsoft to get the ntfs specs? If these guys could do it, do you think we might get free, built-in support for reading and writing to ntfs partitions in the near future?

---

### Post by DaMasta on 2006-04-22
Might provide some insight. I still doubt it is 100% effective, but who knows.
[http://www.ntfs-linux.com/home/personal/faqs.htm#3.3](http://www.ntfs-linux.com/home/personal/faqs.htm#3.3)

---

### Post by curuxz on 2006-04-22
My guess is that its just a money grabbing company that has packaged up the existing support and then rebranded it as a unique product. Charging for drivers is highly counter productive since its a world away from charging for software.

---

### Post by Hanj on 2006-04-22
> It is well known that originally NTFS was very close to the HPFS file system developed by IBM. HPFS was much more OPEN in terms of documentation support, data structure and so on. It helped us to gain a better understanding of its nature, architecture and ideology. The knowledge about NTFS we also have got has already been used for years inside our best-seller product - Paragon Partition Manager. We have sold several million copies of Paragon Partition Manager all over the world. The stability of the products as far as NTFS related operations are concerned says for itself about the stability of the NTFS technology at all. Thus, having a pretty good idea about what the HPFS file system is, we may understand the way NTFS functions. 
Applying to the other sources of information like Linux drivers for NTFS (read only drivers) and debugging Windows applications, we've documented NTFS structures from within and finally created the Universal File System Driver. 
While developing Paragon NTFS for Linux driver we always stuck to the following rules: 1) We never applied to any confidential Microsoft NTFS stuff (docs, codes, etc.) and the reverse engineering approach for MS codes. 2) Open sources are the only thing we used. E.g. from [www.ntfs.com](www.ntfs.com) we got the great part of our NTFS knowledge and understanding. 3) NTFS as a file system as well as on-disk layout is not patented and not documented. 
This sounds like they more or less figured everything out themselves. What's preventing open source developers from doing the same? Having write support for ntfs would be really nice.

---

### Post by NeghVar on 2006-04-22
> 3) NTFS as a file system as well as on-disk layout is not patented and not documented.

It will be. It took them a while but they just won over FAT.

---

### Post by imagine on 2006-04-22
[QUOTE=Hanj]This sounds like they more or less figured everything out themselves. What's preventing open source developers from doing the same?[/QUOTE]
Well, doing that is as appealing as a knife in your back. Sitting down an endless time to figure out how a proprietary file system works which you do not like and want to get rid off, doesn't sound like fun. Especially if you're getting zero support from the manufacturer.

---

### Post by briancurtin on 2006-04-22
[QUOTE=Hanj]so that linux hackers had to sit with hex editors and try to figure it out themselves. Then how come this company could make this driver?[/QUOTE]
"linux hackers had to sit with hex editors and try to figure it out themselves."

---

