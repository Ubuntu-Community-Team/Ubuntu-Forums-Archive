---
title: "Sever Trouble - Please Help Fellow Ubuntu-ers!"
date: 2008-02-19
forum: Server Platforms
---

### Post by rlelek on 2008-02-19
Ok, so my new IBM server came in

The trouble is, it is SSSSLLLOOOOOWWWW
I have no idea why this is happening, the BIOS is just crazy slow, and yes, it IS the latest version. I've been trying to figure this all out so I can run Ubuntu server. 

The BIOS takes about 10 minutes to load the system to even get to an Ubuntu Live CD. No Joke. I was thinking of eliminating some of the parts, i.e., remove some processors. I ran diagnostics, all seems fine.

Please Help!!!
I will be eternally grateful to you.
I have tried and tried to figure this out.


This is a 32x machine


Thanks,
Ryan

---

### Post by tubezninja on 2008-02-19
What model of IBM is this?  Also, are there any error messages, or does it come up fine?

FWIW, I have an eServer running Ubuntu 7.10 and I share your pain.  The BIOS and RAID controller have notoriously slow startups (about 4 minutes for my installation), however, I think that's mainly because eServers are intended for high availability, and not intended to be frequently powered down.

IF there aren't any errors, I'm not sure there's much you can do about it, except avoid powering it down or restarting it unless it's necessary.

---

### Post by rlelek on 2008-02-19
> **scaredpoet said:**
> What model of IBM is this?  Also, are there any error messages, or does it come up fine?

FWIW, I have an eServer running Ubuntu 7.10 and I share your pain.  The BIOS and RAID controller have notoriously slow startups (about 4 minutes for my installation), however, I think that's mainly because eServers are intended for high availability, and not intended to be frequently powered down.

IF there aren't any errors, I'm not sure there's much you can do about it, except avoid powering it down or restarting it unless it's necessary.

Thanks for the reply.

I figured servers were supposed to be powered on 24/7, but i really didnt think it would have been THAT slow. 

This is an IBM x445

And indeed, there is an error, something about the "Bad VPD" error (the # is 188, and/or 187) VPD stands for Vital Product Data I believe. I think this is partially due to the fact my hard drives are in another box, as this is a used server. I am running everything Live, and I'm actually on Ubuntu right now. 

Also, here's another thing that baffles me. Why would my system have 8GB of RAM, when it is a 32 bit system? What good is all of that RAM when only the computer recognizes it, and not the OS? I thought it would be for virtual machines, but if you did that via Ubuntu, it would still only see 3.5-4.0 GB memory.:confused:

Feel free to throw anything you are thinking out there.

Thanks again, Ubuntu Forums... Fast, Fun Support!

Ryan

---

### Post by tubezninja on 2008-02-19
Ah, I have the x345, and it also pops up a few errors on startup, but nothing ever critical.

Also, you sure this is a 32-bit system?   The x445 came with Xeon MPs, which could be either 32 or 64 bit.  It could be you have a 64 bit processor but whoever used it last isntalled a 32-bit kernel.

Can you show us the output when you type in:

```
cat /proc/cpuinfo
```


EDIT:  My mistake, looking at the specs, the x445 is in fact an IA-32 system only, [according to the spec sheets]("http://www.ibm.qassociates.co.uk/pdf/x-series-x445.pdf").

But, there's something VERY weird: evidently the x445 can have up to 64GB of RAM installed, per the specs.  VERY odd!

Anyway, if you could post your /proc/cpuinfo output, I think we can settle this once and for all. :)

---

### Post by rlelek on 2008-02-19
Sure, let me reboot into Ubuntu...( I restarted, but not nearly as much as if it were Windoze)

While it's loading, I'll share some progress...
Actually, a performance boost WAS gained!
After messing around in the BIOS, I turned Memory mirroring on.
Through common sense, I figured if I mirrored the 8GB, I would still have the maximum of 4GB, and it did something... not sure how

Booting into Linux and accessing Terminal... I'll post with updates

Thanks again scaredpoet!

Ryan

---

### Post by rlelek on 2008-02-19
Sorry, Ubuntu CRASHED somehow.
I think it's just my server, not Ubuntu

Very Odd..

Another thing that is very odd... How you managed to navigate IBM's site!
I find that layout a deathtrap for older models, but that's just me...

Rebooting...


***WHAT?!> it Crashed again at time of editing... time for a new Live CD!

---

### Post by tubezninja on 2008-02-19
Oh, I didn't bother navigating IBM's site, I know better than that.  I just googled "IBM x445" and a spec sheet came up.  :)

---

### Post by rlelek on 2008-02-19
Output:

ubuntu@ubuntu:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping        : 6
cpu MHz         : 2694.662
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5398.53
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping        : 6
cpu MHz         : 2694.662
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5389.42
clflush size    : 64

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping        : 6
cpu MHz         : 2694.662
cache size      : 2048 KB
physical id     : 1
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5389.47
clflush size    : 64

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping        : 6
cpu MHz         : 2694.662
cache size      : 2048 KB
physical id     : 1
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5389.48
clflush size    : 64

processor       : 4
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping        : 6
cpu MHz         : 2694.662
cache size      : 2048 KB
physical id     : 2
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5389.46
clflush size    : 64

processor       : 5
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping        : 6
cpu MHz         : 2694.662
cache size      : 2048 KB
physical id     : 2
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5389.47
clflush size    : 64

processor       : 6
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping        : 6
cpu MHz         : 2694.662
cache size      : 2048 KB
physical id     : 3
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5389.42
clflush size    : 64

processor       : 7
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 2.70GHz
stepping        : 6
cpu MHz         : 2694.662
cache size      : 2048 KB
physical id     : 3
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5389.51
clflush size    : 64

---

### Post by rlelek on 2008-02-19
First, I apoligize for double posting, but I wanted to get the results up from the server before it crashed, plus that's a lot of information and probably should be segmented anyway.

So i'm on the laptop right now.
And here's an update on the errors...

Memory mirroring removed the 188 and 187 errors!
but a new one appears... error 175: System complex error VPD CRC#1

according to this link (found on google after scaredpoet's success story) to remove errors 188, 187, and 175
JUST FLASH THE RSA (Remote Supervisor Adaptor)

[http://www.ibm.com/developerworks/forums/thread.jspa?threadID=129508](http://www.ibm.com/developerworks/forums/thread.jspa?threadID=129508)

I'll check it out, but remember mirroring did increase my performance by at least 50%
Will again, post results and perhaps add to this one...

Progess, is sooo nice!!!

Ryan

---

### Post by tubezninja on 2008-02-19
Good to hear you're making progress! :)

As for your CPU configuration: you do in fact have a 32-bit server.  However, it is equipped with an impressive 8 CPU cores, which still makes it a **very** able system.  I'd definitely keep it for a good long time!

---

### Post by rlelek on 2008-02-19
Thank you For Everything!!!

You saved me from tearing my hair out!
All errors are GONE!

It boots well now, after enabling the memory mirroring, but I also noticed about the same speed without it, but I've been rebooting many times. So I guess the rule is...

First enable memory mirroring, for stability first
Boot boot and boot the Ubuntu Live cd
check if your errors go away. (mine did)
If not, unplug/remove the CMOS battery for 5 min (a little extreme)
Then just keep messing around with the BIOS settings (all will be default after the CMOS loses its power...or battery)

I hope this helps someone!!!

Ryan

---

### Post by tubezninja on 2008-02-20
You know, you've helped me as well.  I think I might use some of your steps to iron out the quirks in my x340 :)

---

