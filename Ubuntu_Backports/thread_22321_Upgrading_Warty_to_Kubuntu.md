---
title: "Upgrading Warty to Kubuntu?"
date: 2005-03-26
forum: Ubuntu Backports
---

### Post by stoneguy on 2005-03-26
Does it make any sense to try to upgrade from Warty (with some non-Ubuntu repositories just to make it more difficult) to Kubunu, or should I just install Kubuntu from scratch?

Reason - that gnome-vfs bug [indent][http://bugzilla.gnome.org/show_bug.cgi?id=110191](http://bugzilla.gnome.org/show_bug.cgi?id=110191)[/indent]
is a showstopper. I've got to be able to get to my Win98 shares via GUI.  Kubuntu seems to be able to do this, at least from my Preview Live.

---

### Post by techn9ne on 2005-03-27
Kubuntu is just hoary + kde libs.

---

### Post by stoneguy on 2005-03-27
[QUOTE=techn9ne]Kubuntu is just hoary + kde libs.[/QUOTE]

Using the word **just** that way always strikes terror into my heart  8-[  Yes, the KDE modules can be installed. But does Kubuntu do weird and wonderful things during installation for setting up the desktop that won't have been done in the DIY scenario? This appears to be the case - see [http://ubuntuforums.org/showthread.php?t=22061](http://ubuntuforums.org/showthread.php?t=22061)

---

### Post by poofyhairguy on 2005-03-27
[QUOTE=stoneguy]Using the word **just** that way always strikes terror into my heart  8-[  Yes, the KDE modules can be installed. But does Kubuntu do weird and wonderful things during installation for setting up the desktop that won't have been done in the DIY scenario? This appears to be the case - see [http://ubuntuforums.org/showthread.php?t=22061](http://ubuntuforums.org/showthread.php?t=22061)[/QUOTE]


As someone that has done it all (clean install kubuntu, install hoary then kubuntu, and install warty then upgrade to kubuntu) I recommend a clean install. The kubuntu menus are filled with gnome programs if you have both regular Ubuntu and Kubuntu on the system. Gets confusing and messy.

---

### Post by bored2k on 2005-03-27
[QUOTE=poofyhairguy]As someone that has done it all (clean install kubuntu, install hoary then kubuntu, and install warty then upgrade to kubuntu) I recommend a clean install. The kubuntu menus are filled with gnome programs if you have both regular Ubuntu and Kubuntu on the system. Gets confusing and messy.[/QUOTE]
 I second that opinion.

My experience with hoary then kubuntu install left me with a miriad bunch of error, mostly sound related and just pure uglyness [oh wait, that's KDE, nevermind]. Fresh installing it fixed most of the things I encountered before .

---

### Post by stoneguy on 2005-03-27
Ahhh. Nothing replaces the voice of experience. No diss to techn9ne, but before you've bloodied your nose 7x, see whether someone else knows how to avoid the obstacle.  :mrgreen: 

I spotted the *Permission Issues Fixed* announcement [http://www.ubuntuforums.org/showthread.php?p=106813#post106813](http://www.ubuntuforums.org/showthread.php?p=106813#post106813). Thankee, thankee, thankee. It was a little short on details, but after checking back thru Bugzilla, looks like they've dealt with what's bugging me about Hoary, so I won't have to cut over to Kubuntu.

Although I'm not in the developer loop, I'd be happy to give it a shot if someone pointed me to a nightly build of the LiveCD (if such thing exists - can't find any pointer in the fora).

---

### Post by poofyhairguy on 2005-03-27
[QUOTE=stoneguy]
Although I'm not in the developer loop, I'd be happy to give it a shot if someone pointed me to a nightly build of the LiveCD (if such thing exists - can't find any pointer in the fora).[/QUOTE]

Ask and you shall recieve:

[http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

---

### Post by techn9ne on 2005-03-28
I have hoary (fresh install). I installed kubuntu tried it for 10m didn't like it went back to gnome apt-get remove and it was gone. No problems at all.

---

### Post by stoneguy on 2005-03-28
For the record, no joy with Ubuntu Live Mar 28. Same old same old, as a matter of fact.

Maybe I should just wait until April 6 for the release version, and try the Hoary upgrade path. If that doesn't work, I can reinstall. And if *that* doesn't work, go for Kubuntu.

Edit: Just noticed on IRC that there's an RC scheduled for Mar 30. Will try again then.

---

### Post by stoneguy on 2005-03-31
Torrented the Hoary Live RC (and will seed for a few more days). No joy there either. 

Maybe it's got something to do with live-ness? 

Will wait for release and do the Hoary upgrade from the repositories (hopefully my Java and Firefox backports won't snarl things up). If there's still a problem, I'll wipe and install Kubuntu from CD. Thanks to ubuntu-geek's script [http://www.ubuntuforums.org/showthread.php?t=22646](http://www.ubuntuforums.org/showthread.php?t=22646) reinstallation will be a lot easier.

73

---

