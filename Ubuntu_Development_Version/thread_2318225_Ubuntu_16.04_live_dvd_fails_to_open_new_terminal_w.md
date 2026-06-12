---
title: "Ubuntu 16.04 live dvd fails to open new terminal with Ctrl + Alt + F1"
date: 2016-03-24
forum: Ubuntu Development Version
---

### Post by sanssadness on 2016-03-24
Has anyone tried opening a new terminal with Ubuntu 16.04? On previous Ubuntu versions, this opened a new terminal. When I try to do this with 16.04, it briefly flashes a message that I can only read the first 3 words of: "Failed to load..."

After that, it switches to a black screen with a blinking white cursor and I can't do anything with it. I need the terminal so I can do some manual partitioning.

Does anyone know how to get that terminal working?

---

### Post by cariboo on 2016-03-24
Have you tried Ctrl-Alt-t?

---

### Post by PaulW2U on 2016-03-24
> **sanssadness said:**
> Has anyone tried opening a new terminal with Ubuntu 16.04? On previous Ubuntu versions, this opened a new terminal. When I try to do this with 16.04, it briefly flashes a message that I can only read the first 3 words of: "Failed to load..."
Sorry, but that works here.
> **cariboo said:**
> Have you tried Ctrl-Alt-t?
Which also works here.

If either of the above didn't work for any of the regular posters in this sub-forum then I'm sure that your problem would have been reported long before now. I'm not disputing that you're seeing a problem but I'm thinking that you're very much in the minority.

[http://cdimage.ubuntu.com/daily-live/20160323/](http://cdimage.ubuntu.com/daily-live/20160323/) is the latest Ubuntu build. Many users have tested this and have found no such issue.

Which build have you downloaded?

---

### Post by grahammechanical on 2016-03-24
I have a daily image from 23rd March.

The live session allows me to open tty1 (Ctrl+Alt+F1). The difficulty I have is with logging in. User name = ubuntu. Password = ubuntu does not work. In truth, I cannot think of anything that I would want to do from tty1 in a live session which I cannot do from the live session itself through Gnome Terminal or the utilities that are part of the default set in a live session.

Regards

---

### Post by mc4man on 2016-03-24
> **grahammechanical said:**
> I have a daily image from 23rd March.

The live session allows me to open tty1 (Ctrl+Alt+F1). The difficulty I have is with logging in. User name = ubuntu. Password = ubuntu does not work. In truth, I cannot think of anything that I would want to do from tty1 in a live session which I cannot do from the live session itself through Gnome Terminal or the utilities that are part of the default set in a live session.

Regards
I believe it's password = <nothing>

---

### Post by sanssadness on 2016-03-24
[QUOTE=grahammechanical]I have a daily image from 23rd March.

The live session allows me to open tty1 (Ctrl+Alt+F1). The difficulty I have is with logging in. User name = ubuntu. Password = ubuntu does not work. In truth, I cannot think of anything that I would want to do from tty1 in a live session which I cannot do from the live session itself through Gnome Terminal or the utilities that are part of the default set in a live session.

Regards[/QUOTE]

Oh, yeah I don't like having to use tty1 either. I might have to do it though because I'm trying to set up a LVM over LUKS scheme, which used to work with the alternative installer. But they no longer offer the alternative installer, so the initial setup has to be done through a terminal. I would do it from the boot environment if I could actually get into it, but an unrelated video card problem leaves me unable to get to the Gnome terminal, even with nomodeset.

Anyways, enough people have posted here about the terminal working that I think the problem is on my end only. I'm going to try the latest version of 16.04 and see if that lets me get into the terminal

---

