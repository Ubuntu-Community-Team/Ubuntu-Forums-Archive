---
title: "Banshee 0.11.3 for Edgy"
date: 2007-01-01
forum: Repositories &amp; Backports
---

### Post by gummibaerchen on 2007-01-01
Hello,

creating a .deb of Banshee 0.11.3 under Edgy isn't that simple.

But I finally got working packages, thank to mu in #banshee (GimpNET).

Here they are:

[http://t3-ie.info/banshee_0.11.3+dfsg-0ubuntu1_i386.deb](http://t3-ie.info/banshee_0.11.3+dfsg-0ubuntu1_i386.deb)

Regards

---

### Post by hikaricore on 2007-01-02
Thank you :)

---

### Post by mihai.ile on 2007-01-09
someone can help with a .deb for dapper with all plugins?
i mean, why is so dificult to create a .deb in linux??? :( 
i really don't want to upgrade a distribution just for some programs, it's the stupidest thing I saw in linux..

P.S:
i tried [http://linuxrevolution.blogspot.com/2006/12/howto-banshee-0113-on-ubuntu.html](http://linuxrevolution.blogspot.com/2006/12/howto-banshee-0113-on-ubuntu.html) but on  sudo apt-get build-dep banshee i get:E: Build-dependencies for banshee could not be satisfied.
and yess i have all repository activated..

---

### Post by gummibaerchen on 2007-01-09
> **mihai007 said:**
> someone can help with a .deb for dapper with all plugins?
i mean, why is so dificult to create a .deb in linux??? :( 
i really don't want to upgrade a distribution just for some programs, it's the stupidest thing I saw in linux..

P.S:
i tried [http://linuxrevolution.blogspot.com/2006/12/howto-banshee-0113-on-ubuntu.html](http://linuxrevolution.blogspot.com/2006/12/howto-banshee-0113-on-ubuntu.html) but on  sudo apt-get build-dep banshee i get:E: Build-dependencies for banshee could not be satisfied.
and yess i have all repository activated..

I am waiting for that myself.

I will talk to the lads on #banshee and see if anyone has that.

---

### Post by mihai.ile on 2007-01-12
i just found it: [http://directhex.mfgames.com/](http://directhex.mfgames.com/) ;)

---

### Post by gummibaerchen on 2007-01-12
> **mihai007 said:**
> i just found it: [http://directhex.mfgames.com/](http://directhex.mfgames.com/) ;)

Is it updated for 0.11.**3**?

Edit: Yes, great :)

---

### Post by abzolutxero on 2007-01-14
i tried to install the .deb package, and it tells me "Error: Dependency is not satisfiable:boo"

what does that mean, or how do i figure out what dependency is not  there?

---

### Post by gummibaerchen on 2007-01-14
> **abzolutxero said:**
> i tried to install the .deb package, and it tells me "Error: Dependency is not satisfiable:boo"

what does that mean, or how do i figure out what dependency is not  there?

**boo** is not satisfiable, as it says.

Just run "sudo aptitude install boo", that should do.

---

### Post by abzolutxero on 2007-01-14
i think i may have something misconfigured then, i tried that, and got the following response:

abzolutxero@FreeSpirit:~$ sudo aptitude install boo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for boo
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

---

### Post by molgar on 2007-01-22
> **mihai007 said:**
> i just found it: [http://directhex.mfgames.com/](http://directhex.mfgames.com/) ;)

Beware, that one is a Dapper repo, therefore there may be some unsatisfiable dependencies and other/greater headaches if you plan to use it under Edgy.

---

### Post by deadlydeathcone on 2007-01-24
I packaged a good [edgy deb]("http://lightofcracker.com/ubuntu/banshee-0.11.5.tar.gz") for the just released [banshee 0.11.5]("http://mail.gnome.org/archives/banshee-list/2007-January/msg00121.html"). Just so you know this release merged all of the plugins into the core, so I followed suit with the package.

If you want more plugins, you can grab some [here]("http://banshee-project.org/PluginRepository"). Get the library cleaner!

---

### Post by DtJee on 2007-01-24
Tried to install your package.. but libmusicbrainz4c2a is only avaible in version 2.1.2 ... where can i get 2.14. for edgy ...

---

### Post by deadlydeathcone on 2007-01-24
Sorry about that, here's a repository for it:

#Picard music tagging
deb [http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu](http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu) edgy musicbrainz

I'll build banshee so that it doesn't need that in a few.

edit: I updated the original post

---

### Post by gummibaerchen on 2007-01-24
It's pretty buggy :(
Stops when changing the song and so on...

So I will stay on with the great QuodLibet

---

### Post by golem3 on 2007-01-25
OH sweetness. THanks for that .deb package!!

---

### Post by rockrhino27 on 2007-01-26
I'm trying this .deb package now.  By any chance is it compiled with mtp support?  I'm hoping to get my creative labs zen micro photo to sync to it...

---

### Post by deadlydeathcone on 2007-01-27
> **rockrhino27 said:**
> I'm trying this .deb package now.  By any chance is it compiled with mtp support?  I'm hoping to get my creative labs zen micro photo to sync to it...

Nah, I didn't bother because it would mean having to update libgphoto and a couple other things.   I should be able to build one with mtp and updated ipod support tomorrow, though.

---

### Post by shat on 2007-01-29
The .deb works flawlessly, this is exactly what I was looking for, thanks a ton!

Banshee is an excellent and sexy music management tool!

Just for those that are missing out..

:guitar:

Edit:  Just make sure you get rid of the banshee-official-plugins, if you had previously installed banshee

---

### Post by gummibaerchen on 2007-01-30
The .deb crashes when searching my Music Folder. Also banshee seems to have problems with encoding, which quodlibet got all right.

Of course that's not a problem of the .deb-File, but banshee is not yet grown up IMHO. Should not crash THAT often :(

---

### Post by deadlydeathcone on 2007-01-30
> **gummibaerchen said:**
> The .deb crashes when searching my Music Folder
...
Of course that's not a problem of the .deb-File, but banshee is not yet grown up IMHO. Should not crash THAT often :(

Okay, this time I tried building banshee without missing a huge dependency. ](*,) Banshee just moved to a totem-based parser for its library and playlist, so not building against totem didn't really work all that well.

[The rebuilt version]("http://lightofcracker.com/ubuntu/banshee-0.11.5.tar.gz") is a lot faster, has updated ipod support and hasn't crashed in the hour that I've used it.

It has some updated libraries, so install it like this:

```
tar -xvvzf banshee-0.11.5.tar.gz
cd banshee
sudo dpkg -i libipoddevice0_0.5.2-1_i386.deb libipod-cil_0.6.2-0ubuntu2_all.deb libipodui-cil_0.6.2-0ubuntu2_all.deb ipod_0.5.2-1_i386.deb banshee_0.11.5-0ubuntu1_i386.deb  banshee-daap_0.11.5-0ubuntu1_all.deb
```

---

### Post by gummibaerchen on 2007-01-31
> **deadlydeathcone said:**
> Okay, this time I tried building banshee without missing a huge dependency. ](*,) Banshee just moved to a totem-based parser for its library and playlist, so not building against totem didn't really work all that well.

Good boy ;) Thanks a lot.

But one problem remains: [Umlauts]("http://en.wikipedia.org/wiki/Germanic_umlaut")

Any Idea why that is? Instead of "ä". "ö". or "ü" I just see a "?" :(

---

### Post by AdventHorizon on 2007-01-31
Ugh. I got it working yesterday, and everything was great. Then I decided I'd clean up my hard drive a bit and remove stuff that wasn't being used... Now Banshee's not working.

I'm new to the whole Linux thing...Anyone know what package I need to re-install to get this working again? I've already removed and reinstalled Banshee, and I *thought* I'd reinstalled anything media-related that I removed yesterday...But it's still not working.

Here's the error log:
```
An unhandled exception was thrown: Object reference not set to an instance of an object

at Banshee.MediaEngine.Gstreamer.GstreamerPlayerEngine.OnError (intptr,uint,int,intptr,intptr) <0x00094>
at (wrapper native-to-managed) Banshee.MediaEngine.Gstreamer.GstreamerPlayerEngine.OnError (intptr,uint,int,intptr,intptr) <0x00045>
in (unmanaged) 0xb6fbda6b
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at Banshee.BansheeEntry.Startup (string[]) <0x006a3>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_void_string[] (string[]) <0x00048>
at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.CleanRoomStartup/StartupInvocationHandler,string[]) <0x000ae>

.NET Version: 2.0.50727.42

Assembly Version Information:

System.Configuration (2.0.0.0)
glade-sharp (2.10.0.0)
Boo.Lang.Compiler (1.0.0.0)
Banshee.Plugins.Recommendation (0.11.5.36094)
Banshee.Plugins.Radio (0.11.5.36094)
Banshee.Plugins.Podcast (0.11.5.36093)
Banshee.Plugins.NotificationAreaIcon (0.11.5.36091)
Banshee.Plugins.MiniMode (0.11.5.36090)
Banshee.Plugins.MetadataSearch (0.11.5.36089)
Banshee.Plugins.MMKeys (0.11.5.36090)
Banshee.Plugins.Daap (0.11.5.36088)
Banshee.Plugins.Audioscrobbler (0.11.5.36087)
njb-sharp (0.3.0.27013)
Banshee.Dap.Njb (0.11.5.36086)
gnome-vfs-sharp (2.16.0.0)
Banshee.Dap.MassStorage (0.11.5.36086)
ipod-sharp (0.0.1.0)
Banshee.Dap.Ipod (0.11.5.36085)
Banshee.MediaEngine.GStreamer (0.11.5.36085)
System.Xml (2.0.0.0)
gconf-sharp (2.16.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.10.0.0)
Mono.Cairo (2.0.0.0)
Hal (0.0.0.0)
Banshee.Widgets (0.11.5.36079)
Last.FM (0.0.0.0)
NDesk.DBus (0.0.0.0)
Mono.Posix (2.0.0.0)
gnome-sharp (2.16.0.0)
NDesk.DBus.GLib (0.0.0.0)
gdk-sharp (2.10.0.0)
System (2.0.0.0)
atk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
Banshee.Base (0.11.5.36082)
banshee (0.11.5.36084)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.17-10-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"


```

---

### Post by iradi8 on 2007-02-06
Thanks a lot guy! I was sorely disappointed with the Banshee 0.11.1 that Edgy was forcing upon me, and I was having a heck of a time getting it upgraded to something that actually **worked** for podcasts! (Hint to Ubuntu maintainers 0.11.1 in the edgy repositories doesn't actually work for subscribing to, or retrieving podcasts!)

Deadlydeathcone, you have saved me from committing Hari-Kari with my keyboard! :)

---

### Post by dlbolton on 2007-02-07
Thanks Deadlydeathcone for the banshee 0.11.5 package. I really like the podcast plugin that was missing from the earlier package in the repos.

I have noticed one quirky thing about it though. While the transfer to my ipod shuffle seems less prone to hanging, the podcast episode does not play on the ipod.  I have not had enough time to fully explore what is going on here. Maybe I am doing something wrong.

Dave

---

### Post by gummibaerchen on 2007-02-07
Time that someone creates a .deb for [Banshee **0.11.6**]("http://banshee-project.org/Releases/0.11.6")

---

### Post by dlbolton on 2007-02-07
okay, so the obvious question is ... how can I learn how to make a .deb package?

---

### Post by deadlydeathcone on 2007-02-08
You're welcome iradi8. :)

As requested: banshee 11.6! There's not anything earth shattering this time, just some bug fixes and interface changes.

I compiled two versions: [the standard]("http://www.box.net/public/ll97un9ofv") and one with [mtp support]("http://www.box.net/public/fo36yyve2s") (for creative zens and such).

Getting mtp support required backporting the latest gphoto from Feisty and packaging up a library that's so experimental that it's not even in Debian, and on top of that I haven't been to able test it, either.  Don't have the only copy of your college thesis on your zen when you plug it in, alright? 

There's some info and screenshots [here]("http://banshee-project.org/Guide/DAPs/MTP") and [here]("http://trick.vanstaveren.us/wp/2006/06/21/mtp-its-alive/") that might be worth reading if it doesn't seem to work.

edit: now with instructions!

Open a terminal in the folder extracted from the Banshee tarball and enter: 
```
sudo apt-get install libavahi1.0-cil libmono-cairo2.0-cil libmono-sqlite2.0-cil
```

Then, if you have the regular version of Banshee enter this:
```
sudo dpkg -i libipoddevice0_0.5.2-0ubuntu1_i386.deb ipod_0.5.2-0ubuntu1_i386.deb banshee_0.11.6-0ubuntu1_i386.deb banshee-daap_0.11.6-0ubuntu1_all.deb
```

For the mtp version enter this instead:
```
sudo dpkg -i libgphoto2-2_2.3.0-0ubuntu1_i386.deb libgphoto2-port0_2.3.0-0ubuntu1_i386.deb libgphoto2-sharp_2.3.0-0ubuntu1_i386.deb libipoddevice0_0.5.2-0ubuntu1_i386.deb ipod_0.5.2-0ubuntu1_i386.deb banshee_0.11.6-0ubuntu1_i386.deb banshee-daap_0.11.6-0ubuntu1_all.deb
```

---

### Post by iramos on 2007-02-08
Thanks deadlydeathcone!

---

### Post by danderson3 on 2007-02-09
can anyone make a dapper deb of 0.11.6?  thanks...

---

### Post by gummibaerchen on 2007-02-09
> **danderson3 said:**
> can anyone make a dapper deb of 0.11.6?  thanks...

I found some (probably in one of the links here), but the had broken dependencies on my system...

ahh here is the link:
[http://www.box.net/public/ll97un9ofv](http://www.box.net/public/ll97un9ofv)

---

### Post by danderson3 on 2007-02-09
> **gummibaerchen said:**
> I found some (probably in one of the links here), but the had broken dependencies on my system...

ahh here is the link:
[http://www.box.net/public/ll97un9ofv](http://www.box.net/public/ll97un9ofv)

thanks!  I have dependency problems with this on dapper.  One is 
libc6, which I thought is a big deal to upgrade to 2.4 on dapper.  Any
advice on this?

-d

root@d-desktop:/home/d# dpkg -i libipod*deb ban*deb ipod*deb
dpkg - warning: downgrading libipoddevice0 from 0.5.2-1~dhx1 to 0.5.2-0ubuntu1.
(Reading database ... 215323 files and directories currently installed.)
Preparing to replace libipoddevice0 0.5.2-1~dhx1 (using libipoddevice0_0.5.2-0ubuntu1_i386.deb) ...
Unpacking replacement libipoddevice0 ...
Selecting previously deselected package libipoddevice-dev.
Unpacking libipoddevice-dev (from libipoddevice-dev_0.5.2-0ubuntu1_i386.deb) ...
Preparing to replace banshee 0.11.5+dfsg-1~dhx1 (using banshee_0.11.6-0ubuntu1_i386.deb) ...
Unpacking replacement banshee ...
Preparing to replace banshee-daap 0.11.5+dfsg-1~dhx1 (using banshee-daap_0.11.6-0ubuntu1_all.deb) ...
Unpacking replacement banshee-daap ...
Selecting previously deselected package ipod.
Unpacking ipod (from ipod_0.5.2-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of libipoddevice0:
 libipoddevice0 depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 libipoddevice0 depends on libdbus-1-3; however:
  Package libdbus-1-3 is not installed.
 libipoddevice0 depends on libdbus-glib-1-2 (>= 0.71); however:
  Version of libdbus-glib-1-2 on system is 0.60-6ubuntu8.1.
 libipoddevice0 depends on libglib2.0-0 (>= 2.12.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 libipoddevice0 depends on libsgutils1 (>= 1.21); however:
  Package libsgutils1 is not installed.
 libipoddevice0 depends on libxml2 (>= 2.6.26); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.
dpkg: error processing libipoddevice0 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libipoddevice-dev:
 libipoddevice-dev depends on libipoddevice0 (= 0.5.2-0ubuntu1); however:
  Package libipoddevice0 is not configured yet.
 libipoddevice-dev depends on libgtop2-dev; however:
  Package libgtop2-dev is not installed.
dpkg: error processing libipoddevice-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of banshee:
 banshee depends on libatk1.0-0 (>= 1.12.1); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 banshee depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 banshee depends on libcairo2 (>= 1.2.4); however:
  Version of libcairo2 on system is 1.2.2-0ubuntu2.
 banshee depends on libdbus-1-3; however:
  Package libdbus-1-3 is not installed.
 banshee depends on libdbus-glib-1-2 (>= 0.71); however:
  Version of libdbus-glib-1-2 on system is 0.60-6ubuntu8.1.
 banshee depends on libglib2.0-0 (>= 2.12.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 banshee depends on libgnomevfs2-0 (>= 2.15.90); however:
  Version of libgnomevfs2-0 on system is 2.14.2-0ubuntu1.
 banshee depends on libgtk2.0-0 (>= 2.10.3); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.1.
 banshee depends on libnautilus-burn4 (>= 2.15.3); however:
  Package libnautilus-burn4 is not installed.
 banshee depends on liborbit2 (>= 1:2.14.1); however:
  Version of liborbit2 on system is 1:2.14.0-0ubuntu1.
 banshee depends on libpango1.0-0 (>= 1.14.5); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
 banshee depends on libusb-0.1-4 (>= 2:0.1.12); however:
  Version of libusb-0.1-4 on system is 2:0.1.10a-22ubuntu1.
 banshee depends on libxml2 (>= 2.6.26); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.
 banshee depends on libc6 (>= 2.4-1) | libc6.1 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
  Package libc6.1 is not installed.
 banshee depends on libgconf2.0-cil (>= 2.15.0); however:
  Version of libgconf2.0-cil on system is 2.8.3-1~dhx1.
 banshee depends on libglade2.0-cil (>= 2.9.0); however:
  Version of libglade2.0-cil on system is 2.8.3-1~dhx1.
 banshee depends on libglib2.0-cil (>= 2.9.0); however:
  Version of libglib2.0-cil on system is 2.8.3-1~dhx1.
 banshee depends on libgnome2.0-cil (>= 2.15.0); however:
  Version of libgnome2.0-cil on system is 2.8.3-1~dhx1.
 banshee depends on libgtk2.0-cil (>= 2.9.0); however:
  Version of libgtk2.0-cil on system is 2.8.2-0ubuntu5.
 banshee depends on libipoddevice0 (>= 0.5.2); however:
  Package libipoddevice0 is not configured yet.
 banshee depends on libtotem-plparser1 (>= 2.16.1); however:
  Version of libtotem-plparser1 on system is 1.4.3-0ubuntu1.
dpkg: error processing banshee (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of banshee-daap:
 banshee-daap depends on libavahi1.0-cil (>= 0.6.10); however:
  Package libavahi1.0-cil is not installed.
 banshee-daap depends on libglib2.0-cil (>= 2.9.0); however:
  Version of libglib2.0-cil on system is 2.8.3-1~dhx1.
 banshee-daap depends on libgtk2.0-cil (>= 2.9.0); however:
  Version of libgtk2.0-cil on system is 2.8.2-0ubuntu5.
 banshee-daap depends on banshee (= 0.11.6-0ubuntu1); however:
  Package banshee is not configured yet.
dpkg: error processing banshee-daap (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ipod:
 ipod depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
 ipod depends on libdbus-1-3; however:
  Package libdbus-1-3 is not installed.
 ipod depends on libdbus-glib-1-2 (>= 0.71); however:
  Version of libdbus-glib-1-2 on system is 0.60-6ubuntu8.1.
 ipod depends on libglib2.0-0 (>= 2.12.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 ipod depends on libipoddevice0 (>= 0.5.2); however:
  Package libipoddevice0 is not configured yet.
 ipod depends on libxml2 (>= 2.6.26); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.
dpkg: error processing ipod (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libipoddevice0
 libipoddevice-dev
 banshee
 banshee-daap
 ipod

---

### Post by Imerion on 2007-02-10
Thanks for these packages! Now I have the latest banshee up and running.
Just a question, could someone help create a package for these plugins :

Fleow : "svn checkout svn://svn.berlios.de/fleow/trunk fleow"

ShowTrackOnChange : "svn checkout [http://showtrackonchange.googlecode.com/svn/trunk/](http://showtrackonchange.googlecode.com/svn/trunk/) showtrackonchange"

And perhaps this one also : "svn co svn://svn.banshee-project.org/trunk/banshee-wikipedia-plugin"

I have tried to compile them myself but It does never seem to work. So if anyone could help creating a package for any of these I would be grateful!

---

### Post by molgar on 2007-02-10
> **deadlydeathcone said:**
> You're welcome iradi8. :)

As requested: banshee 11.6! There's not anything earth shattering this time, just some bug fixes and interface changes.

I compiled two versions: [the standard]("http://www.box.net/public/ll97un9ofv") and one with [mtp support]("http://www.box.net/public/fo36yyve2s") (for creative zens and such).

Getting mtp support required backporting the latest gphoto from Feisty and packaging up a library that's so experimental that it's not even in Debian, and on top of that I haven't been to able test it, either.  Don't have the only copy of your college thesis on your zen when you plug it in, alright? 

There's some info and screenshots [here]("http://banshee-project.org/Guide/DAPs/MTP") and [here]("http://trick.vanstaveren.us/wp/2006/06/21/mtp-its-alive/") that might be worth reading if it doesn't seem to work.

You are my hero of the day, thanks!!!

---

### Post by gummibaerchen on 2007-02-10
> **molgar said:**
> You are my hero of the day, thanks!!!

Does that work for you without problems?

---

### Post by spartan777 on 2007-02-10
i tried installing the 11.6 .deb (non-mtp), but when I try to install 

libipoddevice-dev_0.5.2-0ubuntu1_i386.deb            
I get "dependency not satisfiable 'libipoddevice0'"


libipoddevice0_0.5.2-0ubuntu1_i386.deb
and
ipod_0.5.2-0ubuntu1_i386.deb
I get later version already installed.

if I install either of the other banshee .deb's it will obviously break it. what do I do?

---

### Post by deadlydeathcone on 2007-02-11
> **spartan777 said:**
> i tried installing the 11.6 .deb (non-mtp), but when I try to install 

libipoddevice-dev_0.5.2-0ubuntu1_i386.deb            
I get "dependency not satisfiable 'libipoddevice0'"

libipoddevice0_0.5.2-0ubuntu1_i386.deb
and
ipod_0.5.2-0ubuntu1_i386.deb
I get later version already installed.

if I install either of the other banshee .deb's it will obviously break it. what do I do?

Doh, I can be so vacuous at times. Here's the installation instructions:

Open a terminal in the folder extracted from the Banshee tarball and enter: 
```
sudo apt-get install libavahi1.0-cil libmono-cairo2.0-cil libmono-sqlite2.0-cil
```

Then, if you have the regular version of Banshee do this:
```
sudo dpkg -i libipoddevice0_0.5.2-0ubuntu1_i386.deb ipod_0.5.2-0ubuntu1_i386.deb banshee_0.11.6-0ubuntu1_i386.deb banshee-daap_0.11.6-0ubuntu1_all.deb
```

For the mtp version (has anyone tried this yet?) do this instead:
```
sudo dpkg -i libgphoto2-2_2.3.0-0ubuntu1_i386.deb libgphoto2-port0_2.3.0-0ubuntu1_i386.deb libgphoto2-sharp_2.3.0-0ubuntu1_i386.deb libipoddevice0_0.5.2-0ubuntu1_i386.deb ipod_0.5.2-0ubuntu1_i386.deb banshee_0.11.6-0ubuntu1_i386.deb banshee-daap_0.11.6-0ubuntu1_all.deb
```

RAOF is awesome and going to let me use his repository, so this process should hopefuly get a lot easier sometime soon.

@ Imerion:
Fleow looks pretty cool, I'll see if I can get it packaged.

---

### Post by con on 2007-02-11
I installed the mtp version. 

First time round I had the following dependency problems, 
libsgutils1, boo, libmono-system-web2.0-cil, libmono2.0-cil, libmono-sharpzip2.84-cil.

After installing those it worked fine, but it takes an age to load the library from my zen (about half an hour at this stage and still not done). Apparently this is fixed with a newer version of libgphoto2.

---

### Post by spartan777 on 2007-02-13
deadlydeathcone; thanks, when I ran

```
sudo apt-get install libavahi1.0-cil libmono-cairo2.0-cil libmono-sqlite2.0-cil
```

It said that I already had the latest versions installed, and 

```
sudo dpkg -i libgphoto2-2_2.3.0-0ubuntu1_i386.deb libgphoto2-port0_2.3.0-0ubuntu1_i386.deb libgphoto2-sharp_2.3.0-0ubuntu1_i386.deb libipoddevice0_0.5.2-0ubuntu1_i386.deb ipod_0.5.2-0ubuntu1_i386.deb banshee_0.11.6-0ubuntu1_i386.deb banshee-daap_0.11.6-0ubuntu1_all.deb
```

installed fine. However, when I run Banshee, I get this;

```
An unhandled exception was thrown: The classes in the module cannot be loaded.

  at <0x00000> <unknown method>
  at (wrapper managed-to-native) System.Reflection.Assembly:GetTypes (bool)
  at System.Reflection.Assembly.GetTypes () [0x00000] 
  at Banshee.Plugins.PluginFactory`1[Banshee.Plugins.Plugin].LoadPluginsFromAssembly (System.Reflection.Assembly ) [0x00000] 
  at Banshee.Plugins.PluginFactory`1[Banshee.Plugins.Plugin].LoadPluginsFromFile (System.IO.FileInfo ) [0x00000] 
  at Banshee.Plugins.PluginFactory`1[Banshee.Plugins.Plugin].LoadPluginsFromDirectory (System.IO.DirectoryInfo ) [0x00000] 
  at Banshee.Plugins.PluginFactory`1[Banshee.Plugins.Plugin].LoadPlugins () [0x00000] 
  at Banshee.Plugins.PluginCore.Initialize () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
  at Banshee.Base.ComponentInitializer.Run () [0x00000] 
  at Banshee.Base.Globals.Initialize (Banshee.Base.ComponentInitializerHandler interfaceStartupHandler) [0x00000] 
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_string[] (string[])
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

MiniMode (0.11.1.0)
Banshee.Plugins.Recommendation (0.11.6.15221)
Banshee.Plugins.Radio (0.11.6.15220)
Banshee.Plugins.Podcast (0.11.6.15219)
Banshee.Plugins.NotificationAreaIcon (0.11.6.15217)
Banshee.Plugins.MiniMode (0.11.6.15216)
Banshee.Plugins.MetadataSearch (0.11.6.15215)
Banshee.Plugins.MMKeys (0.11.6.15216)
Banshee.Plugins.Daap (0.11.6.15214)
Banshee.Plugins.Audioscrobbler (0.11.6.15213)
njb-sharp (0.3.0.27013)
Banshee.Dap.Njb (0.11.6.15212)
gnome-vfs-sharp (2.16.0.0)
Banshee.Dap.MassStorage (0.11.6.15211)
ipod-sharp (0.0.1.0)
Banshee.Dap.Ipod (0.11.6.15211)
Banshee.MediaEngine.GStreamer (0.11.6.15210)
System.Xml (2.0.0.0)
gconf-sharp (2.16.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
pango-sharp (2.10.0.0)
Mono.Cairo (2.0.0.0)
Hal (0.0.0.0)
Banshee.Widgets (0.11.6.15204)
Last.FM (0.0.0.0)
NDesk.DBus (0.0.0.0)
Mono.Posix (2.0.0.0)
gnome-sharp (2.16.0.0)
NDesk.DBus.GLib (0.0.0.0)
gdk-sharp (2.10.0.0)
System (2.0.0.0)
atk-sharp (2.10.0.0)
glib-sharp (2.10.0.0)
gtk-sharp (2.10.0.0)
Banshee.Base (0.11.6.15207)
banshee (0.11.6.15209)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.17-11-generic i686 unknown GNU/Linux

Disribution Information:

[/etc/debian_version]
testing/unstable

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"


```

this error doesn't show up until "Plugins" is loading in the Banshee splash. Your help is much appreciated.

---

### Post by BrunoC on 2007-02-13
I just installed the non-mtp deb and works great, thanks ;)

---

### Post by nigra on 2007-02-18
Hi,
   Thanks for the packages. I'm running banshee 0.11.6 now but recommendations plugin stopped working. When I run banshee from the terminal, I get the following error for recommendation fetching process:
[HTML]Could not fetch recommendations: Invalid URI: The hostname could not be parsed[/HTML]
   I guess it's about a mis-encoded file or something like that, I couldn't find anything relevant in google. The elegance of this recommendations plugin is the thing that makes me use banshee; it is important for me. :(  I'd appreciate any help.

---

### Post by gabrielrm on 2007-02-19
thank you for packages!
i install and run the standard version of banshee 0.11.6. :)
at install time it run in some dependency problem, but was rezolved by "sudo apt-get -f install", as suggested by apt-get.

---

### Post by gummibaerchen on 2007-02-21
**[SIZE="7"][FONT="Georgia"]Banshee 0.11.7[/FONT][/SIZE]**

[http://www.wikiupload.com/comment.php?id=85998](http://www.wikiupload.com/comment.php?id=85998)
(and klick download, then download)

:popcorn: :guitar:

---

### Post by gilir on 2007-02-21
> **nigra said:**
> Hi,
   Thanks for the packages. I'm running banshee 0.11.6 now but recommendations plugin stopped working. When I run banshee from the terminal, I get the following error for recommendation fetching process:
[HTML]Could not fetch recommendations: Invalid URI: The hostname could not be parsed[/HTML]
   I guess it's about a mis-encoded file or something like that, I couldn't find anything relevant in google. The elegance of this recommendations plugin is the thing that makes me use banshee; it is important for me. :(  I'd appreciate any help.

Same here :( Anyone else try to use the recommendation plugin ?

---

### Post by molgar on 2007-02-22
Regarding the recommendations plugin not working, you might want to check this solution: [http://www.kalmwave.com/2007/02/22/music-recommendations-in-banshee/](http://www.kalmwave.com/2007/02/22/music-recommendations-in-banshee/)

---

### Post by BulletzBill on 2007-02-23
Just installed Banshee 0.11.7 on Edgy using the link provided above ([http://www.wikiupload.com/comment.php?id=85998](http://www.wikiupload.com/comment.php?id=85998)) but when I attempt to run the program nothing happens. I get the busy cursor and there is a window tab on my panel that says "Starting Banshee Music Player" (but does not display a window or splash) for about 10 seconds then disappears, and thats it. 

Any suggestions?

---

### Post by gummibaerchen on 2007-02-23
> **BulletzBill said:**
> Any suggestions?

No, sorry.

Try "sudo apt-get build-dep banshee" or "sudo apt-get install banshee", and then install the package again (to have all dependencies).

---

### Post by spartan777 on 2007-02-26
this is the error I get.

[http://www.flickr.com/photos/68281707@N00/404007955/](http://www.flickr.com/photos/68281707@N00/404007955/)

---

### Post by vinboy on 2007-02-28
great thanks.
apparent the packages on ubuntu is very outdated.

---

### Post by karl_forshaw on 2007-03-09
0.12 is now available. Anybody got any tips for compiling it?

---

### Post by mykalreborn on 2007-03-09
> 0.12 is now available. Anybody got any tips for compiling it?

here ya go:[http://open-conceptions.blogspot.com/2007/03/all-new-banshee-012.html](http://open-conceptions.blogspot.com/2007/03/all-new-banshee-012.html)
:D

---

### Post by karl_forshaw on 2007-03-09
Thanks man, 

One question: --disable-docs seemed to make the difference between it working and not working. Do you mind me asking what the significance of this is?

Thanks again

---

### Post by mykalreborn on 2007-03-09
> 
One question: --disable-docs seemed to make the difference between it working and not working. Do you mind me asking what the significance of this is?

hehe. i don't really know. banshee is built on the .NET mono platform (see [here]("http://www.mono-project.com/Main_Page")), and the docs are for developers i think. or it's something to do with the distribution. 
like i said i don't really know. i saw this on a web page somewhere. :D

---

### Post by karl_forshaw on 2007-03-09
Its well spotted mate, and well done.

I'll test the instructions from your blog out on a vanilla install of edgy and attempt a .deb.

---

### Post by mykalreborn on 2007-03-09
> Its well spotted mate, and well done.

I'll test the instructions from your blog out on a vanilla install of edgy and attempt a .deb.

i'll put in instructions on how to install two un-official plugins in banshee. stay tuned! and tell your friends :p

---

