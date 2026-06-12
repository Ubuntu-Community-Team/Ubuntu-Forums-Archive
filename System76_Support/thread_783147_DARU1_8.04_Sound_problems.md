---
title: "DARU1 8.04 Sound problems"
date: 2008-05-05
forum: System76 Support
---

### Post by esundstr on 2008-05-05
I upgraded to hardy and I lost sound control using the switch on the side of my daru1.  Then after a restart I lost all sound, I'm not sure if these two things are actually related.  Any help would be appreciated.  Thanks.

---

### Post by thomasaaron on 2008-05-05
Go to a terminal and run this:
sudo apt-get install linux-backports-modules-generic

That should fix your hardware switch. Might fix the sound in general too.
Double-click your sound icon and make sure nothing is muted.

---

### Post by esundstr on 2008-05-05
Ok I found the sound settings and got the sound working again but as far as the switch goes I tried your command and got:

esundstr@ubuntu:~$ sudo apt-get install linux-backports-modules-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-generic


Thanks

---

### Post by thomasaaron on 2008-05-06
Hi, sorry about that. I was thinking of a different problem.
If the wireless LED is not working on your older (white) darter, though, you might run this...


sudo apt-get install linux-backports-modules-hardy 

As for the little sound control switch on the side, that was reported as a bug previously...

[https://bugs.launchpad.net/system76/+bug/217070](https://bugs.launchpad.net/system76/+bug/217070)

However, it turned out that it was either fixed by updating the system, or the user overlooked a setting in the sound control settings.

---

