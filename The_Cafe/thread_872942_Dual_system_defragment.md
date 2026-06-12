---
title: "Dual system defragment"
date: 2008-07-28
forum: The Cafe
---

### Post by harbino on 2008-07-28
I am a new user to Ubuntu and this is my first Linux system I have used let alone a dual boot.

I originally downloaded and installed Ubuntu to run alongside Windows XP, as a sort of admin system.

I was wondering if there are any good defraggers and hard disk maintenance programs that I can download and use to defrag my Windows hard drives with.

Any help appreciated.
thanks



Harbino

---

### Post by original_jamingrit on 2008-07-28
I'm not sure if there is such a program, that will defrag and maintain a Windows filesystem while booted into Ubuntu.  After a bit of searching, I haven't found any either.  NTFS isn't perfectly supported, so this is unlikely.  For a FAT32 filesystem, maybe.  I don't think there are any defraggers for windows that are strictly userspace either, they require API built into the windows OS's kernel at least (So, no WINE).

This may not be possible or reliable until NTFS is 100% supported.  So, you'd have to log into Windows to defrag the NTFS.

If you'd rather try to do it remotely, this may help: [http://www.itnewsgroups.net/group/microsoft.public.windows.server.general/topic7461.aspx](http://www.itnewsgroups.net/group/microsoft.public.windows.server.general/topic7461.aspx)

---

### Post by harbino on 2008-07-29
Pity as I am using an NTFS system.  I may uninstall Ubuntu and wait until some good things come out for it.  I was going to use Ubuntu as a maintainer to Windows but...

---

### Post by ibutho on 2008-07-29
> **harbino said:**
> Pity as I am using an NTFS system.  I may uninstall Ubuntu and wait until some good things come out for it.  I was going to use Ubuntu as a maintainer to Windows but...

Why not just use tools dedicated for maintaining Windows? You may have to pay for them, but at least they do the job. Linux is an entirely different OS to Windows and whilst it has some tools that can help rescue a Windows system, thats not its primary function and with Windows being proprietary its difficult for free software developers to create tools to support Windows if they don't know the underlying code.

---

### Post by harbino on 2008-07-29
I used Linux as no Windows programs or files would be running allowing full access to it.  I would be able to remove files without problems.

---

