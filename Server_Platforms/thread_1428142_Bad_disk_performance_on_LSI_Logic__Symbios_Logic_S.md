---
title: "Bad disk performance on LSI Logic / Symbios Logic SAS1064ET"
date: 2010-03-12
forum: Server Platforms
---

### Post by maxxer on 2010-03-12
Hi.

I just installed 8.04 server on an IBM machine equiped with the LSI Logic / Symbios Logic SAS1064ET PCI-E raid controller. 

Everything worked fine, but I noticed right when making filesystem that disk access seemed very low.

Now that the server is installed, it has an enormous IOWait for a base system with no service installed. 
```
# hdparm -tT /dev/sda1

/dev/sda1:
 Timing cached reads:     2 MB in  5.95 seconds = 344.19 kB/sec
 Timing buffered disk reads:    2 MB in  7.04 seconds = 290.99 kB/sec

```
(I performed the test while running a drbd sync, but the performance is deadly poor anyway...)

Anyone else had experiences with this controller? 
I tried googling, but no much information about it.

tanks

---

### Post by leofiska on 2010-04-25
I'm facing the exact same problem in a dedicated server from fujitsu.

01:00.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1064ET PCI-Express Fusion-MPT SAS (rev 04)

I'm getting about 12.5 MB/s where it should be as least 50.0 MB/s. It's impossible to use the system while allocating, even ssh login locks down.

---

