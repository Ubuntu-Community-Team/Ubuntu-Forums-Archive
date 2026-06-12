---
title: "Ubuntu Studio - What is it really?"
date: 2007-11-04
forum: The Cafe
---

### Post by ryanVickers on 2007-11-04
We've all seen it talked about, the themes, the programs, etc., but what *really* is it!?  If you go into "Add/Remove", it appears to be just a program, but in some discussions and other places, a guy could get the idea it's a whole other -buntu, like kubuntu, xubuntu, etc.!  What is it *really*?

This post can be used as a place to answer the question, ;), or just discuss the differences/values/problems/improvements over regular Ubuntu (in the event that it really *is* another -buntu...) :)

---

### Post by bobbocanfly on 2007-11-04
Its an officially supported Ubuntu derivative focusing mainly on Video, Image and Music creation/editing. Linux For The Media Monkeys. Instead of installing desktop apps by default and having desktop like apps in its repositories, it has media creation apps by default and in its repos.

---

### Post by ryanVickers on 2007-11-04
then what exactly is the program in the regular repos of Ubuntu!? :p

---

### Post by WinterWeaver on 2007-11-04
here is the True Ubuntustudio... [http://ubuntustudio.org/](http://ubuntustudio.org/)

I believe the Ubuntu Studio program in the Add/Remove Programs, is the menu that launches the various apps.

follow the link I gave you, and that gives you the Full Ubuntu install.

WW

---

### Post by markp1989 on 2007-11-04
i know this is off subject, i tried installing ubuntu studio from add/remove, and when i start it i get a message saying somthing about jack server?

---

### Post by bobbocanfly on 2007-11-04
> **markp1989 said:**
> i know this is off subject, i tried installing ubuntu studio from add/remove, and when i start it i get a message saying somthing about jack server?

Im guessing its something to do with Ubuntustudios audio. JACKLab is another audio editing distro. Just a guess though.

---

### Post by misfitpierce on 2007-11-04
Ubuntu Studio is a nice project as well imo. :)

---

### Post by antiserious on 2007-11-04
[https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)

---

### Post by pelle.k on 2007-11-04
You need to learn the difference between a "program", which is an application (singular), and a "suite" of applications, settings and artwork which is what ubuntu studio is. They have their own repository with extra packages, not programs, and that includes custom built kernel, drivers (modules), audio and video editing applications, and custom artwork (i.e. gnome icons, wallpaper and theme).

---

### Post by Rexbron! on 2007-11-04
What you have to understand is the history of Ubuntu Studio. 
A Short History of Ubuntu Studio


It initally started off as a wiki page (UbuntuStudioPreparation) describing how to configure a default Ubuntu dapper installation to be better suited to audio production. 

The author of that wiki page produced an app, what you are seeing in Add/Remove to centralize the initalization and set up of the applications documented in the wiki page. 

After durring the edgy release cycle, the author of the wiki page, ManicMusician IIRC, and _MMA_ discussed the idea of an  Ubuntu based distro that provides a set of applications targeted at musicians, graphics artists and film makers. (Due to the current state of video on linux, the video part is lacking, but that is changing with apps like kdenlive, the MLT framework and OpenLibraries)

The first release of Ubuntu Studio as a distro was fiesty. Fiesty had it's own repo because we missed the new package freeze on some very important apps. 

With the release of Ubuntu Studio gutsy, all the packages are in the official repos. The ubuntustudio meta packages provide a good selection of apps for their respective diciplines.

As for hardy, check out the artwork on wiki.ubuntu.com/UbuntuStudio.

As a member of Ubuntu Studio's dev team, I have my own set of a packages that I am going to get into the release (OpenLibraries, Jahtools and freemix).

Hope that answers the question. :)

---

### Post by Ultra Magnus on 2007-11-04
I think Ubuntu Studio does a bit of tweaking to the kernal to make it better for audio stuff - heard that somewhere but I'm not really sure

---

### Post by Nekiruhs on 2007-11-04
> **Ultra Magnus said:**
> I think Ubuntu Studio does a bit of tweaking to the kernal to make it better for audio stuff - heard that somewhere but I'm not really sure
Its more than a bit. Its a practically a real time kernel. That makes a huge difference in the audio and video sides of things.

---

### Post by thisllub on 2007-11-04
I use 64 studio on this machine and Ubuntustudio Feisty on another.

I will ditch Suse 10.3 on my alternate partition to try US 64 bit.

The big downside to real-time / low latency kernels is that  Virtual machine hosts have problems with them. A friend suggested running VirtualBox running on the same priority as audio. A good idea that I will try soon.

---

### Post by HotCocoa on 2007-12-31
The ubuntu-studio packages in the repository are packages to install Ubuntu Studio on your computer.  I know because I'm converting to Studio right now :)
EDIT: Install successful. I confirm this post.

---

