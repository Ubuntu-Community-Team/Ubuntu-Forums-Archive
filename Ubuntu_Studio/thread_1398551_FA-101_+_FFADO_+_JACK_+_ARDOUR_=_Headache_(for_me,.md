---
title: "FA-101 + FFADO + JACK + ARDOUR = Headache (for me, anyway)"
date: 2010-02-04
forum: Ubuntu Studio
---

### Post by crau2 on 2010-02-04
I am looking for someone, *anyone*, who uses an Edirol FA-101 with **Ubuntu Studio** (I use 64-bit, but I'm sure that doesn't matter, eh?) to multitrack live instruments.  

I can't get FFADO to play nice with JACK...  
Without JACK I have no Ardour...  
Without Ardour I just have a FA-101 paperweight... 

Can anyone give me the quick and dirty guide on making this all work?  Please?

I can pay you in awe and admiration.

---

### Post by bluesscream on 2010-02-04
Hi Crau2:
My private checklist when jackd/ffado will not run at all:
0. run ffadomixer. If it shows the gliders goto 4.
1. Run ubuntustudio-controls with all options defaults marked
2. control files manually: /lib/udev/rules.d/50(or an other number)-udev-default-rules: is there a line 'KERNEL=="raw1394", GROUP="video"' (mostly near the end of the file)?
ls -l /dev/raw1394 should be like 'crw-rw---- 1 root video 171, 0 2009-11-26 09:56 /dev/raw1394. reboot
3. has user rights for audio and video? (system/administration/users and groups/myuser/properties/user rights). In earlier versions this was done by adding user to groups. If ffadomixer still shows no device goto 10.a.
4. make sure /etc/security/limits.conf contains a line '@audio - rtprio 99'
5. does jackd run with alsa? with rt unmarked? with low performance settings? Explicitely the internal soundchip selected? if not at all goto 10 b
6. reset fw device, make sure the same samplerate is selected as in qjackctl.
7. try lower priorities in jack i.E. default(=10)
8. Is cpu frequency set to full speed - 'userspace max' or 'perfomance' for each core?
9. Have a look into system-monitor-applet - are there zombie-processes of jackd or other stopped programmes?
10. If it's still not running, completely remove a. ffado b. jackd, with all configurations, consult the howtos and install them new.
Please post your qjackctl's messages

---

### Post by crau2 on 2010-02-05
Thanks (Vielen Dank)...  That helped A LOT! I can record multiple tracks now...  Record being the optimal word.

I set up an experiment and recorded 10 separate inputs into the FA-101...  I can see that Ardour recognizes and records 10 distinctly different signals, however...

When I attempt to play them back I get silence (the monitor bars move showing it *IS* doing something)...

When I export track as a .wav and playback in Audacious2 I get silence...

All other sounds on the machine work fine.  Got any other fixes up your sleeve?

-- 
Vielen Dank für Ihre Hilfe

---

### Post by crau2 on 2010-02-05
for all those noobs in linux firewire/audio limbo...

bluescream's quick & dirty tutorial is great, don't get me wrong...  But if you need a quicker & dirtier guide look no further than here:

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

viva la community!

---

