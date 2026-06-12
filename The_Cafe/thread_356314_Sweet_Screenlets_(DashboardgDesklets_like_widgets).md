---
title: "Sweet: Screenlets (Dashboard/gDesklets like widgets)"
date: 2007-02-08
forum: The Cafe
---

### Post by buellman on 2007-02-08
Hi,

I found some (to me) new eyecandy to play with:
[IMG]http://www.ryxperience.com/storage/screenlets-0.0.4-thumb.jpg[/IMG]

Link: [Screenlets]("http://forum.go-compiz.org/viewtopic.php?t=358"). :)

Greets. Buellman

---

### Post by mr.farenheit on 2007-02-09
spiffy. i'll have to get me some now

---

### Post by zubrug on 2007-02-09
yummy, thanks

---

### Post by delfick on 2007-02-09
you do know that screenlets are made independantly of beryl or compiz ?? :D

(i.e. mods might want to remove "compiz" from the thread title :D)

---

### Post by ButteBlues on 2007-02-09
> **delfick said:**
> you do know that screenlets are made independantly of beryl or compiz ?? :D

(i.e. mods might want to remove "compiz" from the thread title :D)
It's not hurting anything.

---

### Post by FuturePilot on 2007-02-09
I take it by the title these don't work with Beryl?:confused:

---

### Post by steven8 on 2007-02-09
The best thing about the screenshot is the wonderful green background.

---

### Post by hanzomon4 on 2007-02-10
> **FuturePilot said:**
> I take it by the title these don't work with Beryl?:confused:

It works with beryl and it's not a plugin.....

---

### Post by Choad on 2007-02-10
the manager doesnt work for me, but the individual desklets do

---

### Post by delfick on 2007-02-10
> **ButteBlues said:**
> It's not hurting anything.

