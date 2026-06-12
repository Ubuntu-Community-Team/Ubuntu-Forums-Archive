---
title: "libopenvrml5-dev &amp; libxul-dev request removal of packages"
date: 2007-02-01
forum: Repositories &amp; Backports
---

### Post by HugoRune on 2007-02-01
(System: Ubuntu edgy 64bit with kubuntu-desktop installed)

I want to use the openvrml library in a project

So I tried to install libopenvrml5-dev

This is dependant on libxul-dev, which in turn is dependant on
 libnss3-dev 
 libnspr4-dev 
 libmozjs-dev 

When I install either libopenvrml5-dev or libxul-dev, synaptic just displays a message that it depends on that "but it is not going to be installed" and stops. Adept fails in a similar way.

If I try to install libnss3-dev, libnspr4-dev or  libmozjs-dev manually the package manager wants to remove a lot of packages, among them:

Anjuta
Evolution
Firefox
nautilus
ubuntu-desktop
gnome-session
gnome-terminal
gnome-app-install

I definitely need some of these, especially firefox, and I am afraid to remove the rest either, so is there a way to install the openvrml libraries for me?


UPDATE:
I am currently trying to build openvrml from source. If that works I probably will not need that package after all. Still, I am curious how to solve this sort of problem.

---

### Post by jalirious on 2007-03-08
Alright Hugo, how's the building openvrml going? I'm trying to get it on my 6.06 to use it with GEANT4. Fucken nightmare.




> **HugoRune said:**
> (System: Ubuntu edgy 64bit with kubuntu-desktop installed)

I want to use the openvrml library in a project

So I tried to install libopenvrml5-dev

This is dependant on libxul-dev, which in turn is dependant on
 libnss3-dev 
 libnspr4-dev 
 libmozjs-dev 

When I install either libopenvrml5-dev or libxul-dev, synaptic just displays a message that it depends on that "but it is not going to be installed" and stops. Adept fails in a similar way.

If I try to install libnss3-dev, libnspr4-dev or  libmozjs-dev manually the package manager wants to remove a lot of packages, among them:

Anjuta
Evolution
Firefox
nautilus
ubuntu-desktop
gnome-session
gnome-terminal
gnome-app-install

I definitely need some of these, especially firefox, and I am afraid to remove the rest either, so is there a way to install the openvrml libraries for me?


UPDATE:
I am currently trying to build openvrml from source. If that works I probably will not need that package after all. Still, I am curious how to solve this sort of problem.

---

### Post by HugoRune on 2007-03-19
I managed to compile it a while ago, i made the following notes about the process

```
  requires boost 
    configure does not notice missing boost
    --> installed libboost-dev 1.33.1 7ubuntu1
  requires boost-thread
    configure does not notice missing boost-thread, no mention in manual
    quite confusing error-message
    --> installed libboost-thread 1.33.1 7ubuntu1 and libboost-thread-dev

```
I may have had to install a couple of other libraries before that.
Afterwards, compiling took almost 30 hours

But the whole thing seemed quite useless, choking on simple vrml files and making mistakes while parsing.

Currently I am using openSG 1.8 (newest version) to parse vrml, which works quite nice.

---

### Post by crc_canada on 2007-03-25
> **jalirious said:**
> Alright Hugo, how's the building openvrml going? I'm trying to get it on my 6.06 to use it with GEANT4. Fucken nightmare.

Jalirious;

I know that people use the VRML2 output format with FreeWRL; seems to work.

notes from the FreeWRL maintainer (me)

1) the latest parser crashes if you specify vrml1 as an output. I'll put a check into the code before the next release;

2) next release; I've currently got a colleague creating and testing rpms for Fedora Core 6 of the latest and greatest code; final touches going in shortly; after that comes the latest Ubuntu for i386 and amd-64. 

3) OpenVRML is a *good* piece of software - Braden, the creator, is a very bright person; if you want to keep on with the OpenVRML build - no problem.

If you decide to use FreeWRL, keep your eyes peeled on [http://freewrl.sf.net](http://freewrl.sf.net), and, please send in comments (both good and bad). We like to know how we're doing.

John A. Stewart
CRC Canada
[http://www.crc.ca/FreeWRL](http://www.crc.ca/FreeWRL)

---

