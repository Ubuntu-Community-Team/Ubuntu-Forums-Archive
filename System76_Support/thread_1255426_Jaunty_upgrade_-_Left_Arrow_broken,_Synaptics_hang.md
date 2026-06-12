---
title: "Jaunty upgrade - Left Arrow broken, Synaptics hangs on boot"
date: 2009-09-01
forum: System76 Support
---

### Post by ajlewis2 on 2009-09-01
I have a Darter and just upgraded from Hardy to Jaunty.

Two problems:

1. On boot the system hangs for a long time here (from dmesg)

```
[   23.043047] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   23.080725] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[  113.442403] lp: driver loaded but no devices found
```

2. In both Gnome and KDE the **left arrow** does not work.  In Gnome it brings up the applications menu.  The arrow does work when I go into the console with Ctrl-Alt-F1, but doesn't work in terminal, gedit, openoffice or anything else I can find when I'm in Gnome or KDE.

Any ideas on either of these problems?  Thanks.

Anita

---

### Post by thomasaaron on 2009-09-01
Go to System > Prefs > Keyboard and make sure your layout is still generic 105-key intl USA.

Also, did you do a fresh installation of Jaunty, or did you actually upgrade all the way from hardy? (i.e. hardy >> intrepid >> jaunty).

Also, do you have the same symptoms from a Jaunty live CD?

---

### Post by ajlewis2 on 2009-09-01
> **thomasaaron said:**
> Go to System > Prefs > Keyboard and make sure your layout is still generic 105-key intl USA.

Also, did you do a fresh installation of Jaunty, or did you actually upgrade all the way from hardy? (i.e. hardy >> intrepid >> jaunty).

Also, do you have the same symptoms from a Jaunty live CD?

Thanks Thomas.

I checked and I still have 105-key intl USA setting.

I did an upgrade and not a fresh installation.  I used Adept which said there was a new version and it went straight from Hardy to Jaunty which surprised me.  

I did the upgrade without a cd; so I have not tried the live CD.

---

### Post by thomasaaron on 2009-09-02
Hmmm... That's officially weird.

My initial hunch is, that is where the problem is. And it wouldn't surprise me in the slightest if you discover a bunch of other issues. There were incompatibilities between Intrepid and Jaunty. I can only guess at the incompatibilities between Hardy and Jaunty.

Well, try from a live CD just to verify we don't have a hardware issue before we invest time in figuring this one out.

---

### Post by ajlewis2 on 2009-09-02
Good news and more good news.  I downloaded the jaunty desktop iso and installed on a usb stick.  It ran nicely and I did not have the problem with the left arrow.  The best news is that now that I'm back in my original system, the left arrow key still works!  

I still have the problem with Synaptics hanging.  I have an idea, because this is similar to what happened with my Toshiba netbook.  I'll come back on it after I try the idea.

---

### Post by ajlewis2 on 2009-09-03
I haven't been able to solve the long hang while booting; so I have installed jaunty fresh on another partition.  So far it doesn't look like it will be too hard to get my old programs working.  Java, flash, media stuff, and wine should take care of most of it.  I'll back up /etc and /opt for info later if I need it.  I did "dpkg --get-selections > package-list.txt" for a list of all that I have installed.  Thankfully I have a separate /home.  I already know that I need to let .gconf and .gconfd/ be reconstructed.  I'm going to ditch KDE and just use Gnome, because the new KDE is pretty bad.  Gnome is running smoothly.

This might have been avoided doing incremental upgrade, but it's about time for a fresh install anyway. 

Thanks again, Thomas.  It's always good to know you are there!

---

### Post by ajlewis2 on 2009-09-03
I just solved the left arrow problem.  I'm on the new install and just noticed it was happening again.  Then I remembered at the beginning when I first brought it up, there was something about my .Xmodmap.  I obviously made this before I began using the current keyboard layout.  It contains:

```
keycode 113 = Super_L

```

The left arrow is key 113.  I guess it used to be one of the extra windows keys.  So that is it and I doubt anyone else will run into it.  That is why running the live jaunty fixed it.  I'll delete that little file right now!

---

### Post by thomasaaron on 2009-09-03
Bless your heart!

(I don't think I'd have figured that out quickly.) ](*,)

---

