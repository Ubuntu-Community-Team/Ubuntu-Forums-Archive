---
title: "Help with Latency/CA0106 card/Ardour"
date: 2008-12-09
forum: Ubuntu Studio
---

### Post by cvowen on 2008-12-09
Trying to record a few guitar tracks thru Ardour.
I can't get my latency below 171 msec.thru Jack Control, using a SB Audigy LS card.
Have -RT, Pulse Audio installed and have gone thru the forums to figure it out but I'm stuck.
Frames/Period set at 4096 & Sample rate: 48000, periods/buffer @ 2.
Ticking out realtime, no memory lock or unlock memory doesn't help.
Interface & Input Device...set at default...that works but have tried to set both to either hw:0/hw:00 &/or combinations but Jack xruns all day.
I just want to record a few guitar tracks with Ardour, but when I do the Latency is suckin.
Any help would be appreciated.
Thanks

---

### Post by barisurum on 2008-12-09
You should have these lines at the end of your **/etc/security/limits.conf** file:

@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -19

if they aren't there add them. And you must be a member of the audio group. If there's no audio group create one and make yourself a member.

---

### Post by cvowen on 2008-12-09
audio:x:29:pulse,curtis
this is what I've got for member

---

### Post by cvowen on 2008-12-09
MY /etc/security/limits.conf file after changes:
@audio - nice -10
@audio - memlock unlimited
@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -19

My audio group: audio:x:29:pulse,curtis

Reset Frames/Period = 1024 (changed from before)

Latency now at 42.7 msec

Recorded guitar track to Ardour and the Latency was o.k.?!
Thanks,
Whats up with realtime?
Can I tweak card/Ardour/Jack more?
THANK YOU!!!!

---

### Post by barisurum on 2008-12-09
It is genrally safe to set rt priority to say 80-90 or to default in qjackctl settings.
You may achieve better latency tweaking frames/period, remember that a latency around 10 ms or greater will be audible. Its not a problem when recording one sound though, but you will experience annoying delay when playing softsynths.
And you should delete that extra memlock and nice -10

---

### Post by cvowen on 2008-12-09
Deleted memlock etc.
Realtime doesn't work, but xruns are good.
Put a track down on Ardour, get cut-outs on input (electric guitar), but better recording then before.
Thank you so much!
Regards.,

---

### Post by cvowen on 2008-12-10
I found that I've to start pulse audio and set everything to default server, sink & source for Jack to work at these setting.
Still get the cut-outs when live recording.
On Jack, none of the parameters are ticked off, everything is set to default, buffer 2, port max 512, timeout 10000.

---

### Post by barisurum on 2008-12-10
Does ardour put xrun marks on your recording at the point of cut-outs?
If so you should try with a lower frames/buffers setting.
And you should use your card in realtime mode if you have a realtime kernel installed. Type in a terminal:

> uname -a

and check to see an -rt at the end of your kernel version.
Which version of ubuntu are you using? If its 8.10 then you should read this before anything else: [http://ubuntustudio.org/8-10_release_note](http://ubuntustudio.org/8-10_release_note)
So the rt kernel in 8.10 has known issues and it is not advised to be used at this time. 8.04 with rt would be much better.

---

### Post by cvowen on 2008-12-10
Linux curtis-desktop 2.6.24-22-rt #1 SMP PREEMPT RT Mon Nov 24 20:47:19 UTC 2008 i686 GNU/Linux
Reatime function in Jack parameters causes "could not connect to Jack server as client"
Disregard cutout problem, solved by hardware fix.
Ardour just quits on me, locks up and even closes out...crashes.
Didn't try the "set Pulse Audio to default" trick, but ticked of Interface to hw:0.
Ardour crashed again and noticed that in Jack connections there's nothing listed under Audio in/outs.
Grrrrr.

---

### Post by cvowen on 2008-12-10
o.k. here's what works for awhile (3 minutes) and then Ardour froze up:
Start Pulse Audio First, set everything to "Default" server/sink/source.
Start Jack.
Start Ardour.
Then after the 3 minutes later Ardour freezes and Xruns appear.
Audio connections in Jack where there this time.
Interface: hw:0
Nothing else in Parameters checked. Latency 42.7, frames/period 1024

---

### Post by barisurum on 2008-12-10
Hmm looks like the issues I had before I configured my pulseaudio setup with this thread: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
I had jack crashes before and the instructions fixed it, maybe it helps you too.

---

### Post by cvowen on 2008-12-10
I've done that already. Will work on it tonight. 
Thanks for hanging in there with this problem.
I havn't found a simple solution here on the boards.

---

### Post by markbuntu on 2008-12-11
There is some info about jack and pulseaudio you might want to look at here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by cvowen on 2008-12-15
I did that as well, but I'll go thru it again.

---

