---
title: "[Non-PAE] Ubuntu 14.04 Server"
date: 2016-10-31
forum: Server Platforms
---

### Post by nojoke on 2016-10-31
Hey guys,

I have an old, low power, pc104 form factor machine that I would like to work with. Since this machine has an AMD Geode processor it doesn't have PAE, that's why I found OBI "distros". My idea is to have Ubuntu 14.04 server running on this machine. Until now I made it running Ubuntu 14.04 in text mode, however it as stuff that I don't want on it.

Can you help me on this? Or give me some hints?

I know there is a lot of info around in the ubuntu forums but it's a bit confusing and I couldn't figure out the "timeline" of the distros.

Thanks in advance.

Cheers,
Henrique

---

### Post by sudodus on 2016-10-31
Welcome to the Ubuntu Forums :-)

Do you intend to run this machine only in a local area network, or do you intend to connect it somehow to the internet? If connected to the internet it is important to be able to keep all the software up to date, in other words, get a current linux distro with some years to go before the end of life.

What services to you intend to run on the computer?

-o-

It would help us help you, if you specify the computer, more than the general description above (there are many Geode processors). So please specify  your computer, at least

- Brand name and model (of the computer or motherboard)
- CPU
- RAM (size)
- graphics chip/card

I hope that you can also run the following commands (they work in text mode)

```
cat /proc/cpuinfo
free -m
uname -a
sudo parted -ls
```

-o-

Please put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.

---

### Post by nojoke on 2016-10-31
The idea is to run only on a local network. The main goal for this machine is to run a middleware framework called ROS (Robot Operating System), that's why is so important to run Ubuntu since Ubuntu is the "only" officially supported distro for ROS.