afaik, RYX, the developer of screenlets wants them to be recognised as a seperate app to compiz and beryl :D .....
(also, it's misleading :P)


anywho, screenlets are awsome....

(though i recommend waiting till later versions before trying them :P :D)

because (from what i've read) later versions will have source control (i think bzr), a install script (at the moment, you don't actually install them, to use them.....which has it's problems), better support for saving settings, more plugins that have been made by other people since it's initial release, etc :D

(still early days yet) :D

(hopefully RYX doesn't mind me saying this :P)

---

### Post by RAV TUX on 2007-02-10
> **delfick said:**
> afaik, RYX, the developer of screenlets wants them to be recognised as a seperate app to compiz and beryl :D .....
(also, it's misleading :P)


anywho, screenlets are awsome....

(though i recommend waiting till later versions before trying them :P :D)

because (from what i've read) later versions will have source control (i think bzr), a install script (at the moment, you don't actually install them, to use them.....which has it's problems), better support for saving settings, more plugins that have been made by other people since it's initial release, etc :D

(still early days yet) :D

(hopefully RYX doesn't mind me saying this :P)

This seems very similar to SuperKaramba and Opera widgets.:popcorn:

***edited thread title accordingly****

---

### Post by RAV TUX on 2007-02-10
SuperKaramba Screenshots

---

### Post by delfick on 2007-02-10
> **RAV TUX said:**
> This seems very similar to SuperKaramba and Opera widgets.:popcorn:

except better :D


here have a screenshot.... [http://delfick.storage.googlepages.com/screenlets0-0-6.jpg](http://delfick.storage.googlepages.com/screenlets0-0-6.jpg)

and because they're svg, they scale really really well :D [http://delfick.storage.googlepages.com/screenlet-clock-big.jpg](http://delfick.storage.googlepages.com/screenlet-clock-big.jpg)

and...

> FUTURE:
If we can work out a shared codebase, Shelf/nzjrs(desklet-engine), Stuart Langridge(Jackfield Project) and me will (hopefully) merge/combine our projects and create the most ***-kicking Desklet/Screenlet-framework ever seen. 


> ***edited thread title accordingly****

thnx :D

[offtopic] wow, you have a large signature :p[/offtopic]

---

### Post by cbudden on 2007-02-10
> **Choad said:**
> the manager doesnt work for me, but the individual desklets do

I am also unable to run the backend, with the following error:
```

./screenletsd.py start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
Traceback (most recent call last):
  File "./screenletsd.py", line 476, in ?
    service = ScreenletsService(bus_name)
  File "./screenletsd.py", line 232, in __init__
    self.backend = CachingBackend(path = 
TypeError: unsupported operand type(s) for +: 'NoneType' and 'str'

```

After looking through the thread on go-compiz, the solution is to create this directory manually - $HOME/.config/Screenlets/

---

### Post by delfick on 2007-02-10
> **cbudden said:**
> I am also unable to run the backend, with the following error:
```

./screenletsd.py start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
Traceback (most recent call last):
  File "./screenletsd.py", line 476, in ?
    service = ScreenletsService(bus_name)
  File "./screenletsd.py", line 232, in __init__
    self.backend = CachingBackend(path = 
TypeError: unsupported operand type(s) for +: 'NoneType' and 'str'

```

try 


mkdir ~/.config/Screenlets
gedit ~/.config/Screenlets/screenletsd.ses

and save the file

and try again :D

---

### Post by Paulus on 2007-02-10
great to see more promising work in the community!:KS

---

### Post by RYX on 2007-02-11
Hi everybody! 

I am RYX, the author of the screenlets. I have been registered since a few years (for whatever reason) but never made a single post. So hello everyone, this is my first post :) ...

I just wanted to note that the Screenlets have absolutely nothing in common with superkaramba and/or gdesklets. Screenlets have an entirely different architecture and are, basically, stand-alone applications - not plugins or some XML-based pseudo-language theme to some binary app. Instead, Screenlets have theming-support to allow each screenlet to have an unlimited number of totally different designs.

Screenlets are fully-featured gtk-applications written in python. The Screenlet-superclass handles and simplifies a lot of rather complicated stuff and the Screenlet-subclasses (the things called "screenlets") can concentrate on being useful and good-looking ... 

I am no friend of calling them beryl-/compiz-"widgets" because they are a separate application and also work with xfwm4's compositing-mode or even xcompmgr.

So after giving my two cents, I am happy to announce that a 0.0.7 version has been released. [Get it while it's still fresh]("http://forum.go-compiz.org/viewtopic.php?t=358") :D

EDIT: And delfick - thank you a thousand times for promoting the screenlets so well :D :D :D ...

best regards

RYX

---

### Post by delfick on 2007-02-12
> **RYX said:**
> 
EDIT: And delfick - thank you a thousand times for promoting the screenlets so well :D :D :D
my pleasure :D :D :D

---

### Post by reacocard on 2007-02-12
I've built Ubuntu debs for this, and created a repo! Add the following to your sources.list:

```
deb http://download.tuxfamily.org/syzygy42 edgy screenlets
deb-src http://download.tuxfamily.org/syzygy42 edgy screenlets
```

then do 
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install screenlets
```

If you use Beryl, you'll probably also want the Beryl widget plugin, also in the repo:
```
sudo apt-get install beryl-widget-plugin
```

---

### Post by delfick on 2007-02-12
thnx reacocard....though after installing it, there is no trace of it....

no screenlets commands, no screenlet folder, nothing :(

(also, sorcerer has his repo over here [http://hendrik.kaju.pri.ee/ubuntu/dists/edgy/screenlets/](http://hendrik.kaju.pri.ee/ubuntu/dists/edgy/screenlets/) (which funnily enough doesn't seem to work either :P)

(8th post down [http://forum.go-compiz.org/viewtopic.php?t=358&postdays=0&postorder=asc&start=345](http://forum.go-compiz.org/viewtopic.php?t=358&postdays=0&postorder=asc&start=345) )

---

### Post by barney_1 on 2007-02-12
Installing on feisty I ran into a problem:
```
mike@krusty:/usr/local/share/screenlets$ screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
mike@krusty:/usr/local/share/screenlets$ Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 43, in <module>
    from xdg import BaseDirectory
ImportError: No module named xdg

```

Looks like I need python-xdg installed but apt-get game me some dependency issues.  I tried:
```
sudo aptitude install python-xdg
```

That didn't do the trick as I no have this:
```
mike@krusty:/usr/local/share/screenlets$ screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
mike@krusty:/usr/local/share/screenlets$ Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 46, in <module>
    import screenlets
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 266, in <module>
    class Screenlet(gobject.GObject, EditableOptions):
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 290, in Screenlet
    __NOTIFY_OBJ), __NOTIFY_IFACE)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 412, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 232, in __init__
    _dbus_bindings.UInt32(0))
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 171, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
dbus.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Notifications was not provided by any .service files
```

I may try reacocard's Edgy repo listed two posts above to get this thing rolling.

EDIT: No dice on the above posted repo either.

---

### Post by reacocard on 2007-02-12
> **delfick said:**
> thnx reacocard....though after installing it, there is no trace of it....

no screenlets commands, no screenlet folder, nothing :(

(also, sorcerer has his repo over here [http://hendrik.kaju.pri.ee/ubuntu/dists/edgy/screenlets/](http://hendrik.kaju.pri.ee/ubuntu/dists/edgy/screenlets/) (which funnily enough doesn't seem to work either :P)

(8th post down [http://forum.go-compiz.org/viewtopic.php?t=358&postdays=0&postorder=asc&start=345](http://forum.go-compiz.org/viewtopic.php?t=358&postdays=0&postorder=asc&start=345) )

Gah. You're right. Why on earth doesn't he use a proper Makefile instead of this stupid setup.py junk? It's a pain in the *** to package. I'll see if I can fix it, but it may be awhile.

beryl widget plugin package should still be good though.

---

### Post by rado_london on 2007-02-12
I love it but I have black colour around each of the desklets. Any one knows how to fix this?

---

### Post by delfick on 2007-02-12
> **rado_london said:**
> I love it but I have black colour around each of the desklets. Any one knows how to fix this?

you need a compositing manager for transparency to work (the black bits are transparent)

i.e. beryl/compiz/xcompmgr :D

---

### Post by reacocard on 2007-02-12
Repository should be fixed now.

---

### Post by delfick on 2007-02-12
> **reacocard said:**
> Repository should be fixed now.

i'm starting to wonder if this is a problem with my computer, because it still doesn't work :(......

i'm gonna try installing the actual package and see if it installs....


(o ye, and i can't test if the the widget plugin installs from your repo, because it trys to install beryl-core as well, and i'm using svn....)

---

### Post by picpak on 2007-02-12
Would this make a good alternative to adesklets?

---

### Post by delfick on 2007-02-12
> **reacocard said:**
> Gah. You're right. Why on earth doesn't he use a proper Makefile instead of this stupid setup.py junk? It's a pain in the *** to package. I'll see if I can fix it, but it may be awhile.

beryl widget plugin package should still be good though.

hmm, reading the README file here 

> --------------------------------------------------------------------------------
+ INSTALLATION:
--------------------------------------------------------------------------------
Extract the archive into some directory. Navigate to that directory. 
As root-user run "python setup.py install" (Ubuntu users just add a 
leading "sudo" to install).

Alternatively, you can use the Makefile and simply run "make install" 
(as root-user).  

:D

EDIT :: and the makefile worked for me :D :D

---

### Post by delfick on 2007-02-12
> **picpak said:**
> Would this make a good alternative to adesklets?

as it progresses....hell ye!! :D

---

### Post by deadlydeathcone on 2007-02-12
> **reacocard said:**
> Repository should be fixed now.

It's working fine, thanks.

I just took a:
```
screenletsd start
screenletsd add Control

```
to get it started.

Thanks for bringing this up delflick, I had forgotten all about these! There's been a lot of progress since v0.0.2.

edit: using these as widgets is way easy now. Just enable the widget layer in beryl/compiz and check "treat as widget" in a widgets properties box.

---

### Post by picpak on 2007-02-12
This is my dock, will it be easy enough to replicate with screenlets?

[IMG]http://img.photobucket.com/albums/v37/picpak/dock.png[/IMG]

Also, I'm glad to hear it will play nice with compositors (adesklets does a horrible job).

---

### Post by Treviño on 2007-02-12
Well... setup.py isn't hard to package if your debian/rules is well configured ;)
I think setup.py could be more flexible than makefile itself :)

---

### Post by Treviño on 2007-02-12
Well... setup.py isn't hard to package if your debian/rules is well configured ;)
I think setup.py could be more flexible than makefile itself :)

---

### Post by reacocard on 2007-02-12
> **Treviño said:**
> Well... setup.py isn't hard to package if your debian/rules is well configured ;)
I think setup.py could be more flexible than makefile itself :)

How the heck do you get it working in your debian/rules?! I've been looking for a guide to do that and haven't been able to find anything at all.

---

### Post by Treviño on 2007-02-12
> **reacocard said:**
> Gah. You're right. Why on earth doesn't he use a proper Makefile instead of this stupid setup.py junk? It's a pain in the *** to package. I'll see if I can fix it, but it may be awhile.

Well... setup.py isn't hard to package if your debian/rules is well configured ;)
I think setup.py could be more flexible than makefile itself :)

---

### Post by delfick on 2007-02-12
> **deadlydeathcone said:**
> 
```
screenletsd start
screenletsd add Control

```
to get it started.

@anyone, if screenletsd start gives you errors, then

```
sudo gedit /usr/local/share/screenlets/screenletsd.py 
```

and at line 32, insert this 

```
import pygtk
pygtk.require('2.0')
```

then it should work (fixed my problems :D)

(fix from the compiz forums :D)

> Thanks for bringing this up delflick, 

wasn't me, it was buellman :D

> There's been a lot of progress since v0.0.2.

certainly has :D

---

### Post by reacocard on 2007-02-13
> **delfick said:**
> @anyone, if screenletsd start gives you errors, then

```
sudo gedit /usr/local/share/screenlets/screenletsd.py 
```

and at line 32, insert this 

```
import pygtk
pygtk.require('2.0')
```

then it should work (fixed my problems :D)

Thanks delfick, I'll add that as a dependency to the package next time I build.

---

### Post by Mateo on 2007-02-13
don't understand the appeal of widgets.  I already have a clock on my taskbar, don't need another.  don't need to know how much RAM is being used at all times.  Don't want a launcher that I have to minimize everything on screen to use.  ditto for the notepad (already have that available as a panel applet, much faster), and I have absolutely no use for a ruler on my desktop.  but that's just me.

---

### Post by pichalsi on 2007-02-13
> **Mateo said:**
> don't understand the appeal of widgets.  I already have a clock on my taskbar, don't need another.  don't need to know how much RAM is being used at all times.  Don't want a launcher that I have to minimize everything on screen to use.  ditto for the notepad (already have that available as a panel applet, much faster), and I have absolutely no use for a ruler on my desktop.  but that's just me.

Similar here but I still think it looks nice even tho I dont use it. :)

---

### Post by reacocard on 2007-02-13
> **Mateo said:**
> don't understand the appeal of widgets.  I already have a clock on my taskbar, don't need another.  don't need to know how much RAM is being used at all times.  Don't want a launcher that I have to minimize everything on screen to use.  ditto for the notepad (already have that available as a panel applet, much faster), and I have absolutely no use for a ruler on my desktop.  but that's just me.

The examples you mention aren't terribly useful, but there are many possible screenlets that would be useful, just aren't included/made yet. Screenlets for weather, wikipedia, dictionary, etc. would all be very handy, and are really the biggest use for this. Also, if you wanted to get rid if your panels/DE, screenlets could provide much of the same functionality, without the overhead of a complete DE.

---

### Post by buellman on 2007-02-13
> **reacocard said:**
> The examples you mention aren't terribly useful, but there a many possible screenlets that would be useful, just aren't included/made yet. Screenlets for weather, wikipedia, dictionary, etc. would all be very handy, and are really the biggest use for this. Also, if you wanted to get rid if your panels/DE, screenlets could provide much of the same functionality, without the overhead of a complete DE.
I wonder if someone will make some log file viewer screenlet. I would try it myself but have no knowledge and most important no time :)  But maybe someone will do it...

Greets Buellman

---

### Post by hanzomon4 on 2007-02-13
This is progressing along nicely, good job RYX........
I really want to see more apps that take advantage of compositing but are not parts of compiz/beryl. 
This and the Docks(Kiba, Gnome) were at the top of my list, so......

---

### Post by reacocard on 2007-02-13
I've uploaded a new version to the repo, fixing a dependency problem and the build process. I've also added a screenlets-extras package that has several unofficial screenlets, including RSS and Weather.

---

### Post by Super King on 2007-02-13
These look quite neat, I'll give it a try tomorrow.

---

### Post by delfick on 2007-02-14
> **reacocard said:**
> I've uploaded a new version to the repo, fixing a dependency problem and the build process. I've also added a screenlets-extras package that has several unofficial screenlets, including RSS and Weather.

thnx :D

though now it gives me this

> iambob@bob-linux:~$ screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
iambob@bob-linux:~$ Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 46, in ?
    import screenlets
ImportError: No module named screenlets



....

---

### Post by reacocard on 2007-02-14
> **delfick said:**
> thnx :D

though now it gives me this

```
iambob@bob-linux:~$ screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
iambob@bob-linux:~$ Traceback (most recent call last):
File "/usr/local/share/screenlets/screenletsd.py", line 46, in ?
import screenlets
ImportError: No module named screenlets
```

....

Dang, wrong switch. Fixed now.

---

### Post by ButteBlues on 2007-02-14
> **reacocard said:**
> Dang, wrong switch. Fixed now.
For anyone who's wondering, this is caused by not having the screenlets in the correct folder for your python version.

For Feisty Fawn users, this means moving /usr/lib/python/screenlets or /usr/lib/python2.4/site-packages/screenlets to /usr/lib/python2.5/site-packages/screenlets

---

### Post by barney_1 on 2007-02-14
Thanks for the feisty tip.  Unfortunately that didn't get it running for me:
```
mike@krusty:/$ sudo apt-get install screenlets
Reading package lists... Done
Building dependency tree
Reading state information... Done
Recommended packages:
  compiz
The following NEW packages will be installed:
  screenlets
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/237kB of archives.
After unpacking 2114kB of additional disk space will be used.
Selecting previously deselected package screenlets.
(Reading database ... 125824 files and directories currently installed.)
Unpacking screenlets (from .../screenlets_0.0.7-5_i386.deb) ...
Setting up screenlets (0.0.7-5) ...

mike@krusty:/$ sudo mv /usr/lib/python2.4/site-packages/screenlets/ /usr/lib/pyt                                                                                                   hon2.5/site-packages/screenlets/
mike@krusty:/$ sudo screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
mike@krusty:/$ Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 46, in <module>
    import screenlets
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 266, in <                                                                                                   module>
    class Screenlet(gobject.GObject, EditableOptions):
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 288, in S                                                                                                   creenlet
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 671, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 295, in __new__
    mainloop=mainloop)
dbus.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply.                                                                                                    Possible causes include: the remote application did not send a reply, the messa                                                                                                   ge bus security policy blocked the reply, the reply timeout expired, or the netw                                                                                                   ork connection was broken.

```

---

### Post by ButteBlues on 2007-02-14
> **barney_1 said:**
> Thanks for the feisty tip.  Unfortunately that didn't get it running for me:
```
mike@krusty:/$ sudo apt-get install screenlets
Reading package lists... Done
Building dependency tree
Reading state information... Done
Recommended packages:
  compiz
The following NEW packages will be installed:
  screenlets
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/237kB of archives.
After unpacking 2114kB of additional disk space will be used.
Selecting previously deselected package screenlets.
(Reading database ... 125824 files and directories currently installed.)
Unpacking screenlets (from .../screenlets_0.0.7-5_i386.deb) ...
Setting up screenlets (0.0.7-5) ...

mike@krusty:/$ sudo mv /usr/lib/python2.4/site-packages/screenlets/ /usr/lib/pyt                                                                                                   hon2.5/site-packages/screenlets/
mike@krusty:/$ sudo screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
mike@krusty:/$ Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 46, in <module>
    import screenlets
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 266, in <                                                                                                   module>
    class Screenlet(gobject.GObject, EditableOptions):
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 288, in S                                                                                                   creenlet
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 671, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 295, in __new__
    mainloop=mainloop)
dbus.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply.                                                                                                    Possible causes include: the remote application did not send a reply, the messa                                                                                                   ge bus security policy blocked the reply, the reply timeout expired, or the netw                                                                                                   ork connection was broken.

```
Actually, you didn't do it quite right. ;)

[quote=your log]mike@krusty:/$ sudo mv /usr/lib/python2.4/site-packages/screenlets/ /usr/lib/pyt    [/quote]

The target should be /usr/lib/python2.5/site-packages/


The easiest way to do this right is to open Nautilus or Thunar as root and move it that way.

---

### Post by sorcererx84 on 2007-02-14
I have a package in my repository with python2.5 libs, custom screenlets (Weather, Rss, Systemstatus, Convert, Calendar) and a tray-icon which supports installing screenlets from tar.gz files and backing up your settings. The deb with a sample screenlet package is available [here]("http://hendrik.kaju.pri.ee/screenlets/screenlets-deb-0.0.7-4.tar.gz") and the repository at [http://hendrik.kaju.pri.ee/ubuntu]("http://hendrik.kaju.pri.ee/ubuntu")

---

### Post by reacocard on 2007-02-14
I just fixed the python2.5 libs, although dbus doesn't seem too happy about it. sorcererx84, is there any way I can get your tray icon for inclusion in my packages? There doesn't seem to be any way to get its source from your site. Also, sorry about setting up my own repo, if I had known you already had one, I wouldn't have, but with the 25+ page thread on compiz forums, I didn't have time to read it all and find out.

---

### Post by WinterWeaver on 2007-02-14
OK ... I just killed my screenlets.... can anyone tell me how to fix it??

I basically added a Launcher, and added a icon. But for some reason it cant read the icon. I get this error:
```
Error - failed to load icon "/usr/share/firefox/icons/mozicon128.png"
```

How can I fix this?

EDIT: Forgot to mention... after that error pops up... screelets dont start anymore :(

---

### Post by reacocard on 2007-02-14
> **WinterWeaver said:**
> OK ... I just killed my screenlets.... can anyone tell me how to fix it??

I basically added a Launcher, and added a icon. But for some reason it cant read the icon. I get this error:
```
Error - failed to load icon "/usr/share/firefox/icons/mozicon128.png"
```

How can I fix this?

EDIT: Forgot to mention... after that error pops up... screelets dont start anymore :(

I don't think the launchers can handle PNG files ATM, only SVG. To get rid of the offending screenlet, enter this in a terminal (you can substitute gedit for nano if you like)
```
nano ~/.config/Screenlets/screenletsd.ses
```
and remove the line for the launcher.

---

### Post by WinterWeaver on 2007-02-14
Thanks !!! It worked!

---

### Post by sorcererx84 on 2007-02-15
Hi, reacocard
There's no point of having two different Screenlets packages that provide the same features. 
Maybe we could combine our packages in one and have two mirrors for it?

---

### Post by reacocard on 2007-02-15
> **sorcererx84 said:**
> Hi, reacocard
There's no point of having two different Screenlets packages that provide the same features. 
Maybe we could combine our packages in one and have two mirrors for it?

Good idea. I don't know whether it's possible to have falcon mirror only one component of a repo though. My repo also has sections for AWN, exaile, etc. that we wouldn't want to mirror on yours.

---

### Post by aktiwers on 2007-02-15
Sweet! Thanks!

---

### Post by GQed76 on 2007-02-15
```
gqed76@gqed76-desktop:~$ sudo gedit /usr/local/share/screenlets/screenletsd.py
gqed76@gqed76-desktop:~$ screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
gqed76@gqed76-desktop:~$ CachingBackend: Loading cache ...
Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 493, in ?
    service = ScreenletsService(bus_name)
  File "/usr/local/share/screenlets/screenletsd.py", line 247, in __init__
    self.load_session()
  File "/usr/local/share/screenlets/screenletsd.py", line 317, in load_session
    classname = data[1].replace("\n", "")
IndexError: list index out of range

```

:confused:

---

### Post by Sqwishy on 2007-02-17
@ anyone who's started or made their own screenlet

I'm trying to make me own screenlet but it's not working and i'm wondering if anyone had the same problem.

```
~ % screenletsd add CowFortune
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
add-screenlet-utility | (c) RYX (Rico Pfaus) 2007 | released under GPL
Class CowFortuneScreenlet not found.
```

The py file is under ~/.screenlets and i've tested stuff and the screenletsd thing does check to see if there are screenlets in that folder. But when i copied and started chaning stuff in the example screenlet it won't run, there is a class called CowFortuneScreenlet, and everywhere else its been changed from ExampleScreenlet and stuff. :confused: I'm thinking its because it's using python 2.5 or something...? Does anyone else have or did have this problem?

---

### Post by reacocard on 2007-02-17
If I understand you correctly, it's in ~/.screenlets/CowFortuneScreenlet.py ? It should be in ~/.screenlets/CowFortuneScreenlet/CowFortuneScreenlet.py

---

### Post by Sqwishy on 2007-02-17
> **reacocard said:**
> If I understand you correctly, it's in ~/.screenlets/CowFortuneScreenlet.py ? It should be in ~/.screenlets/CowFortuneScreenlet/CowFortuneScreenlet.py No you mean it should be in ~/.screenlets/CowFortune/CowFortuneScreenlet.py witch it already was.

---

### Post by reacocard on 2007-02-17
> **Sqwishy said:**
> No you mean it should be in ~/.screenlets/CowFortune/CowFortuneScreenlet.py witch it already was.

Yes, you're right. Weird. Could you post your screenlet here?

---

### Post by CaptSaltyJack on 2007-02-17
I'd like to report that screenletsd does not work under Kubuntu apparently.  It complains about missing module rsvg, even though I have all the librsvg stuff installed.  I read somewhere that this is a Gnome dependency?

Anyone know how to fix this?

---

### Post by reacocard on 2007-02-17
> **CaptSaltyJack said:**
> I'd like to report that screenletsd does not work under Kubuntu apparently.  It complains about missing module rsvg, even though I have all the librsvg stuff installed.  I read somewhere that this is a Gnome dependency?

Anyone know how to fix this?

You need to have python-gnome2-desktop installed; that's where the python bindings for librsvg are.

---

### Post by CaptSaltyJack on 2007-02-17
Oh ok..thanks.  Too bad this wasn't in the documentation anywhere.. how are we supposed to know this stuff?

---

### Post by reacocard on 2007-02-17
> **CaptSaltyJack said:**
> Oh ok..thanks.  Too bad this wasn't in the documentation anywhere.. how are we supposed to know this stuff?

Well, it's an 0.0.7 release. If you're using it at this early point, you're pretty much expected to be able to troubleshoot on your own.  Also, keep in mind it's not an Ubuntu-specific app, so special instructions aren't likely to be included.

---

### Post by Sqwishy on 2007-02-18
Here is my screenlet that i'm having issues with. It was located in ~/.screenlets/ It's pretty much the example screenlet but just with some names changed

Edit: It works now! I don't know why but it works now?

---

### Post by Roeler on 2007-02-18
Since I've installed screenlets I can't select beryl as windows manager any more...:-(
Can anyone help me ?

---

### Post by reacocard on 2007-02-18
> **Roeler said:**
> Since I've installed screenlets I can't select beryl as windows manager any more...:-(
Can anyone help me ?

Some more information would help.  How are you trying to start beryl? What happens when you do?  What is the output of running
```
beryl --replace
```
in the terminal?

---

### Post by Roeler on 2007-02-18
> **reacocard said:**
> Some more information would help.  How are you trying to start beryl? What happens when you do?  What is the output of running
```
beryl --replace
```
in the terminal?
I solved the problem by upgrading beryl with the Synaptic Package Manager :-)

Anyway, thanks for your quick reply !

---

### Post by adamJ5 on 2007-02-18
I'm getting black borders around all screenlets, and I got xcompmgr installed. What do I do? :(

---

### Post by delfick on 2007-02-18
> **adamJ5 said:**
> I'm getting black borders around all screenlets, and I got xcompmgr installed. What do I do? :(

in the terminal type "xcompmgr" and pressing enter.... see if that fixes it :D

---

### Post by adamJ5 on 2007-02-19
> **delfick said:**
> in the terminal type "xcompmgr" and pressing enter.... see if that fixes it :D
That gives me 

```
adam@Adam:~$ xcompmgr
No composite extension
```

---

### Post by delfick on 2007-02-19
> **adamJ5 said:**
> That gives me 

```
adam@Adam:~$ xcompmgr
No composite extension
```

i'm not sure, but i'm assuming that means your graphics card isn't set up correctly...

what graphics card do you have ??

---

### Post by adamJ5 on 2007-02-19
> **delfick said:**
> i'm not sure, but i'm assuming that means your graphics card isn't set up correctly...

what graphics card do you have ??

I got a Nvidia GeForce 6200

---

### Post by anaconda on 2007-02-19
Cool.. execpt that When I open eg. firefor it goes UNDER the clock I added!!!

---

### Post by delfick on 2007-02-19
> **adamJ5 said:**
> I got a Nvidia GeForce 6200

k then, try this (taken from here [http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#An_automatic_easy_solution_for_.28almost.29_all_problems](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#An_automatic_easy_solution_for_.28almost.29_all_problems) )

> Open a terminal and type:

```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig;
 sudo nvidia-xconfig -composite; sudo nvidia-xconfig -allow-glx-with-composite
 sudo nvidia-xconfig -render-accel; sudo nvidia-xconfig -add-argb-glx-visuals
```

Note: nvidia-xconfig is installed together with the NVidia Drivers when using the NVidia installer.

Now press Ctrl+Alt+Backspace to restart X. After doing this, you should have nVidia drivers perfectly installed and configured. But, if you have problems and X doesn't starts, type this to restore the original xorg.conf:

```
 sudo mv /etc/X11/xorg.conf.orig /etc/X11/xorg.conf
 startx
```

---

### Post by delfick on 2007-02-19
> **anaconda said:**
> Cool.. execpt that When I open eg. firefor it goes UNDER the clock I added!!!

right click on the clock, choose properties and and choose wether to have the clock "keep above", "keep below" or neither... :D (see attached screenshot...)

---

### Post by Icarus3000 on 2007-02-26
> **delfick said:**
> right click on the clock, choose properties and and choose wether to have the clock "keep above", "keep below" or neither... :D (see attached screenshot...)

OFFTOPIC:  What beryl theme are you using?  I have been looking for something with transparent borders but also has many buttons like yours does.

---

### Post by delfick on 2007-02-26
> **Icarus3000 said:**
> OFFTOPIC:  What **emerald** theme are you using?  I have been looking for something with transparent borders but also has many buttons like yours does.

[http://delfick755.googlepages.com/Bigframe_legacy.emerald](http://delfick755.googlepages.com/Bigframe_legacy.emerald)

the buttons are based on Vista (if that already wasn't obvious :D) and were made in the days of the old beryl forums :D
(this theme only really looks good with some kind of border blur ...)

---

### Post by emid on 2007-03-08
Does anyone know how I would:

1. Find additional screenlets? I downloaded the package but it doesn't have the weather or calender screenlets.

2. Make it so it is like OSX dashboard (not visible all the time).  Do I need a Beryl plugin for that to happen?

I also added the availiable repo to my sources.list but when I proceeded to "apt-get install"  it wanted to install compiz.  Is this an issue if I am currently using Beryl?

Sorry if these are obvious questions, I've been reading various threads, but some are so long I can't find what I'm looking for.  If anyone can help it would be awesome.

---

### Post by reacocard on 2007-03-08
> **emid said:**
> Does anyone know how I would:

1. Find additional screenlets? I downloaded the package but it doesn't have the weather or calender screenlets.

2. Make it so it is like OSX dashboard (not visible all the time).  Do I need a Beryl plugin for that to happen?

I also added the availiable repo to my sources.list but when I proceeded to "apt-get install"  it wanted to install compiz.  Is this an issue if I am currently using Beryl?

Sorry if these are obvious questions, I've been reading various threads, but some are so long I can't find what I'm looking for.  If anyone can help it would be awesome.

I would recommend using [my repo]("http://syzygy42.tuxfamily.org/dists/edgy/screenlets/") for getting screenlets.

To use it, add
```
deb http://download.tuxfamily.org/syzygy42 edgy screenlets
deb-src http://download.tuxfamily.org/syzygy42 edgy screenlets
```
to your sources.list, then do
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
sudo apt-get update
```

There are currently three packages in my repo:
screenlets - the engine and official screenlets
screenlets-extras - unofficial screenlets, including Weather and Calendar
beryl-widget-plugin - adds dashboard-like capabilities to beryl/screenlets.

To get them all do
```
sudo apt-get install screenlets screenlets-extras beryl-widget-plugin
```

---

### Post by emid on 2007-03-08
Thanks for replying.  I'm getting an error when I try to update my sources.  I think it's because I'm running 64bit and it can't find those packages in your repo.  Any suggestions as to what I should do?

---

### Post by reacocard on 2007-03-11
> **emid said:**
> Thanks for replying.  I'm getting an error when I try to update my sources.  I think it's because I'm running 64bit and it can't find those packages in your repo.  Any suggestions as to what I should do?

There aren't any 64-bit packages in my repo, as I do not have a 64-bit computer available to build them on (If someone wants to contribute 64-bit packages, I'd be happy to add them). You should probably just download the sources and install them yourself. It's easy for screenlets. Download, extract, then from a terminal in the folder you just extracted do

```
python ./setup.py build
sudo python ./setup.py install
```

---

### Post by emid on 2007-03-11
Yeah, that's what I ended up doing.  I had some issues getting the beryl-widget-plugin installed though.  Do you have any advice on how I would get that properly installed?

Thanks for the help, I appreciate it.

---

### Post by reacocard on 2007-03-11
> **emid said:**
> Yeah, that's what I ended up doing.  I had some issues getting the beryl-widget-plugin installed though.  Do you have any advice on how I would get that properly installed?

Thanks for the help, I appreciate it.

install beryl-dev and build-essential, then download and compile the source with make/make install.

---

### Post by emid on 2007-03-11
> **reacocard said:**
> install beryl-dev and build-essential, then download and compile the source with make/make install.

When I try to install it I get the following:

nothing to build
mkdir -p /usr/lib/beryl/
install -m 644 libwidget.so /usr/lib/beryl/

Also, if the installation is successful, where would it show up in the Beryl Setting Manager?  I'm assuming in the Extras area, but I don't really know.

---

### Post by reacocard on 2007-03-11
> **emid said:**
> When I try to install it I get the following:

nothing to build
mkdir -p /usr/lib/beryl/
install -m 644 libwidget.so /usr/lib/beryl/

Also, if the installation is successful, where would it show up in the Beryl Setting Manager?  I'm assuming in the Extras area, but I don't really know.

Where are you getting that source from? If it's from my repo, it's no good. I had to hack up the Makefile to get it into the deb, so it doesn't build anymore. If it has a Makefile-old still, use that instead. 

It shows up under Desktop, not extras.

---

### Post by Takmadeus on 2007-03-11
do these screenletrs work in gnome without beryl?

why not add them to the main repos?

---

### Post by FuturePilot on 2007-03-11
I'm trying to build these from source and then when I try to run them I keep getting this```
 Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 46, in ?
    import screenlets
  File "/usr/lib/python2.4/site-packages/screenlets/__init__.py", line 34, in ?
    import rsvg
ImportError: No module named rsvg

```
Did I do something wrong when building them?

---

### Post by reacocard on 2007-03-11
> **Takmadeus said:**
> do these screenletrs work in gnome without beryl?

why not add them to the main repos?

They do not depend on beryl exclusively, but they do need a compositor (eg.beryl,compiz,xcompmgr). 

> **FuturePilot said:**
> I'm trying to build these from source and then when I try to run them I keep getting this```
 Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 46, in ?
    import screenlets
  File "/usr/lib/python2.4/site-packages/screenlets/__init__.py", line 34, in ?
    import rsvg
ImportError: No module named rsvg

```
Did I do something wrong when building them?

You're not doing anything wrong. Just install python-gnome2-desktop.

---

### Post by FuturePilot on 2007-03-11
I do have python-gnome2-desktop installed, but I just did a Google on this and apparently these won't work on Dapper because the gnome is too old. My desktop is still running Dapper, I'm waiting for Feisty to be released before I do anything with it since it's the family computer and I really don't want to mess anything up since others need to use it. That's what my laptop is for:lolflag: 

Thanks anyways.:)

---

### Post by FuturePilot on 2007-03-11
Well I tried it on Feisty but I'm getting this
```
No handlers could be found for logger "dbus.proxies"
Error: screenlets-Backend (screenletsd) not found
```

---

### Post by FuturePilot on 2007-03-11
Ok tried it in Edgy and it's all working good:)  These things are cool. Is there any more screenlets I can download? 
I wonder why it only works on Edgy?

---

### Post by Takmadeus on 2007-03-12
> They do not depend on beryl exclusively, but they do need a compositor (eg.beryl,compiz,xcompmgr). 

awww man, no composite manager works with my video card (radeon 9200)

guess there's nothing to do :(

---

### Post by jincast90 on 2007-03-12
> **Takmadeus said:**
> awww man, no composite manager works with my video card (radeon 9200)

guess there's nothing to do :(

I know the feeling. It sucks having a radeon 9200.

---

### Post by reacocard on 2007-03-12
> **FuturePilot said:**
> Ok tried it in Edgy and it's all working good:)  These things are cool. Is there any more screenlets I can download? 
I wonder why it only works on Edgy?

I've attached a tarball of all the additional screenlets I know of.

Also for edgy, you could just use my repo instead, which has a screenets-extras package for all the unofficial screenlets.

It works best on edgy, because edgy uses python 2.4, while feisty uses 2.5, which apparently makes screenlets and dbus hate each other.

---

### Post by sorcererx84 on 2007-03-12
Amd64 package is [here]("http://hendrik.kaju.pri.ee/ubuntu/pool/edgy/screenlets/screenlets-0.0.7-7pre0.0.8_amd64.deb").
Add ```
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) edgy screenlets
``` to get the repo.

---

### Post by FuturePilot on 2007-03-12
> **reacocard said:**
> I've attached a tarball of all the additional screenlets I know of.

Also for edgy, you could just use my repo instead, which has a screenets-extras package for all the unofficial screenlets.

It works best on edgy, because edgy uses python 2.4, while feisty uses 2.5, which apparently makes screenlets and dbus hate each other.

Hey thanks! I love these things:)

---

### Post by garybrlow on 2007-03-12
> **FuturePilot said:**
> Well I tried it on Feisty but I'm getting this
```
No handlers could be found for logger "dbus.proxies"
Error: screenlets-Backend (screenletsd) not found
```

Has anyone successfully made it work on feisty?


Cheers!!!


GaryBrlow :biggrin:

---

### Post by Paulus on 2007-03-14
you can just launch each screenlet manually in fiesty; no need to use the control screenlet or the tray.

just cd to the theme directory and launch

**e.g**
```
paulus@paulus-desktop:~/Desktop/screenlets-0.0.7/src/share/screenlets/Clock$ ./ClockScreenlet.py 

