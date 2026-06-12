---
title: "nvidia and gnome-shell"
date: 2012-05-14
forum: The Cafe
---

### Post by Crempel on 2012-05-14
There has been quite some discussion (rightfully) about precise an unity 3D not working with nvidia-drivers, I have not yet found any comment re nvidia and gnome-shell. (If there have been any, please excuse).
For love or money I could not get unity 3D to work with a GS 7200, 64-bit system. Once I install gnome-shell from the ubuntu repos I got 1280 FPS, everything else 3 D worked like a charm. And that is with a 302.07 driver that did not work with unity.
So, as far as I am concerned, we got a unity and not a nvidia problem. 
Anyway, I think ubuntu's version of gnome shell is excellent, but why was it never made clear that we got a unity prob here, rather than a general one?:confused:
Cheers Mike

---

### Post by Frogs Hair on 2012-05-14
I have not had any Nvidia current driver problems with Unity 3D or the Gnome Shell and that includes beta testing 12.04.

---

### Post by Crempel on 2012-05-14
Gee, I wish I knew how you did that. Maybe we got different video cards; ,mine is a 7200 GS, and as I said, I tried for hours to get it to work with all sorts of nividia drivers. I would like to hear what card you got. Thanks:)

---

### Post by BigSilly on 2012-05-14
Well I have a 9800GT and no issues. There are one or two visual glitches in Unity here and there, but nothing serious and it's nothing Nvidia related. My performance in both Shell and Unity is pretty excellent actually. Sorry to hear of your troubles with it. :(

---

### Post by sffvba[e0rt on 2012-05-14
Probably an issue with compiz...


404

---

### Post by Perfect Storm on 2012-05-14
No problem with Unity3D or Gnome Shell for me. Geforce GTX285 1GB Ram.

---

### Post by Bandit on 2012-05-14
No problems with a nv 460GTX

---

### Post by OldSmoky2 on 2012-05-14
There is a problem with the current Nvidia driver (295.40) and older Nvidia cards, as it was a buggy update not just for Ubuntu but for other Linux distros as well. I know it affects 6series and 7series cards, which I have, so I would assume it affects 5series too.
Nvidia has released an update (295.49) that apparently fixes the problems but that hasn't shown up in Ubuntu updates yet. If you search the forums, you'll find some posts about it, as well as instructions on how to download and install the update from Nvidia. My problems aren't as severe as a blank screen - I do have to reboot if I try to suspend and then wake the computer up running Ubuntu 12.04, though I don't have that problem with my Kubuntu 12.04 partition. So I'm just waiting on Ubuntu to provide the update, which will hopefully be very soon.

---

### Post by alphacrucis2 on 2012-05-14
> **OldSmoky2 said:**
> There is a problem with the current Nvidia driver (295.40) and older Nvidia cards, as it was a buggy update not just for Ubuntu but for other Linux distros as well. I know it affects 6series and 7series cards, which I have, so I would assume it affects 5series too.
Nvidia has released an update (295.49) that apparently fixes the problems but that hasn't shown up in Ubuntu updates yet. If you search the forums, you'll find some posts about it, as well as instructions on how to download and install the update from Nvidia. My problems aren't as severe as a blank screen - I do have to reboot if I try to suspend and then wake the computer up running Ubuntu 12.04, though I don't have that problem with my Kubuntu 12.04 partition. So I'm just waiting on Ubuntu to provide the update, which will hopefully be very soon.

The fixed version is in xswat ppa

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Easy Limits on 2012-05-14
[http://ubuntuforums.org/showthread.php?t=1974205](http://ubuntuforums.org/showthread.php?t=1974205)

---

### Post by Crempel on 2012-05-15
Thank you all for your contributions. I have read a lot about a nvidia problem with 12.04 unity, but does not seem to be that wide spread. Anyway, I have tried nouveau and four different nvidia drivers, with  compiz fully engaged, and nothing worked! Using gnome-shell instead of unity, 3D works even with nouveau, not to mention proprietary nvidia drivers (1280 FPS!)
I am very happy with the gnome-shell, so I will mark this post as solved.):P

---

