---
title: "Autopackage"
date: 2004-12-29
forum: The Cafe
---

### Post by TravisNewman on 2004-12-29
I know this is getting old. People are talking about ways to simplify ubuntu's packaging left and right. I'm joining in :) This would have to be patched to switch from root user to current user (sudo instead of su, basically), and to add itself to the apt database, but it would be really handy, since you can just double click it and install it. You can see how it works at the site:
[http://autopackage.org/](http://autopackage.org/)

---

### Post by mark on 2004-12-29
[QUOTE=panickedthumb]I know this is getting old. People are talking about ways to simplify ubuntu's packaging left and right. I'm joining in :) This would have to be patched to switch from root user to current user (sudo instead of su, basically), and to add itself to the apt database, but it would be really handy, since you can just double click it and install it. You can see how it works at the site:
[http://autopackage.org/](http://autopackage.org/)[/QUOTE] Anybody that can come up with a distro-neutral equivalent of, say, InstallShield for Linux would definitely get a "laurel... and hardy handshake" from me.  You should have heard me trying to explain Linux package differences to my brother....

---

### Post by poofyhairguy on 2004-12-29
[QUOTE=mark]Anybody that can come up with a distro-neutral equivalent of, say, InstallShield for Linux would definitely get a "laurel... and hardy handshake" from me.  You should have heard me trying to explain Linux package differences to my brother....[/QUOTE]

This is the one issue where Linux fails on the desktop.

---

### Post by regeya on 2004-12-30
[QUOTE=poofyhairguy]This is the one issue where Linux fails on the desktop.[/QUOTE]

On the other hand, I can see something like Autopackage turning into a mess like Windows, if one were to carry Autopackage to its (perhaps not so) illogical end.  Can you imagine someone downloading and installing GNOME packages from various sites, each one depending on, say, different  minor versions of libgtk? *shudder*  8-[

On the other hand, as environments and applications get more complex, it's getting a bit tedious to keep trying to figure out why Distribution Brand X has a perfectly working Widget program while Distribution Brand Y gets constant segfaults.  I'm sure we've all run into some jokers at some point that think that Application X sucks, and nearly everyone who uses Distribution X thinks the app sucks as well, while Distribution Y users think that Application X is the bee's knees.   :D 

It's a complex issue without a clear answer, IMHO.  For the record, I just installed the Visual Dependency Walker from their website, and I'm suitably impressed so far.  Maybe it's not quite Joe Sixpack-friendly yet, but it'll get there eventually.  I wonder how long it'll be before we see someone trying to build a distribution based on this packaging model, and if we'll want it when it's done.

I've always been a fan of the appdir model, myself, and one could add things like static binaries, bundled dependencies, etc. using that model.  The real problem is that your environment has to support that, and a number of other issues that can pop up such as upgrades.

---

### Post by ZakZak on 2005-01-02
Okay, GAIM v1.1.1 was just released and they made an autopackage available.  I thought great!  Maybe I can have a more recent GAIM on my Warty machine!  It doesn't work, though.  Autopackage prompts for the root password and when I provide the usual sudo password, it won't accept it.  Is this going to require a special Ubuntu-specific version of autopackage or something?

Anyhow, I'm going to just start up a root terminal and try to install the GAIM autopackage from there and see what happens.

-Zak

-- update --

It still fails with "Error: Could not find 'GNU Transport Layer Security'. Try using the native package manager for Ubuntu (apt-get) to install a package with similar name to 'gnutls'."

I DO have gnutls-bin, libgnutls7, libgnutls10, and libgnutls10-dev all installed...  Aparently autopackage either isn't smart enough to find it or I need a newer version or something.  <shrug>

Autopackage isn't impressing me so far... :)

---

### Post by CowPie on 2005-01-02
[QUOTE=ZakZak]Okay, GAIM v1.1.1 was just released and they made an autopackage available.  I thought great!  Maybe I can have a more recent GAIM on my Warty machine!  It doesn't work, though.  Autopackage prompts for the root password and when I provide the usual sudo password, it won't accept it.  Is this going to require a special Ubuntu-specific version of autopackage or something?

Anyhow, I'm going to just start up a root terminal and try to install the GAIM autopackage from there and see what happens.

-Zak

-- update --

It still fails with "Error: Could not find 'GNU Transport Layer Security'. Try using the native package manager for Ubuntu (apt-get) to install a package with similar name to 'gnutls'."

I DO have gnutls-bin, libgnutls7, libgnutls10, and libgnutls10-dev all installed...  Aparently autopackage either isn't smart enough to find it or I need a newer version or something.  <shrug>

Autopackage isn't impressing me so far... :)[/QUOTE]
 Email the author :)  Mike Hearn is very responsive, post in forum

---

### Post by jdong on 2005-01-02
Exactly what's wrong with dpkg and apt? Just extend Synaptic to support installing standalone debs while grabbing dependencies from APT respositories, then do a few MIME associations, and voila, double-click installations.

---

### Post by ZakZak on 2005-01-03
[QUOTE=jdong]Exactly what's wrong with dpkg and apt? Just extend Synaptic to support installing standalone debs while grabbing dependencies from APT respositories, then do a few MIME associations, and voila, double-click installations.[/QUOTE]

I personally have no problem with apt except that you have to wait for someone to produce an updated package when a new version of the software comes out (the GAIM folks do RPMs but not DEBs).  Their autopackage download has the promise of allowing me to immediately install the new version as soon as they release it.

---

### Post by jdong on 2005-01-03
You can always convert from RPM to deb using alien. That's a huge flexibility plus with  Debian.

Besides, you'd really want to: 
1. Compile it yourself from source.
or
2. Download a version compiled specificly for your distro and version.

Because there may be specific library versions that the package is compiled for.

---

### Post by thtde on 2005-01-03
[QUOTE=jdong]You can always convert from RPM to deb using alien. That's a huge flexibility plus with  Debian.[/quote]

But there may be incompatibilities with Ubuntu.

[QUOTE=jdong]1. Compile it yourself from source.[/quote]

This isn't an option for a newbie.

[QUOTE=jdong]2. Download a version compiled specificly for your distro and version.

Because there may be specific library versions that the package is compiled for.[/QUOTE]

But if there isn't a package for your distro, this isn't possible. A big advantage of autopackage is that it is distro-neutral. It doesn't want to replace dpkg or rpm but wants to give developers the possibility to build a generic package for all distros which also a newbie can install.

---

### Post by jdong on 2005-01-03
No, autopackage is **NOT** distro-neutral. If I try to install a, say, K3b 0.11.18 Autopackage package on Debian Woody, it'll still fail because the correct versions of kde libs aren't available.

---

### Post by thtde on 2005-01-03
[QUOTE=jdong]No, autopackage is **NOT** distro-neutral. If I try to install a, say, K3b 0.11.18 Autopackage package on Debian Woody, it'll still fail because the correct versions of kde libs aren't available.[/QUOTE]

Autopackage has distro-neutrality as a goal but of course many important libraries has to be installed. It is not the goal of autopackage to package every basic lib, that's a task for the distro.

---

### Post by ZakZak on 2005-01-03
[QUOTE=thtde]This isn't an option for a newbie.[/QUOTE]

I don't really consider myself to be a newbie, but I did try to compile GAIM from source once and my head is still spinning...  I installed -dev package after -dev package until it finally DID compile, but it would crash when I tried to run it.  I gave up and rolled back to the warty package.

Since then, I've discovered jdong's backports repository and I'm now happily running GAIM 1.1.0 (which has the specific bugfix I needed).  The Changelog for 1.1.1 lists "More MSN bugfixes" which may be applicable to me (I use MSN a lot) or may not.  I can probably live without 1.1.1 until it shows up in backports, though.

-Zak

---

### Post by jdong on 2005-01-03
[QUOTE=thtde]Autopackage has distro-neutrality as a goal but of course many important libraries has to be installed. It is not the goal of autopackage to package every basic lib, that's a task for the distro.[/QUOTE]

That defeats the purpose of autopackage. Alien can handle conversion from package format to package format, most notably RPM, TGZ, DEB. All the other compatibility issues stem from problems with libraries.

---

### Post by mhearn on 2005-01-12
Hi,

I'm Mike, autopackage maintainer. Somebody pointed me to this thread.

Zak: yes that error message you got is hopelessly confusing, it means "either you do not have the library at all, or you don't have the version this package needs". This is fixed in CVS and the final 1.0 release will give a much better error message.

This doesn't solve your problem of course which is that GnuTLS broke backwards compatibility and now you have the wrong version. Tim (the Gaim developer who builds the autopackages) is very much aware of this problem, we have discussed it on the list, and he is planning on fixing it soon.

SSL in general causes such huge problems for Gaim users that they have an entire FAQ devoted to it, so this isn't really the fault of autopackage - Debian style apt repositories wallpaper over the problem of continuous paltform instability, they don't actually solve it.

The new 1.1.1 release of the Gaim autopackage has had about 2500 downloads and remarkably few issues have been found:

- gnutls if missing is not automatically resolved, because there are no gnutls autopackages and nobody has yet taught autopackage how to use apt (we really want this feature)

- if gnutls is present but of the wrong version, the error message given is crap and misleading: i fixed this a few days ago

- mozilla tries to download the package file as text from some mirrors, this is just the MIME system sucking however we now have a nice hack in there that forces Necko to treat it as binary so this problem will go away for autopackage 1.0

The issue of Ubuntu only using sudo is a major pain in the arse as it's very hard/impossible to provide a graphical frontend to it. So we may simply have to provide Ubuntu users with a worse user experience until either we figure out how to make the GUI su frontend work with sudo or Ubuntu is changed to allow su access (or sudo is modified upstream).

Please let us know if you have any other problems or opinions, this is as easy as joining #autopackage on freenode and stating your thoughts - I am connected to it all the time via dircproxy so I will see it.

thanks -mike

---

### Post by FooBarWidget on 2005-01-12
> That defeats the purpose of autopackage. Alien can handle conversion from package format to package format, most notably RPM, TGZ, DEB. All the other compatibility issues stem from problems with libraries.

I don't think you quite understand the problem.

Alien can change the package format - great. But what about dependancy names? Let's say there's an RPM for Fedora which require gnome-vfs. The specfile says it require gnome-vfs >= 2.0.0. But on your Debian-based distro, the gnome-vfs package is called libgnomevfs. Tadaa - the converted package doesn't work.
And there's the issue of glibc symbol problems. Have you ever seen "undefined symbol GLIBC_2.3 in /lib/libc.so" errors?
Furthermore, autopackage doesn't depend on a database for dependancy checking. It checks whether things are really there, ala autoconf.

autopackage is not just yet another package manager. We deal with a lot of the low-level problems. You should read the FAQ.

---

### Post by Dylanby on 2005-01-12
As a newcomer to Linux, I've run accross a few stumbling blocks when installing 3rd party packages.

Installing ET, RTCW, Doom3, or the UT2004 (updates) on an AMD64 caused a few
problems. I still can't get RTCW working. Doom 3 required a manual copy/paste /directory creation/postinstall-install.

The official & Loki packages both fall short in some areas.

I think this might be an area for autopackage to shine (& increase mindshare).

id, Epic & other commercial game companies could obviously use something more advanced than the standard *.bin files they distribute.

But then they don't "officially" support Linux so...

---

