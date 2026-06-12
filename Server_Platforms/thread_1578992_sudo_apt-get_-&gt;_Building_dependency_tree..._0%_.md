---
title: "sudo apt-get -&gt; Building dependency tree... 0% -&gt; Bus error"
date: 2010-09-21
forum: Server Platforms
---

### Post by Mrio on 2010-09-21
Hi everyone,

I've just installed Ubuntu Server 10.04.1 64 bit. And i've wanted to do an upgrade.

But i get to "Building dependency tree..." then my system hangs for 3 min and then gives a "Bus error"

I cannot even install applications (sudo apt-get install ...), because it hangs there too.

How can i fix this? Or even show the logs?

Specs:
- Amd X2 64 3000
- 4gb Ram 
- 320gb HD (Single sata, configured as raid in BIOS)

Thanx in advance!

Mario

---

### Post by Mrio on 2010-09-21
Aha found some logs:

> 
marciano@linux-server:~$ sudo tail /var/log/messages
Sep 21 14:47:08 linux-server kernel: [ 3041.358791] ata1.00: configured for UDMA/133
Sep 21 14:47:08 linux-server kernel: [ 3041.358825] ata1: EH complete
Sep 21 14:47:12 linux-server kernel: [ 3044.794119] ata1.00: configured for UDMA/133
Sep 21 14:47:12 linux-server kernel: [ 3044.794156] ata1: EH complete
Sep 21 14:47:15 linux-server kernel: [ 3047.895651] ata1.00: configured for UDMA/133
Sep 21 14:47:15 linux-server kernel: [ 3047.895677] ata1: EH complete
Sep 21 14:47:18 linux-server kernel: [ 3051.108048] ata1.00: configured for UDMA/133
Sep 21 14:47:18 linux-server kernel: [ 3051.108074] ata1: EH complete
Sep 21 14:47:21 linux-server kernel: [ 3054.125787] ata1.00: configured for UDMA/133
Sep 21 14:47:21 linux-server kernel: [ 3054.125812] ata1: EH complete
Sep 21 14:47:24 linux-server kernel: [ 3057.283037] ata1.00: configured for UDMA/133
Sep 21 14:47:24 linux-server kernel: [ 3057.283065] sd 0:0:0:0: [sda] Unhandled sense code
Sep 21 14:47:24 linux-server kernel: [ 3057.283070] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 21 14:47:24 linux-server kernel: [ 3057.283078] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Sep 21 14:47:24 linux-server kernel: [ 3057.283088] Descriptor sense data with sense descriptors (in hex):
Sep 21 14:47:24 linux-server kernel: [ 3057.283093]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
Sep 21 14:47:24 linux-server kernel: [ 3057.283111]         00 09 37 2e
Sep 21 14:47:24 linux-server kernel: [ 3057.283118] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Sep 21 14:47:24 linux-server kernel: [ 3057.283128] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 09 37 28 00 00 08 00
Sep 21 14:47:24 linux-server kernel: [ 3057.290622] ata1: EH complete


---

### Post by Mrio on 2010-09-21
I've fixed this error by reinstalling de server.

I still don't have a clue what went wrong

---

### Post by najeebca on 2011-08-18
This problem solved for me with apt-get update

---

