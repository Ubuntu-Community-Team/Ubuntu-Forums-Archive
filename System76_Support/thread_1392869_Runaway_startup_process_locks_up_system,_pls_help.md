---
title: "Runaway startup process locks up system, pls help"
date: 2010-01-28
forum: System76 Support
---

### Post by watchpocket on 2010-01-28
As of last night, when I boot up, a gnome-terminal opens, then another  and another, ad infinitum.

This just continues, creating more and more and smaller and smaller  icons along the bottom panel.  The system locks up and the runaway  process continues til I shut down.

How can I stop this from happening as soon as I log on?  I tried hitting  COMMAND-Q a bunch of times to no avail.

(What's happening is that I put "Terminal" in the startup items, and for  its command I put to launch a script that opens 7 terminals, but once  terminals start to be opened, this doesn't stop.)

I'm running 64-bit karmic on a system76 Wild Dog desktop unit.

---

### Post by pastalavista on 2010-01-28
When you log in, select a fail-safe session. Then edit the start-up list.

---

### Post by watchpocket on 2010-01-28
It occurred to me that one possible way might be to boot into recovery mode or safe mode, get to a shell prompt either as user or su, and do a:

```
chmod ugo-rwx name-of-script.sh
``` (or /full/path/to/ name-ofscript.sh)

Since /bin/sh name-of-script.sh is in the startup command of the "Terminal" that's in "Startup Items," disabling all permissions for the script would cause it not to run.

---

### Post by watchpocket on 2010-01-28
Actually your solution appears to be even simpler, pastalavista.  

I'll try it first, thanks.

---

### Post by pastalavista on 2010-01-28
you're welcome. the simple solutions aren't always the most obvious.

---

### Post by watchpocket on 2010-01-29
Well, I removed "Terminal" from the "Startup Applications" list, and renamed my script file that 
opens several terminals (which is what originally started the problem of the unbidden infinite opening of terminal processes).  

I also removed all permissions from that script file before I re-named it.

Then I opened Terminal from Applications -> Accessories, and the infinite opening of terminals started again, so I removed from my computer "gnome-terminal" "gnome-terminal-data" and "termlauncher-applet."

Then I re-installed all of those.  Now when I try to launch gnome-terminal, the executable in /usr/bin, I get this message:

"There is no installed viewer capable of displaying the document."

Not sure what that means, except that I have no access to a terminal right now. 

I'd also like to get "Terminal" back into the Applications -> Accessories list.  What a pain.  Any tips appreciated.

---

### Post by pastalavista on 2010-01-29
Not knowing for sure exactly what you have done or why, I can only recommend two things I've done and a third for better understanding. I'm not all that well versed in Linux code.

1- Reboot in recovery mode and repair broken packages ```
sudo dpkg --configure -a
``` reboot, Only do the following if the previous doesn't work.

2- Reinstall Ubuntu in MANUAL mode and UNCHECK the 'format' boxes for all partitions. be sure to use the same exact user name. reboot.. run updates.

3- Explain all your changes, reasons, and post your scripts for proofreading. I don't understand why you need to open 7 terminals.

---

