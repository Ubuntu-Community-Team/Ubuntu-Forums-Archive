---
title: "Wipe VS Shred - Your opinion?"
date: 2008-07-24
forum: Security
---

### Post by MaddMatt on 2008-07-24
I know that there has been some discussion about the validity of securely deleting data [(here)]("http://ubuntuforums.org/showthread.php?t=797252&highlight=shred+wipe"), but I want to know what people feel about the differences between Shred and Wipe. 

As far as I can tell, Wipe gives more options from the command line, such as recursive mode, but doesn't offer zeroing the file at the end to "disguise" the data wipe. Shred on the other hand, does have zeroing mode, but has less in the way of command line options. 

Besides this, does anyone have understanding about which more effectively or securely deletes data? Regardless of journaling file systems, which one does a better job? 

Cheers, 
-M

---

### Post by cdenley on 2008-07-24
It looks like wipe uses patterns suggested by Peter Gutmann for most of the passes, which is probably a little better than using random data. I don't think it's necessary to make so many passes with modern hard drives, and the advantages from one tool to another are trivial. You might want to look at srm, which has recursive mode, can use zeros for the last pass, and does 27 passes with Peter Gutmann's special patterns. It also comes with other useful tools.
```

sudo apt-get install secure-delete
man srm

```
You might want to read other threads about the limitations of deleting individual files. The best way to destroy your data (without physically destroying your disk) is to use the "secure erase enhanced" function built into the firmware of modern hard drives. This will erase the entire disk, though.

---

### Post by MaddMatt on 2008-07-24
Good call there with "srm" - it certainly seems thorough, especially with the 0_SYNC mode: flushes disk caches to overwrite old data from the files being deleted. The suite has other programs for cleaning swap and /tmp files as well, so to me this looks like it beats both wipe and shred. Thanks for the tip!

---

