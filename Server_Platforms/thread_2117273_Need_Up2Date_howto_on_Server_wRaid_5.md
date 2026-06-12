---
title: "Need Up2Date howto on Server w/Raid 5"
date: 2013-02-18
forum: Server Platforms
---

### Post by grunge09 on 2013-02-18
I have been looking around the forums and search engines and have been finding pieces of good info some in date and some out of date.  I was wondering if there was a modern up to date howto for what I want.

My need:

File Server 4 x 2tb WD green drives in Raid 5 (So 4tb with a hot spare)
Samba file sharing for users, and storage for Mythtv box data.  I would use Webmin, samba and SSH to admin the box remotely.  

PC is: AMD 6000+ CPU, 2 Gb RAM, one 8 or 16 gb usb drive (boot/run Ubuntu Server 12.10), 4 WD green 2tb - Raid 5 drive setup, dvdrom, on a gigabit network.

I would like to know if:

A. Is it possible to boot this all off a 8/16 gb flash drive?  Then have all the data on the Raid 5?

B. Do I need to Raid 5 the swap space?  Or Raid 0/1 Swap space?  I will be using Mdadm.

C. Can I use Webmin to setup the Raid 5 in its GUI?  Will I have to manually update Fstab or does that do it automatically.

D. What File System do I use for file system > 4gb.  I do plan on periodically growing array by 2tb drives when I can afford them.  

I have a separate Ubuntu 10.10 Desktop pc with 2 TV Tuner Cards with 2TB of data that I need to copy over to the Raid 5 then move that 2tb drive as a hot spare on the raid 5.  That PC is a AMD 965 CPU with 4GB RAM and 4 tuners (HVR-2250 and PVR-500).  

My question there is if I have all data on new file server,  (I can use Samba CIFS to map shares via Fstab on mythtv box)

E. how slow would be it to have the data saved to another pc over the network on the fly.  Is that even doable?  Meaning use mythtv box to record data but save it directly over the network to the new proposed file server.  not locally any more on the mythtv box.  

F. Will that slow my network down and my accessing the internet?

G. Would I need a separate network for mythtv and file server to avoid bottlenecking of data?  or would 2 extra NIC Cards and a crossover cable to both PCs work?  Since they will be right next to  each other.  

I would still want to access the files from other PC's in the house.  

Now I DO have a 24 bay rack mount Super micro Raid Array Box just sitting around, but that thing is freaking LOUD.  I would rather use my full tower AMD 6000+ PC and have a few decent case fans to keep the noise down.

---

### Post by spynappels on 2013-02-18
Wow, big question. I'll answer the few easy one first and come back for the rest when I have time later.

A) Yes, this will run well on a USB thumbdrive, with a few small tweaks. You should probably create a small (~10GB) /var/log directory on your data (RAID) drive, this will mean that the USB thumbdrive will not get constant writes to it as stuff is logged and will increase the lifespan of the thumbdrive. You could do the same for other directories which may see frequent write access, depends on what else you will want to do with the server.

B) I would RAID1 the swap space across all the drives, just to make the layout the same on all drives.

C) RAID like this is better set up at install time, the installer does make this very easy to do though. I've not used the Webmin interface though.

E) You can do it it everything is on a Gigabit network, but you might bget better results using NFS rather than CIFS for this.

I'll try and come back later for some more...;-)

---

### Post by darkod on 2013-02-18
On top of everything said, I would reconsider (not) using webmin. I remember reading somewhere that it's not in the ubuntu repositories for a reason. It does the config files in slightly different way.

I especially wouldn't trust it for setting up the raid.

If you are comfortable administering the server over ssh, forget webmin. If you want webmin for the gui, go with it, but if it really makes issues down the road, you don't want to find that out with your server full of data. And that's a big IF, I'm not claiming it will happen for sure, I am not sure myself...

---

### Post by grunge09 on 2013-02-18
Ok I installed all 3 2tb drives on the MB controller, put in the 16gb flas drive on the back, and a ubuntu 12.10 server x64 install cd and I get all the way to "Found Serial ATA RAID Disks do you wish to activate them?  If I say yes or no I can not get to the manual partitioner.  

I noticed that one of the drives has an older firmware, the MB see's it in bios, 

I found that if I install Win Xp on a drive I can see and format all 3 drives NTFS and copy directories to all of them.

Ubuntu Desktop 12.04 only see's 2 drives.  Not the new drive with the older firmware.  

Now I did have 2x2tb drives RAID 1 Ubuntu Server 11.04 running OK, so I used GPARTED Live CD to delete all those partitions before I started the whole process so far.  Did I screw up?

I would appreciate any advice.  thanks in advance.  

Should I install Server 12.10 on the 16 GB USB w/o the SATA drives connected, then from MDADM from cmd line to install raid5?

