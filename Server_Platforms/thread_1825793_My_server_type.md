---
title: "My server type?"
date: 2011-08-15
forum: Server Platforms
---

### Post by slotdoctor on 2011-08-15
Hello everyone.

For the last 2 o 4 weeks I have been researching, File Server, Server, Partitions, RAID's and other mutuations. Please, pardon my stupidity. But, I am more confused now than when I started. 

The goal for the server is to be use to access: data files, music, video and pictures from my computer and laptop running Ubuntu and the Wife's. That runs windows 7 on the desktop and windows XP on the laptop.  I do not need access from another location. We already have a wireless router connected to the cable service for Internet. I am thinking of using Ubuntu Server Edition 10.04 ( already order a DVD) and the equipment I have on hand is as follows:

1. Generic Micro ATX box.
2. Power Supply = Corsair 450watts 
3. Motherboard = ASUS P7H55-M Pro.
4. Processor = Intel I3-540 (3.06).
5. Memory = Corsair XMS# 8Gb (4 X 2Gbs).
6. Hard Drive 1 = WD 5000AVVS 500Gb – (OS Ubuntu and programs).
7. HD 2 = WD BAAY5000ENC-NRSN 500Gb - (for Data files).
8. HD 3 = WD BAAY5000ENC-NRSN 500Gb - (for Media “music/videos/pictures” files).
9. HD 4 = WD BACX0010BBL-NESN 1Tb USB - (for Back-up).

Could you give me some ideas how to improve my Server, or what additional equipment I may needed? Also any suggestions for the installation would be much appreciated. 

Thank you.

---

### Post by PierreRobiquet on 2011-08-15
You're using way too much for the server, from the sounds of it you will just be running a simple Samba server which will operate with a slow processor and a small amount of RAM. I assume the build is designed to be energy efficient you can buy an AMD Athlon LE CPU for example this one:

[http://www.ebuyer.com/222595-amd-athlon-le-1640-2-7ghz-socket-am2-512kb-cache-oem-processor-adh1640iaa4dp](http://www.ebuyer.com/222595-amd-athlon-le-1640-2-7ghz-socket-am2-512kb-cache-oem-processor-adh1640iaa4dp)

Even that would be overpowered for your solution though but it is in the "energy efficient" line. I'll give you an example about resource usage, I'm running an Ubuntu Server with Murmur, SSH, OpenVPN, (occasional Minecraft server) and Samba on an Intel Atom N270 with 2GB of RAM  the server only uses about 70mb on boot (Minecraft sends RAM usage up to about 500mb) and everything is buttery smooth.  

If anything I would say you should set the motherboard, RAM and CPU aside for an extra desktop computer or maybe media centre for your living room? 

If you're going to do a complete new build for a server I would recommend a large case, slightly beefy PSU (to handle all of the hard drives) along with an energy efficient CPU. Ideally you would want to get a motherboard with on-board RAID or a dedicated RAID card to set up RAID 5 across the drives, I know it may seem slightly paranoid but I'm sure your wife will be angry if a hard drive crashes and the baby/vacation pictures go missing :P

Of course you can go ahead and use your current components, but I still think they would be better used in a full desktop machine. You could buy a fairly cheap barebones Atom system which will be nice and compact as well as energy efficient  however won't provide nearly as much space or RAID support. I wouldn't really recommend a software RAID, firstly due to the extra load they place on the system (it's not a lot but I prefer a dedicated card/chip) and in Linux software a RAID is hard to configure and easy to mess up.

I hope this has helped.

---

### Post by YesWeCan on 2011-08-15
Hi there.
I'd agree with most of what concrete donkey said except that I am a big fan of linux RAID and I think it works really well and a RAID 1 for your data would be very easy to set up using Disk Utility, for example.
A dedicated hardware RAID card is faster but expensive and, IMO, overkill for your requirement.
The RAID that comes with a mobo is not proper RAID. Some law ought to stop them advertising it as if it were real hardware RAID. What it is, as you may already know, is some hardware support for Windows software RAID. Linux software RAID does not require any mobo RAID hardware and is generally considered superior.
You may not want a RAID, tho, if you are backing up anyhow.

Your OS installation is likely to consume a whopping 5GB, 10GB if you really load it up with apps. So can the 500GB disk be better employed? The OS may be installed on the same disk (or array) as your data partition.

---

### Post by slotdoctor on 2011-08-16
> **YesWeCan said:**
>  You may not want a RAID, tho, if you are backing up anyhow.

Thank you for the response. May main concern was to separate the Music files from the data files and the OS in case of a crash. 

I want to install Ubuntu server, I have not used Windows for about 2o 3 years now. What do you mean by I may not want a RAID? I was under the impression it was a necessity? 

May I should forget about it and just build a desktop. But, I really wanted a file server. O well.

Thanks guys. Appreciated.

---

### Post by Wim Sturkenboom on 2011-08-16
Splitting stuff over different HDs is not such a brilliant idea in this scenario. Your music/videos etc will be full in no time and your data might still be nearly empty.

I would start simple with a 1TB drive. A 20GB partition for the OS, some swap and the rest for data/music etc. When the disk is full, add a new one and move e.g. your music etc over.

Further an internal HD is not really a backup. In case of theft or fire, your backup will be gone.

Rather get yourself an external HD. Make a backup once a week (or how often you think that is necessary) and store off site (work, bank, ...). Better would be two externals, but that might be overkill. Cycle your backups (odd weeks on odd numbered disk, even weeks on even numbered disk), store one off site and keep one on site.

---

### Post by Wim Sturkenboom on 2011-08-16
> **slotdoctor said:**
> Thank you for the response. May main concern was to separate the Music files from the data files and the OS in case of a crash.

That is what you have your backup for ;)

> **slotdoctor said:**
> I want to install Ubuntu server, I have not used Windows for about 2o 3 years now. What do you mean by I may not want a RAID? I was under the impression it was a necessity? 
Raid is not a necessity for a home server. It adds redundancy and in a professional environment it is (usually) a necessity. But in that case they also have dual power supplies and spare disks laying around as well as a secondary system with an exact copy of the primary one.

---

### Post by YesWeCan on 2011-08-16
RAIDs are used for different purposes like:

1) Mirrors/distributed parity RAID1/5/6 to keep the server operating without interruption if a disk fails. Obviously important for a public web server.
A sort of backup in the sense of data being duplicated or redundancy added but not a backup in the sense of protection against accidental file deletion or recovery of old files that you want back.
RAID1 mirrors are the most reliable. RAIDs 5 & 6 use complex error correction schemes to make more efficient use of space that are, especially for RAID5, vulnerable to pernicious failure modes and complicated recoveries. RAIDs 5 & 6 are striping with error correction.

