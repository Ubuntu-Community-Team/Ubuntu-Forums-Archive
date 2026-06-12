---
title: "new tools in 16.04"
date: 2016-04-12
forum: Ubuntu, Linux and OS Chat
---

### Post by him610 on 2016-04-12
Some of you may already know of it, but I have recently become aware of a new tool available in 'buntu 16.04 for hardware discovery and investigation of problems in one's system. 

It was not in LTS 14.04, but has been included in pre-release versions of LTS 16.04. The new tool, ported over from OpenSuse and run from the command line, is "hwinfo"

I encourage any of you who may be interested to investigate the capabilities of "hwinfo"

---

### Post by philinux on 2016-04-12
I think it needs installing first.

```
sudo apt install hwinfo
```

I seem to recall installing this in previous releases.

---

### Post by ajgreeny on 2016-04-12
It's not available in normal repos for 14.04.

I can't comment on other versions later than that apart from 16.04 which I use in VBox.

How much better is **hwinfo** than using **lshw**, and perhaps piping the output to an html file with command ```
sudo lshw -html >hardware.html
``` which gives a huge amount of info.

Or what about **hardinfo**, which is available for 14.04, though I've not used it?

---

### Post by vasa1 on 2016-04-12
According to [https://launchpad.net/ubuntu/+source/hwinfo](https://launchpad.net/ubuntu/+source/hwinfo), versions are in Precise (supported), Wily (current), and Xenial (pre-release).

---

### Post by deadflowr on 2016-04-12
> Or what about hardinfo, which is available for 14.04, though I've not used it?
It's also graphically called System Profile and Benchmark,
for anyone interested.

---

### Post by Rocky_Bennett on 2016-04-12
Thanks guys. Good info here.

---

### Post by grahammechanical on 2016-04-12
This command will put in the home folder an HTML file called hardwareprofile.html. It can be read in a browser

```
sudo lshw -html >hardwareprofile.html
```

Another utility to install is inxi. An example.

> graham@sdb7-Dev:~$ inxi -A
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller driver: snd_hda_intel
           Card-2 NVIDIA GT216 HDMI Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-18-generic




As the Ubuntu manpages site is down & there does not seem to be anything in the Ubuntu wiki about inxi, I give you this

[http://smxi.org/docs/inxi.htm](http://smxi.org/docs/inxi.htm)

Regards.

---

### Post by him610 on 2016-04-13
> Another utility to install is inxi.
Yep, I use that too along with *lshw* and *hardinfo*. I first found *inxi* referenced in the Linux Mint forum awhile back. One can never have too many tools.

---

### Post by mastablasta on 2016-04-15
is hwinfo the same one a sin windows? with real time monitoring and such?

---

### Post by him610 on 2016-04-15
> is hwinfo the same one a sin windows? with real time monitoring and such?
I am not that familiar with windows tools so I can not answer your first question. *hwinfo* is run from the command line and provides a snapshot of one's detailed hardware information.

---