```

[[IMG]http://img458.imageshack.us/img458/9839/screenshotwh8.th.png[/IMG]](http://img458.imageshack.us/my.php?image=screenshotwh8.png)

---

### Post by DJ_Peng on 2007-03-14
> **reacocard said:**
> 
beryl-widget-plugin - adds dashboard-like capabilities to beryl/screenlets.

I tried to install this but It only works with the latest version of beryl-core and I rolled my Beryl install back to 0.1.99.2 due to some WSOD issues with my install (Edgy, Nvidia GeFirce2 MX 100, drivers from Automatix). Is there a work around I could use that would keep me away from the WSOD?

Thanks for posting your package, reacocard. With your Weather and Calendar screenlets I was able to ditch the gDesklets completely.

I do have one other question. Is there a way to edit the launchers on the basic Control screenlet? Since I use the Firefox build from Mozilla I'd like to change the Firefox link provided.

---

### Post by reacocard on 2007-03-14
> **DJ_Peng said:**
> I tried to install this but It only works with the latest version of beryl-core and I rolled my Beryl install back to 0.1.99.2 due to some WSOD issues with my install (Edgy, Nvidia GeFirce2 MX 100, drivers from Automatix). Is there a work around I could use that would keep me away from the WSOD?

Yes, if you're willing to compile it yourself. I'm attaching the tar.gz of it. The only dependencies you'll need are beryl-dev and build-essential, and then just use make && make install (no sudo, just normal. yes it's weird, and a pure PITA to package as well). Once you're done installing, it's safe to remove those two packages (and their dependencies), they're only needed to build it, not to use it.

> I do have one other question. Is there a way to edit the launchers on the basic Control screenlet? Since I use the Firefox build from Mozilla I'd like to change the Firefox link provided.
Sure. Just edit /usr/local/share/screenlets/Control/menu.xml to whatever you need. Back up the file once you're done, as whenever there's an update it'll wipe out your changes to that file.

---

### Post by DJ_Peng on 2007-03-14
Sweet. I'll grab the file and compile it. As far as the menu is concerned I had already found the file to edit. Talk about easy! I also seem to have needed to get out of Screenlets and start it again for the change to show up. Thanks for the tip about backing it up. I wouldn't have known about the overwriting until it was too late.

---

### Post by DJ_Peng on 2007-03-14
I saw that Beryl 0.2.0 came out today and was able to get it and the plugin installed without having to compile anbything. Now I just have to scroll back through the topic and see how to use it.

---

### Post by sorcererx84 on 2007-03-15
Paulus: This way each screenlet will take about 20 megs of memory :(

---

### Post by DJ_Peng on 2007-03-15
I created a Screemlet Launcher but it can't load the icon I specified and now it takes down all of Screenlets. Can someone tell me how I can delete the offending launcher?

---

### Post by reacocard on 2007-03-15
> **DJ_Peng said:**
> I created a Screemlet Launcher but it can't load the icon I specified and now it takes down all of Screenlets. Can someone tell me how I can delete the offending launcher?

Edit ~/.config/Screenlets/screenletsd.ses and remove its line.

---

### Post by DJ_Peng on 2007-03-15
I found hat with the help of the guys on the program's main forum. yes, I was impatient. I didn't know how much I loved it until I couldn't run it. I got it fixed though. I think I'll just keep the launcher I creadted on the Control screenlet for now, or else be a lot more careful when I create a launcher. Thanks for the response, tho.

---

### Post by shingalated on 2007-03-15
I can't for the life of me get these screenlets to work.  I have tried compiling it several different ways, none of which have worked, and I also tried several different packages, one even gives me a nice GUI with a tray icon, but whenever I try to run it I get:
```
chris@Linus:~$ Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 48, in ?
    import screenlets
  File "/usr/lib/python2.4/site-packages/screenlets/__init__.py", line 34, in ?
    import rsvg
