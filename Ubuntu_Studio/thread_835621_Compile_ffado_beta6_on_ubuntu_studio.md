---
title: "Compile ffado beta6 on ubuntu studio"
date: 2008-06-20
forum: Ubuntu Studio
---

### Post by ecullerton on 2008-06-20
Has any body compiled the latest version of ffado (beta6) in ubuntu studio?

I have 2 Focusrite Saffire pro 10's and I really want to try out the new software mixers that are available.

Thanks, Ed

---

### Post by Stochastic on 2008-06-21
Compiling ffado won't hurt your freebob install, but it will force you to compile Jack from source (so I guess that could hurt things if something goes wrong at that stage).  Give it a try and post back with any issues you have; I'd be happy to help troubleshoot.

---

### Post by wurdien on 2008-06-21
I installed ffado to my Ubuntu Studio a week ago. I had some problems on installation, but the driver itself works well.

First, get the package, extract it and run "$ scons -h PREFIX=/your/prefix". It will tell you if you are missing some packages. Install them (dev packages too). Also, make sure that you have asound library and automake, autoconf and libtool.

Commands to build and install are:
```
scons -h PREFIX=/prefix
scons
sudo scons install
```

Ffado probably fails to install to /usr. If you install it to /usr/local it says that some files aren't found when running test program. Go around this problem by setting prefix to your home directory and manually copying files to correct locations.

Then you need to compile jack from source. The newest release 0.109.2 is too old, so you must use svn version. Remember to set tmpdir correctly. If I remember right, there were no problems with installing jack.

One question about jack installation, which answer I don't know, is when there comes new version of jackd to package manager, it will probably overwrite the jack installation I made myself. Question is , how can I prevent this from happening?

---

### Post by Stochastic on 2008-06-21
> **wurdien said:**
> One question about jack installation, which answer I don't know, is when there comes new version of jackd to package manager, it will probably overwrite the jack installation I made myself. Question is , how can I prevent this from happening?

