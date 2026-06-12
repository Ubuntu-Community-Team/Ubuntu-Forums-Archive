---
title: "Screen power down completely"
date: 2009-03-08
forum: Ubuntu Brainstorm
---

### Post by Brinstar on 2009-03-08
A minor complaint with Ubuntu i have had for as long as i have been an Ubuntu user still hasn't been addressed, when the screen powers down, it doesn't switch off completely. This is one thing that Microsoft did right in XP. Can we get the same behaviour for Ubuntu?

I think I have explained it fine, but if further explanation is needed, then i can be more specific.

---

### Post by smartboyathome on 2009-03-08
This is more likely a driver-specific issue than an Ubuntu-specific one. What video card does your machine use?

---

### Post by Brinstar on 2009-03-09
> **smartboyathome said:**
> This is more likely a driver-specific issue than an Ubuntu-specific one. What video card does your machine use?

its not driver-specific as i have owned several computers and laptops with various graphics cards from all 3 major brands, and the same exact issue occurs on all of them. Currently though, its an Intel GMA950, though i also have a ATI X1100 with the same problem.

---

### Post by smartboyathome on 2009-03-09
Perhaps talk to the [Xorg team]("http://lists.freedesktop.org/mailman/listinfo/xorg") and see if they can help? Xorg is the X server which is used on Ubuntu.

---

### Post by Brinstar on 2009-03-10
after some digging, i have found that this problem has been reported about 3 YEARS AGO, but sadly and unsurprisingly nothing has been done about it.

This is unfortunately the reality in the linux community. yes, things do eventually get done, but it takes YEARS for someone to do something about the problem once it has been reported. 

kind of ties in with what i was saying about wine, its works, its here today, people are not going to wait for a linux alternative to show up, they want to get stuff done TODAY.

Edit: has something to do with the DPMS option in xorg, see below, copied from mepis support forum

> Turning off lcd monitor backlight
Submitted by inkscarab on Tue, 08/29/2006 - 13:17. Other video cards
Posts: 5

I have scoured google for a solution to my problem but as yet have not had any success... here's the issue. I have set KDE to use power management for the monitor and to turn off the monitor after x minutes. Once x minute arrives, the monitor turns black, but the backlight does not turn off. To try and determine the problem, I issue these commands:

xset dpms force off - results in same blank screen backlight still on
vbetool dpms off - results in backlight turning off (this is the desired behavior)

I had also tried to edit xorg.conf to set dpms on and set time to blank with no success.

Apparently, the hardware is capable of turning off the monitor backlight, but xset or KDE's power management isn't doing so properly.

My issue then is how do I get the backlight to go off with xset or KDE's power management OR how do I write a script to monitor how long the screen saver has been on and invoke the vbetool command to turn it off and subsequently monitor for mouse/keyboard activity (or screensaver termination if that is still monitoring activity) and invoke vbetool dpms on?

Any solution to this problem will help more than just myself from what I see in my searches!

---

### Post by smartboyathome on 2009-03-10
Ok, if you are so unsatisfied with it, fix it yourself. You have the source code available to you. All you need to do is start programming.

Linux is run by the community, and so if no one wants to fix this bug, they don't. If you want, you can even hire someone to fix the bug for you, so that it can be fixed.

---

### Post by a fenderson on 2009-03-10
> **smartboyathome said:**
> Ok, if you are so unsatisfied with it, fix it yourself. You have the source code available to you. All you need to do is start programming.

Linux is run by the community, and so if no one wants to fix this bug, they don't. If you want, you can even hire someone to fix the bug for you, so that it can be fixed.

I really hate this attitude.  Not everyone who uses free software is a programmer, nor should they be expected to be one.  It's perfectly legitimate to bring attention to a problem, especially if it seems like it's been forgotten about.

---

### Post by smartboyathome on 2009-03-10
> **a fenderson said:**
> I really hate this attitude.  Not everyone who uses free software is a programmer, nor should they be expected to be one.  It's perfectly legitimate to bring attention to a problem, especially if it seems like it's been forgotten about.

I know that not everyone who uses it is a programmer, but the problem is that many seem to think that the programs that don't run on it are because it sucks (at least, that is what I got out of that post). It is really because there are a lack of developers.

I did give a suggestion for those who can't program and still want their bug fixed quickly, and that was hire a program to fix the bug for you.

---

### Post by BGFG on 2009-03-11
> **a fenderson said:**
> I really hate this attitude.  Not everyone who uses free software is a programmer, nor should they be expected to be one.  It's perfectly legitimate to bring attention to a problem, especially if it seems like it's been forgotten about.

And I really hate this attitude. So many leeches who contribute nothing, got an Operating System and access to thousands of apps for FREE, but as soon as one (and in this case, near insignificant) thing does not please them or meet their exact needs, they begin taking pot shots at programmers who at their own cost, dedicate millions of hours of time and effort to making things work for us non programmers.

Smartboy is right. If it's that important to you, rather than being another worthless ranter. why not simply politely raise the 'bug' again with the relevant team in the relevant channel ?

but no, you guys are entitled to first class ASAP support by birthright, right ? or maybe you paid and received a support contract.

Contribute. if you can't then politely request. if you can't then say thank you. if you can't then shut up.

---

