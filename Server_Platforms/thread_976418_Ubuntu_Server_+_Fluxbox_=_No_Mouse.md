---
title: "Ubuntu Server + Fluxbox = No Mouse"
date: 2008-11-09
forum: Server Platforms
---

### Post by zunk on 2008-11-09
Hello.

I Installed Ubuntu Server 8.10 (with generic kernel),Then installed xorg and fluxbox. And when in fluxbox the mouse (Trackpoint 4) doesnt work.. I'm not sure the keyboard works.. i can Alt-fx to tty's but haven't yet got any reaction from inside of fluxbox.

It's an IBM R50e.

Any help appreciated!

---

### Post by zunk on 2008-11-10
And no keyboard either... 

Anyone?

---

### Post by Kilgore_Trout on 2008-12-13
I'm playing around with a ThinkPad R32 I got from work and having this same issue.

Zunk, did you figure anything out?

---

### Post by IceBadger on 2008-12-14
I am having the same issues on an old PPC powerbook.  I installed xorg and fluxbox on a clean ubuntu-server install.

The only way I have found to fix this is by installing xubuntu-desktop.  The problem with this is that bootup takes much longer, and I have a window manager that I do not need installed.

I also noticed that my /etc/X11/xorg.conf file is empty.  By running sudo dpkg-reconfigure xserver-xorg I can get the file generated.  This does create a xorg.conf file, but it does not contain any mouse/keyboard entries.

I am going to keep working on this.  If you guys have success, let me know.

---

### Post by IceBadger on 2008-12-14
I have got this working now.  You need to also install 'hal' as well.  This is something that is pulled in when you install *ubuntu-desktop packages, but not when you install fluxbox.  It looks like input devices are no longer configured in xorg.conf in 8.10.

To get the mouse and keyboard working in fluxbox on an ubuntu-server install:
```
sudo apt-get install hal
```
There should be no configuration needed.


Let me know if this does not work for you guys.

---

### Post by IceBadger on 2008-12-14
For those of you who want to use fluxbox on a clean 8.10 ubuntu server install:

```
sudo apt-get install xorg fluxbox hal
```

That should be it!

---

### Post by tbklt on 2009-03-31
Thanks Icebadger,  that was the final piece I was missing in this puzzle!

I did need this post [here]("http://xlayn.blogspot.com/2007/07/oracle-10gr2-on-ubuntu-server-704.html") in conjunction to get to the point where the applications would start:

> step#12: $sudo apt-get install fluxbox xserver-xorg xfonts-base fluxbox xterm

Not sure why fluxbox is in twice, but in summary, on my HP dx6100 P4,I needed these packages to get flux up and running:

fluxbox
fluxconf
xserver-xorg
xserver-xorg-core
xfonts-base
xterm
xinit
hal

cheers!

---

### Post by IceBadger on 2009-04-01
The most likely case is that when **fluxbox** is installed the first time in the list, there is no xserver to configure with (it has not been installed yet).  This is why the second **fluxbox** is necessary from my experiences.  When installed after the xserver packages, **fluxbox** can properly configure itself.

As for your list:

> **tbklt said:**
> 
fluxbox
fluxconf
xserver-xorg
xserver-xorg-core
xfonts-base
xterm
xinit
hal


**fluxconf** is not essential, it is just an interface for editing configuration files.  Most people I know just use nano/gedit/vim for this.

You also do not need to explicitly state **xserver-xorg-core**; it is a dependency of **xserver-xorg** and will be installed automatically.

Does **xserver-xorg**, **xfonts-base**, **xterm**, **xinit**, **fluxbox**, and **hal** give you a running system?  If it does I would be happy to know.

I usually substitute **xorg** for the first four items on this list mostly because it it easier to remember, and I also end up requiring the extra dependencies for other programs.

---

### Post by kerry_s on 2009-04-01
when i used fluxbox, i did> sudo apt-get install xorg fluxbox

that's it that's enough to get you into X.

---

### Post by IceBadger on 2009-04-01
For me it was enough to get me X and load fluxbox, but without **hal** I could not move my mouse or use the keyboard.

I am sure the reason for this is because it uses a PPC chip.  Maybe it had something to do with X not supporting the laptop's keyboard mouse interfaces.

---

