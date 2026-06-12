---
title: "Unofficial personal Gutsy2Feisty backborts repository available"
date: 2007-06-24
forum: Repositories &amp; Backports
---

### Post by felipe on 2007-06-24
Hi, just to inform you that I'm repackaging some of the newest Gutsy packages for Feisty, for **personal** use, and decided to put the packages for anyone to enjoy. I already have a number of testers, and packages seems to do very fine so far. My **policy** is not to depend from outside sources and not to pack any **libraries** (ever), only GNOME or GTK applications, such as:

Ardour 2.0.2
Audtacity 1.3.3 
Brasero 0.5.90
Compiz Config Settings Manager from Compiz Fusion 
Compiz Fusion Plugins Main
Deluge 0.5.1 (with encryption!)
DMZ Cursor Theme 0.4.1
Exaile 0.2.10 <- NEW!
Firefox Gran Paradiso 3.0 Alpha 5
Gimp 2.3.18
GNOME Main Menu
Most of GNOME 2.19.3: EoG, Epiphany, File Roller, New Themes/Engines (new Clearlooks), Totem, Rhythmbox
Jokosher 0.9
K3B 1.0.2 <- NEW!
Liferea 1.2.17
Listen 0.5
Pidgin 2.0.2 with encryption plugin
Wine 0.9.38 (I'm compiling .39 right now)
...more are coming...

I'd like to make clear that I do **minimal** changes to the source packages from Gutsy, so my repository is the closest thing to "official backports". For the time being, only x86 debs are provided (working on more archs) and there'no authentication key, reflecting the UNSTABLE nature of the packages in it :)

Here are the lines for your sources.list:
```

deb [http://download.tuxfamily.org/pollyrepo]("http://download.tuxfamily.org/pollyrepo") feisty/
deb-src [http://download.tuxfamily.org/pollyrepo]("http://download.tuxfamily.org/pollyrepo") feisty/
```

And here's a page where you can make me suggestions, request packages or just say hello: [http://pollycoke.wordpress.com/repository/](http://pollycoke.wordpress.com/repository/) (italian)

That said, enjoy your Ubuntu :)

---

### Post by moredhel on 2007-06-24
thanks :D all good so far :D

---

### Post by F-3582 on 2007-06-24
Sounds pretty interesting, but the "partial upgrade" my Update Manager wants me to do sounds a little scary, to be honest.

EDIT: Okay, I performed the updates and in general, everything went smooth... except for the Gnome Main Menu: All my favourite applications have vanished and the system preferences area is empty, too.

---

### Post by felipe on 2007-06-25
> **F-3582 said:**
> Sounds pretty interesting, but the "partial upgrade" my Update Manager wants me to do sounds a little scary, to be honest.

EDIT: Okay, I performed the updates and in general, everything went smooth... except for the Gnome Main Menu: All my favourite applications have vanished and the system preferences area is empty, too.

That's caused by 

1) the change in the app name (slab->main-menu)
2) the loss of schema file (something still points to SUSE's YaST, go figure)

To get your settings back you can drag you fav apps from the "Application Browser" onto the GNOME Main Menu applet button. These little problems come directly from the Gutsy packages, so they'll get better in time, rest assured ;)

Thanks for the feedback, I'm updating the list ov available packages in the first post :)

---

### Post by limaunion on 2007-06-28
I'd love to see the latest release of audacious backported to feisty, thanks

---

### Post by F-3582 on 2007-06-28
By the way: I don't think that backporting Wine is necessary, because there are already [official repositories]("http://www.winehq.org/site/download-deb") for it.

---

### Post by b3tzi on 2007-06-28
Good job. ;)

---

### Post by felipe on 2007-06-28
> **limaunion said:**
> I'd love to see the latest release of audacious backported to feisty, thanks

I'll give a look at that :)

> **F-3582 said:**
> By the way: I don't think that backporting Wine is necessary, because there are already [official repositories]("http://www.winehq.org/site/download-deb") for it.

Yeah but I prefer the official Ubuntu packages ;)

> **b3tzi said:**
> Good job. ;)

Thank you!

---

### Post by DizzyTech on 2007-07-01
I'd like it if you had a GPG for this release, I hate the Synaptic warnings.

---

