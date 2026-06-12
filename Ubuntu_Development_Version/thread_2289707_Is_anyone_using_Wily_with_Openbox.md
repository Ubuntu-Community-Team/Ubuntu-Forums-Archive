---
title: "Is anyone using Wily with Openbox?"
date: 2015-08-06
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-08-06
Is anyone using Wily with Openbox WM? 

Works very well with kernel 4.0.0.4-generic. I had a problem with Lxapperance and Lxkeypad, but are resolved now, thanks to Sudodus.
When dist-upgraded, the kernel 4.1.0.3-generic, X didn't start, so I looked in the /boot folder. The upgrade process had not given read-only permission for the Group and Others, so I opened /boot as root and gave those permissions, and the kernel booted up quite nicely. 

Ubuntu Wily base, Openbox, Compton, Xfce4-mixer, Xfce4-power-manager, Xfce4-terminal, Xfce4-volumed, network-manager-gnome, Policykit1-gnome, Conky, Tint2 and some apps. I haven't installed LibreOffice, Vlc, Gimp or Wine yet, but have installed Skype.

Have a look,
[[IMG]http://s5.postimg.org/djj11pm5v/Ubu_Wily_Openbox.jpg[/IMG]]("http://postimg.org/image/djj11pm5v/")
clean,

[[IMG]http://s5.postimg.org/52jiqshgz/Ubu_Wily_Openbox_Dirty.jpg[/IMG]]("http://postimg.org/image/52jiqshgz/")
With Obmenu-generator

---

### Post by Chanath on 2015-08-06
I've been testing our development releases for a long time. I had Ubuntu, Gnome, Kubuntu and Xubuntu Wily. I still have Kubuntu and Xubuntu, dist-upgraded every few days. It'd become boring as nothing is happening. So, this try, and that was done within one day, in between work and food. This installation is after few dist-upgrades, and not much trouble. Would someone try too, for example with Fluxbox? You can get the Wily Mini.iso from here; [http://mirror.yandex.ru/ubuntu-cdimage/netboot/wily/](http://mirror.yandex.ru/ubuntu-cdimage/netboot/wily/) Most probably it is available in other repos too.

Openbox is a WM and it is sort of DE agnostic, so I think this Wily Openbox installation could be upgraded to 16.04 without much trouble. The other matter is, when one gets used to Openbox, one doesn't want to move to any other DEs.

I'm trying to create a live iso out of my Openbox installation. I'm not a geek, so it'd take some time. What do you guys think?

---

### Post by syntaxerror74 on 2015-08-10
> **Chanath said:**
> Is anyone using Wily with Openbox WM? 

/me :D 

> Works very well with kernel 4.0.0.4-generic. I had a problem with Lxapperance and Lxkeypad, but are resolved now, thanks to Sudodus.

lxappearance was indeed a bug with openbox 3.5.2 and older, see here:
[https://bugs.launchpad.net/ubuntu/+source/lxappearance/+bug/1469276](https://bugs.launchpad.net/ubuntu/+source/lxappearance/+bug/1469276)

Was a sort of a risk for me to upgrade openbox to (then-proposed) 3.6.x but lxappearance was just essential.

---

### Post by Chanath on 2015-09-27
Still using Openbox. No problems up to today. :D

---

### Post by Irihapeti on 2015-09-27
I've got wily with Openbox on my old EeePC 900, running on an external SD card. It's a fairly minimal install and I don't use it every day, but it seems to behave fine as far as I can tell.

---

### Post by Chanath on 2015-10-09
While I believe desktop environments are needed, I don't feel like moving to any, as Openbox does a very good job, while staying out of the way. No problems to report yet. Anyone else using Openbox, or any other WM without a DE?

---

### Post by zika on 2015-10-09
[img]http://www.zappos.com/boutiques/123/MeToo_header060313.gif[/img]for so many years... ;)

---

### Post by oldos2er on 2015-10-10
> **Chanath said:**
> While I believe desktop environments are needed, I don't feel like moving to any, as Openbox does a very good job, while staying out of the way. No problems to report yet. Anyone else using Openbox, or any other WM without a DE?

I occasionally use i3 version 4.10.3. No issues to speak of.

---

