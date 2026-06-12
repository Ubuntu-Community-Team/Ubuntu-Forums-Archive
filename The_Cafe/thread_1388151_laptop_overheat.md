---
title: "laptop overheat"
date: 2010-01-22
forum: The Cafe
---

### Post by sandyd on 2010-01-22
Does anyone have a problem with the dell studio laptops overheating while its closed?
I have to prop my laptop off the table with my calculus textbook just to keep it out of the damaging temperatures

---

### Post by TheNessus on 2010-01-22
happens with my Fujitsu Siemens. I never close it unless its hibernating/off. Only happened to me with ubuntu though, not so with winblows.

---

### Post by Zoot7 on 2010-01-22
What sort of Dell Studio model is it?

My girlfriend has one of the older Dell Studio models with the nine cell battery that props it up at the back, and there's no such temperature problems.

---

### Post by sandyd on 2010-01-22
newest (well not really) i bought it in august. its a 1735

---

### Post by Zoot7 on 2010-01-22
What program are you using to monitor the temperatures? Sometimes there can be a BIG discrepency across them.
If it's prevelent across several temperature monitoring programs and the machine itself gets noticabally hot, I'd shoot them a call.
You can probably be expected to have formatting the hard drive and reloading Windows to be the proposed solution initally, but persevere and ultimately you'll get someone who actually has a clue.

---

### Post by sandyd on 2010-01-22
yup. its the same on multiple sensor programs.
However, i just remembered i disabled intel speedstep because of my mac osx problem.
lets see if guidance power manager will allow me to do adaptive cpu clocking after reenabling it. (no osx though.... :( )

---

### Post by DodgeV83 on 2010-01-22
> **carlee said:**
> Does anyone have a problem with the dell studio laptops overheating while its closed?
I have to prop my laptop off the table with my calculus textbook just to keep it out of the damaging temperatures

While it's closed?  Does your monitor stay on while it's closed by any chance?  My Dell XPS 1330 had this problem, one of the reasons I now choose to run Ubuntu in Virtualbox under Windows 7.  The laptop runs much cooler now too!

---

### Post by sandyd on 2010-01-22
> **DodgeV83 said:**
> While it's closed?  Does your monitor stay on while it's closed by any chance?  My Dell XPS 1330 had this problem, one of the reasons I now choose to run Ubuntu in Virtualbox under Windows 7.  The laptop runs much cooler now too!
oh wait... thats the problem.

although i set it to lock the screen when the monitor's closed, it never shut off the monitor....

---

### Post by DodgeV83 on 2010-01-22
> **carlee said:**
> oh wait... thats the problem.

although i set it to lock the screen when the monitor's closed, it never shut off the monitor....

Welcome to the wonderful world of Ubuntu bugs!

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/449188](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/449188)

[http://ubuntuforums.org/showthread.php?t=1308126&highlight=laptop+lid](http://ubuntuforums.org/showthread.php?t=1308126&highlight=laptop+lid)

Only one of the proposed solutions worked for me:

```
sudo vbetool dpms off
```

However, closing the lid after running this command would sometimes cause the lid to turn on again!  Also, I sometimes would have to push FN + (external monitor button) to get out of it.

The only way I was able to close the laptop lid and be sure the screen stayed off, was to prop up the lid a bit.  Putting the powercord in the way of the lid so it wouldn't stay completely closed worked...sometimes.

I guess you could try turning off the "laptop lid is closed" trigger after running that command, but I've never tried it.

[http://ubuntuforums.org/showthread.php?t=1376544&highlight=laptop+lid](http://ubuntuforums.org/showthread.php?t=1376544&highlight=laptop+lid)

Either way, I was put off enough by this bug to move back to Windows and use Ubuntu in Virtualbox.  Works for me :)

---

### Post by lostinxlation on 2010-01-22
I'd clean the dust on the air flow  path first and see what will happen.

---

### Post by DodgeV83 on 2010-01-22
> **lostinxlation said:**
> I'd clean the dust on the air flow  path first and see what will happen.

With the 2 Dell 13" laptops I've owned, the temperature should go *down* when closing the lid, since the lid partially obscures part of the vent when open, inhibiting air-flow.

While it couldn't hurt, I don't think this is a likely reason (unless her Dell model doesn't work this way).

---

