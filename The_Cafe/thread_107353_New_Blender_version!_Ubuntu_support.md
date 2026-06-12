---
title: "New Blender version! Ubuntu support?"
date: 2005-12-22
forum: The Cafe
---

### Post by OneSeventeen on 2005-12-22
I'm using blender on my ubuntu laptop now, and just thought I'd bring it to everyone else's attention that version 2.40 is out
(version 2.37a is what ubuntu installs)

Hope to see version 2.40 in the repositories sometime, but either way, head over to [http://www.blender3d.org](http://www.blender3d.org) to check out what's new!

---

### Post by Statik on 2005-12-23
Eagerly awaiting this as well!

Statik

---

### Post by DirtDawg on 2005-12-23
Blender is the type of app that you can just unzip and use.

Simply download the Linux distribution you need, "untar" it, or whatever the slang is, in whichever directory you would like Blender housed, and run it! 
Easy easy.
Thanks for the heads up, btw. I looooooove Blender and new releases make me a happy man.

---

### Post by commodore on 2005-12-24
But how do update my previous Blender verison? I still want to install it not just unpack it.

---

### Post by DirtDawg on 2005-12-24
Unpacking Blender installs Blender, unless I'm [missing something.]("http://download.blender.org/documentation/html/chapter_installation.html")

---

### Post by asimon on 2005-12-24
Yes, unpacking is enough to run it. But of course we want a real deb package with a proper .desktop file, mime type registration, etc. :-)

---

### Post by commodore on 2005-12-25
Right asimon, that's what I meant.

---

### Post by DirtDawg on 2005-12-25
I see. I don't know what that means except that I've got more learning to do! Thanks for filling me in.

---

### Post by asimon on 2005-12-25
[QUOTE=DirtDawg]I see. I don't know what that means except that I've got more learning to do! Thanks for filling me in.[/QUOTE]
.desktop files reside under /usr/share/applications/ and are responsible that the application appears in Gnome's or KDE's applications menu. They contain the name under which the application appear in the menu and translations into different languages. They also define which icon to use for the application. The .desktop files also contain 'mime'-types, that associate the application with specific file types, i.e. they define for example that when you click on a blender 3d file in your file browser that the file should be opened with Blender.

---

### Post by eyce on 2005-12-27
Ssso... any news on the blender 2.4 package front?

I was told in another thread that 2.4 has to make it to the development build, and then we have to ask for a backtrace for the current Breezy build... that true for Blender also?

---

### Post by asimon on 2005-12-27
[QUOTE=eyce]Ssso... any news on the blender 2.4 package front?

I was told in another thread that 2.4 has to make it to the development build, and then we have to ask for a backtrace for the current Breezy build... that true for Blender also?[/QUOTE]

I think the usual way if the following: First Masayuki Hatta, the Debian maintainer for Blender, packages the new version and puts it into Debian unstable. From there it will then be fetched, rebuild, and included in Dapper. Then the backport team takes the dapper package and backport it ... ;-)

As far as I know the Ubuntu Backport projects only backports packages which are already in the current development version of Ubuntu, i.e. currently Dapper.

---

### Post by eyce on 2005-12-29
Thanks for the heads up asimon (asimov? :D) ... had a question on that tho..

So what you're saying is - if Blender 2.4 is not a part of Dapper, we're better off adding the appropriate debian url to our sources.list, rather than hoping against all hopes to see it in ubuntu in the near future? Still confused I s'pose..

---

### Post by commodore on 2005-12-29
So Blender is coming in so late that I have to use Windows?

---

### Post by asimon on 2005-12-29
> **eyce]Thanks for the heads up asimon (asimov? :D)
[/quote]
No, just my surname prefixed with the first letter of my forename.  said:**
> 
So what you're saying is - if Blender 2.4 is not a part of Dapper, we're better off adding the appropriate debian url to our sources.list, rather than hoping against all hopes to see it in ubuntu in the near future? Still confused I s'pose..
It's possible that the Debian package works under Ubuntu too, I haven't tested it. But it can break, Ubuntu is not build to be compatible with Debian. Usually people warn you to add Debian repositories to your sources.list as that can go very wrong.

