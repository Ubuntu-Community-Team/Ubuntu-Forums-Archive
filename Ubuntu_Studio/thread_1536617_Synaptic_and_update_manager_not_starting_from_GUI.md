---
title: "Synaptic and update manager not starting from GUI"
date: 2010-07-22
forum: Ubuntu Studio
---

### Post by raymondvillain on 2010-07-22
Running Ubuntu Studio, 64 bit, "Ubuntu, with Linux 2.6.32-23-preempt".

All of a sudden Synaptic and Program Manager will not start by using the mouse to click on "system>administration>program manager" or "system>administration>synaptic package manager".

But I can (and have) run them successfully from a terminal window, but the system is slow to respond and indicates something is amiss:

user@COMPUTER_NAME:~$ sudo synaptic 
sudo: unable to resolve host COMPUTER_NAME

or

user@COMPUTER_NAME:~$ sudo package-manager
sudo: unable to resolve host COMPUTER_NAME



Has this happened to anyone else?

Any suggestions?

I've been using ZynAddSubFX, jack, and Rosegarden.  Haven't had any problems  with them, but this morning, for some reason, update manager started automatically after I booted and then it "hung".  Had to reboot, after which I tried to run it manually, to no avail.  Then I thought I would re-install it using synaptic and discovered that synaptic also would not start.  Other applications are starting as expected.  Clicking on Synaptic or Update produces a "waiting cursor" for the longest time, which eventually vanishes and the expected program does not start.

---

### Post by Pablo_F on 2010-07-22
Hi Raymond, 

I suggest you use xkill to force quit the  non responsive window. Just do:  ALT+F2 and write: "xkill" then click inside the frozen window. If you try and don't have anything to xkill, rigth click to escape. Or else, in gnome there is an applet "force quit" that you can add to the panel (right click on the panel, add to panel...).

As for the actual problem, have you tried searching the ubuntu forums? 
I made a quick search and found this:
 [http://ubuntuforums.org/showthread.php?t=1174584](http://ubuntuforums.org/showthread.php?t=1174584)

So something might be wrong in your /etc/hosts file and you should fix that.

Cheers! Pablo

---

### Post by raymondvillain on 2010-07-22
Yes, that was it.  Thank you, Pablo_F.  Easily fixed.

Next time I will indeed search the forums more carefully before crying for help.

These forums are great!

I'm going to mark this one solved.

---

