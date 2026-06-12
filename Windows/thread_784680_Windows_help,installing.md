---
title: "Windows help,installing"
date: 2008-05-06
forum: Windows
---

### Post by mattme on 2008-05-06
Hi

My computer came with windows, but I never booted into it, installed ubuntu and shrank windows away.

I've concluded that the company who sold me it, ACER, will never be refunding me the £60 for the value of windows.

If I boot into windows (I don't know how right now, it is missing from grub) and proceed with the install, will grub survive?

it is xp media centre edition, which is worth a fifth of the value of the computer!

Matt

---

### Post by tamoneya on 2008-05-06
if you boot into windows through grub, grub will be left intact.  It will only be messed with if you go into recovery console on the xp install disk and type ```
fixmbr
``` As for how to get windows to boot from grub please post the output of ```
sudo fdisk -l
``` as well as the contents of /boot/grub/menu.lst

---

### Post by mattme on 2008-05-06
No problems I think. I'm in windows. Thought I might as well keep you updated.

First things I did. Install firefox. Remove all the programs that appeared in my face when I first booted.

Trying to run windows update. so far it went like this.

you must install the activex  component.
done.
you must update the windows update software.
done.
a newer version of the software is avaliable.
done

I've installed/updated it three times so far!
Ooh it's going for a fourth!

---

