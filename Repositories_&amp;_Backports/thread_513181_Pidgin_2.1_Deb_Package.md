---
title: "Pidgin 2.1 Deb Package"
date: 2007-07-30
forum: Repositories &amp; Backports
---

### Post by CheetahCat on 2007-07-30
Hello folks,

not yet announced on their website, Pidgin 2.1 is finally available.

[http://sourceforge.net/project/showfiles.php?group_id=235&package_id=230234&release_id=528380](http://sourceforge.net/project/showfiles.php?group_id=235&package_id=230234&release_id=528380)

Is there someone who could provide a deb package for this and place it on getdeb.net?

Thanks :)

Cheetah

---

### Post by aeon on 2007-07-30
compiling right now, i'll post a 64bit deb up there when it's done

---

### Post by misfitpierce on 2007-07-30
> **aeon said:**
> compiling right now, i'll post a 64bit deb up there when it's done

Would be much appreciated :)

and great news

---

### Post by Sewage on 2007-07-30
I installed from source and for some reason it seems like the spell check is not working~? I have installed form source the last few upgrades so I am not sure if it's just not there or it's a glitch.

---

### Post by aeon on 2007-07-30
There we go, i just put up the amd64 deb

get it here:

[http://people.arcada.fi/~andtbacm/debs/pidgin_2.1.0-1_amd64.deb]("http://people.arcada.fi/~andtbacm/debs/pidgin_2.1.0-1_amd64.deb")

Should be working without any glitches

---

### Post by Sewage on 2007-07-30
That doesn't really help me, I'll have to hang around and see if anyone else puts up a deb for none-amd64.

That or I am just missing it, which wouldn't surprise me.

---

### Post by Gremlinzzz on 2007-07-30
Think it made the list check it out
[http://incoming.debian.org/](http://incoming.debian.org/)
:guitar:

---

### Post by Sewage on 2007-07-30
Weird, also mine auto-aways me even when I am active. :S I some how messed this all up, didn't I?

---

### Post by walkerk on 2007-07-30
for those waiting on a .deb... compiling from source is simple.. really.

just dl the .tar.bz2

unpack it. in terminal move to the directroy and then:
```
./configure
```

it'll take a moment.. now make:
```
make
```

this will take awhile.. now make install:
```
sudo make install
```


now you've got 2.1 :)

you don't need to wait on a deb created by someone else (following the above basically...) do it yourself :D

---

### Post by aeon on 2007-07-30
> **Sewage said:**
> Weird, also mine auto-aways me even when I am active. :S I some how messed this all up, didn't I?

It's not a bug, it's a feature :D

---

### Post by Sewage on 2007-07-30
I think you misunderstand~

When I am sitting at my computer doing things, having conversations, etc~ It will put me on away for no particular reason.

I am certainly not away or idle though.

Also I just un-installed and recompiled it but I am still having that error as well as a lack of spell check. :\

---

### Post by GhentK on 2007-07-30
> **aeon said:**
> It's not a bug, it's a feature :DAnd a great one at that. :D

Does anyone know what to do to enable in-line spell checking?

---

### Post by limemonkey on 2007-07-31
**Update:** Try this first: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Pidgin_2.1.0_.28former_GAIM.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Pidgin_2.1.0_.28former_GAIM.29)

Use at own risk, packages check for no requirements, if you had pidgin before, it should work now too.

pidgin_2.1.0-1_i386.deb (7.64 MB)
	- [http://www.mediafire.com/?dtvyjkj2b3s](http://www.mediafire.com/?dtvyjkj2b3s)

purple-plugin-pack_2.0.0-1_i386.deb (183.63 KB)
	- [http://www.mediafire.com/?1de3sczkewy](http://www.mediafire.com/?1de3sczkewy)

pidgin-otr_3.0.0+cvs20070508.orig-1_i386.deb (45.64 KB)
	- [http://www.mediafire.com/?3dizhxg2ybv](http://www.mediafire.com/?3dizhxg2ybv)

pidgin-libnotify_0.13-1_i386.deb (123.64 KB)
	- [http://www.mediafire.com/?ataofzaosw2](http://www.mediafire.com/?ataofzaosw2)

```
pidgin 2.1.0

Build GTK+ 2.x UI............. : yes
Build console UI.............. : yes

Protocols to build dynamically : gg irc jabber msn novell oscar qq sametime simple yahoo zephyr
Protocols to link statically.. :

Build with GStreamer support.. : yes
Build with D-Bus support...... : yes
D-Bus services directory...... : /usr/local/share/dbus-1/services
Build with NetworkManager..... : yes
SSL Library/Libraries......... : Mozilla NSS and GnuTLS
Build with Cyrus SASL support. : no
Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Has you....................... : yes

Use XScreenSaver Extension.... : yes
Use X Session Management...... : yes
Use startup notification...... : yes
Build with GtkSpell support... : yes

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : yes
Build with Tcl support........ : yes
Build with Tk support......... : yes

Print debugging messages...... : no

Pidgin will be installed in /usr/local/bin.
```

---

### Post by CheetahCat on 2007-07-31
Yeah, obviously that is really simple.

This thing is just that I totally hate to have files flying around that my package manager does know nothig about. Those apps are deemed to break on the next system update and don't get updated automatically either.

Installing from source is really the last option for me. ;)



> **walkerk said:**
> for those waiting on a .deb... compiling from source is simple.. really.

just dl the .tar.bz2

unpack it. in terminal move to the directroy and then:
```
./configure
```

it'll take a moment.. now make:
```
make
```

this will take awhile.. now make install:
```
sudo make install
```


now you've got 2.1 :)

you don't need to wait on a deb created by someone else (following the above basically...) do it yourself :D

---

### Post by limemonkey on 2007-07-31
> **GhentK said:**
> Does anyone know what to do to enable in-line spell checking?

my guess would be: sudo apt-get install libgtkspell-dev

After running configure, you will get a summary of the settings, you should have a yes behind each feature you want to have, if not, mostlikely you miss the -dev package.

I used this for the package above:
./configure --prefix=/usr/local  --enable-nm


If anybody knows how to automatically add Depends with checkinstall, let me know... coz i don't really know what's required :-)

---

### Post by Gremlinzzz on 2007-07-31
Got pidgin installed was getting all kinds of errors that i didn't have this and that till i installed  gnome-devel.
These are the development tools of the GNOME Desktop environment, a
graphical interface to use on your Debian system. Included is everything
you need to create applications for GNOME, including IDE programs,
user interface creators and a tool to ease the translation of applications
to other languages.
worked and i installed pidgin from source.:guitar:

---

### Post by altonbr on 2007-07-31
> **walkerk said:**
> for those waiting on a .deb... compiling from source is simple.. really.

just dl the .tar.bz2

unpack it. in terminal move to the directroy and then:
```
./configure
```

it'll take a moment.. now make:
```
make
```

this will take awhile.. now make install:
```
sudo make install
```


now you've got 2.1 :)

you don't need to wait on a deb created by someone else (following the above basically...) do it yourself :D

I've had nothing but problems with that method AND this method: [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

CheckInstall and it's emcompassing .deb that it made seems to think that 2.0.2~getdeb is newer than 2.1.0 :S. Not cool.

So I removed the old Pidgin and installed the [http://incoming.debian.org](http://incoming.debian.org) files, and it works. Thanks for the URL!

Can we bug the guys at Pidgin to start compiling an official .deb?

---

### Post by walkerk on 2007-07-31
> **altonbr said:**
> I've had nothing but problems with that method AND this method: [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

CheckInstall and it's emcompassing .deb that it made seems to think that 2.0.2~getdeb is newer than 2.1.0 :S. Not cool.

So I removed the old Pidgin and installed the [http://incoming.debian.org](http://incoming.debian.org) files, and it works. Thanks for the URL!

Can we bug the guys at Pidgin to start compiling an official .deb?

I'm sure we could.. But its just as easy for one of us to package a deb and host it.. thats what getdeb.net is for right? I honestly don't know why the pidgin developers do no publish a deb.. I'm sure they have their reasons..

---

### Post by Gremlinzzz on 2007-07-31
First install gnome-devel because it helped with dependences
then downloaded source  
[http://pidgin.im/pidgin/download/source/](http://pidgin.im/pidgin/download/source/)
Then right click package and extract to desktop
sudo aptitude update
sudo aptitude install build-essential
cd Desktop
cd pidgin-2.1.0
./configure
make
sudo make install
dont remove gaim till pidgin is install trying to remember all i did think i rebooted 
dont know if this will worked for anyone if you try let me know worked for me:guitar:

---

### Post by aidanr on 2007-07-31
Cheers limemonkey, they worked just fine :)

---

### Post by altonbr on 2007-07-31
> **walkerk said:**
> I'm sure we could.. But its just as easy for one of us to package a deb and host it.. thats what getdeb.net is for right? I honestly don't know why the pidgin developers do no publish a deb.. I'm sure they have their reasons..

Well it's not easier for people who don't know how to build a .deb... like the 14 clients I have running Ubuntu, they at least know that a .deb is almost equivalent to an .exe (as in: you can install software by double-clicking it - there is obviously more to it than that, but they don't need to know), but not how to make their own from source.

Not exactly "human" linux at that point.. but then again, that depends on the Ubuntu developers, not Pidgin's.

---

### Post by apc15x on 2007-07-31
Well it seems like everything is working but I have no sound, all I get is a beep. I don't see any way in the preferences to use my own or if they have default sounds other then the beep.:confused:

---

### Post by Old Pink on 2007-07-31
I'd wait a couple of days before installing from source, and I say that having already created a .deb from source, modified it and installed that. 

Installing from source takes a good 10 minutes, minimum, and it really isn't worth it. 

Read my post on it, I detail "what's new" and there isn't much: [http://www.mbhoy.com/01-08-2007/pidgin-210](http://www.mbhoy.com/01-08-2007/pidgin-210)

---

### Post by altonbr on 2007-07-31
> **Old Pink said:**
> I'd wait a couple of days before installing from source, and I say that having already created a .deb from source, modified it and installed that. 

Installing from source takes a good 10 minutes, minimum, and it really isn't worth it. 

Read my post on it, I detail "what's new" and there isn't much: [http://www.mbhoy.com/01-08-2007/pidgin-210](http://www.mbhoy.com/01-08-2007/pidgin-210)

Now that I have it working, I agree.

---

### Post by Jexel on 2007-08-01
> **Gremlinzzz said:**
> Think it made the list check it out
[http://incoming.debian.org/](http://incoming.debian.org/)
:guitar:

i don't see it

---

### Post by Gremlinzzz on 2007-08-01
Use the guide to install pidgin working now.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Pidgin_2.1.0_.28former_GAIM.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Pidgin_2.1.0_.28former_GAIM.29)
:guitar:

---

### Post by altonbr on 2007-08-01
> **Gremlinzzz said:**
> Use the guide to install pidgin working now.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Pidgin_2.1.0_.28former_GAIM.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Pidgin_2.1.0_.28former_GAIM.29)
:guitar:

The section below won't work because the website is down.

> Ubuntu Plugin Pack for pidgin

    * Dowload the Files using the following command 

wget [http://www.kalpiknigam.com/blog/uploads/purple-plugin-pack_1.0-1_i386.deb](http://www.kalpiknigam.com/blog/uploads/purple-plugin-pack_1.0-1_i386.deb)

    * To install the plugin pack, type this into the terminal 

sudo dpkg -i purple-plugin-pack_1.0-1_i386.deb

    * Note: This install will not work under a 64-bit architecture. 

--Skymera 00:08, 2 July 2007 (EEST) Skymera 

---

### Post by fakie_flip on 2007-08-01
How can I compile Off the record plugin for pidgin? I have pidgin 2.0.2-1 compiled and working in 64 bit Ubuntu right now.

---

### Post by mrgnash on 2007-08-01
It conflicts with Gaim, and I can't remove Gaim because Nautilus depends on it, apparently :-S This is weird, because I already have Pidgin 2.0.2 installed.

EDIT: Ok, tried removing Gaim and installing the Pidgin deb, but it still conflicts with Pidgin 2.0.2 -- namely, it reads the 2.1 as an older version for some reason.

---

### Post by limemonkey on 2007-08-01
> **fakie_flip said:**
> How can I compile Off the record plugin for pidgin? I have pidgin 2.0.2-1 compiled and working in 64 bit Ubuntu right now.

on 32 bit, you just go here: [http://packages.ubuntu.com/gutsy/net/pidgin-otr](http://packages.ubuntu.com/gutsy/net/pidgin-otr) and at the bottom of the page you get pidgin-otr_3.0.0+cvs20070508.orig.tar.gz (or whatever version is current)

[I]./configure --prefix=/usr/local
make
sudo checkinstall --exclude=/etc/gconf,/usr/bin,/usr/lib[/I]

But there's for sure a better way to do it. Coming from Redhat/Fedora, so I am not exactly sure about all the different ways to build packages in the Debian world.

---

### Post by altonbr on 2007-08-03
> **limemonkey said:**
> on 32 bit, you just go here: [http://packages.ubuntu.com/gutsy/net/pidgin-otr](http://packages.ubuntu.com/gutsy/net/pidgin-otr) and at the bottom of the page you get pidgin-otr_3.0.0+cvs20070508.orig.tar.gz (or whatever version is current)

[I]./configure --prefix=/usr/local
make
sudo checkinstall --exclude=/etc/gconf,/usr/bin,/usr/lib[/I]

But there's for sure a better way to do it. Coming from Redhat/Fedora, so I am not exactly sure about all the different ways to build packages in the Debian world.

Wait wait wait, just go here: [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.1.0/pidgin_2.1.0-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.1.0/pidgin_2.1.0-1_i386.deb)

Spell check and everything works.

GetDeb also has theirs up: [http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)

---

### Post by limemonkey on 2007-08-03
> **altonbr said:**
> Wait wait wait, just go here: [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.1.0/pidgin_2.1.0-1_i386.deb](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.1.0/pidgin_2.1.0-1_i386.deb)

We were talking about the pidgin-otr plugin ;-)

---

### Post by altonbr on 2007-08-03
> **limemonkey said:**
> We were talking about the pidgin-otr plugin ;-)

I'd call you a smart-*** but I guess I was in the wrong there wasn't I???

---

### Post by Gremlinzzz on 2007-08-03
OK the Ubuntu Plugin Pack for Pidgin is still not working in ubuntu guide guess the site that was posted couldn't pay there bill.does anyone know where to get the Plugin Pack for Pidgin. i have pidgin installed but not the Plugin Pack for Pidgin.
:guitar:

---

### Post by fakie_flip on 2007-08-05
```
sudo checkinstall --exclude=/etc/gconf,/usr/bin,/usr/lib
```

Why should these options be used to checkinstall? 

I did get Pidgin OTR working in 64 bit except one feature does not work.
[http://www.cypherpunks.ca/otr/help/authenticate.php?lang=en](http://www.cypherpunks.ca/otr/help/authenticate.php?lang=en)
I'm not able to authenticate (verify) my buddies by both of us putting in the secret word. I would like to get that feature working.

---

### Post by Gremlinzzz on 2007-08-05
which one [http://plugins.guifications.org/trac/wiki/PluginPack](http://plugins.guifications.org/trac/wiki/PluginPack)

---