### Post by moore.bryan on 2007-07-01
[I]firstly, great work!  minor problem here, though... when i installed deluge and tried to start it, i got this:
[/I]```
moore@ubuntu:~/debian$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG value: 1
Applying preferences
Starting DHT...
/var/lib/python-support/python2.5/deluge/core.py:723: DeprecationWarning: integer argument expected, got float
  PREF_FUNCTIONS[pref](self.get_pref(pref))
Traceback (most recent call last):
  File "/usr/bin/deluge", line 106, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 67, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 57, in __init__
    '%s %s'%(common.PROGRAM_NAME, common.PROGRAM_VERSION), common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 223, in __init__
    self.state = pickle.load(pkl_file)
  File "/usr/lib/python2.5/pickle.py", line 1370, in load
    return Unpickler(file).load()
  File "/usr/lib/python2.5/pickle.py", line 858, in load
    dispatch[key](self)
  File "/usr/lib/python2.5/pickle.py", line 1069, in load_inst
    klass = self.find_class(module, name)
  File "/usr/lib/python2.5/pickle.py", line 1124, in find_class
    __import__(module)
ImportError: No module named deluge

```[I]ideas?

--------------------------------------------------------------------------------
EDIT

nevermind... i just deleted my .config/deluge entry and everything went fine.  nice work!
[/I]

---

### Post by felipe on 2007-07-02
> **DizzyTech said:**
> I'd like it if you had a GPG for this release, I hate the Synaptic warnings.

You're absolutely **right**, but my repo contains unstable and unsupported software, I wanted a way to keep newbies away and found that a generic "warning" does the job ;)


> **moore.bryan said:**
> 
nevermind... i just deleted my .config/deluge entry and everything went fine.  nice work!
[/I]

Yes, it's a simple change to the way deluge stores its config and removing the old files fixes everything :)

@all:
I added K3B 1.0.2 to the list of available packages :)

---

### Post by moredhel on 2007-07-02
thanks :D :D :D

EDIT: Also, could someone tell me how to hide all warnings about missing GPG keys etc?

---

### Post by sebastjanp on 2007-07-02
Can you please backport also gimp-ufraw package?
I like gimp 2.3 but I cant live without ufraw plugin also :(
Please.

---

### Post by hikaricore on 2007-07-03
> **felipe said:**
> Yeah but I prefer the official Ubuntu packages ;)

Technically, if you're doing personal back-porting of the "official Ubuntu package" of WINE,
then it's becoming a 3rd party repackage and is no longer official.  ^_^

:popcorn:

---

### Post by yopnono on 2007-07-05
The evince say 91 but after the install it say 81

---

### Post by felipe on 2007-07-06
> **sebastjanp said:**
> Can you please backport also gimp-ufraw package?
I like gimp 2.3 but I cant live without ufraw plugin also :(
Please.

gimp-ufraw is now available :)

> **yopnono said:**
> The evince say 91 but after the install it say 81

that was necessary since the transition evince 0.9.0->0.9.1 added a hard dependency on a newer version of poppler library. Since I don't want to backport libraries (for compatibility) the evince version is 0.9.1~really0.8.1, a common "hack" to revert the content of a package to a previous version and fool APT ;)

Thanks for the suggestions, keep 'em coming :)

---

### Post by kadath on 2007-07-07
> **limaunion said:**
> I'd love to see the latest release of audacious backported to feisty, thanks

Seconding this request. Maybe I'm blind, but I can't find Feisty debs for the latest Audacious anywhere.

---

### Post by m_gasior on 2007-07-07
> **kadath said:**
> Maybe I'm blind, but I can't find Feisty debs for the latest Audacious anywhere.

[http://morgoth.free.fr/ubports/]("http://morgoth.free.fr/ubports/")

---

### Post by carusoswi on 2007-07-07
> **felipe said:**
> You're absolutely **right**, but my repo contains unstable and unsupported software, I wanted a way to keep newbies away and found that a generic "warning" does the job ;)




Yes, it's a simple change to the way deluge stores its config and removing the old files fixes everything :)

@all:
I added K3B 1.0.2 to the list of available packages :)

What harm would visitation from newbies do?  

Caruso

---

### Post by picpak on 2007-07-07
Thank you thank you thank you thank you thank you thank you thank you THANK YOU. This is what every Ubuntu release needs.

Any chance of a Dapper to Feisty (or Gutsy) repo? Now that'd be amazing. Heck, I'd pay money for it.

---

### Post by F-3582 on 2007-07-07
The problem I see with this are the libraries in Dapper which are already a year old. I suppose, this will decrease the number of applications you can backport dramatically.

---

### Post by picpak on 2007-07-07
I do see that as a problem, but all my mom wants is the latest Gaim (Pidgin).

---

