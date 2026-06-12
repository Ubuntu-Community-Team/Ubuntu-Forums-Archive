---
title: "Hard drive upgrade woes"
date: 2008-10-21
forum: The Cafe
---

### Post by Colro on 2008-10-21
I ordered Seagate's new 1.5TB drive, and it should get here in the morning....problem is, I don't want to have to reinstall everything. Does anyone know of a good way to just copy everything on my current (160gb) drive to the new one, boot sector and all? Can GParted do it? I've heard there's something called DD tools on the knoppix live CD as well, has anyone ever used it? Thanks for any suggestions, I really don't want to spend hours loading all of my backups / ISOs >_>

Edit: If it matters, this is my work machine running Vista 64 bit, **not** ubuntu or any other distro. But since I just want to copy a partition from one drive to another, I doubt that matters..

---

### Post by Grant A. on 2008-10-21
Couldn't you just use RAID and mount both drives?

---

### Post by Colro on 2008-10-21
Nah, I'm wanting to put the 160 in an enclosure and use it for backups. It's old and significantly slower then the 1.5TB as well.

---

### Post by Erdaron on 2008-10-21
I think you're looking for a disk image program, such as Norton Ghost. I've never used it myself, but my understanding is that clones a disk to a backup media, and then writes it bit-for-bit to another drive.

---

### Post by PurposeOfReason on 2008-10-21
May I ask why you would put an OS on such a big HDD?

---

### Post by LaRoza on 2008-10-21
> **Colro said:**
> I ordered Seagate's new 1.5TB drive, and it should get here in the morning....problem is, I don't want to have to reinstall everything. Does anyone know of a good way to just copy everything on my current (160gb) drive to the new one, boot sector and all? Can GParted do it? I've heard there's something called DD tools on the knoppix live CD as well, has anyone ever used it? Thanks for any suggestions, I really don't want to spend hours loading all of my backups / ISOs >_>

Edit: If it matters, this is my work machine running Vista 64 bit, **not** ubuntu or any other distro. But since I just want to copy a partition from one drive to another, I doubt that matters..

That may be against the Windows EULA.

The easiest, if possible, solution is two have two drives. After hooking up the drive, and rebooting, Windows will detect it and assign it a drive letter (assuming it is pre-formated). You can use "Disk Management" (search in the start menu) to format it.

---

### Post by Grant A. on 2008-10-21
> **LaRoza said:**
> That may be against the Windows EULA.

The easiest, if possible, solution is two have two drives. After hooking up the drive, and rebooting, Windows will detect it and assign it a drive letter (assuming it is pre-formated). You can use "Disk Management" (search in the start menu) to format it.

I believe Disk Management can also be accessed by right clicking the My Computer icon and clicking manage. Please correct me if I'm wrong.

---

### Post by LaRoza on 2008-10-21
> **Grant A. said:**
> I believe Disk Management can also be accessed by right clicking the My Computer icon and clicking manage. Please correct me if I'm wrong.

In Vista, there is no My Computer icon.

In my setup, there are no desktop icons at all. I'm unfamiliar with the various ways of doings things in Windows though.

---

### Post by Colro on 2008-10-21
Well, being against the Windows EULA is of no concern to me for sure. However, the 1.5TB is one of the fastest non-raptors on the market right now, and this 160GB is old and slow, so I want to just rip it out of my case for good. I'll look in to Norton Ghost, but I was hoping there would be an easier way (such as copying the partition over directly using GParted). Thanks for all of the suggestions so far :)

---

### Post by LaRoza on 2008-10-21
> **Colro said:**
> Well, being against the Windows EULA is of no concern to me for sure. However, the 1.5TB is one of the fastest non-raptors on the market right now, and this 160GB is old and slow, so I want to just rip it out of my case for good. I'll look in to Norton Ghost, but I was hoping there would be an easier way (such as copying the partition over directly using GParted). Thanks for all of the suggestions so far :)

You can use free software to clone, see the link in my sig.

My concern was that it wouldn't work after ;)

---

### Post by Colro on 2008-10-21
I fail to see why it wouldn't. So long as the entire partition is copied over at a low level, wouldn't it be just like before? I know Vista doesn't complain much when its partition is constantly resized, so this shouldn't be any different.

---

### Post by igknighted on 2008-10-22
> **Colro said:**
> I fail to see why it wouldn't. So long as the entire partition is copied over at a low level, wouldn't it be just like before? I know Vista doesn't complain much when its partition is constantly resized, so this shouldn't be any different.

It will, however, recognize when there is new hardware present and un-activate itself.  If it does this, you need a re-install.

---