ImportError: No module named rsvg

```
I am running Edgy, and I have installed every possible package that I even think may be related to "rsvg"  (python-gnome2-desktop libimage-librsvg-perl librsvg2-2 librsvg2-bin librsvg2-common librsvg2-dev librsvg2-ruby.......etc/ etc/)  All are installed and up to date.  Can anyone help?

---

### Post by 8bit on 2007-03-15
> **RYX said:**
> Hi everybody! 

I am RYX, the author of the screenlets. I have been registered since a few years (for whatever reason) but never made a single post. So hello everyone, this is my first post :) ...

I just wanted to note that the Screenlets have absolutely nothing in common with superkaramba and/or gdesklets. Screenlets have an entirely different architecture and are, basically, stand-alone applications - not plugins or some XML-based pseudo-language theme to some binary app. Instead, Screenlets have theming-support to allow each screenlet to have an unlimited number of totally different designs.

Screenlets are fully-featured gtk-applications written in python. The Screenlet-superclass handles and simplifies a lot of rather complicated stuff and the Screenlet-subclasses (the things called "screenlets") can concentrate on being useful and good-looking ... 

I am no friend of calling them beryl-/compiz-"widgets" because they are a separate application and also work with xfwm4's compositing-mode or even xcompmgr.

So after giving my two cents, I am happy to announce that a 0.0.7 version has been released. [Get it while it's still fresh]("http://forum.go-compiz.org/viewtopic.php?t=358") :D

EDIT: And delfick - thank you a thousand times for promoting the screenlets so well :D :D :D ...

best regards

RYX

[SIZE="7"]God Bless You !!!![/SIZE]
I was so sick of gDesklets I could puke!

---

### Post by reacocard on 2007-03-15
> **shingalated said:**
> I can't for the life of me get these screenlets to work.  I have tried compiling it several different ways, none of which have worked, and I also tried several different packages, one even gives me a nice GUI with a tray icon, but whenever I try to run it I get:
```
chris@Linus:~$ Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 48, in ?
    import screenlets
  File "/usr/lib/python2.4/site-packages/screenlets/__init__.py", line 34, in ?
    import rsvg
