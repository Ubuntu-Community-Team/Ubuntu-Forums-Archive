---
title: "Mysterious hard drive activity grinds system to a halt at regular intervals"
date: 2009-11-25
forum: Server Platforms
---

### Post by clove on 2009-11-25
I have an Ubuntu media server set up that hosts music, videos, and movies on a raid 5 array that is shared via nfs to various computers and media client machines in my house.  The server also runs the Deluge daemon and Deluge webui for bittorrent activity.

The problem is that every 5-15 minutes, the hard drive light will light up solid for 2-3 minutes straight and any videos or music playing on connected machines will stutter or stop while the server goes through this unexplained process.

Here's what I have done so far:

run 'iotop' to monitor hd activity: funny thing is it shows nothing when the hd light is solid other than a few quick nfs blips

run 'iozone' to test read/write speed: the "random write" speed drops to a pathetic 440Kbps for benchmarking files over 1GB--speed is good for small files

run 'top' to monitor running processes: nothing unusual during solid hard drive light

I've shut down the two Deluge processes (so there is no bittorrent activity) on the server and shut down all client machines so the server is isolated and idle.  The hard drive light still comes on solid at the usual intervals.

I then decided there must be some raid problem, so I completely reformatted and rebuilt my raid 5 array which made up of three 1.5TB sata drives using mdadm raid5 and formatted with ext3.  I changed the chunk size to 128K and tuned up some other settings based on articles I've read.  This didn't help.

I upgraded Ubuntu server from Jaunty to Karmic.  Didn't help.

Switched the sata setting in the bios to AHCI.  Didn't help.

My setup:
Ubuntu Server 64 bit Karmic, headless
1 320GB sata boot drive
3 1.5TB sata drives (WD Caviar Green SATA Intellipower) in raid 5 array controlled by mdadm
64bit AMD dual core chip
4GB memory
A newer mobo, the brand of which I can't recall without unbolting the server out of the rack
Gigabit ethernet network

I really don't know where to go next with the diagnosis other than to start replacing pieces of hardware one by one.  My server is supposed to be an "upgrade" of my previous setup which was a bunch of 500GB drives in a mdadm raid5 array on the gui version of Ubuntu Hardy--this older setup ran just fine and didn't have this problem.

Any ideas what I can do next to troubleshoot?  I don't know where to go next other than start pulling my hair out.

---

### Post by clove on 2009-11-27
After days of googling I've come to one conclusion:

software RAID5 + Ubuntu = bad idea

I've ordered a 4th 1.5TB drive and my plan is to scrap the RAID5 setup and build a RAID10 across the four drives.  Hopefully I'll see an end to all this random disk activity along with a dramatic increase in write speed.

---

### Post by beniwtv on 2009-11-27
Well, here we're using RAID5 on a Ubuntu server (8.04.3) just fine. Make sure it's not something stupid like the HDD's trying to go to sleep or something...

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd1[0] sda1[4] sdc1[3] sdb1[2] sde1[1]
      5860543744 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]
      
unused devices: <none>

```

---

### Post by laluz on 2009-11-27
> **clove said:**
> After days of googling I've come to one conclusion:

software RAID5 + Ubuntu = bad idea

I've ordered a 4th 1.5TB drive and my plan is to scrap the RAID5 setup and build a RAID10 across the four drives.  Hopefully I'll see an end to all this random disk activity along with a dramatic increase in write speed.

I have a RAID6 with mdadm and no problem like that. Ubuntu 8.10.

---

### Post by clove on 2009-12-04
Checked all the power settings and I don't think the drives are trying to sleep.

I've switched to RAID 10 with ext4 file system and replaced the CPU with AMD's fastest quad-core.  Everything is incredibly fast...UNTIL the hard drive lights up solid which still lasts for several minutes, at which point everything slows to a crawl.

The hdd light is solid about 20% of the time now, even when the server should be idle.  I watch Iotop and mostly see some occasional /usr/bin/del activity, but just brief instances of this.

My next step was going to be to try Hardy server, but I realized that Hardy cannot read ext4 and I don't really want to go through the 3 day process of reformatting and moving TBs of data back just to experiment with Hardy.

I may replace the motherboard next--I don't know what else I can possibly replace.  I was thinking also maybe I should see what happens with Fedora or Red Hat on a fresh boot drive.  This problem is driving me insane.

---

### Post by clove on 2009-12-06
I took out the SATA boot drive and replaced it with an IDE boot drive with a fresh install of Karmic server and VOILA!!..everything runs beautifully now!

Is there a reason having a SATA boot drive alongside a RAID array of SATA drives could cause a conflict on the SATA bus or something? My previous SATA boot drive showed no health problems and had a vanilla install of Ubuntu server, so I have to believe there was some sort of SATA conflict going on. Switching to IDE boot drive fixed it.

I'll tag this solved even though I don't understand why.

---

