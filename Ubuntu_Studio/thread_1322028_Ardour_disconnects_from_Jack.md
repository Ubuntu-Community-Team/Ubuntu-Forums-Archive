---
title: "Ardour disconnects from Jack"
date: 2009-11-10
forum: Ubuntu Studio
---

### Post by fabiotheimpaler on 2009-11-10
Hey, I'm having a bit of a problem.  I just upgraded to Karmic, and my Ardour randomly disconnects from Jack and gives me this message:
[INDENT]JACK has either been shutdown or it
disconnected Ardour because Ardour
was not fast enough. Try to restart
JACK, reconnect and save the session.[/INDENT]
Then I get an Xrun on JACK, and I can't reconnect.  I then get this in the Ardour log:
[INDENT][ERROR]: could not reconnect system:capture_2 and ardour:Audio 3/in 1 (err = -1)
[ERROR]: could not reconnect system:capture_1 and ardour:Audio 3/in 2 (err = -1)
[ERROR]: could not reconnect ardour:Audio 3/out 1 and ardour:master/in 1 (err = -1)
[ERROR]: could not reconnect ardour:Audio 3/out 2 and ardour:master/in 2 (err = -1)
[ERROR]: Ardour's audio engine is not connected and state saving would lose all I/O connections. Session not saved[/INDENT]

Any suggestions?

---

### Post by homerj742 on 2009-11-11
Funny, I've been experiencing similar issues, though i'm using 8.04 release...

It just started happening out of the blue...

---

### Post by markbuntu on 2009-11-11
You can try adjusting the timeout in jack control/setup to 1000-5000 so jack does not go to sleep.

---

### Post by NewAgeGuitarist on 2009-11-13
I was having the same problem the other day and, as usual, the problem was a Ladspa plugin.  In my case it was Freeverb version 3.  There have been problems with the tap plugins and various others in the past causing this same issue with Ardour, and even if added into Hydrogen right now, Freeverb 3 will cause serious xruns.  You can try disabling your plugins to see if that stops your issue and then activate them one by one to find the offending plugin.

I hope this helps, and if not please let us know if you solved your problem and how you did it, so this thread might be of use to others who are having this problem.

---

### Post by homerj742 on 2009-11-13
That makes sense, come to think of it, these problems started happening after I started messing with the plugins.

---

### Post by bluesscream on 2009-11-13
I guess there is a problem in cpu frequency scaling governor ondemand, seems to adjust frequency too slow or to late. There are two ways to fix this: 1. use gnome cpu frequency scaling panel applets and set to max userspace frequency. This will lead to a hot notebook and much fan noise. You have to do this every time you need full realtime audio performance.
2. manipulate ondemand up_threshold by editing /etc/rc.local:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
(sleep 2 && echo 20 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold) & 
(sleep 2 && echo 20 > /sys/devices/system/cpu/cpu1/cpufreq/ondemand/up_threshold) & 
#echo 20 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/up_threshold
#echo 20 > /sys/devices/system/cpu/cpu1/cpufreq/ondemand/up_threshold
exit 0
```
No warranty! But this did the job for me to get full performance for heavy load jackd ardour/rakarrack/zyaddsubfx/hydrogen/linuxsampler, wine/wineasio/reaper/vsti etc. without crashes but acceptable latencies and just a few xruns only at users control inputs. Even the temperatures and fan noise are better on my notebook then in the first option
But again: You might do this on your own risk, this may affect your hardware, no warranty.
Control the temperatures.

---

### Post by fabiotheimpaler on 2009-11-16
Well, I tried adjusting the Jack timeout setting, and it hasn't crashed yet.  However, now that I'm thinking about it, it usually crashed while I was playing with the pan and a Freeverb'd track.

---

