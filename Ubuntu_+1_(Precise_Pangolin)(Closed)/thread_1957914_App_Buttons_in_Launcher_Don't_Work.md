---
title: "App Buttons in Launcher Don't Work"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by neu5eeCh on 2012-04-13
Filed a bug report here:

[https://bugs.launchpad.net/unity/+bug/975942](https://bugs.launchpad.net/unity/+bug/975942)


For the last week, if an app is in a different workspace, pressing that app's button on the launcher won't bring it up. It will only switch me to the app **if** the app *is in the same workspace*. Curiously, this problem extends to the AWN dock as well. Just wondering if anyone else is having the same problem. If so, go to the bug report and confirm it.:popcorn:

---

### Post by cariboo on 2012-04-13
I've seen this behavior, but is it usually  because the application is partially overlapping another workspace. See the screenshot, when I click the Thunderbird icon, nothing happens.

---

### Post by neu5eeCh on 2012-04-17
> **cariboo907 said:**
> I've seen this behavior, but is it usually  because the application is partially overlapping another workspace. See the screenshot, when I click the Thunderbird icon, nothing happens.

I just ran all the updates to see if they fix the problem. They don't. I made sure there was no overlapping, but the buttons simply don't work unless I'm in the same workspace. It just occurs to me that there might be a conflict with the [minimize feature]("http://www.omgubuntu.co.uk/2012/04/how-to-minimizemaximize-apps-to-unity-launcher/") I installed, but I haven't tried uninstalling it. I'm back in Xubuntu.

At this point, I hate to say it (in a way) but I spend less and less time in Ubuntu, and nearly all my time in Xubuntu. It's just a more enjoyable, feature-ful and flexible DE (to me). I get incredibly frustrated by the global menu. The weird problem is that the menu doesn't always match the "ostensibly" open window. I click to close the window and I unexpectedly close another (almost closed the terminal while it was downloading updates).

---

### Post by neu5eeCh on 2012-04-18
Still no satisfaction.

I'm up-to-date but the buttons on the launcher *and* on AWN fail to switch me to an app if it's on a different workspace. It would just figure if I'm the only one suffering this bug. What does the fact that neither the launcher nor AWN are functional suggest?

---

### Post by mc4man on 2012-04-18
It would suggest a couple of things - 
Your install or user configl is borked
or
As mentioned clicking on an icon won't switch if the window is on the current space to any extent, or unity thinks it's on that WS
So what do the little icon arrow(s) show when not on the WS where window is open? Should just be > on left side.
or
Awn is interfering somehow with proper behavior

---

### Post by neu5eeCh on 2012-04-18
> **mc4man said:**
> It would suggest a couple of things - 
Your install or user configl is borked

Yeah... but that's above my pay grade.

> **mc4man said:**
> As mentioned clicking on an icon won't switch if the window is on the current space to any extent, or unity thinks it's on that WS

It will switch between windows if they're all on the same workspace, but not if the app is on a different workspace. In that case, Unity will "background" the workspace's current apps but do nothing else. I also notice that the [unity-minimize-on-click]("https://launchpad.net/%7Eojno/+archive/unity-minimize-on-click") function isn't working. And I continue to wonder whether the patch is to blame, but I can't for the life of me figure out how to remove it. Apt-get remove doesn't respond to any name I can think of. I can't find it in Software Center or Synaptic.

> **mc4man said:**
> So what do the little icon arrow(s) show when not on the WS where window is open? Should just be > on left side.

I'm on WS 1, the Terminal is open in WS 2. If I click on the Terminal Icon, all open windows are "backgrounded" on WS 1 but I'm not switched to WS 2 (or the terminal) and only one arrow (the left arrow) shows.

> **mc4man said:**
> Awn is interfering somehow with proper behavior

Possibly, but if I log in without AWN, or kill AWN, the behavior continues. AWN works in other sessions like Gnome Shell or Cinnamon.

---

### Post by mc4man on 2012-04-18
If you got the left click to min unity version from a ppa then ppa-purge should remove it

Is that the case & if so do you have the ppa enabled in your sources?

If so & you have a link or name of the ppa I'll install it & see. (if there is a unity-5.10 package set

Edit: I found this ppa but it doesn't have builds after unity-5.8
[https://launchpad.net/~ojno/+archive/unity-minimize-on-click](https://launchpad.net/~ojno/+archive/unity-minimize-on-click)

---

### Post by neu5eeCh on 2012-04-18
> **mc4man said:**
> If you got the left click to min unity version from a ppa then ppa-purge should remove it

Thanks. I purged the PPA, removing the Minimize patch, but no change; so at least I can eliminate that red herring.

> **mc4man said:**
> Is that the case & if so do you have the ppa enabled in your sources?

No longer. 

I killed AWN and tried CAIRO - the same behaviour. So... what does one make of **that**? Presumably, Launcher, AWN and CAIRO are all making the same calls to the same subroutine (if that's what we call it nowadays). So... the problem must be smack-dab in Unity somewhere. Something is broken and it's going to take a more *ubuntu-soaked* mind that mine to sort it out.

---

### Post by alphacrucis2 on 2012-04-18
What if you set unity back to defaults.
```

unity --reset
```

You need to then log out and back in again. Downside is that you will lose any customisations and have to redo.

---

### Post by neu5eeCh on 2012-04-18
> **alphacrucis2 said:**
> What if you set unity back to defaults.
```

unity --reset
```You need to then log out and back in again. Downside is that you will lose any customisations and have to redo.

Well! Butter my parsnips. That worked! 

**That** makes me think Ubuntu Tweak or MyUnity were somehow involved in this mess. On the downside, I just tried: 

Life --reset

And nothing happened.:popcorn: Damn.

---

### Post by alphacrucis2 on 2012-04-18
> **VTPoet said:**
> Well! Butter my parsnips. That worked! 

**That** makes me think Ubuntu Tweak or MyUnity were somehow involved in this mess. On the downside, I just tried: 

Life --reset

And nothing happened.:popcorn: Damn.


:lolflag:

---

