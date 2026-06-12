---
title: "Setting up RAID on Lenovo TS430; Ubuntu still sees two drives instead of one virtual?"
date: 2011-12-28
forum: Server Platforms
---

### Post by diablo75 on 2011-12-28
I'll have to admit I've never setup one of these servers before.  It's a Lenovo TS430 and I'm trying to use the on-board LSI MegaRAID configuration tool.  I'm fairly certain I've got the two 500 GB hard drives in this system initialized as a single virtual drive, at least from what I've been able to see from within the MegaRAID configuration utility.  The problem is that, I'm not sure, and when I go to install Ubuntu 10.04 LTS it doesn't allow me to create any partitions.  However if I cancel out of the installer and later run Gparted from the System menu, I am able to access both drives separately.  

I didn't notice that I could see both drives the first time I tried to install so I formated the first drive and installed to it.  No problems, until I rebooted and the RAID utility claimed the array had suddenly become degraded and it began to attempt a rebuild.  This was going to take forever so I aborted the rebuilt, cleared the RAID configuration and recreated it from scratch trying to make sure I got everything done in that utility.  I'm running into the same problem and so here I am.  Is it normal to see both drives from a Live CD when you have a RAID array initialized?

---

### Post by rubylaser on 2011-12-28
What is the model of the RAID card?  It sounds like you may have a [FakeRAID]("https://help.ubuntu.com/community/FakeRaidHowto") card.

---

### Post by diablo75 on 2011-12-28
Well, to be honest I'm not sure.  It's whatever is built into the motherboard of the Lenovo TS430.

Here is the tutorial for this particular server that shows the exact configuration utility used to setup things (and glancing over this I should mention I already set the mode of the drives from SATA to RAID mode in the BIOS before attempting to create and initialize a new array).

[http://www.google.com/url?sa=t&rct=j&q=lenovo%20ts430%20raid&source=web&cd=2&ved=0CCkQFjAB&url=http%3A%2F%2Fwww.lenovo.com%2Fshop%2Famericas%2Fcontent%2Fpdf%2Fservers%2FConfiguringRAID100onTS430.PDF&ei=dEf7TsbGAe3FsQLrxdHIAQ&usg=AFQjCNFab7Gpz7lLCSXLT7kOzOHVQ7bRyg&cad=rja](http://www.google.com/url?sa=t&rct=j&q=lenovo%20ts430%20raid&source=web&cd=2&ved=0CCkQFjAB&url=http%3A%2F%2Fwww.lenovo.com%2Fshop%2Famericas%2Fcontent%2Fpdf%2Fservers%2FConfiguringRAID100onTS430.PDF&ei=dEf7TsbGAe3FsQLrxdHIAQ&usg=AFQjCNFab7Gpz7lLCSXLT7kOzOHVQ7bRyg&cad=rja)

I should also mention I am trying to install the Desktop edition of 10.04, not the server edition.

Edit:  lspci shows:

RAID bus controller: Intel Corporation Cougar Point SATA RAID Controller (rev 05)

---

### Post by lukeiamyourfather on 2011-12-28
The RAID controller on the motherboard of that server is a "fake" RAID controller. In other words the RAID calculations are done on the CPU rather than a dedicated processor on the RAID controller.

---

### Post by diablo75 on 2011-12-28
From a glance at a couple pages it looks like... my best option might be to go with SoftRAID.  How difficult is it to rebuild a degraded drive in that kind of scenario?

---

### Post by rubylaser on 2011-12-28
mdadm is simple and very effective to use and recover from failed disks.

---

### Post by diablo75 on 2011-12-28
I'm getting the impression from the guides I've read so far that you can't setup a software-based RAID1 array using the manual partioning tool available with Ubuntu desktop edition.  Is that right?  Or might it be available on the Alternate install disc?  Or will I have to install the Server edition?

---

### Post by rubylaser on 2011-12-28
The Alternate install disc supports setting up a RAID array during installation.

---

### Post by diablo75 on 2011-12-29
> **rubylaser said:**
> The Alternate install disc supports setting up a RAID array during installation.

Thanks.

---

