---
title: "Problem with  UCG102 USB Guitar Interface"
date: 2012-10-28
forum: Ubuntu Studio
---

### Post by robtnix on 2012-10-28
I've gotten the UCG102 working under Ubuntu 12.10, using qjackctl and  rakarrack, but had issues with latency.  So I thought I'd try out Ubuntu  Studio from the livecd. And I can't get it to work.   Any help would be  appreciated.

I'm guessing that if I could just connect  everything correctly I'd be fine, but I just can't figure it out.   I  see that after I configure and run jack using qjackctl, and then run  either rakarracl or guitarix, that lots of  connections get made.  But  neither gets a signal from my guitar.  It does get input from the  builtin microphone of my computer (Thinkpad 420s FWIW).

I'd really appreciate any help getting this to work! Does it have anything to do with ubuntu studio's using pulse audio?

Here's a bit more info in case it's of use.

#output of aplay -l
ubuntu-studio@ubuntu-studio:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

#output of arecord -lubuntu-studio@ubuntu-studio:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by sgx on 2012-10-28
Hi, looking at qjackctl Setup page Input Device > 
click the   >  does 'USB Audio CODEC' or 'USB Audio' appear?

If not, try typing that in, (with no quotes or brackets)
and restart qjackctl.

Periods/Buffer setting should be 3 for a usb input device.

killall pulseaudio

use top, htop, or command

ps ux

to see if anything with pulse in the name is running.

also, look at this solution info:

[http://ubuntuforums.org/showthread.php?t=1457334](http://ubuntuforums.org/showthread.php?t=1457334)

Cheers

---

### Post by mahavishnu on 2012-11-11
Try executing the content of  ~/.jackdrc file from command line and then start qjacktcl.

---

