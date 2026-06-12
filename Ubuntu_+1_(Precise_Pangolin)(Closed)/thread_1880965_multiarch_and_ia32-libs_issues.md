---
title: "multiarch and ia32-libs issues"
date: 2011-11-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by doctordruidphd on 2011-11-14
This is an upgraded 64-bit system from oneiric. The multiarch file is set up in /etc/dpkg.

I notice that while doing dist-upgrade, ia32-libs is being held back. Trying to **apt-get install --reinstall ia32-libs** produces the following:

```
The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch but it is not installable
E: Unable to correct problems, you have held broken packages.
```

OK, so trying ia32-libs-multiarch (which is evidently the metapackage that pulls in the :i386 packages):

```
$ sudo apt-get install ia32-libs-multiarch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: gstreamer0.10-plugins-base:i386 but it is not going to be installed
                            Depends: gstreamer0.10-plugins-good:i386 but it is not going to be installed
                            Depends: gstreamer0.10-fluendo-mp3:i386 but it is not going to be installed
                            Depends: gvfs:i386 but it is not going to be installed
                            Depends: ibus-gtk:i386 but it is not going to be installed
                            Depends: libao4:i386 but it is not going to be installed
                            Depends: libcanberra-gtk-module:i386 but it is not going to be installed
                            Depends: libcap2:i386 but it is not going to be installed
                            Depends: libesd0:i386 but it is not going to be installed
                            Depends: libglapi-mesa:i386 but it is not going to be installed
                            Depends: libglu1-mesa:i386 but it is not going to be installed
                            Depends: libgphoto2-2:i386 but it is not going to be installed
                            Depends: libgphoto2-port0:i386 but it is not going to be installed
                            Depends: libmpg123-0:i386 but it is not going to be installed
                            Depends: libqt4-opengl:i386 but it is not going to be installed
                            Depends: libqtwebkit4:i386 but it is not going to be installed
                            Depends: libsane:i386 but it is not going to be installed
                            Depends: libsdl-mixer1.2:i386 but it is not going to be installed
                            Depends: libpam-winbind:i386 but it is not going to be installed
                            Recommends: libgl1-mesa-glx:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Trying to install most of those packages threatens to remove most of the system.

---

### Post by lonniehenry on 2011-11-14
I'm seeing this with a new install.  Waiting for updates.

---

### Post by nicx76 on 2011-11-15
I have the same problem with a fresh installation, waiting for an update:


root@server:~# apt-get install ia32-libs-multiarch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: bluez-alsa:i386 but it is not going to be installed
                            Depends: gstreamer0.10-plugins-good:i386 but it is not going to be installed
                            Depends: gvfs:i386 but it is not going to be installed
                            Depends: libcap2:i386 but it is not going to be installed
                            Depends: libgphoto2-2:i386 but it is not going to be installed
                            Depends: libsane:i386 but it is not going to be installed
                            Depends: libxss1:i386 but it is not going to be installed
                            Depends: libpam-winbind:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
root@server:~# 


regards,
nicx...

---

### Post by epvipas on 2011-11-15
Same problem here. Tried to fix it and lots of :1386 packages were removed along with wine1.3. I can't seem to get wine back on now though due to a long list of failed dependencies including ia32-libs as above. Hopefully time will fix this as more things get built.

---

### Post by lkjoel on 2011-11-15
Same problem here.

---

### Post by tghe-retford on 2011-11-15
Since toward the end of Oneiric development, this problem has been apparent. And yes, I have the same dependency problems as well from a fresh install. The joys of using a development version of Ubuntu and its derivatives.

---

### Post by doctordruidphd on 2011-11-15
Thanks to all who have responded; looks like a general problem. 

Also watch out for today's (15 Nov) updates -- the perl update will remove most of your system if you inadvertently dist-upgrade. Another one to sleep on for a few days.

---

### Post by Sworddragon on 2011-11-15
Just a quote from me:

> **Sworddragon said:**
> This behaviour in ia32-libs is wanted: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/879091](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/879091)

---

### Post by epvipas on 2011-11-19
I know I shouldn't be unhappy as this is a very early alpha and not for production machines. Having said that I'm a former gentoo user and enjoy the challenge of fixing breakages. 

I'm stumped at this though and I could really do with being able to get wine reinstalled. Anyone managed and if so how?

---

### Post by thatguruguy on 2011-11-19
> **epvipas said:**
> I know I shouldn't be unhappy as this is a very early alpha and not for production machines. Having said that I'm a former gentoo user and enjoy the challenge of fixing breakages. 
 Actually, it's not even an alpha yet.
> **epvipas said:**
> I'm stumped at this though and I could really do with being able to get wine reinstalled. Anyone managed and if so how?

I'm gonna go out on a limb here and assume you didn't read the bug report.

If you had, you would have seen the following comment:
> As indicated in the changelog, this is deliberate.  ia32-libs will be  installable again when all of the libraries it previously shipped have  been converted for multiarch.You also would have noticed that the status of the bug is marked "Won't fix"

You have several different available choices:

[LIST]
[*]You can use something other than a pre-alpha as your primary OS.
[*]You can install ia32-libs from a different repository.
[*]You can run the 32-bit version of Precise.
[*]You can wait for the conversion of the libraries to multiarch.
[/LIST]

---

### Post by effenberg0x0 on 2011-11-19
I am now looking at two fully updated machines 64-Bit PCs (Oneiric and PP). ia32-libs is installed and working. You will have problems if you force the installation of ia32-libs.

Use apt/aptitude options to simulate an upgrade. It will become evident to you that it will break the system if you force an update.

You can use this tools to establish what libs are holding the upgrade of ia32-libs and recompile them from source. But it's too much effort for something that will be fixed soon.

---

### Post by doctordruidphd on 2011-11-19
Apparently the package that replaces ia32-libs is ia21-libs-multiarch, a metapackage that drags in all the :i386 packages that were in is32-libs.  Doing the following:

sudo apt-get --dry-run install ia32-libs-multiarch

produces a list of dependencies that are "not going to be installed".  Attempting to install them (with the above --dry-run there as a safeguard) shows why -- it will remove X, and everything that depends on it.

I did not remove ia32-libs, and wine is running just fine. So, as already said, it may just be a matter of waiting until the new i386s are built.  It might be possible to install the ia32-libs package from oneiric, but who knows that that might break.

---

### Post by ranch hand on 2011-11-19
I have never used wine myself, don't allow MS products in the house.

There is always a thread like this in testing.  It takes a while for wine to catch up with the new dev release.

Don't panic.  Seems to work out in the end.

---

### Post by effenberg0x0 on 2011-11-19
@ [doctordruidphd]("http://ubuntuforums.org/member.php?u=740768") Are you a gamer?

Looking at Wine HQ page (haven't been there in last 6 months or more), it seems like it's entirely geared toward games now. Real applications one might consider the need to use, like MS-Office, do not run better now than they did 4 years ago. I had faith in this project as a potential substitute for MS-Windows in many machines. Many people, companies, etc just buy Windows cause they need to run MS-Office. No one buys and install Windows to use Paint and Notepad, but to run Win32 Apps. Wine could change the market. We'd be talking about cheaper PCs (no windows) sold to people, schools, companies, capable of doing the exact same stuff. Also the possibility of linking to winelib sounded very cool. But none of that is close to happening at all.

It seems that reproducing Win32API libs functioning using standard C and Linux libs is just harder than everyone thought it would be. And, weirdly, implementing DirectX support is more possible and advances reasonably faster.

---

### Post by doctordruidphd on 2011-11-19
> @ doctordruidphd Are you a gamer?

formerly, gave up when (1) I couldn't get witcher2 to run with wine nohow (even following all the advice of those who did get it to work) and (2) games have just gotten too hard. Too many of them sitting on the shelf unfinished. So I don't waste any more of my money (on that, at least).

You're right, wine is almost entirely geared toward games, because that is what the community uses it for.  Code Weavers (as I understand it, the actual source of the wine project) is more geared toward MSOffice and other office applications.  It's a pay-for commercial project, with support, etc., and my understanding is it works quite well. Cheaper than windows, especially considering the cost of virus software, etc. I don't use it, Libreoffice and Gimp handle everything I want to do in that respect.

What I use wine for at this point: Garmin Mapsource for my gps unit, and that's about it. What I would like to use it for is uploading and downloading to several radio scanners I have, but alas usb connectivity is just about nonexistent. Have to resort to windows in virtualbox for that. So I don't know at this point if I will even be pursuing it further.

---

### Post by 3vi1 on 2011-12-03
I just ran into this same problem when I rebuilt my system today.

I got around it by grabbing the following packages from Oneiric and installing them (a few of these will need --force-depends to sidestep some dependencies on old versions).  After that, you need to apt-get upgrade to get some of them up to the current version so that the wine1.3 package dependencies work.

```

