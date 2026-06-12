---
title: "Problems after partial upgrade"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by samft on 2012-03-15
somebody please help me. i upgraded to 12.04 and my screen is doing weird things and it would let me do update only a partial one. the 'x' and min and max disappeared and the computer just freezes. just a lot of graphical errors ive ben looking everywhere for an answer. any kernels that should be installed? i dont even know what a kernel really is :'(

---

### Post by samft on 2012-03-15
i didnt know how to create a new post so i just put the question here :'(

---

### Post by samft on 2012-03-15
somebody please help me. i upgraded to 12.04 and my screen is doing weird things and it would let me do update only a partial one. the 'x' and min and max disappeared and the computer just freezes. just a lot of graphical errors ive ben looking everywhere for an answer. any kernels that should be installed? i dont even know what a kernel really is :'(

---

### Post by cariboo on 2012-03-15
Moved to U+1 sub-forum. and a thread of your own. I also moved you other post to this thread, as it was also in the wrong place.

---

### Post by novafluxx on 2012-03-16
> **cariboo907 said:**
> Moved to U+1 sub-forum. and a thread of your own. I also moved you other post to this thread, as it was also in the wrong place.

First off, what version did you upgrade from?

Is this your testing box or VM or your main install?

---

### Post by cariboo on 2012-03-16
I'd suggest that once you are at your desktop, press Ctrl-Alt-F1, at the prompt type:

```
sudo apt-get -f install
```

the above command should bring in the missing packages you need to fully upgrade your system. Once the process is finished, press Ctrl-Alt-Del to reboot the system. If all went well, you should boot to a working desktop. Keep in mind that this is only the first beta, so there will be many changes coming. In the future, if you are presented with a partial upgrade, please put it off for a couple of hours, and then try again.

---

### Post by novafluxx on 2012-03-16
Whenever presented with a partial upgrade you should wait a few hours to see if it goes away.


If it does not then you should search for the reasoning behind the changes.


Again this is a beta and not meant to be used in a production system.

---

### Post by ranch hand on 2012-03-16
Read the thread in the stickies for this forum on Partial Upgrades.

Then learn to use a real package management tool suitable for dev releases.

Avoiding UM will cause you not to have that particular problem.  There are plenty of other problems in a dev release with out shooing yourself in the foot.

---

### Post by jerrylamos on 2012-03-16
My rule of thumb for development level unstable ubuntu's:

sudo aptitude update
sudo aptitude save-upgrade

Haven't gotten any partials that way.

Sometimes it doesn't upgrade a kernel, so I do a

sudo aptitude full-upgrade

I can't count how many times apt-get update apt-get dist-upgrade has destroyed an installation.  Update Mangler has also caught me badly.

Oh, yes, I don't updgrade from 11.10 to 12.04 I make a separate partition to do the new level & do an install.  If it's working, then the 11.10 partition is available for the next install.  No matter what I do, an upgrade takes more disk space than an install.

Jerry

---

