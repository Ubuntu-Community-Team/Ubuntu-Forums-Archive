---
title: "Jack MIDI &amp; ALSA tabs"
date: 2009-04-26
forum: Ubuntu Studio
---

### Post by demios on 2009-04-26
k, this is kind of trivial, but I finally got my first interface, a presonus firebox, working today (upgrading to jaunty studio helped alot), but i go and try to use my midi keyboard with it and the midi outputs in jack's connection window are under the MIDI tab, while everything that I'd connect them to is under the ALSA tab, rendering the midi unusable. so I just to get the midi outs over to the alsa tab, or combine the two somehow.

also, seq 24 and hydrogen and stuff crash regularly, is this because I'm running the amd64 install or are they still in development? (I can switch to i386, but I thought I'd try out 64 bit, which is what I think that is... right?)

any help is appreciated.

---

### Post by _nate on 2009-04-27
I have a presonus firebox and am running amd64 version as well but cannot get jack to work properly.  did you have to do anything special to get it going? Also, could you please let me know what settings you are using so I can try it out?  thanks nate

---

### Post by Stochastic on 2009-04-27
To get Jack MIDI to talk to ALSA MIDI (the difference between the two tabs) you'll need to install a2jmidid.  Here's the website: [http://home.gna.org/a2jmidid/](http://home.gna.org/a2jmidid/)
And I've built a quick package in my PPA for Jaunty: [https://launchpad.net/~stochastic/+archive/ppa](https://launchpad.net/~stochastic/+archive/ppa)

As for your crashes, I don't think amd64 is to blame.  Hopefully apport is starting up after each crash and you can send that crash report data into launchpad.net (manually send that data in yourself if it isn't).  Both of those apps shouldn't be crashing.

---

### Post by demios on 2009-04-28
> **Stochastic said:**
> To get Jack MIDI to talk to ALSA MIDI (the difference between the two tabs) you'll need to install a2jmidid.  Here's the website: [http://home.gna.org/a2jmidid/](http://home.gna.org/a2jmidid/)
And I've built a quick package in my PPA for Jaunty: [https://launchpad.net/~stochastic/+archive/ppa](https://launchpad.net/~stochastic/+archive/ppa)

As for your crashes, I don't think amd64 is to blame.  Hopefully apport is starting up after each crash and you can send that crash report data into launchpad.net (manually send that data in yourself if it isn't).  Both of those apps shouldn't be crashing.

unfortunately, due to a wonky situation here, only one computer in the house (a windows machine) works with the internet. it's entirely frustrating having to run to the barn just to upgrade/download programs, but I'll see what I can do.


[QUOTE=_nate]I have a presonus firebox and am running amd64 version as well but cannot get jack to work properly. did you have to do anything special to get it going? Also, could you please let me know what settings you are using so I can try it out? thanks nate [/QUOTE]

I had to do some permissions stuff with groups. I'll get back to you with my settings in jack, but I don't think those affect whether it works or not, just how it works (though, before doing the permissions stuff, I could run the on board sound card in non-realtime). you have to edit /etc/security/limits.conf to include the following three lines:
```
@audio - rtprio 99
@audio - memlock unlimited
@audio - nice -10
```
then, create the user group audio and add yourself to it (it's in the gnome menus somewhere, I don't know how to do it from the command line)
this thread helped me: [http://ubuntuforums.org/archive/index.php/t-453486.html](http://ubuntuforums.org/archive/index.php/t-453486.html)

---

### Post by demios on 2009-05-04
Actually, just remembered that you have to have read and write permissions on /dev/raw1394 -- open nautilus as root (sudo nautilus) then navigate to the file, right click >> properties >> permissions then set up the audio group to have read and write privileges.

You probably found this already, the reason I posted was because I can't figure out how to do it so it takes permanent effect -- I have to do this after every reboot if I want my firewire to work. any help?

---

### Post by Stochastic on 2009-05-05
I've noticed a problem in some upgrades for Ubuntu Studio Controls not setting the right option when the user checks 'enable raw1394'

Essentially, if you've enabled raw1394 in Ubuntu Studio Controls, AND you run both of these ```
grep -H -n raw1394 /lib/udev/rules.d/*
grep -H -n raw1394 /etc/udev/rules.d/*
``` and they both return nothing, then do the following:







- run ```
sudo gedit /lib/udev/rules.d/50-udev-default.rules
```
- add this line anywhere in that file (though under the #Firewire line is probably nicest) ```
KERNEL=="raw1394",              GROUP="video"
```
- save the file and close the program
- run ```
sudo gedit /etc/modules
```
- add this line to the bottom of the file (or make sure it's already in that file somewhere) ```
raw1394
```
- save the file and close the program
- add yourself to a 'video' group (you may need to create this through System->Administration->Users&Groups )
- reboot




Edit: But now this thread is really off topic.

---

