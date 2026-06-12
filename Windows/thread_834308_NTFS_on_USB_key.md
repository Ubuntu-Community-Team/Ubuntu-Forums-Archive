---
title: "NTFS on USB key"
date: 2008-06-19
forum: Windows
---

### Post by Ptero-4 on 2008-06-19
Hi. I'm thinking about formatting my USB key as either xfs or ntfs and wanted to know, if I go with NTFS how do I keep windoze from choking on the key (ironically ntfs-3g is more stable than windoze handling windoze's own filesystem on USB keys)? or if I go with xfs, is there any small, OSS, xfs filesystem driver for windoze?

---

### Post by damis648 on 2008-06-19
XFS Driver: [http://www.crossmeta.com/crossmeta.html](http://www.crossmeta.com/crossmeta.html)

No guarantees windows will not choke on the NTFS. :popcorn:

---

### Post by Ptero-4 on 2008-06-19
That's the irony of it. Windoze can't handle it's own filesystem.

---

### Post by myusername on 2008-06-19
i would go with ntfs. in my experience...windows doesnt work to well with linux filesystems

---

### Post by rickyjones on 2008-06-20
> **Ptero-4 said:**
> That's the irony of it. Windoze can't handle it's own filesystem.

Ya wanna clarify that before I label it as complete FUD? 

On topic - how large is this USB key? If it is over a Gig then I would probably go with NTFS, else FAT32.

Sincerely,
Richard

---

### Post by Ptero-4 on 2008-06-22
> **rickyjones said:**
> Ya wanna clarify that before I label it as complete FUD? 

On topic - how large is this USB key? If it is over a Gig then I would probably go with NTFS, else FAT32.

Sincerely,
Richard

What I meant (sort of TIC) is that windoze tends to get all sort of "delayed writing" errors when you try to wirte large files to a ntfs-formatted usb key, while linux can easily cope with even larger files on the same ntfs-formatted usb key.

---

### Post by myusername on 2008-06-22
i have never experienced that...

---

### Post by aamukahvi on 2008-06-22
> **Ptero-4 said:**
> That's the irony of it. Windoze can't handle it's own filesystem.
What's Windoze?

---

### Post by Ptero-4 on 2008-06-23
> **aamukahvi said:**
> What's Windoze?

It's a derogative name for Windows, because you can literally take a nap (doze off) while waiting for it to complete any given task (specially true for Vista).

---

### Post by LaRoza on 2008-06-24
I wouldn't recommend NTFS for USB. It will wear it out (like all journalling file systems)

I recommend FAT32 or EXT2 (Not ext3)

---

### Post by ComputerGeek31618 on 2008-06-24
I wasn't aware Windows would put NTFS on a USB drive (I haven't formatted one in a very long time, though).  If you use linux to format, well, I never have.  Anyway, when in doubt, FAT 32.  When in doubt about really old computers, FAT16 (but you shouldn't have to under normal circumstances).  Anyway, I've never heard of Windows having a problem with an NTFS USB drive, othrwise, I'd stick to NTFS.  (When in doubt, FAT32.)  And I've never heard of any way Windows could interface with and ext file system, (when in doubt...)

---

### Post by LaRoza on 2008-06-24
> **ComputerGeek31618 said:**
> And I've never heard of any way Windows could interface with and ext file system, (when in doubt...)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

USB drives have limited writing, a journalling file system will just wear them out and is an inefficient use of space.

---

### Post by ComputerGeek31618 on 2008-06-24
Interesting.  I'll try that on my computer, I could use it.

---

### Post by LaRoza on 2008-06-24
> **ComputerGeek31618 said:**
> Interesting.  I'll try that on my computer, I could use it.

It works great. I just used it, to access a storage partition I have, and it works flawlessly (so far).

It didn't even require a restart.

---

### Post by ComputerGeek31618 on 2008-06-24
So, what is journaling?  Is it where data is pre-written in a cache and then written to it's proper location later?

---

### Post by LaRoza on 2008-06-24
> **ComputerGeek31618 said:**
> So, what is journaling?  Is it where data is pre-written in a cache and then written to it's proper location later?

[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

The cacheing is part of the OS mainly, to keep things speedy and efficient.

---

### Post by ComputerGeek31618 on 2008-06-24
I see.  That definately makes sense in terms of USB device lifespan.  Yeah, a non-journaling filesystem would be an advantage (just more susceptable to corruption in power failure situations.)

---

### Post by LaRoza on 2008-06-24
> **ComputerGeek31618 said:**
> I see.  That definately makes sense in terms of USB device lifespan.  Yeah, a non-journaling filesystem would be an advantage (just more susceptable to corruption in power failure situations.)

Portable media is always vulnerable, and that would be the least of its worries.

---

