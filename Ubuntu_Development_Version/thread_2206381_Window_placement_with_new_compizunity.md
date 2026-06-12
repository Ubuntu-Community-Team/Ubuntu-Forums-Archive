---
title: "Window placement with new compiz/unity"
date: 2014-02-18
forum: Ubuntu Development Version
---

### Post by mc4man on 2014-02-18
Here on a couple of installs the 2nd un maxed window opened on a workspace can open 1 px to adjacent ws & several px to below ws, - depends on what Ws the 2 windows are opened on  (2nd window on ws1 spills on to ws2  & in a 2x2 to ws3
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1281816](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1281816)

---

### Post by ventrical on 2014-02-18
I read your bug report and I still do not understand  what you mean (how to replicate the bug).

Thanks

---

### Post by ventrical on 2014-02-18
ok.. Very weird thing happened here. I tried what I think you meant and now I have only 2 workspaces (previously had 8) and when I went to use ccsm<general options to switch to four it indicated there was only 1 ws and then zoomed into this split, vertical zoom windows that I cannot get out of.

---

### Post by mc4man on 2014-02-18
Not sure what you  have there in screen??

This may show you what I mean, - (back on my real install which is 1x4 but notice part of the 2nd nautilus window is below the visible screen & 1 px into Ws 2 - the white line
```
wget http://ubuntuone.com/2VUO0HYxgghL75471nmNeC
```

---

### Post by grahammechanical on 2014-02-18
@ventrical

This is most probably not appropriate, but if we have Gnome Flashback installed and in the With Compiz session we set the number of workspaces by right clicking on the workspace icon in the bottom panel and selecting Preferences, then it overrides any setting in CCSM, even when we are back in Unity.

Regards.

---

### Post by ventrical on 2014-02-19
> **grahammechanical said:**
> @ventrical

This is most probably not appropriate, but if we have Gnome Flashback installed and in the With Compiz session we set the number of workspaces by right clicking on the workspace icon in the bottom panel and selecting Preferences, then it overrides any setting in CCSM, even when we are back in Unity.

Regards.

Ahhh ... yes indeed it does.

Thanks 

Regards..

---

### Post by ventrical on 2014-02-19
> **mc4man said:**
> Not sure what you  have there in screen??

This may show you what I mean, - (back on my real install which is 1x4 but notice part of the 2nd nautilus window is below the visible screen & 1 px into Ws 2 - the white line
```
wget http://ubuntuone.com/2VUO0HYxgghL75471nmNeC
```



 Yes .. same here.

+1 mee tooed it.



 Thanks.

---

### Post by mc4man on 2014-02-23
There is another small issue, only happens when multiple unmaxed windows of one app are on 1 workspace
(if any other app is open doesn't occur
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1283775](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1283775)

The other bug, (2nd/3rd window opening into other workspace(s) is really becoming a pita, unfortunately any other window place method isn't as good as 'smart'

The other 'issue' is that if one opens an unmaxed window (defaults to top left corner), then minimizes it, the next window opened goes to bottom right, ie. the space the now minimized window occupied is still seen as taken.
Don't have a saucy install to see if the same occurred there..

---

