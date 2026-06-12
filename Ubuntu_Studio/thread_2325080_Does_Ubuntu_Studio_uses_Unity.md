---
title: "Does Ubuntu Studio uses Unity?"
date: 2016-05-18
forum: Ubuntu Studio
---

### Post by javierdl on 2016-05-18
I was wondering if I could use the Unity Tweak Tool with US too.

---

### Post by vasa1 on 2016-05-18
Interesting question!

I'm guessing the tweak tool just provides a nice GUI for editing various config files (and some may not be editable using plain text editors). Have you looked at what it will pull in if installed?

```
sudo apt-get install -s unity-tweak-tool
```should give you a clue (**-s** indicates that just a simulation will be run).

To my mind, it's going to bring in everything related to unity!

On my system, that command wants to install 243 new packages. You may see a different figure.

Using ```
--no-install-recommends
```reduces that figure to 99.

BTW, do you have some specific tweak in mind for which you need help?

---

### Post by javierdl on 2016-05-19
Thanks for replying vasa1, and for asking :)

Yes, I need to use Blender. But I can't orbit around objects as I used to. Normally I do it holding Alt. I did it in Ubuntu 14.04, but with the help of either the Unity Tweak Tool, or the Compiz Configuration Settings Manager. You can find more info on this in this [2-post thread]("http://askubuntu.com/questions/687875/how-to-orbit-in-blender-without-a-mmb-these-days"). I must have obtained the info on the second post from somewhere else.

---

### Post by jejeman on 2016-05-20
Change the ALT shortcut to Super key or something else.
Go to **Settings Manager > Window Manager Tweaks > Accessibility** and change ALT to something else.

No, Ubuntu Studio uses XFCE not Unity.

---

### Post by yoshii on 2016-05-20
I did use TweakTool on Ubuntu Studio v14.04.3(?) yet you have to be very careful and only use it for things like filetype associations and not much else.  
It's so old that it's compatibility is probably risky.  Ubuntu Studio uses Xfce, as already stated, but it's application menu component is different from Xubuntu, which also uses Xfce.

---

### Post by javierdl on 2016-05-21
jejeman,
That's just what I needed! No need to install any additional utilities!
Thanks a bunch! :)

J

---