ia32-libs_20090808ubuntu26_amd64.deb
lib32asound2_1.0.24.1-0ubuntu10_amd64.deb
lib32bz2-1.0_1.0.5-6ubuntu1_amd64.deb
lib32ffi6_3.0.11~rc1-2_amd64.deb
lib32gcc1_4.6.1-9ubuntu3_amd64.deb
lib32ncurses5_5.9-1ubuntu5_amd64.deb
lib32ncursesw5_5.9-1ubuntu5_amd64.deb
lib32stdc++6_4.6.1-9ubuntu3_amd64.deb
lib32tinfo5_5.9-1ubuntu5_amd64.deb
lib32z1_1.2.3.4.dfsg-3ubuntu3_amd64.deb
libc6-i386_2.13-20ubuntu5_amd64.deb
lsb-release_4.0-0ubuntu16_all.deb
```

This appears to work fine (launched a couple of 3D games).

The only real problem I can see right now that the system seems to fight over who has sound.  I.e.  You can't run a 64 bit app and a 32 bit app and get sound from both.  The first to run locks the sound devices to that architecture.  This caveat is exactly as it has been for anyone who upgraded from Oneiric to Precise though - it's not caused by my workaround.  

So now, everything's fine - unless you want to run native Teamspeak while playing a game.  Hopefully, this will be worked out when the real multiarch packages hit.

Oh yeah - you can download the packages at [http://packages.ubuntu.com/oneiric/ia32-libs](http://packages.ubuntu.com/oneiric/ia32-libs).  Reading back over the older posts, this is basically the second solution Thatguruguy suggested.

---

### Post by sparker256 on 2011-12-03
So is there any time table as to when all this will be fixed? I want to only run 64bit and until this is fixed I cannot run X-Plane in 64bit.

Thanks Bill

---

### Post by jfernyhough on 2011-12-03
--edit
nm

---

### Post by psypher on 2011-12-20
Hope this gets fixed soon. Cannot install skype as well due to this

---

### Post by thedarkdonut on 2011-12-23
I ran into the same problem today.  My system isn't a clean install, but it was also an upgrade from oneiric to precise.  I wouldn't have known if I wasn't trying to install skype.  Received about the same error from both the terminal and synaptic.

---

### Post by nutznboltz on 2012-01-30
The [sun-java6 script]("http://blog.flexion.org/2012/01/16/install-sun-java-6-jre-jdk-from-deb-packages/") fails on 12.04 because ia32-libs-multiarch can't be installed.

Updated: I tried again and the ia32-libs-multiarch package can be installed.  It pulls in a lot of packages but that is OK.


[http://wiki.debian.org/Multiarch](http://wiki.debian.org/Multiarch)

[http://askubuntu.com/questions/49674/what-is-the-status-of-multiarch-for-11-10](http://askubuntu.com/questions/49674/what-is-the-status-of-multiarch-for-11-10)

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-o-multiarch-next-steps](https://blueprints.launchpad.net/ubuntu/+spec/foundations-o-multiarch-next-steps)

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-lts-upgrades](https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-lts-upgrades)

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-64bit-by-default](https://blueprints.launchpad.net/ubuntu/+spec/foundations-p-64bit-by-default)

---

