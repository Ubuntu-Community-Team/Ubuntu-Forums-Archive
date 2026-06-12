---
title: "KDE - Fat fonts"
date: 2012-01-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by lucazade on 2012-01-25
In Kubuntu precise fonts look bold instead of regular.
This is probably due to ubuntu-font-family that ships a lot of sub-type (light, regular, bold...) and qt4 is not able to handle this.

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-font-family-sources/+bug/921488](https://bugs.launchpad.net/ubuntu/+source/ubuntu-font-family-sources/+bug/921488)

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-font-family-sources/+bug/921488/+attachment/2692597/+files/pkpEh.png](https://bugs.launchpad.net/ubuntu/+source/ubuntu-font-family-sources/+bug/921488/+attachment/2692597/+files/pkpEh.png)

hints? confirmations?

---

### Post by lucazade on 2012-01-25
there is an older bug report for this: 
[https://bugs.launchpad.net/ubuntu-font-family/+bug/744812](https://bugs.launchpad.net/ubuntu-font-family/+bug/744812)

confirmed now and tracked for precise beta2.

---

### Post by JMB74 on 2012-01-25
I thought the fonts had actually improved. :???:

---

### Post by lucazade on 2012-01-25
@JMB74

It is a matter of tastes. You probably like bold fonts, I prefer to have a consistent behaviour among gtk and qt apps. :)

---

### Post by PaulW2U on 2012-01-25
> **JMB74 said:**
> I thought the fonts had actually improved. :???:

So had I but in some applications such as LibreOffice they have got worse. They're certainly not consistent across applications as lucazade points out. I've never been happy with the fonts in Kubuntu and as a result I've started using Ubuntu again.

---

### Post by lucazade on 2012-01-25
> **PaulW2U said:**
> I've never been happy with the fonts in Kubuntu and as a result I've started using Ubuntu again.

font situation in Kubuntu is quite dramatic, Ubuntu fonts should sparkle in it.. I wonder if there were any kind of quality check before release.

If only kde could get any kind of attention and love by ubuntu devs..

---

### Post by ft_ on 2012-01-26
I unchecked Ubuntu medium font in syst pref, it's enough to avoid any confusion of KDE.

---

### Post by lucazade on 2012-01-26
> **ft_ said:**
> I unchecked Ubuntu medium font in syst pref, it's enough to avoid any confusion of KDE.

It is not enough.. look at the bug report for more info.

---

### Post by ft_ on 2012-01-26
It's enough.
It simply solved, for me at least (and that's for sure !), the confusion between regular and medium Ubuntu fonts.
I've got clean menus, plasma ws and apps.

---

### Post by lucazade on 2012-01-26
> **ft_ said:**
> It's enough.
It simply solved, for me at least (and that's for sure !), the confusion between regular and medium Ubuntu fonts.
I've got clean menus, plasma ws and apps.

not enough and not simply solved in fact the issue has been tracked for precise beta2 and devs are aware of the problem.


plasma doesn't follow hinting and subpixel and this is a different issue.. text in plasma is converted to image  to apply shadow and glow... that's why it is currently broken. Known issue.

---

### Post by VMC on 2012-01-26
I never did like the Kubuntu fonts. I really like Ubuntu fonts though. Over at kubuntu.org this topic has come up and there is a solution of sorts. I don't have the topic on hand but it has something to do with anti-aliasing

---

### Post by ft_ on 2012-01-26
I repeat in a different way : for me there is no more issue, i.e. I'm not worried. That does not mean the bug is not still open.
**Hinting rvb full.**

I've got the exact rendering as Oneiric's one I got, clean on plasma, menus and firefox eg.

---

### Post by lucazade on 2012-01-26
> **ft_ said:**
> I repeat in a different way : for me there is no more issue, i.e. I'm not worried. That does not mean the bug is not still open.
**Hinting rvb full.**

I've got the exact rendering as Oneiric's one I got, clean on plasma, menus and firefox eg.

You can find also a third way to express it.. but what really matters is that *default* settings work as expected.
This means slighthinting, rgb, 96dpi and ubuntu fonts.

If you like full hinting, rvb it is up to you. Ubuntu fonts are not meant to work with those settings.

QT4 apps are not able to use Ubuntu font type correctly, they use medium weight instead of regular. We're discussing about this bug, currently wip, not about personal preferences.

---

### Post by cottfcfan on 2012-03-24
I know this thread is now 2 months old, but has a fix been released for this problem yet?
All my QT apps in Ubuntu 12.04 still have fat fonts.

---

### Post by lucazade on 2012-03-24
> **cottfcfan said:**
> I know this thread is now 2 months old, but has a fix been released for this problem yet?
All my QT apps in Ubuntu 12.04 still have fat fonts.

haven't tried kde4 lately.. so no idea if fixed.
I've seen there was some work in the bug report..

---

### Post by mparillo on 2012-03-24
> **cottfcfan said:**
> I know this thread is now 2 months old, but has a fix been released for this problem yet?
All my QT apps in Ubuntu 12.04 still have fat fonts.

I thought things looked a whole lot better after a clean install of Kubuntu 12.04 Beta1.

---

### Post by cottfcfan on 2012-03-24
Sorry I think you misunderstand.
I am running Ubuntu not Kubuntu, but using QT apps like luckybackup & keepassx with the Ubuntu font is just not integrating into the Desktop.
Fonts are too fat.

---

### Post by PaulW2U on 2012-03-24
> **cottfcfan said:**
> Sorry I think you misunderstand.
I am running Ubuntu not Kubuntu, but using QT apps like luckybackup & keepassx with the Ubuntu font is just not integrating into the Desktop.
Fonts are too fat.

But the original poster was referring to **K**ubuntu. The *fatter* fonts are making my KDE experience better than ever. If I boot into the Natty or Oneiric versions of Kubuntu that I have installed, I don't like what I see. :(

---

### Post by cottfcfan on 2012-03-24
> **PaulW2U said:**
> But the original poster was referring to **K**ubuntu. The *fatter* fonts are making my KDE experience better than ever. If I boot into the Natty or Oneiric versions of Kubuntu that I have installed, I don't like what I see. :(

I realize that now that I have read the thread again, sorry.
Regardless the same problem exists in Ubuntu, using kde apps.

---

### Post by craig10x on 2012-03-24
Hmmm.....interesting....i run ubuntu 11.10 and use k3b (kde-qt app) and VLC media player (not kde specific...it is cross platform but also a qt application) and the font's look exactly the same as they do on all my gnome programs...

---

### Post by cottfcfan on 2012-03-24
They are OK in 11.10, but not 12.04.
If I change my Font to sans for instance, no problem.
It just seems to affect the Ubuntu font.
The apps I run are keepassx & luckybackup.

---

### Post by lucazade on 2012-03-24
> **cottfcfan said:**
> They are OK in 11.10, but not 12.04.
If I change my Font to sans for instance, no problem.
It just seems to affect the Ubuntu font.
The apps I run are keepassx & luckybackup.

because sans doesn't have a medium font-type like Ubuntu font, so it doesn't suffer of the same problem. (anyway in the bug report available in OP the issue is well known)

---

### Post by PaulW2U on 2012-03-31
Original bug report now showing as "Fix Released" - [https://bugs.launchpad.net/ubuntu-font-family/+bug/744812](https://bugs.launchpad.net/ubuntu-font-family/+bug/744812).

---

### Post by cottfcfan on 2012-03-31
Yep.
Ubuntu fonts now rendering properly in all apps.

---

### Post by mparillo on 2012-03-31
> **cottfcfan said:**
> Yep.
Ubuntu fonts now rendering properly in all apps.

Agreed, but when I read this:
  * Don't ship Ubuntu Medium ("Ubuntu Light" "Bold") because
    of issues with the font/toolkit stacks on Ubuntu not working.
    Workaround for (LP: [#744812]("https://bugs.launchpad.net/bugs/744812")).
It reads more like a work-around than a fix.

---

