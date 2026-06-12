---
title: "xfce 4.10 pre in ubuntu 12.04"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rburkartjo on 2012-04-17
has anyone else tried this
[http://sourceforge.net/projects/babble777.u/files/xfce-4.10-daily/Ubuntu%2012.04/](http://sourceforge.net/projects/babble777.u/files/xfce-4.10-daily/Ubuntu%2012.04/)

---

### Post by baizon on 2012-04-18
Looking pretty good, no bugs found yet and nothing was broken after installation. 
Btw. i love the new tiling feature :KS

---

### Post by neu5eeCh on 2012-04-18
> **rburkartjo said:**
> has anyone else tried this
[http://sourceforge.net/projects/babble777.u/files/xfce-4.10-daily/Ubuntu%2012.04/]("http://sourceforge.net/projects/babble777.u/files/xfce-4.10-daily/Ubuntu%2012.04/")

Thanks for the heads-up. I'm off to try it.

---

### Post by rburkartjo on 2012-04-18
yes it does seem to be pretty cool and works well on 12.04. no crashes yet

---

### Post by neu5eeCh on 2012-04-18
Did you install the Xubuntu Desktop (in Ubuntu) before installing the deb? I was also thinking of installing the deb in my 11.10 or 11.04 Xubuntu installs - just to see. Any thoughts or advice that way? If I bork something, I've got backups.

---

### Post by neu5eeCh on 2012-04-18
Ok..... I can now reliably assert that installing the deb package in Xubuntu 11.04 will bork your system. Just thought I'd pass that along. No problem, I was going to re-format that partition anyway...

---

### Post by rburkartjo on 2012-04-18
it worked fine when i installed while i was in xfce. it didnt have the weather applete so i uninstalled the deb package with no problem and got all my 4.8 settings back

---

### Post by neu5eeCh on 2012-04-18
> **rburkartjo said:**
> it worked fine when i installed while i was in xfce. it didnt have the weather applete so i uninstalled the deb package with no problem and got all my 4.8 settings back

Yes, but was this in 12.04?

---

### Post by jefsview on 2012-04-18
There's now a PPA available for Precise:

[http://ppa.launchpad.net/mrpouit/ppa/ubuntu](http://ppa.launchpad.net/mrpouit/ppa/ubuntu) precise

It's about the only active XFCE PPA still on launchpad, and it just became fully populated for Precise.

Just added it through Yppa manager, but haven't installed yet.

-- Jeff

---

### Post by rburkartjo on 2012-04-18
vt yes it was in 12.04

---

### Post by rburkartjo on 2012-04-18
jef tks for the info on the ppa

---

### Post by Toz on 2012-04-18
From the main PPA page: [https://launchpad.net/~mrpouit/+archive/ppa]("https://launchpad.net/~mrpouit/+archive/ppa")

> (Experimental) Xfce packages.

Currently: work in progress for Xfce 4.10pre2.

PACKAGES FROM THIS PPA WILL BREAK PANEL PLUGINS WHEN INSTALLED. YOU'VE BEEN WARNED.

---

### Post by rburkartjo on 2012-04-19
toz good to know. i used a different ppa and it broke xfce. had to log into a unity session and remove. the deb link i posted worked fine for me but it did break one of my panel plugins. i use a lot and it only broke the weather plugin. note bad for a prerelease.

---

### Post by jefsview on 2012-04-19
That's what I was afraid of. I didn't even try to install any yet, since it's just the core packages. Just using the PPA as a reference for the final release just in case it doesn't make it into the main Ubuntu repository.

Been following over at the XFCE forums, and those that are testing seem to like the improvements. 

But I like and need my weather app and my orage clock/calendar :)

-- Jeff

---

### Post by neu5eeCh on 2012-04-19
Installed the PPA in my Ubuntu 12.04 partition. Works. Looks nice. In fact, in looks beautiful. With thumbnails on the desktop, XFCE has **_finally_** made it out of the 1980's.

---

### Post by dentaku65 on 2012-04-19
Nice... but most of my plugins panel are gone (like stated on PPA btw)
I've suggest to install ppa-purge before to test the PPA of XFCE 4.10pre
```
sudo apt-get install ppa-purge
```
The, if you need/wish you can safely remove the PPA packages
```
sudo ppa-purge ppa:mrpouit/ppa
```

:popcorn:

---

### Post by xebian on 2012-04-19
> **dentaku65 said:**
> Nice... but most of my plugins panel are gone (like stated on PPA btw)
I've suggest to install ppa-purge before to test the PPA of XFCE 4.10pre
```
sudo apt-get install ppa-purge
```
The, if you need/wish you can safely remove the PPA packages
```
sudo ppa-purge ppa:mrpouit/ppa
```

:popcorn:

It's dis-obedient.  It could bork your system.

```
Suggested packages:
  compizconfig-settings-manager gnome-themes
The following packages will be DOWNGRADED:
  compiz compiz-core compiz-gnome compiz-plugins-default libdecoration0
0 upgraded, 0 newly installed, 5 downgraded, 0 to remove and 0 not upgraded.
Need to get 1,384 kB of archives.
After this operation, 0 B of additional disk space will be used.
[COLOR="Red"[B]]Do you want to continue [Y/n]? n
Abort.
The following packages will be DOWNGRADED:
  compiz compiz-core compiz-gnome compiz-plugins-default libdecoration0 [/B][/COLOR]
0 packages upgraded, 0 newly installed, 5 downgraded, 0 to remove and 0 not upgraded.
Need to get 1,384 kB of archives. After unpacking 0 B will be used.
Get: 1 http://us.archive.ubuntu.com/ubuntu/ precise/main compiz-gnome amd64 1:0.9.7.6-0ubuntu1 [300 kB]

```

I said not to continue and said ok "Abort" but keep on going anyway.

---

### Post by neu5eeCh on 2012-04-20
Something I've been noticing: Installing XFCE in Ubuntu makes for terrible font rendering in XFCE. I've done all the font twiddling I can do via settings. This reminds me of a problem I used to have between KDE and Gnome (when installing KDE in Ubuntu). Had something to do with a font.cfg (?) file in the home folder? Some kind of bug...

---

### Post by arabuli on 2012-04-20
Hi, I've tried installing XFCE 4.10 on my ubuntu 12.04 but it looks very ugly. See screenshot below

[http://i.imgur.com/kk7DS.png](http://i.imgur.com/kk7DS.png)

How can I fix this?

---

### Post by Toz on 2012-04-20
That looks like the default xfce look. Go to "Settings Manager->Window Manager" and change the window manager theme and also go to "Settings Manager->Appearance" and change the appearance theme. While you're there, click on the "Icons" tab and change the icon theme (if you want) and you might also want to fiddle with the font presentation on the Fonts tab. GTK3 themes work the best. Here are some links:
- Greybird/Bluebord/Albatross -> [http://shimmerproject.org/]("http://shimmerproject.org/")
- a collection of some nice user-made ones -> [http://forum.xfce.org/viewtopic.php?id=6770]("http://forum.xfce.org/viewtopic.php?id=6770")
- and as always: [http://xfce-look.org/]("http://xfce-look.org/")

You can change the look and appearance of the top and bottom panels by right-clicking them and selecting "Panel->Panel Preferences.

---

### Post by neu5eeCh on 2012-04-20
> **arabuli said:**
> Hi, I've tried installing XFCE 4.10 on my ubuntu 12.04 but it looks very ugly. See screenshot below

[http://i.imgur.com/kk7DS.png](http://i.imgur.com/kk7DS.png)

How can I fix this?

What? You don't like the Windows 2000 look? ;)

I'll post a screenshot from my XFCE install as soon as I'm back on that partition. The font still looks terrible, but other than that, it's lovely.

**Edit:** Presumably your computer can handle it, but be sure and turn on compositing (in settings).

---

### Post by ranch hand on 2012-04-21
See post 20.

You also need to check all the items in the settings manager.  There are a number that have to do with the look of the thing.

One will enable compositing if your box will run it.  This will add a lot to what you can do with the look of the panel.

Panel preferences will let you do just about anything with the panels.

The bottom panel is configured to look like a dock.  It is locked but can be unlocked.  I delete it on my installs and only use the top one.

If you add a launcher you can put anything in it you want by right clicking on it and choosing preferences (or maybe properties - too late and it was one in older versions and the other in newer ones - I am not on Xfce at all right now so can't check) but you can add as many to each launcher as you want.  I have all my image manipulation, viewing and screenshot on one.

---

### Post by arabuli on 2012-04-21
Wow, thanks for your answer.

I was hoping that default look will be nicer in new release :D

I changed themes and icons and it looks much nicer now.

Thanks again.

---

### Post by ranch hand on 2012-04-22
This is straight up Xfce.  It is the way Debian gives it to you.

Xubuntu, like all Ubuntu family members, sets up the eye candy for you ahead of time.  I am sure that when it hits the repo you will find it spiced up a bit.

I prefer it raw myself.  I can add my own eye candy.

A fresh install of Xubuntu 12.04 is a lot bigger than a fresh install of Debian Wheezy Xfce.

It is looking pretty good though.  Going to miss it.  Have to grab some of the eye candy I found for it before I delete the partition.

---

### Post by dentaku65 on 2012-04-24
Just for feedback.
On my Precise Xubuntu everything seems to work quite well; just a couple of plugins do not works, not fundamentals, but I think nice to have:

[LIST=1]
[*]Session Menu (crash on add)
[*]Action Buttons (error on Log-out action)
[/LIST]

:popcorn:

---

