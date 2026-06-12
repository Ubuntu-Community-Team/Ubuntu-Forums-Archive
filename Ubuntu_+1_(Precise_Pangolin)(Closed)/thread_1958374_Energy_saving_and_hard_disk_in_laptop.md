---
title: "Energy saving and hard disk in laptop"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by palimmo on 2012-04-14
I noticed a behavior "different" from what happened in previous versions. 

When my laptop is in battery mode, I can notice a continuous "plug/unplug" or something similar coming from the hard disk. 
In previous Ubuntu versions there was an option to manage in some way the hd energy supply. I do not remember very well. 

But now I cannot find anything like that. 
Do you have any idea?

---

### Post by palimmo on 2012-04-15
No experiences?

---

### Post by Yellow Pasque on 2012-04-15
What kind of laptop is it? Do you know what kind of disk it is? (sudo lshw -C disk)

---

### Post by palimmo on 2012-04-15
> **Temüjin said:**
> What kind of laptop is it? Do you know what kind of disk it is? (sudo lshw -C disk)

Packard Bell Easynote TJ65
```
*-disk                  
       description: ATA Disk
       product: WDC WD3200BEVT-2
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 11.0
       serial: WD-WX70E99ED623
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=95ec95ec

```
thanks!

---

### Post by Yellow Pasque on 2012-04-15
It may be the infamous "intellipark" feature of WD drives. IF you want to disable disk power management and see if clicking stops, see: [http://forum.notebookreview.com/linux-compatibility-software/513675-ubuntu-running-acpi-ahci-mode.html#post6661220](http://forum.notebookreview.com/linux-compatibility-software/513675-ubuntu-running-acpi-ahci-mode.html#post6661220)

---

### Post by palimmo on 2012-04-16
> **Temüjin said:**
> It may be the infamous "intellipark" feature of WD drives. IF you want to disable disk power management and see if clicking stops, see: [http://forum.notebookreview.com/linux-compatibility-software/513675-ubuntu-running-acpi-ahci-mode.html#post6661220](http://forum.notebookreview.com/linux-compatibility-software/513675-ubuntu-running-acpi-ahci-mode.html#post6661220)

Can I sleep peacefully with this edit?
I've read also here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/795760](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/795760)

---

### Post by Yellow Pasque on 2012-04-16
> **palimmo said:**
> Can I sleep peacefully with this edit?
The worst it can do is shorten battery life a bit. On the plus side, it can save your drive from premature failure since Linux and Intellipark don't play nice together.

---

### Post by palimmo on 2012-04-17
Battery mode:
```
alessio@alessio-ubuntu:~$ sudo hdparm -I /dev/sda | grep "Advanced power management level"
	Advanced power management level: 127
```
Adapter mode:
```
alessio@alessio-ubuntu:~$ sudo hdparm -I /dev/sda | grep "Advanced power management level"
	Advanced power management level: 254
```

---

### Post by Yellow Pasque on 2012-04-17
Okay, so do you hear the clicks when using AC adapter?

---

### Post by pqwoerituytrueiwoq on 2012-04-17
I think this is what the OP is referring to
[IMG]http://i.imgur.com/bw7Ci.png[/IMG]
sorry if this post is a bit late to be relevant

---

### Post by palimmo on 2012-04-18
> **Temüjin said:**
> Okay, so do you hear the clicks when using AC adapter?

no... only when i am on battery

---

### Post by palimmo on 2012-04-18
> **pqwoerituytrueiwoq said:**
> I think this is what the OP is referring to
[IMG]http://i.imgur.com/bw7Ci.png[/IMG]
sorry if this post is a bit late to be relevant
it doesn't exist in 12.04. Doesn't it?

---

