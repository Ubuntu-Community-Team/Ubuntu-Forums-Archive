---
title: "Howto delete files in a secure way"
date: 2009-11-03
forum: Security
---

### Post by Soul-Sing on 2009-11-03
The best and safe way to delete p/a confidential files is to encrypt them, because linux/ubuntu doesn't come with another/secure alternative.
Agree/ disagree?

---

### Post by CharlesA on 2009-11-03
Use wipe?

[http://www.cyberciti.biz/tips/linux-how-to-delete-file-securely.html](http://www.cyberciti.biz/tips/linux-how-to-delete-file-securely.html)

---

### Post by TheForumTroll on 2009-11-03
Is Wipe able to overwrite all free space on a drive with random data? Or is there some other way to do this?

---

### Post by wojox on 2009-11-03
Encryption would work. The only other thing I thought would be to create a partition called "docs" and make it ext2. Then 

```
sudo apt-get install secure-delete
```

Which you could use to truly delete files. Which is the same as wipe and shred. You just can't have a journaling file-system to use these utilities.

---

### Post by TheForumTroll on 2009-11-03
Looking in the repo there sure is a lot of FUD in the file descriptions. Like this one from secure-delete:

```
Even if you overwrite a file 10+ times, it can still be recovered. 
```

Or from Wipe:
```
A technique called Magnetic Force Microscopy
(MFM) allows any moderately funded opponent to recover the last two or three
layers of data written to disk
```

One of my interests is Computer forensic and I'm willing to bet an arm and a leg that no one in the entire world is able to recover a complete file after it has been overwritten just one time on any modern drive.

---

### Post by hggdh on 2009-11-03
> **leoquant said:**
> The best and safe way to delete p/a confidential files is to encrypt it, because linux/ubuntu doesn't come with another/secure alternative.
Agree/ disagree?

Respectfully disagree. Linux comes with coreutils' shred, which is good enough.

---

### Post by Agent ME on 2009-11-03
> **TheForumTroll said:**
> Is Wipe able to overwrite all free space on a drive with random data? Or is there some other way to do this?
In a terminal:
```
cat /dev/urandom > BIGFILE ; rm BIGFILE
```

---

### Post by rookcifer on 2009-11-04
> **TheForumTroll said:**
> Looking in the repo there sure is a lot of FUD in the file descriptions. Like this one from secure-delete:

```
Even if you overwrite a file 10+ times, it can still be recovered. 
```

Or from Wipe:
```
A technique called Magnetic Force Microscopy
(MFM) allows any moderately funded opponent to recover the last two or three
layers of data written to disk
```

One of my interests is Computer forensic and I'm willing to bet an arm and a leg that no one in the entire world is able to recover a complete file after it has been overwritten just one time on any modern drive.

You are right.  There was even a paper published last year where researchers tried to use a MFM to recover once overwritten data.  Their conclusion was that it's impossible.

To answer the OP's question:  you can install the "secure-delete" tools and then use the "sfill" option to securely erase all free space from a partition or disk.  Just read the man page for precise options.

---

### Post by Soul-Sing on 2009-11-04
I must say shred does nicely integrates -via nautilus-actions- with nautilus.

---

### Post by TheForumTroll on 2009-11-04
Is there a way to get a package information changed? I was looking for sfill myself but only stumbled over it by accident. Adding to secure-delete what tools it contains would be a great help i think.


I would run sfill with -ll to only get one pass unless you got lots of time. I started my one pass yesterday on one drive and it is still running ;)

---

### Post by hggdh on 2009-11-04
> **TheForumTroll said:**
> I would run sfill with -ll to only get one pass unless you got lots of time. I started my one pass yesterday on one drive and it is still running ;)

Well, yes, does not surprise me (caveat: I have not looked at the source for sfill). sfill seems to use /dev/urandom (the default source of entropy). So, if you are heavily drawing on /dev/[u]random, the entropy source gets deplected, and it will take some time for it to acquire more entropy. If you do that for a LARGE file/space, it will take a long, REALLY long time to get it done...

This is a change done in shred a few months ago, to use another source of entropy.

---

### Post by rookcifer on 2009-11-04
I personally like BCWipe.  It allows for using SHA-1 for faster overwriting as well as many other options.  The only problem is it isn't open-source. :(

---

### Post by TheForumTroll on 2009-11-04
Hmm, maybe that could be a small project. A small utility to overwrite free drive space as fast as possible while still being reasonably safe. It's not like most users need multiple passes security or 100 % random data on all free space anyway. On the other hand I don't think I trust my programming skills enough to let it loose on other peoples data :KS

---

### Post by Agent ME on 2009-11-04
> **TheForumTroll said:**
> Hmm, maybe that could be a small project. A small utility to overwrite free drive space as fast as possible while still being reasonably safe. It's not like most users need multiple passes security or 100 % random data on all free space anyway. On the other hand I don't think I trust my programming skills enough to let it loose on other peoples data :KS
If using /dev/urandom is too slow for erasing your free space for you, try this instead:
```
cat /dev/zero > BIGFILE ; rm BIGFILE
```

---

### Post by fela on 2009-11-04
> **Agent ME said:**
> In a terminal:
```
cat /dev/urandom > BIGFILE ; rm BIGFILE
```

Ah, the joys of creative command line work. So beautiful. Although you might want to use /dev/zero instead of /dev/urandom, if all you want is zeros. With zeros you get a zero chance of all your data coming back, but if the overwritten data is random, there's the smallest possibility that the data you overwrite with is exactly the same as the data that gets overwritten...a teeny chance but still theoretically possible ;)

edit: turns out someone said the same thing for different reasons.

---

### Post by TheForumTroll on 2009-11-05
> **Agent ME said:**
> If using /dev/urandom is too slow for erasing your free space for you, try this instead:
```
cat /dev/zero > BIGFILE ; rm BIGFILE
```

Is this usable on the root drive too?

---