### Post by kadath on 2007-07-07
> **m_gasior said:**
> [http://morgoth.free.fr/ubports/]("http://morgoth.free.fr/ubports/")

Thanks for that link!

---

### Post by picpak on 2007-07-08
> **m_gasior said:**
> [http://morgoth.free.fr/ubports/]("http://morgoth.free.fr/ubports/")

I can't play mp3s with this version; all it says is "Illegal instruction" and then quits...anyone else have this problem? :(

---

### Post by F-3582 on 2007-07-08
How about upgrading to Feisty, then? It is a lot more responsive than Dapper was, IMO.

And if all that she wants is Pidgin, get it from [www.getdeb.net](www.getdeb.net) ;)

---

### Post by picpak on 2007-07-08
They don't make it for Dapper. They haven't made anything for Dapper since April.

---

### Post by limaunion on 2007-07-08
> **kadath said:**
> Thanks for that link!

Yes! big thanks! 

For some reason this version isn't reading my ~/.audacious/Skins, is anyone else having the same problem ?

---

### Post by limaunion on 2007-07-08
> **picpak said:**
> They don't make it for Dapper. They haven't made anything for Dapper since April.

I'm having the same problem: Illegal instruction, but I'm running Feisty, what's wrong with audacious??.

dpkg -l | grep audacious
ii  audacious                                  1.3.2-2~7.04mlk1                       Small and fast audio player which supports l
ii  audacious-plugins                          1.3.5-1~7.04mlk1                       Base plugins for audacious
ii  audacious-plugins-extra                    1.3.5-1~7.04mlk1                       Various extra plugins for audacious
ii  libaudacious5                              1.3.2-2~7.04mlk1                       Audacious C++ shared library

---

### Post by picpak on 2007-07-09
> **limaunion said:**
> I'm having the same problem: Illegal instruction, but I'm running Feisty, what's wrong with audacious??.

dpkg -l | grep audacious
ii  audacious                                  1.3.2-2~7.04mlk1                       Small and fast audio player which supports l
ii  audacious-plugins                          1.3.5-1~7.04mlk1                       Base plugins for audacious
ii  audacious-plugins-extra                    1.3.5-1~7.04mlk1                       Various extra plugins for audacious
ii  libaudacious5                              1.3.2-2~7.04mlk1                       Audacious C++ shared library

Well, I was referring to Pidgin, but yeah, from looking at their forums you apparently need to recompile the Audacious-plugins without SSE support. Recompiling just to play MP3s? >< Ouch.

---

### Post by F-3582 on 2007-07-09
> **picpak said:**
> They don't make it for Dapper. They haven't made anything for Dapper since April.
Then, why don't you upgrade her Ubuntu?

---

### Post by picpak on 2007-07-09
> **F-3582 said:**
> Then, why don't you upgrade her Ubuntu?

It's not so much that upgrading bothers her as much as upgrades breaking her system bother her. Upgrading would have to take her through Edgy, and that's not a chance I'm willing to take.

---

### Post by felipe on 2007-07-11
1) picpak, I have a Dapper installation somewhere :D I'll try and see if there's any chance (i doubt it)

2) As for Audacious plugins: I don't use that software, so I normally wouldn't package it... I'll see what can I do :)

If someone wants to request other packages feel free to do so, and if someone was asking (ie. picpak)... you can make me  donations at your wish, here: [http://download.tuxfamily.org/pollyrepo/donazione.html](http://download.tuxfamily.org/pollyrepo/donazione.html) 

Thanks for you feedback!

---

### Post by felipe on 2007-07-11
**UPDATE:** Audacious + Audacious Plugins is now in the repo :)

---

### Post by F-3582 on 2007-07-12
I just noticed that Eye of Gnome doesn't work anymore. The program starts without showing anything and the process sits frozen in the Process Monitor. Everytime you try to run it, another dead process is added to the list.

---

### Post by felipe on 2007-07-12
> **F-3582 said:**
> I just noticed that Eye of Gnome doesn't work anymore. The program starts without showing anything and the process sits frozen in the Process Monitor. Everytime you try to run it, another dead process is added to the list.

Working perfectly fine here. Tried to re-login into GNOME?

BTW, here's **Pidgin for Dapper**: [http://download.tuxfamily.org/pollyrepo/dapper/](http://download.tuxfamily.org/pollyrepo/dapper/) but it's not a repository, just debs to install (dpkg -i *.deb)

---

### Post by F-3582 on 2007-07-12
My fault. It only crashes with TIFF images for no apparent reason.

---

