---
title: "Ubuntu Server 12.04: PCIe Bus Error: severity=Corrected, type=Data Link Layer"
date: 2013-12-06
forum: Server Platforms
---

### Post by downingaustin on 2013-12-06
Ubuntu forums,

I have millions of these errors in my log files, as far as I can tell constantly filling it. Whenever I write to my RAID array.

```
Dec  5 16:12:46 VeeamLongTermStorage kernel: [19451.793628] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e4(Transmitter ID)
Dec  5 16:12:46 VeeamLongTermStorage kernel: [19451.793629] pcieport 0000:00:1c.4:   device [8086:8c18] error status/mask=00001000/00002000
Dec  5 16:12:46 VeeamLongTermStorage kernel: [19451.793630] pcieport 0000:00:1c.4:    [12] Replay Timer Timeout  
```

Also at some point when running my Veeam Backups to this server my server will hard crash and the last thing in my log is repeated.

```
NULNULNULNULNULNULNULNULNULNULNULNULNULNULNULNULNULNULNULNUL
```

What is causing these issues and more importantly how can I correct them?

System specs.

OS: Ubuntu 12.04
Motherboard: SuperMicro X10SLH-F-O
Processor: Intel Core i3-4130
Boot Drive: Plextor M5P 128GB
Memory: 4 x Crucial 8GB ECC Memory [CT8G3ERSLD8160B]("http://www.neweggbusiness.com/product/product.aspx?item=9b-20-148-642")
PSU: Rosewill 450w
SATA Controllers: 3 x SY-PEX40008 PCI-E 2.0
Storage 12 x WD 2TB RED Drives in Linux RAID 6

My Linux knowledge is moderate to low so I am looking to the community and its expertise to help me with this.

Here is a pastebin of /var/log/dmesg

[http://pastebin.com/CMdhuf9R](http://pastebin.com/CMdhuf9R)

Here is a pastebin of /var/log/kern.log

[http://pastebin.com/uY3GrBiF](http://pastebin.com/uY3GrBiF)

---

### Post by tgalati4 on 2013-12-06
Looks like a hardware problem.  Could be the power supply.  450 watts may not be enough to support 12 spinners.  Take a voltmeter and measure the 12VDC rails during operation.  Any drops to 11.5VDC could be an issue.  Examine the motherboard for any obvious defects--swelled capacitors, broken inductors, etc.  Is this a new hardware build, or has this system been running a while?

Try reseating the SATA controllers.  Move them around if they are slot-based, otherwise, swap the cables around.  One bad cable could cause issues.

---

### Post by downingaustin on 2013-12-06
Basically brand new, when I had FreeNAS 8 & 9 for three months on it I had no problems at all though. 450w should be plenty for 12 spinners.

---

### Post by downingaustin on 2013-12-06
Any other ideas? I upgraded to 13.10 to see it was a compatibility issue and it appears that any time I write to the disks I get this error.

Here is a pastebin of my /var/log/dmesg

[http://pastebin.com/CMdhuf9R](http://pastebin.com/CMdhuf9R)

---

### Post by tgalati4 on 2013-12-06
You have a kernel dump (call back trace) at 0.0 seconds during boot.  I don't know if this is normal, but you should not be getting any call back traces in dmesg.  As a result, the kernel may have some missing code that is causing your errors.  The fact that it is recoverable is interesting.

Try a LiveDVD of 13.04 or 13.10 and see if the call back traces go away during boot.  If so, then try mounting the arrays and see if the write errors go away.

---

