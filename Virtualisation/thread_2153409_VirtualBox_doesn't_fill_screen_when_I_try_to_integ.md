---
title: "VirtualBox doesn't fill screen when I try to integrate it with my desktop"
date: 2013-06-11
forum: Virtualisation
---

### Post by hopungo on 2013-06-11
After I updated my Ubuntu to 13.04 I noticed that VirtualBox looks strange (see the attachments below) when I try to integrate it with desktop. As well as the VB menu doesn't work. I had no such problem before. Does anyone know how to fix it?

[COLOR=#777777][FONT=Arial]Host machine packages & config:[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]VirtualBox 4.2.12 r84980[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]nvidia-current 304.88[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]GPU GeForce 6150SE nForce 430[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]Last Xorg taken from xorg-edgers PPA repo:[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]X.Org X Server 1.13.4[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]Release Date: 2013-04-17[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]X Protocol Version 11, Revision 0[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]Current Operating System: Linux karimov-danil 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 2013 x86_64[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-25-generic root=UUID=b632398e-9f06-46f7-8fe9-3e61266354a6 ro quiet splash[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]Build Date: 08 May 2013  02:34:03PM[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]xorg-server 2:1.13.4~git20130508+server-1.13-branch.10c42f57-0ubuntu0ricotz~raring (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) [/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]Current version of pixman: 0.28.2[/FONT][/COLOR]

[COLOR=#777777][FONT=Arial]Guest machine config:[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]Windows 7 Flowers Edition x86[/FONT][/COLOR]
[COLOR=#777777][FONT=Arial]VirtualBox Additions 4.2.12 r84980[/FONT][/COLOR]

---

### Post by cub on 2013-06-13
Did you install the guest addons?

---

### Post by hopungo on 2013-06-14
[FONT=Arial]Guest machine config:[/FONT]
[FONT=Arial]Windows 7 Flowers Edition x86[/FONT]
[B][FONT=Arial]VirtualBox Additions 4.2.12 r84980[/FONT][COLOR=#777777][FONT=Arial]


[/FONT][/COLOR][/B][FONT=Arial]Be more attentive, pls.[/FONT]

---

### Post by hopungo on 2013-06-25
Updated VB to version 4.2.14 r86644. Installed corresponding Guest Additions. Now Integration mode does not work at all. Virtual machine simply crashes when I turn it on. Had problems with installing Extension Pack, but solved them.

---

### Post by hopungo on 2013-07-15
Found that using another Desktop Environment (i.e. LXDE) solves this problem. I think it's a Unity bug.

---

### Post by SeijiSensei on 2013-07-15
> **hopungo said:**
> Found that using another Desktop Environment (i.e. LXDE) solves this problem. I think it's a Unity bug.

I've never had any problems with VirtualBox on the KDE desktop.  I'm running it on two 13.04 machines and all the screen effects work fine.

---

### Post by hopungo on 2013-07-19
Reported it [h]("https://bugs.launchpad.net/unity/+bug/1202936")[ere]("https://bugs.launchpad.net/unity/+bug/1202936"). If anyone can confirm, please do me a favor :).

---