ImportError: No module named rsvg

```
I am running Edgy, and I have installed every possible package that I even think may be related to "rsvg"  (python-gnome2-desktop libimage-librsvg-perl librsvg2-2 librsvg2-bin librsvg2-common librsvg2-dev librsvg2-ruby.......etc/ etc/)  All are installed and up to date.  Can anyone help?

You need the python bindings for rsvg, which are (oddly) in python-gnome2-desktop.

---

### Post by 8bit on 2007-03-15
I installed it fine and was able to get the calendar and weather screenlet working but when I added the mail check, every time I start screenlets, I can no longer configure the screenlets.

I have beryl installed but not running btw with edgy installed. I also don't have transparent backgrounds.

Any ideas.

Again, what a breath of fresh air. Running gDesklets was like using an app for Windows 95.

Thank you!!

---

### Post by progrockusa on 2007-03-16
does this app perform like a dashboard?
i'm looking for something that performs like gDesklets but plays better with beryl

---

### Post by reacocard on 2007-03-16
> **progrockusa said:**
> does this app perform like a dashboard?
i'm looking for something that performs like gDesklets but plays better with beryl

Yes, with the beryl widget plugin enabled, it's extremely similar to dashboard.

---

### Post by shingalated on 2007-03-16
> **reacocard said:**
> You need the python bindings for rsvg, which are (oddly) in python-gnome2-desktop.

I have already installed python-gnome2-desktop, but still get the same error
chris@Linus:~$ sudo apt-get install python-gnome2-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gnome2-desktop is already the newest version.

---

### Post by 8bit on 2007-03-16
> **8bit said:**
> I installed it fine and was able to get the calendar and weather screenlet working but when I added the mail check, every time I start screenlets, I can no longer configure the screenlets.

I have beryl installed but not running btw with edgy installed. I also don't have transparent backgrounds.

Any ideas.

Again, what a breath of fresh air. Running gDesklets was like using an app for Windows 95.

Thank you!!

Ok, I got beryl working after upgrading to Edgy from Dapper. Beryl is working nicely and my screenlets load but I can't configure them. I can't move them, nothing. I stopped the screenlets process. Now I can't add any desklets. I get the error of

```
user@linuxbox:/usr/local/share/screenlets$ /usr/local/share/screenlets/add-screenlet.py Weather
add-screenlet-utility | (c) RYX (Rico Pfaus) 2007 | released under GPL
Introspect error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Error: Screenlets-Backend (screenletsd) not found.

```

screenletsd is running so I'm not sure what's happening. Now that I'm running beryl again, the black borders are gone.

---

### Post by 8bit on 2007-03-16
I get the same error as above for all screenlets. FYI

---

### Post by 8bit on 2007-03-17
Ok, I forgot to install the beryl-widget package. I installed it and rebooted but I still have the same problem.

Help!  I really want to get these up and running.

---

### Post by reacocard on 2007-03-17
> **8bit said:**
> Ok, I forgot to install the beryl-widget package. I installed it and rebooted but I still have the same problem.

Help!  I really want to get these up and running.

Use 'screenletsd add Weather' to add it, not add-screenlet.py. Every command you give to screenlets should be through screenletsd.

---

### Post by mand0 on 2007-03-17
These screenlets are great. Thanks for your effort RYX.

I hope that in the future there will be a 'screenlets' section in websites like gnome-looks where we can download new content.

---

### Post by 8bit on 2007-03-17
> **reacocard said:**
> Use 'screenletsd add Weather' to add it, not add-screenlet.py. Every command you give to screenlets should be through screenletsd.

Thanks for the quick resonse!!

I'm still getting this error after a brief pause:
```

user@linuxbox:~$ screenletsd add /usr/local/share/screenlets/Clock
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
add-screenlet-utility | (c) RYX (Rico Pfaus) 2007 | released under GPL
Introspect error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Error: Screenlets-Backend (screenletsd) not found.
```

I want to get these working so bad I can taste them!

---

### Post by reacocard on 2007-03-17
> **8bit said:**
> Thanks for the quick resonse!!

I'm still getting this error after a brief pause:
```

user@linuxbox:~$ screenletsd add /usr/local/share/screenlets/Clock
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
add-screenlet-utility | (c) RYX (Rico Pfaus) 2007 | released under GPL
Introspect error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Error: Screenlets-Backend (screenletsd) not found.
```

I want to get these working so bad I can taste them!

Weird. screenletsd is already running right? (screenletsd start) It seems it's not finding the screenlets daemon over dbus. Make sure you have python-dbus installed and dbus is running.

---

### Post by shingalated on 2007-03-17
> **shingalated said:**
> I have already installed python-gnome2-desktop, but still get the same error
chris@Linus:~$ sudo apt-get install python-gnome2-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gnome2-desktop is already the newest version.


Is there another way to get the rsvg python bindings installed?  The python-gnome2-desktop package doesn't seem to be doing it.  Please help I, I desperately need a gDesklets replacement....SO ugly

---

### Post by 8bit on 2007-03-17
> **reacocard said:**
> Weird. screenletsd is already running right? (screenletsd start) It seems it's not finding the screenlets daemon over dbus. Make sure you have python-dbus installed and dbus is running.

dbus launch and dbus daemon are running. Also, screenletsd has been started and is running.

I don't see screenletsd in the system monitor but if I try to start it, it tells me that it's running.

---

### Post by mustiy on 2007-03-17
I have the same problem, i'll explain.

When i first installed Screenlets i added a few widgets (sticky notes, weather, launcher), played and configured them no problem. Beryl and Screenlets worked great together with no problems.

My problems started when i installed the "mailcheck" widget, it crashes Screenlets. 

Terminal output: 

Connecting to POP3-server ... please wait.
Connecting to POP3-server ... please wait.

From here i get a error window saying "error while connecting to server" if you press "ok" it halts Screenlets and all the other widgets become black and wou cannot configure them.

I tried to uninstall and then reinstall but it seems like it remembers which widgets you added somehow - how can i completely uninstall Screenlets and start from scratch without adding the "checkmail" widget? I tried everything :(

---

### Post by reacocard on 2007-03-17
> **mustiy said:**
> I have the same problem, i'll explain.

When i first installed Screenlets i added a few widgets (sticky notes, weather, launcher), played and configured them no problem. Beryl and Screenlets worked great together with no problems.

My problems started when i installed the "mailcheck" widget, it crashes Screenlets. 

Terminal output: 

Connecting to POP3-server ... please wait.
Connecting to POP3-server ... please wait.

From here i get a error window saying "error while connecting to server" if you press "ok" it halts Screenlets and all the other widgets become black and wou cannot configure them.

I tried to uninstall and then reinstall but it seems like it remembers which widgets you added somehow - how can i completely uninstall Screenlets and start from scratch without adding the "checkmail" widget? I tried everything :(

No need to be so drastic. Just do
```
rm -rf ~/config/Screenlets
```
to reset its settings.

---

### Post by mustiy on 2007-03-17
> **reacocard said:**
> No need to be so drastic. Just do
```
rm -rf ~/config/Screenlets
```
to reset its settings.

I tried what you suggested and i still have the problem with the mailcheck widget (yes it loads 2 of them).

> user@user-desktop:~$ rm -rf ~/config/Screenlets
user@user-desktop:~$ screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
mustiy@mustiy-desktop:~$ CachingBackend: Loading cache ...
CachingBackend: Loading <pfRbsAi92H0DfSxq>
CachingBackend: Loading <jI4CltugvK7RxJl9>
CachingBackend: Loading <6T3e805Yc5fO1TBf>
CachingBackend: Loading <J1Ab6tNcf46IaxjG>
CachingBackend: Loading <FsdjggQsfFKRioAO>
CachingBackend: Loading <QoUTFQjEpcfqnLVL>
CachingBackend: Loading <VvyxdbkoQN1yh5YM>
CachingBackend: Loading <DakNKsRKw63QOt0i>
Restore: <NotesScreenlet#QoUTFQjEpcfqnLVL>
import_and_create_screenlet: NotesScreenlet
Restore: <ControlScreenlet#DakNKsRKw63QOt0i>
import_and_create_screenlet: ControlScreenlet
Restore: <CalendarScreenlet#jI4CltugvK7RxJl9>
import_and_create_screenlet: CalendarScreenlet
Restore: <MailCheckScreenlet#VvyxdbkoQN1yh5YM>
import_and_create_screenlet: MailCheckScreenlet
Restore: <MailCheckScreenlet#FsdjggQsfFKRioAO>
import_and_create_screenlet: MailCheckScreenlet
Restore: <ControlScreenlet#pfRbsAi92H0DfSxq>
import_and_create_screenlet: ControlScreenlet
Restore: <LauncherScreenlet#J1Ab6tNcf46IaxjG>
import_and_create_screenlet: LauncherScreenlet
Restore: <CPUMeterScreenlet#6T3e805Yc5fO1TBf>
import_and_create_screenlet: CPUMeterScreenlet
Connecting to POP3-server ... please wait.
Connecting to POP3-server ... please wait.


As you can see the last 2 lines is where it hangs, is there a Screenlet command line to remove widgets? Much like screenlets add widgetame, but to remove...

---

### Post by reacocard on 2007-03-17
> **mustiy said:**
> I tried what you suggested and i still have the problem with the mailcheck widget (yes it loads 2 of them).



As you can see the last 2 lines is where it hangs, is there a Screenlet command line to remove widgets? Much like screenlets add widgetame, but to remove...

Ooops. I had a typo in the command. :oops:  Here's the correct one:
```
rm -rf ~/.config/Screenlets
```

---

### Post by 8bit on 2007-03-17
I tried your suggestion but still no luck. Come to think of it, I started having problems after running the MailCheck screenlet as well.

Same old error:

```
user@linuxbox:~$ screenletsd add Weather
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
add-screenlet-utility | (c) RYX (Rico Pfaus) 2007 | released under GPL
Introspect error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Error: Screenlets-Backend (screenletsd) not found.

