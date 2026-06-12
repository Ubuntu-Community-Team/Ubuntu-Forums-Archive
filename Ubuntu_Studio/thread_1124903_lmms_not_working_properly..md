---
title: "lmms not working properly."
date: 2009-04-13
forum: Ubuntu Studio
---

### Post by translucent juicebox on 2009-04-13
I just installed lmms from the synaptic package manager program, and while it starts up, it doesn't work quite right.  The demo files and synths that were supposed to come with lmms, didn't, and the graphics are all wrong.  I uploaded a screenshot of LMMS running on my computer to be compared to some screenshots here, [http://lmms.sourceforge.net/screenshots.php](http://lmms.sourceforge.net/screenshots.php) to illustrate what&#347; wrong with it.

Take note of how there is simply a dot on all of the buttons, instead of the appropriate symbol for the button's function.

---

### Post by ad_267 on 2009-04-13
Do you have the lmms-common package installed? It should have been automatically installed as a dependency.

---

### Post by translucent juicebox on 2009-04-13
yeah, lmms-common was automatically installed with the lmms package.

---

### Post by Stochastic on 2009-04-13
I don't know where to begin troubleshooting that version of lmms, all I can offer as advice is to upgrade to a newer version.  This can be done a few different ways:
- wait until Ubuntu Jaunty 9.04 is released on April 23rd and upgrade to the 0.4.2 version in those repositories when you upgrade your system
- compile lmms from source (probably the hardest technical option of the three)
- download a newer .deb file for lmms from some other website

---

### Post by mc4man on 2009-04-13
While it's not too difficult to build here's a ppa with current lmms packages for 8.04 > 8.10 and I guess 9.04

[https://edge.launchpad.net/~tobydox/+archive/ppa](https://edge.launchpad.net/~tobydox/+archive/ppa)

While it may not be related if you have a nvidia card and are using the 96 drivers on 8.10 then the menus of some apps may be blank

---

### Post by simtaalo on 2009-04-15
yeah you really shouldn't be trying to run that version of lmms, its really outdated. unfortunately its the one in the repo's, but use the above links and get 0.4.3 and have fun :)

---

### Post by translucent juicebox on 2009-04-15
Whenever I try to install the newer lmms I get, the following. 


Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies.  make sure that all the required repositories are added and enabled in preferences.

lmms:
  Depends: libasound2 (>1.0.18) but 1.0.17a-0ubuntu4 is to be installed
  Depends: libjack0 (>=0.116.1) but 0.109.2-3ubuntu1 is to be installed
  Depends: libpulse0 (>=0.9.14) but 0.9.10-2ubuntu9.3 is to be installed
  Depends: libqt4-xml (>=4.5.0~+rc1) but 4.4.3-0ubuntu1.2 is to be installed
  Depends: libqtcore4 (>=4.5.0~+rc1) but 4.4.3-0ubuntu1.2 is to be installed
  Depends: libqtgui4 (>=4.5.0~+rc1) but 4.4.3-0ubuntu1.2 is to be installed


But I already have all of these dependencies installed, so I don't understand why it says I don't.

EDIT:  I don't know why that smiley face is there, ignore it.

---

### Post by Stochastic on 2009-04-15
hmm it looks like you're attempting to install a package that wasn't designed for your system.

What version of Ubuntu are you running and what dos the output of ```
cat /etc/apt/sources.list
``` say?

---

### Post by translucent juicebox on 2009-04-16
I'm running Xubuntu 8.10, and running that command in terminal gave me...

bash: cat/ect/apt/sources.list: No such file or directory

Although if that commands means to list what Third-Party Software Sources I have checked off, then I have only [http://ppa.launchpad.net/tobydox/ppa/ubuntu](http://ppa.launchpad.net/tobydox/ppa/ubuntu) jaunty.

---

### Post by ad_267 on 2009-04-17
There should be a space after cat, but you're right it just shows what software sources you're using.

And the problem is you're using the repository for Jaunty (9.04), you should have:
deb [http://ppa.launchpad.net/tobydox/ppa/ubuntu](http://ppa.launchpad.net/tobydox/ppa/ubuntu) intrepid main

---

### Post by translucent juicebox on 2009-04-17
Nevermind, I just compiled it from source instead.  But I still have problems.  There are still dots on all the buttons, there's a black space for the keyboard at the bottom of the synth plugin's window, some knobs are a black space, amongst other things.  But the plugins were included, and It does make noises, so I'm making some progress.

Nevermind the above also. :)  I closed lmms and restarted it, and it looks just the way it should.  Strange eh?

---

### Post by wsonar on 2009-04-17
I originally built mind from source following the directions on the lmms
website

---

