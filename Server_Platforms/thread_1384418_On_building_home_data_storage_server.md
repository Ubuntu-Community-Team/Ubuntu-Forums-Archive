---
title: "On building home data storage server"
date: 2010-01-18
forum: Server Platforms
---

### Post by denarced on 2010-01-18
I need some advice or tips or maybe your own experiences about building a home data storage or NAS.
Here's some thoughts / requirements I think it should have:
[LIST=1]
[*]It should expandable. I'll stick a couple of 1TB HDDs and a little later I'll stick some more
[*]It should easily integrated to both Ubuntu and Windows 7. Ideally it'll be an integrated part of the filesystem.
[*]I'm thinking some sort of RAID as a backing up my data. RAID 1 seems like a such a waste but then again, these days, HDDs are cheap.
[*]And when I do add more HDDs, I'd like them to appear as one big storage unit instead of separate drives.
[/LIST]

Any suggestions and tips on how to go about this is welcome. Questions are plenty: should I go with server hardware or is bigger ATX case and standard hardware enough? I'll need some pointers so keep 'em coming

Thanks for any and all participation

---

### Post by scrooge_74 on 2010-01-18
LVM file system? <-linux
zfs file system? <-open solaris

for Win7 you would use samba, on linux is just an nfs mount

---

### Post by denarced on 2010-01-18
LVM sounds like what the doctor ordered.
How's about network bandwidth? Is 100mbps going to cut it or is gigabit necessary ?

---

### Post by pirateghost on 2010-01-18
> **denarced said:**
> LVM sounds like what the doctor ordered.
How's about network bandwidth? Is 100mbps going to cut it or is gigabit necessary ?
i would recommend gigabit if you have a lot of data to transfer back and forth

LVM is great.  and to clarify, RAID is NOT backup....period

---

### Post by denarced on 2010-01-18
> **pirateghost said:**
> i would recommend gigabit if you have a lot of data to transfer back and forth

LVM is great.  and to clarify, RAID is NOT backup....period

Really, RAID is not backup? Not even a little.
I thought RAID 1 is a sort of fool's backup. It doesn't help you if you accidentally delete a file. Nor if your entire machine gets fried. But if the other HDD gives up, then it acts as a backup. So not really a backup, but just a little.

---

### Post by pirateghost on 2010-01-18
> **denarced said:**
> Really, RAID is not backup? Not even a little.
I thought RAID 1 is a sort of fool's backup. It doesn't help you if you accidentally delete a file. Nor if your entire machine gets fried. But if the other HDD gives up, then it acts as a backup. So not really a backup, but just a little.

by profession i am a system administrator in charge of 110 servers worldwide + 2 SANs + entire DR site including offsite disk to disk backup.  when someone suggests that RAID is backup, its one of those pet peeves of mine....mostly due to my job.


you are correct that it will help if one drive fails, the system will keep on going without missing a beat.  but in the IT world, there is a HUGE difference in RAID and backups
RAID provides REDUNDANCY
backups provide point in time recovery of data

---

### Post by Xianath on 2010-01-19
My home storage server runs a regular desktop motherboard with on-board video, six SATA slots and three PCI Express slots (one x16 and two x1). This is enough to get 12 drives in it. I used a cheap ($40) middle tower case (16" height) which I modded to fit three 3-to-4 drive cages ($15 each) with fans, and a grill from a DIY store. Add in a 300W fanless power supply (I know 300W pushing it but it works), a cheap low power CPU (Athlon X2 4050e) and 4GB DDR2 and twelve 1TB hard drives, and I got myself a decent storage system.

Oh, and several months of research and about a month putting it together REALLY help. But on the bright side, I recently recovered from a dual-disk failure (a controller got misplaced somehow) with no issues. It's not backup, but tape storage is expensive so this is the best I could afford. All in all, I got 9.6TB of storage for less than $1000. Quite a deal.

Cheers,
Peter

---

### Post by denarced on 2010-01-21
> **Xianath said:**
> My home storage server runs a regular desktop motherboard with on-board video, six SATA slots and three PCI Express slots (one x16 and two x1). This is enough to get 12 drives in it. I used a cheap ($40) middle tower case (16" height) which I modded to fit three 3-to-4 drive cages ($15 each) with fans, and a grill from a DIY store. Add in a 300W fanless power supply (I know 300W pushing it but it works), a cheap low power CPU (Athlon X2 4050e) and 4GB DDR2 and twelve 1TB hard drives, and I got myself a decent storage system.

Oh, and several months of research and about a month putting it together REALLY help. But on the bright side, I recently recovered from a dual-disk failure (a controller got misplaced somehow) with no issues. It's not backup, but tape storage is expensive so this is the best I could afford. All in all, I got 9.6TB of storage for less than $1000. Quite a deal.

Cheers,
Peter

what kind of lan speed you got? is it enough?

---

### Post by R.Bucky on 2010-01-21
My setup: RAID1 Ubuntu Server v8.04, 1 500GB drive network storage (Samba), and a 1TB external for backup and archives. My home network is Cat6 with Gbit cards, which includes 2 Vista machines and 3 Ubuntu machines. No problems and good for everyone on the network. The RAID1 server drives double as storage in that all my music is RAID'd and accessible via a web interface within the network.

---

### Post by Xianath on 2010-01-21
100Mbps are definitely not enough to boot Windows from unless you're the patient type, but a gigabit is just fine. I got an on-board gigabit NIC and a 100Mbps PCI in a separate VLAN for Internet access. For reasons I haven't cared to deeply investigate yet (bad cable?), I am getting no more than 400Mbps from my gigabit LAN. The disk subsystem itself delivers over 200MBps, and iSCSI to localhost gives me about 150MBps, so this is definitely network related. Even so, the Windows experience score on my iSCSI targets is 5.1, higher than a WD5000AAKS attached directly to the motherboard SATA2 ports.

Cheers,
Peter

---

### Post by denarced on 2010-01-21
> **Xianath said:**
> 100Mbps are definitely not enough to boot Windows from unless you're the patient type, but a gigabit is just fine. I got an on-board gigabit NIC and a 100Mbps PCI in a separate VLAN for Internet access. For reasons I haven't cared to deeply investigate yet (bad cable?), I am getting no more than 400Mbps from my gigabit LAN. The disk subsystem itself delivers over 200MBps, and iSCSI to localhost gives me about 150MBps, so this is definitely network related. Even so, the Windows experience score on my iSCSI targets is 5.1, higher than a WD5000AAKS attached directly to the motherboard SATA2 ports.

Cheers,
Peter

Usually that kind of speed says the bottleneck is hdd

---

### Post by Xianath on 2010-01-21
Well, the array can do over 200MB/sec, and when mounted over iscsi through the loopback, it drops down to 150MB/sec due to the iscsi overhead. However when mounted from Windows 7 over iscsi through the network, speed is just 40MB/sec. It's either the NICs themselves, the NIC drivers, some NIC settings like jumbo frames and off-loading (which I tried to no avail), the Windows iSCSI implementation, or the cable. But given the above, it's not the disks.

Cheers,
Peter

---

