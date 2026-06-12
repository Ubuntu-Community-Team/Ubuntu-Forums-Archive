---
title: "Botched Trusty beta upgrade"
date: 2014-03-22
forum: Ubuntu Development Version
---

### Post by nachokb2 on 2014-03-22
Hi guys,
  I've been running Ubuntu Saucy with GNOME Shell 3.10 from PPA (with GDM) for a while now. Quickly tested Trusty beta in a VM and I liked it, and being used to somewhat easy upgrades, I decided to go ahead and fix any error which comes up.

  But this quickly got over my head :P.

  I usually have many PPAs set up so I'm used to having some of them disabled and going around when things break (e.g. after upgrading to GS 3.10 via PPA LightDM stopped working, but a simple dpkg-reconfigure enabled GDM).

  This time I really screwed up. GDM wouldn't start up (if installer switched to LightDM, that doesn't either). Had to drop to "Recovery Mode" and fix broken packages. It took a while but it left the system bootable.

  So I restart, login, and find all APT sources upgraded to Trusty or disabled (correct). But GNOME Shell is still 3.10 (no 3.11.9x in the repos, PPA is disabled), kernel is 3.11 (no newer packages available either).

  Unity seems rather updated (synaptic says it's 7.1.2, I think that's from Trusty), which looks fully functional... save for the clock! (the clock indicator is just not there). Unity 8 shows up in the repo; but if I mark it I see something weird: it depends on lots of stuff which should be installed, like network-indicator (which does show up and works).

  So it looks like a botched upgrade left inconsistent packages / versions, but no matter how many times I reload packages info, no new upgrades show up; /etc/apt/sources.list shows main, universe and multiverse enabled and pointing to Trusty, but still apt can't see e.g. kernel 3.11 [1].

  Any idea? Perhaps APT has an inconsistent cache or something?

-- nachokb

