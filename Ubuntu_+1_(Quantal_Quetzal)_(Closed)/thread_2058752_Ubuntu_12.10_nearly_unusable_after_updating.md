---
title: "Ubuntu 12.10 nearly unusable after updating"
date: 2012-09-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kaefert66014235 on 2012-09-16
Hi there!

I'm owning an Asus Zenbook UX23VD and installed Ubuntu 12.10 alpha3 a few weeks ago. Now that beta1 is out and I upgraded my installation, I have a lot of problems with my desktop:

[LIST]
[*]My desktop icons are missing. Files and folders that are placed in "/home/myusername/Arbeitsfläche" are not visible on the desktop. I cannot draw selections on my desktop with my mouse.

[*]When I'm on an empty workspace (no open window) the windows or super-button on my keyboard doesn't open the unity stuff that it should.

[*]When I have open windows, then the super button does open this unity stuff, but its drawn below the open windows.

[*]The Keyboard combinations from the compiz plugins "move window" and "resize window" are imediatly reset to super+button1 and super+button2 when try to set them to alt+button1 and alt+button2 which was the default on most linux desktops I have seen as of yet. Those super+button combinations are not really a good choice, since long presing super will show a popup with the available key-combinations of unity.

[*]One problem I have since the very start when I installed ubuntu 12.10 alpha3 on my notebook: I need to disable the compiz plugin "place window" in ccsm. If I do not, my windows always vanish from one workspace and materialise themselfs on some other random workspace.

[*]The package nautilus-open-terminal still gives me the context-menu entry to open a terminal, but the opened terminal when clicking it does only exist for two tenths of a second and vanishes before showing a prompt.

[*]chromium-browser sometimes has the default window decorations in addition to its own window decorations.
[/LIST]

Has anybody else observed any of those described problems? are there bug-reports for them somewhere? I could not find them. Do you think that a clean beta1 installation of ubuntu 12.10 would give me less problems?

---

### Post by dino99 on 2012-09-16
if its a dist-upgrade, and that partition has not got a fresh installation recently, cleaning the system might help. 
You can run gtkorphan & bleachbit (as root, but carefully) and rename (or remove) some hidden folders; .gconf, .local, .gnome2 & .config

Those will be cleanly recreated on next boot, but note that your custom settings will be reset to default indeed.

maybe a : sudo dpkg-reconfigure -phigh -a
(be patient, it can take a while)

---

### Post by epikvision on 2012-09-16
> **kaefert66014235 said:**
>  Has anybody else observed any of those described problems? are there bug-reports for them somewhere? I could not find them. Do you think that a clean beta1 installation of ubuntu 12.10 would give me less problems?

Wow, that's a surprise. The installation to beta should've been clean.  

I run the daily build of quantal, and so far, I haven't experienced any of those problems.  When I do see some bugs, I make sure I report them.  

If you don't see any bug reports related to your problems, try reporting them yourself.  Remember, you will need a [launchpad]("http://www.launchpad.net") account.

A clean installation is probably your best solution. Not only will you have less problems, but you're starting off fresh.

---

### Post by effenberg0x0 on 2012-09-16
> **kaefert66014235 said:**
> Hi there!

I'm owning an Asus Zenbook UX23VD and installed Ubuntu 12.10 alpha3 a few weeks ago. Now that beta1 is out and I upgraded my installation, I have a lot of problems with my desktop:

[LIST]
[*]My desktop icons are missing. Files and folders that are placed in "/home/myusername/Arbeitsfläche" are not visible on the desktop. I cannot draw selections on my desktop with my mouse.

[*]When I'm on an empty workspace (no open window) the windows or super-button on my keyboard doesn't open the unity stuff that it should.

[*]When I have open windows, then the super button does open this unity stuff, but its drawn below the open windows.

[*]The Keyboard combinations from the compiz plugins "move window" and "resize window" are imediatly reset to super+button1 and super+button2 when try to set them to alt+button1 and alt+button2 which was the default on most linux desktops I have seen as of yet. Those super+button combinations are not really a good choice, since long presing super will show a popup with the available key-combinations of unity.

[*]One problem I have since the very start when I installed ubuntu 12.10 alpha3 on my notebook: I need to disable the compiz plugin "place window" in ccsm. If I do not, my windows always vanish from one workspace and materialise themselfs on some other random workspace.

[*]The package nautilus-open-terminal still gives me the context-menu entry to open a terminal, but the opened terminal when clicking it does only exist for two tenths of a second and vanishes before showing a prompt.

[*]chromium-browser sometimes has the default window decorations in addition to its own window decorations.
[/LIST]

Has anybody else observed any of those described problems? are there bug-reports for them somewhere? I could not find them. Do you think that a clean beta1 installation of ubuntu 12.10 would give me less problems?

Hi, 

It's important to mention that some relatively new Asus models have a few problems with Linux in general (not only Ubuntu). There are issues and workarounds regarding VGA/OpenGL support, ACPI, keyboard mapping, etc. Some recent threads in General and Ubuntu Asus Support areas of UF address these problems. It's worth a search / read to see if the content of these threads matches what you are seeing there and helps somehow, before doing anything else. **EDIT:** Have a look [here]("http://ubuntuforums.org/showthread.php?t=2005756") for example.

Here are my wild guesses:
- You have properly performed a fresh install of Ubuntu 12.10 from the ISO but are dealing with Asus-specific problems I mentioned above; or

- You have properly performed a fresh install of Ubuntu 12.10 from the ISO but are not up-to-date to official repos or are using alternative/non-official sources/PPAs; or

