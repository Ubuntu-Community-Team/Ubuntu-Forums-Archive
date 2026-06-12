---
title: "mts video to other formats"
date: 2009-12-16
forum: Ubuntu Studio
---

### Post by Criminel on 2009-12-16
soft for .mts format conversion
Hi,
Does anyone know of  a good software for converting .mts video to other formats?

I've tried m2toavi but I couldnt manage the terminal good enough, so I'm looking for a graphical alternative.
Also, VLC does transcode these files but their original resolution is somehow lost.

many thanks.

---

### Post by cotcot on 2009-12-16
Try [[COLOR="Red"]Handbrake[/COLOR]]("http://handbrake.fr/").

---

### Post by Criminel on 2009-12-17
Tried  Handbrake.
Message when trying to install:
"Dependency is not satisfiable : libdbus-glib-1-2"

After apt-get install libdbus-glib-1-2: libdbus-glib-1-2 is already in its most recent version.

Any ideas?

---

### Post by FakeOutdoorsman on 2009-12-18
> **Criminel said:**
> Tried  Handbrake.
Message when trying to install:
"Dependency is not satisfiable : libdbus-glib-1-2"

After apt-get install libdbus-glib-1-2: libdbus-glib-1-2 is already in its most recent version.

Any ideas?

I have two ideas that may not be correct.  What version of Ubuntu are you using?  The package file for Handbrake that you downloaded is for Ubuntu 9.10.  If you're using something older it may not work.

Do you have any third-party repositories or PPAs enabled?  Show the output of your */etc/apt/sources.list* file.  Also list any files that are located in */etc/apt/sources.list.d/*.

Also, what format would you like these MTS files to be converted to?

---

### Post by cotcot on 2009-12-18
I compiled handbrake meself (version HandBrake svn2289) on 9.04.
Maybe one of [[COLOR="Red"]these[/COLOR]]("http://rsync.labby.co.uk/index.php?dir=getdeb/ubuntu/jaunty/ha/") work.

---

### Post by cotcot on 2009-12-19
I found back how I compiled Handbrake. See [[COLOR="Red"]here[/COLOR]]("http://filthypants.blogspot.com/2009/03/new-directions-for-building-handbrake.html").

---

### Post by JohnAStebbins on 2009-12-20
> **cotcot said:**
> I found back how I compiled Handbrake. See [[COLOR="Red"]here[/COLOR]]("http://filthypants.blogspot.com/2009/03/new-directions-for-building-handbrake.html").

Or you could follow the official directions on HandBrake's wiki
[Compiling HandBrake on Linux]("http://trac.handbrake.fr/wiki/CompileOnLinux")

---

### Post by LuisGMarine on 2009-12-20
+ 1 for handbrake.  

I don't get why you might be experiencing problems, I just downloaded the 64-bit deb for my computer and all is smooth.

---

### Post by Criminel on 2009-12-23
I'm using Ubuntu 8.04 LTS, that may explain my problems.

Pavtube MTS Converter is not open source, so it's out of the picture.

I'll try Handbrake soon and let you know.

Thanks, you all.

---

### Post by FakeOutdoorsman on 2009-12-23
> **hatetea58 said:**
> im using Pavtube MTS Converter, u can have a try, hope it helps u

You keep posting about Pavtube.  Why?  I am guessing you are shill for this software.  It is Windows only, not free, and violates the [GPL](http://www.gnu.org/licenses/gpl.html) because it uses FFmpeg, LAME, and xvid without giving credit and does not provide the source code.

---

### Post by skibster on 2010-01-29
hey guys don't mean to double up on this but will blender support .mts or no?

---

### Post by LuridCinema on 2010-01-29
ffmpeg will do it, be sure and use the -sameq option and experiment, experiment and log your settings. I found Handbrake rendered lower quality video, however I did not experiment too much.

---

