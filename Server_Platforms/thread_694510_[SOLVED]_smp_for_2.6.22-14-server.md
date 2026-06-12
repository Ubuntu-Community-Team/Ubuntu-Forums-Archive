---
title: "[SOLVED] smp for 2.6.22-14-server"
date: 2008-02-12
forum: Server Platforms
---

### Post by rickyble on 2008-02-12
I am trying to install using command line apt-get the lastest smp for this kernel but I am not having any success.  Can someone help me.  Its a 386 dual proc intel 500.  Its an older machine but reliable.  compaq.  I did the uname -r and this is the returned image that is installed.  I just need to add smp to it.  thanks in advance

---

### Post by faulkes on 2008-02-12
iirc

```

sudo apt-get install linux-image-2.6.22-14-server

or

sudo apt-get install linux-image-2.6.22-14-generic

```

Faulkes

---

### Post by rickyble on 2008-02-12
I did the server install but the smp is not working.  Will this make the smp work?  Anything else I need to do?  esc at the grub and boot to smp?  Anything?

---

### Post by faulkes on 2008-02-12
-386 kernels are not SMP capable.

-generic and -server are.

IIRC, you should not have to do anything special, however to confirm that, after adding the new kernel, simply check /boot/grub/menu.lst, you should see the new kernel listed above all others.

Edit: You may actually just want to use the following, after doing a bit of research

```

sudo apt-get install linux-server

```

Although all the commands I've shown will work, the above is technically the preferred route as it provides for future upgrades being done properly.
--note that if you've done the first set of commands already, you may wish to remove the first package and then add this one.

Faulkes.

---

### Post by rickyble on 2008-02-12
thanks I ll give those a try as soon as I get home.  I am attempting to install/use a mediatomb server.  I got everything installed but it will error out booting when initializing the processors and I notice it only shows one proc.  I have a few problems downloading to the shared subdirectories so I wanted to make sure I had all the errors taken care of before anything else and I really want to use both procs.  I can stream from the web interface fine but copying to the server is problematic also.  Ill tackle that one after the smp.   Thanks again.!

---

### Post by ikonia on 2008-02-12
please post the output of "uname -a" please

---

### Post by rickyble on 2008-02-12
Linux wshome5 2.6.22-14-server #1 SMP Fri Feb 1 05:28:54 UTC 2008 i686 GNU/Linux

---

### Post by faulkes on 2008-02-12
> **rickyble said:**
> Linux wshome5 2.6.22-14-server #1 SMP Fri Feb 1 05:28:54 UTC 2008 i686 GNU/Linux

Is the date correct on that uname command?

and did you install the -server kernel prior to doing it?

Faulkes

---

### Post by rickyble on 2008-02-13
Yes I did.  I tried both the server and generic.  No difference.  I shouldnt be that hard should it.  I mean its should be able to pick up the two and use smp.

---

### Post by faulkes on 2008-02-13
If you installed the -server and -generic kernels and it is not seeing the second cpu, then a larger issue exists than just the kernel.

Do you have the exact cpu / hardware specifications of the machine you are running?

Faulkes

---

### Post by rickyble on 2008-02-13
compaq sp700.  dual 550 100s.  I gig ram.

---

### Post by rickyble on 2008-02-13
just so you know the machine picks up both and recognizes them.  It displays processor 0 and processor 1.  I have another machine identical and 2000 runs on it as a video processing machine for Pinnacle.  It picks up them both

---

### Post by faulkes on 2008-02-13
> **rickyble said:**
> just so you know the machine picks up both and recognizes them.  It displays processor 0 and processor 1.  I have another machine identical and 2000 runs on it as a video processing machine for Pinnacle.  It picks up them both

Could you clarify, the machine (ubuntu linux server) now sees both procs?

Faulkes

---

### Post by rickyble on 2008-02-14
ON boot up the bios picks up both machines.  When it goes through post and initialization processor 0 and 1 show they are present and initialized.  Ubuntu still does not see them or at least use them

---

### Post by faulkes on 2008-02-14
> **rickyble said:**
> ON boot up the bios picks up both machines.  When it goes through post and initialization processor 0 and 1 show they are present and initialized.  Ubuntu still does not see them or at least use them

Interesting, could you send the ouput of the 'dmesg' command? as well as 

```

sudo lshw -short

```

Faulkes

---

### Post by rickyble on 2008-02-14
I will as soon as I get back home.  Thanks for working with me.  I am not exactly a beginner but far from a journey person yet.

---

### Post by rickyble on 2008-02-14
Also I did get my network dropping fixed.  I forced it to 100 half instead of 100 full.

---

### Post by rickyble on 2008-02-15
H/W path            Device      Class      Description
======================================================
                                system     Professional Wor
