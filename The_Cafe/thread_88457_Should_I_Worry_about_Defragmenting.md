---
title: "Should I Worry about Defragmenting?"
date: 2005-11-10
forum: The Cafe
---

### Post by Ubuntist on 2005-11-10
Being a Linux newbie, I was slightly taken aback when I learned that the file systems available for Linux do not allow defragmentation.  Is this a big deal, or is it something that isn't really needed under Linux?

---

### Post by cedjo on 2005-11-10
As linux can use some journalized FS, like ext3, reiser, etc... there's no need to have a defragmenter.
But elementary rule is to have a backup of your informations (not in case fo fragmentation, but in case of hardware failure)

---

### Post by Ubuntist on 2005-11-10
If you'll forgive my ignorance, what is journalization?

---

### Post by dbott67 on 2005-11-10
[QUOTE=Ubuntist]If you'll forgive my ignorance, what is journalization?[/QUOTE]

Journaling is essentially a log of all scheduled file system activities.  In the event of a crash, the journal can be read to verify the completion of any file system activities.  If the system finds any inconsistencies, they will be corrected.

You can read a good article here: 
[http://en.wikipedia.org/wiki/Journaling_file_system](http://en.wikipedia.org/wiki/Journaling_file_system)

-Dave

---

### Post by GeneralZod on 2005-11-10
Basically, the general consensus seems to be that no, you don't have to worry about fragmentation.  As I understand it, this is not because of journalling but because Linux's filesystems are simply more intelligent with respect to where they place their files, so fragmentation occurs less in the first place and, when it does, it is less of an issue.

---

### Post by ssam on 2005-11-10
just make sure you have a few percent of the disk free and you should be ok with out defraging

---

### Post by Ubuntist on 2005-11-10
Thanks everybody!

---