2) Striping RAID0 to concatenate disks and improve performance. RAID0 is not a RAID at all but just AID. There is no redundancy at all. The mdadm driver won't let you expand a RAID0 after you've created it.

3) Linear concatenation to make multiple disks appear to be one big disk. This isn't strictly RAID either but the linux RAID driver, mdadm, will do this. So will Logical Volume Management (LVM).

There may be others.

So it depends what you need. You should have some backup system regardless. It can be useful to have a concatenation scheme so you don't have to worry about physical disk boundaries - you just add a disk and expand the partition. Of course, if you lose a disk out of a concatenation then I think all the disks become unreadable, not sure about LVM but certainly for RAID0. But if you have a backup you may not care about that.

I think in your case, I'd consider concatenating my disks with LVM so I don't have to worry about boundaries and can have whatever partitions I like, and can easily add another disk (of any size) if I need to expand. And back it all up regularly, of course. If you want continuity of service even if a disk fails, concatenate RAID1 sets. RAID5 is an efficient way to concatenate and improve read speed (because it stripes), the only limitation I think is that its disks need to be the same size - so may be less flexible than LVM - I'm not certain of this.

---

### Post by a2j on 2011-08-16
> **Wim Sturkenboom said:**
> 

Raid is not a necessity for a home server. 

when one of my drives died on a home server, I was thinking just the opposite...

---

### Post by PierreRobiquet on 2011-08-16
How fast is your upload bandwidth? Rather than a RAID I suppose you could use an online backup service which supports rsync, if you're not too worried about your movies and music that would be even better and you could just keep your pictures backed up with the remote servers. You'll only need a hosting provider that gives you enough storage space for what you plan to backup and then you're protected against fire, flooding and hard drives crashes.

---

### Post by slotdoctor on 2011-08-30
Hello again everyone.

OK so I did build the server and installed Ubuntu Server Version 10.04lts. I have Open ssh running fine now. I can see the Server with the laptop, running Ubuntu also. But the Desktop running Windows 7 is another story. So after much research and reading several tutorials. I have a couple questions.

Could I run Samba and Open Ssh on the same server?  Would they share the same directory?

Like I said before, I have been going over some configurations samples and below is what I understand I am supposed to do. Could anyone give me some suggestions? Does it look bad? How could I improve my set-up?

Many thanks for your help.

Using Samba software to make an Ubuntu machine into a file server that can, share files with Windows machines, Macs, and other Linux systems. 

1. From the terminal install Samba:

Code:  sudo apt-get install samba


2. To create a Samba name and password:

Code:  sudo useradd -c mario 

Code:  sudo smbpasswd -a mario

Code:  sudo smbpasswd -e mario


3. Create directory, and set permissions and ownership:

Code:  # mkdir /home/mario/data

Code:  # chmod u+rwx,g+rx,o+rx /home/mario/data

Code:  # chown mario.users /home/mario/data

(DO NOT use sudo to create the folder).


4. Make a backup copy of the original smb.conf file:

Code:  sudo cp /etc/samba/smb.conf  /etc/samba/smb.conf.bak


5. Use a text editor to edit smb.conf:

Code:  sudo nano /etc/samba/smb.conf


6. Restart Samba:

Code:  sudo restart smbd


To create a Share edit /etc/samba/smb.conf, the configuration file. Samba shares are named in brackets, [ ], and are configured by adding options in the lines that follow. Most options are boolean (yes / no).  There should be no spaces between the lines, and there should be a single space before and after each of the equal signs.

7. To give permission to read, write and share to the DATA folder:

(add to the bottom of the conf file).

	[DATA]
    		comment = Ubuntu File Server Share
    		path = /home/mario/data
   		browsable = yes
    		guest ok = no
    		read only = no
    		create mask = 0755
    		directory mask = 0755


8. Check smb.conf for any syntax errors

Code:  sudo testparm


9. To free hard drive space and update your system

Code:  sudo apt-get update 

Code:  sudo apt-get clean 

NOTES:

a) To make sure the directory /var/spool/samba is owned by the (root) user and group: 

Code:  root# chown root.root /var/spool/samba 

b) Directory permissions should be set for public read-write: 

Code:  root# chmod a+twrx /var/spool/samba

c) Parameters that have to be verified:

		[global]
			workgroup =  network_name
			netbios name = sevrver_name
			printcap name = cups
			
		[printers]
			comment = All Printers
			path = /var/spool/samba
			printable = Yes
			use client driver = Yes


Again Thank you.

---

