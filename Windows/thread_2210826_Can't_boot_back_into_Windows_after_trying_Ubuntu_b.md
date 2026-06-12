---
title: "Can't boot back into Windows after trying Ubuntu by booting from USB"
date: 2014-03-12
forum: Windows
---

### Post by cole.h.cohen on 2014-03-12
Apologies if this is in the wrong section, could someone point me to a better place if so?

As the thread title says, I started a live session of Ubuntu (13.10) from a usb stick, used it for a while and had a look around and whatnot. I did open the "Install Ubuntu" tool but did not go through with the installation (I may install on a partition at a later date), this i guess is where the problem was introduced. Now when I shut down my computer, remove the USB stick and boot up again, I get a generic "Please install an operating system" message. I tried to see if I could get into the BIOS by tapping F2 or F12 while starting up but that didn't help. 

I ran boot repair, and [http://paste.ubuntu.com/7082156/](http://paste.ubuntu.com/7082156/) here is the report from that. 

[http://imgur.com/oCwrWL4](http://imgur.com/oCwrWL4) here is a screenshot of GParted and the "disks" tool. That big partition is where all my data from windows is stored, there's the Windows launcher partition etc, but I can't actually boot into them. Confusingly, the disks programme lists the partition type of what was a Windows partition to be a Linux LVM. Why would there be Linux partitions on my HDD when I didn't actually run an install?

No partitions have had their sizes changed or anything like that, so I guess I should still have all the data in there, I just can't figure out how to get it recognised as a Windows partition!

Any help would be much appreciated, my Googling hasn't turned up much useful stuff (too many shared words and phrases with different, more common, problems).

---

### Post by monkeybrain20122 on 2014-03-12
deleted for double posting.

---

### Post by monkeybrain20122 on 2014-03-12
> **cole.h.cohen said:**
>  I did open the "Install Ubuntu" tool but did not go through with the installation .

Well how far did you go? Obviously the label of the drive has changed. If the data files are not erased you should be able to access them from a live usb and then transfer them to another drive.

---

### Post by cole.h.cohen on 2014-03-12
I got as far as the partition manager and then stopped, but have also run boot repair and opened up GParted (without applying any changes). Yeah the label has indeed changed somewhere along the way! 

The first time I booted up with the live USB I could access the files on the other partitions as devices from the launcher bar at the side. Since restarting (back into the live USB) I can't see them though. I can still see "WINRE" - the windows recovery partition.

edit:

Looking over my posts, I don't think I was completely clear, I'm looking to revert the labels on my partitions to how they were before I tried Ubuntu. Would that be possible using GParted or something? Thanks.

---

