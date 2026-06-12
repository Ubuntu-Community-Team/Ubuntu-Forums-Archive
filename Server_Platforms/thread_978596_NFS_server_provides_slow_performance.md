---
title: "NFS server provides slow performance"
date: 2008-11-11
forum: Server Platforms
---

### Post by zeevikn on 2008-11-11
Hi.

I have a Ubuntu 8.04 server, with NFS, SAMBA and FTP servers.
Storage is 4 * 500GB sata disks, in RAID-5 configuration.

Download and upload using FTP or SAMBA works great.
NFS server provides poor performance.

this is how the share is configured
/NAS    10.55.0.0/255.255.0.0(rw,no_root_squash,insecure,sync,no_subtree_check)

How can I speed up the NFS performance ?
What other configuration files should I look into ?

Any help will be highly appreciated.
Thanks,
Zeevik

---

### Post by oneloveamaru on 2008-11-11
If your network is 10.55.0.0 then your exports file looks right. With what you have, you are opening that NFS share to everyone on that network as root.

Are there any firewalls between your server and the client?

Also, how are you measuring performance?

---

### Post by zeevikn on 2008-11-11
Indeed, 10.55 is the network being used.
No FW between the clients and the server, just a GbE switch.

the clients are VMware ESX hosts, using this NFS server as storage for the Virtual machines.

the way I measured the performance is copying data from the NFS server to the ESX hosts local disk, using FTP, SAMBA and NFS.
NFS resutled with about 5MB/s
FTP and Samba resulted with much higher rates (upto +50MB/s)
Testing networking performance (iperf) from the client to the server results with 500Mb/s (=+50MB/s)

(I also tested scp from the NFS server to itself, resulting with +50MBs. for my understanding, it means that the Raid is not the problem)

Is there another way to measure that ? are there any other debug tools ?
any more information (conf files, etc) that would help you to help me with solving the problem ?

Thanks a lot,
Zeevik.

---

