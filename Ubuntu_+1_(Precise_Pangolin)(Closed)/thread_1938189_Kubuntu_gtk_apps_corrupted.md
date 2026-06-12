---
title: "Kubuntu: gtk apps corrupted"
date: 2012-03-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Gavin77 on 2012-03-09
Using Kubuntu 12.04 64bit fully updated.
None of the gtk apps that I use will display correctly.  Attached are 2 examples.  The sliders and checkboxes are unusable.

---

### Post by JMB74 on 2012-03-09
I had that with **oxygen-gtk** and some other themes a few days ago. Switched to Greybird and seems to be OK.

So I presume that the version of Oxygen-gtk you have installed isn't playing well with the current precise GTK version?

---

### Post by Gavin77 on 2012-03-09
I've tried both the gtk-engines-oxygen that is installed by default and a newer version from [https://launchpad.net/~hrvojes/+archive/kde-goodies](https://launchpad.net/~hrvojes/+archive/kde-goodies) with the same result.

It's not a major problem as I've got alternatives to the above apps but I hope it gets fixed soon.

---

### Post by ft_ on 2012-03-09
try to install ```
xsettings-kde
``` and reboot KDE.
I reinstalled kubuntu-desktop but I think it's not necessary.

It worked for me and another ubuntu-fr member (and xsettings-kde belongs to dependancies of meta-package kubuntu-desktop, so that's not a tweak but a real solution).

---

### Post by Gavin77 on 2012-03-09
I already had xsettings-kde installed so I re-installed it and rebooted.  It didn't change anything.

---

### Post by ft_ on 2012-03-10
Do you have *now* the default Kubuntu install or with extra PPA packages for oxygen ?

---

### Post by Gavin77 on 2012-03-10
When I posted my previous message I was using the default install.  Right now I'm using the git version from the ppa, it's still broken.

---

### Post by xeizo on 2012-03-10
Actually, the aforementioned bug is what tipped me over from Kubuntu and back to Ubuntu again. All gtk-apps was unusable in 12.04, I even had inverted colors in their gui ...  Mabe I'll switch back again after the official release, I'm no fan of Unity.

---

### Post by Gavin77 on 2012-03-20
This seems to be fixed now as gtk3-engines-oxygen was just updated and the changelog has "* Set ENABLE_INNER_SHADOWS_HACK=0 to work around a bug in gtk3. (LP: #959031)".

---

### Post by Mr.Pytagoras on 2012-03-21
Hi, I installed the new version of the gtk3-engines-oxygen and the windows are not currupted any more however now they are kinda black

[ATTACH]214703[/ATTACH]

Anybody know how to fix it?

---

### Post by Gavin77 on 2012-03-21
It might be related to this bug [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/951725](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/951725)

Seems to affect nvidia cards.  I'm on Intel graphics and don't have the problem.

---

### Post by Mr.Pytagoras on 2012-03-21
> **Gavin77 said:**
> It might be related to this bug [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/951725](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/951725)

Seems to affect nvidia cards.  I'm on Intel graphics and don't have the problem.

I don't agree

I'm actually using intel graphics too, so it can't be an nvidia cards issue. The problem seems to be with the oxygen gtk theme, because I have tried others themes for gtk and they didn't have this issue, but the problem I'm having now is that if I use oxygen gtk all my gtk2 apps works/looks prefect but all gtk3 apps looks like on that screenshot I posted and if I use other theme that have gtk2/gtk3 support my gtk2 apps looks horible and gtk3 apps look like they should(theme). 

I tried to combine them but no matter what I have done the result was still the same, you had either gtk2 or gtk3 nicely themed, newer both

---

