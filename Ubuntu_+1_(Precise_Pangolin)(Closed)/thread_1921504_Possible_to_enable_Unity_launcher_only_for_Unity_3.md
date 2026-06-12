---
title: "Possible to enable Unity launcher only for Unity 3D mode with ccsm installed?"
date: 2012-02-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by prusswan on 2012-02-06
Here's the deal, I still prefer the pre-Unity interface which is more or less achievable with ccsm and gnome-fallback-session installed, but that currently leaves Unity broken since the launcher does not appear as long as Unity plugin is disabled in ccsm, which is what I want for GNOME Classic. 

PS: I use ccsm mainly for the put to next output function for moving windows across a dual monitor setup.

Edit: Turns out I already have what I want (Unity only appears in Ubuntu session, even with CCSM installed)

---

### Post by effenberg0x0 on 2012-02-07
> **prusswan said:**
> Here's the deal, I still prefer the pre-Unity interface which is more or less achievable with ccsm and gnome-fallback-session installed, but that currently leaves Unity broken since the launcher does not appear as long as Unity plugin is disabled in ccsm, which is what I want for GNOME Classic. 

PS: I use ccsm mainly for the put to next output function for moving windows across a dual monitor setup.

I'm sorry if I didn't understand you right. 
You want the traditional interface and for some reason ccsm. But it bothers you that Unity Launcher Bar is not showing when you disable unityshell. 

So the outcome you are trying is an accelerated '3d' desktop (hence CCSM being mentioned), in which you have both gnome-panel (the traditional interface you enjoy) but also the Unity Launcher Bar? Isn't that the same as starting Ubuntu/Unity and launching gnome-panel? See the screenshot:
[ATTACH]212204[/ATTACH]
Is that it more or less? (This is a hideous screen shot, but one can probably fix the overlapping top panels, etc: There are professional and successful attempts to recreate the traditional gnome desktop out there).

Regards,
Effenberg

---

### Post by prusswan on 2012-02-07
Sorry if I did not make myself clear. With gnome-session-fallback and ccsm installed, GNOME Classic is working fine (no unity), but Ubuntu (Unity 3D) is broken (no launcher + no menu) if I choose to use that as DE at login screen. Ubuntu (Unity) 2D seems to be working (with menu + launcher).

Btw, right now (with the latest dist upgrades) Unity is at 5.2.0-0 while a couple of other unity related packages are at 5.2.1-0. I am not sure if the broken Unity 3D has anything to do with this.

---

### Post by grahammechanical on 2012-02-07
Here is the real deal: Like 11.10 before it 12.04 is based upon the Gnome 3 desktop environment. Canonical are pressing ahead with their vision for Ubuntu. But as this is Linux and Canonical believe in the Open Source no one is forbidden from developing alternative user interfaces.

Here is the catch: We are limited to what other people are willing to provide and we have to accept their choices. I am speaking as a non-programmer who is not able to code a user interface according to his own tastes.

There are a few alternative UI around that we can install and then select at the log in screen. Canonical may even make it easy to install them but, in my opinion, there are only two official User interfaces that Canonical really care about. You see, Canonical also believe in community. I see nothing wrong with Canonical leaving some things to the community.

Regards.

---

### Post by TerryNewton on 2012-02-07
> **prusswan said:**
> Here's the deal, I still prefer the pre-Unity interface which is more or less achievable with ccsm and gnome-fallback-session installed, but that currently leaves Unity broken since the launcher does not appear as long as Unity plugin is disabled in ccsm, which is what I want for GNOME Classic.

Boot into Classic then use CCSM's preferences to add a separate "Classic" profile, then boot into Unity and use CCSM's preferences to select the existing unity profile (if not already selected, if a unity profile doesn't exist then add one). Then separate settings can be applied to each environment.

---