[COLOR=#000000]-o-[/COLOR]

Machine specs:
Brand: AEWIN PM6100A-G
CPU: AMD Geode LX-800 500MHz
RAM: 512MB PC3200 SODIMM

```
~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 5
model  : 10
model name    : Geode(TM) Integrated Processor by AMD PCS
stepping    : 2
microcode    : 0x8b
cpu MHz  : 499.916
cache size    : 128 KB
physical id    : 0
siblings    : 1
core id  : 0
cpu cores    : 1
apicid  : 0
initial apicid    : 0
fdiv_bug    : no
f00f_bug    : no
coma_bug    : no
fpu  : yes
fpu_exception    : yes
cpuid level    : 1
wp  : yes
flags  : fpu de pse tsc msr cx8 sep pge cmov clflush mmx mmxext 3dnowext 3dnow
bogomips    : 999.83
clflush size    : 32
cache_alignment    : 32
address sizes    : 32 bits physical, 32 bits virtual
power management:
```
[COLOR=#000000]
[/COLOR]```
[COLOR=#000000]~$ free -m
             total       used       free     shared    buffers     cached
Mem:           487         85        402          0          9         44
-/+ buffers/cache:         30        456
Swap:         4533          0       4533[/COLOR]
```[COLOR=#000000]

[/COLOR]```
[COLOR=#000000]~$ uname -a
Linux nonpae 3.13.0-non-pae #1 SMP Sat Jun 28 15:36:25 BST 2014 i586 i586 i586 GNU/Linux[/COLOR]
```[COLOR=#000000]

[/COLOR]```
[COLOR=#000000]~$ sudo parted -ls
Model: ATA SDCFXPS-032G (scsi)
Disk /dev/sda: 32,0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  27,3GB  27,3GB  primary  ext4
 2      27,3GB  32,0GB  4754MB  primary  linux-swap(v1)[/COLOR]
```[COLOR=#000000]


I know that these specs are not great, but this machine will only do the interface with some low-level sensors for an autonomous underwater vehicle, where the power consumption is a problem...[/COLOR]

---

### Post by sudodus on 2016-11-01
I see. You need not upgrade to be safe against attacks from the internet, so it might be OK to use this old custom made non-pae kernel.

Ubuntu Trusty is still supported, which means that you can get new program packages. Let us hope that they will work with this old kernel. Otherwise I can help you find the developer of the non-pae kernel and ask if it is possible to get a current version.

-o-

Now to the problem you mentioned in post #1: > however it as stuff that I don't want on it.

Please explain, what you need and what you want to get rid of, and we can try to help you fix it.

---

### Post by nojoke on 2016-11-01
> **sudodus said:**
> 
Ubuntu Trusty is still supported, which means that you can get new program packages. Let us hope that they will work with this old kernel. Otherwise I can help you find the developer of the non-pae kernel and ask if it is possible to get a current version.

That would be nice! :D

-o-

> **sudodus said:**
> 
Please explain, what you need and what you want to get rid of, and we can try to help you fix it.

To be honest I have not dissected all the packages that are on the [obi_Trusty-nonpae-txt5-9w.iso]("http://phillw.net/isos/linux-tools/9w/obi_Trusty-nonpae-txt5-9w.iso") distro, but I noticed, for example, NetworkManager and some packages for the graphic plymouth that don't come in the server version of Ubuntu.

All these small stuff, cause a "big" impact on a machine like this one, on the boot time for example.

Anyway, even with the [obi_Trusty-nonpae-txt5-9w.iso]("http://phillw.net/isos/linux-tools/9w/obi_Trusty-nonpae-txt5-9w.iso"), I didn't manage to have it working perfectly fine. Every time that I boot I get this error:

```
error: attempt to read or write outside of disk 'hd0'
```

I think is some problem with the grub but I cannot fix it

---

### Post by mörgæs on 2016-11-01
As mentioned already there are several versions of the Geode. Though the LX series is old it's still one of the younger members of the family. 

If you managed to get a 14.04.0 server running with kernel 3.13 I expect that it will also support 16.04.1. Here is a guide for the [PAE]("https://help.ubuntu.com/community/PAE") problem.

An autonomous underwater vehicle? Wow, please tell more :-)

---

### Post by sudodus on 2016-11-01
If you want something really minimal, yet modern, I would suggest that you start with a Debian Jessie mini.iso - if the ROS software works with Debian Jessie (even if not officially supported). There is a non-pae version, and that way you can built it by adding program packages, which is much easier than to strip packages that you don't need (and risk problems with dependencies).

-o-

By the way, have you considered Raspberry Pi instead of this old computer with Geode? Do you think the Raspberry Pi is not reliable enough, or does it need too much power, or is there some other reason, that you prefer this old computer?

---

### Post by nojoke on 2016-11-02
> **sudodus said:**
> If you want something really minimal, yet modern, I would suggest that you start with a Debian Jessie mini.iso - if the ROS software works with Debian Jessie (even if not officially supported). There is a non-pae version, and that way you can built it by adding program packages, which is much easier than to strip packages that you don't need (and risk problems with dependencies).

That could be an alternative, but it should be one of the last. There are a lot of people with problems running ROS with Debian, not only because of some packages but mainly because of the versions of some of them.

-o-

> **sudodus said:**
> By the way, have you considered Raspberry Pi instead of this old computer with Geode? Do you think the Raspberry Pi is not reliable enough, or does it need too much power, or is there some other reason, that you prefer this old computer?

Yes, the decision to use this computer is not final. The main reason, beside the power consumption and the MTBF, is also the amount of reliable and industrial expansions boards available. Most of the sensors still use serial ports (!!!), so I need at least 10 serial ports and some CAN bus available. Of course there are hubs available, but I would like to stick to these tested expansions boards. 

Regarding the reliability, I don't know exactly how is the Raspberry Pi but I know how is this machine. I don't know yet, but this machine maybe will also run some low-level controllers for emergency and, as you can imagine, it cannot fail at 3000 meters depth :D

---

### Post by sudodus on 2016-11-04
[QUOTE=nojoke]Just a quick question: Do you know why I get this message when installing OS through OBI?

```
error attempt to read or write outside of disk 'hd0'
```[/QUOTE]

No, not directly. I need more information.

1. Can you describe when it happens: - What happens before?

2. What happens afterwards? Will the installation crash or is it just an 'annoying warning'?

It would help if you can post whatever output you can copy and paste from the terminal window to a reply here, and put it within CODE tags.

---

