---
title: "Unity's keyboard shortcut screeen has vanished"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by iowabeakster on 2012-04-11
After updates yesterday (12.04 Ubuntu), the pop-up that lists the keyboard shortcuts is no longer visible.  I talking about the pressing and holding the "super" (windows) key. The numbers on the launcher apps still appear, though.

My wife is trying to adapt to using unity on her new laptop (no mouse) and getting this shortcut hint screen back would be a big help.  Any ideas how to get it back?

---

### Post by jbicha on 2012-04-11
I believe tomorrow (Thursday) we'll be getting a new Unity (5.10) which hopefully will fix a bunch of problems in the current Unity build.

---

### Post by mc4man on 2012-04-11
You could, just to check, run this in a terminal to see if the option is still enabled - should return 'true'

```
gconftool -g /apps/compiz-1/plugins/unityshell/screen0/options/shortcut_overlay
```

---

### Post by xyzzyman on 2012-04-11
Mine shows but doesn't draw a border all the way around. I'm just waiting until Unity 5.10 before looking for a bug report.

EDIT: Couldn't wait. Fixed my shortcut issue.

---

### Post by iowabeakster on 2012-04-12
> **mc4man said:**
> You could, just to check, run this in a terminal to see if the option is still enabled - should return 'true'

```
gconftool -g /apps/compiz-1/plugins/unityshell/screen0/options/shortcut_overlay
```

it does indeed return true.

---

### Post by PaulW2U on 2012-04-13
Just upgraded to Unity 5.10 on my netbook. The shortcut screen is still not displayed when holding down the Windows key. I ran mc4man's command and the result was 'true'.

Anyone else still missing this feature?

---

### Post by Procrustes on 2012-04-13
> **PaulW2U said:**
> Just upgraded to Unity 5.10 on my netbook. The shortcut screen is still not displayed when holding down the Windows key. I ran mc4man's command and the result was 'true'.

Anyone else still missing this feature?

Yep - I am missing it despite the command returning true on my e350

---

### Post by PaulW2U on 2012-04-15
I've reported this. Bug [#982102]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/982102")

I do see the shortcut screen when using my original 12.04 installation on my laptop but not when using the newer installation on my netbook.

Does the size of the screen matter I wonder.

---

### Post by keithpeter on 2012-04-15
> **PaulW2U said:**
> I've reported this. Bug [#982102]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/982102")

I do see the shortcut screen when using my original 12.04 installation on my laptop but not when using the newer installation on my netbook.

Does the size of the screen matter I wonder.

If your netbook is like mine then it has a vertical resolution of 600px. The shortcut overlay seems to be supressed for small screens. When I tried my netbook on an external monitor with the netbook screen turned off, the overlay came back.

So the overlay code is installed, its just checking the size of the screen. I suppose scrolling would be difficult to organise in the overlay.

---

### Post by PaulW2U on 2012-04-15
> **keithpeter said:**
> So the overlay code is installed, its just checking the size of the screen. I suppose scrolling would be difficult to organise in the overlay.

I'm not in a position to use an external monitor with my netbook at present so that's not something I can check for myself. I'll amend the bug report accordingly. Thanks for your input.

---

### Post by PaulW2U on 2012-04-16
I think the latest response to the bug report that can be found at [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/922979/comments/5](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/922979/comments/5) suggests that certain features of Unity on Ubuntu 12.04 will never be supported on netbooks. :sad:

The posts seems to be saying if you can fix it yourself and you can supply a patch then we'll consider releasing it. 

May be I'll just install Lubuntu instead. ](*,)

---

### Post by victorche on 2012-04-16
> **PaulW2U said:**
> I think the latest response to the bug report that can be found at [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/922979/comments/5](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/922979/comments/5) suggests that certain features of Unity on Ubuntu 12.04 will never be supported on netbooks. :sad:

The posts seems to be saying if you can fix it yourself and you can supply a patch then we'll consider releasing it. 

May be I'll just install Lubuntu instead. ](*,)

I don't get it... Is it so hard to design this with scrollers or something? So anyone with a netbook is a "second hand" user?
:confused:

---

