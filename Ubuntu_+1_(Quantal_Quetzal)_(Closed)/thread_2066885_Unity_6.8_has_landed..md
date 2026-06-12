---
title: "Unity 6.8 has landed."
date: 2012-10-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philinux on 2012-10-05
[http://www.iloveubuntu.net/unity-68-landed-ubuntu-1210-support-enabledisable-online-search-results-visual-refinements-and](http://www.iloveubuntu.net/unity-68-landed-ubuntu-1210-support-enabledisable-online-search-results-visual-refinements-and)

I though I'd post this here as well as the sticky for discussion.

---

### Post by Frogs Hair on 2012-10-05
I have been using Unity 6.8, but have proposed updates enabled and don't know if all 12.10 users have it yet. The feature allowing or blocking internet content in privacy is nice. The Amazon and Ubuntu store search seem to work fine.

---

### Post by GreatDanton on 2012-10-06
> **Frogs Hair said:**
> The feature allowing or blocking internet content in privacy is nice. The Amazon and Ubuntu store search seem to work fine.

I agree. Finally step in the right direction.

---

### Post by VinDSL on 2012-10-06
> **Frogs Hair said:**
> The feature allowing or blocking internet content in privacy is nice.
> **GreatDanton said:**
> I agree. Finally step in the right direction.

I have yet to see this System Settings-->Privacy option show up.

```
vindsl@Zuul:~$ unity --version
unity 6.8.0
```

---

### Post by VinDSL on 2012-10-06
Aha!  Figured it out...

Had to install "activity-log-manager-control" to get the "Privacy" option.  :guitar:

---

### Post by Milos_SD on 2012-10-07
I can't use "metacity --replace" script anymore with this Unity version. What is changed that prevents this?

---

### Post by stinkeye on 2012-10-07
**metacity --replace** still works.
What does the script do?

---

### Post by philinux on 2012-10-07
> **Milos_SD said:**
> I can't use "metacity --replace" script anymore with this Unity version. What is changed that prevents this?

Metacity has been removed iirc 
[http://www.theorangenotebook.com/2012/08/call-for-testing-compiz-unity.html?m=1](http://www.theorangenotebook.com/2012/08/call-for-testing-compiz-unity.html?m=1)

---

### Post by Milos_SD on 2012-10-07
> **stinkeye said:**
> **metacity --replace** still works.
What does the script do?

It is a .desktop file with this content:

```

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=gnome-panel-launcher
Name[en_US]=metacity
Exec=metacity --replace
Name=metacity
Icon=gnome-panel-launcher
```

I realy need this, becouse I can't play games with Compiz enabled.

---

### Post by mc4man on 2012-10-07
> **Milos_SD said:**
> I can't use "metacity --replace" script anymore with this Unity version. What is changed that prevents this?
You'd probably be better off to just log into a Classic (no effects) session to play games or whatever.

If you want metacity --replace to give you control of your windows (wm) from an ubuntu session then you'll need to enable compositing for metacity - in dconf
org.gnome.metacity compositing-manager true
 
Edit: - just to note - it may not just good enough to run metacity --replace (kill compiz), after that if need be then start metacity (/usr/share/applications/metacity or like in screen

---

### Post by Cyber72 on 2012-10-10
I'm fairly new to ubuntu (12.04) what are the pros and cons of

a) sticking to my current version of unity (how do I check which version I have?)
b) give them a couple of months to debug before upgrading
c) upgrade now
or is it a case of 
d) It will upgrade itself at a time of it's own choosing

Also should I be excited by this news?

---

### Post by Cyber72 on 2012-10-10
And is the workspace switcher still stuck at the bottom of the launcher?

---

### Post by mcellius on 2012-10-10
> **Cyber72 said:**
> I'm fairly new to ubuntu (12.04) what are the pros and cons of

a) sticking to my current version of unity (how do I check which version I have?)
b) give them a couple of months to debug before upgrading
c) upgrade now
or is it a case of 
d) It will upgrade itself at a time of it's own choosing

Also should I be excited by this news?

You can check your version of unity by typing the following code into a terminal:

```
unity --version
```

I like the newer unity, but that's a subjective thing.

As to whether to upgrade now or wait awhile, I'm beginning to think it depends on your hardware.  I have two Dells - a desktop and a laptop, both with Intel graphics - and they work extremely well with 12.10 (as also with 12.04).  I've read about lots of difficulties with Nvidia and ATI graphics, though, so with those I might want to wait a bit to see if they get things fixed.

Your 12.04 won't uprade itself to 12.10, although it is likely over time that some of the fixes and features will find themselves into 12.04 ... eventually.

---

### Post by fjgaude on 2012-10-10
> **Cyber72 said:**
> And is the workspace switcher still stuck at the bottom of the launcher?

No, you can move it up and down like the other apps.

---

### Post by Rukiri on 2012-10-10
Has anyone seen or made a PPA for unity 6.8 for 12.04? I'm asking as my main setup with ubuntu is ZFS and ZFS doesn't work at all in 12.10 because the PPAs aren't there yet.

---

### Post by Cyber72 on 2012-10-11
Thanks mcellius and fjgaude.

---

