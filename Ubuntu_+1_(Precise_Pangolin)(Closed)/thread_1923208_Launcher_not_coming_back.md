---
title: "Launcher not coming back"
date: 2012-02-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by superflymonkeyboy on 2012-02-10
I've set the launcher to come back when I move the mouse to the left of the screen, but it isn't working. I have to minimise and go back to the desktop to see it. Any ideas why anyone?

---

### Post by grahammechanical on 2012-02-10
I am assuming that you are using 12.04 and that when you say

>  I have to minimise and go back to the desktop to see it.

You are referring to a having a Window full screen or maximised.

I do not have this problem. I have set the Launcher Reveal Sensitivity towards the Low end of the scale. Is your setting towards the High end of the scale?

System Settings>Appearance>Behaviour.

Regards.

---

### Post by mc4man on 2012-02-10
> **superflymonkeyboy said:**
> I've set the launcher to come back when I move the mouse to the left of the screen, but it isn't working. I have to minimise and go back to the desktop to see it. Any ideas why anyone?
It's done now by going to left edge, then pushing against the edge

To make the launcher easier to reveal you would technically raise the sensitivity  in System Setting ...  or in ccsm/gconf lower the pressure.

Atm in unity-5.2 there are 3 ways to adjust - ccsm, gconf-editor, system settings... & they are not on the same page so to speak. If you have ccsm installed then probably better to go into the Unity plugin settings & lower the pressure from the default of 20, 5 -10 seems more reasonable for many

In unity-5.4 the whole adjustment deal may be working better & if desired 'top left only'  now does work

---

### Post by VMC on 2012-02-10
> **superflymonkeyboy said:**
> I've set the launcher to come back when I move the mouse to the left of the screen, but it isn't working. I have to minimise and go back to the desktop to see it. Any ideas why anyone?

I had that issue before I upgraded. When was the last time you upgraded?

---

### Post by superflymonkeyboy on 2012-02-10
Hi - yes I'm using 12.04 LTS. Just upgraded.  I can't see a sensitivity slider in my settings. I've attached a screenshot. I can see the launcher if I don't have any windows full screen. When any window is set to full screen, the launcher doesn't come back when I put my mouse over to the left side of the screen.

Tried doing an update. It says I have to do a partial upgrade, but then it fails to complete for some reason I can't work out. I upgraded about a week ago.

Cheers guys.

---

### Post by cariboo on 2012-02-10
It looks like you are behind on your updates, I'd suggest using synaptic, but it's fairly broken at the moment. Your best bet would be to update/upgrade from the command line using apt, or aptitude.

---

### Post by terry_gardener on 2012-02-10
> **superflymonkeyboy said:**
> Hi - yes I'm using 12.04 LTS. Just upgraded.  I can't see a sensitivity slider in my settings. I've attached a screenshot. I can see the launcher if I don't have any windows full screen. When any window is set to full screen, the launcher doesn't come back when I put my mouse over to the left side of the screen.

Tried doing an update. It says I have to do a partial upgrade, but then it fails to complete for some reason I can't work out. I upgraded about a week ago.

Cheers guys.

as mc4man said above you need to change the sensitivity using one of those programs ccsm is probably the easiest.

---

### Post by mc4man on 2012-02-10
As mentioned you should get updated before anything, generally waiting a week during dev is a bit long.

Also you should refrain from ever accepting a partial update thru update manager during dev, as in **never**.
(learn how to use other means such as synaptic to upgrade packages update-manager can't deal with

As far as the reveal setting - if ccsm (compizconfig-settings-manager) isn't installed then once you get gnome-control-center upgraded the slider will be there & may work.

Additionally if ccsm isn't installed you can use gconf to adjust, if ccsm is installed i'd just go there

Edit : as is quite common you may need to restart an apt to see changes or just do a log out/in

Ex gconf command for a setting of 10

```
gconftool -s --type Integer /apps/compiz-1/plugins/unityshell/screen0/options/reveal_pressure 10
```

---

### Post by VMC on 2012-02-14
Odd, but I'm having this same issue with a new install on todays amd64 iso:
' precise-desktop-amd64.iso  14-Feb-2012 07:58'

I tried all options on "System Settings>Appearance> Behavior". Nothing worked except setting launcher always on.

edit: Strange, but if I bounce the mouse against the left wall several times, then the launcher becomes active!
Kinda like a salesman banging on your door until you answer :)

---

