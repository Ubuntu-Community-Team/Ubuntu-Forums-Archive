---
title: "Sound Juicer causes hard crash"
date: 2007-04-20
forum: System76 Support
---

### Post by klato on 2007-04-20
So I've got a few CDs laying around (or is it lying? I always mess that one up..) and I figured I'd rip these bad boys onto my Gazelle Perf.  Popped the CD in, nothing happened.  Opened up Sound Juicer...task bar said "Starting up Sound Juicer"...and then disappeared.  I tried it multiple times, but always the same thing.

Then I rebooted, this time saw an "Audio CD" icon on my desktop.  Cool, so I started up Sound Juicer.  Crap, the Title/Artist fields are reversed.  Ok, I cleaned it up.  Then I added an MP3 gstreamer profile as per the Ubuntu wiki.  Hit extract, and BOOM, my mouse stops, everything stops.  No ctrl+alt+backspace, no crtl+alt+del, no ctrl+alt+f1, NADA.  I had to turn it off hardcore with the power button.

My questions are two:

1) What's up with Sound Juicer?  It worked fine on my old laptop.

2) How harmful is it to my laptop to just hit the power button and shut it off like that?

Thanks!

---

### Post by crichell on 2007-04-20
Wow - the same thing happened to me today exept that it was after Sound Juicer finished ripping (I rarely rip cd's but I just happened to today.)

> 1) What's up with Sound Juicer? It worked fine on my old laptop.

Are you running Feisty?  - I didn't experience it before but I don't really remember if I ripped any CD's during Edgy.  BTW - This was causing CPU softlocks and errors that my hard drive wasn't ready to except commands.

> 2) How harmful is it to my laptop to just hit the power button and shut it off like that?

My crash wasn't as hard - I could slowly close windows and eventually shutdown.  It's not the best but you should be fine.

Anyone know if there is launchpad bug on this?

---

### Post by klato on 2007-04-20
Nope, I'm still running Edgy.

---

### Post by klato on 2007-04-30
bump...i still can't rip any cds...sound juicer just hardcore locks up my system... :(

also, i just tried using Grip, and THAT locked up too...

---

### Post by aidanr on 2007-04-30
> **klato said:**
> 2) How harmful is it to my laptop to just hit the power button and shut it off like that?

if you have to do a hard reboot do it like [this]("http://en.wikipedia.org/wiki/Magic_SysRq_key"), it'll work so long as you haven't gotten a kernel panic, and your harddrive and data will thank you for it

sorry haven't got any input on the sound juicer problem

---

### Post by klato on 2007-04-30
cool thanks for that info.  didn't know that kind of stuff was possible

---

### Post by thomasaaron on 2007-04-30
I'm running Feisty on a Darter.
Just burnt an ISO.
No problems.

Maybe you should upgrade?

Best,
Tom

---

### Post by tptak on 2007-05-04
It's not about burning - it's about ripping the cd.
I've got a bit different problem. While ripping the CD (I'm trying to get my entire collection in ogg), Sound Juicer takes a lot of CPU (up to 100%), so everything else works much slower, even stops reacting (turns grey for a long time or until I kill it).
I'm having Feisty on AMD64 3500 (around 2,2GHz). The XGL is on.

---

### Post by klato on 2007-05-06
cI think it might be a bigger issue for me.  I just tried even burning a CD using CD/DVD Creator and that program locks up too.  My drive is recognized in Places as "CD ROM 1" which I guess isn't correct as it should be a DVD/CD-RW drive...

Also, when I put a blank cd in the drive, nothing appears on my desktop.  I've absolutely no idea how to go about fixing this...

---

### Post by thomasaaron on 2007-05-07
1. Try re-seating  your drive. There is a single screw on the bottom (not the one in the deep-recessed hole, but the one beside it. Pull the drive out (it should come out pretty easily). Re-insert it and replace the screw.

Does this fix the problem?

2. In a terminal, type:     cat /etc/fstab > ~/Desktop/fstab
It will put a file on your desktop that you can copy and paste.

3. In a terminal type:
tail -f /var/log/messages
This will create a live log in the terminal.
Remove the disk from the drive. Then re-insert it and close the drive door.
Let me know what message you see appended to the bottom of the log.

I will compare the results with a known good Gazelle Value.

Best,
Tom

---

### Post by RhysU on 2007-05-24
I am experiencing the same problems.  Soundjuicer causes a hard crash on rip or play.  Grip causes a hard crash on rip (haven't tried play).  The problem is consistent across two separate CDROM drives (the first drive gave me IO errors in /var/log/messages so I've tried a new one that does not).  The same CDROM drives can both read data CDs without any problems.

My system started as Dapper and was upgraded to Edgy.  The exact same drive/gstreamer settings (audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001 ! id3v2mux) worked beautifully in the past under both major versions.  Not sure what has changed in Edgy or what changes I've made to cause this.

My /etc/fstab looks like:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>                               <dump>  <pass>
proc            /proc           proc    defaults                                0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=d179661b-271d-42f2-a174-7c179e22abfb / ext3 defaults,errors=remount-ro,acl 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=f519a60d-deda-4eca-8ec9-b8bfd53bc7da none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto                         0       0
/dev/sdb1           /media/usbdisk      vfat    rw,user,nosuid,nodev,async,quiet,shortname=mixed,gid=100,umask=077,iocharset=utf8 0 0
/dev/sdb2           /media/ipod         vfat    rw,user,nosuid,nodev,async,quiet,shortname=mixed,gid=100,umask=077,iocharset=utf8 0 0
/dev/sdb3           /media/ipod-1       hfsplus rw,user,nosuid,nodev,gid=100 0 0


I see no output in either /var/log/messages or /var/log/syslog when I insert a CDROM and cause Soundjuicer to lock up.  After starting to rip, it takes maybe 30 seconds for the system to freeze fully.  Soundjuicer's UI locks before that, but killing Soundjuicer's process does not prevent the full system crash.

Any suggestions for what now?  Seems like focusing on getting the CD playing to work is the first order of business, but I'm not sure where to start futzing to get that to happen...

Thanks,
Rhys

---

### Post by kubilus1 on 2007-09-18
Upgraded Dapper to Edgy.  Lots of CD Burner problems.  Try to burn CDs=Lockup.  Try to rip with Sound-Juicer=Lockup.  What's going on here?

---

### Post by RhysU on 2007-09-18
I was never able to fix the problem through software.  I started suspecting my CD-ROM drive and replaced it with a newer CD/DVD-RW.  After that, I've not had any issues.

---

### Post by thomasaaron on 2007-09-19
Run your System 76 driver.

Also, if you are using a DarU1 or a black Gazelle Value, you should email me at support. There is a firmware upgrade you need to apply.

---

