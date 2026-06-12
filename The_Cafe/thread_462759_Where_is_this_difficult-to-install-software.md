---
title: "Where is this difficult-to-install-software?"
date: 2007-06-03
forum: The Cafe
---

### Post by Iandefor on 2007-06-03
After having received a lot of useful criticism in [another thread of a very similar title ]("http://ubuntuforums.org/showthread.php?t=237770")which I needed to sit on for a while to allow it to sink in, I've started to wonder: what software is out there that, for most people, is simply too difficult or more trouble than it is worth to get installed?

I've written up a few criteria for what seems fair to say is 'too difficult' based on the criticism in the other thread. Let's see if we can't get a *useful* list going of software that is too difficult to install; a list of what is out there that doesn't work for the 'average user' that can then begin to be remedied.
 
The criteria I've come up with are:

[LIST=1]
[*]The software is not in an official Ubuntu repository
[*]The software is not available in a third-party apt repository that satisfies all dependencies
[*]The software is not available as a prepackaged .deb, self-contained archive or binary installer that can satisfy all dependencies using official Ubuntu repositories.
[*]The software depends on packages outside of the official Ubuntu ecosystem to compile
[*]The software requires manual hacking on the code in order for it to work[/LIST] 
For clarity, newer versions of software that is already in the Ubuntu ecosystem will be clearly marked as such.

PS: I'm actually trying to get a useful list going of this software, so people who might be inclined to think that I'm going to arbitrarily set criteria in such a way to artificially keep the list small or that I'll apply the criteria too liberally to create a useful list may rest assured I'm not interested in letting that happen. My intentions in making this thread are much different than my intentions in making the other thread; the other thread was to prove a point. This thread is to be constructive. I'm also going to make a conscious effort to be more receptive to [constructive criticism]("http://en.wikipedia.org/wiki/Constructive_criticism").

---

### Post by KiwiNZ on 2007-06-03
I think say 3 years ago your list would have been huge due to dependency hell, but now, we have come along way . I think your list will be surprisingly short , I hope.
 
It will be an interesting thread to follow.

---

### Post by Iandefor on 2007-06-03
> **KiwiNZ said:**
> I think say 3 years ago your list would have been huge due to dependency hell, but now, we have come along way . I think your list will be surprisingly short , I hope.
 
It will be an interesting thread to follow. There were a surprising number of pieces of software mentioned in [this thread]("http://ubuntuforums.org/showthread.php?t=237770") that would have met the above criteria.

---

### Post by Iandefor on 2007-06-03
The list:

[ LSongs]("http://lsongs.com/")
[ DiskDrake]("http://qa.mandriva.com/twiki/bin/view/Main/DiskDrake")
[ CDEmu]("http://cdemu.sourceforge.net/") (.8 and 1.0; svn checkout works)
[Gendesign]("http://gendesign.sourceforge.net/") .5.3

As I can, I will populate this list with the projects mentioned in the other thread.

---

### Post by KiwiNZ on 2007-06-03
Haven't tried it for a while but Lgeneral was a pesky little bugger to install

---

### Post by Kingsley on 2007-06-03
I've always given up on installing cdemu.

---

### Post by kenthomson799 on 2007-06-03
> **Kingsley said:**
> I've always given up on installing cdemu.
CDEMU = i need that thing and it gives a variety of error messages on being installed--maybe that is what is causing the software to run irratically.

---

### Post by Iandefor on 2007-06-03
> **KiwiNZ said:**
> Haven't tried it for a while but Lgeneral was a pesky little bugger to install Lgeneral is in Multiverse in the following packages.

lgeneral (1.1.1-4ubuntu1)
lgc-pg (0.32-2)

I don't see any campaigns, but there are a few listed at [http://lgames.sourceforge.net/index.php?project=LGeneral](http://lgames.sourceforge.net/index.php?project=LGeneral)

