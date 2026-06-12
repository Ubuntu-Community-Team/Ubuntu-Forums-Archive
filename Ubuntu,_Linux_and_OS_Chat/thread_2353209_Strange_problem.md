---
title: "Strange problem"
date: 2017-02-19
forum: Ubuntu, Linux and OS Chat
---

### Post by cariboo on 2017-02-19
I have a file server where I store all of my recorded video and ripped dvd files. About a month ago I was getting errors when watching videos stored on one of the drives. I checked the logs, and saw lots of errors that led me to believe the drive was going bad, so I pulled it out, and set it aside until I had time to look at it.

Today I put the drive in another computer to see if I could recover anything from it, and when checking the drive, I found nothing wrong with it. All the files were there, and from what I can tell they all are OK.

I put it back in the server, and it started throwing errors during boot up, I changed SATA cables, and moved power cables around, but still no joy. I then put the drive in a third system, and it works as it should.

Server Details:

```
System:    Host: willy Kernel: 4.4.0-62-generic x86_64 (64 bit) Console: tty 0
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: MICRO-STAR model: G31TM-P21 (MS-7529) v: 1.0
           Bios: American Megatrends v: V4.4 date: 11/25/2009
CPU:       Dual core Pentium E5400 (-MCP-) speed/max: 1203/2700 MHz
Graphics:  Card: Intel 82G33/G31 Express Integrated Graphics Controller
           Display Server: N/A driver: N/A
           tty size: 80x24 Advanced Data: N/A out of X
Network:   Card: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169
Drives:    HDD Total Size: 3960.8GB (68.2% used)
Info:      Processes: 219 Uptime: 1:46 Memory: 727.0/1990.7MB
           Init: systemd runlevel: 5 Client: Shell (bash) inxi: 2.2.35
```

I got the case and power supply from a former employer about 10 years ago, and the motherboard, cpu and ram in 2009, the hard drives I've added over the years they consist of:

[LIST]
[*]1 X 160Gb
[*]2 X 400 Gb
[*]2 X 500Gb
[*]2 x 1Tb
[/LIST]

The drive in question is a Seagate 1Tb.

I'm starting to think it may be the power supply in the server, as I have no idea how old it is. 

Does anyone have any suggestions? I plan on upgrading the drives a little later this year, I'm wondering if I should replace the power supply too.

**Edit:** I should add that the motherboard has 4 SATA ports, and I purchased an add in adaptor with another 4 SATA ports.

---

### Post by QIII on 2017-02-19
Is the drive connected to one of the native motherboard SATA headers, or the add-on one?

---

### Post by cariboo on 2017-02-19
> **QIII said:**
> Is the drive connected to one of the native motherboard SATA headers, or the add-on one?

It was originally, and I initially hooked it the same way when I first tried it today. I tried a different port on the add in adaptor and a different power plug, I then swapped SATA cables with one that is connected to a port on the motherboard.

The one thing I never did was document which drive is connected to which SATA port, although they are mounted via UUID in /etc/fstab.

---

### Post by QIII on 2017-02-19
Interesting.  Probably not the SATA connection, then.

Since you tried different power connectors, I wouldn't think a PSU problem would be limited to odd behavior in just one device.

That would go back to the device itself, then.  But it works on other machines.  Inode table, maybe?  MemTest?

Maybe you need a shaman?  :)

---

### Post by CharlesA on 2017-02-19
What error were you seeing in the logs? I've seen similar things in the past but I think they were due to the drive itself - I had one 2TB Hitatchi drive throw all sorts of errors in one machine and be completely fine in another, even tho the same cables were used and the PSU was solid. Quite strange tbh.

FWIW, I have had problems in the past with certain drives after restoring them with clonezilla.. they wouldn't be bootable in one machine, but work completely fine in another. I blame gremlins for that!

---

### Post by cariboo on 2017-02-20
Here is a bit of the errors I was getting in /var/log/kern.log:

```
Feb 19 16:13:34 willy kernel: [   11.645501] ata7.00: BMDMA2 stat 0x80d2209
Feb 19 16:13:34 willy kernel: [   11.646894] ata7: SError: { Handshk UnrecFIS }
Feb 19 16:13:34 willy kernel: [   11.648282] ata7.00: failed command: READ DMA
Feb 19 16:13:34 willy kernel: [   11.649657] ata7.00: cmd c8/00:00:00:0a:00/00:00:00:00:00/e0 tag 0 dma 131072 in
Feb 19 16:13:34 willy kernel: [   11.652429] ata7.00: status: { DRDY ERR }
Feb 19 16:13:34 willy kernel: [   11.653822] ata7.00: error: { ABRT }
Feb 19 16:13:34 willy kernel: [   16.676140] ata7.00: qc timeout (cmd 0xa1)
Feb 19 16:13:34 willy kernel: [   16.677554] ata7.00: failed to IDENTIFY (I/O error, err_mask=0x5)
Feb 19 16:13:34 willy kernel: [   16.678933] ata7.00: revalidation failed (errno=-5)
Feb 19 16:13:34 willy kernel: [   16.680321] ata7: hard resetting link
Feb 19 16:13:34 willy kernel: [   17.000034] ata7: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Feb 19 16:13:34 willy kernel: [   17.032049] ata7.00: both IDENTIFYs aborted, assuming NODEV

```

