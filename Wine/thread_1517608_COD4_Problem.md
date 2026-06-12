---
title: "COD4 Problem"
date: 2010-06-25
forum: Wine
---

### Post by connorh123 on 2010-06-25
Hi guys, I got a problem with Call of Duty 4.
Okay, so let's start from the beginning. I recently got the latest version of wine and tried to install it again (I have the cd), and it worked! So now that it's installed the only thing that works is Singleplayer, and the farthest it gets is to the Infinity Ward sign. When I click on the Multiplayer icon, it says to restart the cd/dvd then press ok. I keep doing this and nothing happens. If anyone has had any luck installing cod4 please help.

---

### Post by asdfoo on 2010-06-25
hello

what do you consider the latest version of wine to be?
type "wine --version" at a terminal, it should print wine-1.2-rc5

which video card and drivers do you have? (check the output of "glxinfo" and "lspci")

---

### Post by connorh123 on 2010-06-25
I have 1.2-rc4 version, and my driver is a Nvidia Geforce 7025 and an nForce 630a.

---

### Post by asdfoo on 2010-06-25
which version of the nvidia drivers do you have? if they are old/outdated it could be the cause.

256.xx 257.xx, 190.xx 195.xx 196.xx 197.xx are relatively new, anything less is probably worth upgrading from.

otherwise do you get any information on the terminal when you run it?

[http://wiki.winehq.org/FAQ#get_log](http://wiki.winehq.org/FAQ#get_log)

---