### Post by picpak on 2007-07-13
> **felipe said:**
> BTW, here's **Pidgin for Dapper**: [http://download.tuxfamily.org/pollyrepo/dapper/](http://download.tuxfamily.org/pollyrepo/dapper/) but it's not a repository, just debs to install (dpkg -i *.deb)

You are one amazing man. Thanks!!

---

### Post by smartboyathome on 2007-07-13
would you be able to build a new package for SuperKaramba? The one in the repos is 3.5.6, whereas the newest version is 3.9. I know it isn't a backport, but I would still like to see it. =)

---

### Post by limaunion on 2007-07-14
> **felipe said:**
> **UPDATE:** Audacious + Audacious Plugins is now in the repo :)

Thank you so much for this backport Felipe !!! I'm right now using it without a glitch!
Ciao!
JC.

---

### Post by loopeando on 2007-07-14
I've just made a clean install of Feisty and added the backport repository.

Everything upgraded fine except Rhythmbox which crashes when I use a volume up/down hotkey.

Anybody else had this problem?

Thx!

---

### Post by loopeando on 2007-07-14
I've doing some tweaks and found out that disabling the Multimedia Keys plugin on Rhythmbox allows me to use the Volume Up/Down hotkey without crashing Rhythmbox.

So, there seems to be a conflict between the Multimedia Keys plugin in Rhythmbox and the volume control on GNOME.

Any ideas?

---

### Post by picpak on 2007-07-16
> **felipe said:**
> BTW, here's **Pidgin for Dapper**: [http://download.tuxfamily.org/pollyrepo/dapper/](http://download.tuxfamily.org/pollyrepo/dapper/) but it's not a repository, just debs to install (dpkg -i *.deb)

It doesn't work! :(

It says

> error while loading shared libraries: libnm_glib.so.0: cannot open shared object file: No such file or directory.

---

### Post by phr0ze on 2007-07-16
picpak, I upgraded from dapper to edgy then to feisty without problems. If you're worried, image the disk first.

---

### Post by picpak on 2007-07-16
That's great, but I seem to be one of the unlucky ones as almost all of my upgrades break, including my mom's from Breezy to Dapper. When I explained to her the upgrading process, she said "Well it'd be quicker than trying to fix this!" (referring to the broken Gaim). She then decided that she didn't feel the need to upgrade just for a messaging program, so now all is well.

---

### Post by stinger30au on 2007-07-19
does anyone know of a cnetral web site with links to all these handy bacports and extar repos rather then doing a google search and spending your life trying to find them.

a central place like a distro watch but a repo watch would be awesome

---

### Post by felipe on 2007-07-30
There's always the big repository list compiled by my friend Treviño, a well known packager himself :)

[http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)

---

### Post by F-3582 on 2007-08-07
Could you please backport Tracker? It is lots faster than Beagle and it's enabled by default in Gutsy, now.

---

### Post by altonbr on 2007-08-11
> **felipe said:**
> 
Ardour 2.0.2
Audtacity 1.3.3 
Brasero 0.5.90
Compiz Config Settings Manager from Compiz Fusion 
Compiz Fusion Plugins Main
Deluge 0.5.1 (with encryption!)
DMZ Cursor Theme 0.4.1
Exaile 0.2.10 <- NEW!
Firefox Gran Paradiso 3.0 Alpha 5
Gimp 2.3.18
GNOME Main Menu
Most of GNOME 2.19.3: EoG, Epiphany, File Roller, New Themes/Engines (new Clearlooks), Totem, Rhythmbox
Jokosher 0.9
K3B 1.0.2 <- NEW!
Liferea 1.2.17
Listen 0.5
Pidgin 2.0.2 with encryption plugin
Wine 0.9.38 (I'm compiling .39 right now)
...more are coming...

Do you have an up-to-date list? Wine 0.9.41 was already officially back ported to Feisty. Deluge is now 0.5.4 with an official Feisty deb and Pidgin is 2.1.0 (although you have this one updated in your repo). (Note to everyone else: you can simply check out [http://download.tuxfamily.org/pollyrepo/feisty/](http://download.tuxfamily.org/pollyrepo/feisty/) to see the software versions before adding the URL to the sources.list file)

Sorry if I sound harsh, just making sure you're on top of things ;)

I am extremely appreciative of your work, especially for Kino and Rhythmbox, Gimp. Thank you OH so very much!

May I ask what you have to do to backport software from Gusty to Feisty? It seems like some of the packages may be tedious to do.

---

### Post by altonbr on 2007-08-14
Oh, and what about gEdit? Feisty = 2.18.1, Gusty = 2.19.3

---