```

---

### Post by hanzomon4 on 2007-03-17
> **8bit said:**
> dbus launch and dbus daemon are running. Also, screenletsd has been started and is running.

I don't see screenletsd in the system monitor but if I try to start it, it tells me that it's running.

I feel your pain, back in compiz-quinn days compiz would fail on login due to a dbus error. Everyone said that I must not have dbus running but I checked and dbus-daemon  and dbus-launch were both running. 

I still have problems with some apps not being able to connect with dbus(deskbar), but yeah... just thought I'd chime in.

---

### Post by 8bit on 2007-03-17
> **hanzomon4 said:**
> I feel your pain, back in compiz-quinn days compiz would fail on login due to a dbus error. Everyone said that I must not have dbus running but I checked and dbus-daemon  and dbus-launch were both running. 

I still have problems with some apps not being able to connect with dbus(deskbar), but yeah... just thought I'd chime in.

What's weird is that when I first installed screenlets I was not running beryl but had it installed. Screenlets worked but I they had a black border around them. I added Weather, CPU then MailCheck. Things started acting funning after that. I could no longer set the properties on my screenlets

So I set Beryl back up and my screenlets would load without the black border but I still couldn't set the properties to them. I couldn't move them, etc. Now they won't even load.

I hope there is a solution our there.

---

### Post by mustiy on 2007-03-17
> **reacocard said:**
> Ooops. I had a typo in the command. :oops:  Here's the correct one:
```
rm -rf ~/.config/Screenlets
```


Worked like a charm, thanks.

---

### Post by mustiy on 2007-03-17
> **8bit said:**
> What's weird is that when I first installed screenlets I was not running beryl but had it installed. Screenlets worked but I they had a black border around them. I added Weather, CPU then MailCheck. Things started acting funning after that. I could no longer set the properties on my screenlets

So I set Beryl back up and my screenlets would load without the black border but I still couldn't set the properties to them. I couldn't move them, etc. Now they won't even load.

I hope there is a solution our there.

Try uninstalling Screenlets, and then reinstallaing - upon launching it again (after the reinstall) type in the command above to reconfigure and it should be fine?

---

### Post by hanzomon4 on 2007-03-17
Checkout rxy's thread on the compiz forums, last time I checked this was still pretty early in the development. 
What happens when you launch them from the command line? ```
 screenletsd start
``` ```
screenletsd add Control
```


Mine work but your results may very

---

### Post by 8bit on 2007-03-18
IT WORKED!!!!

I uninstalled screenlets then removed the config info. I then rebooted my machine since I couldn't see screenletsd running. After rebooting I ran screenletsd start, it created the .confg folder then I added Weather and bamm! I'm golden!

Thanks a million everyone!!!! These things are sweet.

---

### Post by garybrlow on 2007-03-18
Newer version now works in Feisty. Its still buggy as the author claims but its awesome. Mail plug-in crashes the whole thing, it connects to an unset default pop server on load and hangs itself and the other screenlets. Anyone know how to manually remove a particular sceenlet using the terminal or other manual methods whilst the screenletsd isn't running?

Cheers!!!


GaryBrlow :biggrin:

---

### Post by reacocard on 2007-03-18
> **garybrlow said:**
> Newer version now works in Feisty. Its still buggy as the author claims but its awesome. Mail plug-in crashes the whole thing, it connects to an unset default pop server on load and hangs itself and the other screenlets. Anyone know how to manually remove a particular screenlet using the terminal or other manual methods whilst the screenletsd isn't running?

You can do that by removing its line in ~/.config/Screenlets/screenletsd.ses

---

### Post by rjcsc on 2007-03-18
> **GQed76 said:**
> ```
gqed76@gqed76-desktop:~$ sudo gedit /usr/local/share/screenlets/screenletsd.py
gqed76@gqed76-desktop:~$ screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
gqed76@gqed76-desktop:~$ CachingBackend: Loading cache ...
Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 493, in ?
    service = ScreenletsService(bus_name)
  File "/usr/local/share/screenlets/screenletsd.py", line 247, in __init__
    self.load_session()
  File "/usr/local/share/screenlets/screenletsd.py", line 317, in load_session
    classname = data[1].replace("\n", "")
IndexError: list index out of range

```

:confused:

I have this error too. Any Ideas?

---

### Post by BOBSONATOR on 2007-04-02
Does anyone have a monster deb or package of this with all of the latest add-ons?(weather ect)

i have trev's repo installed and i still get the basic packages.

nvm

just do a 

```
sudo apt-get install screenlets-extras
```

---

### Post by Tatty on 2007-04-02
This looks exciting, is there a Feisty repo yet?

---

### Post by reacocard on 2007-04-02
> **Tatty said:**
> This looks exciting, is there a Feisty repo yet?

No, but the install is really easy. Just extract it, open a terminal and do 'sudo python ./setup.py install'. No extra software required, Ubuntu has everything you need already, if you're using Gnome.

I'll upgrade my repo to feisty after I upgrade myself, probably within a week of its release. So if you can wait, there will be one. Actually, the edgy repo might work on feisty anyway, since it's a pure python program, but no guarantees.

---

### Post by jariku on 2007-04-03
I used the repo mentioned here: [http://www.go-compiz.org/index.php?title=Desktop_Screenlets](http://www.go-compiz.org/index.php?title=Desktop_Screenlets)

Everything seems to be working fine.

---

### Post by Spike-X on 2007-04-09
How do I find out what non-US ZIP code to enter in teh Weather screenlet? I'm in Geelong, Victoria, Australia. Postcode 3220.

---

### Post by mrgnash on 2007-04-09
I'm using Feisty and neither the Control or invidual-adding methods work for me.

---

### Post by Paulus on 2007-04-09
> **Spike-X said:**
> How do I find out what non-US ZIP code to enter in teh Weather screenlet? I'm in Geelong, Victoria, Australia. Postcode 3220.

I think you need to goto weather.com and search for your area- click on it then look at the url which will contain the code you need.

---

### Post by cbudden on 2007-04-09
> **Paulus said:**
> I think you need to goto weather.com and search for your area- click on it then look at the url which will contain the code you need.

[http://www.weather.com/outlook/travel/businesstraveler/local/ASXX0043?from=search_city](http://www.weather.com/outlook/travel/businesstraveler/local/ASXX0043?from=search_city) is the link, with the code ASXX0043

---

### Post by sorcererx84 on 2007-04-12
Feisty repository is [here]("http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/screenlets/") :D

---

### Post by cbudden on 2007-04-12
Hello.

I'm using Feisty, and when I try to launch screenlets, i'm now getting this error as of Thursday 12th April.

```

screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
cbudden@cbudden-laptop:~$ Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 491, in <module>
    session_bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 669, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 293, in __new__
    mainloop=mainloop)
dbus.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-heA6RIk6Tx: Connection refused

```

---

### Post by Spike-X on 2007-04-21
> **Paulus said:**
> I think you need to goto weather.com and search for your area- click on it then look at the url which will contain the code you need.

That worked, thanks!

---

### Post by pnhers on 2007-04-24
Sorry if already posted and for my bad English :P

I have made a dirty hack (using Beryl) to use the screenlets just like in macOs. By pressing a button it will show up and by pressing the button again it will disappear .

create a new file in the /home/*username*/ named for example screenletsStartStop
put the next code in the file:

```
#!/bin/sh

