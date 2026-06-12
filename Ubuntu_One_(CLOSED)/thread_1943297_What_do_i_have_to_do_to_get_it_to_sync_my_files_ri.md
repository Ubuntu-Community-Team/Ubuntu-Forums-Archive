---
title: "What do i have to do to get it to sync my files right."
date: 2012-03-19
forum: Ubuntu One (CLOSED)
---

### Post by moteprime on 2012-03-19
I have three computers with Ubuntu One on them, and i paid for 20 Gb of storage in the Ubuntu One cloud.
But it really doesn't work very well, and the support can't help me. What do i have to do to get it to sync my files, i don't want to loose any data.

One the 3 computers the 3 synced folders have these file counts.

Computer 1,2 and 3
1. Documents: 11.331 files
2. Documents: 11.332 files
3. Documents: 11.280 files

1. Pictures: 489 files
2. Pictures: 503 files
3. Pictures: 503 files

1. Ubuntu One: 489 files
2. Ubuntu One: 489 files
3. Ubuntu One: 497 files

It's not possible to figure out which of the files that are in the cloud, and what are on the different computers.

Can't i get it to recheck the local files against the ones in the cloud, or in anyway get it to rescan what's not synced, without up or downloading the hole thing again, the servers are really slow and it takes several days, and i will end up with lots of unsynced files again.

---

### Post by moteprime on 2012-03-26
Nobody? :-(

---

### Post by duanedesign on 2012-04-06
I would try deleting the metadata from one of the computers that appears to be missing files and see if that help. You can do that with the following commands:


Open a Terminal and run the commands:

```
u1sdtool -q

sudo rm -rf ~/.local/share/ubuntuone

u1sdtool -c
```

---

### Post by moteprime on 2012-04-07
Thanks.
It did help.
I had to delete the metadata on all computers, and after they downloaded some +15Gb of data it seems that they are synced again.

Would it not be possible to make a command that rescans the directories, compares the data and only downloads what's out of sync instead of so much data?

Thanks

---

