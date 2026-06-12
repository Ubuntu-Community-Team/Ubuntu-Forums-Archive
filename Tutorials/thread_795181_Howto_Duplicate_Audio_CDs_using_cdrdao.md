---
title: "Howto: Duplicate Audio CDs using cdrdao"
date: 2008-05-15
forum: Tutorials
---

### Post by andrew.46 on 2008-05-15
This page has been moved to the Ubuntu Community wiki:

[https://help.ubuntu.com/community/cdrdao](https://help.ubuntu.com/community/cdrdao)

However support is still available from this thread. Feel free to ask any questions :).

---

### Post by rosencrantz on 2008-12-16
Great post, just a quick note: The ATA syntax is obsolete (see [http://markmail.org/message/b7yf4kkdnywqijpb]("http://markmail.org/message/b7yf4kkdnywqijpb")), so try 
the wodim --devices output to get the correct device (something like --device /dev/scd0)

---

### Post by andrew.46 on 2008-12-16
Hi rosencrantz,

> **rosencrantz said:**
> Great post, just a quick note: The ATA syntax is obsolete (see [http://markmail.org/message/b7yf4kkdnywqijpb]("http://markmail.org/message/b7yf4kkdnywqijpb")), so try 
the wodim --devices output to get the correct device (something like --device /dev/scd0)

Thanks for your post. I will admit to not having used wodim that much, I tend to use Jorg Schilling's cdrecord as a deliberate choice. cdrecord uses the same scsi syntax though. I have not tested the wodim syntax, does it work with cdrdao? Burning on my system has been flawless with the scsi address given in this guide.

  Andrew

---

### Post by rosencrantz on 2008-12-16
Hi Andrew,
yep, sorry - evil SuSE user, so I wrote wodim kind of automatically. Considering the fact that I have a compatibility package symlinking cdrecord directly to wodim, I suppose they kept the syntax the same after the fork - naturally, I have no way to test that assumption. AFAIK, cdrdao is not affected by the fork.
Fiddling with [FONT="Courier New"]cdrdao copy[/FONT] on SuSE 11, I tried both the SCSI specs from  [FONT="Courier New"]cdrdao scanbus[/FONT], which didn't work  and the [FONT="Courier New"]/dev/cdr0[/FONT] from [FONT="Courier New"]cdrecord --devices[/FONT], which did. 
Update: [FONT="Courier New"]cdrdao scanbus[/FONT] warns me: "the ATA: method is considered deprecated on modern kernels! Use --devices to display the native names."
Kernel 2.6.25 - are you using an older one or is this some weird distro/fork-specific issue?


Greets rosencrantz

---

### Post by andrew.46 on 2008-12-17
Hi,

Ubuntu also uses wodim instead of cdrecord with a similar symlinking device, it is actually only *me* who uses the real cdrecord on Ubuntu :-).

But I am not one to ignore advice so I tested on my freshly reloaded Ubuntu Intrepid Ibex system with the default cdrdao and wodim installed. Forgive me if this reply is somewhat long-winded but I have investigated this thoroughly:

```
**[COLOR="Red"]andrew@skamandros:~$ sudo cdrdao scanbus[/COLOR]**
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

**[COLOR="Red"]1,0,0 : Optiarc , DVD+-RW AD-5560A, DD11[/COLOR]**

```

and with wodim:

```
**[COLOR="Red"]andrew@skamandros:~$ wodim --devices[/COLOR]**
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  **[COLOR="Red"]dev='/dev/scd0'[/COLOR]**	rwrw-- : 'Optiarc' 'DVD+-RW AD-5560A'
-------------------------------------------------------------------------

```

which all looks reasonable. So to try the wodim syntax with cdrdao:

```
[B][COLOR="Red"]andrew@skamandros:~/Desktop$ sudo cdrdao read-cd --source-device /dev/scd0 --driver generic-mmc \
>                       --paranoia-mode 3 audiocd.toc[/COLOR][/B]
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

/dev/cdrw: Optiarc DVD+-RW AD-5560A	Rev: DD11
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Reading toc and track data...

Track   Mode    Flags  Start                Length
------------------------------------------------------------
 1      AUDIO   0      00:00:32(    32)     04:19:63( 19488)
 2      AUDIO   0      04:20:20( 19520)     02:47:45( 12570)
 3      AUDIO   0      07:07:65( 32090)     04:17:65( 19340)
 4      AUDIO   0      11:25:55( 51430)     03:35:70( 16195)
 5      AUDIO   0      15:01:50( 67625)     03:43:45( 16770)
 6      AUDIO   0      18:45:20( 84395)     03:51:65( 17390)
 7      AUDIO   0      22:37:10(101785)     03:02:62( 13712)
 8      AUDIO   0      25:39:72(115497)     04:37:35( 20810)
 9      AUDIO   0      30:17:32(136307)     02:24:33( 10833)
10      AUDIO   0      32:41:65(147140)     03:06:40( 13990)
11      AUDIO   0      35:48:30(161130)     03:34:17( 16067)
12      AUDIO   0      39:22:47(177197)     04:07:00( 18525)
13      AUDIO   0      43:29:47(195722)     03:26:18( 15468)
14      AUDIO   0      46:55:65(211190)     03:16:70( 14770)
15      AUDIO   0      50:12:60(225960)     04:57:27( 22302)
16      AUDIO   0      55:10:12(248262)     02:18:15( 10365)
17      AUDIO   0      57:28:27(258627)     03:28:28( 15628)
Leadout AUDIO   0      60:56:55(274255)

PQ sub-channel reading (audio track) is supported, data format is BCD.
Raw P-W sub-channel reading (audio track) is supported.
Cooked R-W sub-channel reading (audio track) is supported.
Copying audio tracks 1-17: start 00:00:00, length 60:56:55 to "data.bin"...
Track 1...

```

And this works perfectly, as does the syntax that I give in the guide:

```
[B][COLOR="Red"]andrew@skamandros:~/Desktop$ sudo cdrdao read-cd --source-device 1,0,0 --driver generic-mmc \
>                       --paranoia-mode 3 audiocd.toc[/COLOR][/B]
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

/dev/cdrw: Optiarc DVD+-RW AD-5560A	Rev: DD11
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

Reading toc and track data...

Track   Mode    Flags  Start                Length
------------------------------------------------------------
 1      AUDIO   0      00:00:32(    32)     04:19:63( 19488)
 2      AUDIO   0      04:20:20( 19520)     02:47:45( 12570)
 3      AUDIO   0      07:07:65( 32090)     04:17:65( 19340)
 4      AUDIO   0      11:25:55( 51430)     03:35:70( 16195)
 5      AUDIO   0      15:01:50( 67625)     03:43:45( 16770)
 6      AUDIO   0      18:45:20( 84395)     03:51:65( 17390)
 7      AUDIO   0      22:37:10(101785)     03:02:62( 13712)
 8      AUDIO   0      25:39:72(115497)     04:37:35( 20810)
 9      AUDIO   0      30:17:32(136307)     02:24:33( 10833)
10      AUDIO   0      32:41:65(147140)     03:06:40( 13990)
11      AUDIO   0      35:48:30(161130)     03:34:17( 16067)
12      AUDIO   0      39:22:47(177197)     04:07:00( 18525)
13      AUDIO   0      43:29:47(195722)     03:26:18( 15468)
14      AUDIO   0      46:55:65(211190)     03:16:70( 14770)
15      AUDIO   0      50:12:60(225960)     04:57:27( 22302)
16      AUDIO   0      55:10:12(248262)     02:18:15( 10365)
17      AUDIO   0      57:28:27(258627)     03:28:28( 15628)
Leadout AUDIO   0      60:56:55(274255)

PQ sub-channel reading (audio track) is supported, data format is BCD.
Raw P-W sub-channel reading (audio track) is supported.
Cooked R-W sub-channel reading (audio track) is supported.
Copying audio tracks 1-17: start 00:00:00, length 60:56:55 to "data.bin"...
Track 1...

```

So on an Ubuntu Intrepid Ibex system ***both*** types of syntax will work. This is probably not a huge suprise when I looked more closely at the man pages and found:

> --device [prot:]bus,id,lun
      Sets the SCSI address of the CD-recorder in form of a bus/id/lun triple, e.g.  &#8217;0,2,0&#8217;  for  the
      logical  unit  0  of SCSI device with ID 2 on bus 0. ATAPI devices can be specified by using the
      prefix &#8217;ATAPI:&#8217;, e.g. &#8217;ATAPI:0,0,0&#8217;. [B][COLOR="Red"]On some systems a device node may  be  specified  directly,
       e.g.  &#8217;/dev/sg0&#8217;  on  Linux systems.[/COLOR][/B] Linux 2.6 users may also try the newer ATAPI interface with
      the &#8217;ATA:&#8217; prefix.


You will note the slight difference between the *ATA* syntax you have spoken of and the *scsi* syntax I demonstrate in the guide.

So my conclusion is that in Ubuntu at least both the scsi syntax and the device address specified by wodim can be successfully used with cdrdao. The ATA style syntax also works on my machine but this may not be the case universally I suspect.

As for one being deprecated in favour of the other, this is a battle that Jorg Schilling and Debian can continue to fight out without me :-).

All the best,

  Andrew Strong

---

### Post by rosencrantz on 2008-12-17
Thorough indeed ;-) and good to know.
Thanks

rosencrantz

---

### Post by daqron on 2010-05-08
This is so excellent, thank you andrew! The other documentation available for cdrdao is completely incomprehensible, so your tutorial really saved the day. It also serves as a great workaround for [this bug]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696").

At first I was having issues with cdrdao hanging while reading track 1 (same as [http://ubuntuforums.org/showthread.php?t=719167](http://ubuntuforums.org/showthread.php?t=719167)). This turned out to be a hardware issue. I swapped out the "read" drive in a two-drive configuration and everything works fine now.

Thanks again. Your various posts/tutorials about CD backups in Linux are really helpful.

---

### Post by bapoumba on 2010-06-16
daqron +1, thanks much Andrew. brasero and gnomebaker are not currently working on any of my Lucid computers, you saved me while I wait for a fix :)

---

### Post by andrew.46 on 2011-05-05
> **bapoumba said:**
> daqron +1, thanks much Andrew. brasero and gnomebaker are not currently working on any of my Lucid computers, you saved me while I wait for a fix :)

My apologies for this somewhat epic necropost, I had temporarily lost site of this guide :). Glad that the guide was useful to you all that time ago, you might be interested in this guide's big brother:

