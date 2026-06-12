---
title: "SAMBA is slow on newer machine. Fine on old."
date: 2011-02-26
forum: Server Platforms
---

### Post by kaioshin on 2011-02-26
The issue:
It takes 45min to transfer 10MB from my laptop to my replacement server.
It takes 1minute to transfer the same 10MB from my laptop to the old server.

All connections are equal. Both servers are plugged to the same router.

Details:
I have decided to migrate away from my Proliant 1600 to a slightly newer less complex piece of hardware.

Both  machines are LAMP installs. Both are setup to be maintained headless  99% of the time and gnome is launched from the command line only when it  is needed. 

The older machine has more things running on it than  the replacement. The replacement has nothing running that the older  machine does not have.

Old box runs Ubuntu 6.06 but was fully updated a month ago.
Replacement box runs Ubuntu 10.10 and was fully updated just last night.

smb.conf  was the same on both boxes other than the share locations. Reading  trying to fix it myself, I did put some known speedup lines into the new  box's smb.conf, but it did not make a noticeable difference.


Hardware:
Old box,
Proliant 1600 = 1998 small server tech. (weighs 50lbs w/o drives)
single 500mhz xeon (upgradable to 2 600mhz, though they are hard to find reasonably priced)
1GB SDRAM with ECC
then it gets complex....
3 19GB 15k 80pin SCSI in RAID0+1 for the OS and /var/www
1 19GB spare for above raid
2 72GB 15k 80pin SCSI in RAID1 for temp storage of downloads and photos
IDE card
2 120GB and 1 500GB IDE drives for main storage. Just recently realized they all defaulted to PIO mode...
Uses the onboard NIC and video

Because  that box was confused by the addition of the IDE card it will not boot  from ANY of the hard drives. The card nor the BIOS gives an option to  kick off to the other. To remedy this, I had to make a grub floppy for  it to boot from that then kicks over to the OS RAID. If that floppy  fails, it will boot from CD still. But being a 13yr old floppy and CDROM  makes them both untrustworthy and encourages migration as well.

The newer computer,
900MHz Athlon
1.5GB SDRAM
1 120GB IDE HDD as the OS and temp drive
SATA (FakeRAID) card (no onboard sata)
2 1TB 7200RPM SATA drives in RAID1 for storage
Nvidia Geforce 2 64mb video (no onboard video)
Generic 10/100 nic card (no onboard nic)

It does not matter what share/drive/partition I transfer to on either machine. The result is always the same.

On the newer computer CPU usage rarely goes over 50% and it has not had to go into swap at all yet.

---

### Post by kaioshin on 2011-02-26
Bit more info,

Loaded up gnome on both machines and did transfers to/from each.

New machine finds and transfers at a decent speed to/from any other share on my network.
Old machine finds and transfers at a decent speed to/from any other share on my network except the new machine. It does transfer faster with the new machine than my Vista laptop, but still takes 5+ minutes to move a 10MB file either way.

I am really confused...
I had the old box up for ~7years and have never had this kind of problem with it. Only problem I do have (besides the boot issue I worked around) is that I have never been able to get a mouse to work with it. Serial or PS2. The mouse did work in win2000 when I first got it.

---

### Post by kaioshin on 2011-02-27
So, I was so frustrated by this that I did an 

apt-get purge samba 

then rebooted.

I reinstalled and at the end of the installation it 'failed to start'

I found that smd.conf was not in /etc/samba so I copied an example one in there. Samba started. But I can not get anything to actually access the server in any way. Reboots and restarts of the process has made no difference.

---

### Post by doas777 on 2011-02-27
install ethtool via whatever method you prefer (softwarecenter/apt-get/...) and post back the output of (replacing 'eth0' with your device name if it is different.)
```
sudo ethtool eth0
```

---

### Post by kaioshin on 2011-02-27
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes

I can get into the webserver no problem, just not SAMBA

---

### Post by doas777 on 2011-02-27
> **kaioshin said:**
> Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 32
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Current message level: 0x00000007 (7)
    Link detected: yes

I can get into the webserver no problem, just not SAMBA
well everything looks fine there. as for the webserver, its a very differant type of traffic than a "large" file transfer. 

is the transfer from the server to the laptop equally slow (initiated from the laptop)?

---

### Post by kaioshin on 2011-02-27
When SAMBA was working,

Transfers to/from the new server initiated by the laptop were slow.
Transfers to/from the old server initated by the laptop worked as normal

Transfers to/from the old server initated by the new server were normal
transfers to/from the new server initiated by the old server were slow, but faster than from the laptop.

FTP worked as expected.
Moving files locally on the server was not at all slow either.
I figured that eliminated any hardware issues.

Now I am confused as to why SAMBA did not work at all when it reinstalled and still does not work correctly.

---

### Post by kaioshin on 2011-02-27
I've given up.

I recently received a machine that needs a new PSU but is better than my current desktop in every way. Unfortunately I do not have a spare PSU with the 20+4 connector it needs. I'll just buy a PSU and rebuild it to replace my desktop and restart my migration to a new box with my current desktop as its base.

My current/old server is stable but is nearly out of space, has little/no room left for expansion, does not mirror/backup the most important data, and sucks up a lot of power.

---

