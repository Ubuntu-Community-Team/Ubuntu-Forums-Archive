---
title: "Bottom Launcher Commands"
date: 2016-03-26
forum: Ubuntu Development Version
---

### Post by Frogs Hair on 2016-03-26
Tested the following commands and launcher position did survive reboot. No additional software required other than an up to date Unity package.
```

gsettings set com.canonical.Unity.Launcher launcher-position Bottom
```

```
gsettings set com.canonical.Unity.Launcher launcher-position Left
```

---

### Post by QDR06VV9 on 2016-03-26
Nice Share Frogs Hair.. Thanks:D

---

### Post by craig10x on 2016-03-31
Just wondering...over the weekend, i am going to a run a live session iso of ubuntu 16.04 LTS and would like to try the "move launcher to the bottom" command...Will it just change automatically?.. it doesn't require a reboot, does it? (which of course, i would not be able to do on a live session)....Thanks....

---

### Post by howefield on 2016-03-31
> **craig10x said:**
> Just wondering...over the weekend, i am going to a run a live session iso of ubuntu 16.04 LTS and would like to try the "move launcher to the bottom" command...Will it just change automatically?.. it doesn't require a reboot, does it? (which of course, i would not be able to do on a live session)....Thanks....

Should be automatic... at least I just tried it and the launcher moved instantly.

---

### Post by mc4man on 2016-03-31
you can also do so thru dconf-editor, the change is immediate

---

### Post by craig10x on 2016-03-31
Thanks Guys...should be interesting to try :D

---

### Post by danc-dccathome on 2016-03-31
Can it be moved to the top and centered?

---

### Post by deadflowr on 2016-03-31
> **danc-dccathome said:**
> Can it be moved to the top and centered?

No.

---

### Post by howefield on 2016-04-01
> **danc-dccathome said:**
> Can it be moved to the top and centered?

Ubuntu Kylin (who drove the enabling work as I understand it) has the launcher by default set to the bottom, the rest of us can use the command line to switch or install and use dconf as pointed out by mc4man. But it is only bottom or left.

Much as I prefer the launcher on the left, it does look good at the bottom on a large screen.

---

### Post by MikeMecanic on 2016-04-01
Thanks for sharing these two miraculous command lines Frog Hair.  

I try it on Ubuntu March 27th build and it is working perfectly.

Will give it a try in Kylin next time.  The Kylin team set the launcher(default) to the bottom last week and it comes with new icons all over the system.  

Much more easier that way, thanks a lot.

---

### Post by fjgaude on 2016-04-02
> **howefield said:**
> Should be automatic... at least I just tried it and the launcher moved instantly.

Yep, works like a charm. But for me, it is not where I want it, to the left, where I need all the vertical space I can get. Others may have other reasons for the Launcher to be at the bottom.

---

### Post by craig10x on 2016-04-02
You can "Auto hide" it you know (so that you only bring it up for a few seconds to launch something) that can be done whether it is on the left or the bottom...When auto hidden, it doesn't take up any space (horizontal or vertical) except for the few seconds you are using it...

And of course you can also shrink the size of the icons...for my 17 inch laptop screen, i have always shrunk my icons to about 38 pixels, which i felt looked better then the full size icons (even when using on the left side)...

---