CD and DVD Writing from the Linux Command Line
[http://www.andrews-corner.org/burning.html](http://www.andrews-corner.org/burning.html)

which features a lot more commandline burning :)

---

### Post by bapoumba on 2011-05-06
Thanks again Andrew, bookmarked :)

---

### Post by andrew.46 on 2012-01-11
With a repartition of my drive I have found a place for Oneiric Ocelot and also some time to gently modify this guide for 2012 :). I have altered the location of the cdrdao configuration file, makes more sense to allow the user to host his own configuration and could be a lot safer in the event of some mistyping! Also adjusted the drive identification as cdrdao scanbus does not seem to be using scsci ids any more. Anyway it is an old guide that has now hopefully had a little extra life breathed into it....

---

### Post by hhhobbit on 2012-02-02
You will also probably need icedax in addition to cdrdao.  If you add cdrkit-doc (optional documentation) with Ubuntu 10.04 LTS (sorry, but I go by version numbers for less confusion) you will be good to go with Brasero.  I know because I just made a copy with all of these installed.  I was unable to make a copy of the Ubuntu 10.04 LTS OS using Brasero until cdrdao was installed.  Even with cdrdao installed I was still unable to make a copy of a family history CD with nine *.wav files on it until after I installed icedax.  icedax installs cdda2mp3, cdda2ogg, and cdda2wav, all in /usr bin.

Now, what else am I missing?

---

### Post by andrew.46 on 2012-04-09
This page has been moved to the Ubuntu Community wiki:

[https://help.ubuntu.com/community/cdrdao](https://help.ubuntu.com/community/cdrdao)

However support is still available from this thread. Feel free to ask any questions :).

---