The drive has an XFS file system, generally I've found XFS to be quite reliable.

**Edit:** For completeness the drive is a Seagate Barracuda ST1000DM003-1CH1

---

### Post by CharlesA on 2017-02-20
Have you checked the SMART data for that drive?

```
sudo apt-get install smartmontools
```

```
sudo smartctl -a -H /dev/sdX | less
```

I've seen this error before and a quick google tells me that it usually means the disk is on it's way out.

---

### Post by uNoubu8a on 2017-02-20
Up until a few years ago I had not had one hdd fail on me yet... now I have two dead Seagate Barracuda drives :/

---

### Post by cariboo on 2017-02-20
I've had problems with Seagate drives over the years, I had a 750GiB drive that was replaced under warranty 4 times, the 5th time they sent me a 1Tib drive, I'm not sure if it was this one, or the other Seagate 1Tib drive that I have. Regardless I got both of them as replacements.

I checked S.M.A.R.T, and from what I can see, and what I've read there may be a chance that the drive is failing, but nothing seems to be conclusive. Here are the S.M.A.R.T. results.

[[img]https://s7.postimg.org/jfg9y0d5z/Screenshot_from_2017_02_20_12_13_40.png[/img]](https://postimg.org/image/jfg9y0d5z/)

---

### Post by CharlesA on 2017-02-20
Hrmm, that looks OK.

I would probably still RMA the drive after you get your data off it, if it is still under warranty.

---

### Post by speedwell68 on 2017-02-22
> **work-work said:**
> Up until a few years ago I had not had one hdd fail on me yet... now I have two dead Seagate Barracuda drives :/

I have had one drive fail since 1990 and that was in a machine that was given to me after it had been dropped from a great height.

---

### Post by ventrical on 2017-02-24
> **cariboo said:**
> 
I'm starting to think it may be the power supply in the server, as I have no idea how old it is. 



Ohm's Law my friend. Tally all the Watts being used and check the output of the PSU. Subtract 20% from the original output. An aging drive will require more watts to startup <and it may explain the TIMEOUT>. An aging power supply will produce less watts over time. There is this huge resistor that eventually fatigues over time.

So if the drive in question is pulling 75Watts increase it to  85 watts. If the PSU is rated for 400Watts rate it for 325 watts etc..


Regards..

---

### Post by cariboo on 2017-02-25
> **ventrical said:**
> Ohm's Law my friend. Tally all the Watts being used and check the output of the PSU. Subtract 20% from the original output. An aging drive will require more watts to startup <and it may explain the TIMEOUT>. An aging power supply will produce less watts over time. There is this huge resistor that eventually fatigues over time.

So if the drive in question is pulling 75Watts increase it to  85 watts. If the PSU is rated for 400Watts rate it for 325 watts etc..


Regards..

That was my thought too, but using a wattage usage calculator, my systems needs about 220 watts. I haven't looked at the power supply, but judging by it's age it is more than likely a 250 watt power supply.

To my way of thinking, if the power supply isn't putting out enough wattage to run all the components in the system, problems will show up in any of the components, not just one hard drive.

Right now the hard drive is running happily in my desktop system. I've copied files to and from the drive while monitoring the logs and so far it hasn't been throwing up any errors.

---

### Post by ventrical on 2017-02-25
> **cariboo said:**
> That was my thought too, but using a wattage usage calculator, my systems needs about 220 watts. I haven't looked at the power supply, but judging by it's age it is more than likely a 250 watt power supply.

To my way of thinking, if the power supply isn't putting out enough wattage to run all the components in the system, problems will show up in any of the components, not just one hard drive.

Right now the hard drive is running happily in my desktop system. I've copied files to and from the drive while monitoring the logs and so far it hasn't been throwing up any errors.

if the hdd in question and the CPU  + data pumps both call for power simutaneously (parallel) then there will be a BUS fault. This due to a big voltage drop.  Some of the older PSUs (+400watts) are very durable but the actual lead  from the large power resistor will most always cause a 'cold-solder' joint and when power is  needed it will fail anywhere along the chain . Newer (cheap) power supplies are notorious for this. 3 years maybe and then ffffttt .. kaput.  :)

Regards..

---

