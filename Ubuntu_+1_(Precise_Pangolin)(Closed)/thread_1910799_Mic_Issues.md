---
title: "Mic Issues"
date: 2012-01-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by clivejo on 2012-01-17
Im having issues with my mic under 12.04.  Basically I cant use it at all, any ideas ow to fit it?

---

### Post by xyzzyman on 2012-01-17
Did you remove the test version of pulseaudio from the headphone jack tests and rollback to the regular repository versions?

---

### Post by clivejo on 2012-01-17
I did a ppa-purge on it, is this enough?

---

### Post by xyzzyman on 2012-01-17
If it did it right. ppa-purge for me was wanting to remove alot of packages that it wasn't going to replace, and looked like it was going to break alot of things. That's the life of running an early alpha. lol David Henningsson who is working on the headphone jack project at Canonical emailed me and I replied with the different issues with PulseAudio server crashing upon running and some of the log files, and waiting back for a response on what other information he'll need. Alsamixer still sees the card and lets me adjust values so it appears it's not a problem with the test kernel itself. I'm kind of disappointed that more people didn't reply to their call for testers as that would be a great feature for them to backport.

---

### Post by clivejo on 2012-01-18
> **xyzzyman said:**
> If it did it right. ppa-purge for me was wanting to remove alot of packages that it wasn't going to replace, and looked like it was going to break alot of things. That's the life of running an early alpha. lol David Henningsson who is working on the headphone jack project at Canonical emailed me and I replied with the different issues with PulseAudio server crashing upon running and some of the log files, and waiting back for a response on what other information he'll need. Alsamixer still sees the card and lets me adjust values so it appears it's not a problem with the test kernel itself. I'm kind of disappointed that more people didn't reply to their call for testers as that would be a great feature for them to backport.

Just been in Synaptic.  Yes, your right, some of PulseAudio has been rolled back and other packages havent.  Its a right mess!  Tried to force version of libpulse0, it wants to remove a ton of packages which would render my system borked!  Now Im in a pickle!  Do I wait for the Jack Detection guys to fix the issues or do a reinstall !!  I dont have enough internet allowance this month to download an iso :(

---

### Post by mc4man on 2012-01-18
ppa-purge worked out ok here - what you should do is carefully gather all the PP packages you still need downgraded, put them in a folder, cd to the folder & run

sudo dpkg -i *.deb

Make sure you have them all, if you happen to get an install error or broken packages just read the terminal carefully & get the missing package, put in folder & re-run the command till it's right.

You should be able to retrieve what you need from here
[http://packages.ubuntu.com/source/precise/pulseaudio](http://packages.ubuntu.com/source/precise/pulseaudio)

---

### Post by clivejo on 2012-01-18
> **mc4man said:**
> ppa-purge worked out ok here - what you should do is carefully gather all the PP packages you still need downgraded, put them in a folder, cd to the folder & run

sudo dpkg -i *.deb

Make sure you have them all, if you happen to get an install error or broken packages just read the terminal carefully & get the missing package, put in folder & re-run the command till it's right.

You should be able to retrieve what you need from here
[http://packages.ubuntu.com/source/precise/pulseaudio](http://packages.ubuntu.com/source/precise/pulseaudio)

Done, everything back to normal.  But still no mic!!  In Sound Settings I can see the Internal Audio Analogue Stereo but when I plug in my mic in can not hear it or see the meter moving.  Same with Video Grabber Audio which I know is working too as I can hear it in mplayer direct from alsa:hw2,0

---