There are a number of different ways, depeding on the package-manager of your choice (read the man page accordingly).  The simplest thing would be to read through your updates to make sure there are no jackd or qjackctl packages.  The good news is that an update of jackd or qjackctl is extremely unlikely unless its a major bugfix (I'm not aware of any bugs that need fixing in those packages) or security issue (a type of bugfix).  Chances are you won't see a new jack/qjackctl version hit the repos until Intrepid's release (it may not even happen then).

I'm about to give ffado a go on my own system... I'll report back with my issues/successes.

---

### Post by Stochastic on 2008-06-26
Hmm, libffado built for me with no problems.  Test program executed nicely.

But when I got jack from svn, there was instructions (QUICK-INSTALL file) to edit kernel options, rebuild kernel, install new kernel library (which failed to build properly on my sytem), and configure when there is no executable ./configure file included.

I'd like to know how to get this done, and if recompiling kernels is really needed.  Anyone?

---

### Post by wurdien on 2008-06-26
I read that quick install file, and noticed that it was written for 2.4 series kernel. I don't know if same changes should be done for 2.6 kernels. I didn't but jack still installed fine.

Myself I followed instructions from ffado's wiki to install jack. [http://subversion.ffado.org/wiki/JackForTrunk](http://subversion.ffado.org/wiki/JackForTrunk)

I still have some problems with my fp10; Sometimes I am not able to get any audio out. Now it works fine, but if (=when) I am able to reproduce that problem I will post some more details about it. (Haven't found out if this also happens with PCI-soundcard and alsa)

---

### Post by Stochastic on 2008-06-26
Yup, that did it, no recompile needed.  The drivers seem a bit shaky on my firepod, but I haven't done too many tests yet.  I ignored your earlier suggestion of installing libffado into the home folder then copying manually to the appropriate spot, and everything works fine, so I'm not sure what issues you were trying to avoid.

---

### Post by ecullerton on 2008-06-26
Hi again,

Thanks for the responses, I've been plugging away at this for a while and haven't had any luck yet. I tried following your suggestion of using my home directory as a PREFIX, and things started working, but I can't get it to build the mixer.  I get this response...

scons: Reading SConscript files ...
Checking for a working C-compiler (cached) yes
Checking for a working C++-compiler (cached) yes
Checking for C header file expat.h... (cached) yes
Checking for XML_ExpatVersion() in C library expat... (cached) yes
Checking for pkg-config (at least version 0.0.0)... (cached) yes
Checking for libraw1394 (1.3.0 or higher)... 	(cached) yes
Checking for libavc1394 (0.5.3 or higher)... 	(cached) yes
Checking for libxml++-2.6 (2.13.0 or higher)... 	(cached) yes
Checking for dbus-1 (1.0 or higher)... 	(cached) yes
Checking for libiec61883 (1.1.0 or higher)... 	(cached) yes
Checking for lrint(3.2) in C library m... (cached) yes
Checking for lrintf(3.2) in C library m... (cached) yes
Checking whether 'which pyuic' executes (cached) no

	I couldn't find all the prerequisites ('pyuic' and the python-modules 'dbus' and
	'qt', the packages could be named like dbus-python and PyQt) to build the mixer.
	Therefor the mixer won't get installed.



I've installed every package I could find related to qt, pyqt, dbus-python, and sip, but sill no luck.  Here is a list of the packages I installed.  As you can see, I was getting desperate.

qt4-designer
qt4-dev-tools
sip4
python-qt4
python-qt4-dbus
python-qt4-dev
pyqt-tools
pyqt-dev-tools
libdbus-qt-1-1c2
libdbus-qt-1-dev
python-qt4-dbus-dbg
python-qt-dv
libqt4-debug
qt4-qtconfig
python-qt4-dbg

Many other packages were installed along with the above that I checked off, but I didn't note them down.

Can anyone see what I am missing?

Thanks again for your help.

Ed

---

### Post by thorgal on 2008-06-27
i don't think you need the -dbg packages. These are the debug packages which contain the same thing as the non debug ones but with debug symbols (non stripped binaries, if you know a bit about software development).

---

### Post by wurdien on 2008-06-27
See [this]("http://ffado.org/?q=node/613") tutorial from ffado's site. There's instructions how to go around that problem.

EDIT: [This tutorial](https://help.ubuntu.com/community/UbuntuStudio/Record_Now_with_FireWire) tells to use jdelay to measure latency and then manually align audio tracks. However, when I record tracks seem to be aligned correctly automatically. Do you know if that thing has already been fixed and that guide is just outdated?

---

### Post by Stochastic on 2008-06-27
> **wurdien said:**
> EDIT: [This tutorial](https://help.ubuntu.com/community/UbuntuStudio/Record_Now_with_FireWire) tells to use jdelay to measure latency and then manually align audio tracks. However, when I record tracks seem to be aligned correctly automatically. Do you know if that thing has already been fixed and that guide is just outdated?

That tutorial is about a year old (though it has been updated recently as part of the [June Documentation Month]("http://ubuntuforums.org/showthread.php?t=814808") push - edit: nevermind those recent edits were just altering the markup), but jdelay is still a useful tool.  Your tracks may seem aligned, but with a high-end audio card the delay/latency you experience is so small (<~5ms) that it can be off sync and your ear won't even hear it.  If memory serves correct, the human ear can percieve about 7ms-10ms latency, but sometimes it can unconsciously ignore latencies (the percussion section of an orchestra is usually about 10ms, in distance, behind the violins).  Try a loopback recording test (where you play a track out of one of ardour's channels, then record it onto another channel; zoom in nice and close (it's best if there are some sharp clicks or pops in the recording) and see how much difference there is (note: on a round trip out AND back in, there will actually be twice the latency as a one-way trip).

On another note, I didn't bother building the ffado mixer, is there anything terribly useful in it?  Anyone know where a screenshot would be (particularly interested in the firepod/fp10 features).

---

### Post by wurdien on 2008-06-28
I did that test and it seems like tracks would get correctly aligned automatically. I increased latency to 400ms so if the tracks weren't in sync I would hear that. Also, I used jdelay to measure the latency and then moved another track forward as much as jdelay told to, and I was able to hear that tracks weren't synced. So, this thing seems to be fixed.

As far as I know, there is no mixer for fp10 (there weren't one even in windows, if I remember right). Once I had the mixer installed, and when started it just told that my card was FP10.

---

### Post by jimei on 2008-06-28
[Dunk SB]("http://www.gucci-sneaker.com/catalog_39.html")
[Air force one]("http://www.gucci-sneaker.com/catalog_42.html")

---

### Post by Stochastic on 2008-06-28
Is this auto-alignment in ardour?  It may not be the same for every DAW.

---

### Post by JJoel on 2008-10-05
I'd like to compile the ffado driver. However, I already have a working freebob jack, which is part of the ubuntu-studio package. I can't remove the jackd package with out removing all the studio packages. Do I need to remove jack before I recompile it, or will it overwrite the existing packge and not cause any problems?

---