# check daemon already started
ps -ef | grep -v grep | grep screenletsd
# if not found - equals to 1, start it
if [ $? -eq 1 ]
then
screenletsd start
else
screenletsd stop
fi
```

Make sure the file is executable chmod +x ~/screenletsStartStop

1. Go to: beryl configurationscreen.
2. Open an new command by general options -> commands .
3. Add the next line in the input field: /home/*username*/screenletsStartStop
4. Go to: shortcuts -> keyboard & mouse -> General Options -> Commands.
5. add a new shortcut (for example F10) to the command referents to command-number you just added at step 3

now by pressing you're selected key, screenletsd will start en by pressing again it stops.

---

### Post by DJ_Peng on 2007-04-24
My Update Manager (Feisty) tells me that there's an update for screenlets-extra but there's no information on exactly what is being updated. Can anyone provide a little 411 on the update?

---

### Post by reacocard on 2007-04-24
> **pnhers said:**
> Sorry if already posted and for my bad English :P

I have made a dirty hack (using Beryl) to use the screenlets just like in macOs. By pressing a button it will show up and by pressing the button again it will disappear .

create a new file in the /home/*username*/ named for example screenletsStartStop
put the next code in the file:

```
#!/bin/sh

# check daemon already started
ps -ef | grep -v grep | grep screenletsd
# if not found - equals to 1, start it
if [ $? -eq 1 ]
then
screenletsd start
else
screenletsd stop
fi
```

Make sure the file is executable chmod +x ~/screenletsStartStop

1. Go to: beryl configurationscreen.
2. Open an new command by general options -> commands .
3. Add the next line in the input field: /home/*username*/screenletsStartStop
4. Go to: shortcuts -> keyboard & mouse -> General Options -> Commands.
5. add a new shortcut (for example F10) to the command referents to command-number you just added at step 3

now by pressing you're selected key, screenletsd will start en by pressing again it stops.

Or you could just use the widget plugin. ;)

Packages:
Feisty (for Beryl from Universe): [http://download.tuxfamily.org/syzygy42/pool/feisty/reacocard/beryl-widget-plugin_0.1-2_i386.deb](http://download.tuxfamily.org/syzygy42/pool/feisty/reacocard/beryl-widget-plugin_0.1-2_i386.deb)
Edgy (for Beryl 0.2.0 from repo): [http://download.tuxfamily.org/syzygy42/pool/edgy/screenlets/beryl-widget-plugin_0.1-2_i386.deb](http://download.tuxfamily.org/syzygy42/pool/edgy/screenlets/beryl-widget-plugin_0.1-2_i386.deb)

Source tarball: [http://download.tuxfamily.org/syzygy42/static/misc/beryl-widget.tar.gz](http://download.tuxfamily.org/syzygy42/static/misc/beryl-widget.tar.gz)

---

### Post by russell.h on 2007-04-24
> **reacocard said:**
> Or you could just use the widget plugin. ;)

Packages:
Feisty (for Beryl from Universe): [http://download.tuxfamily.org/syzygy42/pool/feisty/reacocard/beryl-widget-plugin_0.1-2_i386.deb](http://download.tuxfamily.org/syzygy42/pool/feisty/reacocard/beryl-widget-plugin_0.1-2_i386.deb)
Edgy (for Beryl 0.2.0 from repo): [http://download.tuxfamily.org/syzygy42/pool/edgy/screenlets/beryl-widget-plugin_0.1-2_i386.deb](http://download.tuxfamily.org/syzygy42/pool/edgy/screenlets/beryl-widget-plugin_0.1-2_i386.deb)

Source tarball: [http://download.tuxfamily.org/syzygy42/static/misc/beryl-widget.tar.gz](http://download.tuxfamily.org/syzygy42/static/misc/beryl-widget.tar.gz)

How do I enable this thing?

---

### Post by reacocard on 2007-04-24
> **russell.h said:**
> How do I enable this thing?

Just install it and then use the Beryl Settings Manager to enable the 'Widget Layer' plugin under Desktop. You can then map the widget layer to a shortcut or a screen corner (I think lower-left is default). Then just check the 'Treat as Widget' option in a screenlet's properties to send it to the widget layer, and press whatever you mapped the widget layer to to access it.

Here's a youtube video I made demostrating this, among other things: [http://www.youtube.com/watch?v=aLLlvlHoveU](http://www.youtube.com/watch?v=aLLlvlHoveU)
Sorry about the poor quality, youtube's resizer wasn't kind on it. The original MPEG is available here: [http://download.tuxfamily.org/syzygy42/static/desktop_demo_avant_affinity_screenlets.mpg](http://download.tuxfamily.org/syzygy42/static/desktop_demo_avant_affinity_screenlets.mpg)

---

### Post by FuturePilot on 2007-04-24
Beryl Settings Manager>Extras>Widgets or something like that. Then right click on a screenlet to set it to behave as Widgets (Note: when you do that they will disappear, this is normal) so then when you move your mouse to a corner of the screen your screenlets will appear.

---

### Post by russell.h on 2007-04-25
Anyone know where I can get a .deb for 64 bit Feisty? I'm looking into compiling it myself, but it doesnt have a configuration script so I'm having troubles with dependencies.

Edit: Oh, and --force-architecture had some strange results, one of which doesn't seem to have been a working installation (depending on where you look it might be installed, but it doesn't work).

---

### Post by graabein on 2007-04-25
Can I have more than one clock and show different timezones on them? I have a couple friends in different timezones so that would be great.

---

### Post by DJ_Peng on 2007-04-25
From what I'm seeing I don't see why not. You'd just need to set the Clock Offset for the additional clocks. You can even use the face text to ID which clock was which.

---

### Post by reacocard on 2007-04-25
> **russell.h said:**
> Anyone know where I can get a .deb for 64 bit Feisty? I'm looking into compiling it myself, but it doesnt have a configuration script so I'm having troubles with dependencies.

Edit: Oh, and --force-architecture had some strange results, one of which doesn't seem to have been a working installation (depending on where you look it might be installed, but it doesn't work).

I think a 
```
sudo apt-get install build-essential beryl-dev
```
should get you everything you need. The Makefile is really weird though, you do 'make install' without sudo, iirc, because it just installs to ~/.beryl/plugins.  I had to do some serious modifications to get the plugin into a deb.

---

### Post by papercuts on 2007-04-25
Oh Man!

I was asking myself the whole time Why on earth would someone need a RULER screenlet? I was so dumb I can't beleive it. 

I guess no more quick pixel measure with a folded piece of paper in front of the screen for us. :)

On a serious note: I'm teaching myself python, so I think I found a good testing ground. Integrating small but useful applications into a screenlet I think is a good development idea.

Could the author please post some directions on this? To start some of us off.

---

### Post by Spike-X on 2007-04-29
My Weather screenlet is blank. It was working fine, until I restarted X after tweaking my Conky script. Now, no matter what I do, I can't un-blank it!

I've deleted and re-added it a bunch of times, tried restarting X without Conky, and everything else I can think of. Help!

I'm running Compiz on Feisty, using the Screenlets packages from sorceror's repo.

---

### Post by ghettro on 2007-04-29
I have screenlets working sweeet on beryl.   Is there a calculator available for it?  Of all the widgets I normally use the calculator would have to be the most useful one.

---

### Post by Spike-X on 2007-04-29
> **Spike-X said:**
> My Weather screenlet is blank. It was working fine, until I restarted X after tweaking my Conky script. Now, no matter what I do, I can't un-blank it!

I've deleted and re-added it a bunch of times, tried restarting X without Conky, and everything else I can think of. Help!

I'm running Compiz on Feisty, using the Screenlets packages from sorceror's repo. 
Well, that's weird. It just fixed itself.

---

### Post by Spike-X on 2007-04-29
> **Spike-X said:**
> Well, that's weird. It just fixed itself.
Now it's broken again. Gah!

---

### Post by b0ng0 on 2007-04-29
When I run "screenletsd start" it seems to be ok but when I try to add Weather or run the Control I get this error in the terminal:

Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
Traceback (most recent call last):
  File "/usr/local/share/screenlets/add-screenlet.py", line 14, in <module>
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 669, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 293, in __new__
    mainloop=mainloop)
dbus.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Any ideas what's wrong? I have put the Weather folder in ~/.config/Screenlets that was created automatically.

---

### Post by sorcererx84 on 2007-04-29
It is a DBus error. Try rebooting, DBus is really tricky sometimes. And if you have screenlets-extra package installed, you don't have to install Weather yourself, it should already be there.

---

### Post by b0ng0 on 2007-04-29
I have shut down and rebooted and I still get the same error. I installed it from Synaptic and to run it I am typing 2screenletsd start". This then does this:

Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
dave@hades:~$ CachingBackend: Loading cache ...
Session-file /home/dave/.config/Screenlets/screenletsd.ses not found (will be created automatically).

And nothing happens. I try to load the Control Panel and it comes up with the error I previously mentioned. What am I doing wrong?!

---

### Post by WinterWeaver on 2007-04-29
> I have shut down and rebooted and I still get the same error. I installed it from Synaptic and to run it I am typing 2screenletsd start". This then does this:

Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
dave@hades:~$ CachingBackend: Loading cache ...
Session-file /home/dave/.config/Screenlets/screenletsd.ses not found (will be created automatically).

And nothing happens. I try to load the Control Panel and it comes up with the error I previously mentioned. What am I doing wrong?!

I have the same problem, which is why I'm not using screenlets atm. This happened after I installed Feisty.

On another note (and of course when I get screenlets working again), there is another wee problem I noticed with Screenlets. When some of the screenlets cannot connect to the internet, like the weather-let, then it stalls ALL screenlets for a couple of seconds. Is there no way to make them independent, so that all my screenies continue functioning, even though one of the others cant connect to the net?

ta

WW

---

### Post by 71CH on 2007-04-29
I have screenlets installed and the beryl plugin installed as well but the screenlets won't act like widgets.  I set them all the 'widget' but they won't disappear.  Anybody have any advice for me?

---

### Post by reacocard on 2007-04-29
> **WinterWeaver said:**
> ...On another note (and of course when I get screenlets working again), there is another wee problem I noticed with Screenlets. When some of the screenlets cannot connect to the internet, like the weather-let, then it stalls ALL screenlets for a couple of seconds. Is there no way to make them independent, so that all my screenies continue functioning, even though one of the others cant connect to the net?

That's a known problem and is being worked on.

> **71CH said:**
> I have screenlets installed and the beryl plugin installed as well but the screenlets won't act like widgets.  I set them all the 'widget' but they won't disappear.  Anybody have any advice for me?

Is the widget plugin enabled in beryl settings?

---

### Post by FuturePilot on 2007-04-29
Anyone have a problem with the Compiz widget plugin? Every time I set a screenlet to act as a widget, Compiz crashes to Metacity.

---

### Post by kronepils on 2007-04-30
I have the same problem with compiz/widget screenlets. If I start compiz again everything works, though!
I guess it's the widget plugin. Screenlets *SHOULDN'T* be able to crash compiz...
But you never know.

---

### Post by FuturePilot on 2007-04-30
Yeah, other than that they work fine. But as widgets they crash Compiz. At least I know I'm not the only one. It must be with the plugin.

---

### Post by shadowboxer_k on 2007-05-01
my weak box doesn't let me use compiz nor beryl, but i do have screenlets. i also ran into the same problem as WinterWeaver - one of the screenlets couldn't connect to the internet and it stalled all the other screenlets. i have tried removing screenlets with sudo-apt get remove screenlets, in hope that i could reinstall them and get them to work, but to no avail. it was just like restarting them, with the old settings. sigh, i guess we'll just have to wait.

---

### Post by reacocard on 2007-05-01
> **shadowboxer_k said:**
> my weak box doesn't let me use compiz nor beryl, but i do have screenlets. i also ran into the same problem as WinterWeaver - one of the screenlets couldn't connect to the internet and it stalled all the other screenlets. i have tried removing screenlets with sudo-apt get remove screenlets, in hope that i could reinstall them and get them to work, but to no avail. it was just like restarting them, with the old settings. sigh, i guess we'll just have to wait.

```
rm -rf ~/.config/Screenlets
```
will remove your old configuration. No need to reinstall, just run this then start screenlets again.

Also, have you tried xcompmgr? It's a compositor, but it doesn't replace your WM and is a lot lighter than Beryl/Compiz.

---

### Post by shadowboxer_k on 2007-05-02
reacocard, thank you so much! i will be trying this first thing when i get home tonight! i like the screenlets a lot and i was really sad to have to forget about them. 

i am using xcompmgr already. someone recommended it a couple of days ago and i installed it and it's working just fine.

---

### Post by mustang on 2007-05-05
> **reacocard said:**
> Or you could just use the widget plugin. ;)

Packages:
Feisty (for Beryl from Universe): [http://download.tuxfamily.org/syzygy42/pool/feisty/reacocard/beryl-widget-plugin_0.1-2_i386.deb](http://download.tuxfamily.org/syzygy42/pool/feisty/reacocard/beryl-widget-plugin_0.1-2_i386.deb)
Edgy (for Beryl 0.2.0 from repo): [http://download.tuxfamily.org/syzygy42/pool/edgy/screenlets/beryl-widget-plugin_0.1-2_i386.deb](http://download.tuxfamily.org/syzygy42/pool/edgy/screenlets/beryl-widget-plugin_0.1-2_i386.deb)

Source tarball: [http://download.tuxfamily.org/syzygy42/static/misc/beryl-widget.tar.gz](http://download.tuxfamily.org/syzygy42/static/misc/beryl-widget.tar.gz)

Thanks! Was tearing my hair trying to figure out how to compile the source (got weird compilation errors).

> 
I have screenlets installed and the beryl plugin installed as well but the screenlets won't act like widgets. I set them all the 'widget' but they won't disappear. Anybody have any advice for me?


I did a reload window manager and that did the trick.

---

### Post by tompot on 2007-05-06
Why all my screenlets are displayed on black background? Is there any solution to fix it.

---

### Post by lepz on 2007-05-06
start up Beryl

---

### Post by tompot on 2007-05-06
Is it possible to fix it without beryl or compiz?

---

### Post by reacocard on 2007-05-06
> **tompot said:**
> Is it possible to fix it without beryl or compiz?

xcompmgr might also work, but you have to have a compositing manager of some sort enabled.

---

### Post by shadowboxer_k on 2007-05-09
xcompmgr works just fine to get the screenlets working. here's how to install it:

```
sudo apt-cache search xcompmgr
```

and you should see this among other things:

```
xcompmgr - X composition manager
```

then just do this:

```
sudo apt-get install xcompmgr
```

thanks to rolf-c fot this. and [here's a nice how to for xcompmgr]("http://ubuntuforums.org/showthread.php?t=75527"). good luck!

---

### Post by andytof47 on 2007-05-09
nice working well and so much better than B4

---

### Post by airtonix on 2007-05-22
any chance that a ghtmlkit-screenlet is possible?

then we blow opera out of the scene

also beryl needs more than two animation groups per window-event. seriously. ther are like 20-30 window types and i have to choose which of the two groups that these 20-30 windows types are effected by....

maybe i want a third group of animations ...like ahem for SCREENLETS!!!

sigh.

---

### Post by DeadSuperHero on 2007-06-09
Well, I installed it, and it worked great...until I tried to place the Checkmail thing.
I already had it saved as a session, and when this happened, I logged out.
Now I can't get it to run again.

I get this code when I try doing "screenletsd add control" now.
> sean@legionaire:~$ screenletsd add control
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
Traceback (most recent call last):
  File "/usr/local/share/screenlets/add-screenlet.py", line 16, in <module>
    '/org/freedesktop/Screenlets')
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 410, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 230, in __init__
    _dbus_bindings.UInt32(0))
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 169, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
dbus.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Screenlets was not provided by any .service files



Please help. I love the screenlets, I don't want to have to use KDE for fun widget thingies.

---

### Post by Takmadeus on 2007-06-10
I was wondering how hard would it be to code a screenlet that would allow you to launch the menu (like a start button) so I would not need to keep gnome's menu and taskbar all the time in the desktop (so it would look more coherent).... I would love to code it but I have no idea about coding in any language.... thanks for the help

Also I was wondering if there was the possibility to code a random quote displayer... that would look like the notes screenlet but that would allow to read a file with quotes to be displayed randomly on a time basis...

any answer please forward it to me via PM, thanks a lot!

---

### Post by MrGreen on 2007-06-11
In Gibbon I get 

```

