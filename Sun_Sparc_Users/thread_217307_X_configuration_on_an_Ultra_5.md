---
title: "X configuration on an Ultra 5"
date: 2006-07-16
forum: Sun Sparc Users
---

### Post by kliner on 2006-07-16
Hello -

I was able to install Ubuntu Server just fine, but my issue is with xserver in particular. Using apt-get (and aptitude the first time I installed) xserver downloads, installs, and runs me through the setup of picking video chipsets, resolutions, and such. I just left the default options as they were "detected" as I'm not sure what I should pick. After that config, the box reboots...and the initial Ubuntu screen comes up and the progress bar starts moving as things begin to load...and that's where everything goes kaput. My screen then goes black and my display shows "unusable signal".

I have found a handful of others with this issue, but no solution so far. My video setup is nothing more than the on-board adapter.

I should have spared you having to read that, and just asked if you had Xserver up and running on an Ultra 5...and if so, how'd you do it. Sorry!

Any/all help is much appreciated!

Scott

---

### Post by netztier on 2006-07-17
> **kliner said:**
> I should have spared you having to read that, 

No, you shouldn't.

It's ok to ask the straightforward question. 

And it's even more ok to include some detailed description of what is happening, under what circumstances, what kind and number of error messages are generated and which steps and procedures you have already taken to analyze or fix things.

People who like to help don't often have looking-glass crystal balls to look into and tell what might be wrong, and if they do, in 4 times out of 5, their crystal ball had to be sent back for repairs right the day before it would be useful, anyway. ;-)

> **kliner said:**
>  and just asked if you had Xserver up and running on an Ultra 5...and if so, how'd you do it. Sorry!

Nope. That would have hinted a lot more in the direction of "unwitting n00b that just wants someone else to fix his problems". So it's perfectly ok to include some additional info.

Back to the question.

[COLOR="DarkGreen"]I suspect that it's just the video timing settings that are screwed up. Can you bring up some information about your monitor (make, model, supported refresh rates, supported resolutions, supported vertical and horizontal sync rates and the like? Check with the manual - or try downloading it form the maker's web site)
[/COLOR]

Once the screen goes black and the monitor says that the signal is unusable, can you switch back into a text console (Alt+F1 or Ctrl+Alt+F1) and login there? If yes, the U5 is running well. It's just that the graphics subsystem delivers a signal that the monitor can't handle. 

We should look into the **/etc/X11/xorg.conf** and **/var/log/Xorg.0.log** files in that case. Can you extract them from that machine and post them as attachments to a reply to this posting?

I also suggest you rather install one of the **ubuntu-desktop** (Gnome), **kubuntu-desktop** (KDE) or **xubuntu-desktop** (XFCE) packages instead of *xserver-xorg* (unless you exactly know what you are doing). These will install a whole desktop environment, while  the latter just brings you part of the graphics framework.

kind regards

Marc

---

