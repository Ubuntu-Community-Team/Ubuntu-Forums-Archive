---
title: "Gnome-shell in Ricotz Testing PPA"
date: 2011-10-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-10-26
Those who wish to use the new git version of Gnome-shell from Ricotz Testing PPA,
note that packages gnome-shell, gjs and pango are built against new glib2.0, which must also be installed (libglib2.0 >= 2.31.0~) from this PPA.

I have all these installed and I can tell you they do work very well.

But at least Eog will not work with libglib2.0-0_2.31.0

---

### Post by zika on 2011-10-26
> **Harry33 said:**
> Those who wish to use the new git version of Gnome-shell from Ricotz Testing PPA,
note that packages gnome-shell, gjs and pango are built against new glib2.0, which must also be installed (libglib2.0 >= 2.31.0~) from this PPA.

I have all these installed and I can tell you they do work very well.You're writing about gnome-shell side-by-side with Unity on the same machine?
I wanted to try that but was not sure if that would make some troubles (lots of packags get installed by dependencies...)...
Ups, my fingers are itchy...

---

### Post by ronacc on 2011-10-26
It shouldn't cause any more problems than normal dev glitches , even if you run GS all the time like I do , you start out with unity because that is default and GS has to be installed after first boot so unless you removed unity somehow you still have it .

---

### Post by zika on 2011-10-26
I was put off by the disclaimer: This package contains packages from GNOME3 and their dependencies so they can be used in Ubuntu 11.04 (Natty).  This PPA is EXPERIMENTAL and MAY BREAK YOUR SYSTEM.  There is no downgrade process.

I hope that it does not appy in PP case...

---

### Post by ronacc on 2011-10-26
thats for the PPA , GS is also available from the normal repos , that disclaimer is on a lot of ppas , the version of GS in Rico's ppa is newer than the one in the "official" repos .

---

### Post by zika on 2011-10-26
> **ronacc said:**
> thats for the PPA , GS is also available from the normal repos , that disclaimer is on a lot of ppas , the version of GS in Rico's ppa is newer than the one in the "official" repos .Cool.
I've installed „official“ Gnome-Shell. It did not incorporate itself in a LogIn menu so I had to make a backdoor approach using startx... It is nice... I'll try to add PPA and see what is new... Thank You!

---

### Post by zika on 2011-10-26
It worked. I'm in... ;)
It seems very nice...

---

### Post by ronacc on 2011-10-26
it should have added itself to the login menu , it is just listed as gnome not gnome shell , unity is listed as ubuntu .

---

### Post by zika on 2011-10-26
> **ronacc said:**
> it should have added itself to the login menu , it is just listed as gnome not gnome shell , unity is listed as ubuntu .After some encouragement everything is OK. It is in the menu and...
Quite different approach to way of working, but not unappealing...

---

### Post by Harry33 on 2011-10-26
> **zika said:**
> You're writing about gnome-shell side-by-side with Unity on the same machine?
I wanted to try that but was not sure if that would make some troubles (lots of packags get installed by dependencies...)...
Ups, my fingers are itchy...

No I do not have Unity installed at all.
OK, I do have the package libunity6, but that is because Nautilus depends on it.
I am very familiar with Gnome-shell and intend to follow that path for the time being.
There is absolutely no added value for me in Unity.

---

### Post by zika on 2011-10-26
> **Harry33 said:**
> No I do not have Unity installed at all.
OK, I do have the package libunity6, but that is because Nautilus depends on it.
I am very familiar with Gnome-shell and intend to follow that path for the time being.
There is absolutely no added value for me in Unity.
It cohabits with Unity nicely.
Thank You guys for pushing me to try this. This is a love on first site. It even works with startx (.Xsession)... Nice!
I love escaping usage of any unnecessary apps in the process...
Mouse bump in the upper left corner is cute!

---

### Post by Harry33 on 2011-10-26
> **zika said:**
> It cohabits with Unity nicely.
Thank You guys for pushing me to try this. This is a love on first site. It even works with startx (.Xsession)... Nice!
Mouse bump in the upper left corner is a cutie!

The upper left corner is called "the Hot spot".
I use mainly that to open the overview screen in GS, do not have to click on anything.

---

### Post by cariboo on 2011-10-27
This is just a general comment on user interfaces and muscle memory. I started gnome-shell for the first time in a couple of weeks, and found that after using Unity for the past little while, I found myself automagically moving the mouse cursor to the left side in order to reveal the launchers instead of going to the top left corner. :)