> **Kingsley said:**
> I've always given up on installing cdemu. Here are my notes from installing it:
```
cdemu- cdemu: Unknown symbol generic_file_read after building .8
    experimental 1.0 module builds, installs, modprobes, complains of "cdemu_device_release: not implemented yet!" after rmmod but seems to get removed anyways
        -libmirage requires libsndfile-dev, in repos
        -cdemu-daemon requires libsysfs-dev, libdaemon, in repos, returns 1 upon running
        -cdemu-client builds

``` You can get 1.0 (for some reason, it's experimental but still called 1.0) source here: [http://kabelkaos.net/cdemu/experimental/](http://kabelkaos.net/cdemu/experimental/)

I also downloaded fragment-mac.tar.bz2 there and attempted to build it. Didn't work.

CDEMU added for now because of brokenness. I'll try the latest subversion tomorrow morning.

---

### Post by Iandefor on 2007-06-03
JEdit and F4L were mentioned in the other thread, so I tested those, as well as the subversion of CDEmu.

JEdit has a [working .deb]("http://www.jedit.org/index.php?page=download") which depends on software in Multiverse, F4L is now a part of [UIRA]("http://www.uira.org/"), and the subversion checkout of CDEmu *seemed* to work fine as far as mounting .iso files goes. I will try to test UIRA soon.

You can checkout CDEmu with this command:```
svn co https://cdemu.svn.sourceforge.net/svnroot/cdemu cdemu
```:

---

### Post by Adamant1988 on 2007-06-03
I have found that MugShot has been non-trivial to install.  I tried compiling from source and that just led to a long string of dependency problems that I was never able to resolve.  I tried to use an older .deb but that didn't work because of Ubuntu's packaging standards.  

In all honesty though, what you should be looking for is software that is non-trivial to install, not necessarily difficult.  Software that requires me to edit my sources.list is non-trivial, it represents a security risk, a standards issue (not many 3rd parties are going to keep up with Ubuntu's strict packaging standards), and can cause breakage.  (Upgrades have failed to work on systems that rely on 3rd party repos before).    Truly, the list of criteria should be modified to label software as non-trivial that: 

[LIST]
[*]Is compiled from source
[*]is from a 3rd party repo
[*]requires altering code or config files
[*]relies on software outside of Ubuntu's repos (long, ridiculous dependency chains)
[/LIST]

---

### Post by Iandefor on 2007-06-03
> **Adamant1988 said:**
> I have found that MugShot has been non-trivial to install.  I tried compiling from source and that just led to a long string of dependency problems that I was never able to resolve.  I tried to use an older .deb but that didn't work because of Ubuntu's packaging standards.  

In all honesty though, what you should be looking for is software that is non-trivial to install, not necessarily difficult.  Software that requires me to edit my sources.list is non-trivial, it represents a security risk, a standards issue (not many 3rd parties are going to keep up with Ubuntu's strict packaging standards), and can cause breakage.  (Upgrades have failed to work on systems that rely on 3rd party repos before).    Truly, the list of criteria should be modified to label software as non-trivial that:[LIST]
[*]Is compiled from source
[*]is from a 3rd party repo
[*]requires altering code or config files
[*]relies on software outside of Ubuntu's repos (long, ridiculous dependency chains)[/LIST]That also seems like a good set of criteria, but for something other than what I intend with this list. This list is aimed at software for which there is simply not an accessible installation path for most people (as opposed to a* trivial *installation path). I would say that triviality is another ballpark entirely.

You may find installation instructions for Mugshot here (albeit, non-trivial instructions), by the way: [http://developer.mugshot.org/wiki/Downloads#Ubuntu](http://developer.mugshot.org/wiki/Downloads#Ubuntu)

---

### Post by zugu on 2007-06-04
[ProjectM]("http://xmms-projectm.sourceforge.net/") and al its related deps.

---

### Post by Bou on 2007-06-04
As I said, [gendesign]("http://ubuntuforums.org/showpost.php?p=2761560&postcount=77") has been impossible to install so far.

---

### Post by Iandefor on 2007-06-04
> **zugu said:**
> [ProjectM]("http://xmms-projectm.sourceforge.net/") and al its related deps.From the ProjectM homepage: 
> projectM is a reimplementation of Milkdrop under OpenGL. projectM depends on OpenGL and [FTGL]("http://homepages.paradise.net.nz/henryj/code/#FTGL")(for fonts). [libvisual]("http://localhost.nl/%7Esynap/libvisual/") is also reccomended and is the preferred method of using projectM. Please port your music player to libvisual so you can use projectM. Libvisual and a development package for FTGL are both in the repositories, under the following names/versions:

[INDENT]libvisual-0.4-0 (0.4.0-1.1)
libvisual-0.4-dev (0.4.0-1.1)
ftgl-dev (2.1.2-3) [universe]
[/INDENT]With these, the ProjectM framework .99 compiles and install correctly without any special configuration options on my machine. xmms-projectm would fall outside of that, though. It isn't in the repositories and depends on projectM (which isn't, either).

---

### Post by Iandefor on 2007-06-04
> **Bou said:**
> As I said, [gendesign]("http://ubuntuforums.org/showpost.php?p=2761560&postcount=77") has been impossible to install so far.[Gendesign's site]("http://gendesign.sourceforge.net/help.html") claims it depends on a number of fairly straightforward things: > para compilar el gendesign necesitas las bibliotecas
gtk+-2.0 >= 2.10.11
glib-2.0 >= 2.12.11
libgnomeui-2.0 >= 2.18.1
libglade-2.0 >= 2.6.0
gnome-vfs-2.0 >= 2.18.0.1
libxml-2.0 >= 2.6.24 Which, for the Spanish-impaired, roughly means "gendesign depends on these libraries to compile" Those libraries are all readily available in the Ubuntu repositories. It also depends on gecko, which the help page doesn't mention. Gecko's development files are in the firefox-dev package.

make returns the following on compiling with version .5.3:```
make[2]: *** No rule to make target `README', needed by `all-am'.  Stop.
make[2]: Leaving directory `/home/ian/Desktop/gendesign-0.5.3'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ian/Desktop/gendesign-0.5.3'
make: *** [all] Error 2
``` I'm too tired to see if .5.2 will work right now, so gendesign will go on the list.

---

### Post by DarkMageZ on 2007-07-01
can i take xmms-projectm off that list?

[http://mirror.randumb.net/darkmagez/libprojectm/](http://mirror.randumb.net/darkmagez/libprojectm/)

---

### Post by tenmoi on 2007-07-01
to me it is the difficulty in installing software in linux that thrills me and attracted me to linux in the first place.
In fact one should play with ubuntu for a while to get drivers installed. First here is my machine specs: Acer 5570, 120 G hd, Nvidia Gefore go 7300, 256 Meg RAM.

To install driver for the Orbicam I first followed exactly as instructed on this thread [http://ubuntuforums.org/showthread.php?t=322218&highlight=orbicam](http://ubuntuforums.org/showthread.php?t=322218&highlight=orbicam) but then I did not hack anything as instructed. JUst make, make install, then modprobe gspca and open Ekiga to use the webcam.
SO my advice is tinker around with the machine and you may get things done.
Sencond, stick with Egdy I have never had any problems with it. I once installed Feisty and ran it to my most despair.

THis may seeam off-topic. BUt I think this may help.:D

---

