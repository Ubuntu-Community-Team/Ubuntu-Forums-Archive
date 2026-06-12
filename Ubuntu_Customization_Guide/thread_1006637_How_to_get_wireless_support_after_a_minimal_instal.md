---
title: "How to get wireless support after a minimal install of ubuntu?"
date: 2008-12-09
forum: Ubuntu Customization Guide
---

### Post by Alden born on 2008-12-09
How to get wireless support after a minimal install of Ubuntu?  What packages do I have to download? thanks.

---

### Post by mikewhatever on 2008-12-09
Have you added any GUI, or is it intended to be a CLI installation?

---

### Post by Alden born on 2008-12-09
> **mikewhatever said:**
> Have you added any GUI, or is it intended to be a CLI installation/

well I was just playing around with the mini install.  I did have icewm installed at one time.  But as now I don't have it minimal installation installed on anything. Just kinda planning ahead of time.  

BTW what is CLI installation?

thanks.

---

### Post by mikewhatever on 2008-12-09
CLI = Command Line Interface. The reason I've asked is, I wasn't sure you wanted to install GUI tools. GUI = Graphical User Interface. From what I remember, the minimal install has no GUI tools. If you kept it that way, here is a good guide to manage your wireless from command line.
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by Alden born on 2008-12-09
> **mikewhatever said:**
> CLI = Command Line Interface. The reason I've asked is, I wasn't sure you wanted to install GUI tools. GUI = Graphical User Interface. From what I remember, the minimal install has no GUI tools. If you kept it that way, here is a good guide to manage your wireless from command line.
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

oh ok thanks.  I do want GUI so do you know of what I need to install to get it working like regular install of ubuntu.

And thanks for that link it will useful.

---

### Post by mikewhatever on 2008-12-09
You have a few options. I'd recommend trying wicd first.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
If you want the default tools, install the network-manager-gnome package.

---

### Post by Alden born on 2008-12-09
> **mikewhatever said:**
> You have a few options. I'd recommend trying wicd first.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
If you want the default tools, install the network-manager-gnome package.

ok thanks ill look into both of them and would the network-manager-gnome package work in ICEwm? I'm trying to keep this Operating system light weight. the size of it does not matter just want to keep it light and fast so to speak.

---

### Post by mikewhatever on 2008-12-09
I may be wrong, but NMG and ICEWM are two different things, with neither of them depending or working on top of the other. That said, NMG is a part of Gnome Desktop Environment and has many dependencies which may also have dependencies of their own. WICD should most probably have a lot fewer dependencies, hence the 'try it first' recommendation.
Edit: You'd also want the wpasupplicant package in both cases.

---