[ ~ ] > screenletsd 
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
Usage: screenletsd <action> [option(s)]
[ ~ ] > screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
Screenletsd is already running - stop the running daemon first.
[ ~ ] > screenletsd add Control
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
add-screenlet-utility | (c) RYX (Rico Pfaus) 2007 | released under GPL
ERROR:dbus.connection:Unable to set arguments ('ControlScreenlet',) according to signature u'vv': <type 'exceptions.TypeError'>: More items found in D-Bus signature than in Python arguments
Error: Screenlets-Backend (screenletsd) not found.

```

;-(

---

### Post by MrGreen on 2007-06-12
*BUMP

Just wondered if screenlets work under Gibbon?

```
[ ~ ] > screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
[ ~ ] > CachingBackend: Loading cache ...
Session-file /home/mrgreen/.config/Screenlets/screenletsd.ses not found (will be created automatically).

```

then it gets stuck?

---

### Post by Forlong on 2007-06-14
> **Mr. Psychopath said:**
> Well, I installed it, and it worked great...until I tried to place the Checkmail thing.
Had the exact same thing today. You shouldn't mess around with it too much :p ;)

Dunno if you still need help but here it is:
The configurations of screenlets get saved to **~/.config/Screenlets** (_not_ ~/.screenlets)
Just delete the folder and you can start over.

---

### Post by catnappist on 2007-07-08
Crap.  After stumbling through the really messy install (I got the instructions here, so it ain't me), I ended up with this:

~/.config/Screenlets/screenletsd.ses not found (will be created automatically)

There isn't anything in that Screenlets folder. In my usr/lib folder I have python2.3, python2.4, and python2.5 folders, the latter having a lot of folders and the first two having very little.  I did a search for screenletsd.ses and there isn't one anywhere.

What do I have to do to get this prick working?:confused::frown::evil:

---

### Post by Forlong on 2007-07-08
And... where's your problem?

It's just like it tells you: the file "will be created automatically" once you add some screenlets to your desktop.

---

### Post by catnappist on 2007-07-08
Thanks, that was real helpful.

---

### Post by jhenager on 2007-07-15
I like it. I pretty much have all the functionality of my favorite Yahoo widgets now. Thanks.

---

### Post by Hybrid86 on 2007-07-31
Is there a way to keep the screenlets from floating upwards with the rest of the windows when using beryl's cube?

---

### Post by QwUo173Hy on 2007-08-06
There is a new version of Screenlets out 0.0.9. Would any of the package wizards out there care to pop up a .deb?

---

### Post by Depressed Man on 2007-08-06
I don't know how to make a .deb (though I really should look into learning how.. it would make installing things between my laptop and desktop easier). But you can watch this thread. I think someone is working on a .deb for .09. 

[http://forum.compiz.org/viewtopic.php?t=358&start=945](http://forum.compiz.org/viewtopic.php?t=358&start=945)

---

### Post by QwUo173Hy on 2007-08-06
I'm looking into packaging myself, but by the looks of it, it will take a long time before I'll be any use to the community.
[http://doc.ubuntu.com/ubuntu/packagingguide/C/](http://doc.ubuntu.com/ubuntu/packagingguide/C/)

---

### Post by orbital on 2007-08-06
I'm having trouble install Screenlets, all the repos mentioned seem to be down. Any help getting Screenlets installed is very much appreciated!

---

### Post by FuturePilot on 2007-08-06
Yeah, they seem to be down right now. [this one]("http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/screenlets/") has the latest version 0.9 but isn't working. Probably just have to wait a bit. Probably updating the repos.

---

### Post by orbital on 2007-08-08
> **FuturePilot said:**
> Yeah, they seem to be down right now. [this one]("http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/screenlets/") has the latest version 0.9 but isn't working. Probably just have to wait a bit. Probably updating the repos.

Still no .deb for version 0.9?

---

### Post by FuturePilot on 2007-08-08
Yeah still not working.:( Is there any other repos out there with 0.9?

---

### Post by ykpaiha on 2007-08-13
for the repo I had the same probleme 
see here  this one looks very good
at least for me...
:[http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/screenlets/](http://hendrik.kaju.pri.ee/ubuntu/dists/feisty/screenlets/)

---

### Post by FuturePilot on 2007-08-13
I installed 0.9 but it has fewer screenlets? Where did they all go?

---

### Post by airtonix on 2007-09-25
> Is there a way to keep the screenlets from floating upwards with the rest of the windows when using beryl's cube?mark them as sticky..

then goto your beryl/compiz manager and tell it not to move stickied windows on cube rotate

ps. beryl/compiz/screenlets dev : thankyou so much for creating multi-animation profiles now i can have seperate animations for each and every window type. awesomeness.

---

### Post by jeroach on 2008-04-20
How do I install screenlets?

---

### Post by SuperSon!c on 2008-04-20
in a terminal type

```
sudo apt-get install screenlets
```

---

### Post by Otto-C on 2008-04-27
Did an install of gdesklets using
sudo apt-get install -y gdesklets

Very disappointed.  How to uninstall please.
tia
otto-c

---

### Post by maniacmusician on 2008-04-27
sudo apt-get remove gdesklets

---

