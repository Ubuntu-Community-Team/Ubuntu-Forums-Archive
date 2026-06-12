---
title: "Why would functioning hard drive cause kernel panic?"
date: 2011-08-26
forum: System76 Support
---

### Post by birdsarah on 2011-08-26
Hi,

I have a new GazP6 - loving it.

I got a caddy case to put my hard drive from my thinkpad into the optical drive.

This causes a kernel panic every few hours - although the time between panics was increasing - 12 hours for the last one - it's not a good thing.

I am pretty sure it's the hard drive and not the caddy as I put in a different hard drive from a different thinkpad and everything was fine.

The specs of the hard drive that causes kernel panics are (320GB 7200 rpm):
       description: ATA Disk
       product: ST9320423AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 0003
       serial: 5VH41VYB
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00097ed4

The specs of the hard drive that doesn't are (80GB 5400rpm):
       description: ATA Disk
       product: HTS541080G9SA00
       vendor: Hitachi
       physical id: 1
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: MB4I
       serial: MPBDPAXNH0UJLM
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=ed1f86f7

When either of the above drives are the hard drive of my thinkpad I have no issues.

The 80GB drive is nearly 5 years old, the 320 GB hard drive is 9 months old.

I would prefer to be able to have the larger drive in my new GazP6.

Thanks,

Bird

---

### Post by birdsarah on 2011-08-26
Hi,

so it turns out they're both causing it!

So sad.

Help welcome.

---

### Post by Actonix on 2011-08-26
Check out what the panic is, that should help you identify the problem, post it here if you need further help with it,

Open up a terminal and run the following command
```

sudo dmesg -n 1

```

Would probably also help to provide a bit more detail to assist, Are you running Ubuntu on both systems and what partition types exist on the drives ?

---

### Post by birdsarah on 2011-08-26
Hi,

dmesg with "-n 1" gives me nothing at all.

just plain dmesg has lots of stuff not sure if any of it's relevant though.

Just to clarify, I am now pretty certain it's the caddy given that both hard drives have now caused a kernel panic although one much more so than the other. I have now put the optical bay back in to confirm this and am going to wait a day or so. If I am kernel panic free then System76 will replace the caddy.

If not - then I guess it's either software - which wouldn't make any sense as there doesn't appear to be one specific thing that causes it or some kind of internal hardware problem which would mean sending back my beautiful laptop which would make me sad. So I'm hoping it's the caddy!

And yes, all the hard drives are from Linux Ubuntu 11.04 systems with ext4 file system.

And - thank you! :D

Best,

Bird

---

### Post by birdsarah on 2011-08-27
So sad....the optical drive is back in and after a promising 9 hours I just got another kernel panic....I have a horrible feeling that this means that there's something wrong with the laptop I've fallen in love with (in spite of the 10 kernel panics in 3 days). Thoughts welcome.

Bird

---

### Post by birdsarah on 2011-08-27
Well that's a first - two kernel panics in 15 minutes! Sigh.

This time they were both during a large file transfer between an external hard drive and my SSD. 

Help - this is a major bummer.

---

### Post by Actonix on 2011-08-28
Hi again,

Would have thought others would have assisted you in seeking resolution here by now, sadly, I've not really been around much of late and only pop in very briefly when I do look in.

The command I gave you was meant to be used to show up the kernel panics and as such will show nothing if you issue it when no panics have occurred - the details thus obtained should help you or anybody else that may be able to assist you in identifying the problem and seeking appropriate solution.

I could go further and provide you with commands to check your files-system which is one of the areas your problem might lie in but then again if the problem is intermittent it might actually be related to the caddy interface ie loose connectivity between it and the PC in question which could also result in a corrupt file-system - if the latter is the case you might be able to find resolution by loosening the screws holding the hard disk in, squaring out the caddy in order to get a better connection and re-tighten.

Whatever the case, when next a panic occurs try and post the details here and take things from there.

I wish you the best of luck with things.

---

### Post by birdsarah on 2011-08-28
Hi!

