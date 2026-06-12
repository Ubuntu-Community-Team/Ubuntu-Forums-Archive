---
title: "Ubuntu Server 16.04 - Mounted NFS Drive Stalls When Writing To It"
date: 2017-03-22
forum: Server Platforms
---

### Post by realmuhko on 2017-03-22
Hello uBuntu Forum!

 
I am looking for assistance and hope someone will be able to assist me with some good advises on this one...
 
My issue is disk speed related and I simply can't figure it out.
 
I am running a host with: VMWARE ESXi PC with Intel i7-3770s CPU and 16GB RAM. Storage is a single mSATA 240Gb (3gb/s)

 
To the host I have connected a NFS (3TB) - this NFS is placed on my Synology NAS running 2x WDC 3TB RED in RAID1 Configuration.

 

Both my Vmware ESXi Host and Synology NAS are each connected with a single 1GBps uplink to a Cisco Switch.

 
----------
 
I  have added a VM on my VMWare ESXi running uBuntu 16.04 Server - this has 14Gb  RAM allocated and a "Hard disk 1" of 60GB located on the mSATA drive  mounted in the host machine.

 

I have also added a "Hard disk 2" of 300GB this one is placed on the NFS on the Synology NAS.

 
----------
 
My  issue is when uploading files via FTP/SFTP to the VM and to the mounted 300GB  Drive which is located on the NFS of the Synolog NAS - the file  transfers are lagging.

 

Fx.  When i upload a 2GB File, it will work great for the first 10% of the  transfer, than stall and stay stalled for maybe 1-2 seconds before  resuming the transfer again and after around 10% more it will stall  again. This will continue throughout the whole file transfer.

 
I  only seem to get this "error" when I write to the disk located on the  NFS Share of the Synology NAS - When I read from the same drive I get speeds  around 70mb/s and no stalls.

 
When  I transfer to the 60Gb drive located on the internal mSATA drive, I am  getting speeds around 100mb/s and no stalling which is perfect!
 
So it seems like the problem is related to the NFS mounted on the NAS and the disks placed on that NFS.

 
My ubuntu drives are EXT3 and mounted in uBuntu without any SWAP.

Everything else is standard/unchanged.

 

Does  anyone have an idea of how to avoid these stalls in the file-transfer  to the drive placed on the NFS when writing to data to it ?
 
Thank you guys!
 
Best Regards From
 
Martin B.

---

