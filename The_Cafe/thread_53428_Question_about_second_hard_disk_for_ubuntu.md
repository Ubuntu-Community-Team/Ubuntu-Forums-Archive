---
title: "Question about second hard disk for ubuntu"
date: 2005-07-31
forum: The Cafe
---

### Post by PatrickMay16 on 2005-07-31
Yo, people. Sorry if this is a bit of a long post, and sorry if it's in the wrong subforum. I wasn't quite sure where to put it, so I put it here.

I want to install Ubuntu on this computer without getting rid of windows, and I don't like the idea of re-sizing the NTFS partition on this hard disk. It sounds risky, and I don't like the fact that I'd lose some space due to it. Awhile ago, my brother built a computer and gave it two hard disks. He installed Windows on one hard disk, and the other hard disk was mostly unused. I came and installed Mandrake Linux 10.1 on  second (barely used) hard disk, and it set it up automaticall for duel booting. It worked without problems, and I was happy with it.
I liked that, so for my own computer, I have bought a second hard disk. It hasn't come in the mail yet so it's not installed yet. It's a 20GB IDE hard disk. 

Now, here're questions. I'm not such a clever guy, heh... but bear with me. When I put this hard disk in my computer, what will the jumper setting need to be? I'm not sure if it should be Slave or Master. I was thinking it should be master, but then would that cause conflicts with the other hard disk because that one is also master? I'd appreciate if someone could explain about Slave and Master to me. 

Also, will the Ubuntu installer automatically detect Windows on the other drive and set up GRUB so that an option to boot Windows will appear in the GRUB menu?

Thanks very much.

---

### Post by DJ_Max on 2005-07-31
Jumper settings on ATA drives differ from brand to brand. So I can't tell you the jumper settings for my Western Digital, if you buy a Maxtor. The instructions are on their website.

There should only be one "master". So make the second one "slave". The only practical difference between master and slave is that the PC considers the master "first" and the slave(s) "second", "third", and so forth.

As for Ubuntu recongnizing Windows, it should, but I don't know. If it doesn't it won't be much of a problem to set it up manually.

---

### Post by Brunellus on 2005-08-01
[QUOTE=DJ_Max]Jumper settings on ATA drives differ from brand to brand. So I can't tell you the jumper settings for my Western Digital, if you buy a Maxtor. The instructions are on their website.

There should only be one "master". So make the second one "slave". The only practical difference between master and slave is that the PC considers the master "first" and the slave(s) "second", "third", and so forth.

As for Ubuntu recongnizing Windows, it should, but I don't know. If it doesn't it won't be much of a problem to set it up manually.[/QUOTE]
 the Hoary installer detects windows automagically.  You can select Windows off the GRUB menu at startup, if you like.  I dual-boot my present computer (Call of Duty is too much fun to give up....) and it works like a charm.

Resizing the NTFS partition isn't a big deal, provided you've thoroughly defragged it...and then, having resized, defrag again.

---

### Post by WirelessMike on 2005-08-01
Assuming these are ide (not sata)...

Leave the jumpers in their default positions, they are typically set by default to allow the cable to decide, then put the cable on so that the master is whichever hdd your linux partition is on (this one will have grub in the bootloader sector), and slave is on the windows hdd (I'm assuming you're making absolutely no change to this hdd).

This will insure, if you're running ide hdds, that your hardware boot order is consistent with where grub is actually located.  Just in case--  The master connector of an 80-wire ide cable is on the end of the cable, the slave is between the master end and the mobo end (but you probably already knew that).

Obviously, to ease stress on your cable, you'll want to physically mount the "master" hdd over the "slave" hdd (unless you're wisely using round cables, in which case it won't matter much which is mounted where).

---

