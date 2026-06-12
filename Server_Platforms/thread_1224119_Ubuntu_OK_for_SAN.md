---
title: "Ubuntu OK for SAN?"
date: 2009-07-27
forum: Server Platforms
---

### Post by Vegan on 2009-07-27
Can Ubunbtu currently provide everything I need to build a SAN storage appliance?

I use SAMBA now but I have only used simple shares so far.

I have seen comments of NFS but I have not seen any reason to swerve from SAMBA so far.

I was considering iSCSI as a possible software stack. I was looking at using it over a fast LAN.

---

### Post by jhannah on 2009-07-27
I have used NFS on my Ubuntu server for sometime now without any real complaints. The setup painless and there are sane packages for everything. If you are looking for a guide, I would check out [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo).

As for iSCSI, though I haven't really used it in any sort of semi-production environment, all of the packages are there. My only real concern would be if you have a HBA that isn't well supported by Linux (although I'm not really aware of any except for counterfeit knock-offs) if you are using an HBA at all. Depending what kind of throughput you need, you could probably get away with a pair of 1 gig NICs with TCP offloading engines.

Nevertheless, I think you will be much happier with NFS or iSCSI than Samba.

---

### Post by koenn on 2009-07-27
> **Vegan said:**
> Can Ubunbtu currently provide everything I need to build a SAN storage appliance?

I use SAMBA now but I have only used simple shares so far.

I have seen comments of NFS but I have not seen any reason to swerve from SAMBA so far.

I was considering iSCSI as a possible software stack. I was looking at using it over a fast LAN.

it depends on your needs. Samba is great for serving to windows cliets, but for serving linux hosts NFS seems more appropriate. NFS is also an excellent choice to provide storage to eg Vmware's ESX - there are tests that indicate it is more efficient than eg iSCSI in such a scenario. 

technically, what you"re talking about would be called NAS, not SAN

---

### Post by Vegan on 2009-07-28
Yes I use NAS now, but I was looking at iSCSI to provide more storage to 1U type machines with quad processor boards.

SAN is used mostly by enterprise class users. NAS is less costly and useful for many tasks too.

I have noticed most gear uses fiber channel. Some though support Ethernet 1G/10G too.

Been looking at HBA now to see what can be leveraged cheaply.

---

### Post by PilotJLR on 2009-07-28
But what do you need to serve to these machines? These are completely different technologies we're talking about.

Samba / CIFS / SMB is a NAS protocol that easily allows for file level concurrent read/write from a bunch of different machines.

iSCSI and FC are block level. UNLESS you are using a cluster file system, then presenting an iSCSI LUN to more than one host will cause data corruption really quickly. For example, if I present an ext3 or NTFS iSCSI or FC LUN to 2 hosts, then that data is gone in just a few seconds.

So if you need concurrent read/write from multiple hosts on the same LUN, and you do not want to implement a cluster filesystem, then NFS or Samba is it.

HBA's are not needed with iSCSI. You'd need some crazy spindles behind your target for that to be a realistic necessity.

---

