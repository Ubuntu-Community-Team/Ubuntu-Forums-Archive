---
title: "How best to create backup of Windows XP drive?"
date: 2007-01-29
forum: Windows
---

### Post by kexodusc on 2007-01-29
You folks are great at helping me solve my Ubuntu problems, I hope I can bounce a Windows XP question off you.  Not sure if this is the right forum for this but here goes.

I spent about 6 hours fixing my mom and dad's Windows XP machine (format, reinstall, download install drivers, apps, etc).  

After all that, I'm wondering if there's any good, hopefully free software out there for creating a backup image of their drive, one that could be recovered with a bootable recovery CD, so I don't have to spend another Sunday doing this in the future.

I have Nero 7 - think it has a backup tool, and bootable recovery CD, but I'm not sure if it's any good.  I don't trust the Windows XP backup tool. 

Any suggestions or tips?

---

### Post by kpkeerthi on 2007-01-29
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
> 
The NTFS (Windows NT File System) is currently not fully supported: this means you will be able to save an NTFS partition if system files are not very fragmented, and if system files are not compressed. In this case, you will be able to save the partition into an image file, and you will be able to restore it after. If there is a problem when saving, an error message will be shown and you won't be able to continue. If you have successfully saved an NTFS NTFS partition, you shouldn't have problems as you restore it (except in the case of bugs). Then the best way is to try to save a partition to know if it is possible. If not, try to defragment it with diskeeper or another tool, and try to saving the partition again.


---

### Post by kexodusc on 2007-01-29
> **kpkeerthi said:**
> [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

Thanks, kpkeerthi, I'll give that a shot.

---

### Post by frrobert on 2007-01-29
XP only 

If you just want to backup the xp drive use Drive Image XML.  It works well will run off the drive or a Bart Pe cd.  It is free, as in no charge.  The best way to use it is using it with a Bart Cd it is much faster.

[http://www.runtime.org/dixml.htm](http://www.runtime.org/dixml.htm)

If you want a tool that works on both XP and linux drives

One of the best tools I found was Patition Manager by Paragon.

I works on most all disk formats, windows or Linux

[http://www.paragon-software.com/products](http://www.paragon-software.com/products)

It is few pieces of paid closed software is worth it.  

Hope this helps.

---

### Post by xhaan on 2007-01-29
And I definitely wouldn't trust Nero.
I tried to back up some files onto dvds, just writing the data to them with no special backup scheme or anything... silliy me thought that since the burn completed ok they must be good but it turned out that 99% of the files were corrupted and when I did a system restore and tried to put them back, I then found out that I lost most of my files.

---

### Post by Brunellus on 2007-01-29
thread moved to more relevant forum.

---