[1] [http://packages.ubuntu.com/trusty/kernel/linux-image-3.13.0-18-generic](http://packages.ubuntu.com/trusty/kernel/linux-image-3.13.0-18-generic)

---

### Post by nachokb2 on 2014-03-22
Well, just reloaded repos information and now I've got a linux-generic 3.11 kernel, which I'm installing now (it also depended on a lot of stuff like newer libc, gcc, etc). 

And I just checked [1] to see that GNOME Shell 3.11.x is not in the main repos, sorry for that (will have to try the PPA). Still there seems to be some inconsistent packages, I'll try to keep you posted.

-- nachokb

[1] [http://packages.ubuntu.com/trusty/gnome/gnome-shell](http://packages.ubuntu.com/trusty/gnome/gnome-shell)

---

### Post by cariboo on 2014-03-22
Trusty gnome-shell is at version 3.10.4, and at this late time in the development cycle we won't see anything newer.

---

### Post by Mateusz Stachowski on 2014-03-23
> **nachokb2 said:**
> 
  Unity seems rather updated (synaptic says it's 7.1.2, I think that's from Trusty), which looks fully functional... save for the clock! (the clock indicator is just not there). Unity 8 shows up in the repo; but if I mark it I see something weird: it depends on lots of stuff which should be installed, like network-indicator (which does show up and works).

  So it looks like a botched upgrade left inconsistent packages / versions, but no matter how many times I reload packages info, no new upgrades show up; /etc/apt/sources.list shows main, universe and multiverse enabled and pointing to Trusty, but still apt can't see e.g. kernel 3.11 [1].

  Any idea? Perhaps APT has an inconsistent cache or something?

-- nachokb

[1] [http://packages.ubuntu.com/trusty/kernel/linux-image-3.13.0-18-generic](http://packages.ubuntu.com/trusty/kernel/linux-image-3.13.0-18-generic)

[indicator-network]("http://packages.ubuntu.com/trusty/indicator-network") is a new indicator from Unity 8 (see its dependencies) the one that you see normally in Unity 7 comes from [network-manager-gnome]("http://packages.ubuntu.com/trusty/network-manager-gnome") checkout the screenshot. If you don't believe me than look at this questions on Ask Ubuntu: [How can I restore Network Indicator in Unity Panel?]("http://askubuntu.com/questions/138196/how-can-i-restore-network-indicator-in-unity-panel") and [Network manager indicator missing]("http://askubuntu.com/questions/159812/network-manager-indicator-missing").

The newest kernel available in Trusty is [3.13.0-19]("http://packages.ubuntu.com/trusty/any/linux-image-3.13.0-19-generic") and I had it in updates yesterday.

---

### Post by grahammechanical on 2014-03-24
In my experience there is one period when it is reasonably safe to upgrade from the last version of Ubuntu to the development branch of the next version of Ubuntu (which is what we still have). And that is during the first 8 to 10 weeks of the development cycle when the code base is still very much the code base of the last release.

The further into the development cycle we go the greater the risk, in my opinion. We should either install a daily image or wait until the development cycle is compete or almost complete and the upgrade path has been carefully scripted.

I also see greater risk in upgrading Ubuntu + alternative desktop environments or user interfaces then upgrading the genuine Ubuntu flavour. In this case Ubuntu Gnome.

Regards.

---

### Post by nachokb2 on 2014-03-25
> **cariboo907 said:**
> Trusty gnome-shell is at version 3.10.4, and at this late time in the development cycle we won't see anything newer.

You're right, the I had read about 3.12 in Trusty, but I must have overseen that it was from PPA :P.

Thanks.

P.S. Now running from PPA. It works nice (though the poor extensions API and its versioning is still frustrating).

nachokb

---

### Post by nachokb2 on 2014-03-25
> **Mateusz Stachowski said:**
> [indicator-network]("http://packages.ubuntu.com/trusty/indicator-network") is a new indicator from Unity 8 (see its dependencies) the one that you see normally in Unity 7 comes from [network-manager-gnome]("http://packages.ubuntu.com/trusty/network-manager-gnome") checkout the screenshot. If you don't believe me than look at this questions on Ask Ubuntu: [How can I restore Network Indicator in Unity Panel?]("http://askubuntu.com/questions/138196/how-can-i-restore-network-indicator-in-unity-panel") and [Network manager indicator missing]("http://askubuntu.com/questions/159812/network-manager-indicator-missing").

The newest kernel available in Trusty is [3.13.0-19]("http://packages.ubuntu.com/trusty/any/linux-image-3.13.0-19-generic") and I had it in updates yesterday.

You're correct, too. I just got confused.

Didn't install unity8 to test it though, not yet at least.

nachokb

---

### Post by nachokb2 on 2014-03-25
> **grahammechanical said:**
> In my experience there is one period when it is reasonably safe to upgrade from the last version of Ubuntu to the development branch of the next version of Ubuntu (which is what we still have). And that is during the first 8 to 10 weeks of the development cycle when the code base is still very much the code base of the last release.

The further into the development cycle we go the greater the risk, in my opinion. We should either install a daily image or wait until the development cycle is compete or almost complete and the upgrade path has been carefully scripted.

I also see greater risk in upgrading Ubuntu + alternative desktop environments or user interfaces then upgrading the genuine Ubuntu flavour. In this case Ubuntu Gnome.

Regards.

Yep, I agree this is risky. But then again, that is not my main work computer so I use it to experiment a little. 

That being said, this is the third Ubuntu version in a row that I upgrade to ~4 weeks before release (perhaps it's time to start fresh!), and the previous two it went without a hitch (even with me having many PPAs like GNOME's, etc).

What confused me the most was (1) that it left the machine basically unbootable and (2) that it didn't show the upgraded kernel (which I used as a reference). I think both were caused by some strange caching or some confusion on the part of APT, as it later did pick the newer kernel up.

Running great now. Still licking my wounds, though, and I've got a lot of (beta) stuff to test.

Thanks!

nachokb

---

