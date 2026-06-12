---
title: "I'm struggling with Raid USB-disks in Ubintu 24.04"
date: 2024-09-29
forum: Server Platforms
---

### Post by cgn1954 on 2024-09-29
I've had Ubuntu for many years now and have consumed some 4-5 servers. All of them had **external USB-disks** and I've only experienced troubles when an HDD crashed hardware wise, never spontaneous degrading&#8217;s, as at present.

I've recently installed a new HP small factor server (never had one before); it has four USB 3.1 ports. OS is Ubuntu 24.04.1. 

There's **four 16 TB HDD USB-drives** attached:
- Raid1 md0 = 16 + 16 TB 
- Raid1 md1 = 16 + 16 TB 
- Raid0 md2 = md0 + md1, witch gives approx. 32 TB. 

The disks are not brand new; they have been working for about 1,5 years on the old Backup-server.

  The problem is that in md0 or md1 a sdN-disks fails (degrades), the log says only "Fail". Syslog: &#8220;md/raid1:md1: Disk failure on sdf1, disabling device.&#8221; 

It could by any of these four disks, randomly. This server is Ubuntu 24.04.1, my other four Ubuntu servers run 22.04.4.

  This is a bit strange, if only one disk failed, I could suspect the USB-port or the hard drive itself, but this isn't the case, all fails randomly. (My action to restore function is: Power off the actual drive/drives, power on and resyncing the Raid).

This did not happen with the old server and with these same four disks, nor other servers with Ubuntu 22.04.5 fails within software raid services.

  Could it be an Ubuntu problem with the version 24.04.1, just a humble question?

  Or could it more likely be a server hardware issue? 

*Facts*: Server: 2 x USB are 3.2 Gen 2 (3.1 Gen 2) - 2 x USB are 3.2 Gen 1 (3.1 Gen 1).

  *Facts *HDD: USB are 3.0. Smart status says 6Gb/s SATA throughput status. They have one partition/disk and are Linux ext4 formatted.

  I know this is tricky, but I can cook it down to a simple question: 
- Is there any (major?) changes between 24.04 and 22.04 regarding software RAID? 

I&#8217;m near now to downgrade the backup server to Ubuntu 22.04.

**Why can't I delete the post?**

---

### Post by TheFu on 2024-09-30
This isn't what you want to hear.

Using USB for any RAID needs is a terrible idea.  You've been lucky in the past.
Mark this as a "lesson learned" - Don't do RAID over USB.  Use SATA, eSATA, Infiniband, Fibre, SCSI ... AoE, iSCSI ... pretty much **any** thing else. [COLOR="#FF0000"]_**Just because something is possible, doesn't make it a good idea.**_[/COLOR]

Also, in case someone is lurking, don't do RAID with cheap flash storage.

Over time, USB connections become loose, but what's really important is that the USB storage drivers don't have the full command set that other storage connections do.

The version of Linux doesn't matter.  This isn't a Linux thing. It is a USB problem that somehow you've avoided.  

You've been lucky.  Feel free to ignore me.

I suspect you've already realized this sub-forum is for 24.10.  Probably should be moved to the Server subforum by a moderator.

---

### Post by oldfred on 2024-09-30
Moved to the server sub-forum.

Note that the report post is not just for spam. 
You can use it to request an admin or moderator to move a post or thread

---

