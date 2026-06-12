---
title: "Software RAID Performance Questions/Testing"
date: 2009-02-26
forum: Server Platforms
---

### Post by himuraken on 2009-02-26
Hello all, I just put together a Ubuntu based file server and I am having some serious performance issues with Linux software RAID. Be patient with me, I have always used hardware RAID up until this project XD. The long and short of it is that the systems read and write speed is terrible even though it is running on relatively decent hardware. Here are the specs and setup:

Dell Optiplex GX280
Ubuntu Server 8.10
CPU: Pentium 4 HT @2.6GHz
Mem: 1GB DDR
Onboard Sata port 1: WD 80GB /dev/sda1 mounted as /

Software RAID5 /dev/md0 mounted on /home
Onboard Sata port 2: WD 250GB /dev/sdb1
PCI addon Sata port 1: WD 250GB /dev/sdc1
PCI addon Sata port 2: WD 250GB /dev/sdd1

This system only has samba and openssh-server installed and configured in addition to the default load.

To put this in perspective my Dell Latitude D630 with a 5400 sata drive gets twice the score/number when I run hdparm with the -tT switches.

To further add to the situation, the system WAS running Windows just fine before it was reloaded with Ubuntu, so I believe that it isnt a general system problem.

Thanks in advance,
Himuraken

---

### Post by fjgaude on 2009-02-26
Show us the -tT hdparm results on the raid5 array, please.

---

### Post by netztier on 2009-02-27
> **himuraken said:**
> 
Onboard Sata port 1: WD 80GB /dev/sda1 mounted as /

Software RAID5 /dev/md0 mounted on /home
Onboard Sata port 2: WD 250GB /dev/sdb1
PCI addon Sata port 1: WD 250GB /dev/sdc1
PCI addon Sata port 2: WD 250GB /dev/sdd1


There's one problem: the way your RAID-5 Disks are connected is not symmetrical. The two disks connected to the PCI card might be racing for bandwidth on the PCI bus. Onboard-SATA ports are often connected directly to the system bus or PCI-Express (and therefore faster) and are not behind a PCI bridge that connects your PCI slots to the system bus.

Test all drives individually with **sudo hdparm -tT /dev/sdX** and compare the results against the result from **sudo hdparm -tT /dev/md0**.

Also look at the output of **lspci** to see how the SATA chips are connected to the PCI buses of your system.

Then I'd suggest this for the sake of testing: connect your boot drive to the PCI adapter and build a RAID-1 array with two disks connected to the onboard SATA ports.

To check throughput performance, ditch samba and use **iPerf** instead. Search the forums a bit, I recently posted several times how to use it and how to have it read data from a file (i.e. from your array) instead of memory.

regards

Marc

---

### Post by himuraken on 2009-02-27
Thanks for the tips guys, ran a few updates and restarted the box. Prior to checking on this thread I decided to rerun the hdparm tests and the scores are much better. 

I was thinking the same thing about the onboard vs the expansion card. All four drives are hitting somewhere around 50+MB/s. Running the the hdparm on /dev/md0 yielded consistent 105+ scores which seem to be pretty decent to me.

Now that I know that the array is running well, I decided to transfer a couple (10GB) of files to the NAS from a Windows box. The performance seemed sort of lack luster. Would iPerf be the tool to test this with?

---

