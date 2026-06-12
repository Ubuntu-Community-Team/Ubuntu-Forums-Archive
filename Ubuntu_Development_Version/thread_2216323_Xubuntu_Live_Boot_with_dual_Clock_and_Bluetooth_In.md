---
title: "Xubuntu Live Boot with dual Clock and Bluetooth Indicators?"
date: 2014-04-11
forum: Ubuntu Development Version
---

### Post by spsf2 on 2014-04-11
Attachment says it all...

---

### Post by slickymaster on 2014-04-11
There's an already [reported bug in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/xfce4-indicator-plugin/+bug/1302571") that address the misbehavior of the xfce4-indicator-plugin in Trusty. Please access the bug report with SSO account and click the _**This bug affects 10 people. Does this bug affect you?**_ link as affecting you.

---

### Post by pqwoerituytrueiwoq on 2014-04-11
what about the extra clock?

---

### Post by slickymaster on 2014-04-11
Have you tried to restart the panel to check if it's still showing the same issue?```
xfce4-panel -r
```

---

### Post by slickymaster on 2014-04-11
OTH, OP issue might not be at all related to said bug. Presently xubuntu-meta holds in -recommends multiple bluetooth stacks. See bellow:
[ATTACH=CONFIG]251936[/ATTACH]

---

### Post by mc4man on 2014-04-12
It seems to be fairly simple (mentioned elsewhere).
Xubuntu ships with unity-control-center/unity-settings-daemon

u-c-c now deps on several indicators which *can* cause them to show up in the panel, so then for instance you could see blueman & indicator-bluetooth, ect., ect.
(- I don't know Xubuntu well enough to know why it's including u-c-c & u-s-d

---

### Post by Elfy on 2014-04-13
We're trying to get these recommends changed to suggests - though given the *enormous* size of the team it's not as easy as it could be. 

Things changing elsewhere are having undesired effects on us :(

---

### Post by spsf2 on 2014-04-13
I just can't believe in this, tested the live iso from today (apr/13) and guess wthat?!
I just not only have 2 bluetooth indicators, but ALSO 2 clocks...!!!??? The (new) one wich is related to "indicator plugin" is nice, but has options that do not work at ALL
Come on *ubuntu developers, we are only 5 days to final release and you keep changing/adding packages...
This way, the xubuntu 14.04 date/time/sound/bluetooth will be just another fiasco like what happened to 13.10.
Sorry for this rant, but i really like xubuntu, and would like to have a polished final product to show/install on friends machines.
Hope you guys get this fixed

[ATTACH=CONFIG]252025[/ATTACH]

---

### Post by spsf2 on 2014-04-14
Any news on this? Even with latest updates I still have 2 clocks and 2 bluetooth indicators... :(

---

### Post by pqwoerituytrueiwoq on 2014-04-14
you can hide the extras/duplicates right click the indicator applet -> preferences
hopefully it is fixed by the 17th, the bug is by no means a deal breaker

---

### Post by Elfy on 2014-04-14
> **spsf2 said:**
> Any news on this? Even with latest updates I still have 2 clocks and 2 bluetooth indicators... :(

The latest updates don't include anything that would affect this. 

You can see what bugs have been fixed and which are still waiting fixes at the blueprint - [https://blueprints.launchpad.net/ubuntu/+spec/xubuntu-t-bugs](https://blueprints.launchpad.net/ubuntu/+spec/xubuntu-t-bugs)

The only one left not Fix Released is the black screen on suspend.

---

### Post by spsf2 on 2014-04-14
> **pqwoerituytrueiwoq said:**
> you can hide the extras/duplicates right click the indicator applet -> preferences
hopefully it is fixed by the 17th, the bug is by no means a deal breaker
Thanks, it actually does work, let's hope it gets fixed for final release

---

### Post by spsf2 on 2014-04-14
> **Elfy said:**
> The latest updates don't include anything that would affect this. 

You can see what bugs have been fixed and which are still waiting fixes at the blueprint - [https://blueprints.launchpad.net/ubuntu/+spec/xubuntu-t-bugs](https://blueprints.launchpad.net/ubuntu/+spec/xubuntu-t-bugs)

The only one left not Fix Released is the black screen on suspend.
Thanks for the link Elfy. But you mean the latest iso (from april 13th) does not have this bug?
Because it shows bluetooth and clock icons doubled on 2 different boxes I have here...

---

### Post by Elfy on 2014-04-14
I never said that :)

The new build will be along shortly - it will show up on [http://iso.qa.ubuntu.com/qatracker/milestones/314/builds](http://iso.qa.ubuntu.com/qatracker/milestones/314/builds)

When you're looking at that you can report results too - the more results we get the happier we will be.

---

### Post by spsf2 on 2014-04-14
> **Elfy said:**
> I never said that :)

The new build will be along shortly - it will show up on [http://iso.qa.ubuntu.com/qatracker/milestones/314/builds](http://iso.qa.ubuntu.com/qatracker/milestones/314/builds)

When you're looking at that you can report results too - the more results we get the happier we will be.
Thanks! :D

---

