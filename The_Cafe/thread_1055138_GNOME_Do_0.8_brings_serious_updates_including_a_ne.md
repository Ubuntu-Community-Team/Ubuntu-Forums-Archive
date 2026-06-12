---
title: "GNOME Do 0.8 brings serious updates including a new dock"
date: 2009-01-30
forum: The Cafe
---

### Post by wersdaluv on 2009-01-30
GNOME Do is one of the most essential applications for me, another reason why I can't ditch GNOME for KDE 4.2. It's a keystroke launcher... I mean, do-er. What it does is to allow the user to do things on the desktop as fast and intuitively as possible with a few keystrokes. A new version is out and this brought the greatest improvements to the application so far. It brings bug fixes, new plugins, new themes, a new dock, plus more. 

If you don't have it yet, download it now! :KS

[http://do.davebsd.com/release.shtml](http://do.davebsd.com/release.shtml)

[http://lifehacker.com/5142692/gnome-do-08-brings-great-plug+ins-intuitive-dock-to-linux](http://lifehacker.com/5142692/gnome-do-08-brings-great-plug+ins-intuitive-dock-to-linux)

---

### Post by Sealbhach on 2009-01-30
Thanks, Gnome Do is rockin. Is this a later version than the one in the repos?


.

---

### Post by FuturePilot on 2009-01-30
> **Sealbhach said:**
> Thanks, Gnome Do is rockin. Is this a later version than the one in the repos?


.

You can get the latest version here [https://launchpad.net/~do-core/+archive/ppa]("https://launchpad.net/~do-core/+archive/ppa")

---

### Post by zachtib on 2009-01-30
> **FuturePilot said:**
> You can get the latest version here [https://launchpad.net/~do-core/+archive/ppa]("https://launchpad.net/~do-core/+archive/ppa")

The amd64 builds are still failing to build :(

---

### Post by FuturePilot on 2009-01-30
> **zachtib said:**
> The amd64 builds are still failing to build :(

Looks like there's one here [https://edge.launchpad.net/do/trunk/0.8.0]("https://edge.launchpad.net/do/trunk/0.8.0") :)

---

### Post by zachtib on 2009-01-30
> **FuturePilot said:**
> Looks like there's one here [https://edge.launchpad.net/do/trunk/0.8.0]("https://edge.launchpad.net/do/trunk/0.8.0") :)

cool, though I still hope they get the repo working so i don't have to manually grab upgrades

---

### Post by btdown on 2009-01-30
I don get it..I installed it, then ran it..and it does nothing. How do you work the darn thing?

---

### Post by dorkdork777 on 2009-01-30
It should have put an icon in the system tray. Right-click it to select preferences, or click it to start it.

EDIT: Installed on my 64-bit machine thanks to FuturePilot's link :) It didn't put an icon in my tray; weird. You might have to use Super+Space to bring it up; click the triangle in the top corner to open Preferences.

---

### Post by aaaantoine on 2009-01-30
> **wersdaluv said:**
> GNOME Do is one of the most essential applications for me, another reason why I can't ditch GNOME for KDE 4.2.

Gnome Do *is* awesome, but last I checked you can run it in KDE.

Also I've found that Kicker behaves similarly to Gnome Do.

---

### Post by Sealbhach on 2009-01-30
> **dorkdork777 said:**
> 
EDIT: Installed on my 64-bit machine thanks to FuturePilot's link :) It didn't put an icon in my tray; weird. 

Same here, I just dragged the icon from Applications/Accessories up to the panel.

I tried Docky, but like all docks I've tried I dislike it....:(

I guess it's just personal preference, I don't like docks.


.

---

### Post by binbash on 2009-01-30
There is a big thread about this.

---

### Post by Aiello on 2009-01-30
Well, I just downloaded and and sure is a neat little program. Unfortunately, the Hardy repositories only have version 0.6 or so, and thus are lacking some of the major updates. Anyway I can get 0.8 on 8.04?

---

### Post by aaaantoine on 2009-01-30
> **Aiello said:**
> Well, I just downloaded and and sure is a neat little program. Unfortunately, the Hardy repositories only have version 0.6 or so, and thus are lacking some of the major updates. Anyway I can get 0.8 on 8.04?

1. Check backports.
2. See if you can find a deb from a reliable source or third-party repository.
3. Compile from source.

---

### Post by GrouchoMarx on 2009-01-30
> **Aiello said:**
> Well, I just downloaded and and sure is a neat little program. Unfortunately, the Hardy repositories only have version 0.6 or so, and thus are lacking some of the major updates. Anyway I can get 0.8 on 8.04?

There is a [PPA]("https://edge.launchpad.net/~do-core/+archive/ppa"). Follow [these instructions]("https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories") to add the PPA to your sources list along with the matching PGP key.

Note that the instruction are specific for AWN. Just do the same procedure with Gnome-do's PPA and key.

---

### Post by wersdaluv on 2009-01-31
I just have to say this. I love Docky so much. It combined the concepts of the OS X Dock and the Windows 7 Superbar :D Brilliant! It just needs more polishing because it crashed on me twice when I was doing odd things. hehe

---

### Post by Aiello on 2009-01-31
I should mention that I have the Hardy PPA for GnomeDo, but this is only at 0.6. Can I enable the Intreiped PPA for GnomeDo, or will bad things happen?
Or should I just wait to see if it is updated?

---

### Post by b3n87 on 2009-01-31
I just installed gnome-do 0.8 and its painfully slow. completely unusable. My machine is more than capable of running it so im not sure whats wrong :/

---

### Post by mknepher on 2009-01-31
If you're running an nVidia card, you may need to do the following:

kill gnome-do
in a terminal run:

nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1

then restart gnome-do

---

### Post by days_of_ruin on 2009-01-31
> **Aiello said:**
> I should mention that I have the Hardy PPA for GnomeDo, but this is only at 0.6. Can I enable the Intreiped PPA for GnomeDo, or will bad things happen?
Or should I just wait to see if it is updated?

I tried that.It wouldn't install.

---

### Post by banjobacon on 2009-01-31
> **mknepher said:**
> If you're running an nVidia card, you may need to do the following:

kill gnome-do
in a terminal run:

nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1

then restart gnome-do

What does this do?

---

### Post by b3n87 on 2009-02-01
> **mknepher said:**
> If you're running an nVidia card, you may need to do the following:

kill gnome-do
in a terminal run:

nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1

then restart gnome-do

LOL!

how did you know that?

worked a treat!

---

### Post by speedwell68 on 2009-02-01
> **Sealbhach said:**
> 
I tried Docky, but like all docks I've tried I dislike it....:(

I guess it's just personal preference, I don't like docks.


.

Ditto.:D  But I do love gnome do.

---

### Post by hyperdude111 on 2009-02-01
To install on AMD64 you need to compile from source then it works.

---

### Post by moore.bryan on 2009-02-01
has anyone been able to get all the icons in docky to look right? any of the prism icons are rendered like garbage, no matter what iconset i use.

---

### Post by GrouchoMarx on 2009-02-02
> I should mention that I have the Hardy PPA for GnomeDo, but this is only at 0.6. Can I enable the Intreiped PPA for GnomeDo, or will bad things happen?
Or should I just wait to see if it is updated?

> I tried that.It wouldn't install. 

There is a drop-down menu just above these lines:
> deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) intrepid main
on the launchpad PPA that gives you the hardy deb entries. Really all you need to do is change "intrepid" to "hardy".

---

### Post by Aiello on 2009-02-02
> **GrouchoMarx said:**
> There is a drop-down menu just above these lines:

on the launchpad PPA that gives you the hardy deb entries. Really all you need to do is change "intrepid" to "hardy".

I have already done this, but their repositories are only at 0.6.1.0 for Hardy.

---

### Post by KVan D on 2009-02-02
I'm having the same issue as Aiello. I'm running Hardy Server, and the launchpad repositories only bring me up to version 0.6.

---

### Post by Dr.Suave on 2009-02-10
I'm running Intrepid, and can still only get my hands on 0.6.1.0 from the repos.

---

