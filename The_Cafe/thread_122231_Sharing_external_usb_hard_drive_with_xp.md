---
title: "Sharing external usb hard drive with xp"
date: 2006-01-27
forum: The Cafe
---

### Post by jocke1s on 2006-01-27
Hi

I am pondering getting a new external harddrive. I would like to use it as a common disk from my ubuntu and my wifes xp computers.

Any pointers on how to set it up would be much welcomed.

It should preferably work even if just one of the computers are up and
running.

Any ideas?

/Joakim

---

### Post by blueturtl on 2006-01-27
Well for starters I'd recommend getting a Seagate disk (yes, there are always people who would differ as all brands have bad apples / batches), for example [these 3.5 inch externals]("http://seagate.com/products/retail/external") have received great reviews in comparison to La Cie or Maxtor drives. Seagate's drives seem to run cool and stable.

Using an external hard-disk with Windows might become problematic for these reasons:

[LIST]
[*]Microsoft has a patent over NTFS (and recently claimed a patent over FAT).
[*]Out of the two systems currently the only one supported properly by Linux (due to obvious reasons) is FAT which happens to be quite outdated; no journaling, wastes space on large disk drives and finally has no support for very large files.
[/LIST]

> It should preferably work even if just one of the computers are up and
running.

Another thing: if you have an external drive with a FireWire or USB interface, you can only connect it to one PC at a time. For that kind of functionality another computer acting as a disk server would be preferable as it would also override any problems you might have with filesystems.

---

### Post by jocke1s on 2006-01-27
thanks for these clarifications. It looks like I would like to set up a file server then.
Could I have my linux box set up 24/7 and add a large external disk or should I go for a separate pc as a server?

/Joakim

---

### Post by r0nin on 2006-01-27
There's an Ext2/3 driver for windows: [http://www.fs-driver.org/](http://www.fs-driver.org/)
I am using Ext3 my external HD and have had no serious probs. Just don't repartition the HD under Windows though, I lost a whole HD worth of data because it ended up all corrupted.

---

