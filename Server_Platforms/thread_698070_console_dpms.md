---
title: "console dpms?"
date: 2008-02-15
forum: Server Platforms
---

### Post by isecore on 2008-02-15
Here's a question to ponder:

is there a way to make a monitor go into standby in console?

See, I run a Debian-server so the technique should be similar to an Ubuntu-server. It runs console only, no X. Currently it blanks the screen but doesn't turn it off. Of course I can do this by just turning off the monitor, but I started wondering if it would be possible to do it automagically.

Any input is appreciated.

---

### Post by yabbadabbadont on 2008-02-15
```
man setterm
```

:D

You need to read up on the "powersave" and "powerdown" options I think.

---

### Post by isecore on 2008-02-15
So it would seem, thanks for the input :)

---

### Post by yabbadabbadont on 2008-02-15
You're welcome.  Half the battle in Unix/Linux is knowing which commands you need to read up on.  On the other hand, if you already know which command you need to research, you probably don't need to research it...  :D

---

### Post by isecore on 2008-02-17
> **yabbadabbadont said:**
> You're welcome.  Half the battle in Unix/Linux is knowing which commands you need to read up on.  On the other hand, if you already know which command you need to research, you probably don't need to research it...  :D

That's very true. I'm not exactly a newbie to Linux or UNIX (first serious exposure was around '96), but I'm constantly learning new stuff - and I'm not afraid to ask questions when I don't know the answer either :)

---

### Post by hansaplast on 2008-07-22
I Use this in ~/.bash_profile
```

setterm -blank 5		# Blank the screen in 5 minutes
setterm -powersave on		# Put the monitor into VESA power saving mode
setterm -powerdown 10		# Set the VESA powerdown to 10 minutes
```

After reboot these settings are lost. Since I'm not always at the box' console, where can I put these so that they are loaded during boot and not at login?

---

### Post by hansaplast on 2008-07-22
> **hansaplast said:**
> 
After reboot these settings are lost. Since I'm not always at the box' console, where can I put these so that they are loaded during boot and not at login?
Found it.. its /etc/console-tools/config

---

