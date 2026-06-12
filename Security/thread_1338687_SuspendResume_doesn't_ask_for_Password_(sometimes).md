---
title: "Suspend/Resume doesn't ask for Password (sometimes)"
date: 2009-11-26
forum: Security
---

### Post by Cuco3 on 2009-11-26
Before anything, Google searches revealed no information.

This started happening about 3 weeks ago. Sometimes when I resume from Suspend, Ubuntu goes right to the desktop without asking for a P/W. Being a Systems Administrator, I like to practice secure computing. As you can see, this presents a huge problem for me.

Here's my Apps/Gnome-Power-Management/Lock settings in GConf Editor:
[IMG]http://img6.imageshack.us/img6/3043/screenshot1mr.png[/IMG]


Has this happened to anyone before?
Were you able to fix it?
Should I file a bug report?

_Specs_
CPU:2.4 GHz Pentium 4
MB: Intel D845PESV
RAM: 1GB RAM
HD: 80GB WD 8MB cache PATA
Video: nVidia GeForce 7600 GS AGP
Sound: SoundBlaster Live! PCI
OS: Dual Boot; Win XP SP3 & Ubuntu 9.04

---

### Post by EJeanmaire on 2009-11-27
> **Cuco3 said:**
> Before anything, Google searches revealed no information.

This started happening about 3 weeks ago. Sometimes when I resume from Suspend, Ubuntu goes right to the desktop without asking for a P/W. Being a Systems Administrator, I like to practice secure computing. As you can see, this presents a huge problem for me.

Here's my Apps/Gnome-Power-Management/Lock settings in GConf Editor:
[IMG]http://img6.imageshack.us/img6/3043/screenshot1mr.png[/IMG]


Has this happened to anyone before?
Were you able to fix it?
Should I file a bug report?

_Specs_
CPU:2.4 GHz Pentium 4
MB: Intel D845PESV
RAM: 1GB RAM
HD: 80GB WD 8MB cache PATA
Video: nVidia GeForce 7600 GS AGP
Sound: SoundBlaster Live! PCI
OS: Dual Boot; Win XP SP3 & Ubuntu 9.04

Not that I have an answer to you question but look on the bright side, atleast you don't have my problem whereas if I lock the screen, it refuses my password on unlock.

---

### Post by mumi on 2009-11-27
Make sure that the proces "gnome-screensaver" is running. You can find it in menu->system->preference->startup applications->"gnome-screensaver".
I know, it says screensaver, but it also controls the password/lock mechanisme. I found this on the hard way :0).

You say sometimes: maybe it is because you have done something to that proces! Or a program/proces is making some complications with it.

Good luck.

---

### Post by Rebelli0us on 2009-11-27
I found the same problem, no prompt for password on resume. See the last post in this thread


[http://ubuntuforums.org/showthread.php?p=8396836#post8396836](http://ubuntuforums.org/showthread.php?p=8396836#post8396836)

---

### Post by Cuco3 on 2009-11-28
> **mumi said:**
> Make sure that the proces "gnome-screensaver" is running. You can find it in menu->system->preference->startup applications->"gnome-screensaver".
I know, it says screensaver, but it also controls the password/lock mechanisme. I found this on the hard way :0).

Thanks for your help. The "gnome-screensaver" process isn't listed as part of the "Startup Applications." The only thing close to screensaver would be "Power Manager."

Note: "gnome-screensaver" is running as a process.

> **mumi said:**
> You say sometimes: maybe it is because you have done something to that proces! Or a program/proces is making some complications with it.

Good luck.That's my hunch. I have installed a lot of programs, most of them through the repositories, and I'm pretty sure one program just made a change somewhere. But still, the random occurrence of this suggests it's something that might have gotten changed with the way power management or screensaver works.

---

### Post by Cuco3 on 2009-11-28
> **Rebelli0us said:**
> I found the same problem, no prompt for password on resume. See the last post in this thread


[http://ubuntuforums.org/showthread.php?p=8396836#post8396836](http://ubuntuforums.org/showthread.php?p=8396836#post8396836)Thank you for your reply. I'm glad someone else is experiencing this, meaning we can file a bug report. Anyone else experiencing this problem?

---

### Post by Cuco3 on 2009-12-19
I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+bug/498694](https://bugs.launchpad.net/ubuntu/+bug/498694)

---

