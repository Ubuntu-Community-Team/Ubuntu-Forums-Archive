---
title: "Access to ext3-partition from Windows Vista Home Basic"
date: 2010-06-21
forum: The Cafe
---

### Post by xoomer.ap on 2010-06-21
Hi to everyone.
Actually, I can not correctly do this thing with popular programs for this. Noticeable, after installing driver for this FS, OS seeing drive, but on request for open it, I proposed to ...format drive. Of course, I can not do this. :)

Has anyone faced with similar?  What should I do for troubleshoot this?

---

### Post by nerdy_kid on 2010-06-21
i ran into this issue when i was using vista, never really solved it.  From what I understand the ext driver for windows is rather outdated and i dont think (could be totally wrong) that anyone is really working on it anymore.  I dont think there is really a fix.  What you could do is put your $HOME folder on a seperate partition formated as say NTFS and then you will be able to access your documents if not your system files from windows.

---

### Post by oldfred on 2010-06-21
You cannot put /home into a NTFS partition but should just create a shared data NTFS partition. I did this three years ago with my XP and it has worked very well.

Some windows folks suggest keeping all your windows data in a separate data partition so when you have to reinstall windows your data is still safe.:)

I do not recommend writing into any system partition either windows or Ubuntu root from a different system unless it is an emergency repair. You can easily read and use the shared data without issue.

---

### Post by blur xc on 2010-06-21
> **nerdy_kid said:**
> i ran into this issue when i was using vista, never really solved it.  From what I understand the ext driver for windows is rather outdated and i dont think (could be totally wrong) that anyone is really working on it anymore.  I dont think there is really a fix.  What you could do is put your $HOME folder on a seperate partition formated as say NTFS and then you will be able to access your documents if not your system files from windows.

I've used ext2fs to access my ext3 partitions from Vista.  It was a while ago, and I think Vista didn't like the drivers at first, but it worked in the end.  But it's been a long time since I've booted into vista for anything.

might have been from this site- [http://www.fs-driver.org/](http://www.fs-driver.org/)

BM

---

### Post by xoomer.ap on 2010-06-21
**nerdy_kid**, as for me - lets /home stay reiserfs. I am not sure, that "mixing" can bring me peace of mind (if I correctly talking). Lets each OS stay with native FS-s. ;)
In Win Vista I just want access to my downloaded files in Linux, that  are on second drive without system partitions from any OS-s.

**oldfred**,
> I do not recommend writing into any system partition either windows or  Ubuntu root from a different system unless it is an emergency repair.My  opinion is similar. :)
By the way:
> You cannot put /home into a NTFS partitionWhy?

**blur xc**, yeah, I can not correctly run that driver - exactly one from that cases, about which I'm already wrote. :)
Anyway, thanks for the post **to all**! ;)

---

### Post by cariboo on 2010-06-21
If your partition is formatted as ext4, there is no way you can access it from vista/windows 7, there just aren't drivers available.

---

### Post by oldfred on 2010-06-21
Windows partition NTFS or FAT do not support Linux style permissions and ownership. Part of the underlying difference in security and design.

---

### Post by Hman242 on 2010-06-21
Windows can't read the EXT format past EXT2. If you have EXT3 or 4, then you're SOL. Sorry dude. I would love for someone to prove me wrong by finding a solution though.

---

### Post by FuturePilot on 2010-06-21
> **Hman242 said:**
> Windows can't read the EXT format past EXT2. If you have EXT3 or 4, then you're SOL. Sorry dude. I would love for someone to prove me wrong by finding a solution though.

It can read up to and including Ext3, but it mounts it as Ext2. However most distros use a 256bit inode size. The Windows Ext2 driver does not support over a 128bit inode size. So unless you manually formatted the drive with a 128bit inode size you can't access it from Windows anyway.

---

### Post by nerdy_kid on 2010-06-21
found this: [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)
not sure how accurate it is, just glanced at it.

---

### Post by xoomer.ap on 2010-06-24
**FuturePilot**, ok, thanks for the info! :)
**nerdy_kid**, seems that software is for opening files with filesystem inside, etc.

---