/0                              bus        04A0h
/0/0                            memory     128KB BIOS
/0/4                            processor  Pentium III (Kat
/0/4/f                          memory     32KB L1 cache
/0/4/10                         memory     512KB L2 cache
/0/5                            processor  Pentium III (Kat
/0/5/11                         memory     32KB L1 cache
/0/5/12                         memory     512KB L2 cache
/0/21                           memory     System Memory
/0/21/0                         memory     128MB DIMM DRAM
/0/21/1                         memory     256MB DIMM DRAM
/0/21/2                         memory     128MB DIMM DRAM
/0/21/3                         memory     DIMM DRAM [empty
/0/21/4                         memory     128MB DIMM DRAM
/0/21/5                         memory     256MB DIMM DRAM
/0/21/6                         memory     128MB DIMM DRAM
/0/21/7                         memory     DIMM DRAM [empty
/0/22                           memory     Flash Memory
/0/22/0                         memory     512KB Chip FLASH
/0/1                            memory
/0/2                            memory
/0/100                          bridge     CNB20-LE Host Br
/0/100/0.1                      bridge     CNB20-LE Host Br
/0/100/0.1/0                    processor  GLINT Gamma G1
/0/100/0.1/0.1                  display    GLINT R3
/0/100/7            scsi0       storage    53c895
/0/100/f                        bridge     Compaq Computer
/0/100/f.1          scsi3       storage    Triflex Dual EID
/0/100/f.1/0.0.0    /dev/sda    disk       232GB WDC WD2500
/0/100/f.1/0.0.0/1  /dev/sda1   volume     46GB Linux files
/0/100/f.1/0.0.0/2  /dev/sda2   volume     55GB Linux files
/0/100/f.1/0.0.0/3  /dev/sda3   volume     121GB Linux file
/0/100/f.1/0.0.0/4  /dev/sda4   volume     9569MB Linux swa
/0/100/f.1/0.1.0    /dev/cdrom  disk       CRD-8322B
/0/100/f.2                      bus        ZFMicro Chipset
/0/101                          bridge     CNB20-LE Host Br
/0/102                          bridge     CNB20-LE Host Br
/0/8                            storage    53c875
/0/8.1                          storage    53c875
/0/9                            bus        FireWire Control
/0/b                eth0        network    82557/8/9 Ethern
myth@wshome5:~$

---

### Post by tehet on 2008-02-15
If you run "top" and then press "1", do you see Cpu0 and Cpu1 on the 3rd and 4th line?

Also I think you shouldn't force your ethernet at all if possible. It's best to let it autonegotiate with the other side of the cable.

exmpl:
```
$ top
top - 11:02:17 up 4 days,  1:56,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  80 total,   1 running,  79 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.3%us,  0.3%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.7%us,  0.0%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    516836k total,   451772k used,    65064k free,    66732k buffers
Swap:   369452k total,       52k used,   369400k free,   227692k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2572 root      15   0  6272 1804 1268 S    1  0.3  28:33.82 nmbd
14595 root      15   0  1684  508  440 S    0  0.1   0:00.10 iptotal
...
```

---

### Post by faulkes on 2008-02-15
> **rickyble said:**
> 
H/W path            Device      Class      Description
======================================================
/0/4                            processor  Pentium III (Kat
/0/5                            processor  Pentium III (Kat


So it appear that lshw does see two processers, can you double check 
/proc/cpuinfo (also do an ls of /proc to see if there is anything else re: cpu's
in there).

Faulkes

---

### Post by faulkes on 2008-02-15
> **tehet said:**
> If you run "top" and then press "1", do you see Cpu0 and Cpu1 on the 3rd and 4th line?


Good suggestion with top! I hadn't thought about it.

> 
Also I think you shouldn't force your ethernet at all if possible. It's best to let it autonegotiate with the other side of the cable.


It's not always best to allow auto-negotiation, there have been known problems with switches failing to bring up auto-neg (i.e. cisco used to have this alot).

Faulkes]

---

### Post by rickyble on 2008-02-15
Ill do the top as soon as I get back to the machine.  It does now appear that it now sees both.  

Also I had to force full.  I am pulling videos from two hacked tivos using a program called tysuitej.  It converts them on the fly to mpg2.  I am using the sister machine of this server(sp700 dual) running Windoze 2000 as a go between. Tysuitej runs on the windoze and pulls it from the tivos converts it on the fly and saves it to the linux box.  One of the tivos is hd and the files are pretty big.  If I use auto the linux server freezes and completely locks.  I have to hard boot just to get it back on line.  Since I forced to full it flies and down loads converts all in a reasonable time.  This morning I was downloading a HD LOST and playing a mp3 on another machine and streaming a LOST episode with mediatomb  all at the same time after I forced to full.  Worked beautiful.  I had tried the MTU everything but the forcing is the only thing that worked.  Since it looks like everything works now this weekend I intend to start in earnest and use mythbuntu, install a new raid card, new hard drives and build my media server.

---

### Post by rickyble on 2008-02-16
Thanks you guys so much.  They both show up now and are functioning.  Must have been the generic install or server that did it.  I think it was the generic that actually did an install.  Also I had the acpi error at boot but I fixed that with a post I found about acpi=force.  Looks all is good now and I can buy my storage and start my media server in earnest.  I have mybuntu downloaded and burned and ready to go.  I really had my doubts about this machine being so old but apparently not.   I was trying to find a bios update for it but since compaq is now hp its not near as easy to find them.  
And the age of the machine makes it hard too.  The server does boot with the bios warning its pre 2000 and complains about it being 1999 but it doesnt really seems to affect it.  Thanks again for everything.  One last ....how can I mark this thread as solved?

---

### Post by faulkes on 2008-02-17
> **rickyble said:**
> how can I mark this thread as solved?

Under "Thread Tools" select "Mark this thread as solved".

I have taken the liberty of doing so for you.

Faulkes

---

### Post by rickyble on 2008-02-25
Thanks! Sorry for the delay.

---

