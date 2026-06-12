---
title: "My new $450 RAID5/LVM server"
date: 2008-08-17
forum: Server Platforms
---

### Post by fido777 on 2008-08-17
[SIZE="3"]Specs[/SIZE]

[AMD Athlon 64 X2 5000+ Brisbane 2.6GHz Socket AM2 65W Dual-Core Processor Model ADO5000DOBOX - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103211") $60
[A-DATA 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model ADQVE1B16K - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820211188") $75
[Seagate Barracuda 7200.10 ST3250410AS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive - OEM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148262") 3x60 = $180
[ASRock ALiveNF7G-FullHD R3.0 AM2+/AM2 NVIDIA GeForce 7050 Micro ATX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157126") $65
[Linkworld PRESCOTT 437-01-C2222 Black SECC/SGCC MicroATX Mid Tower Computer Case 430W Power Supply - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811164089") $30

Items were chosen for low cost and low/no shipping cost.  The MB had to have good Linux reviews, onboard video for potential HTPC down the line, many SATA connectors (this has 6), and be expandable to 8GB RAM.  I knew I wanted software RAID5 for performance and protection against drive failure, so I had to get at least 3 drives.  RAID5/LVM allows me to easily add new drives and get a performance boost each time I do so.  I need the memory for database stuff, but 4GB isn't much more expensive than 2GB anyway.

[SIZE="3"]Setup[/SIZE]

Ubuntu 8.04.1 x64 **Alternate** CD install.  The alternate CD allows RAID5/LVM setup, and doesn't have the LiveCD functionality which I don't need.  I wanted to have a desktop install for maximum flexibility.

For setting up the drive array, I partitioned each drive to have a 200 MB partition for /boot and set that to RAID1 (boot partitions have to be fairly vanilla).  The rest of each drive was setup for RAID5/LVM, with one LVM partition for swap and one for data (ext3).  This is Linux software RAID, not the MB RAID (which probably only works with Windoze).  Running "sudo hdparm -t /dev/md1" gives me 115 MB/sec which verifies the RAID5 performance.  I used [this page]("http://www.debian-administration.org/articles/512") and [this page]("http://users.piuha.net/martti/comp/ubuntu/en/raid.html") for reference.

[SIZE="3"]Usage[/SIZE]

I mainly want to run the server remotely from my desktop.  A lot of people talk about remote desktop, but unless you put it on a virtual workspace it will waste a lot of desktop space.  Instead, I use nfs and sshd which are both easy to set up.  I can drag and drop files in Nautilus/Dolphin, and by using 
```
ssh -X myservername
```
I have full shell access and I can launch gnome/kde apps that display on the desktop and run off the server.

I know it's not optimal (especially the case), but it was easy and cheap, and it's pretty dang fast!  Comments welcome...

---

### Post by fjgaude on 2008-08-17
Sounds good to me, and I'm sure many will benefit from your post. Thanks!

---

### Post by Ocelaris on 2008-09-13
That's great, that's exactly what I'm in the process of building... though I'm quite a long way off on figuring out how to actually do that. 

One question I have, is do you make a mdadm raid 5 array BEFORE you make a LVM volume out of it? I guess you would have to, but then how would you ADD a disk to the LVM volume.

> I mainly want to run remotely from my desktop. A lotta people talk about remote desktop, but I don't like it. Instead, I use nfs and sshd which are both easy to set up. I can drag and drop files in Nautilus/Dolphin, and by using
Code:

ssh -X myservername

I have full shell access and I can launch gnome/kde apps that display on the desktop and run off the server.

That sounds great, I have no idea how that would work, but it's hot! I was just planning on setting up some VMs and controlling them remotely. I need to get things up and running sufficiently enough so that I can be motivated to continue working on it. So Desktop/GUI were mandatory, I wouldn't have gotten anywhere without it. You know what they say about GUI-less machines, the road to hell is paved with them :)


Picked up a Biostar board with 6 SATA ports, onboard video, 4x1TB drives, and a seperate HD for the OS.  The Mobo/CPU was actually a combo deal at newegg for $100

[BIOSTAR TFORCE TA780G M2+ AM2+/AM2 AMD 780G Micro ATX AMD Motherboard - Retail]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813138105") $79.99

[AMD Athlon X2 BE-2400 Brisbane 2.3GHz Socket AM2 Dual-Core Processor Model ADH2400IAA5DO - OEM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103215") $39.99

---

### Post by trmentry on 2008-09-13
I have a home built file server at home running 8.04.1 now.  :)  This is the 3rd generation of the server.   

When I was in the process of building it for the first gen, I wanted to get a controller that did just that, controller functions.  No raid, jbod, or whatever.  But I wanted 8 ports on each card.

The problem I found, is that 8+ port cards are all raid type cards.

But then I found these. 

[http://www.supermicro.com/products/accessories/addon/AoC-SAT2-MV8.cfm](http://www.supermicro.com/products/accessories/addon/AoC-SAT2-MV8.cfm)

They are PCI-X cards (64 bit pci slots) but work fine in a normal pci slot.  I have 2 of them in my server in normal pci slots.  So this gave me 8x500 and 8x400 drives up and running in Raid5.  (2 arrays)  The cards are around 99$ last time I looked.

There is a performance hit as I'm killing the pci bus on a rebuild, but for a file server day to day it's fine and never had an issue.

```

trmentry@hoth:~$ lspci
<SNIP>
05:00.0 SCSI storage controller: Marvell Technology Group Ltd. MV88SX6081 8-port SATA II PCI-X Controller (rev 09)
05:02.0 SCSI storage controller: Marvell Technology Group Ltd. MV88SX6081 8-port SATA II PCI-X Controller (rev 09)

```

---

### Post by fjgaude on 2008-09-14
Using the PCI bus, instead of PCI-X or -E, really takes a hit on drive throughput, tops at 110 MB/sec when it could be over 400 with five or more drives in a raid5 array.

---

### Post by trmentry on 2008-09-14
> **fjgaude said:**
> Using the PCI bus, instead of PCI-X or -E, really takes a hit on drive throughput, tops at 110 MB/sec when it could be over 400 with five or more drives in a raid5 array.

Yeah... btu since it's really only streaming to the xbox and a mapping for My Documents from Windows, not much of a hit seen.  Eventually Hoth v4 will have proper card/slots, but ran out of money on Hoth v3

---

### Post by Ocelaris on 2008-09-16
More importantly than thorough put is the access time and i/o load I would think when using it as a block device, either iscsi or nfs... Am I incorrect in thinking NFS is a block device? I was just going to use Samba, but haven't given the actual file sharing much thought yet, it was more figuring out the LVM + Raid 5 which I've been able to get working, VMware server + remote http Daemon, which will let me run a domain controller etc... test boxes, while also hosting the file systems. whoo hoo... did it already with a test x64 desktop version, going to try for the server CLI version tomorrow.

---

### Post by trmentry on 2008-09-16
> **Ocelaris said:**
> More importantly than thorough put is the access time and i/o load I would think when using it as a block device, either iscsi or nfs... Am I incorrect in thinking NFS is a block device? I was just going to use Samba, but haven't given the actual file sharing much thought yet, it was more figuring out the LVM + Raid 5 which I've been able to get working, VMware server + remote http Daemon, which will let me run a domain controller etc... test boxes, while also hosting the file systems. whoo hoo... did it already with a test x64 desktop version, going to try for the server CLI version tomorrow.

I'm not sure about block device.  But on my server.. I run both Samba and NFS.   Samba for the windows clients to attach to... and NFS for the linux ones.  

I'm running ESXi Server currently.  I highly recommend it over vmware server if you have a dedicated machine you can use for it. (It's an OS in of itself).   It has a much stronger gui mgmt client although it's windows only.  

I did type up a how-to to get esxi talking via iscsi to my server to have more space for the vm's.

---

### Post by Ocelaris on 2008-09-16
The only reason I'm using VMware server not ESXi is that I want a file server and some other things on the same box...

I see VMware pulling people away from standard linux and into their proprietary system and I worry... it's great the way it works now, hope it stays almost open-source like it is now. Good easy interface. The VMware console isn't too bad, just like VMware infrastructure client as far as I can tell for a first look.

---

### Post by volkswagner on 2008-09-17
Why not go a little greener.  Can one of these CPU,s meet your needs?  I don't see a spec for the L1 cache.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103255](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103255)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103256](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103256)

These should save you around $14/yr, plus produce less heat.

---

### Post by Ocelaris on 2008-09-17
I have a kill-a-watt meter hooked up to my Desktops... The entire Desktop takes about 130-150watts with 4 1TB barracuda 7200.11 drives, and a single SAS 15k drive for /

This Chip is also 45watts, and a bit cheaper, probably could overclock it if you want stably, but with so much Processing power these days why bother?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103215](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103215)

(this is the one I got with the Biostart 780g motherboard for 100$ after "combo" discount from newegg.) supports compiz well.

---