I think it's best -- as it was mentioned above -- to just download the prebuild package from [Bender3d.prg](blhttp://blender.org/cms/Blender.31.0.html), unpack it somewhere and run it from there. With this way it won't appear in your application menu automatically (the old version from the ubuntu package will still be there if you have it installed) but it works. If you download the tarball from blender3d.org use the "Linux i386 2.3.2, static, Python 2.4 (7.2 MB)" version. That one seems to work fine, with the dynamic version I got some graphic distortions in the menus.

I am sure that Blender 2.40 will find it's way into Ubuntu, but it will probably take some time. Remember that between Christmas and New Year many people (including Ubuntu and Debian maintainers) have some days off.

---

### Post by commodore on 2005-12-29
But where are apps installed in Linux/UNIX? Can't I overwrite the old files with the newly downloaded files?

---

### Post by tlc on 2005-12-29
You can install stuff wherever you want. Personally I stick apps in /home/apps as there's no other users on this PC. Otherwise I stick them in /opt because I don't know what else the hell /opt is for. It works for me... ;) Afterwards I just create a launcher on my desktop or taskbar, enter the path, and forget about it.

---

### Post by asimon on 2005-12-30
BTW, if you need more detailed steps about installing Blender see the [Blender Installation Instructions](http://download.blender.org/documentation/html/chapter_installation.html), there is also described how to create program icons for Blender under KDE and Gnome.

Regarding the question where are apps are installed in Linux/UNIX? That depends. There is the [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/) which Ubuntu follows. To see where the files of a package are installed you can run 'dpkg -L <packagename>' on the command line, i.e. 'dpkg -L firefox' or under Synaptic choose "Properties" in the right-mouse-button-menu of an installed package. (You can see this in Adept too, but I am not familiar with that one). This only works for packages which are already installed. To see where the files of a single .deb package are going to be installed you can use 'dpkg-deb -c <.deb file>'.

And for apps like Blender where you don't need a complicated setup after installation and which doesn't integrate deeply into the desktop you can install it in principle everywhere you want, like for example somewhere in your home directory.

It's not recommended to overwrite files which are installed through debian packages on your system. That can cause (among others) problems if you later update the package. To install non-packaged software (i.e. which doesn't come from your distribution) most proeple use either /usr/local/ or /opt/<packagename>/. Or if it's for only one user the home dir.

---

### Post by vtrandal on 2006-01-07
Hello,

I am new to Ubuntu after using various other Linux Distrubutions.  Here's my initial installation experience of Ubuntu 5.10 the Breezy Badger CD.

1. No network adapter.  It was there during installation, but not afterwards. Tried using USB Wifi adapter, but still no adapter shown via ifconfig or iwconfig.
2. Cannot untar blender.tar ([http://www.blender.org)](http://www.blender.org)).  Says I don't have right permissions???  Tried "sudo passwd root".  I was able to untar blender.tar, but running blender results in error due to missing shared library libstdc++.so.5.

Is there a more complete installation of Ubuntu that comes with more drivers and libraries so I can use it?  The 5.10 CD is just the beginning right?

Vincent Randal
Longmont, CO

---

### Post by poofyhairguy on 2006-01-07
[QUOTE=vtrandal]Hello,

I am new to Ubuntu after using various other Linux Distrubutions.  Here's my initial installation experience of Ubuntu 5.10 the Breezy Badger CD.

1. No network adapter.  It was there during installation, but not afterwards. Tried using USB Wifi adapter, but still no adapter shown via ifconfig or iwconfig.[/QUOTE]

Not all hardware works unfortunatly.

> 
2. Cannot untar blender.tar ([http://www.blender.org)](http://www.blender.org)).  Says I don't have right permissions???  Tried "sudo passwd root".  I was able to untar blender.tar, but running blender results in error due to missing shared library libstdc++.so.5.

Hmm...seems to be a dependancy problem. That is usually solved by nerdily installing that needed lib.

> 
Is there a more complete installation of Ubuntu that comes with more drivers and libraries so I can use it?  The 5.10 CD is just the beginning right?


Kinda. There is more drivers and libraries on the internet...but I don't think that will fix your networking problem.

---

### Post by asimon on 2006-01-08
[QUOTE=vtrandal]but running blender results in error due to missing shared library libstdc++.so.5.[/QUOTE]

This library is part of the package "libstdc++5".

---

### Post by kxs on 2006-01-11
[QUOTE=DirtDawg]Blender is the type of app that you can just unzip and use.[/QUOTE]

And I think then, that what we need more is the latest yafray package. Especially when yafray.0.0.8 is now 6 months old :???:

---

