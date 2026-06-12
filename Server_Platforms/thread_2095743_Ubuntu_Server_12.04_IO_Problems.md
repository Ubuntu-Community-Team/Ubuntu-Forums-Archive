---
title: "Ubuntu Server 12.04 IO Problems"
date: 2012-12-17
forum: Server Platforms
---

### Post by Cueball61 on 2012-12-17
We run the following specs:
2x SATAII 2tb HDDs
2x 40gb SSD (RAID1)
Xeon CPU (can't remember model off the top of my head)
24GB DDR3 RAM

The issue? The file IO on our machine is horrendous, I've tried changing the IO Scheduler and that didn't help. Essentially, I can be editing a vim file and when I :wq it spends 10-20 seconds sitting there saving a few kb of data.

Another, more prominent example: Our Minecraft server runs a permissions system that saves its data from a HashMap or similar to a YML file. This can take up to 5 seconds to save. Nobody else has this issue, and at maximum the file takes up about 300 lines tops right now. We also see constant stack traces of FileIO related errors when our main thread hangs (which it's doing a lot).

Can anyone give any suggestions? This happens on both the SSDs and the HDDs, I've done SMART tests on the HDDs and they've been fine, checked the CPU, RAM, etc via tests and all is clean. I'm at a loss right now really.

Oh, ext4 is the filesystem by the way. iostat doesn't provide much but jdb2 is writing quite a lot.

---

### Post by tgalati4 on 2012-12-17
Are any of these "green" drives?  If so, they then to despin quickly and go to sleep.  So you get unlogged IOWaits as the disks spin up.

I had an old server that was up for several years.  It started to get sluggish, but no errors.  I opened the machine to clean it out and found that the power connector to the drive had vibrated its way out.  Just barely touching.  Well, when you power down a drive, the kernel will just wait for IO from that drive without generating any syslog messages!  When power came back, the data was served and still no error messages.  I put tape on the connectors and tie straps to keep them from backing out.  Not an everyday problem.

I would check your power supply.  With all of that RAM, it's possible that the drives can't spin up properly.

---

### Post by Cueball61 on 2012-12-18
Not that I'm aware of, I have a Green drive in my desktop currently and I know how much of a pain they can be, especially as a system drive.

The four drives are:
Seagate ST32000641AS
Hitachi HDS72302
2x Intel SSDSA2CT04

---

### Post by tgalati4 on 2012-12-18
What are the BIOS settings for SATA?  Perhaps you are running IDE or compatibility mode that is causing slow disk access.  Also mixing spinners with SSD's might be becausing your IO bridge on the motherboard some heartache.  That or the fact that you have them in a RAID configuration.  Hardware (via BIOS) or software RAID?  What is the make and model of the motherboard?

Troubleshooting a system like this requires a teardown.  Start with one disk (a spinner) and say 2GB or RAM, or whatever a matched RAM pair is.  Run it for a few days then slowly add components back into the system.  I like phoronix for testing:

```
sudo apt-get install phoronix-test-suite
man phoronix-test-suite
phoronix-test-suite interactive

```

Also check your 12 Volt DC on your machine when fully populated, either through BIOS or with a voltmeter.

One test is worth a thousand expert opinions.

---

### Post by Cueball61 on 2012-12-18
This isn't really viable for me to do, as it's not a machine I can physically access.

Software raid by the way.

Motherboard is a supermicro X8STi v2.0. Here's the full output from Phoronix:


Hardware:
Processor: Intel Xeon W3520 @ 2.67GHz (8 Cores), Motherboard: Supermicro X8STi v2.0, Chipset: Intel 5520/5500/X58 + ICH10R, Memory: 24576MB, Disk: 2 x 40GB INTEL SSDSA2CT04 + 2000GB Seagate ST32000641AS + 2000GB Hitachi HDS72302, Graphics: Matrox MGA G200eW WPCM450, Network: Intel 82574L Gigabit Connection

---

### Post by tgalati4 on 2012-12-18
Send an email to Supermicro about your performance problems.  A simple BIOS update might cure your problem.

With that hardware, IO performance should be screaming.

---

### Post by Cueball61 on 2012-12-20
I dropped them an email, there are apparently no known performance issues with my board on older BIOS versions, and my BIOS appears to be up to date.

Well, back to the drawing board.

As another note, the SSDs have three RAID1 arrays: swap (stopped using that though, so need to remove it), root and a data array (mainly used for our MySQL DBs). Wondering if software RAID is causing the issue here...

---

