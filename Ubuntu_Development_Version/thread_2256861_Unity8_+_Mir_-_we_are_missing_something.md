---
title: "Unity8 + Mir - we are missing something"
date: 2014-12-15
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2014-12-15
And it is this thread on Discourse Ubuntu. See the work being done by one engineer.

[http://discourse.ubuntu.com/t/unity-8-desktop-mode-windows-on-mir/1986](http://discourse.ubuntu.com/t/unity-8-desktop-mode-windows-on-mir/1986)


Regards.

---

### Post by ventrical on 2014-12-15
@graham

Thanks for staying the course on this.  It appears to me the the lxc project is now part of the unity-next because updates have provided all mentioned in that unity8=lxc thread.

Perhaps it may be too early to comment as such but it appears that the new direction of turning phone=> desktop is really just a slight remake of unity7 on top of mir and/or/X.  The method of using radio buttons seems to have  provided a bridge for usual desktops and unity8 to crossover  quietly in the convergence process. So the work now is setting up a more sophisticated radio/tweak/patch/tool that can handle all the flags to come. This makes perfect sense because it can now actually be testable in a more practical manner.

One thing concerns me and that is  that the link you have provided mentions only one dev who is working on this. Are other devs going to  jump on this bandwagon  or will there be a revolt (as such there was with wayland/mir controversy)  ? Secondly .. how much of a real difference is this new framework different from the standard and current unity7?  This leads me to conclude that there may not be an option for regular unity as we know it for the desktop and that the converged unity (in a year and a half or so) will include the radio button technique. There is nothing really new here..

Regards..

---

### Post by grahammechanical on 2014-12-15
It may be that Canonical engineers are allowed to pursue their own course in the hope that something useful may come from it. Other engineers may also be working on this but from a different direction. Or they may be working on other aspects of convergence. I think that the rootless X running on Mir is important. It leads on to the default Ubuntu desktop applications being able to run on Mir, such as Libreoffice, without needing to be converted into Click packages. Although I think that conversion to click apps will be neccessary if convergence is to truely mean convergence. Regards (posting from Unity8 in LXC using Browser which does not give line breaks on this forum but with resized application windows).

---

### Post by ventrical on 2014-12-15
> **grahammechanical said:**
>  Regards (posting from Unity8 in LXC using Browser which does not give line breaks on this forum but with resized application windows).

 I think this is the way to go as it represents  a more sound  intergration of sorts that is inclusive  of three decades of clickity adaptation. The lone  dev has got it bang on as they say in London :)

Regards..

---

### Post by cariboo on 2014-12-15
> **grahammechanical said:**
> It may be that Canonical engineers are allowed to pursue their own course in the hope that something useful may come from it. Other engineers may also be working on this but from a different direction. Or they may be working on other aspects of convergence. I think that the rootless X running on Mir is important. It leads on to the default Ubuntu desktop applications being able to run on Mir, such as Libreoffice, without needing to be converted into Click packages. Although I think that conversion to click apps will be neccessary if convergence is to truely mean convergence. Regards (posting from Unity8 in LXC using Browser which does not give line breaks on this forum but with resized application windows).

You need javascript enabled in order to fully take advantage of vBulletin features, the browser obviously doesn't do this yet.

---

### Post by grahammechanical on 2014-12-18
In his latest post in that Discourse thread the engineer demonstrates X11 apps such as Libreoffice running on Xmir on Unity8

Does anybody know how to do this?

> [FONT=Ubuntu]you can already run the code... install Ubuntu NEXT and then apply the "patch", you have to copy 3 qml files from the diff[/FONT]

The code is here

[https://code.launchpad.net/~mzanetti/unity8/desktop-stage/+merge/242140](https://code.launchpad.net/~mzanetti/unity8/desktop-stage/+merge/242140)

[https://code.launchpad.net/~mzanetti/unity8/desktop-stage](https://code.launchpad.net/~mzanetti/unity8/desktop-stage)

> [COLOR=#333333][FONT=monospace]bzr branch [/FONT][/COLOR][COLOR=#333333][FONT=monospace]lp:~mzanetti/unity8/desktop-stage[/FONT][/COLOR]

Obviously, I already have Ubuntu Desktop Next installed. It is the "patch" bit I am curious about.

Regards

---

### Post by pixelro on 2014-12-19
it's an old post, the "patch" already landed. that patch was for the windowing system. also there are many people working on mir, unity8 :>

---

### Post by grahammechanical on 2014-12-19
> [COLOR=#000000]also there are many people working on mir, unity8[/COLOR]

I was never in doubt of that. :) I was thinking that if I installed the code branch that the developer was using I could test his work before it got merged into trunk. I will experiment with this information and see how it goes. No doubt I will learn something. If only the fact that I am out of my depth. Which I already know.

[https://help.ubuntu.com/community/EasyBazaar](https://help.ubuntu.com/community/EasyBazaar)

Regards

---

