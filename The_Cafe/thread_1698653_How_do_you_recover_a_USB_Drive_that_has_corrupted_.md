---
title: "How do you recover a USB Drive that has corrupted freespace?"
date: 2011-03-02
forum: The Cafe
---

### Post by MasterNetra on 2011-03-02
For those who find this thread and have a similar problem.
1. Make sure you have the USB drive (or external drive?) plugged in.
2. Unless you don't care make sure all retrievable data is extracted from the device and backed up.
3. With preferably only the device in question connected enter:
```

dd if=/dev/zero of=/dev/sd? bs=1M

```
Replacing the question mark with the appropriate letter. (In most cases like in mine, it was sdb)

4. ???

5. Profit!

Original Message:
> 
While it was trying to move data on my 8GB Drive to make some freespace (for swap),then for seemly no reason at all gparted crashed and now it seems gparted cannot even read the drive at startup without crashing (If the drive is plugged in and it loads or I plug the drive and reload devices for gparted it crashes). Tried using Disk Utility but it just won't apply any changes even if I sudo it... I dunno what else to do... Even booted into windows, and its disk management utility could see it but couldn't do anything with it (the free space).


---

### Post by mips on 2011-03-02
Are you trying to recover the data or restore the drive?

If it's the data have a look at PhotoRec/TestDisk.

---

### Post by MasterNetra on 2011-03-02
> **mips said:**
> Are you trying to recover the data or restore the drive?

If it's the data have a look at PhotoRec/TestDisk.
Trying to Restore the drive, There was no data (i think) in the freespace, at least I don't think so, at any-rate I just want my drive back.

---

### Post by mips on 2011-03-02
Try zeroing it using dd and afterwards use gparted to create new partitions & format it.

```
dd if=/dev/zero of=/dev/sd**[COLOR="Red"]?[/COLOR]** bs=1M
```

?=Identify the correct drive before proceeding. You DON'T want to erase the wrong drive!

WARNING: This will erase the entire drive!

---

### Post by MasterNetra on 2011-03-02
> **mips said:**
> Try zeroing it using dd and afterwards use gparted to create a new partitions & format it.

```
dd if=/dev/zero of=/dev/sd? bs=1M
```

WARNING: This will erase the entire drive!

It would be sdb, sda would be my harddrive, which is something I don't want to zero. But yea zero-ing the flash drive now. Hopefully it will work.

---

### Post by mips on 2011-03-02
> **MasterNetra said:**
> It would be sdb, sda would be my harddrive, **which is something I don't want to zero**. But yea zero-ing the flash drive now. Hopefully it will work.

You definitely don't want to do that. Many a person has made that mistake before though.

Let us know how it goes.

---

### Post by MasterNetra on 2011-03-02
> **mips said:**
> You definitely don't want to do that. Many a person has made that mistake before though.

Let us know how it goes.

lol prehaps you should replace the sda? with sdb? just a thought. ;)

---

### Post by mips on 2011-03-02
> **MasterNetra said:**
> lol prehaps you should replace the sda? with sdb? just a thought. ;)

Done. Please edit my post where you quoted me else it's you to blame if things go wrong :lolflag:

---

### Post by MasterNetra on 2011-03-02
It worked! Had to use gparted to create a new partiton table, but I have my drive back! Yay!

---

### Post by mips on 2011-03-02
> **MasterNetra said:**
> It worked! Had to use gparted to create a new partiton table, but I have my drive back! Yay!

Cool bananas!

---

### Post by MasterNetra on 2011-03-02
> **mips said:**
> Cool bananas!

Thanks for the assist! I hereby mark this thread as solved!

---