Just had ANOTHER Kernel Panic! sudo dmesg -n 1 reveals nothing. (I am doing this after a reboot as I am completely locked out of the machine when it happens - Ctl-Alt-F1 doesn't take me to a terminal - completely stuck).

It is not the caddy as I put the optical drive back in.

It is not the bluetooth as I have had that off since the last one as a test.

This is so disappointing. I have been looking forward to owning a System76 for 8 months now. 

I have long-used my Thinkpad with Ubuntu and loved it. When it came time for a replacement I decided that investing in a company who specifically built and supported hardware for Ubuntu would be awesome....I am now about 3 kernel panics away from feeling like I've made a horrible mistake.

---

### Post by birdsarah on 2011-08-28
Let's make that 2 kernel panics

---

### Post by Actonix on 2011-08-28
> **birdsarah said:**
> Hi!

Just had ANOTHER Kernel Panic! sudo dmesg -n 1 reveals nothing. (I am doing this after a reboot as I am completely locked out of the machine when it happens - Ctl-Alt-F1 doesn't take me to a terminal - completely stuck).

It is not the caddy as I put the optical drive back in.

It is not the bluetooth as I have had that off since the last one as a test.

Hmmm, unfortunately it does not help that you cannot run it when it could give an indication as your system is frozen, and for the same reason though the error is logged on the screen the system is essentially not functioning at this point and so does not get logged to file. 

Well, as you have eliminated the caddy let's checkout other areas - you can try using lm-sensors to measure the CPU  temp while it is under load - eliminate overheating as the cause, 

... from a terminal  run

```
sensors
```

... might as well go a step further and use pSensor as it's more visual, a GUI

... I think you get that from Universe, install via Synaptic or from a terminal  ```
sudo apt-get install psensor
```

- and try MemTest86+  to test your RAM (you can do this from the Live CD )

... a process of problem resolution by elimination - slow it might be but if you persevere we will get there.

So far, if I read into things and made a haphazard a guess I would say overheating is the cause and I say this as you indicate the kernel panics to be closer after an initial freeze and reboot, might be a failed or failing fan or more simply just accumulated dirt hindering the cooling process - if you could open up the laptop or at least the area the fan is located you could easily clean that up and or verify this to be or not the case.

---

### Post by birdsarah on 2011-08-29
Hi,

Thanks for the reply. 

I will start looking at these for possible elimination step-by-step.

My instinct says it's not overheating or the fan. It's only 5 days old and my apartment's fairly clean :D so the fan shouldn't be clogged up yet. The fans kick in occasionally but not much. I haven't done anything that taxing. And the times I deliberately taxed it - running a flash movie in a virtual machine while compiling code - the fan was going but I couldn't make it panic - I did this for 3 hours the other morning as an attempt.

However, when I did "sensors" after installing lm-sensors, I only got the following result:
> acpitz-virtual-0
Adapter: Virtual device
temp1:       +39.0°C  (crit = +154.0°C)   
I would have expected more devices no?

I will certainly start logging this temperature every 5 minutes as it's easy and we can take a look.

MemTest -  will have a look - never done this before - only got 4GB ram as am getting 4 more in the mail this week so have been running at about 80-90% capacity on the RAM almost all the time.

Cheers,

Bird

---

### Post by birdsarah on 2011-08-29
Latest kernel panic - temperature at 40C - hasn't gotten above that all day :(

Will give the MemTest a try over the next day or so.

Bird

---

### Post by Mart on 2011-08-30
I'm struggling with a similar issue on a LeoX2.  System reboots when the processor is under load with no log entry.

Tested the memory with memtest86+and after many passes (8) I found 2 bad chips.  I'm assuming after heat built up they started failing.

I've replaced the bad chips but the system still shuts down so I've tested the processor with mprime and watched the sensors for heat issues (watch -n .5 sensors) but the heat isn't building up past 70C and the system usually reboots within 15 minutes.

I'm waiting now on a reply from support.  

Good luck with your issue.  I feel the same way. After working with linux on windows systems I also decided to start supporting a "linux" company.

---

### Post by isantop on 2011-08-30
For this issue on a Leopard, we were recently made aware of an issue caused by hyperthreading in the Leopard BIOS. We're working very hard to fix that problem, but as a workaround, you can disable hyperthreading in the BIOS configuration to prevent the kernel panics. 

For the issue with the Gazelle, you should run MemTest86 to ensure that the memory is okay (it sounds like you've ruled out both the hard drive and the caddy case very well). You can download a MemTest86 ISO file from [here.](http://www.memtest.org/)

Simply download the .ISO, right-click on it, then click "Burn to disk". Then, put the disk in the Gazelle DVD drive and boot it up. It should start from the DVD drive automatically, but if it doesn't, you can force it to by hitting F7 during the System76 splash page.

---

### Post by Mart on 2011-08-30
Thanks

Wasn't attempting to hijack this I just wanted to mention that it took a few passes before the memory failed.

---

### Post by birdsarah on 2011-09-10
An update:

I got 4GB extra ram installed.

I ran the memtest once, one pass, no errors. and again overnight, many passes and no errors.

I then went away for Labor Day weekend and left my laptop behind - sad but sometimes it's good to take a break (apparently!).

Since I've been back I haven't had a panic - that's four days and counting. 

I will leave it for a few days more and then if still nothing, I will try putting the external caddy with hard drive back in and see what happens!

Best,

Bird

---

### Post by birdsarah on 2011-09-19
Hi all,

So - I can't really explain this. Apparently all my laptop needed was a Labor Day vacation! I haven't had a kernel panic since I returned from a weekend away. The only thing I did was add new RAM, as I explained above. 

I have now put in a new external hard drive in the caddy, and everything is still functioning as normal.

Thanks for all your support. 

This will have to just go down as a gremlin who needed a break!

All the best,

Sarah Bird

---

### Post by isantop on 2011-09-21
Keep us up to date. It could have been the RAM.

Enjoy your system! Particularly now that it's stable!

---

### Post by birdsarah on 2011-09-25
Bahhhhhh......

I spoke to soon - of course :D

Kernel panic last night. Nothing particularly exciting going on at the time.

I am very happy with my laptop overall, and thanks to the stability of linux I haven't lost anything yet due to this issue.

Will keep posting.

---

