---
title: "USB 3.0 backup drive logical disconnect"
date: 2011-10-11
forum: Server Platforms
---

### Post by outerringz on 2011-10-11
I am running Ubuntu Server 10.04.3 LTS 64-bit, Kernal version  2.6.32-34-server. I have installed a Rosewill PCI Express USB 3.0 card  that uses the NEC (uPD720200) chipset. This server has a large RAID 5  array, using SATA drives, that is used for daily backups and two Western  Digital USB 3.0 external hard drives for rotating Friday backups.

The  issue I'm having is that the USB 3.0 drives will randomly logically  disconnect from the system as in no longer listed in fdisk -l or lsusb.  However, even after a logical disconnect happens, the 3.0 root hub is  still listed in lsusb. This logical disconnect obviously interrupts my  backup process and the only way I have found to reconnect the drive  logically is to reboot the server, or disconnect and reconnect the drive  physically. 

Prior to installing the USB 3.0 card, I was doing  this same backup scenario using USB 2.0 external drives on the on-board  USB 2.0 controller and never had any issue with logical disconnects. I  need the increased speed of USB 3.0 because my backups are now too large  to rely on the slow speeds of USB 2.0. 

This server was running  Ubuntu 9.10 for a long time, and I confirmed that this was the first  version to support USB 3.0 natively, but after the USB 3.0 card  installation, and the issue with the drives logically disconnecting, I  decided to upgrade to 10.04.3 to see if that might correct the issue,  but it unfortunately did not.

I'm at a loss on how to trouble shoot this further, any help anyone can offer is appreciated.

---

### Post by szafran on 2011-10-12
Almost same here.
I have a SSD OCZ Vertex 3 in a external (Enermax Jazzmate EB211U3-B USB 3.0) enclosure connected to the internal USB 3.0 (Gigabyte GA-890GPA-UD3H) controller, and I'm using it for MySQL. It disconnects itself from time to time damaging the DBs, but in my case it reconnects almost instantly, but as a different dev (eg. now it went from sdj to sds). It's very annoying. I don't have any other way of connecting this drive, and I've bought it specially for MySQL (and on USB 3.0 it has ~120MB/s better perf than on internal SATA2 controller).

My config: [click]("http://szafr4n.pl/nas")

Does anyone have any idea how to fix this problem ?


______
Regards
Szafran

---

### Post by outerringz on 2011-10-12
I have found a few related post on various forums that seems to imply that this only occurs with a faulty drive or external drive case controller. I'm testing my secondary drive now and will report my findings.

---

### Post by szafran on 2011-10-13
The thing is that this harware works perfect under Win, without any disconnects etc. So I'm pretty confident that it's a software fault.

---

### Post by WasMeHere on 2011-10-13
So far I have only a USB 3 stick (relatively fast also with USB 2), but no USB 3 connection to a computer yet, but I am interested and try to understand how well it is supported, before buying something.

My humble contribution to this thread is to suggest using *eSATA* to connect external disk(s) to get much better speed than USB 2.0. I have been using eSATA for years, and it works well.

I guess that eventually the software will catch up. By the way, I suggest that you report it as a software bug.

Having fun finding out about Ubuntu :-)
Olle

---

### Post by szafran on 2011-10-13
I've tried that. But adding another controller to my config (see earlier posts) stops internal SATA3 controller from discovering drives (and the system doesn't boot) - probably some base mem issue. So I'm stuck with USB 3.0 - which is faster than eSATA2 (most current controllers do work with only SATA2 speeds)

---

### Post by outerringz on 2011-11-02
Looks like this was a faulty USB 3.0 drive. My second drive, and my new replacement drive are both working fine.

---

### Post by szafran on 2011-11-02
So far anything that I connect to USB3 ports gets disconnected at some point. I don't think that over 10 USB3 devices are faulty (some were exchange, and the same thing happens with new ones). But everything works just fine under Win7 on the same config.

---

