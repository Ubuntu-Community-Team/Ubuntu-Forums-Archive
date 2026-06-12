---
title: "[karmic, starling] fix for wireless failures?"
date: 2010-03-14
forum: System76 Support
---

### Post by tlroche on 2010-03-14
summary: My girlfriend's starling runs UNR 9.10 pretty well, *except* that it occasionally loses wireless entirely. This can be kludged, but not the same way (procedures below). Is there a more permanent fix?

details:

This nearly-new starling (model=star1, System76=2.4.4) shipped with jaunty. I attempted to upgrade it to karmic using Update Manager per the [wiki directions]("http://knowledge76.com/index.php/KarmicUpgrade") but [failed]("http://ubuntuforums.org/showpost.php?p=8702320&postcount=1") , so I did a [fresh install of karmic and System76]("http://ubuntuforums.org/showpost.php?p=8714199&postcount=5") which worked. Since then the starling has run fine, ***except*** that, every few weeks, it loses wireless entirely: no connections in Network Manager, wireless LED goes off.

This can be kludged, but not the same way. Sometimes
[LIST=1]
[*]Twiddle the hardware WiFi/3G switch: pull it to the right, release,let it pop back.
[*]Shutdown.
[*]Restart.
[/LIST]
works, sometimes not. Other times
[LIST=1]
[*]Cable in starling, wait for autoconnect.
[*]System>Administration>System76 Driver>Install Drivers>Install
[*]Shutdown.
[*]Restart.
[/LIST]
works, sometimes not. Today I did the first procedure, which failed, then the second procedure, which failed, then the first procedure again, which worked.

Is there a more permanent fix?

---

### Post by PatrickVogeli on 2010-03-14
when this happens, you may try doing, in a terminal:

sudo service network-manager restart

---

### Post by thomasaaron on 2010-03-15
Kernel updates should no longer break the Starling's wireless in 9.10. So running the System76 Driver probably isn't necessary.

You had the right idea with moving the wireless/3G switch ONCE to the right, releasing it and rebooting.

It sounds like the switch is accidentally getting toggled... maybe in the carrying case or something.

---

