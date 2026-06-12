---
title: "Ubuntu Server 8 grinding to a halt every 3 days"
date: 2008-08-27
forum: Server Platforms
---

### Post by baliktad on 2008-08-27
I have recently set up Ubuntu Server 8.04.1 as a virtual machine on Virtual Server 2005.  This requires the -generic kernel instead of the i686 kernel, but otherwise, the platform is identical to a physical machine.

The machine is primarily used to run Asterisk for a handful of VoIP clients.  Other than that, it runs tftpd-hpa for phone configuration files and Exim4 for emailing voicemail.  I also use [JungleDisk]("http://jungledisk.com/index.aspx") to back up configuration/logs/etc. nightly.

The box runs perfectly up to 4 days at a time.  Usually shortly after 3 days of uptime, 1 or 2 phone extensions will not be able to register.  At this point, I will be able to log on to the machine, connect to Asterisk, and see the SIP registration messages come in and the responses go back out.  Most will be "200 OK" but some will be "503 Server Error."  At this point, I know something is wrong and have a small window of opportunity to diagnose the machine.

My problem is I don't know what to look for.  Within half an hour, the box will become completely non-responsive and I am forced to reboot.  Please advise what I should look for, what logs to retrieve, or even what I can do to prepare for the inevitable.

---

### Post by windependence on 2008-08-28
I had the same problem, and it ended up being a megaraid SCSI driver for my Dell Perc3 card I was using to run an LTO tape drive. Removed the card and the problem went away. Frustrating though because you need 3 or 4 days each time to test it when troubleshooting.

-Tim

---

### Post by ilrudie on 2008-08-28
You can also run some of the following commands to get and idea whats going on.
1) free  - tells you about memory and swap (might want the -m flag for more readable output)
2) iostat  - tells you if a disk is being overworked or there is very high io wait etc... (-x for more info)
3) top  - lots of info about processes/users/cpu/memory/load etc... I don't know if its installed by default but I think it is.

Also pidstat, vmstat, and mpstat can give you some interesting info.  Read the man pages to find the right flags to get just what you need.  

You can also look into an awesome open source monitoring solution called zabbix.  You can monitor absolutely anything you can script on all your servers (Linux, Aix, Solaris, even Windows I think) from one webpage and it can send emails when vital stats get to a level where you should be concerned.

---

### Post by de0xyrib0se on 2008-08-28
Sounds like a memory leak from one of the drivers indeed. Start removing things :)

---

### Post by baliktad on 2008-08-28
OK, the suggestions so far were helpful.  It does appear to be a memory leak of some sort.  Here's the output of free this morning:

```
             total       used       free     shared    buffers     cached
Mem:        255680     197120      [COLOR="Red"]58560[/COLOR]          0      24780     144744
-/+ buffers/cache:      27596     228084
Swap:       738948      39696     699252

```

And then 4 hours later (no system activity occured in the meantime):

```
             total       used       free     shared    buffers     cached
Mem:        255680     201192      [COLOR="red"]54488[/COLOR]          0      28888     144744
-/+ buffers/cache:      27560     228120
Swap:       738948      39696     699252

```
By my calculation, it's losing about 1MB of memory an hour to... something.  I'm not sure how to tell what.

---

### Post by de0xyrib0se on 2008-08-28
This should get you what you need:

[http://unixlive.editboard.com/general-linux-admin-stuff-f3/how-much-ram-is-used-per-program-t5.htm](http://unixlive.editboard.com/general-linux-admin-stuff-f3/how-much-ram-is-used-per-program-t5.htm)

4 megs isnt really that much, i mean the mere fact you opened a new shell or something could have triggered memory allocation or something, watch it closer over a day and see if the trend continues.

---

### Post by windependence on 2008-08-29
Keep in mind that the Linux memory management model is much different than Windoze. Linux will seem to "consume" memory, but it's really not. It will use the available memory if it can, and just keep everything cached in memory until you need it again. If you open a new application, it will swap out memory instead of disk, which saves on disk activity and make the machine more responsive.

I am quite sure, you have a hardware incompatibilty or even a hardware failure somewhere. Unfortunately, these problems are extremely hard to diagnose, especially without being there.

-Tim

---

### Post by baliktad on 2008-08-29
Results from overnight (again, while nothing was happening).  Before:
```
             total       used       free     shared    buffers     cached
Mem:        255680     208920      [COLOR="Red"]46760[/COLOR]          0      30308     151144
-/+ buffers/cache:      27468     228212
Swap:       738948      39696     699252

```
After 9 hours:
```
             total       used       free     shared    buffers     cached
Mem:        255680     222548      [COLOR="red"]33132[/COLOR]          0      43740     151144
-/+ buffers/cache:      27664     228016
Swap:       738948      39696     699252

```
I also suspect the culprit is Asterisk.  If I stop it, I regain approx. 4 MB of memory, but the slow leak stops (measured over ~6 hours yesterday).

Now I just have to figure out what Asterisk is doing that's causing me so much grief.

---

### Post by baliktad on 2008-08-29
> **windependence said:**
> Keep in mind that the Linux memory management model is much different than Windoze. Linux will seem to "consume" memory, but it's really not. It will use the available memory if it can, and just keep everything cached in memory until you need it again. If you open a new application, it will swap out memory instead of disk, which saves on disk activity and make the machine more responsive.

Actually, this is quite similar to Windows.

> **windependence said:**
> I am quite sure, you have a hardware incompatibilty or even a hardware failure somewhere. Unfortunately, these problems are extremely hard to diagnose, especially without being there.

As I mentioned in my first post, everything is running on Virtual Server 2005.  This means all hardware is emulated.  I highly doubt there is a hardware failure, although I'm willing to take any diagnostic steps you can suggest to identify incompatible hardware/drivers.

---

