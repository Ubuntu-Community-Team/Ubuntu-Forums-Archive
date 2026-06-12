---
title: "is it SO difficult to resize a partition?"
date: 2006-01-14
forum: The Cafe
---

### Post by xmastree on 2006-01-14
Probably not the correct forum, in fact it's not even an ubuntu question but here goes anyway...

I have this old laptop (P166/32MB/2GB), and I want to resize the current 2GB partition down to about 1.5GB, then install Damn Small Linux on the remaining 500.

Pretty straightforward, no?

**No.**

I can't find a suitable program for resizing it... DSL runs well but has nothing (that I'm aware of), so I d/l [the ultimate boot disc]("http://www.ultimatebootcd.com/") to try that. There's a [partition resizer]("http://zeleps.com/") but that doesn't seem to work. For some reason, there's 20MB unpartitioned at the end of the disk. The above program seems capable of moving the partition within the drive, but not resizing it.

So, I go for F7 to run insert linux, which contains qtparted.
X doesn't run, qtparted needs X. ](*,)
it **almost** runs... I get the crisscross screen and x cursor, screen changes to a smooth colour, cursor to an arrow (movable), then it barfs.

**[COLOR="Blue"]X-Window session terminated with errors.[/COLOR]**

I look in /var/log and see **XFree86.0.log** so I take a look. The only obvious errors are font problems, nothing fatal.

**Warning: font renderer for "pcf/snf/bdf/.Z/.gz" already registered at priority 0**

I've tried all the options (well, most of them... :rolleyes: )

So, if I can't get this running, is there a better solution I can try? Puppy doesn't load (known problem on <64MB systems) so that's not an option.

Starting over is an option, there's nothing important on the Windows 98 installation, but I would prefer to try resizing as it's something I've never done before, and if I screw up it's no big deal.

---

### Post by briancurtin on 2006-01-14
have you tried using regular old "parted" or you could try "gparted"

get the ubuntu live CD and try that

---

### Post by aysiu on 2006-01-14
I highly recommend [using DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142).

---

### Post by Iandefor on 2006-01-14
System Rescue CD or Knoppix. Both have QTParted (But SRCD requires you to enable the framebuffer on boot, so it might just be simpler to use Knoppix), which I've had good luck with. Also, the Ubuntu LiveCD should have a partitioning tool on it.

---

### Post by xequence on 2006-01-14
The partitioner on the ubuntu installer rocks my socks.

---

### Post by xmastree on 2006-01-14
Knoppix? I didn't even consider that since I only have 32MB RAM.
I know Ubuntu live needs 128MB, and IIRC Knoppix uses KDE so I figured it's bound to be more hungry.

I have it somewhere around here...

Hmm... it asked me to create a swap file on /dev/hda1 which is fair enough, but that's the partition I want to resize...

---

### Post by Wallakoala on 2006-01-14
You can use the partitioner on the ubuntu install cd, or you can use freedos. I have never actually used freedos, but I know you can burn a floppy image and then use fdisk to manage your partitions.

---

### Post by xmastree on 2006-01-14
I didn't know fdisk could **resize** a partition... I have a free fdisk on the ultimate boot disc but it's the same as the MS one, no option to resize. I could easily delete the primary and create a smaller one, but I don't want to destroy the Windows installation if possible.
The Ubuntu Live CD needs more RAM.
Knoppix is **still** booting since my last post, swapping like crazy no doubt.
I've even been and had my lunch while waiting for it!

---

### Post by BSDFreak on 2006-01-14
parted hda -i
(parted) rezise 1 0 1500

That will resize the 1'st partition on the IDE master on primary channel so it begins at 0 and ends at 1500MB.

It can be done from any cd that has parted on it (every cd that has qtparted or gparted on it has parted since qtparted and gparted are just the GUI's for parted).

---

### Post by xmastree on 2006-01-14
[QUOTE=BSDFreak]parted hda -i
(parted) rezise 1 0 1500[/QUOTE]
Will that do it without destroying any data? I have already defragged it so it's all in the first half.
Knoppix is **still** trying to boot, I suspect it'll never get there. :( 

I see the spaceman floating above earth, and three vcr buttons, movable cursor, but nothing else.

Maybe damn small has parted.

---

### Post by BSDFreak on 2006-01-14
[quote=xmastree]Will that do it without destroying any data? I have already defragged it so it's all in the first half.
Knoppix is **still** trying to boot, I suspect it'll never get there. :( 

I see the spaceman floating above earth, and three vcr buttons, movable cursor, but nothing else.

Maybe damn small has parted.[/quote] 
No, it won't destroy any data, i'd say it's safer than qtparted or gparted since they will issue these commands to parted anyway, it's one less step that could go wrong.

I was going to recommend that you defrag it first so that's a good thing that you have.

Fdisk as someone suggested won't resize any partition, not the Linux version and not the DOS version either.

EDIT:Looks like DSL has parted, at least they did in older versions. :)

---

### Post by xmastree on 2006-01-14
Ok, sounds good.
I'm just defragging again, since I've used it since last time, then I'll go for it... [-o<

---

### Post by BSDFreak on 2006-01-15
[quote=xmastree]Ok, sounds good.
I'm just defragging again, since I've used it since last time, then I'll go for it... [-o<[/quote]

Best of luck!

---

### Post by xmastree on 2006-01-15
Well, it worked. \\:D/
Although parted isn't included with the version of dsl I have here (1.4) but it is there on the ultimate boot CD, and doesn't need X.

So, Houston, we have lift off.

Thanks for the help. :D

---

### Post by BSDFreak on 2006-01-15
[quote=xmastree]Well, it worked. \\:D/
Although parted isn't included with the version of dsl I have here (1.4) but it is there on the ultimate boot CD, and doesn't need X.

So, Houston, we have lift off.

Thanks for the help. :D[/quote]

No worries, glad you got it up and running. :)

---

