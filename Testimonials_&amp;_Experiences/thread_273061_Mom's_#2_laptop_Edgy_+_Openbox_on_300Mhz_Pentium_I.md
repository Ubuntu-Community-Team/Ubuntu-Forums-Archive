---
title: "Mom's #2 laptop: Edgy + Openbox on 300Mhz Pentium II"
date: 2006-10-07
forum: Testimonials &amp; Experiences
---

### Post by K.Mandla on 2006-10-07
From the "You can do it, Waterboy" department. ...

I let [Mom]("http://www.ubuntuforums.org/showthread.php?t=156175") borrow an old busted laptop (the one I built the [Live CD server]("http://www.ubuntuforums.org/showthread.php?t=268121") on, actually), so she can send e-mails if Dad is using Windows on the fast machine -- an Inspiron 600m.

[CENTER][[IMG]http://img83.imageshack.us/img83/254/img0001st1.th.jpg[/IMG]](http://img83.imageshack.us/my.php?image=img0001st1.jpg)[/CENTER]

This is a 300 Mhz Pentium II -- Dell's Latitude CPi-A series. The service tag (WMRB9) shows a ship date of July 1999. I had an old DVD-CDRW that fit the optical bay, a spare 256Mb RAM stick and a spare battery and power supply. The hard drive is an ancient 20Gb 4200rpm clunker I was (occasionally) using as an external archive. I almost forgot: Video is via a NeoMagic 2200NM. Remember NeoMagic? :rolleyes:

[CENTER][[IMG]http://img468.imageshack.us/img468/8219/screenshot01sr9.th.jpg[/IMG]](http://img468.imageshack.us/my.php?image=screenshot01sr9.jpg) [[IMG]http://img480.imageshack.us/img480/4126/screenshot02hg2.th.jpg[/IMG]](http://img480.imageshack.us/my.php?image=screenshot02hg2.jpg)[/CENTER]

This is running Openbox on the Edgy beta. Ubuntu configures everything at installation, including the WPC11 v3 wireless card. I've tweaked it to get it running as fast as possible, which trims the startup time to 1:11 from a cold boot. Shutdown is just via the power button, and takes about 8 seconds.

As you can see in conky's display, the system load is tiny -- even with the Gimp running to get the screenshot. 

Iceweasel is the browser, XFE is the file manager and there's even enough muscle left to run Frozen Bubble. She can stream audio from the Shoutcast site through XMMS. The system load is so low that battery life reaches 2 hours. I might install Java for Bookworm, but I'm not sure. Bookworm is always so laggy anyway. ...

But best of all, nobody fights over the 600m any more! Ubuntu makes everybody happy! :biggrin:

---

### Post by Old Pink on 2006-10-07
Nice setup! 

300Mhz... nice. :P 

1:11 startup time is a little disapointing, have you tried profiling?

---

### Post by K.Mandla on 2006-10-07
Yup, it's profiled. Remember that's a cold boot; it's the BIOS startup that really drags things down. If I start the clock when Grub kicks in, it's considerably shorter. (Edit: I just realized I timed it when it was on battery, so it might be that it moves a little faster on AC. ;) )

There's also the fact that it's [an incredibly oversized drive]("http://www.dewassoc.com/kbase/hard_drives/drive_size_barrier_limitations_2.htm") for that machine. The original shipped with a 4.8Gb drive.

So I have a feeling the BIOS sits there, dumbstruck for a second or two (or three or five or eight), before it throws its hands in the air and goes on with what it was doing. (I can't boot Windows on that machine from that drive without a dynamic drive overlay of some sort. Another good reason not to use Windows. ... :rolleyes: )

---

### Post by Old Pink on 2006-10-07
You should add this thread to your signatue, mate, it's a good one! :D

---

### Post by K.Mandla on 2006-10-07
Good idea! ;)

---

### Post by zek725 on 2006-10-15
What's Openbox? Is it faster than XFCE? How do you install one?

Xubuntu 6.06 on PIII 600Mhz, 384Mb SDRAM, 64Mb Nvidia GeForce TNT2 MX.

---

### Post by John.Michael.Kane on 2006-10-15
K.Mandla Sweet install. alot of those socalled old machines still have alot of life left in them..

@zek725 Openbox is a light-weight window manager. more info here [http://icculus.org/openbox/about.php](http://icculus.org/openbox/about.php)

For howto install it:
[http://ubuntuforums.org/showthread.php?t=103806&highlight=openbox](http://ubuntuforums.org/showthread.php?t=103806&highlight=openbox)
[http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox](http://ubuntuforums.org/showthread.php?t=75471&highlight=openbox)
[http://ubuntuforums.org/showthread.php?t=192106&highlight=openbox](http://ubuntuforums.org/showthread.php?t=192106&highlight=openbox)

---

### Post by K.Mandla on 2006-10-15
> **zek725 said:**
> What's Openbox? Is it faster than XFCE? How do you install one?
MUCH faster, in my opinion. It's also a bit more sparse, and requires a little more command-line savvy to get going, but it's worth it in the end. I have a sweet 1Ghz machine that goes from cold boot to online and browsing in less than 42 seconds with Openbox. The same machine was getting 53 or 54 seconds plus with XFCE. (That's just what I use as an informal benchmark.)

Follow those links SD-Plissken gave you. It's worth learning if you're a fellow speed freak. ;)

@SD-Plissken: Thanks! :mrgreen:

---

### Post by Mike_Longbow on 2007-01-15
Hey K.Mandla.

This is, indeed, a curious situation, but it doesn't matter, hehehe...
Ok, the fact is that Mom just got exactly a laptop of those, and I've been wondering how to install edgy on it.
But the problem is that, being de cd-rom drive a plug-and-play device, the bios doesn't recognize it and it can't boot from it. Also, I can't find a way to get in the bios setup, no key seems works :-k 
So, could you share with my some of your experiences in this install? 
Well... first of all, how did you made it to boot the installer?

Thanks in advance.
Mike

---

### Post by K.Mandla on 2007-01-15
For machines that don't boot from CD, I usually use this:

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

Does that help at all?

---

### Post by Mike_Longbow on 2007-01-15
> **K.Mandla said:**
> For machines that don't boot from CD, I usually use this:

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

Does that help at all?

It would... If I had a floppy drive to boot with :-? 
Anyway, I found a way to boot from a DOS partition, wich the machine already has... but I don't think that could help me if I'm about to install the system from scratch on a blank HDD.
:-k
Maybe if I, somehow, create the partition in the empty drive and install the boot loader in it, using another laptop... Maybe... :-k  But how, exactly?
Anyway, thanks for the reply K. Mandla. You rock when it's about messing with old hardware 8)

---

### Post by K.Mandla on 2007-01-17
A couple of ideas come to mind. First, yank the hard drive and install on a different machine. When you put it back, reconfigure a few things (like the network and the video adapter) and keep your fingers crossed.

Also, there's a (supposed) method to install Linux from inside Windows here: [http://instlux.sourceforge.net/](http://instlux.sourceforge.net/)

There are also instructions on installing from an ISO here: [http://www.ubuntuforums.org/showthread.php?t=316093](http://www.ubuntuforums.org/showthread.php?t=316093)

---

### Post by happy-and-lost on 2007-02-07
Nice one. Makes me wish I hadn't pulled my old 100Mhz P1 laptop to pieces (It was running DSL, mind, I just like OB better than Flux)...

Would you mind posting the .conkyrc in that shot? It'll make a nice change from the monochrome one on the side I've got now :)

---

### Post by K.Mandla on 2007-02-07
Does this work? It's more or less the same thing, shifted to the center and a little smaller.

```
background yes
use_xft yes
xftfont Dejavu Sans:size=9
xftalpha 0.8
update_interval 2
own_window no
double_buffer yes
draw_shades no
draw_outline yes
stippled_borders no
border_margin 0
border_width 1
default_color white
default_shade_color black
alignment bottom_left
minimum_size 1582
gap_x 9
gap_y 9
use_spacer no
no_buffers yes
uppercase no

TEXT
${alignc}${color white}Ubuntu $sysname $kernel ${color darkgrey}on ${color white}$nodename ${color darkgrey}[${color white}${freq}Mhz ${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'}${color darkgrey}] | ${color white}$uptime_short ${color darkgrey}uptime at ${color white}$cpu% ${color darkgrey}cpu load with ${color white}${mem}b${color darkgrey} of ${color white}${memmax}b${color darkgrey} (${color white}$memperc%${color darkgrey}) used by ${color white}$processes ${color darkgrey}processes
${alignc}${color white}${fs_used /}b${color darkgrey} of ${color white}${fs_size /}b${color darkgrey} root partition used, ${color white}${fs_used /home}b${color darkgrey} of ${color white}${fs_size /home}b${color darkgrey} home partition used | ${color white}${downspeed eth1} kbps${color darkgrey} down (${color white}${totaldown eth1}b${color darkgrey} total), ${color white}${upspeed eth1} kbps${color darkgrey} up (${color white}${totalup eth1}b${color darkgrey} total) on ${color white}${addr eth1}
```

---