- You have upgraded from 12.04 or a previous version to 12.10 and the upgrade failed or kept wrong deprecated settings.

It would be nice to know exactly how you installed/upgraded to 12.10 and if you are up-to-date to official Quantal repos, if you are using alternative sources/PPAs, etc. 

I have started answering your items one-by-one, but the number of possible answers to each is too broad, from VGA support to keyboard mapping. We need to know more to proceed. 

There's one thing that usually avoids a lot of tinkering and a long discussion: Do you see the same exact inconsistencies when you create a new user and login using it? Depending on your answer, a lot of possibilities can be excluded.

Regards,
Effenberg

---

### Post by kaefert66014235 on 2012-09-16
hey! thanks for the many answers, wasn't expecting you guys to be that fast ;)

Well I installed a fresh 12.10 alpha3 and upgraded it from time to time.

I am up-to-date now and I do use a few ppa's.. here's a list:

[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main
[http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) quantal main
--> for beeing able to use my nvidia card

[http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu](http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu) precise main
--> found this stuff to be quite nice

[http://ppa.launchpad.net/dajhorn/skype-call-recorder/ubuntu](http://ppa.launchpad.net/dajhorn/skype-call-recorder/ubuntu) precise main

[http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free
[http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main
[http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

UPDATE:
Okey, so I now removed most of those ppas, especially the scopes and removed the packages but that did not help.
I created a new user and logged into a unity session with it (instead of "rename (or remove) some hidden folders; .gconf, .local, .gnome2 & .config") but that also did not change the behaviour I've described.

could you please elaborate what I should do with gtkorphan & bleachbit?

---

### Post by kaefert66014235 on 2012-09-17
I got a very good advice from user "screemo" in this thread: 
[http://ubuntuforums.org/showthread.php?p=12243929#post12243929](http://ubuntuforums.org/showthread.php?p=12243929#post12243929)

sudo apt-get install ubuntu-desktop 

Now most of my bugs are gone, bugs left:

[LIST]
[*]The package nautilus-open-terminal still gives me the context-menu entry to open a terminal, but the opened terminal when clicking it does only exist for two tenths of a second and vanishes before showing a prompt.
[*]Using the mouse key combination alt + mouse button 2 often crashes compiz and makes it restart.
[*]I need to disable the compiz plugin "place window" in ccsm. If I do not, my windows always vanish from one workspace and materialise themselfs on some other random workspace. also random movements within a workspace do happen.
[/LIST]

---

### Post by screemo on 2012-09-17
> **kaefert66014235 said:**
> I got a very good advice from user "screemo" in this thread: 
[http://ubuntuforums.org/showthread.php?p=12243929#post12243929](http://ubuntuforums.org/showthread.php?p=12243929#post12243929)

sudo apt-get install ubuntu-desktop 

Now most of my bugs are gone, bugs left:

[LIST]
[*]The package nautilus-open-terminal still gives me the context-menu entry to open a terminal, but the opened terminal when clicking it does only exist for two tenths of a second and vanishes before showing a prompt.
[*]Using the mouse key combination alt + mouse button 2 often crashes compiz and makes it restart.
[*]I need to disable the compiz plugin "place window" in ccsm. If I do not, my windows always vanish from one workspace and materialise themselfs on some other random workspace. also random movements within a workspace do happen.
[/LIST]


Could you try this to fix your nautilus problem:
```

# sudo apt-get --purge remove nautilus-open-terminal
# rm -rf ~/.nautilus
# nautilus -q
# sudo apt-get install nautilus-open-terminal

```

Regarding the place window problems, this might be the bug you're hit with [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/974242](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/974242), and appears to be on the list for Beta2 of Quantal (ie. acknowledged).

However I'm not seeing it - are you using an external monitor ?

---

### Post by kaefert66014235 on 2012-09-17
> **screemo said:**
> Could you try this to fix your nautilus problem:
```

# sudo apt-get --purge remove nautilus-open-terminal
# rm -rf ~/.nautilus
# nautilus -q
# sudo apt-get install nautilus-open-terminal

```


hmm, nope, that didn't change the problem :(


> **screemo said:**
> 
Regarding the place window problems, this might be the bug you're hit with [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/974242](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/974242), and appears to be on the list for Beta2 of Quantal (ie. acknowledged).

However I'm not seeing it - are you using an external monitor ?

well yes I do also, but I've also seen the problem in the past without external monitors, and It's not only windows that are placed in between monitors.

---

### Post by mc4man on 2012-09-17
The open-in-terminal ext. is currently broken. bug on
[https://bugs.launchpad.net/ubuntu/+source/nautilus-open-terminal/+bug/1046791](https://bugs.launchpad.net/ubuntu/+source/nautilus-open-terminal/+bug/1046791)

However I'm pretty  sure that it is the same glib bug as seen here, so when glib gets repaired the ext. should start working
(I have it working here now with a repaired glib
[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1051447](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/1051447)

---

### Post by kaefert66014235 on 2012-09-18
Thanks for the find mc4man!

Is there a simple way to apply this patch to my system or do I need to wait till it finds its way into the repositories?

---

### Post by mc4man on 2012-09-20
> **kaefert66014235 said:**
> Thanks for the find mc4man!

Is there a simple way to apply this patch to my system or do I need to wait till it finds its way into the repositories?

The new glib upgrade today to  2.33.14-1 will return function of the open-in-terminal extension

---

### Post by kaefert66014235 on 2012-09-20
> **mc4man said:**
> The new glib upgrade today to  2.33.14-1 will return function of the open-in-terminal extension

yes!!! thanks man! you're great! the ubuntu devs are great! :D

---

