---
title: "Swap file second harddrive ubuntu server"
date: 2020-11-18
forum: Server Platforms
---

### Post by sharkey97 on 2020-11-18
Hi!


We are in the process of starting to set up a filcoin server with Ubuntu 18.04 server.
We are a little hesitant about what is best.
To install Ubuntu Server 18.04 on an SSD disk and Swapfile on a separate 2TB M.2 NVMe disk.
Or it does not matter purely performance-wise to have the OS and the Swap file on the same disk and then, as a suggestion, on a 2TB M.2 NVMe.
In addition, the spec looks like this.
AMD Threadripper 3960x
Asus Prime TRX40-Pro
Corsair Vengeance LPX Black DDR4 4x32 = 128GB
Seagate IronWolf Pro 2x10TB
Puts great value in tips and help.


// Michael

---

### Post by slickymaster on 2020-11-18
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2020-11-19
There was a thread here about **swap** 3-6 months ago. Seek it out. It has lots of good information.

Basically, it is a way for 1 party to **pay** another party to hold their data securely. There is a middleman, certainly taking a cut.  There have been many solutions for this over the decades, but this adds in a block chain aspect and should, in theory, provide infinite storage, for a price, though much of it will likely be slow.

Seems like typical desktop systems need not apply.  This all needs to be on redundant storage able to handle 100TB in a way that no loss of data can happen.  That means ZFS and ECC RAM.  

The 20TB listed above doesn't come close to their required 100TB minimum.
Rethink your RAM. It isn't ECC. When it comes to not screwing 1-bit up, you need ECC RAM.  The motherboard listed supports ECC, so that's fine.

IMHO, I don't use a swapfile. Use a swap partition or swap LV or whatever ZFS calls "swap" devices. Avoid the overhead of a file system for swap or other issues in using a file for a critical OS and security aspect to the system.

[https://filecoin.io/blog/filecoin-guide-to-storage-mining/](https://filecoin.io/blog/filecoin-guide-to-storage-mining/)  For people unfamiliar with filecoin, like me. That link has an overview of what filecoin is.

---

### Post by LHammonds on 2020-11-19
> **sharkey97 said:**
> 
To install Ubuntu Server 18.04 on an SSD disk and Swapfile on a separate 2TB M.2 NVMe disk.
Or it does not matter purely performance-wise to have the OS and the Swap file on the same disk and then, as a suggestion, on a 2TB M.2 NVMe.

As a server admin, I try my best to ensure my servers are NEVER touching swap.  Once it needs to swap out of RAM and into swap space...it won't matter much if it is ssd or nvme.  Best performance means running out of RAM, not swap.

**EDIT:** Starting with Ubuntu Server 18.04 and higher, I now use swap files rather than swap partitions.

LHammonds

---

