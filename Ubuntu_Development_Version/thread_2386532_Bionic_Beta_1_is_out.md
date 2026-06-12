---
title: "Bionic Beta 1 is out"
date: 2018-03-07
forum: Ubuntu Development Version
---

### Post by slickymaster on 2018-03-07
Bionic Beta 1 for all flavours is out for testing. ISOs are available on the tracker at [http://iso.qa.ubuntu.com/qatracker/milestones/387/builds](http://iso.qa.ubuntu.com/qatracker/milestones/387/builds)

This is the first beta Bionic milestone so please take a few minutes of your time to test it and please do report your testing in the tracker.

---

### Post by cruzer001 on 2018-03-07
The flavors are listed at ISO Tracker, but not Ubuntu.  Why is that?

Must this be a fresh install or is a update of an existing install acceptable?

---

### Post by exploder on 2018-03-07
> The flavors are listed at ISO Tracker, but not Ubuntu. Why is that?

Must this be a fresh install or is a update of an existing install acceptable? 

Ubuntu is not participating in the bets one release. If you kept your system up to date you have beta one.

---

### Post by slickymaster on 2018-03-07
> **exploder said:**
> Ubuntu is not participating in the bets one release. If you kept your system up to date you have beta one.
Exactly. Only the flavours taking part in this milestone are listed there.

---

### Post by corradoventu on 2018-03-07
I downloaded the ISO but is still named alpha: Ubuntu 18.04 LTS "Bionic Beaver" - Alpha amd64 (20180307)

---

### Post by flocculant on 2018-03-08
> **cruzer001 said:**
> The flavors are listed at ISO Tracker, but not Ubuntu.  Why is that?

Must this be a fresh install or is a update of an existing install acceptable?

Ubuntu stopped taking part in milestones up to Final Beta a good few cycles ago.

---

### Post by kerry_s on 2018-03-08
i'm going to try that lubuntu next see how lxqt is doing.

i tried the xubuntu core a couple of days ago but the installer kept crashing. any issue with the regular xubuntu installer?

well lubuntu next was a waste in time.
[ATTACH=CONFIG]278849[/ATTACH]

---

### Post by kansasnoob on 2018-03-08
> **kerry_s said:**
> i'm going to try that lubuntu next see how lxqt is doing.

i tried the xubuntu core a couple of days ago but the installer kept crashing. any issue with the regular xubuntu installer?

well lubuntu next was a waste in time.
[ATTACH=CONFIG]278849[/ATTACH]

Yep, it's borked :(

I have managed to get it installed choosing openbox but it doen't run well enough to even begin using it.

---

### Post by slickymaster on 2018-03-08
> **kerry_s said:**
> i'm going to try that lubuntu next see how lxqt is doing.

i tried the xubuntu core a couple of days ago but the installer kept crashing. any issue with the regular xubuntu installer?

well lubuntu next was a waste in time.
[ATTACH=CONFIG]278849[/ATTACH]

> **kansasnoob said:**
> Yep, it's borked :(

I have managed to get it installed choosing openbox but it doen't run well enough to even begin using it.

Not seeing/getting that here. I have Xubuntu 18.04 core running on a 2007 Asus Eee PC.

---

### Post by cruzer001 on 2018-03-08
> **kansasnoob said:**
> Yep, it's borked :(

I have managed to get it installed choosing openbox but it doen't run well enough to even begin using it.

Same results with LXQT.  On my install when asked to choose a WM, it took me to my bin directory where only OB would work.

---

### Post by kerry_s on 2018-03-08
> Not seeing/getting that here. I have Xubuntu 18.04 core running on a 2007 Asus Eee PC.
is that the current 1 from beta download.

> Same results with LXQT. On my install when asked to choose a WM, it took me to my bin directory where only OB would work.
i missed ob, i chose lxqt-session, just got the black screen with the x cursor

---

### Post by flocculant on 2018-03-08
> **kerry_s said:**
> is that the current 1 from beta download...

Xubuntu Core isn't at a beta level - it's currently done seperately. We've been trying for some time to get it built officially at which point it would make it on to the tracker properly.

Currently the iso is available from one of the Xubuntu Team at [http://unit193.net/xubuntu/core/pending/](http://unit193.net/xubuntu/core/pending/)

---

### Post by slickymaster on 2018-03-08
> **kerry_s said:**
> is that the current 1 from beta download.
....

Nopes.
> **flocculant said:**
> Xubuntu Core isn't at a beta level - it's currently done seperately. We've been trying for some time to get it built officially at which point it would make it on to the tracker properly.

Currently the iso is available from one of the Xubuntu Team at [http://unit193.net/xubuntu/core/pending/](http://unit193.net/xubuntu/core/pending/)
This one ^^^

---

### Post by kerry_s on 2018-03-08
> **flocculant said:**
> Xubuntu Core isn't at a beta level - it's currently done seperately. We've been trying for some time to get it built officially at which point it would make it on to the tracker properly.

Currently the iso is available from one of the Xubuntu Team at [http://unit193.net/xubuntu/core/pending/](http://unit193.net/xubuntu/core/pending/)

i just grabbed the regular xubuntu from beta 1, i'll try that 1 later.
i have hospital app. today so i'm getting ready to go now. although i would rather play, hate hospitals.

---

### Post by kerry_s on 2018-03-08
xubuntu core still crashes during install
[ATTACH=CONFIG]278862[/ATTACH]

xubuntu 18 installs but the settings are screwy, i wanted to change the display, but it crashes on launch.
the display settings says segmentation fault, core dumped. reported it
[ATTACH=CONFIG]278863[/ATTACH]

---

### Post by slickymaster on 2018-03-08
> **kerry_s said:**
> xubuntu core still crashes during install
[ATTACH=CONFIG]278862[/ATTACH]

xubuntu 18 installs but the settings are screwy, i wanted to change the display, but it crashes on launch.

Are you going directly to the 'Install' option? If that's the case would you mind to try another approach?

Select the 'Try' option and once there use the install icon in the desktop. Reason being that we had some testers reporting what you're getting but being able to proceed with the installation this way.

---

### Post by #&amp;thj^% on 2018-03-08
> **slickymaster said:**
> Are you going directly to the 'Install' option? If that's the case would you mind to try another approach?

**_Select the 'Try' option _**and once there use the install icon in the desktop. Reason being that we had some testers reporting what you're getting but being able to proceed with the installation this way.

+1

---

### Post by kerry_s on 2018-03-08
> **slickymaster said:**
> Are you going directly to the 'Install' option? If that's the case would you mind to try another approach?

Select the 'Try' option and once there use the install icon in the desktop. Reason being that we had some testers reporting what you're getting but being able to proceed with the installation this way.

yeah, that ends the same way.
it could just be a vm thing, i'm using gnome boxes.

---

### Post by slickymaster on 2018-03-08
> **kerry_s said:**
> yeah, that ends the same way.
it could just be a vm thing, i'm using gnome boxes.

Didn't had any issues with VMware and VB

---

### Post by kerry_s on 2018-03-08
> **slickymaster said:**
> Didn't had any issues with VMware and VB

don't know what to tell you, i only currently have 3 vm's, including the xubuntu 18 i just grabbed this mourning, still plenty of space on my ssd drive.
[ATTACH=CONFIG]278865[/ATTACH]

---

### Post by flocculant on 2018-03-08
> **kerry_s said:**
> don't know what to tell you, i only currently have 3 vm's, including the xubuntu 18 i just grabbed this mourning, still plenty of space on my ssd drive.
[ATTACH=CONFIG]278865[/ATTACH]

thanks for trying it out - will pass it along :)

---

### Post by VMC on 2018-03-08
xubuntu-b1 partition install hasn't crashed once, and I have been working it hard. Installing a lot of stuff. Playing music, movies... lubuntu is another story.

---

### Post by kerry_s on 2018-03-08
> **flocculant said:**
> thanks for trying it out - will pass it along :)

i do click the report button, hopefully that helps.

> xubuntu-b1 partition install hasn't crashed once, and I have been working it hard. Installing a lot of stuff. Playing music, movies... lubuntu is another story.

it's the display setting that crashes, on me. i usually set to native resolution & go full screen to play with.
so i'm stuck like this for now, hopefully a update will fix. also terminal output.
[ATTACH=CONFIG]278866[/ATTACH]

---

### Post by VMC on 2018-03-08
> **kerry_s said:**
> i do click the report button, hopefully that helps.



it's the display setting that crashes, on me. i usually set to native resolution & go full screen to play with.
so i'm stuck like this for now, hopefully a update will fix. also terminal output.
[ATTACH=CONFIG]278866[/ATTACH]

Here's mine. As I stated, its on a partition:
[https://imgur.com/YQd0wbV](https://imgur.com/YQd0wbV)

---

### Post by kerry_s on 2018-03-08
> **VMC said:**
> Here's mine. As I stated, its on a partition:
[https://imgur.com/YQd0wbV](https://imgur.com/YQd0wbV)

like i said most likely the vm.
i just installed ubuntu 18 & i'm going to use virtual machine manager instead of gnome boxes, which is broken on 18
still getting things setup the way i like before i start downloading.

---

### Post by kerry_s on 2018-03-08
yeap, it looks like it was gnome boxes at fault.

i got it running in vmm, it's working like a champ, currently updating.

my apologies for using a crappy vm :)

---

### Post by flocculant on 2018-03-09
> **kerry_s said:**
> yeap, it looks like it was gnome boxes at fault.

i got it running in vmm, it's working like a champ, currently updating.

my apologies for using a crappy vm :)

ha ha - no apology needed :p

ftr I tend to use qemu/kvm now pretty much exclusively - helps that I know the name of one of the people at Canonical who maintains it - 'oi this thing's broken - again!'
 :D

---

### Post by sudodus on 2018-03-09
I tested **Lubuntu alternate i386**. Many of the texts in the [alternate] installer's dialogue were bad, when I selected Swedish.

I reported it as a bug. Please try it! I think you must set a non-English language in order to reproduce the bug.

[Bug #1754646: Texts in the dialogue in Swedish is faulty in Lubuntu alternate Bionic beta 1](http://launchpad.net/bugs/1754646)

If you are affected, please mark 'affects me too' at the bug report to confirm the bug.

Edit:

**Ubuntu Server bionic daily** suffers from the same bug, I am testing it right now with Swedish in a USB pendrive cloned from

**bionic-server-amd64.iso**

---

### Post by sports fan Matt on 2018-03-10
Downloading it now.

---

