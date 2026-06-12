---
title: "Xubuntu GTK3 Indicators"
date: 2013-12-13
forum: Ubuntu Development Version
---

### Post by Elfy on 2013-12-13
We have some PPA's and instructions now for getting the new proposed GTK3 indicators in.

We obviously want this testing by as many people as possible.

Once we are happy with the results we can move forward and away from PPAs.

The instructions can be found here

    [https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Trusty/Gtk3Indicators](https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Trusty/Gtk3Indicators)


Please read the bug reporting note in Known Issues.

Cheers.

---

### Post by Elfy on 2013-12-18
If anyone doing this is doing so with nouveau (my card is a GeForce210) - have you seen oddities like the indicator panel going transparent? 

[http://i.imgur.com/mstzH87.png]("http://i.imgur.com/mstzH87.png")

I'm also getting xchat decide to run back a few decades for me 

[http://i.imgur.com/IiIekKB.png]("http://i.imgur.com/IiIekKB.png")

Finding errors in .cache/upstart/startxfce4.log

like this 
> 
The program 'xfsettingsd' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRRCrtc (invalid Crtc parameter)'.

Edit - you can forget this - I sort of got to the bottom of it - hdmi to tv was causing it, when tv goes to standby the issue occurs. Whether it can be fixed or not is another thing altogether.

---

### Post by OrangeCrate on 2013-12-28
Can confirm the GTK3 indicators work in Xubuntu 14.04. See post #5 in this thread:

[http://ubuntuforums.org/showthread.php?t=2185498](http://ubuntuforums.org/showthread.php?t=2185498)

If you want me to check if the ppa's work, let me know...

---

### Post by Elfy on 2013-12-29
PPA is the most current method and the one which is being updated to deal with other issues.

That said I've got 4 different PPAs here now for various things - themes, a prettier tabwin amongst them. 

I'm trying to get these things landed so people don't need to fiddle about - a bit Sysyphus like ...

---

### Post by OrangeCrate on 2013-12-29
Deleted

---

