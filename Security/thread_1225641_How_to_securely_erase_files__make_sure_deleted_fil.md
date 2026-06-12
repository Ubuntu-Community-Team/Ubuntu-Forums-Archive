---
title: "How to securely erase files / make sure deleted files can't be recovered"
date: 2009-07-28
forum: Security
---

### Post by NDLunchbox on 2009-07-28
Hi,
I have two Ubuntu computers (a Lenovo ultraportable and a bare-bones Shuttle SFF box) that I've been using to learn and test some security tools (like password crackers, network monitors and sniffers, vulnerability scanners, etc).

I've started applying some of what I've learned to audit my network at work and I want to make sure that any sensitive data used or exposed is completely and securely removed since both computers are actually my own and they're small enough that theft is a worry.

I read shred doesn't work with 100% effectiveness with EXT3 since there will still be data in the journal.  I've already deleted the files and am looking for a way to make sure they can't be recovered short of using DBAN on the entire drive.

Would filling the partition with random data work?  I noticed JtR can easily do this if you use it's mangling rules to output a password list and loop it through twice.  Are there other programs that can do this?

The files ranged from simple text files (password lists, hash dumps, etc.) to backup files and Virtual Machines used in a test environment that had Active Directory data on them.

As you can see I need to be assured they are safely off the machines.  I'd also like to include precautions I took to make sure the actual results of the audit were destroyed in my executive summary... I just don't want to have to wipe the entire computers / partitions.

Thanks!
-NDLB

---

### Post by meeples on 2009-07-28
theres the shred tool i think would probably be the only option unless you want to pour acid on the hard drives:) 

i think in terminal its

```
man shred
```

i have never used it so i dont know anymore sorry

---

### Post by hggdh on 2009-07-28
I am not sure there is anything that would clean up the journal for journaled filesystems. Anyways, the journal will be rewritten quite fast, so this should not be a problem (it only stores the last few transactions, *not* the whole life of the fs).

In other words: shred is good enough. The real only other options are:
* (a) physical destruction of the harddrive
* full shred of the harddrive
* encrypted filesystem.

The *new* shred, available on Karmic onwards, will do all you need; it now defaults to 3 passes only (albeit, right now, all of them random), and is much faster than the old, 6.10 version, available on Intrepid/Jaunty. The 6.10 shred is slower, but still very good for shredding. The shred limitation is related to the fact that the journal is not accessible by userland applications, and *might* be an exposure if you shred a file and *immediately* have the computer taken for forensic analysis.

Also, depending on your Ubuntu version, you can use ecryptfs, and have an encrypted filesystem.

---

### Post by wojox on 2009-07-28
Totally delete a file

```
shred -f -v -z -u file.txt
```

---

### Post by NDLunchbox on 2009-07-28
> **hggdh said:**
> I am not sure there is anything that would clean up the journal for journaled filesystems. Anyways, the journal will be rewritten quite fast, so this should not be a problem (it only stores the last few transactions, *not* the whole life of the fs).

In other words: shred is good enough. The real only other options are:
* (a) physical destruction of the harddrive
* full shred of the harddrive
* encrypted filesystem.

The *new* shred, available on Karmic onwards, will do all you need; it now defaults to 3 passes only (albeit, right now, all of them random), and is much faster than the old, 6.10 version, available on Intrepid/Jaunty. The 6.10 shred is slower, but still very good for shredding. The shred limitation is related to the fact that the journal is not accessible by userland applications, and *might* be an exposure if you shred a file and *immediately* have the computer taken for forensic analysis.

Also, depending on your Ubuntu version, you can use ecryptfs, and have an encrypted filesystem.

Thanks!  How about if I've already deleted the files... anyway to shred the unused space on a partition?

---

### Post by lsmobrian on 2009-07-28
[http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html)

secure-delete is probably what you're looking for

---

### Post by hggdh on 2009-07-28
> **NDLunchbox said:**
> Thanks!  How about if I've already deleted the files... anyway to shred the unused space on a partition?

Well... now they are (mostly) lost. Of course, they can still be accessed, but we do not *know* where they were located. But there is still something you can do, but more costly:

(1) write a small script to fill the free filesystem space (i.e., create a file large enough, by writing zeros, or ones, or whatever);
(2) shred this file.
(3) if it is a large FS, and you are *not* running Karmic, while shred runs, go take a shower. Or sleep. Or travel.

If the FS is you home directory, then you will be better off by exiting X (Gnome, xfce, or KDE), and doing it from a console terminal.

---

### Post by shaggy999 on 2009-07-28
Install the *secure-delete* package and run the program 'sfill'. Make sure you also wipe the swap space using the 'sswap' command.

---

### Post by HermanAB on 2009-07-28
The correct way is to always encrypt your disk drive.  Then you simply hit yourself upside the head with a brick when you need to forget the password.

---

### Post by dragos2 on 2009-07-29
> **HermanAB said:**
> The correct way is to always encrypt your disk drive.  Then you simply hit yourself upside the head with a brick when you need to forget the password.

Funny :)

I don't know if this is a urban tale/myth or not but I read that you must overwrite a file
7 times at least to become unreadable even using expensive and not purchasable government
tools :D

I have been able to recover some lost files after hard format, but not shreded.

---

### Post by NDLunchbox on 2009-07-29
> **lsmobrian said:**
> [http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html)

secure-delete is probably what you're looking for

Yup, I think that is what I need!

> **hggdh said:**
> Well... now they are (mostly) lost. Of course, they can still be accessed, but we do not *know* where they were located. But there is still something you can do, but more costly:

(1) write a small script to fill the free filesystem space (i.e., create a file large enough, by writing zeros, or ones, or whatever);
(2) shred this file.
(3) if it is a large FS, and you are *not* running Karmic, while shred runs, go take a shower. Or sleep. Or travel.

If the FS is you home directory, then you will be better off by exiting X (Gnome, xfce, or KDE), and doing it from a console terminal.

I think I was accomplishing something similar to this with my massive, partition filling wordlists output by JtR.

> **shaggy999 said:**
> Install the *secure-delete* package and run the program 'sfill'. Make sure you also wipe the swap space using the 'sswap' command.

Thanks again!

I'm going to get the secure-delete tools and use them to wipe the free space, swap, etc.

---

### Post by bodhi.zazen on 2009-07-29
> **hggdh said:**
> I am not sure there is anything that would clean up the journal for journaled filesystems. Anyways, the journal will be rewritten quite fast, so this should not be a problem (it only stores the last few transactions, *not* the whole life of the fs).

In other words: shred is good enough. The real only other options are:
* (a) physical destruction of the harddrive
* full shred of the harddrive
* encrypted filesystem.

The *new* shred, available on Karmic onwards, will do all you need; it now defaults to 3 passes only (albeit, right now, all of them random), and is much faster than the old, 6.10 version, available on Intrepid/Jaunty. The 6.10 shred is slower, but still very good for shredding. The shred limitation is related to the fact that the journal is not accessible by userland applications, and *might* be an exposure if you shred a file and *immediately* have the computer taken for forensic analysis.

Also, depending on your Ubuntu version, you can use ecryptfs, and have an encrypted filesystem.

Overwriting hard drives from /dev/zero has been shown to be sufficient.

[Can Intelligence Agencies Read Overwritten Data?]("http://www.nber.org/sys-admin/overwritten-data-gutmann.html") 

[Overwriting Hard Drive Data « SANS Computer Forensics, Investigation, and Response]("http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/")

---

