---
title: "Using “Sata Controller” to add extra ports with mdadm software raid to create a raid"
date: 2013-12-12
forum: Server Platforms
---

### Post by Kurisu87 on 2013-12-12
[COLOR=#333333][FONT=UbuntuRegular]Here is the set up.... Ubuntu 1204 LTS, Plex. samba ect as a media server. I am looking on setting up a raid 5 using 4 2tb disks to create 6tb of space with a fail safe.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My motherboard is from 2008 which from looking through the bios , I do not believe it has raid capability in built. I was wondering what my options are...

Could i buy a 4 port sata III extension PCI card and then use mdadm to create a software raid 5 array... or is not not doable and need to get a raid card as my motherboard does not have raid in the bios
thanks guys![/FONT][/COLOR]

---

### Post by mcapaldo on 2013-12-12
Most motherboards have 6 sata ports.  I have an older board with a AMD 6000+ CPU and it has six.  I am using all six sata ports with ubuntu mdadm RAID 5 using all wd green 2tb drives.   Booting off ubuntu 12.04 server on an 8gb USB Flash Drive.  I just added a 4 port pci sata card and a 2tb drive to it and am in process of converting RAID5 to RAID6.  Only issues I can see is running out of room in case for drives/airflow, adequate power supply.  

I used the CORE Server install directly to USB Flash Drive, setup SAMBA and MDADM during server install. 

You may want to start out with RAID6 that way if 2 drives fail at once you can still rebuild, RAID5 only allows 1 failure at a time and still rebuild.  

I will warn you, adding a drive and re-syncing and growing takes almost 24 hours with my setup.

---

### Post by Kurisu87 on 2013-12-12
Thanks fir your reply, my bored has 4 sata 2 ports, if it had size it would have been perfect. Currently it hold 2 drives, 1 x 250gb which holds the OS and the downloads folder for deluge and a 1.5tb which just media. The plan is to add 4 more 4 x 2tb however, I was hoping to keep the 2 other disks already contained (keep the os on the 250gb and the 1.5tb as something els).

Though, I got to say the idea of the OS on a flash drive is intriguing... what was your reasoning for doing that?

And time is no issue, and 1 drive failure is fine for me, currently, I can not afford 1 to fail so having one as redundancy would be quite a weight off lol

---

### Post by Kurisu87 on 2013-12-12
Anybody else have any further information in using a simple sata controller (not raid) to use to extend drive capacity for use in a raid 5 setup using mdadm?

---

### Post by CharlesA on 2013-12-12
> **Kurisu87 said:**
> Anybody else have any further information in using a simple sata controller (not raid) to use to extend drive capacity for use in a raid 5 setup using mdadm?

If you are going to be running software RAID, you would need an adapter that acts as a normal HBA, so it passes the drives directly to the OS instead of showing them as a hardware RAID volume.

If you are going to be using more than 3 disks, I would recommend running RAID6 instead of RAID5.

---

### Post by mcapaldo on 2013-12-12
My reasoning for using the flash drives so I would free up all six Sata2 ports.  

And I added a 4 port PCI sata2 card and put the drive in, and added it to the array.  I had a SMART failure on 2nd 2tb drive so I replaced that and then am in the middle of going to RAID6.  

Others will probably tell you RAID5 mdadm is not a backup.  You should have a dvd burner or tape backup or some other secondary set of backups.  

I have an old 4tb 16 drive bay array with 2 8 port raid cards (3ware) with raid setup on the raid card (no mdadm) so having multiple raid cards is not a problem.  

I have a 24 bay rack mountable SATA array should I need it (it has three 8 port super micro raid cards).  with mdadm I can move all the drives over to it and plug in the usb flash drive and boot off that and no problems.  a 8GB Flash drive is pretty easy to clone and have a backup.

---

### Post by Kurisu87 on 2013-12-13
> If you are going to be running software RAID, you would need an adapter that acts as a normal HBA, so it passes the drives directly to the OS instead of showing them as a hardware RAID volume.

If you are going to be using more than 3 disks, I would recommend running RAID6 instead of RAID5.

So a standard PCI sata III extension hub to add 4 more ports will work? I am also currently researching raid 6... seem like a much stable option

---

### Post by CharlesA on 2013-12-13
> **Kurisu87 said:**
> So a standard PCI sata III extension hub to add 4 more ports will work? I am also currently researching raid 6... seem like a much stable option

It should. I would suggest a PCI-express card instead of a PCI, though because it will be faster.

---

### Post by Kurisu87 on 2013-12-13
> **CharlesA said:**
> It should. I would suggest a PCI-express card instead of a PCI, though because it will be faster.

supurb! Thank you very much for your help, I will grab myself a sata III PCI express card and set up raid six! Again, thank you :)

---

### Post by CharlesA on 2013-12-13
Welcome. Good luck!

---

