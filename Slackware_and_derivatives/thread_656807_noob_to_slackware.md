---
title: "noob to slackware"
date: 2008-01-02
forum: Slackware and derivatives
---

### Post by chips24 on 2008-01-02
can someone tell methe ins and outs with slackware, im very curious.

---

### Post by Whiffle on 2008-01-02
What would you'd like to know?   I'm not quite sure what you mean by ins and outs.

---

### Post by chips24 on 2008-01-02
good things and bad things

---

### Post by Whiffle on 2008-01-02
ah yes.

in's

Well, slackware is extremely simple in its construction, as in things are not unneccessarily complicated.  For example, enabling/disabling init scripts is done simply by making the script executable or non-executable.  Simple as   that.  Most of it follows a pretty similar scheme.

Its fast.  Theres not a whole lot of overhead on slack, unless you add a bunch.  For me, a basic slackware install is much faster than an ubuntu install out of the box.  Actually, even once ubuntu is tweaked, it doesn't feel as fast as slack.

outs
no package manager, sort of.  On a standard install, packages are managed using pkgtool, installpkg, upgradepkg, and removepkg.  Once you've got it installed though, you can add different programs, such as slapt-get and slackpkg.  They aren't as comprehensive as those found on ubuntu, but if you pay attention to what you're doing they're not too bad to use.   I actually tend to not upgrade much on slackware, it not like ubuntu where lets you know every time theres an update.  I like it that way actually...

finding packages.  They're out there, no doubt, but they can be occasionally tough to find.  On my recent install I went ahead and installed both of the first two cd's and thats taken care of most of my dependency problems.  YMMV

Hardware detection.  Its not as developed as ubuntu, so quite a few things won't just work.  One such thing is the sleep/suspend on my laptop.  I had to do some fanagaling to make it work, but once I got it working, it always works.  

Its a fun distro to learn, and if you're successful with it you'll learn quite a bit about linux.  Its also rock solid stable.

---

### Post by tommcd on 2008-01-03
Hardware detection is as good on slackware as any other distro, it's just that you may need to configure things yourself.  Read the slackbook to get started:
[http://slackbook.org/](http://slackbook.org/)
If you install the first 2 slackware CDs you get all of KDE and all of XFCE, which includes a lot of apps. For additional stuff check out slackbuilds:
[http://slackbuilds.org/](http://slackbuilds.org/) These are scripts that build a slackware .tgz package for installation, and they work very well. Also there are binary slackware packages:
[http://linuxpackages.net/](http://linuxpackages.net/)
[http://slacky.eu/](http://slacky.eu/)
And there is src2pkg, which converts source code packages to .tgz binaries and is said to work well. Slackware is great for learning linux.

---

### Post by Junglizer on 2008-03-12
I'm in agreement with what Whiffle has said with a few points of my own.

The install is very simple and fast and generally hard to mess up. If you don't want a lot of excess on the system you can do the "menu" install, and just don't select applications and programs you don't need. I have had some issues with the multiple CD install and highly recommend the DVD install whenever possible, it makes everything much easier. (Version 12.0 gave a great boost in hardware compatibility over 11.0 in my opinion.) It has been viewed, by many for quite some time, as one of the more difficult distro's to work with. I would say that for the most part this is due to the package management, or rather lack thereof.  It really comes down to your prior experience with Linux. I tend to burn a CD of apps/programs that I will want that are not in the default install and just keep that with my install disks. I highly recommend Slackware whenever you have a specific use or application and you don't want a bunch of random crap trying to update every time you try to install some thing new. (most every package manager, as this often leads to breaking stuff) 

So all in all, I personally think that the good outweighs the bad, and the bad is really only "bad" b/c it is difficult. Most hardware can be got working if you don't mind recompiling your kernel and are used to fiddling around within your system.

---

### Post by Xerp on 2008-05-12
Slackware is a nice, vanilla distro. It isn't bleeding edge, but it is stable. Nothing is assumed for you - you do all your own customising. Its very good!

---

### Post by Caraibes on 2008-05-15
I am actually dual-booting Ubuntu 8.04 and Slackware 12.1 now. All my other boxes have Debian.

But I went to Slack for learning purposes... It is not the easiest, but once you learn, some stuff don't seem that hard.

-The most valuable post-install command I learned this time ?
```
xorgsetup
```
It is the equivalent (I think) of the Debian's:
```
dpkg-reconfigure -phigh xserver-xorg
```

But I must say I am relieved to have my Hardy partition and my other Debian boxes to boot in, because life is so much more easy in a Debian world !

Anyway, I enjoy the Slack experience... Using mostly Xfce, because I really don't feel at home with KDE...

---

