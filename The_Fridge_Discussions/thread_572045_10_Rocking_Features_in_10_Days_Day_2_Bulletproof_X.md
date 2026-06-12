---
title: "10 Rocking Features in 10 Days: Day 2: Bulletproof X and Graphical X configuration"
date: 2007-10-10
forum: The Fridge Discussions
---

### Post by TheFridge on 2007-10-10
Yesterday we kicked this whole thing off and took a look at Deskbar and Tracker. Today we turn our attention to X, the graphical subsystem of any Ubuntu (or Linux or Unix machine). As any existing Ubuntu user knows, not only do you need to configure X, but breakages can happen. Thankfully with Ubuntu 7.10, there comes a few new features to help out with these problems, including better auto detection and configuration, Bulletproof X and graphical X config, for those times when you really to play with something. But first, some explanations
 **So what is X?**
 X, or X windowing system, is &#8220;a networking and display protocol which provides windowing on bitmap displays&#8221;, according to [Wikipedia]("http://en.wikipedia.org/wiki/X_Window_System"). It is also the basis of 99% of the GUIs on Linux and Unix systems such as Ubuntu.
 **So what is this &#8220;autoconfiguration&#8221; stuff?**
 Thanks to the awesome work of all the X.org developers, Ubuntu 7.10 now is able to detect your video hardware and monitor better, meaning in most instances, everything should just work. But what about those times that it doesn&#8217;t?
 **So I can config this graphically, right?**
 With 7.10, yes! The new displayconfig-gtk, written primarily by Sebastien Heinlein and based off the KDE systemconfig work, allows you to easily change the resolution, add another monitor, change your driver and more. Take a peak:
 [IMG]https://wiki.ubuntu.com/GutsyGibbon/Beta?action=AttachFile&do=get&target=displayconfig1.jpg[/IMG]
**Saving your broken X.conf with BulletProofX**
 Of course, not everything can always be roses and champagne. Sometimes things break, including X. Like most software, X reads off a configuration file to determine how to start up, including what monitor(s) and video card(s) you have. If this file gets corrupted, things can break, very very badly:
 [[IMG]http://people.ubuntu.com/~bryce/BulletProofX/100_0938.m.JPG[/IMG]]("http://people.ubuntu.com/~bryce/BulletProofX/100_0938.m.JPG")
 But hey, all is not doom and gloom any more. With 7.10, you are no longer given a useless and arcane error dialog, you are now shown displayconfig-gtk to allow you to fix that broken config and get back on your feet:
 [[IMG]http://people.ubuntu.com/~bryce/BulletProofX/100_1116.m.JPG[/IMG]]("http://people.ubuntu.com/~bryce/BulletProofX/100_1116.m.JPG")
 If you want to read a bit more, check out the X.org maintainer for Ubuntu, Bryce Harrington&#8217;s, [article on BulletproofX]("http://people.ubuntu.com/~bryce/BulletProofX/")
 Tomorrow, it&#8217;s off to explore all the new shiny with Desktop Effects, as brought to you by Compiz Fusion. Until then!
 

[More...](http://fridge.ubuntu.com/node/1156)

---

