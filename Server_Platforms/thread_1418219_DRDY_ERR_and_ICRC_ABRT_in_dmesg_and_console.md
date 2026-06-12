---
title: "DRDY ERR and ICRC ABRT in dmesg and console"
date: 2010-02-28
forum: Server Platforms
---

### Post by tubezninja on 2010-02-28
I have a system running Ubuntu Karmic 64-bit server edition:

- [Shuttle SG31G2]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856101037") with Intel Core2Quad Q6600 processor

- 4GB DDR2 800 (PC2 6400) SDRAM
- 1 Samsung Spinpoint 750GB hard drive
- 1 Seagate Barracuda ST31500341AS 1.5TB drive

And it's been running fine for over a year now, until just a couple days ago when the following started repeatedly showing up both on the console and on dmesg output:

```
[35876.766809] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[35876.767629] ata3.00: BMDMA stat 0x66
[35876.768440] ata3.00: cmd 35/00:00:47:8c:ea/00:04:49:00:00/e0 tag 0 dma 524288 out
[35876.768442]          res 51/84:9c:ab:8e:ea/84:01:49:00:00/e0 Emask 0x30 (host bus error)
[35876.770223] ata3.00: status: { DRDY ERR }
[35876.771132] ata3.00: error: { ICRC ABRT }
[35876.772099] ata3: soft resetting link
[35877.060320] ata3.00: configured for UDMA/133
[35877.127629] ata3.01: configured for UDMA/133
[35877.127652] ata3: EH complete

```


I've had issues with a bad batch of Seagate Barracudas on other systems in the past relating to a finicky version of firmware on the drives, so I immediately assumed that the Barracuda was about to fail.  Ended up spending a few hours getting a fresh full backup of the data on that drive, powered down the system, remove the "bad" drive and popped in one of the several "known good" replacement drives we have on hand, then copied all of the data back.  Then RMA'd the old drive.

This morning, I find that this system is throwing the same messages AGAIN!

So now, I'm not sure if this is *another* bad Seagate, if this is actually the other Samsung drive that's causing the issue (which would be surprising since those have been rather reliable), or there's something else I'm missing here.

Rather than tearing this system down and replacing parts till the messages stop, is there a better way to trace the problem and find its cause?

---

### Post by tubezninja on 2010-03-01
FYI: looking further into this, the problems appeared to have started with the latest kernel release in ubuntu (2.6.31-19-server).  I rebooted and used the previous version (2.6.31-17-server) and the error messages have disappeared.

I'll continue to monitor, and if the messages still don't appear, I'll be submitting a bug report.

---