---

### Post by cecilpierce on 2011-10-30
I have ricotz ppa and installed these extensions and they all have problems, any reason or cure ?

---

### Post by zika on 2011-10-30
While we are on the subject of Ricotz PPA, did anyone try gconf-cleaner? It reports that I could erase 600+ keys... I, of course, did not agree, not easily... Should have I?

It seems I decided correctly, by declining... ;) : [http://ubuntuforums.org/showpost.php?p=11409903&postcount=1](http://ubuntuforums.org/showpost.php?p=11409903&postcount=1)

---

### Post by cbowman57 on 2011-10-30
> **cecilpierce said:**
> I have ricotz ppa and installed these extensions and they all have problems, any reason or cure ?

Use looking glass & check for errors.

---

### Post by zika on 2011-10-30
> **cecilpierce said:**
> I have ricotz ppa and installed these extensions and they all have problems, any reason or cure ?
Where did You get these &#8222;Advanced settings&#8220;...?

---

### Post by cbowman57 on 2011-10-30
> **zika said:**
> Where did You get these „Advanced settings“...?

That's gnome-tweak-tool

---

### Post by jfernyhough on 2011-10-30
$ sudo apt-get install gnome-tweak-tool

---

### Post by zika on 2011-10-30
> **cbowman57 said:**
> That's gnome-tweak-tool> **jfernyhough said:**
> $ sudo apt-get install gnome-tweak-tool
Thank You...!
This is getting better every time I look deeper into it...

---

### Post by cecilpierce on 2011-10-30
> **cbowman57 said:**
> Use looking glass & check for errors.

No errors in lg, tried screenshot and it won't go with lg.

---

### Post by Harry33 on 2011-10-30
Gnome-shell, gjs and libpango1.0-0 (Ricotz PPA) are build against libglib2.0-0_2.31.0.
This in turn makes Eog segfault. This is also known upstream.

---

### Post by cecilpierce on 2011-10-30
> **Harry33 said:**
> Gnome-shell, gjs and libpango1.0-0 (Ricotz PPA) are build against libglib2.0-0_2.31.0.
This in turn makes Eog segfault. This is also known upstream.

Is there a fix or should I just wait?
thanks

---

### Post by Harry33 on 2011-10-30
> **cecilpierce said:**
> Is there a fix or should I just wait?
thanks

ATM no fix is available. So if you need to have eog in a working order, better not to use Ricotz Testing PPA.

Here are the upstream bug reports:

[https://bugzilla.gnome.org/show_bug.cgi?id=662630](https://bugzilla.gnome.org/show_bug.cgi?id=662630)

[https://bugzilla.gnome.org/show_bug.cgi?id=663043](https://bugzilla.gnome.org/show_bug.cgi?id=663043)

---

### Post by cecilpierce on 2011-10-30
OK, thanks, I'll just wait, I have another 12.04 that doesn't have ricotz and it works good.

---

### Post by Starks on 2011-10-31
Anyone else getting a nautilus menu on the top bar when using transparent themes?

---

### Post by jfernyhough on 2011-10-31
Yes, this is a by-product of appmenu. I removed appmenu-gtk, appmenu-gtk3, indicator-appmenu and it went away.

---

### Post by tekstr1der on 2011-10-31
> **Starks said:**
> Anyone else getting a nautilus menu on the top bar when using transparent themes?

Here's the bug report:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771)

Here's a workaround:

```
sudo apt-get install dconf-tools
```

dconf-editor > gnome > desktop > background and untick "show-desktop-icons".

You can achieve the same using gnome-tweak-tool and disabling nautilus control of the desktop.

---

### Post by jfernyhough on 2011-10-31
That's great unless you like icons. :)

---

### Post by Starks on 2011-10-31
The fix is now in the repos.

---

### Post by Harry33 on 2011-11-01
> **Starks said:**
> The fix is now in the repos.

This bug is not a gnome-shell issue, so this discussion is in the wrong thread.
It should rather be here:
[http://ubuntuforums.org/showthread.php?t=1872780](http://ubuntuforums.org/showthread.php?t=1872780)

BTW. This same nautilus bug-fix version 3.2.1-0ubuntu2 has been in oneiric-proposed since 25th October.

---

