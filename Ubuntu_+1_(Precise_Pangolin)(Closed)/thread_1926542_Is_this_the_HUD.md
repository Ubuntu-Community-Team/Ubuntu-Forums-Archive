---
title: "Is this the HUD?"
date: 2012-02-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Gregory Lee on 2012-02-16
I just did my routine update with "aptitude update" and "aptitude safe-upgrade" and got a new version of Compiz.  I see some ghostly rectangles on my desktop which might be vestiges of the rumored HUD.

---

### Post by philinux on 2012-02-16
> **Gregory Lee said:**
> I just did my routine update with "aptitude update" and "aptitude safe-upgrade" and got a new version of Compiz.  I see some ghostly rectangles on my desktop which might be vestiges of the rumored HUD.

[http://www.omgubuntu.co.uk/2012/01/hud-new-unity-feature/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29](http://www.omgubuntu.co.uk/2012/01/hud-new-unity-feature/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG!+Ubuntu!%29)

Without a screenshot you could be seeing a compiz or graphics problem.

Also see this thread. [http://ubuntuforums.org/showthread.php?t=1925433](http://ubuntuforums.org/showthread.php?t=1925433)

---

### Post by andrek on 2012-02-16
Yeah, it's a compiz-related problem.

[[IMG]http://i.imgur.com/rpDB7l.png[/IMG]](http://i.imgur.com/rpDB7.png)

---

### Post by ernestj on 2012-02-16
I have the same problem, can I or do I fix it or wait till a new update fixes it?

---

### Post by jrothwell97 on 2012-02-16
Well, there's a bug [here](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/933615) should you want to mark it as affecting you.

---

### Post by Gregory Lee on 2012-02-16
> **ernestj said:**
> I have the same problem, can I or do I fix it or wait till a new update fixes it?
I suggest waiting.  (I think the answer to my question is "no".)  The next thread down on "menu shadows" claims there is already a new fixed Compiz package (but I'm not seeing it yet).

---

### Post by grahammechanical on 2012-02-16
That is not the HUD. Run the mouse over the ghostly panels and you will see the menu items appear.

Imagine the Dash search panel without the accompanying pane. That is the HUD; a search panel that reaches more than half way across the screen under the top panel. But you will not see it unless you tap the super key. 

I have the  HUD because I put a PPA in my Software Sources specifically to install a version of Unity with the HUD to take part in testing it before it gets added to Precise.

I would say that the HUD still needs some things to be fixed before it becomes a part of Precise. Further testing might be needed. Something like the HUD has to work precisely to be included in Precise and so I do not think that there is any hardship to wait until even the last few days before distribution release to get things right.

Regards.

---

### Post by Gregory Lee on 2012-02-16
> **grahammechanical said:**
> Imagine the Dash search panel without the accompanying pane. That is the HUD; a search panel that reaches more than half way across the screen under the top panel. But you will not see it unless you tap the super key. 

When I tap the super key, a translucent Dash panel does appear.  Is that all the HUD is?

---

### Post by mc4man on 2012-02-16
What you're seeing is from the new compiz upgrade - empty reqtangular boxes are created by some actions, easiest is to just open any menu or context menu

The menus windows aren't being destroyed when they are closed
screen on a new install

---

### Post by VinDSL on 2012-02-16
> **Gregory Lee said:**
> [...] might be vestiges of the rumored HUD.
Heh!  I've been referring to it (lovingly) as "DUD".  :D

From all the negativity I've read, I was expecting HUD to blow up in my face, but all it does is sit there.

I can't see any difference at all, so far!

---

### Post by philinux on 2012-02-16
> **Gregory Lee said:**
> When I tap the super key, a translucent Dash panel does appear.  Is that all the HUD is?

You need to watch the video in the link I posted in post #2

---

### Post by Milos_SD on 2012-02-16
Just lower everything in Active and Inactive Shadows in CCSM -> Window decorations. X and Y offset put to 0.

That shadows are the least of my problems with new compiz. :)

It happends all the time, that my mouse get stucked in click mode, and I can not write or click anywhere. I'm in KDE right now, until this is fixed. :)

---

### Post by jppr on 2012-02-16
[https://lists.ubuntu.com/archives/precise-changes/2012-February/010082.html](https://lists.ubuntu.com/archives/precise-changes/2012-February/010082.html)

---

### Post by mc4man on 2012-02-16
> **Milos_SD said:**
> Just lower everything in Active and Inactive Shadows in CCSM -> Window decorations. X and Y offset put to 0.

That shadows are the least of my problems with new compiz. :)

It happends all the time, that my mouse get stucked in click mode, and I can not write or click anywhere. I'm in KDE right now, until this is fixed. :)

On a new install today, updated, even that doesn't help with the shadows 
Also seeing cursor getting stuck on click though it happens at random here, can't find a way to cause at will.
Have switched to unity-2d for a while to see it it also  happens there

---

### Post by Gregory Lee on 2012-02-16
> **philinux said:**
> You need to watch the video in the link I posted in post #2
I did watch it, thank you.  I also watched a pretty neat related video [Ubuntu 12.04 LTS - Unity 5.0/HUD]("http://www.youtube.com/watch?feature=player_embedded&v=q49P6czyPs0#%21").  So you'd think I would know if I now have the HUD.  I don't see the depicted functionality on my system, but maybe I just don't know how to invoke it.  Anyhow, I don't yet know whether I actually have some version of the HUD.

---

### Post by andrek on 2012-02-16
Updated compiz is already built for i386, currently building for amd64...
**and done!**

---

### Post by philinux on 2012-02-16
> **Gregory Lee said:**
> I did watch it, thank you.  I also watched a pretty neat related video [Ubuntu 12.04 LTS - Unity 5.0/HUD]("http://www.youtube.com/watch?feature=player_embedded&v=q49P6czyPs0#%21").  So you'd think I would know if I now have the HUD.  I don't see the depicted functionality on my system, but maybe I just don't know how to invoke it.  Anyhow, I don't yet know whether I actually have some version of the HUD.

What version of unity have you got.

 [http://ubuntuforums.org/showthread.php?t=1925433](http://ubuntuforums.org/showthread.php?t=1925433)

---

### Post by arpanaut on 2012-02-16
@Gregory Lee
Unless you added the PPA to your sourses and explicitly installed the compiz version w/ HUD,
then you don't have any HUD bits on your 'puter yet.  If you are using standard repos then,
It has not arrived yet, and from looking at the testing posts, it may be a while.

---

### Post by andrek on 2012-02-16
Aaaaaand it's fixed! compiz 0.9.7.0~bzr2995-0ubuntu3
Thank god

---

### Post by Milos_SD on 2012-02-16
compiz 0.9.7.0~bzr2995-0ubuntu3 wants to remove unity and ubuntu-desktop on amd64. :(

---

### Post by andrek on 2012-02-16
That's weird, are you sure that this particular package causes this? 
If yes, try to download and install those from [https://launchpad.net/ubuntu/+source/compiz/1:0.9.7.0~bzr2995-0ubuntu3/+build/3218193](https://launchpad.net/ubuntu/+source/compiz/1:0.9.7.0~bzr2995-0ubuntu3/+build/3218193)

---

### Post by Milos_SD on 2012-02-16
Everything is ok now, all packages are here. :)

---

### Post by ernestj on 2012-02-16
Great it is fixed. When does the fix come through the updates? or do I have to manually do something?

Ernie

---

### Post by mc4man on 2012-02-16
The 'fix' to compiz was to revert a patch that attempted to fix this bug & a similar one
[https://bugs.launchpad.net/compiz-core/+bug/931473](https://bugs.launchpad.net/compiz-core/+bug/931473)

Myself had never seen before but on a fresh install with the new compiz can now get ocassionally

---

### Post by jrothwell97 on 2012-02-16
> **ernestj said:**
> Great it is fixed. When does the fix come through the updates? or do I have to manually do something?

Ernie

The fixed package has been built and released on the main mirror, but it might take a bit of time (read: a couple of hours, tops) for your mirror to receive it. Keep checking for updates and it'll show once it comes through :)

---

### Post by Milos_SD on 2012-02-16
Shadows bug is fixed. But the issue with stucked mouse click on indicators (they don't actualy open, they just get there round borders like I clicked on them). And then I can't write at all ( keys don't respond at all). I had to do "metacity --replace" to be able to write this post. I can't even open Dash, clicks work only on window that is focused in that time when that happends. Not to mention that, somethimes I can't open windows that are minimized, they don't render at all.

---

### Post by Gregory Lee on 2012-02-16
> **arpanaut said:**
> @Gregory Lee
Unless you added the PPA to your sourses and explicitly installed the compiz version w/ HUD,
then you don't have any HUD bits on your 'puter yet.  If you are using standard repos then,
It has not arrived yet, and from looking at the testing posts, it may be a while.
I did not add PPA or install a testing version of Compiz -- I'm all standard.  I did see Compiz packages come up after "aptitude safe-upgrade", but I guess this was not yet the version with HUD.  I don't know what version of Unity I have.

---

### Post by cariboo on 2012-02-16
@Gregory Lee, open a terminal and type:

```
unity --version
```

to find out what version you are using.

---

### Post by Gregory Lee on 2012-02-16
> **cariboo907 said:**
> ```
unity --version
```to find out what version you are using.
It's 5.2.0.  (The man page for unity does not list a "--version" option.)

---

### Post by Gregory Lee on 2012-02-16
I got the fixed version of Compiz without menu shadows.  I saw this during "aptitude safe-upgrade":
```
 Setting up compiz-core (1:0.9.7.0~bzr2995-0ubuntu3) ...
```
However, it didn't actually get fixed until I rebooted.

---

### Post by cariboo on 2012-02-16
> **Gregory Lee said:**
> It's 5.2.0.  (The man page for unity does not list a "--version" option.)

Try:

```
unity --help
```

---

### Post by Gregory Lee on 2012-02-16
> **cariboo907 said:**
> Try:

```
unity --help
```
The man page for unity doesn't give a "--help" option.

---

### Post by cariboo on 2012-02-16
Just because the manpage doesn't give you a help option doesn't mean it isn't there, this is the output I get from the --help option:

```
unity --help
Usage: unity [options]

Options:
  --version         show program's version number and exit
  -h, --help        show this help message and exit
  --advanced-debug  Run unity under debugging to help debugging an issue. /!\
                    Only if devs ask for it.
  --debug           Run unity under gdb and print a backtrace on crash. /!\
                    Only if devs ask for it.
  --distro          Remove local build if present with default values to
                    return to the package value (this doesn't run unity and
                    need root access)
  --log=LOG         Store log under filename.
  --replace         Run unity /!\ This is for compatibility with other desktop
                    interfaces and acts the same as running unity without
                    --replace
  --reset           Reset the unity profile in compiz and restart it.
  --reset-icons     Reset the default launcher icon.
  -v, --verbose     Get additional debug output from unity.
```

---

### Post by Gregory Lee on 2012-02-16
> **cariboo907 said:**
> Just because the manpage doesn't give you a help option doesn't mean it isn't there, ...
Yes, sorry, I was just kidding.

---

### Post by Gregory Lee on 2012-02-17
Now, I do have the HUD.  But it's not 100% clear how to see it.  The write-up I saw says to press Alt to see it.  That doesn't work.  You have to *tap* Alt to see it.

---