I would that I should not run a swap on USB to save drive life.  And modify Fstab for NOATIME.

Right so far?

---

### Post by darkod on 2013-02-18
If a disk has fakeraid meta data, it will be ignored by the installer thinking it's part of fakeraid.

First boot the machine with a desktop live cd, open terminal and get rid of any left over meta data (lets assume the three big disks are sda, sdb and sdc):
```
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb
sudo dmraid -Er /dev/sdc
```

After that start the install again and see if this time it shows all three disks + the usb stick where you want to install.

If the third disk is not seen in Gparted/parted also, not just in the installer, then you might have a hardware issue. The meta data makes it not show only in the installer, usually parted can see it correctly.

---

### Post by grunge09 on 2013-02-18
Did that and got....

ubuntu@ubuntu:~$ sudo dmraid -Er /dev/sda
no raid disks and with names: "/dev/sda"
ubuntu@ubuntu:~$ sudo dmraid -Er /dev/sdb
no raid disks and with names: "/dev/sdb"
ubuntu@ubuntu:~$ sudo dmraid -Er /dev/sdc
Do you really want to erase "ddf1" ondisk metadata on /dev/sdc ? [y/n] :y
ERROR: ddf1: seeking device "/dev/sdc" to 1024204253954048
ERROR: writing metadata to /dev/sdc, offset 2000398933504 sectors, size 0 bytes returned 0
ERROR: erasing ondisk metadata on /dev/sdc

---

### Post by darkod on 2013-02-18
Sorry, too late in my time zone, can't spend much time on this now. Maybe someone else will jump in too.

I sort of remember there is some issue removing this ddf meta data, try googling about it too, and it might turn out something. The standard meta data would have been removed, but this is some different kind I think.

In any case, you found your problem, now you only need the solution. :)

---

### Post by grunge09 on 2013-02-19
After some searching I found the answer to removing the DDF1 meta Data.

I had to boot off a Ubuntu 11 Lice Desktop CD, and run Partition Editor.  I deleted all partitions on all drives, then created a new ext4 primary partition on /dev/sda, and copied that onto /dev/sdc (the affected drive).  Took 12 hours on my green 2TB Drive.  But after that I was able to boot a Ubuntu 12.10 server cd install and see and use all 3 sata drives in RAID5 and boot off the USB.

Now the problem is I picked a super slow USB stick.  So I will have to find another one that is faster and try again.

---

### Post by grunge09 on 2013-02-19
I tried DD to drive 2 drive copy and it ran out of room.  So I put the 8gb flash drive on the back of the server, and re-ran the server install.  I used F4 to run minimal install.

Got the RAID part up and deleeted /dev/md0 and cleaered all drive partitions.  

Re-created the RAID5 with 3 drives and no spares.  Then I created partition on 8gb usb driove with no swao file and the install finished.  I had it install Samba only.

Booot on the flash drive the 1st time took 1 min 30 seconds.  I checked CAT /PROC/MDSTAT and array is re-syncing.  

I modified /etc/fstab to add noatime and added tmpfs for prolonging the flash drives life.  

Will have to wait 6 hours for the array to sync.  Then I can create a partition and start making shares and adding smb users.

---

### Post by SaturnusDJ on 2013-02-20
About the swap:
A few years ago I read it's best to not apply a form of RAID underneath the swap. "Leave it to the kernel" they said.

Just saying.

> **spynappels said:**
> 
A) Yes, this will run well on a USB thumbdrive, with a few small tweaks. You should probably create a small (~10GB) /var/log directory on your data (RAID) drive, this will mean that the USB thumbdrive will not get constant writes to it as stuff is logged and will increase the lifespan of the thumbdrive. You could do the same for other directories which may see frequent write access, depends on what else you will want to do with the server.

A energy savings drawback of this is that the hard disks in the array probably never will spin down.
In my new setup (which I hope to launch before next week) I consider this:
8GB SSD partitions (all noatime):
1. 64MB GPT
2. 200MB /boot
3. 4GB /
4. ~4GB swap

xTB Raid5 array partitions:
1. /home2

With only user data on the /home2 (shared via samba) I can't think of a reason why it won't spin down at night. :)

---

### Post by grunge09 on 2013-02-26
I got the array shnced (6 hours later).  Had sseveral problems with Samba so I turned to webmin and in like 5 minutes I had the shares setup, users added and it was working.

I ran CP SMB.ORIG SMB.CONF

stopped and restarted smb service

removed directories on new raid5 share.  

Used Webmin to create shares and added smb users and it just works that simply without even reading any documentation. 

2 days of pulling hair out to 5 minutes of webmin bliss.  

And I changed the port on webmin and the ip's that could access it over the network.

---

