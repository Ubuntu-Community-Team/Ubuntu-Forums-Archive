---
title: "Ubuntu Server 10.04 LTS NAS?"
date: 2010-11-08
forum: Server Platforms
---

### Post by ehcah on 2010-11-08
Hello,

I'm wondering if anyone can help me understand what I would need to do in order to get an Ubuntu Server install to behave as other NAS products like Nexenta, FreeNas or OpenFiler etc...?  I have 2 Ubuntu servers running DHCP, DNS and internet sharing now.  I'm about to assemble a 24 bay, 4U Chassis and not sure what to install. I know that I will not continue with unRAID, which is what I currently run for NAS.

I'd really like to stick to Ubuntu - if it makes sense.  To begin with, I'll be adding 12 x 2TB drives.  I'll most likely shoot for RAID 6 and roughly 20TB usable.  With 12 additional bays, I need to be able to grow my array easily without risk of losing and/or rebuilding everything. My files are all movies, music, pictures etc... No database's or anything with heavy writing requirements.

Where I get a bit confused is how the other packages I mentioned, differ or have advantages then building a file server? As far as I know, Raid is Raid? ZFS seems to be something that other solutions offer, but I read that Ubuntu is working on BTRFS to compete.

What am I losing or gaining with Ubuntu Server vs. some of the other solutions available?  Are these other packages just scaled back linux OS focusing solely on storage?

Thank you,
Jason

---

### Post by Coder68 on 2010-12-17
I am only just learning Ubuntu Server/RAID myself, but I am using Ubuntu 10.04 LTS 64 bit as a NAS. (And a few other things.) 

I installed webmin and used that to build my RAID 5 (5 x 2TB) I then mounted this volume to /mnt/media1  I think my next step is to add Samba so my one Windows PC can see and use it. 

I am using Samsungs hd204UI 2TB drives. If you use these, or one of their other green drives, you will need to update the firmware (patch in my case) to not lose data when SMART is used! - FYI See smartmon tools site for more info. 

Hope this gives you somewhere to start looking.

Coder68

---

### Post by NX3 on 2010-12-30
Can you advise how to format the HD204UI in Ubuntu ? I've got 10.04 and 10.10 but both fail to install at 33% when it trying to partition the drive. I'm using the default partition app from the install CD.

---

