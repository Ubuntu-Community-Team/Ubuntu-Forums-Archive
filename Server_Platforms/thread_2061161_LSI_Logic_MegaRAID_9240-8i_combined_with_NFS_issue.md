---
title: "LSI Logic MegaRAID 9240-8i combined with NFS issues"
date: 2012-09-21
forum: Server Platforms
---

### Post by samdart on 2012-09-21
I have a peculiar problem, which I have not encountered until today.

I have a NFS, SAMBA server with 2 x independent disks and 5 x disks in RAID5 on LSI Logic MegaRAID 9240-8i PCIe card. Let us call this the NFSServer

Independent disks
1. /home
2. /opt1

RAID5 Volume
1. /opt2

I have few NFS and few SAMBA clients all on a Gigabit network including the server.

One of the NFS clients is a server (let us call is XServer) where all the users login and run several programs using XDMCP or X tunneling over SSH. On this server all three directories above are mounted using NFS.

Whenever a huge data transfer from a windows machine using samba to the RAID5 disk on the NFS Server, the load average on XServer shoots up rapidly and all XSessions freeze.

The load average spike is due to all programs waiting for /home or /opt1 or /opt2 mounts.

I have tried making huge transfers using netcat on a remote machine to NFSServer and observed the same behavior if data is being written to /opt2 and nothing happens when data is written to /home or /opt1 which are independent disks. I used iptraf to watch the BW used during the transfer in both cases it was around 8-850Mbits/sec.

The question is why does the NFSServer stop responding for /home or /opt1 mounts when data is only being written to /opt2?

The NFS server is a Xeon quad core processor running Ubuntu Server 12.04.1 64-bit and kernel version 3.2.0-23-generic

Can someone shed light on this?

Thanks in advance
Samdart

---

