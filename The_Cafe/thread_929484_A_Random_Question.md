---
title: "A Random Question"
date: 2008-09-25
forum: The Cafe
---

### Post by FLCL on 2008-09-25
I was just curious of this. When transfering files within the same drive in ubuntu, it does not need to re-copy the entire file/folder to the new location, but simply moves it there in a flash. As well when you transfer files to another drive, they copy with very nice speed. Compared to Windows, where everything is a tedious wait time for all large files; relocation or copying. Why is this? :)

---

### Post by wolfen69 on 2008-09-25
i dont question it. i enjoy it.

---

### Post by xeth_delta on 2008-09-25
> **FLCL said:**
> I was just curious of this. When transfering files within the same drive in ubuntu, it does not need to re-copy the entire file/folder to the new location, but simply moves it there in a flash. As well when you transfer files to another drive, they copy with very nice speed. Compared to Windows, where everything is a tedious wait time for all large files; relocation or copying. Why is this? :)

Relocation of a file in the same partition is simply a change in the name of the file/partition (AFAIK). This is why, also when you intend to rename a file, you simply use the "mv" command. Don't know if Windows does this, too.

You can learn more about mv if you open a terminal and type:
```
man mv
```
type "q" to exit the manual.

About transfer between different partitions, I am not sure. maybe the file system is faster. I don't have Windows on my computer, so I really can't tell right now.

---

### Post by FLCL on 2008-09-25
> **wolfen69 said:**
> i dont question it. i enjoy it.

Indeed haha. Windows takes forever to copy files, It would go something like this "hm...i would move my music to another another directory...buut, i feel like using my computer some time this year."

---

### Post by uberdonkey5 on 2008-09-25
> **xeth_delta said:**
> Relocation of a file in the same partition is simply a change in the name of the file/partition (AFAIK). This is why, also when you intend to rename a file, you simply use the "mv" command. Don't know if Windows does this, too.

You can learn more about mv if you open a terminal and type:
```
man mv
```
type "q" to exit the manual.

About transfer between different partitions, I am not sure. maybe the file system is faster. I don't have Windows on my computer, so I really can't tell right now.

from my ubuntu manual I have, they confim this (above) and state that windows copies and then deletes old file when it moves a file (and then presumably when you defragment it pretty much sticks it back where it was...but you have to wait for that too!)

I noticed a BIG difference between copying large video files from a USB drive into windows (vista) and copying them to ubuntu (on the same computer). Indeed, my friend laughed when I was copying a file into windows, and I shut down windows, started ubuntu and copied the file in ubuntu in about 1/8 th of the time windows was telling me I had to wait. Not sure why this is, but guess file system is faster.

---

### Post by pp. on 2008-09-25
> **FLCL said:**
> Compared to Windows, where everything is a tedious wait time for all large files; relocation or copying. Why is this? :)

You can move files in Windows as well, at least the API provides that function. Last time I looked, the function was called 'rename'. I seem to remember that moving a file or directory using Windows Explorer copied the file while 'moving' (renaming) the same from the command line just moved the directory entries without touching the files.

It's been a while since I took an interest in such things, and it's perfectly possible that my recollections are not accurate.

Moving stuff from an USB stick to the hard drive might be slow in Windows on account of virus scanning. On the other hand, it might be a genuine difference in the respective speeds of the file system. I seem to recall that the Linux file system processes can cache very large portions of a drive. That can produce the mistaken impression that Linux writes files much faster than Windows does. However, once Windows says the file is copied is has been completely written to the drive while in Linux you may have to wait a while for the actual writing to complete.

Take with a grain of salt. It's all hearsay.

---

