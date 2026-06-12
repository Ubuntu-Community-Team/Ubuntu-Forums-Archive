---
title: "Counterstrike Source Debugging"
date: 2009-07-09
forum: Wine
---

### Post by NagWolf on 2009-07-09
Hi,
I've got Ubuntu 9.04, CrossOver Games 7.1 and then Steam (legal) and CSS (legal) setup. Nvidia 8600GT with Proprietery 1.80 drivers.

Installation and update etc. went perfect. Opening CSS, all 100%. Scan for local servers - 100%, But connecting to a server it goes about 70%, shows a couple of status messages, last msg says sending Client details... and then I sit with the Desktop in front of me. CSS bombed out before I could even throw a Grenade!!!
  The CrossOver I'm using is an outdated, not supported version anymore (you have to pay a monthly subs to get the support, etc.), but for instance my Diablo LOD MedianXL works perfect... So in theory it works, just don't know how to get Error Logs or something like that to do some Debugging.

Any ideas?

---

### Post by diagram30 on 2009-07-09
I apologize if this is not the message that you would expect, but why not try WINE?  CSS runs extraordinarily well on it, and Steam has just a few bugs here and there.

---

### Post by ackanao on 2009-07-09
Hi NagWolf,

Try something like this:

Goto CS:S installation directory:
```
cd ~/.cxgames/bottlename/drive_c/Program\ Files/Counter\ Strike
```

and then run:
```
WINEDEBUG=-all ~/cxgames/bin/wine -cx-log errorlog.txt Game.exe --bottle bottlename
```
*(WINEDEBUG=-all means that all debug channels are turned off. "errorlog.txt" file will be placed in your CS folder)*

Type the name of your CS:S bottle instead of "**bottlename**".

If you get some errors, then start CrossOver Games, goto "Manage Bottles" tab; Select your CS:S bottle and click on "Make Default" button. Then try again.

Be careful which debug channels you want to activate!

Here are some useful links:

[http://www.codeweavers.com/support/docs/unsupported/misc]("http://www.codeweavers.com/support/docs/unsupported/misc")
[http://www.winehq.org/docs/wineusr-guide/x542#AEN544]("http://www.winehq.org/docs/wineusr-guide/x542#AEN544")

---

