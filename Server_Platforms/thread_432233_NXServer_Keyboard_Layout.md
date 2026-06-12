---
title: "NXServer Keyboard Layout"
date: 2007-05-03
forum: Server Platforms
---

### Post by elventear on 2007-05-03
Hi,

I just upgraded one of my workstations from 6.10 to 7.04. So far everything seems fine, except for one thing. My previous install had NXServer installed and working. After doing the upgrade NXServer is still accessible but the Keyboard layout is screwed up. 

I also got this message:

"the x system keyboard settings differ from your current gnome keyboard settings"

I think the reason is because NX Server is configured by default to look at these keymaps:

"/etc/X11/xkb/keymap/xfree86"

But I have a gut feeling that because of Gnome it should be pointing somewhere else (When I login locally into Gnome I get a different keyboard options in the preferences menu than when I login with NX Server).

Has anyone experienced the same problem? Has anyone found solution?

Thanks!

---

### Post by elventear on 2007-05-03
It seems that the problem is related to Macs, X11 on Mac, and Ubuntu. This didn't happen in Edgy. 

For a somewhat working workaround check:

[http://ubuntuforums.org/showthread.php?p=2393785](http://ubuntuforums.org/showthread.php?p=2393785)

---

### Post by zoffmann on 2007-05-04
I had swedish letters in Gnome and english letters in Unix console, I have changed from english to swedish in console with the following:

[SIZE="3"]sudo dpkg-reconfigure console-setup[/SIZE]

hope it works for you.

---

### Post by elventear on 2007-05-04
Thanks, but that didn't help. The actual problem is in gnome. If I ssh remotely and launch xterm, the keyboard mapping is fine, and if I do and Xnest, the keyboard mapping is fine for me to enter my username and password. It is after going into gnome that the keymap is screwed.

---

### Post by zoffmann on 2007-05-05
I thought I found the universal solution but it helped me only  temporarily.

if i issue **sudo dpkg-reconfigure console-setup**

and then swich back to Gnome and then back to unix console the letters become scrambled - now swedish letters don't work for me.

:confused:

---

### Post by joachim.j on 2007-05-14
I have the exact same problem with NX after upgrading to Feisty. As well as some of the other posters in this thread I'm on Mac OS X 10.4.9, with a Swedish keyboard, trying to access my Ubuntu 7.04-server at home. I did a clean install on one of my servers here at work and have the exact same problem there as well.


Everything works terrific in KDE, but in Gnome my keyboard settings are totally screwed up. For instance, the number keys are located in the middle of my keyboard.


Unfortunately I don't have any solution to the problem, other than to install Kubuntu-Desktop through SSH on the Terminal in OS X.

---

