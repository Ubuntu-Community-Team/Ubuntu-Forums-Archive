---
title: "Home Nas with Raid1"
date: 2010-12-27
forum: Server Platforms
---

### Post by alliance1975 on 2010-12-27
A recent post by another member requested information about building a home NAS with RAID 1 

--------------------------------------------------------------------------------

My plan is to build a NAS which will run 2x500GB drives in RAID 1config. The purpose is to store media which can be accessed by both Ubuntu and Windows computers on my home network and to provide print server services.

His basic question was where to install the OS since he did not provide a third drive for Ubuntu Server.

My situation will provide a Compact flash card for the OS. I've read a lot of guides regarding server install and all advise setting up the raid drives with similar partitioning for boot, swap and /. Is this for configurations that will boot from the raid drives themselves? If my config will boot from the CF card then do I need the the elaborate partitioning suggested on the guides. I would prefer to just have the raid drives equipped with single NTFS partitions.

Can someone clear up my confusion regarding the need for the multiple partitions if the OS will be separate from the raid drives.

---

### Post by Lonewolf321 on 2010-12-27
> **alliance1975 said:**
> A recent post by another member requested information about building a home NAS with RAID 1 

--------------------------------------------------------------------------------

My plan is to build a NAS which will run 2x500GB drives in RAID 1config. The purpose is to store media which can be accessed by both Ubuntu and Windows computers on my home network and to provide print server services.


His basic question was where to install the OS since he did not provide a third drive for Ubuntu Server.

My situation will provide a Compact flash card for the OS. I've read a lot of guides regarding server install and all advise setting up the raid drives with similar partitioning for boot, swap and /. Is this for configurations that will boot from the raid drives themselves? If my config will boot from the CF card then do I need the the elaborate partitioning suggested on the guides. I would prefer to just have the raid drives equipped with single NTFS partitions.

Can someone clear up my confusion regarding the need for the multiple partitions if the OS will be separate from the raid drives.

I run a FreeNAS file server on my home network. It servers files to both Windows and Linux machines.

It is an older version of FreeNAS which installs on the HD but, the latest version can be run from cdrom with configs written to a flash drive. They have several different versions that can run from embedded devices and from flashdrives.  The version i run has a plugin that allows it to operate as a print server.  Haven't tried since the printer is to far from unit.  If you want to take a look at it FreeNAS their site can be found at [http://www.freenas.org](http://www.freenas.org).

Hope this helps.

---

