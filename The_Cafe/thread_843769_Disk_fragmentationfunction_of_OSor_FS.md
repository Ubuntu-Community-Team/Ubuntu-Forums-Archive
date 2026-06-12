---
title: "Disk fragmentation:*function of OS*or FS?"
date: 2008-06-28
forum: The Cafe
---

### Post by drumsticks on 2008-06-28
I wonder, is file placement and hence disk fragmentation a function of the operating system (OS) or file system (FS)? Take FAT32 for example, does using Windows to manage files result in more fragmentation than using Linux to do the same? Assume the files managed are only data or media files, as is usual for external hard disks.

I imagine it would be strongly dependent on the FS, not the OS, but that's just a guess. That's the way I would design it from ground up, but there's also years of backward compatibility to consider. 

I've not been able to find any evidence to support either argument. Is there anyone here that might know?

Edit:*Aside, how come I*keep getting extraneous symbols (such as the asterisk in the title) when I*post?

---

### Post by LaRoza on 2008-06-28
It is the file system, and its driver.

FAT32 is just as bad on Linux as it is on Windows.

---

### Post by drumsticks on 2008-06-28
How about on-the-fly disk defragmentation, as used in OS*X? Surely that is an OS*feature and not an FS feature? Does this OS*X feature even work on non HFS+ drives?

---

### Post by LaRoza on 2008-06-28
> **drumsticks said:**
> How about on-the-fly disk defragmentation, as used in OS*X? Surely that is an OS*feature and not an FS feature? Does this OS*X feature even work on non HFS+ drives?

I don't know about OS X. There are background defragmenters for Windows file systems, and they are separate applications.

It is possible that OS X has something like that to compensate for a bad file system.

---

### Post by drumsticks on 2008-06-28
> **LaRoza said:**
> I don't know about OS X. There are background defragmenters for Windows file systems, and they are separate applications.

It is possible that OS X has something like that to compensate for a bad file system.

On-the-fly disk defragmentation in OS*X only defragments files as they are read – there is no point in defragmenting files that are unused. This is quite different to the background defragmenters in Windows you are alluding to, at least the ones that I*know of.

To be honest, my question is not really about FAT32. I*use Ext2-IFS to access my external ext3 drives in the 0.1% of the time I*do use Windows. I just didn't want Windows to mess up my ext3 drives. I*use FAT32 only for my memory cards - everything else is formatted in ext3. I posed the question a little more generically because I*was curious about the more general case.

---

