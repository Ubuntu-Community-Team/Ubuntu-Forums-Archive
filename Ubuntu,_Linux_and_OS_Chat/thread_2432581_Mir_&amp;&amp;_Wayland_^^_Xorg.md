---
title: "Mir &amp;&amp; Wayland ^^ Xorg"
date: 2019-12-04
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-12-04
can someone explain how Mir and Wayland work together (if they do)?

one of my big concerns is how user switching and/or multiple users will  work.  under Xorg (and earlier versions of X) i can have multiple  process instances of X.  these instances can exchange control of the  display hardware.  this was (and maybe still is) controlled via  switching of the virtual console.  in earlier versions of Linux, i set  up the use of all 63 consoles the kernel supported by defining (in a  keymap) the use of Alt+Shift+key for just about every key on the  keyboard, to change console to a specific console.  i ran 60 of the 63  in text mode and ran 3 instance of X on 10, 11, and 12 (at the time X  didn't understand a virtual console number above 12).

today lightdm is taking care of this.  it did so when i used Unity  (Ubuntu 13.10, 14.04, 16.04) and now as i use Xfce (Ubuntu 16.04 and  Xubuntu 18.04).  and it gives me the ability to switch users.  under  Unity, i was doing so with a drop down menu.  under Xfce i use keyboard  shortcuts.  way back i used multiple users to compartmentalize data  access in case i ran something that might try to access my data.  i  could have many sessions of the same user among the 60 text consoles.   now days, each user is set up with 10 workspaces, which i also switch  with keyboard shortcuts.  many of those workspaces are unused.  the  number of users i run at any given time, varies.  lately, my startup has  been pre-logging 15 users.  16 are logged in, right now, so there are a  total of 160 workspaces, with over 100 of them with one or more windows  active.

i would like to know if Mir/Wayland would let me continue to do this, even if limited to X compatibility.

---

### Post by grahammechanical on 2019-12-07
I cannot claim to know what you are doing but I have found some blogs that give some information.

1) XFCE does not plan to have Wayland support any time soon. So, Xubuntu 20.04 may still prove suitable for what you do.

[https://www.reddit.com/r/xfce/comments/4aeqda/xfce_wayland_support/](https://www.reddit.com/r/xfce/comments/4aeqda/xfce_wayland_support/)

2) Ubuntu defaults to Xorg at present. We can load into Ubuntu on Wayland at the login screen but Wayland will not be default in Ubuntu 20.04

[https://www.phoronix.com/scan.php?page=news_item&px=No-Wayland-Default-20.04-LTS](https://www.phoronix.com/scan.php?page=news_item&px=No-Wayland-Default-20.04-LTS)

3) Canonical has given up on using Mir as a display server on the Ubuntu desktop. Mir is now being offered as a library for developing shells.

[https://ubuntu.com/blog/mir-support-for-wayland](https://ubuntu.com/blog/mir-support-for-wayland)

These were fairly recent blogs. You could do a test by installing Ubuntu 18.04 or 20.04 development version and logging into Ubuntu on Wayland and see if you can still do what you want


Regards

I have just done an experiment on Ubuntu 18.04. Using Ctrl + Alt + Fn 

I can create consoles using F1 - F6 and switch back to the desktop using Ctrl + Alt + F7. In Ubuntu on Wayland I can do the same but to get back to the desktop it is Ctrl + Alt + F8.

So, Ubuntu on X server uses a Linux console on F7 and Ubuntu on Wayland uses a Linux console on F8. That is how they a giving a Wayland session at the moment.

---

### Post by CatKiller on 2019-12-07
> **Skaperen said:**
> can someone explain how Mir and Wayland work together (if they do)?

Wayland is a display protocol to replace X. The display server under Wayland is called a compositor. Mir is one of the Wayland compositors. Prior to Wayland taking off Mir was intended to be a replacement for X in its own right.

---

### Post by Skaperen on 2019-12-07
"Wayland is called a compositor" ... is it just called that, but isn't one?  "Mir is one of the Wayland compositors" ... so Mir is a compositor but we say that E-Wayland is?  what do these 2 things do?  do Mir and Wayland work together?  when did Mir becomes "one of the Wayland compositors"?

---

### Post by CatKiller on 2019-12-08
> **Skaperen said:**
> "Wayland is called a compositor" ... is it just called that, but isn't one?  
Read the whole sentence, please. 

>  "Mir is one of the Wayland compositors" ... so Mir is a compositor but we say that E-Wayland is?  what do these 2 things do? 
Mir is a Wayland compositor. Weston is a Wayland compositor. Clutter is a Wayland compositor. KWin is a Wayland compositor. Sway is a Wayland compositor. 

[ [img]https://wayland.freedesktop.org/wayland-architecture.png[/img]](https://wayland.freedesktop.org/architecture.html) 

> do Mir and Wayland work together?  when did Mir becomes "one of the Wayland compositors"?
2017.

---

### Post by Skaperen on 2019-12-08
i did read the whole sentence.  that's where the confusion came in.

---

