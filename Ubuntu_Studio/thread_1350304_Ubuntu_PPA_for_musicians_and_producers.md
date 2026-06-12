---
title: "Ubuntu PPA for musicians and producers"
date: 2009-12-09
forum: Ubuntu Studio
---

### Post by falkTX on 2009-12-09
Hi there community!

We decided to help non-geek guys (and girls) that need good software out-of-the-box.
We prepared 3 specials PPAs for audio production (apps, plugins and tools).

For Karmic, use philip5 PPA:
[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)
```
ppa:philip5/extra
```

For Lucid, use my PPA:
[https://launchpad.net/~falk-t-j/+archive/lucid/](https://launchpad.net/~falk-t-j/+archive/lucid/)
```
ppa:falk-t-j/lucid
```

For Lucid, bleeding-edge packages: (*)
[https://launchpad.net/~falk-t-j/+archive/lucid-latest/](https://launchpad.net/~falk-t-j/+archive/lucid-latest/)
```
ppa:falk-t-j/lucid-latest
```



The easiest way to install this PPA is through Synaptic.
Open it in System->Administration->Synaptic

Go to Settings->Repositories.
On the 2nd tab, "Other Software" add the PPA code (one of the displayed before)

Then click on the big "Reload" button.


You can check the web pages for a list of the packages available

I maintain a changelog of my main Lucid PPA:
[http://kxstudio.sourceforge.net/downloads/PPA-Changes](http://kxstudio.sourceforge.net/downloads/PPA-Changes)


Enjoy making music!


*(*) This PPA depends on ppa:falk-t-j/lucid*

---

### Post by thorgal on 2009-12-09
the latest LV2 calf plugins should not be ignored :)
(SVN version only I think, not sure).

what about the latest guitarix ? It has some cool features, w.r.t to jack, jconv (now called jconvolver), etc.

---

### Post by DerickX on 2009-12-09
FST might be useful for users
[http://www.joebutton.co.uk/fst/](http://www.joebutton.co.uk/fst/)

---

### Post by falkTX on 2009-12-09
> **DerickX said:**
> FST might be useful for users
[http://www.joebutton.co.uk/fst/](http://www.joebutton.co.uk/fst/)

Doesn't dssi-vst does the job?

Anyway, I'll try packaging that too

---

### Post by falkTX on 2009-12-09
> **thorgal said:**
> the latest LV2 calf plugins should not be ignored :)
(SVN version only I think, not sure).

what about the latest guitarix ? It has some cool features, w.r.t to jack, jconv (now called jconvolver), etc.

Will look for these apps.

What so special about LV2 latest svn release over the regular 1.2?

---

### Post by thorgal on 2009-12-09
not lv2 itself but calf plugins. They updated their lv2 plugin suite.

newest guitarix release: 

[http://sourceforge.net/projects/guitarix/files/guitarix/guitarix-0.05.4-1/guitarix-0.05.4-1.tar.bz2/download](http://sourceforge.net/projects/guitarix/files/guitarix/guitarix-0.05.4-1/guitarix-0.05.4-1.tar.bz2/download)

calf plugins: not svn but git, sorry 
git clone [http://repo.or.cz/r/calf.git](http://repo.or.cz/r/calf.git)

---

### Post by AutoStatic on 2009-12-09
Nice initiative!!
Question though, what package method do you use? I'd like to know, first because I think packaging for Ubuntu doesn't seem as straightforward to me as Fedora for example, and second because I have time, knowledge and the necessary processing power (fast server at work) to help out.

---

### Post by DerickX on 2009-12-09
Of course, for longterm quality, it's better to package for the Debian Multimedia team (which means that you're packaging for Ubuntu too of course), And then you learn good packaging :)

You can do both of course, packaging for the Debian Multimedia Team and maintaining your own PPA (including  packages from Debian unstable for example.)

[http://wiki.debian.org/DebianMultimedia/DevelopPackaging](http://wiki.debian.org/DebianMultimedia/DevelopPackaging)
[http://wiki.debian.org/DebianMultimedia](http://wiki.debian.org/DebianMultimedia)

---

### Post by dawiba on 2009-12-09
For the non-geeks here, just add your ppa then download and click on install package? No need to uninstall anything? It's okay to install these debs over the top of previously installed packages?

Just a bit of clarity for non-geeks ;)

---

### Post by falkTX on 2009-12-09
> **dawiba said:**
> For the non-geeks here, just add your ppa then download and click on install package? No need to uninstall anything? It's okay to install these debs over the top of previously installed packages?

Just a bit of clarity for non-geeks ;)

The easiest way is through Synaptic.
Open it in System->Administration->Synaptic

Go to Settings->Repositories.
On the 2nd tab, "Other Software" add the PPA:
ppa:falk-t-j/music

Then click on the big "Reload" button.

You can now search for the software listed in the beginning of this thread.

---

### Post by falkTX on 2009-12-09
> **AutoStatic said:**
> Nice initiative!!
Question though, what package method do you use? I'd like to know, first because I think packaging for Ubuntu doesn't seem as straightforward to me as Fedora for example, and second because I have time, knowledge and the necessary processing power (fast server at work) to help out.

I just use a basic template I made for new packages, then modify it to whatever I need.
I can provide it if you want

---

### Post by DerickX on 2009-12-09
> **falkTX said:**
> Doesn't dssi-vst does the job?

Anyway, I'll try packaging that too

About FST: make sure you build it from git

---

### Post by falkTX on 2009-12-09
> **DerickX said:**
> Of course, for longterm quality, it's better to package for the Debian Multimedia team (which means that you're packaging for Ubuntu too of course), And then you learn good packaging :)

You can do both of course, packaging for the Debian Multimedia Team and maintaining your own PPA (including  packages from Debian unstable for example.)

[http://wiki.debian.org/DebianMultimedia/DevelopPackaging](http://wiki.debian.org/DebianMultimedia/DevelopPackaging)
[http://wiki.debian.org/DebianMultimedia](http://wiki.debian.org/DebianMultimedia)

Maybe yes, maybe not.
Some of the stuff I package are non-free or has restrictions (VST!).
Using a PPA ensures we get all features

---

### Post by falkTX on 2009-12-09
> **DerickX said:**
> About FST: make sure you build it from git

Yep, I notice the site about it.
The new version doesn't need Asio SDK, which is very good for us.

---

### Post by AutoStatic on 2009-12-09
> **falkTX said:**
> I just use a basic template I made for new packages, then modify it to whatever I need.
I can provide it if you wantWell, I was thinking more in the way of what do you use to build packages, debuild, pbuilder, do you use a chrooted environment, stuff like that :)

---

### Post by falkTX on 2009-12-09
> **AutoStatic said:**
> Well, I was thinking more in the way of what do you use to build packages, deb-build, pbuild, do you use a chrooted environment, stuff like that :)

Ah, I just prepare the source package and then run:

Add a new entry to changelog:
```
dch - i
```

Prepare the package to upload:
```
debuild -S -sa
```

Put the source in Launchpad PPA:
```
dput ppa:<launchpad-id>/<repo> path-to-filename.changes
```


To test the packages first (making sure it compiles), I run:
```
debuild -rfakeroot
```

Hope I was useful

---

### Post by DerickX on 2009-12-09
> **falkTX said:**
> Maybe yes, maybe not.
Some of the stuff I package are non-free or has restrictions (VST!).
Using a PPA ensures we get all features
Not maybe..

Yes for sure!

And for the packages you need Steinberg stuff (which doesn't account for latest dssi-vst and fst for instance)

No for sure!

You can put both in your PPA of course

But it's not a maybe that packaging for the Debian Multimedia Team will in the long run give better quality and will provide you with better packaging skills! :)

---

### Post by falkTX on 2009-12-09
> **DerickX said:**
> But it's not a maybe that packaging for the Debian Multimedia Team will in the long run give better quality and will provide you with better packaging skills! :)

I'll need some help on that.

Let me just upload the rest of the stuff in my list, then we'll see about that

---

### Post by AutoStatic on 2009-12-09
> **DerickX said:**
> Of course, for longterm quality, it's better to package for the Debian Multimedia team (which means that you're packaging for Ubuntu too of course), And then you learn good packaging :)

You can do both of course, packaging for the Debian Multimedia Team and maintaining your own PPA (including  packages from Debian unstable for example.)

[http://wiki.debian.org/DebianMultimedia/DevelopPackaging](http://wiki.debian.org/DebianMultimedia/DevelopPackaging)
[http://wiki.debian.org/DebianMultimedia](http://wiki.debian.org/DebianMultimedia)Thanks! I'm going to read it through and see what I can make of it.

---

### Post by DerickX on 2009-12-09
Yeah you need to learn some stuff for sure, but you can get help from the team, debian mentors and ubuntu motu.


Btw did you build dssi-vst without the steinberg stuff? I think the Steinberg stuff is not needed anymore for the last version.

---

### Post by AutoStatic on 2009-12-09
> **falkTX said:**
> Ah, I just prepare the source package and then run:

Add a new entry to changelog:
```
dch - i
```

Prepare the package to upload:
```
debuild -S -sa
```

Put the source in Launchpad PPA:
```
dput ppa:<launchpad-id>/<repo> path-to-filename.changes
```


To test the packages first (making sure it compiles), I run:
```
debuild -rfakeroot
```

Hope I was usefulThanks! But this doesn't explain how to prepare the source package, and that happens to be the one thing I find pretty complicated.

---

### Post by jsevi83 on 2009-12-09
The lastest stable version of Calf is 0.0.18.5. The development version (at git) is 0.0.19 and it has really nice new plugins (incluiding LV2), as parametric equalizers, multiband compressor, etc. Also all the interfaces have been changed. You should check it out!!

---

### Post by falkTX on 2009-12-10
I have some bad news.
My laptop "broke". Not really broke, but is the wired internet just doesn't work anymore.
It's not an OS prob, it is hardware problem. I'll see if I can still upload the packages that I have already created (fixed fst, festige (fst-gui, made by me) and lmms-git)
I can't live without internet, so I'm sure I'll find a solution soon

And to answer your questions:
@DerickX: DSSI-vst was compiled using Steinberg stuff. It wasn't fully necessary, but the README said to use it if possible, which I did.

@AutoStatic: I use my package template, then modify it to the software needs (package name, build depends, etc) and then create a new changelog (first entry is always "Initial release")

@jsevi83: I'll look into that later.


BTW, what do you think it's the best host for LV2 plugins?

---

### Post by jsevi83 on 2009-12-10
Good luck with your laptop, I hope you find a cheap fix. The LV2 host I use is Ardour 2.8.4 (built with slv2 libraries). There is a package here =>  ppa:philip5/extra

---

### Post by jsevi83 on 2009-12-10
Got a smile! The repository is ppa philip5/extra

---

### Post by falkTX on 2009-12-10
Ha! I still can connect through wireless! huff... :p

Upload 2 new packages:
- **festige**:
 GUI for "fst" [VST Loader], _made by me_! - tell me what you think!

- **lmms-git**:
the latest LMMS from git, can be installed together with normal LMMS.
to launch run:
```
/opt/lmms/bin/lmms
```

The next package coming is "fst"

---

### Post by falkTX on 2009-12-10
> Got a smile! The repository is ppa philip5/extra

Thanks for the PPA!
Will copy some packages right away!

---

### Post by falkTX on 2009-12-10
Just uploaded fst. You should also install "festige", a GUI I made for it
(then tell me what you think about it)

Also start packaging some vst-packs (mda and ndc so far, more to come).

guitarix and calf-git are coming

---

### Post by c00kie55 on 2009-12-10
Thanx. lots off good things in this ppa you might just have maked live more easy for me.. and i love your fst gui keep it rolling 

 
ladish could be cool if possible 
 
i got a little problem with slv2-9 

E: /var/cache/apt/archives/slv2-9_0.6.6-karmic~ppa2_i386.deb: trying to overwrite '/usr/bin/lv2_inspect', which is also in package slv2-jack 0
E: /var/cache/apt/archives/slv2-9-dev_0.6.6-karmic~ppa2_i386.deb: trying to overwrite '/usr/include/slv2/pluginui.h', which is also in package libslv2-dev 0

guess i might be my old compiled drobilla-lad that need to be manually un-installed

---

### Post by falkTX on 2009-12-11
> **c00kie55 said:**
> Thanx. lots off good things in this ppa you might just have maked live more easy for me.. and i love your fst gui keep it rolling 

 
ladish could be cool if possible 

Sure.

 > **c00kie55 said:**
> 
i got a little problem with slv2-9 

E: /var/cache/apt/archives/slv2-9_0.6.6-karmic~ppa2_i386.deb: trying to overwrite '/usr/bin/lv2_inspect', which is also in package slv2-jack 0
E: /var/cache/apt/archives/slv2-9-dev_0.6.6-karmic~ppa2_i386.deb: trying to overwrite '/usr/include/slv2/pluginui.h', which is also in package libslv2-dev 0

guess i might be my old compiled drobilla-lad that need to be manually un-installed

I noticed that too, it happens when you use other PPAs.
I'll bump my PPAs slv2 version and this should fine in a few moments

---

### Post by DerickX on 2009-12-11
falk, What kind of templates do you use for packages as dssi-vst and fst? They are script packages which just produces a binary right? How do you make a deb package of it.
I'm gonna check out the fst gui, are you a programmer?


Maybe this package is interesting for a ppa:
[http://linuxmusicians.com/viewtopic.php?f=4&t=2323](http://linuxmusicians.com/viewtopic.php?f=4&t=2323)

---

### Post by falkTX on 2009-12-11
> **DerickX said:**
> falk, What kind of templates do you use for packages as dssi-vst and fst? They are script packages which just produces a binary right? How do you make a deb package of it.
I'm gonna check out the fst gui, are you a programmer?


Maybe this package is interesting for a ppa:
[http://linuxmusicians.com/viewtopic.php?f=4&t=2323](http://linuxmusicians.com/viewtopic.php?f=4&t=2323)

I know some C and python.
For interfaces I use PyQt.

I've attached my package templates.
You can also download any package from the PPA to check it out more deeply

And about that PPA, I've just released a better solution, I'll explain it soon

---

### Post by falkTX on 2009-12-11
Just added:

- guitarix
- pulse-jack
- vst-pack-mda
- vst-pack-ndc

Also some fixes for other packages.


The "pulse-jack" is a new package I made.
It provides Jack support for pulseaudio (including Firefox!)
Once Jack is running, just run:
```
pulse-jack
```
And pulseaudio will be added to the connections list.

If an application refuses to work this way, you can force it to output audio to pulse:
```
padsp <app>
```

Enjoy!

---

### Post by kayosiii on 2009-12-11
@falkFX -- You Rock... yes you really do...

[edit]Might it be possible to set up a package that sets realtime permissions/firewire permissions etc (I will look into it) So I can stop explaining to people why their jack is broken on ubuntu.[/edit]

---

### Post by falkTX on 2009-12-11
> **kayosiii said:**
> @falk_T_X -- You Rock... yes you really do...

thanks

---

### Post by falkTX on 2009-12-11
> **kayosiii said:**
> ]Might it be possible to set up a package that sets realtime permissions/firewire permissions etc (I will look into it) So I can stop explaining to people why their jack is broken on ubuntu.

Great idea!
Will do that right away!

---

### Post by thorgal on 2009-12-11
> **DerickX said:**
> 
Maybe this package is interesting for a ppa:
[http://linuxmusicians.com/viewtopic.php?f=4&t=2323](http://linuxmusicians.com/viewtopic.php?f=4&t=2323)

falkTX, don't forget this stuff for those who don't give a damn about pulse.

---

### Post by AutoStatic on 2009-12-11
> **falkTX said:**
> I know some C and python.
For interfaces I use PyQt.

I've attached my package templates.
You can also download any package from the PPA to check it out more deeply

And about that PPA, I've just released a better solution, I'll explain it soonThanks! I'll take a look at it. And just tested some of your packages, looks good!!

---

### Post by falkTX on 2009-12-11
> **kayosiii said:**
> Might it be possible to set up a package that sets realtime permissions/firewire permissions etc (I will look into it) So I can stop explaining to people why their jack is broken on ubuntu.

Done!
Package is "ubuntu-rt-enable"

---

### Post by c00kie55 on 2009-12-11
when using festige.. lash dont bring back my vst(vsti)'s
seams to be a returning problem with me, lash and fst ...
only working when i use fst command  ./fst /home/gorm/vst/V-Station.dll executed from from build dir  /home/gorm/fst/  

don't know if its a wine or others kind of permission problem 

it must be possible to tell festige to launch from /home/gorm/fst/ 

or how do i make a shortcut launch  /home/gorm/fst/ ./fst /home/gorm/vst/V-Station.dll
(not fst /home/gorm/vst/V-Station.dll)
                                                      
there seams to be some conflicts with ppa frasten your ppa... flowcanvas and lv2 (dont know if its a help)

---

### Post by kayosiii on 2009-12-11
> **falkTX said:**
> Done!
Package is "ubuntu-rt-enable"

If you rocked any harder you would probably have to be arrested.
:)

---

### Post by falkTX on 2009-12-11
> **c00kie55 said:**
> when using festige.. lash dont bring back my vst(vsti)'s
seams to be a returning problem with me, lash and fst ...
only working when i use fst command  ./fst /home/gorm/vst/V-Station.dll executed from from build dir  /home/gorm/fst/  

don't know if its a wine or others kind of permission problem 

it must be possible to tell festige to launch from /home/gorm/fst/ 

or how do i make a shortcut launch  /home/gorm/fst/ ./fst /home/gorm/vst/V-Station.dll
(not fst /home/gorm/vst/V-Station.dll)
                                                      
there seams to be some conflicts with ppa frasten your ppa... flowcanvas and lv2 (dont know if its a help)

Use "festige", a GUI for fst, to launch the VSTs

I had to disable lash support in order to build for amd64.
I'll add it again soon (32bit only)

I've been working with the conflicts (bumping versions up, might be fixed now)

---

### Post by c00kie55 on 2009-12-11
thanX and
sorry if iam not clear i have been using festige also i have tryed making fst from git (ver 1.9) with lash enable.. renamed fst.exe to fst copyed it and fst.exe.so to /usr/local/bin/  and /usr/bin/
guessed it is from there festige launches fst but still my lash projects don't reload vst plug-ins..

 
lash is working when i use fst command  ./fst /home/gorm/vst/V-Station.dll executed from from build dir  /home/gorm/fst/   
 
 
i been figthing this for fst and lash thing for some time now so when i saw fst in your ppa..  

it was like a good early Christmas present but guess i will have to wait some more.. maybe when you have build fst 32bit without disabled lash how knows..

hope I am not spamming and thanks again

---

### Post by falkTX on 2009-12-11
> **c00kie55 said:**
> thanX and
sorry if iam not clear i have been using festige also i have tryed making fst from git (ver 1.9) with lash enable.. renamed fst.exe to fst copyed it and fst.exe.so to /usr/local/bin/  and /usr/bin/
guessed it is from there festige launches fst but still my lash projects don't reload vst plug-ins..

 
lash is working when i use fst command  ./fst /home/gorm/vst/V-Station.dll executed from from build dir  /home/gorm/fst/   
 
 
i been figthing this for fst and lash thing for some time now so when i saw fst in your ppa..  

it was like a good early Christmas present but guess i will have to wait some more.. maybe when you have build fst 32bit without disabled lash how knows..

hope I am not spamming and thanks again

No prob.
In fact, I'll add the lash support now

---

### Post by falkTX on 2009-12-11
I'm really enjoying this!

fst lash support is now packaged (amd64 was built without it)
libflashsupport-jack added
calf-plugins (git) added


I recommend you to try the calf plugins, they're really awesome!

---

### Post by c00kie55 on 2009-12-11
cool what version of lash did you build with ? 
 now nothing shows up in lash_panel (lash 5.4) when loading a vst so guess that wasnt the version you used

---

### Post by falkTX on 2009-12-11
> **c00kie55 said:**
> cool what version of lash did you build with ? 
 now nothing shows up in lash_panel (lash 5.4) when loading a vst so guess that wasnt the version you used

The Karmic one, it's 0.5.4.

---

### Post by c00kie55 on 2009-12-11
about calf i notesed that the gui dont work in lv2rack, ingen or ardour anyway not on my computer i found the best way of using the new calf is when compiled --whitout lv2 ,dssi or ladspa(using stable insted) but as stand alone  yes the gui is real cool looks better than lots of ***commercial *ones and the synth and organ are stunning

---

### Post by AutoStatic on 2009-12-11
Yup, I totally agree on that, the Calf synths and organ are really, really nice.

---

### Post by falkTX on 2009-12-11
> **c00kie55 said:**
> about calf i notesed that the gui dont work in lv2rack, ingen or ardour anyway not on my computer i found the best way of using the new calf is when compiled --whitout lv2 ,dssi or ladspa(using stable insted) but as stand alone  yes the gui is real cool looks better than lots of ***commercial *ones and the synth and organ are stunning

The Calf LV2 plugins works for me in Ardour (see attachments).

Have you tried my PPA for this?

---

### Post by c00kie55 on 2009-12-11
well its kills my ardour or any other host i try. guess i will try a clean install of karmic with your repro and no other ppa's then adding things slowly one by one with crossed fingers..
hopping not to end back at square ONE

---

### Post by falkTX on 2009-12-11
> **c00kie55 said:**
> well its kills my ardour or any other host i try. guess i will try a clean install of karmic with your repro and no other ppa's then adding things slowly one by one with crossed fingers..
hopping not to end back at square ONE

Maybe it's something else... (or probably not)
Can you paste the output of ardour when you run it from a terminal?

---

### Post by c00kie55 on 2009-12-11
ofcource 

gorm@audio-book:~$ ardour2
Ardour/GTK 2.8.4
   (built using 6077 and GCC version 4.4.1)
Copyright (C) 1999-2008 Paul Davis
Some portions Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker

Ardour comes with ABSOLUTELY NO WARRANTY
not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
This is free software, and you are welcome to redistribute it 
under certain conditions; see the source for copying conditions.
loading default ui configuration file /etc/ardour2/ardour2_ui_default.conf
loading user ui configuration file /home/gorm/.ardour2/ardour2_ui.conf
Loading ui configuration file /etc/ardour2/ardour2_ui_dark.rc
theme_init() called from internal clearlooks engine
ardour: [INFO]: Ardour will be limited to 1024 open files
loading system configuration file /etc/ardour2/ardour_system.rc
loading user configuration file /home/gorm/.ardour2/ardour.rc
ardour: [INFO]: No H/W specific optimizations in use
librdf error URI file:///home/gorm/.lv2/bundles/manifest.ttl - file '/home/gorm/.lv2/bundles/manifest.ttl' open failed - No such file or directory
VST_PATH not set, defaulting to /home/gorm/vst:/usr/local/lib/vst:/usr/lib/vst
RemoteVSTClient: all cache files are up-to-date, not running scanner
ardour: [INFO]: looking for control protocols in /home/gorm/.ardour2/surfaces/:/usr/lib/ardour2/surfaces/
ardour: [INFO]: Control protocol Tranzport not usable
ardour: [INFO]: Control surface protocol discovered: "Wiimote"
ardour: [INFO]: Control surface protocol discovered: "Generic MIDI"
powermate: Opening of powermate failed - No such file or directory
ardour: [INFO]: Control protocol powermate not usable
ardour: [INFO]: Control surface protocol discovered: "Mackie"
system template path = /usr/share/ardour2/templates
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkWidget::cursor-color' of type `GdkColor' from rc file value "((GString*) 0xa09c960)" of type `GString'
loading bindings from /etc/ardour2/mnemonic-us.bindings
Session writable based on /home/gorm/testcalf2/
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::odd-row-color' of type `GdkColor' from rc file value "((GString*) 0xa3d99a0)" of type `GString'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkWidget::cursor-color' of type `GdkColor' from rc file value "((GString*) 0xa3df820)" of type `GString'
Found UI [http://calf.sourceforge.net/plugins/Phaser](http://calf.sourceforge.net/plugins/Phaser) at index 0 in:
    /usr/lib/lv2/calf.lv2/calflv2gui.so

CALF DEBUG: instance 0xa53f000 data 0xa0cdaa8
CALF DEBUG: calf 0xad4843e4 cpi 0xaccb0460
/usr/share/calf/calf.rc:1646: error: unexpected identifier `radius', expected character `}'
/usr/share/calf/calf.rc:1646: error: unexpected identifier `radius', expected character `}'
/usr/share/calf/calf.rc:1646: error: unexpected identifier `radius', expected character `}'
..........................same error ongoing and ardour freazes................
Killed

it looks like i have some gtk errors but others like invada plugins works great ...

---

### Post by c00kie55 on 2009-12-11
by the way fst again

gorm@audio-book:~$ fst /home/gorm/vst/V-Station.dll
yo... lets see...
instantiate... 
Sample Rate = 44100,00
Block Size = 512
Plugin isSynth = 1
Plugin canDo receiveVstEvents = 1
Plugin canDo receiveVstMidiEvent = 1
Plugin canDo sendVstEvents = 0
Plugin canDo SendVstMidiEvent = 0
PortLayout: in: 0 out: 2
created audio thread
Calling Jack activate
open Editor
And xid = 5a00005
Entering main loop
ok.... RockNRoll
calling gtk_main now


i cant see it tryes to start lash ??
and this is the one from your ppa mayby the disabled-lash version somehow is shadowing over the other one by having same name or something (just a wild guess)
as i can only see one in synaptic named fst 1.8 git20091209 ppa7 wich is the one i have installed and reinstalled.. a couple off times

---

### Post by falkTX on 2009-12-11
> **c00kie55 said:**
> by the way fst again

gorm@audio-book:~$ fst /home/gorm/vst/V-Station.dll
yo... lets see...
instantiate... 
Sample Rate = 44100,00
Block Size = 512
Plugin isSynth = 1
Plugin canDo receiveVstEvents = 1
Plugin canDo receiveVstMidiEvent = 1
Plugin canDo sendVstEvents = 0
Plugin canDo SendVstMidiEvent = 0
PortLayout: in: 0 out: 2
created audio thread
Calling Jack activate
open Editor
And xid = 5a00005
Entering main loop
ok.... RockNRoll
calling gtk_main now


i cant see it tryes to start lash ??
and this is the one from your ppa mayby the disabled-lash version somehow is shadowing over the other one by having same name or something (just a wild guess)
as i can only see one in synaptic named fst 1.8 git20091209 ppa7 wich is the one i have installed and reinstalled.. a couple off times

if you still have ~/bin/fst you'll need to remove it.
You're using the correct version.

What should the output of a compiled fst with lash support?

---

### Post by falkTX on 2009-12-11
> **c00kie55 said:**
> ofcource 

gorm@audio-book:~$ ardour2
Ardour/GTK 2.8.4
   (built using 6077 and GCC version 4.4.1)
Copyright (C) 1999-2008 Paul Davis
Some portions Copyright (C) Steve Harris, Ari Johnson, Brett Viren, Joel Baker
...
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::odd-row-color' of type `GdkColor' from rc file value "((GString*) 0xa3d99a0)" of type `GString'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkWidget::cursor-color' of type `GdkColor' from rc file value "((GString*) 0xa3df820)" of type `GString'
Found UI [http://calf.sourceforge.net/plugins/Phaser](http://calf.sourceforge.net/plugins/Phaser) at index 0 in:
    /usr/lib/lv2/calf.lv2/calflv2gui.so

CALF DEBUG: instance 0xa53f000 data 0xa0cdaa8
CALF DEBUG: calf 0xad4843e4 cpi 0xaccb0460
/usr/share/calf/calf.rc:1646: error: unexpected identifier `radius', expected character `}'
/usr/share/calf/calf.rc:1646: error: unexpected identifier `radius', expected character `}'
/usr/share/calf/calf.rc:1646: error: unexpected identifier `radius', expected character `}'
..........................same error ongoing and ardour freazes................
Killed

it looks like i have some gtk errors but others like invada plugins works great ...

Can't really say, sorry.
Maybe it's some kind of conflict with some other guy's repo packages.

I'll re-format my PC now (all this packaging resulted in... and anyway, I decided to build my own Ubuntu+Studio thing)

I also use Karmic Backports and Proposed, but probably that doesn't change anything.


If you're going to reinstall ubuntu, I recommend the following PPAs:
```
# add-apt-repository ppa:c-korn/vlc #Use only if VLC is giving problems
add-apt-repository ppa:cdemu/ppa
add-apt-repository ppa:chromium-daily/ppa
add-apt-repository ppa:debfx/firefox-kde
add-apt-repository ppa:dnjl/ppa
add-apt-repository ppa:dnjl/multimedia
add-apt-repository ppa:dnjl/virtualization
add-apt-repository ppa:falk-t-j/ppa
add-apt-repository ppa:falk-t-j/falkuntu
add-apt-repository ppa:falk-t-j/games
add-apt-repository ppa:falk-t-j/music
add-apt-repository ppa:falk-t-j/qtsixa
add-apt-repository ppa:kubuntu-ppa/ppa
add-apt-repository ppa:kubuntu-ppa/backports
# add-apt-repository ppa:kubuntu-ppa/beta #Future KDE 4.4.0 Beta
add-apt-repository ppa:motin/until-jack-is-included-in-main
add-apt-repository ppa:motumedia/ppa
add-apt-repository ppa:rvm/libs
add-apt-repository ppa:rvm/mplayer
add-apt-repository ppa:rvm/smplayer
add-apt-repository ppa:samrog131/ppa
add-apt-repository ppa:sunab/ppa
add-apt-repository ppa:ubuntu-wine/ppa
```

Also check medibuntu and playdeb/getdeb


See ya soon

---

### Post by c00kie55 on 2009-12-11
i have removed everything fst*.* from /usr/bin/ and usr/local/bin/

well i dont realy know but here is the output from fst 1.9 i build from git

gorm@audio-book:~/fst$ ./fst /home/gorm/vst/V-Station.dll
yo... lets see...
instantiate... 
Sample Rate = 44100,00
Block Size = 512
lash_init: Not attempting to start daemon server automatically
Plugin isSynth = 1
Plugin canDo receiveVstEvents = 1
Plugin canDo receiveVstMidiEvent = 1
Plugin canDo sendVstEvents = 0
Plugin canDo SendVstMidiEvent = 0
PortLayout: in: 0 out: 2
created audio thread
Calling Jack activate
open Editor
And xid = 5600005
Entering main loop
ok.... RockNRoll
calling gtk_main now

guess its the string:  lash_init: Not attempting to start daemon server automatically

---

### Post by falkTX on 2009-12-11
> **c00kie55 said:**
> i have removed everything fst*.* from /usr/bin/ and usr/local/bin/

well i dont realy know but here is the output from fst 1.9 i build from git

gorm@audio-book:~/fst$ ./fst /home/gorm/vst/V-Station.dll
yo... lets see...
instantiate... 
Sample Rate = 44100,00
Block Size = 512
lash_init: Not attempting to start daemon server automatically
Plugin isSynth = 1
Plugin canDo receiveVstEvents = 1
Plugin canDo receiveVstMidiEvent = 1
Plugin canDo sendVstEvents = 0
Plugin canDo SendVstMidiEvent = 0
PortLayout: in: 0 out: 2
created audio thread
Calling Jack activate
open Editor
And xid = 5600005
Entering main loop
ok.... RockNRoll
calling gtk_main now

guess its the string:  lash_init: Not attempting to start daemon server automatically

I'll check my package (maybe I did something wrong?).
You may had noticed that I added lib32qtcurve to the PPA, so I'll add lib32lash too (for lash amd64 support).

I just formated my PC, not all the packages are installed yet, so please be patient while waiting for this

---

### Post by c00kie55 on 2009-12-11
will that add lash supported fst on karmic 64 bit becource then i wil try to go the 64 bit way.. could be cool.. i have been dreaming off that 

and if done that way will it then work like in mixed mode (both 32 bit and 64 bit lash suportet apps) i sure hope so..

---

### Post by babarosa on 2009-12-11
Hello FalkTX,

on my system (Xubuntu 9.10) using your repo killed my mplayer, devede and mencoder. Ardour is not working, there are problems with two libraries which should be changed but can't. The reason of course could be interference with other ppa repos.

It is only for your information, I will jump back to 8.04 this evening and will not bother with 9.10 anymore.

Regards,
Michael

---

### Post by bluesscream on 2009-12-11
> **kayosiii said:**
> @falkfx -- you rock... Yes you really do...


+1, txl

---

### Post by falkTX on 2009-12-11
> **babarosa said:**
> Hello FalkTX,

on my system (Xubuntu 9.10) using your repo killed my mplayer, devede and mencoder. Ardour is not working, there are problems with two libraries which should be changed but can't. The reason of course could be interference with other ppa repos.

It is only for your information, I will jump back to 8.04 this evening and will not bother with 9.10 anymore.

Regards,
Michael

You shouldn't go 8.04...
I really want to fix all packaging issues, but I need reports.

For example, "patchage" complaing about missing libflowcanvas.so.2, where the package that should contain it actually has (...).so.3.

That was probably due to copying some other guys's repo packages, so I'm thinking about deleting ardour and its libs and start over again (for ardour).

---

### Post by trulan on 2009-12-11
**Edit:** I thought I had it.  I had lv2core installed from frasten_ppa and I installed yours instead.  But it didn't help - it just sits there hogging the cpu.  It's gotta be something simple I'm sure...

Your calf plug-ins do not work for me for some reason.  They don't work in Ardour (your version) and calfjackhost fails to start.  When I ran it from a terminal it complained about LASH, then the terminal would just sit there and wait.  I installed lashd and glashctl (haven't a clue how to use them) and the LASH errors went away, but the terminal still just waited.  So I reverted to the plugins from the repos and everything is working again.  It may not be your fault - it may be something stupid I am doing wrong, just thought you might like to know.  (I think the calf LAPSDA plugins worked but the LV2 plugins didn't.)  I am running jack from frasten_ppa, if that means anything.

Thanks for all the great work, BTW!

---

### Post by falkTX on 2009-12-11
> **trulan said:**
> Your calf plug-ins do not work for me for some reason.  They don't work in Ardour (your version) and calfjackhost fails to start.  When I ran it from a terminal it complained about LASH, then the terminal would just sit there and wait.  I installed lashd and glashctl (haven't a clue how to use them) and the LASH errors went away, but the terminal still just waited.  So I reverted to the plugins from the repos and everything is working again.  It may not be your fault - it may be something stupid I am doing wrong, just thought you might like to know.  (I think the calf LAPSDA plugins worked but the LV2 plugins didn't.)  I am running jack from frasten_ppa, if that means anything.

Thanks for all the great work, BTW!

Looks like mixing repos it's not a good thing... :(

This *fully* works for me though (ardour, lv2, etc).
I'm not sure about lash, cause I actually don't know what that is.

I already deleted the copied ardour and libs (raul, liblo & libflowcanvas). I'll try again for these

One thing that I know that is not working OK is dssi-vst, but that because of a code problem when searching-and-finding VSTs with no GUI.

---

### Post by falkTX on 2009-12-11
**NOTICE:**
Because of some bad packages I copied from another repo (I've learned the lesson, won't do that again!), some packages we're broken.
To ensure you have a working system please remove them:
```
sudo apt-get remove libraul2 libflowcanvas2 liblo0ldbl ardour
```

Sorry for the inconvenience.
An updated Ardour with proper LV2 support will come soon.

---

### Post by falkTX on 2009-12-11
Now let me compensate this.

I've just added:
fluisynth-dssi
whysynth
zyn
zynjacksu

also fixed dssi-vst, so vsts on QTractor are now possible
----------------

What software do you want to see compiled?

Next in the list are:
1 - ladish
2 - vst-bridge (ladspa, made by the Audacity team)
3 - more open/free VST packs
4 - any other good synth/plugin I can find

I'll be waiting for more suggestions, specially good plugins

---

### Post by c00kie55 on 2009-12-11
ladish working with fst,
else just lash working with festige is good enough for me 

if posible on 64bit..
without lash support, fst is preaty much useless to me.

calf is working as standalone on my computer, but it takes minutes to load. 
the one from calf dev, start much faster but then i cant get the eq's working.

also, none of the mda plugins, seams to launch from vestige but are working in ardour.

---

### Post by falkTX on 2009-12-12
> **c00kie55 said:**
> ladish working with fst,
else just lash working with festige is good enough for me 

if posible on 64bit..
without lash support, fst is preaty much useless to me.

I'll see what I can do about lash 64bit (it could take a while to get things done). I'm on 64bit, so I'll do testing first.

> **c00kie55 said:**
> calf is working as standalone on my computer, but it takes minutes to load. 
the one from calf dev, start much faster but then i cant get the eq's working.
I noticed a problem in the calf package and I'll fix it right away. Just wait for an update.

> **c00kie55 said:**
> also, none of the mda plugins, seams to launch from vestige but are working in ardour.
fst can't load non-GUI VSTs, and that's why it can't load mda plugins.

mda appears to have LV2 plugins too. I'm not sure where to get them, but I'll look around

---

### Post by falkTX on 2009-12-12
Maybe this is not the right way to do this... Some package are older then other's people PPAs, while some of my packages are newer...
This make some things, just, unusable.

So, I believe the solution to all problems is to create a Launchpad team (of uploaders/devs) and maintain a PPA as a group (instead of just me).
The PPA will have the latest SVN/Git of the major plugins, while keeping other music applications updated.

If you have packaging skills and want to contribute, please reply.
We'll also need testers (and users of course!)


This PPA will continue as it is.
No more uploads.

I'll give some more news soon.

---

### Post by Stochastic on 2009-12-12
> **falkTX said:**
> Maybe this is not the right way to do this... Some package are older then other's people PPAs, while some of my packages are newer...
This make some things, just, unusable.

So, I believe the solution to all problems is to create a Launchpad team (of uploaders/devs) and maintain a PPA as a group (instead of just me).
The PPA will have the latest SVN/Git of the major plugins, while keeping other music applications updated.

If you have packaging skills and want to contribute, please reply.
We'll also need testers (and users of course!)


This PPA will continue as it is.
No more uploads.

I'll give some more news soon.

Why don't you just consider helping the Ubuntu Studio team rather than creating a new team?

---

### Post by falkTX on 2009-12-12
> **Stochastic said:**
> Why don't you just consider helping the Ubuntu Studio team rather than creating a new team?

Because it's just a team for packaging; not bug reports, code etc.

Also, I use KDE, not Gnome.
If I was going to help them, the first thing I would do was creating "kubuntu-studio".

The UbuntuStudio team can also be part of it.

---

### Post by Stochastic on 2009-12-12
> **falkTX said:**
> Because it's just a team for packaging; not bug reports, code etc.

Also, I use KDE, not Gnome.
If I was going to help them, the first thing I would do was creating "kubuntu-studio".

The UbuntuStudio team can also be part of it.

So you don't want bug reports?  I'd welcome bug reports as they let you know something is wrong with your package.  They're also a great way of helping users with your packages.

I also see no packages in the PPA that are either Gnome or KDE specific.

Unfortunately we're quite overworked right now so joining a backporting project like this one might not be the most effective use of the Ubuntu Studio developers' time.

A large portion of what Ubuntu Studio developers do is upload packages and package fixes to the Ubuntu repositories.  Currently, we're working on getting Zyn into Lucid (among many other things - LV2 is coming).  Calf, for instance, was a package by an Ubuntu Studio developer, and we will be updating it as soon as the git branch works out the lv2 host bugs that many of your PPA users have run into (we regularly discuss releases with the upstream developer, but he doesn't believe it's ready for release yet).

Anyway, I don't mean to argue semantics of your effort here - it's great that you're making all this available.  I just wanted to extend the offer for you to help improve Ubuntu proper by joining the Ubuntu Studio team.  The previous suggestion that you help the Debian Multimedia team would also be a great way for you to help Ubuntu proper.

You seem to have a good level of packaging skill, a lot of enthusiasm, and an interest in making users lives easier.  I think it would be great if you joined a well-established packaging team rather than forking efforts.  (you could continue your PPA for certain illegal packages, though if Steinberg or Canonical find out, you may find yourself in some very hot water)

The Ubuntu Studio team did have a dedicated backporter whose sole job was to take recent releases and port them to past releases.  Unfortunately he resigned from the post a little while back.  If you're interested in that position, I think you'd be a great fit.

Just my 2 cents.

---

### Post by c00kie55 on 2009-12-13
well i just compiled this ladish from git and after a little testing iam really happy about it
all my problems with fst-1.9 seams gone.. if i just cut figure out making it to a deb file.. ?
then again i have jack-1.9.4 installed guess others migth need that, to use my deb file..
and the flowcanvas4 i had to build guess i would have to include that ..or

if i cut figure out thoes things i would happily help

---

### Post by falkTX on 2009-12-13
Thanks guys.

I'll help Ubuntu Studio team, in time. Let me just finish some basic uploads/packages so I can have a proper PPA this time.

Some of the things that are causing more trouble are:
- liblo in Karmic/Lucid is too old. Many packages depend on this. We do need to package 0.25 and rebuild all stuff against it.
- Using other PPAs might give svn snapshots of LV2 stuff. So I started packaging it too. This one is going to be different - an AllInOne package that has LV2+slv2+ingen+patchage+raul+flowcanvas+redlandmm+mda-lv2. The usual separate packages will be provided as dummy ones (empty, only exists for compatibility). This ensures that any user will be using LV2-svn (which I really think its stable enough), and it's much easier to maintain
- Anytime a new lib gets updated, lots of apps need to be rebuild or they won't work. With more and more packages we get... more work.
- Steinberg VST... if you look at the wineasio and dssi-vst packages, you'll see that I put there the license. I'm really not sure how to deal with this, but the aeffectx.h header made by LMMS devs seems to be a solution (many projects are using it now).
- 32bit lash on 64bit is no way. Although I did package lib32lash, everytime I compile against it, it results on bad binaries... I have no clue about what to do to fix it.


Once I finish the packaging, I'll sure help UbuntuStudio.
The backport thing seems a very good job for me

---

### Post by trulan on 2009-12-13
> **Stochastic said:**
> Calf, for instance, was a package by an Ubuntu Studio developer, and we will be updating it as soon as the git branch works out the lv2 host bugs that many of your PPA users have run into (we regularly discuss releases with the upstream developer, but he doesn't believe it's ready for release yet).
Nice to know it's not just me.  It's got me itching to see what the Calf developers have been doing!  Guess I'll have to be patient for now...
> The Ubuntu Studio team did have a dedicated backporter whose sole job was to take recent releases and port them to past releases.  Unfortunately he resigned from the post a little while back.  If you're interested in that position, I think you'd be a great fit.I agree, someone to maintain good backports is sorely needed.  Currently we're basically running old software or messing with a bleeding-edge, buggy system.

Not to complain - I need at least one bleeding-edge, buggy Ubuntu install to tinker with.  Thanks again to everybody for all the great work.

---

### Post by falkTX on 2009-12-14
I've been thinking a lot this weekend...

And I decided:

- I'll help UbuntuStudio, yes, but for Lucid.
- I'll stop packaging for a private PPA, instead, all efforts will be for Lucid.
- Lucid...


I'm getting tired of "just wait for the next release, it will be awesome....", so this will be the last time.
I think we need to focus everything for a "WOW" Lucid release (LV2 plugins, Jack in main, etc)

Anyone agrees with me?

---

### Post by trulan on 2009-12-14
Hey, I'm okay with that - somebody with time and talent to help the team sounds good to me.  We'll benefit from your work either way.  Thanks again for all the work you've done.

---

### Post by falkTX on 2009-12-14
Already started packaging for Lucid
[https://launchpad.net/~falk-t-j/+archive/lucid](https://launchpad.net/~falk-t-j/+archive/lucid)

The latest git plugins from Calf now has name "calf-plugins-git" and conflicts/replaces normal "calf-plugins".

I'll try to make as much release packages as possible (no ~ppa stuff).
I hope my work will be somewhat useful

---

### Post by Stochastic on 2009-12-15
> **falkTX said:**
> I've been thinking a lot this weekend...

And I decided:

- I'll help UbuntuStudio, yes, but for Lucid.
- I'll stop packaging for a private PPA, instead, all efforts will be for Lucid.
- Lucid...


I'm getting tired of "just wait for the next release, it will be awesome....", so this will be the last time.
I think we need to focus everything for a "WOW" Lucid release (LV2 plugins, Jack in main, etc)

Anyone agrees with me?

Great!  If you haven't already joined the ubuntustudio-devel mailing list, please do so here: [http://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-devel](http://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-devel)
And it'd be great if you joined the #ubuntustudio-devel IRC chat room in irc.freenode.net and had a conversation with some of us there.
Your packages still need a bit more tweaking before they're ready for the archives, but I certainly see potential.  I look forward to working with you.

---

### Post by falkTX on 2009-12-15
> **Stochastic said:**
> Great!  If you haven't already joined the ubuntustudio-devel mailing list, please do so here: [http://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-devel](http://lists.ubuntu.com/mailman/listinfo/ubuntu-studio-devel)
And it'd be great if you joined the #ubuntustudio-devel IRC chat room in irc.freenode.net and had a conversation with some of us there.
Your packages still need a bit more tweaking before they're ready for the archives, but I certainly see potential.  I look forward to working with you.

Nice to know my work is not in vain.

We should work hard to get Lucid a really rocking release!

---

### Post by falkTX on 2009-12-17
My laptop broke for real now.
I won't be able to help Lucid for a while.

I hope they fix it soon

---

### Post by eightdollarbeer on 2009-12-17
> **falkTX said:**
> My laptop broke for real now.
I won't be able to help Lucid for a while.

I hope they fix it soon

did you do a fresh install of lucid or upgrade , i know the installer messes up alot of stuff , i would install karmic then upgrade worked out better for me .
with the cd all sorts of stuff diddnt work mouse was all over the place video a mess. upgrade is the key.
good luck

---

### Post by falkTX on 2009-12-18
> **eightdollarbeer said:**
> did you do a fresh install of lucid or upgrade , i know the installer messes up alot of stuff , i would install karmic then upgrade worked out better for me .
with the cd all sorts of stuff diddnt work mouse was all over the place video a mess. upgrade is the key.
good luck

I'm the kind of guy that can't be without a PC more than one day...
So, it's already fixed.

And the problems seemed to do with Windows 7 (I use dualboot, most because Lucid can fail anytime).
For now on, I'll only boot into Windows when really needed.

...


*(I hate Windows)*

---

### Post by eightdollarbeer on 2009-12-19
> **falkTX said:**
> I'm the kind of guy that can't be without a PC more than one day...
So, it's already fixed.

And the problems seemed to do with Windows 7 (I use dualboot, most because Lucid can fail anytime).
For now on, I'll only boot into Windows when really needed.

...


*(I hate Windows)*

i see , i would say use the wubi on your win part worked prety good for me when i tried it .

---

### Post by orin zolis on 2009-12-19
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 133EAF26736E4F0B 

can someone help please

---

### Post by Stochastic on 2009-12-20
> **orin zolis said:**
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 133EAF26736E4F0B 

can someone help please

The Karmic PPAs have been deleted by Launchpad admins because they contained copyright infringing materials (Steinberg & Adobe files).

---

### Post by greasywhiteboy on 2009-12-27
I'm a complete noob, so please pardon any stupid questions, but I added the ppa in synaptic, now what? Is the paa is supposed automatically install all these packages or whatever? The help files don't say anything.

---

### Post by AutoStatic on 2009-12-27
Hello greasywhiteboy, why do you need this PPA?

---

### Post by philip5 on 2010-01-01
I'm not sure if this is of any interest but I also have the latest LMMS 0.4.6 and the latest version of Ardour (and bunch of other goodies) on my repo for 9.10/Karmic:

[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

Maybe worth a shot?!?!

Regards,

Philip

---

### Post by JC Cheloven on 2010-01-01
Fantastic initiative, thank you. 

A few of my favourite apps which are under active development, are missing. Perhaps you could consider interesting to include them:

- Muse sequencer. Has reached version 1 by now.
- MuseScore. My score editor.
- Traverso DAW. See my signature.
- MHWaveEdit. The latest version has pulse support.

Thank you anyway ;-)
_____________________________

---

### Post by babarosa on 2010-01-01
muse score has it's own ppa [https://launchpad.net/~mscore-ubuntu/+archive/mscore-stable](https://launchpad.net/~mscore-ubuntu/+archive/mscore-stable)

Compiling muse sequencer (which has grown very ripe now) isn't trivial to my mind, but it works fine and on [www.muse-sequencer.org](www.muse-sequencer.org) in the user-list you'll find appropriate help.

@Philip5, 
I'd like to thank you very much for your efforts and great ppa - it saves us from a lot of compiling labourand the apps work very fine!

With my kindest regards,
Michael

---

### Post by philip5 on 2010-01-02
> **JC Cheloven said:**
> Fantastic initiative, thank you. 

A few of my favourite apps which are under active development, are missing. Perhaps you could consider interesting to include them:

- Muse sequencer. Has reached version 1 by now.
- MuseScore. My score editor.
- Traverso DAW. See my signature.
- MHWaveEdit. The latest version has pulse support.

Thank you anyway ;-)
_____________________________

If your post was intened for me then I might have a look at them later on this evening and see if I could upload some updated packages for yor requested apps.

> **babarosa said:**
> 
@Philip5, 
I'd like to thank you very much for your efforts and great ppa - it saves us from a lot of compiling labourand the apps work very fine!

With my kindest regards,
Michael
Thank you for the feedback and you are very welcome. :)

---

### Post by JC Cheloven on 2010-01-02
> **philip5 said:**
> If your post was intened for me then I might have a look at them later on this evening and see if I could upload some updated packages for yor requested apps.
Yes, it was intended for you, whith my warmests thanks regardless whether you'd decide taking into account or not the packages I mentioned.

I devised (and I may be wrong) some aim of "completeness" in your ppa, and thus I pointed out some programs that I consider useful. I know there is already a ppa for [Traverso]("https://launchpad.net/~bojo42/+ppa-packages"), and for MuseScore, both "considered [stable]("https://launchpad.net/~mscore-ubuntu/+archive/mscore-stable/+packages")" and "[testing]("https://launchpad.net/~mscore-ubuntu/+archive/ppa")" (the one I use btw). 

On the other hand, the extremely simple (and useful for quick&dirty recording + cutting the fat + fading + some reverb) [MHWaveEdit]("http://gna.org/projects/mhwaveedit"), lacks a ppa with version 1.4.16 or 1.4.17 which have pulseaudio support. Also the [Muse]("http://muse-sequencer.org/index.php/Main_Page") sequencer lacks a ppa with version 1.0 , which came out by dec09. These two would be of personal interest for me though.

---

### Post by falkTX on 2010-01-03
I actually already started working for Lucid. And I think it's better that way.

My plan now is: 
**1. **Package everything possible (that is good enough & stable) [Lucid]
**2. **Create a lot of meta-packages
**3. **Code the software that is missing (a few GUIs for non-GUIs apps)
**4. **Pack everything in a ISO when Lucid is released.


I'm really looking for more good software (thanks for telling me about traverso).

The Lucid testing PPA is:
[https://launchpad.net/~falk-t-j/+archive/lucid/](https://launchpad.net/~falk-t-j/+archive/lucid/)

Please make requests!

---

### Post by JC Cheloven on 2010-01-03
> **falkTX said:**
> I actually already started working for Lucid. And I think it's better that way.

My plan now is: 
**1. **Package everything possible (that is good enough & stable) [Lucid]
**2. **Create a lot of meta-packages
**3. **Code the software that is missing (a few GUIs for non-GUIs apps)
**4. **Pack everything in a ISO when Lucid is released.


I'm really looking for more good software (thanks for telling me about traverso).

The Lucid testing PPA is:
[https://launchpad.net/~falk-t-j/+archive/lucid/](https://launchpad.net/~falk-t-j/+archive/lucid/)

Please make requests!

Wow, awesome plans !!  I bookmark your PPA, and look forward for its great success, and also personal convenience to myself ;-) I guess that your "request for requests" looks for possibly unnoticed good sofware, not well established programs everybody knows about. So let's sum up my experience:

As I said, **MuseScore** has PPAs from the developpers, but there isn't a lucid version, even in the testing ppa. So it may be of interest for your plans, although there will surely be a devel ppa for lucid in due time. Anyway, regarding usability, it has become the best free score editor imo.

**Traverso**... yes, I think it's definively worth. A time will come in which many other programs will take its interface as a canonical model. It's very stable now (except for some external plugins that don't get on fine, and isn't traverso's fault). I'd like to see a few particular features added soon though.

If you are thinking also in video, I'd seriously consider [OpenShot]("http://www.openshotvideo.com/"). It's improving damn fast, to a point that I prefer now using it instead of my previous choices (avidemux, pitivi...). I already heard voices in this forums claiming for it being included in ubuntustudio.

Although mostly an utilitary program (for me), **MHWaveEdit** is rock solid, and a very nice tool for recordings & edittings on single waves. Newer versions have pulseaudio support.

Although I plan to, I haven't really used the **Muse** sequencer much. But it's always a happy occasion for the commmunity when a project finally reaches version 1.0, isn't it? 

That's it. Sorry if some bits are repeated from a previous post, but I prefer that instead of asking you to look back and forward ;-)

---

### Post by philip5 on 2010-01-03
I have now updated my repo with MHWaveEdit 1.4.17 (with pulseaudio support) and Muse 1.0 for karmic. 

Had some problem making Muse detect python (2.6) includes (the binary and libs are detected but not the includes) during ./configuration so for the moment the Muse build lacks python support. Hope to look into this soon to see what's going on and why. If someone else have built Muse 1.0 successfully with full python support on Karmic I'm open for some input.

Regards,

Philip

---

### Post by falkTX on 2010-01-03
> **philip5 said:**
> I have now updated my repo with MHWaveEdit 1.4.17 (with pulseaudio support) and Muse 1.0 for karmic. 

Had some problem making Muse detect python (2.6) includes (the binary and libs are detected but not the includes) during ./configuration so for the moment the Muse build lacks python support. Hope to look into this soon to see what's going on and why. If someone else have built Muse 1.0 successfully with full python support on Karmic I'm open for some input.

Regards,

Philip

Can I have your permission to use your source files?
You seem to have some good stuff in your PPAs

I'll package everything for lucid, so you'll know in advance if it will work or not.

---

### Post by babarosa on 2010-01-03
@Philip,

I am in awe concerning your attitude!

Here is my command list for compiling muse successfully with python support on karmic koala (mathias from "our" muse group included python support for to add self written plugins, e.g. mixer controls, ...)

1 dependencies

sudo apt-get install subversion build-essential gcc make cvs

sudo apt-get install pyqt-tools python-dbus python-qt3 qt3-designer qt3-dev-tools qt3-qtconfig glibc-source libcap-dev libqt3-headers libqt3-i18n libqt3-mt-dev qt3-assistant qt3-designer qt3-qtconfig automake1.9 libtool libjack-dev libsndfile1-dev libfluidsynth-dev fluidsynth-dssi libladspa-ocaml-dev libsamplerate0-dev docbook polymer libltdl3-dev libltdl3 python2.5-dev python-dev python-qt-dev pyro liblash-dev lashd python-all-dev cpp-4.4 libltdl3-dev libltdl7

dssi-vst:
install dssi-vst
Run ./configure with the --enable-dssi switch. Be sure dssi and liblo, and their devel packages are installed.
After building, there is also a runtime switch '-I' to turn off loading of dssi plugins.

2 compiling muse

cvs -d:pserver:anonymous@lmuse.cvs.sourceforge.net:/cvsroot/lmuse login    ...#/replace smiley with ":_p" without "_"

cvs -z3 -d:pserver:anonymous@lmuse.cvs.sourceforge.net:/cvsroot/lmuse co -r REL07 -P muse   ...#/replace smiley with ":_p" without "_"


cd muse

./autogen.sh --prefix=/usr

export QTDIR=/usr/share/qt3

./configure --enable-optimize --prefix=/usr --enable-jack --enable-dssi --enable-arch=pentium4 --enable-lash --enable-shared --enable-vst --enable-ladcca --with-docbook-stylesheets=/usr/share/sgml/docbook/dsssl-stylesheets-1.79 --enable-python=yes --with-qt-prefix=/usr/share/qt3

(some switches depend on the system, e.g. arch=...)

make

sudo make install

This works fine on my system, hope it helps you too.

Kind regards,
Michael

---

### Post by philip5 on 2010-01-03
> **falkTX said:**
> Can I have your permission to use your source files?
You seem to have some good stuff in your PPAs

I'll package everything for lucid, so you'll know in advance if it will work or not.
Sure, in the spirit of GPL that is what open source is all about. If you borrow something you can always give me credit in your debian/changelog if you like. I know that I'm not always the best to write everthing I do in my own changelogs though...

---

### Post by falkTX on 2010-01-03
> **philip5 said:**
> Sure, in the spirit of GPL that is what open source is all about. If you borrow something you can always give me credit in your debian/changelog if you like. I know that I'm not always the best to write everthing I do in my own changelogs though...

Thanks.
I'll probably only change the needed stuff for lucid, or to activate any missing feature.
The final packages shouldn't be too different from yours

---

### Post by philip5 on 2010-01-03
> **babarosa said:**
> @Philip,

sudo apt-get install pyqt-tools python-dbus python-qt3 qt3-designer qt3-dev-tools qt3-qtconfig glibc-source libcap-dev libqt3-headers libqt3-i18n libqt3-mt-dev qt3-assistant qt3-designer qt3-qtconfig automake1.9 libtool libjack-dev libsndfile1-dev libfluidsynth-dev fluidsynth-dssi libladspa-ocaml-dev libsamplerate0-dev docbook polymer libltdl3-dev libltdl3 python2.5-dev python-dev python-qt-dev pyro liblash-dev lashd python-all-dev cpp-4.4 libltdl3-dev libltdl7

./autogen.sh --prefix=/usr

export QTDIR=/usr/share/qt3

./configure --enable-optimize --prefix=/usr --enable-jack --enable-dssi --enable-arch=pentium4 --enable-lash --enable-shared --enable-vst --enable-ladcca --with-docbook-stylesheets=/usr/share/sgml/docbook/dsssl-stylesheets-1.79 --enable-python=yes --with-qt-prefix=/usr/share/qt3

I don't really get why it doesn't get the python includes when I try to build. I have what you have beside I build from the Muse 1.0 tarball and not from cvs. 

```
checking for python build information...                                                                  
checking for python2.6... python2.6                                                                       
checking for main in -lpython2.6... yes                                                                   
checking python2.6/Python.h usability... yes                                                              
checking python2.6/Python.h presence... yes                                                               
checking for python2.6/Python.h... yes                                                                    
checking for python2.5... (cached) python2.6                                                              
checking for main in -lpython2.6... (cached) yes                                                          
checking for python2.6/Python.h... (cached) yes                                                           
checking for python2.4... (cached) python2.6                                                              
checking for main in -lpython2.6... (cached) yes                                                          
checking for python2.6/Python.h... (cached) yes                                                           
checking for python2.3... (cached) python2.6                                                              
checking for main in -lpython2.6... (cached) yes                                                          
checking for python2.6/Python.h... (cached) yes                                                           
checking for python2.2... (cached) python2.6                                                              
checking for main in -lpython2.6... (cached) yes                                                          
checking for python2.6/Python.h... (cached) yes                                                           
checking for python2.1... (cached) python2.6                                                              
checking for main in -lpython2.6... (cached) yes                                                          
checking for python2.6/Python.h... (cached) yes                                                           
checking for python... (cached) python2.6                                                                 
checking for main in -lpython2.6... (cached) yes                                                          
checking for python2.6/Python.h... (cached) yes                                                           
results of the Python check:                                                                            
    Binary:      python2.6                                                                                
    Library:     python2.6                                                                                
    Include Dir: no                                                                                       
checking support for DSSI + DSSI-Vst plugins... checking for LO... yes                                    
checking dssi.h usability... yes                                                                          
checking dssi.h presence... yes                                                                           
checking for dssi.h... yes                                                                                
configure: creating ./config.status                                                                       
config.status: creating Makefile                                                                          
config.status: creating m4/Makefile                                                                       
config.status: creating al/Makefile                                                                       
config.status: creating doc/Makefile                                                                      
config.status: creating xpm/Makefile                                                                      
config.status: creating demos/Makefile                                                                    
config.status: creating grepmidi/Makefile                                                                 
config.status: creating packaging/Makefile                                                                
config.status: creating muse/Makefile                                                                     
config.status: creating muse/widgets/Makefile                                                             
config.status: creating muse/master/Makefile                                                              
config.status: creating muse/midiedit/Makefile                                                            
config.status: creating muse/arranger/Makefile                                                            
config.status: creating muse/liste/Makefile                                                               
config.status: creating muse/driver/Makefile                                                              
config.status: creating muse/waveedit/Makefile                                                            
config.status: creating muse/ctrl/Makefile                                                                
config.status: creating muse/instruments/Makefile                                                         
config.status: creating muse/mixer/Makefile                                                               
config.status: creating muse/cliplist/Makefile                                                            
config.status: creating muse/marker/Makefile                                                              
config.status: creating muse/mplugins/Makefile                                                            
config.status: creating muse/remote/Makefile                                                              
config.status: creating share/Makefile                                                                    
config.status: creating share/drummaps/Makefile                                                           
config.status: creating share/html/Makefile                                                               
config.status: creating share/locale/Makefile                                                             
config.status: creating share/wallpapers/Makefile                                                         
config.status: creating share/instruments/Makefile                                                        
config.status: creating share/plugins/Makefile                                                            
config.status: creating share/templates/Makefile                                                          
config.status: creating share/pybridge/Makefile                                                           
config.status: creating share/scripts/Makefile                                                            
config.status: creating synti/Makefile                                                                    
config.status: creating synti/libsynti/Makefile                                                           
config.status: creating synti/fluidsynth/Makefile                                                         
config.status: creating synti/fluid/Makefile                                                              
config.status: creating synti/organ/Makefile                                                              
config.status: creating synti/s1/Makefile                                                                 
config.status: creating synti/vam/Makefile                                                                
config.status: creating synti/deicsonze/Makefile                                                          
config.status: creating synti/simpledrums/Makefile                                                        
config.status: creating lib/Makefile                                                                      
config.status: creating lib/synthi/Makefile                                                               
config.status: creating lib/plugins/Makefile                                                              
config.status: creating plugins/Makefile                                                                  
config.status: creating plugins/freeverb/Makefile                                                         
config.status: creating plugins/pandelay/Makefile                                                         
config.status: creating plugins/doublechorus/Makefile                                                     
config.status: creating Doxyfile                                                                          
config.status: creating utils/Makefile                                                                    
config.status: creating config.h                                                                          
config.status: executing depfiles commands                                                                
configure:                                                                                                

  MusE configured

  LASH support:                  yes
  DSSI support:                  yes
  FluidSynth:                    yes

  jade:                          jade
  doxygen:                       /usr/bin/doxygen
  graphviz:                      /usr/bin/dot    
  perl:                          /usr/bin/perl   
  treeviews in doxygen                           
  html output:                   yes             

  C++ compiler:                  g++
  optimizing:                    yes
  debug:                         no 
  optimise for arch:             none
  SSE optimizations              no  
  python bindings:               no - devel pkg not found

  installation prefix:           /usr

  Deprecated:
  ---------------------------------------------------
  using rtcap:                   no                  
  setuid root install:           no                  
  setuid root build:             no                  
  VST/win support:               no
```

---

### Post by lunar_shuttle on 2010-01-04
Hej Philip!

I'm the one who added python support to MusE. That python autoconf script isn't the best it seems, not to mention I'm utterly helpless when it comes to autoconf/make stuff... I found that .m4-script somewhere around and don't have much of a clue of how it works internally, it sets some variables that I try to use later on in :-/ You're using the tarball and not cvs? One thing you can try is to not set --enable-python=yes when running configure.

I'll try using the tarball myself.

---

### Post by philip5 on 2010-01-04
> **lunar_shuttle said:**
> Hej Philip!

I'm the one who added python support to MusE. That python autoconf script isn't the best it seems, not to mention I'm utterly helpless when it comes to autoconf/make stuff... I found that .m4-script somewhere around and don't have much of a clue of how it works internally, it sets some variables that I try to use later on in :-/ You're using the tarball and not cvs? One thing you can try is to not set --enable-python=yes when running configure.

I'll try using the tarball myself.

Seams like a black box and dark arts that python detection thing in .m4 as I don't really get how it doesn't get that I have the python headers which it even detects in the first place.

Tried both --enable-python=yes and --enable-python and without to let it auto-detect but nothing helps in this case.

And I use the 1.0 tarball and not cvs code for this. I also use the tarballs ./configure script and I don't generate anything with ./autogen.sh (but it doesn't help when I do either).

---

### Post by lunar_shuttle on 2010-01-05
> **philip5 said:**
> Seams like a black box and dark arts that python detection thing in .m4 as I don't really get how it doesn't get that I have the python headers which it even detects in the first place.

Tried both --enable-python=yes and --enable-python and without to let it auto-detect but nothing helps in this case.

And I use the 1.0 tarball and not cvs code for this. I also use the tarballs ./configure script and I don't generate anything with ./autogen.sh (but it doesn't help when I do either).

 I've tested the 1.0 tarball and it works ok for me... :-/ One difference between our systems is that you're using Python 2.6 and I'm using Python 2.5. I also remember that there were some strange differences between the autoconf/make versions once (different between hardy and jaunty). Running xubuntu hardy here, autoconf 2.61.

---

### Post by JC Cheloven on 2010-01-06
@ philip, falk, & the rest of awesome people in this thread:

[SIZE="4"][FONT="Arial Black"]THANK YOU[/FONT][/SIZE]

Has been nice to install mhwaveedit with pulse support, will be nice to start testing lucid with updated packages next week... You are offering a great service to the community.

---

### Post by philip5 on 2010-01-06
> **JC Cheloven said:**
> @ philip, falk, & the rest of awesome people in this thread:

[SIZE="4"][FONT="Arial Black"]THANK YOU[/FONT][/SIZE]

Has been nice to install mhwaveedit with pulse support, will be nice to start testing lucid with updated packages next week... You are offering a great service to the community.
You are welcome.

Hope you didn't miss the packages of traverso 0.49.1, muse 1.0 and jack-mixer 8 that you also find on my repo that all seam to be requested.  All only for Karmic so far though.

---

### Post by babarosa on 2010-01-07
People,

it was me who asked Philip5 to compile jack_mixer only a few days ago. Now we already have this fine app at our hands =D> ... So that brings me to some more wishes :-\"

Philip5, Andrea (frasten) and some others really are awesome!

@Philip5
Yesterday I compiled "swami soundfont editor" on my v9.10 machine and had to install some python related dependencies. Today I compiled muse again because of code amendments and the python bindings are okay now (yesterday I also got the "python bindings: no"-message ):
[http://i14.servimg.com/u/f14/12/84/23/35/muse_c10.png](http://i14.servimg.com/u/f14/12/84/23/35/muse_c10.png)

 The additional commands were:[I]

sudo apt-get install build-essential automake libtool intltool subversion

sudo apt-get install libgnomecanvas2-dev python-gtk2-dev libfftw3-dev libgtksourceview-dev libfluidsynth-dev libasound2-dev

sudo apt-get install librsvg2-dev
sudo apt-get install libaudiofile-dev
sudo apt-get install python-gobject-dev
sudo apt-get install gtk-doc-tools
sudo apt-get install libglade2-dev
sudo apt-get install libfftw3-dev
[/I]
Here is a screenshot with one of the plugins opened [http://i14.servimg.com/u/f14/12/84/23/35/muse_p10.jpg](http://i14.servimg.com/u/f14/12/84/23/35/muse_p10.jpg)

My kindest regards,
Michael

---

### Post by philip5 on 2010-01-07
> **babarosa said:**
> 
@Philip5
Yesterday I compiled "swami soundfont editor" on my v9.10 machine and had to install some python related dependencies. Today I compiled muse again because of code amendments and the python bindings are okay now (yesterday I also got the "python bindings: no"-message ):
[http://i14.servimg.com/u/f14/12/84/23/35/muse_c10.png](http://i14.servimg.com/u/f14/12/84/23/35/muse_c10.png)

 The additional commands were:[I]

sudo apt-get install build-essential automake libtool intltool subversion

sudo apt-get install libgnomecanvas2-dev python-gtk2-dev libfftw3-dev libgtksourceview-dev libfluidsynth-dev libasound2-dev

sudo apt-get install librsvg2-dev
sudo apt-get install libaudiofile-dev
sudo apt-get install python-gobject-dev
sudo apt-get install gtk-doc-tools
sudo apt-get install libglade2-dev
sudo apt-get install libfftw3-dev
[/I]

When you build Muse on karmic which version of python does it detect when it find the bindings? For me it always detects python 2.6 and never get that right for that version (finds libs, includes and headers but doesn't use them) even if I tried with all the packages you mentioned above.

---

### Post by falkTX on 2010-01-07
Good News!
In my Lucid PPA, Jack is now available for ALL sound apps, including PulseAudio (play & record).
I tested this extensively, and created a script to auto-start pulseaudio after jackd. See the "pulse-jack" package for details

Also Mixxx has Jack now.

Lucid is going to rock!

---

### Post by babarosa on 2010-01-07
Hello Philip,

I have python 2.5.4 and python 2.6.4 installed on my machine. I am using xubuntu, but can that make any difference?

Here is the complete output of "./configure ..." - it seems to be using python 2.6

> babarosa@acer:~$ cd lmuse/trunk/muse
babarosa@acer:~/lmuse/trunk/muse$ ./configure --enable-optimize --prefix=/usr --enable-arch=pentium4 --enable-lash --enable-shared --enable-vst --with-docbook-stylesheets=/usr/share/sgml/docbook/dsssl-stylesheets-1.79 --enable-python=yes --with-qt-prefix=/usr/share/qt3 --enable-dssi
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether ln -s works... yes
checking for openjade... no
checking for jade... jade
checking for onsgmls... no
checking for nsgmls... nsgmls
checking for DocBook V4.1... yes
checking for DocBook stylesheets... /usr/share/sgml/docbook/stylesheet/dsssl/modular
checking for doxygen... no
checking for dot... no
checking for perl... /usr/bin/perl
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for QT environment variable QTDIR... no
configure: WARNING:

    ***************** WARNING *****************

YOU HAVE NOT SET YOUR 'QTDIR' ENVIRONMENT VARIABLE!!!

This is the source of most people's problems when
configuring muse.  If the configuration fails to find
qt, try setting your QTDIR environment variable to
the directory where qt is installed.

    *******************************************


checking for QT includes (/usr/share/qt3/include)... 
yes
checking for QT libraries (/usr/share/qt3/lib)... yes
checking for QT moc (/usr/share/qt3/bin/moc)... yes
checking for QT uic (/usr/share/qt3/bin/uic)... yes
checking for QT version >= 3.2.0... yes
checking for qt_selection_property in -lqt-mt... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl
checking for libasound headers version >= 0.9.0... found.
checking for snd_seq_create_event in -lasound... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for Fluidsynth... yes
checking for SNDFILE... yes
checking for SAMPLERATE... yes
checking uuid/uuid.h usability... yes
checking uuid/uuid.h presence... yes
checking for uuid/uuid.h... yes
checking for uuid_generate in -luuid... yes
checking for JACK... yes
checking for LASH... yes
checking for python build information... 
checking for python2.6... python2.6
checking for main in -lpython2.6... yes
checking python2.6/Python.h usability... yes
checking python2.6/Python.h presence... yes
checking for python2.6/Python.h... yes
  results of the Python check:
    Binary:      python2.6
    Library:     python2.6
    Include Dir: /usr/include/python2.6
checking for FST... no
checking support for DSSI + DSSI-Vst plugins... checking for LO... yes
checking dssi.h usability... yes
checking dssi.h presence... yes
checking for dssi.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating m4/Makefile
config.status: creating al/Makefile
config.status: creating doc/Makefile
config.status: creating xpm/Makefile
config.status: creating demos/Makefile
config.status: creating grepmidi/Makefile
config.status: creating packaging/Makefile
config.status: creating muse/Makefile
config.status: creating muse/widgets/Makefile
config.status: creating muse/master/Makefile
config.status: creating muse/midiedit/Makefile
config.status: creating muse/arranger/Makefile
config.status: creating muse/liste/Makefile
config.status: creating muse/driver/Makefile
config.status: creating muse/waveedit/Makefile
config.status: creating muse/ctrl/Makefile
config.status: creating muse/instruments/Makefile
config.status: creating muse/mixer/Makefile
config.status: creating muse/cliplist/Makefile
config.status: creating muse/marker/Makefile
config.status: creating muse/mplugins/Makefile
config.status: creating muse/remote/Makefile
config.status: creating share/Makefile
config.status: creating share/drummaps/Makefile
config.status: creating share/html/Makefile
config.status: creating share/locale/Makefile
config.status: creating share/wallpapers/Makefile
config.status: creating share/instruments/Makefile
config.status: creating share/plugins/Makefile
config.status: creating share/templates/Makefile
config.status: creating share/pybridge/Makefile
config.status: creating share/scripts/Makefile
config.status: creating synti/Makefile
config.status: creating synti/libsynti/Makefile
config.status: creating synti/fluidsynth/Makefile
config.status: creating synti/fluid/Makefile
config.status: creating synti/organ/Makefile
config.status: creating synti/s1/Makefile
config.status: creating synti/vam/Makefile
config.status: creating synti/deicsonze/Makefile
config.status: creating synti/deicsonze2/Makefile
config.status: creating synti/simpledrums/Makefile
config.status: creating lib/Makefile
config.status: creating lib/synthi/Makefile
config.status: creating lib/plugins/Makefile
config.status: creating plugins/Makefile
config.status: creating plugins/freeverb/Makefile
config.status: creating plugins/pandelay/Makefile
config.status: creating plugins/doublechorus/Makefile
config.status: creating Doxyfile
config.status: creating utils/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
configure:

  MusE configured

  LASH support:                  yes
  DSSI support:                  yes
  FluidSynth:                    yes

  jade:                          jade
  doxygen:                       no
  graphviz:                      no
  perl:                          /usr/bin/perl
  treeviews in doxygen
  html output:                   yes

  C++ compiler:                  g++
  optimizing:                    yes
  debug:                         no
  optimise for arch:             pentium4
  SSE optimizations              no
  python bindings:               yes

  installation prefix:           /usr

  Deprecated:
  ---------------------------------------------------
  using rtcap:                   no
  setuid root install:           no
  setuid root build:             no
  VST/win support:               no



Strange, isn't it? 

Greetings,
Michael

---

### Post by JC Cheloven on 2010-01-07
> **philip5 said:**
> You are welcome.

Hope you didn't miss the packages of traverso 0.49.1, muse 1.0 and jack-mixer 8 that you also find on my repo that all seam to be requested.  All only for Karmic so far though.
Of course :-) I installed muse 1.0 from your repo, but didn't test it extensively so far, that's why didn't mention it. (I had already traverso 0.49.1, works nicely). Again, thank you.

---

### Post by Grishka on 2010-01-07
TYVM. nice job.

---

### Post by m0o on 2010-01-07
Does anyone know if there are any packages for guitar tuners? I have yet to find one that takes MIC input.

---

### Post by trulan on 2010-01-07
> **m0o said:**
> Does anyone know if there are any packages for guitar tuners? I have yet to find one that takes MIC input.
There's fmit, but it needs patched to be compatible with the current version of Jack.  I think if you got the .deb from debian sid it would work in Ubuntu as well.  The version of fmit in Ubuntu currently doesn't work - unless they fixed it in the past two weeks or so.  And like I said if you build it from source it needs patched.

---

### Post by lunar_shuttle on 2010-01-08
Weird! But good!

One thing though - the screenshot is actually not related to the Python-bindings (although the scripts used for these plugins are based on python - but they do not need to be).

The Python bindings are used to control MusE via Pyro, so you need sudo apt-get install pyro as well. There is an example script in muse-1.0/share/pybridge/musepclient.py

---

### Post by m0o on 2010-01-08
> **trulan said:**
> There's fmit, but it needs patched to be compatible with the current version of Jack.  I think if you got the .deb from debian sid it would work in Ubuntu as well.  The version of fmit in Ubuntu currently doesn't work - unless they fixed it in the past two weeks or so.  And like I said if you build it from source it needs patched.

Fantastic! Just what I was looking for. Thank you.

---

### Post by babarosa on 2010-01-08
Mathias wrote,

"...One thing though - the screenshot is actually not related to the Python-bindings (although the scripts used for these plugins are based on python - but they do not need to be)."

Ooops :oops: I meant it well, but that is truly the only one thing I do not know about GNU/Linux!!!

Greetings,
Michael

---

### Post by philip5 on 2010-01-10
Rakarrack 0.3.0 can now be found on my PPA uploaded on request.

Description: Simple and easy guitar effects processor for GNU/Linux Rakarrack is a guitar effects processor for GNU / Linux simple and easy to use but it contains features that make it unique in this field of applications.

Currently it contains 17 effects:
  * Linear Equalizer
  * Parametric Equalizer
  * Compressor
  * Distorsion
  * Overdrive
  * Echo
  * Chorus
  * Phaser
  * Flanger
  * Reverb
  * WahWah
  * Alienwah
  * Harmonizer
  * NoiseGate
  * Musical Delay
  * Cabinet
  * AutoPan/Extra Stereo

Rakarrack integrates a tuner and a MIDI converter. It can also be handled by an external MIDI controller. The settings designed by the user can be stored in presets and these presets can be used to create banks of effects.

---

### Post by sanket_s on 2010-01-11
> **m0o said:**
> Does anyone know if there are any packages for guitar tuners? I have yet to find one that takes MIC input.

There is lingot, a pretty nice guitar tuner, tunes other instruments as well. 

For newbies there is GTick, a simple metronome. And Tuxguitar to access guitar pro files.

---

### Post by ignotus666 on 2010-01-12
Hi all!

First of all thanks for making all these programs easily available for noobs like me - your efforts are much appreciated.

I'm not too sure this is the right place to post this, but if not hopefully someone can point me in the right direction.

Here's my problem: I recently installed dssi-vst from the ppa here and was happily using a few vst's with hydrogen, ardour and jack. But suddenly. a couple of days ago, both hydrogen and ardour refused to start. When I try starting them in a terminal, i get the following message:

loading default ui configuration file /etc/ardour2/ardour2_ui_default.conf
loading user ui configuration file /home/daryl/.ardour2/ardour2_ui.conf
Loading ui configuration file /etc/ardour2/ardour2_ui_dark.rc
theme_init() called from internal clearlooks engine
ardour: [INFO]: Ardour will be limited to 1024 open files
loading system configuration file /etc/ardour2/ardour_system.rc
loading user configuration file /home/daryl/.ardour2/ardour.rc
ardour: [INFO]: No H/W specific optimizations in use
VST_PATH not set, defaulting to /home/daryl/vst:/usr/local/lib/vst:/usr/lib/vst
RemoteVSTClient: all cache files are up-to-date, not running scanner
terminate called after throwing an instance of 'RemotePluginClosedException'
Aborted

Hydrogen does the same.

What I don't get is this vst_path stuff - I'm not running any vst's nor vsthost or anything so what could this be about? As soon as I uninstall dssi-vst things go back to normal again so it's something to do with that. I've tried reinstalling all the programs involved, rebooting, but to no avail, only uninstalling dssi-vst does the trick.

Anyone here have an idea as to what's wrong, or where I should be asking this?

Thanks in advance!

---

### Post by philip5 on 2010-01-12
> **ignotus666 said:**
> 
Here's my problem: I recently installed dssi-vst from the ppa here and was happily using a few vst's with hydrogen, ardour and jack. But suddenly. a couple of days ago, both hydrogen and ardour refused to start. When I try starting them in a terminal, i get the followin

What I don't get is this vst_path stuff - I'm not running any vst's nor vsthost or anything so what could this be about? As soon as I uninstall dssi-vst things go back to normal again so it's something to do with that. I've tried reinstalling all the programs involved, rebooting, but to no avail, only uninstalling dssi-vst does the trick.

Anyone here have an idea as to what's wrong, or where I should be asking this?

Thanks in advance!
Is it my PPA with dssi-vst that gives you this problem or someone else's PPA? If so I can't look into the package (that should work) until tomorrow evening. It would be great to know if someone else also have this problem with my dssi-vst.

Also, do you use any other 3rd party repo/PPA that could give some kind of problem here?

---

### Post by ignotus666 on 2010-01-13
Hi

It first happened with the one from your ppa, which made me think it might be something specific to that one, because with Jaunty I never had a problem with dssi-vst compiled from source (I have Karmic now). Today I compiled it instead of installing from the repository (used the fix where a line -include <stdio.h>- had to be added to a few files) and the exact same thing happens. I also found that movie player (totem) won't start either, giving the same message with the vst_path stuff. For the time being what I do is open ardour, hydrogen, etc, and then I install dssi-vst and open my vst's - a pretty sloppy workaround but at least it works.
The only ppa's/3rd party repo's I use are the ones I found on this thread.

Thanks for replying and if you need any more info just tell me.

---

### Post by philip5 on 2010-01-17
Qtractor 0.4.4 without VST support (due to licens issues) is now avalible for Karmic on my PPA if someone is interested of using it or just to try it out.

Have fun!

---

### Post by philip5 on 2010-01-22
Uploaded the brand new Rakarrack 0.4.2 for karmic on my repo for anyone who wants some guitar fun.

> Changes: New features have been added, including two new effects, Analog Phaser and Derelict Distortion, Limiter at the end of the chain, Four waveshape types for distortion effects, four... LFO types for all the modulated effects, SubOctave, Compresor knee, automatic gain function and stereo mode, Reverse echo, Global Wet/Dry controller, jack MIDI, MIDI learn, scalable fonts, Background images, and new presets. Bugs were fixed, including data for big endian architectures like PowerPC, CPU usage related to computation denormal, and other minor bugs.

[IMG]http://www.ubuntu-pics.de/bild/39250/screenshot_001_9l3r89.png[/IMG]

---

### Post by falkTX on 2010-01-22
> **philip5 said:**
> Uploaded the brand new Rakarrack 0.4.2 for karmic on my repo for anyone who wants some guitar fun.

Finally it looks nice (old versions had poor GUI).

Thanks for this, I'll copy it to my Lucid PPA

---

### Post by AutoStatic on 2010-01-22
Looks good, and with the MIDI learn functionality it's very useful for me. Thanks for packaging!
And maybe you guys could take a look at the following projects: [Arpage]("https://sourceforge.net/projects/arpage/") and [Yoshimi]("https://sourceforge.net/projects/yoshimi/")
There are no packages available yet so maybe you could provide those?

---

### Post by AutoStatic on 2010-01-22
Oh, and falkTX, thanks for the information on packaging you provided earlier in this thread. I took some time to work it all out and managed to set up a PPA: [https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa)
For starters, I've uploaded recordMyDesktop because that package is currently kind of broken: [https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/448027](https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/448027)

---

### Post by philip5 on 2010-01-22
> **AutoStatic said:**
> Looks good, and with the MIDI learn functionality it's very useful for me. Thanks for packaging!
And maybe you guys could take a look at the following projects: [Arpage]("https://sourceforge.net/projects/arpage/") and [Yoshimi]("https://sourceforge.net/projects/yoshimi/")
There are no packages available yet so maybe you could provide those?
I have packaged Arpage for Karmic now and it's avalible on my repo. I'll try to package Yoshimi later this evening.

Here is a little screenshot from Arpage for the interested to look at :)

[[img]http://www.ubuntu-pics.de/thumb/39290/screenshot_002_3QH8lR.png[/img]](http://www.ubuntu-pics.de/bild/39290/screenshot_002_3QH8lR.png)

---

### Post by AutoStatic on 2010-01-22
That's fast, thanks!

---

### Post by babarosa on 2010-01-22
Dear Philip5,

I hope you won't feel uncomfortable, but from time to time I am forced to mention that you are great and your efforts are very much appreciated \\:D/

With my kindest regards,
Michael

---

### Post by philip5 on 2010-01-22
> **babarosa said:**
> Dear Philip5,

I hope you won't feel uncomfortable, but from time to time I am forced to mention that you are great and your efforts are very much appreciated \\:D/

With my kindest regards,
Michael
You're welcome. It's more fun to work with a repo that is alive and in use and not just for my own pleasure. To be frank, I don't even use these kind of music apps so I package them as the upstream developers intend them to be, check out that they work/start and leave the rest for upstream to do the fixing.

I have added so both Yoshimi and Arpage shows up in your menu but that's not standard and they don't have any icons yet so for the moment the icon looks like it does in your menu. I could change the icon to something more appealing if you like that is some general purpose icon on Ubuntu as a temporary solution until they make their own icons.

Speaking about fixing. I have now uploaded packages of Yoshimi 0.044 for Karmic to my repo. Yoshimi 0.053 is the latest though but have some serious problems working with jackd in both RT-mode and non-RT (this is features that the developers are working on what I have found out) so until that is fixed you have to play with the 0.044 release that seam to work as it should. If you like Yoshimi and find it useful then let me know when there is any update of it and I can make an updated package.

Here you have screenshots och Yoshimi 0.044 in basic and advanced GUI-mode:

[[img]http://www.ubuntu-pics.de/thumb/39332/screenshot_004_USCk4J.png[/img]](http://www.ubuntu-pics.de/bild/39332/screenshot_004_USCk4J.png)[[img]http://www.ubuntu-pics.de/thumb/39333/screenshot_003_k8171e.png[/img]](http://www.ubuntu-pics.de/bild/39333/screenshot_003_k8171e.png)

---

### Post by AutoStatic on 2010-01-22
Cool! And good to know 0.053 has some serious issues. 0.044 is ok, works better than ZynAddSubFX 2.4.0 for me.

---

### Post by philip5 on 2010-01-22
> **AutoStatic said:**
> Cool! And good to know 0.053 has some serious issues. 0.044 is ok, works better than ZynAddSubFX 2.4.0 for me.
Btw, I updated the ZynAddSubFX banks in 0.044 with the newer/more/better (I hope) banks from 0.053 so you'll have the banks goodies from that version anyway with my package...

---

### Post by AutoStatic on 2010-01-22
The banks are from ZASFX 2.4.0 so there are not really much differences I think.

---

### Post by philip5 on 2010-01-22
> **AutoStatic said:**
> The banks are from ZASFX 2.4.0 so there are not really much differences I think.
Yoshimi 0.044 doesn't include any zynaddsubfx files by it self (which 0.053 does) but finds the versions of the zynaddsubfx package/install you have so which version of zynaddsubfx you use is otherwise what Yoshimi 0.044 will find. In Karmic that would be version 2.2.1-4.1.

Anyway, I made it install 2.4.0 with Yoshimi 0.044 so it will be what it use for sure. Not sure though what happens if Yoshimi finds zynaddsubfx files that are duplicates and from different versions. If anyone finds any problems with this then let me know.

---

### Post by philip5 on 2010-01-24
And now you guys also have Qtractor 0.4.5 (still no VST support due to license issues) avalible on my repo.

---

### Post by AutoStatic on 2010-01-25
Nice! I use Qtractor a lot so good to have a new version available and packaged, thanks!

---

### Post by philip5 on 2010-01-25
> **AutoStatic said:**
> Nice! I use Qtractor a lot so good to have a new version available and packaged, thanks!
You're welcome. 

It's just a shame though that Qtractor use Steinbergs VST and not the free and open VST that comes with the DSSI-VST project. Steinberg forbidds distribution of its VST-stuff in the license so you can't package the support for it and put it on a repo, only use it for your self... :(

---

### Post by mango42 on 2010-01-27
Now that I've finally got Karmic Studio working (sorta - minus Grub!) I'd firstly like to offer a very heartfelt thanks indeed to **philip5** for enabling us non-programmers to try out the latest versions of software. I'm particularly looking forward to Muse 1 & the latest Rackarrack.

Now onto AutoStatic's links to firewire nirvana ;-)

---

### Post by philip5 on 2010-01-27
And now you guys also have the latest (and greatest) Ardour 2.8.6. I also bumped up the versions of the following two packages: vamp-plugin-sdk 2.1 and rubberband 1.3. Moore goodies (more or less) with that too I guess, not exactly sure what's new though.

[edit]
And now also Muse 1.0.1 with Python support (finally detects python correctly during build) for Karmic.

---

### Post by falkTX on 2010-01-28
> **philip5 said:**
> And now you guys also have the latest (and greatest) Ardour 2.8.6. I also bumped up the versions of the following two packages: vamp-plugin-sdk 2.1 and rubberband 1.3. Moore goodies (more or less) with that too I guess, not exactly sure what's new though.

[edit]
And now also Muse 1.0.1 with Python support (finally detects python correctly during build) for Karmic.

@philip5:

I've sucessfully build Ardour 2.8.6 with VST support, so please check it out cause users might want it. VST is not possible for 64bit yet.

Also, can you write a little intro to your PPA? I no longer maintain my Music PPA (moved all my efforts to Lucid), so it might trick users to think my PPA has your stuff.

PM me with the new content and I'll modify the first post.

---

### Post by jsevi83 on 2010-01-28
why don't you build the latest version of rubberband, 1.4? It is out since september 2009, don't know why we use an outdated version.

---

### Post by philip5 on 2010-01-28
> **jsevi83 said:**
> why don't you build the latest version of rubberband, 1.4? It is out since september 2009, don't know why we use an outdated version.
Good question. So to answer that I made an update of rubberband to 1.4 for Karmic. Was first a bit afraid that it would be an update that needed apps depended on it to be built but that's not the case what it seams. :)

---

### Post by AutoStatic on 2010-01-29
Hello Philip, I'm having a real hard time getting the latest [MilkyTracker]("http://milkytracker.org/") release to compile for Karmic. Maybe you could take a look at it. The maintainer already has some useful stuff available: [http://gnu.ethz.ch/debian/milkytracker/2010/](http://gnu.ethz.ch/debian/milkytracker/2010/). Thanks!

---

### Post by philip5 on 2010-01-29
> **AutoStatic said:**
> Hello Philip, I'm having a real hard time getting the latest [MilkyTracker]("http://milkytracker.org/") release to compile for Karmic. Maybe you could take a look at it. The maintainer already has some useful stuff available: [http://gnu.ethz.ch/debian/milkytracker/2010/](http://gnu.ethz.ch/debian/milkytracker/2010/). Thanks!
Done! Milkytracker 0.90.85 is now avalible on my PPA for Karmic.

I would appreciate if someone running a 32bit Ubuntu 9.10 installation could verify that it run correctly (it should but I haven't been able to verify it) as the build use a 64bit patch.

Here is also a screenshot for anyone who wonder what this app is all about and it's more impressive than it looks...

[[img]http://www.ubuntu-pics.de/thumb/40252/screenshot_005_ke7AKl.png[/img]](http://www.ubuntu-pics.de/bild/40252/screenshot_005_ke7AKl.png)

[edit]
Also added the latest guitarix 0.05.8 to my repo.

[[img]http://www.ubuntu-pics.de/thumb/40260/screenshot_006_wu3m73.png[/img]](http://www.ubuntu-pics.de/bild/40260/screenshot_006_wu3m73.png)

[edit 2]
Also added lingot 0.7.7 beta5 which have support for jack. Yeah!

[[img]http://www.ubuntu-pics.de/thumb/40276/screenshot_007_1s0v3G.png[/img]](http://www.ubuntu-pics.de/bild/40276/screenshot_007_1s0v3G.png)

---

### Post by AutoStatic on 2010-01-29
Yeah, MilkyTracker is cool, I really liked FastTracker back in the days and MilkyTracker feels like coming home. I also applied the 64bit patch but got stuck at the zlib.h dependency. Thanks for sorting it out!

---

### Post by philip5 on 2010-01-30
> **AutoStatic said:**
> Yeah, MilkyTracker is cool, I really liked FastTracker back in the days and MilkyTracker feels like coming home. I also applied the 64bit patch but got stuck at the zlib.h dependency. Thanks for sorting it out!
Btw, you were missing the zlib1g-dev package on your system that contains the zlib.h that was missed during your build.

---

### Post by AutoStatic on 2010-01-30
> **philip5 said:**
> Btw, you were missing the zlib1g-dev package on your system that contains the zlib.h that was missed during your build.Yeah, now I see, mixed things up (libzzip-dev and zlib1g-dev). Also because of the MilkyTracker README. Thanks for pointing it out!

---

### Post by philip5 on 2010-01-30
> **AutoStatic said:**
> Yeah, now I see, mixed things up (libzzip-dev and zlib1g-dev). Also because of the MilkyTracker README. Thanks for pointing it out!
I don't think you really mixed them up as they are both needed. It's not something you might figure out by just reading the readme but it's more obvious when zlib.h is called on as an include in the code and breaks if it's missing (might say that's missing in the documentation) Then you have to be a bit of a Sherlock Holmes to detect which package that includes the header (trivial task if you know how to look throu packages content).

Anyway, my package works just fine so feel free to use it instead but as you gave the build a try and it didn't work it might be good to know what broke it...

---

### Post by AutoStatic on 2010-01-30
It's this part of the README that confused me:
> Note to package maintainers: MilkyTracker contains an internal copy of libzzip that has been modified for use with MilkyTracker; An externally
linked libzzip will not work correctly (ZIP support will be broken).

And there's a zlib directory in /src/compression so I thought the zlib.h includes in the /src/compression/zziplib had to point to that specific zlib directory. But zlib can be linked externally.

---

### Post by philip5 on 2010-02-01
Does anyone have any more suggestions on what I could/should update/add and package for upload to my repository to make it even more usefull?

Off topic:
Tomorrow I will be up against the EMEA membership board for them to decide if I will be granted Ubuntu membership. If anyone here feel like endorsing me for being me and/or my work then feel free to add a few lines about me on the wiki page about me at: [https://wiki.ubuntu.com/philip5](https://wiki.ubuntu.com/philip5)

---

### Post by AutoStatic on 2010-02-01
Yup, you might want to take a look at Minicomputer: [http://minicomputer.sourceforge.net/](http://minicomputer.sourceforge.net/)

And there are some nice things going on concerning vocoders/autotuners, like jretune (not released yet, from the author of jconvolver) and VocProc ([http://hyperglitch.com/dev/VocProc/](http://hyperglitch.com/dev/VocProc/)).

I'll check your Wiki page :)

---

### Post by philip5 on 2010-02-02
> **AutoStatic said:**
> Yup, you might want to take a look at Minicomputer: [http://minicomputer.sourceforge.net/](http://minicomputer.sourceforge.net/)

Now you guys have Minicomputer 1.41 avalible on my repo. Their own description: ""Minicomputer is a standalone Linux softwaresynthesizer for creating experimental electronic sounds as its often used in but not limited to Industrial music, IDM, EBM, Glitch, sound design and minimal electronic. It is monophonic but can produce up to 8 different sounds at the same time.
It uses Jack as realtime audio infrastructure and can be controlled via Midi.""

It's not the prettiest or most straight forward app ever made but maybe have some great fun for the right person. It works with jack so you can play around with it regarding with that. You have a few presets in /usr/share/minicomputer and also full documentation as a pdf in /usr/share/docs/minicomputer.


The thing looks like this for the curious one:

[[img]http://www.ubuntu-pics.de/thumb/40726/screenshot_008_V0PLVf.png[/img]](http://www.ubuntu-pics.de/bild/40726/screenshot_008_V0PLVf.png)

---

### Post by AutoStatic on 2010-02-02
Awesome, thanks! I was working on it to package it myself but it uses scons instead of plain make.

---

### Post by philip5 on 2010-02-02
> **AutoStatic said:**
> 
And there are some nice things going on concerning vocoders/autotuners, like jretune (not released yet, from the author of jconvolver) and VocProc ([http://hyperglitch.com/dev/VocProc/](http://hyperglitch.com/dev/VocProc/)).

As you guys know, a wish from you guys in this thread is my command (almost at least...). Here it is:

VocProc 0.12.2 is now avalible on my repository for Karmic.

"VocProc is a real time vocal processing software for Linux, witten by Igor Brki&#263;. It can be used for singing voice pitch shifting with or without formant correction, automatic pitch correction, vocoder effect and harmonizer. Currently it is distributed as standalone JACK application but there are plans to build it also as a plugin (LV2 and maybe VST). It is in early alpha stage of development."

And the mandatory screenshot: :guitar:

[[img]http://www.ubuntu-pics.de/thumb/40836/screenshot_010_gR5IXQ.png[/img]](http://www.ubuntu-pics.de/bild/40836/screenshot_010_gR5IXQ.png)

Off topic: Today I was granted Ubuntu membership so especially thanks to **AutoStatic** here in this thread for giving me his endorsment on the wiki page. :)

---

### Post by AutoStatic on 2010-02-03
Congrats! That's what communities are for :)
And thanks for the VocProc package, it's quite a nice, neat little toy. Make sure you don't set your buffers too low because VocProc demands some processing power/time.
Thanks again for packaging all this really cool stuff philip5 :D

---

### Post by philip5 on 2010-02-03
> **AutoStatic said:**
> Congrats! That's what communities are for :)
And thanks for the VocProc package, it's quite a nice, neat little toy. Make sure you don't set your buffers too low because VocProc demands some processing power/time.
Thanks again for packaging all this really cool stuff philip5 :D
You're welcome!

I took some time to polish a few of the packages that was missing menu icons as the upstream projects for them doesn't have any yet so I added a generic temp icon (a speaker) so it look nicer in your menues. If someone have a suggestion of an other generic icon I'm open to suggestion.

Hope you guys haven't missed the update of Yoshimi that got a make some nice work from the developers.

---

### Post by Stochastic on 2010-02-03
Philip5,  You may want to consider uploading some of your packages (the ones not yet in Ubuntu's repos) to the Ubuntu REVU system at [http://revu.ubuntuwire.com](http://revu.ubuntuwire.com) so that they can be peer reviewed by the MOTU uploaders (nagging them to review is often the hardest part) and after two positive peer reviews the packages will become official Ubuntu packages for everyone to enjoy.

If you are open to this idea, I should mention that the Lucid feature freeze is on Feb 18th, so if you want to aim to get your packages into Lucid then they need two passing reviews before that date.  A great place to nag the uploaders is in #ubuntu-motu on irc.freenode.net  Let me know if you are planning to try this.

---

### Post by philip5 on 2010-02-03
If I should make some of my packages in this thread uploaded to Ubuntu REVU then they could need some cleaning up and propper changelogs.

Any wishes here what I should give priority that you feel more is a "must have" in Lucid? Which apps are best and what packages do you guys use (more then just fun to test) of these packages? Have to coordinate it with falkTX too so we doesn't double work.

---

### Post by naught101 on 2010-02-07
Very tidy display, you lot. Very nice indeed. Thanks for all your hard work, especially on LADISH, will be great to see that in ubuntu in the future.

This isn't a request, so much as an idea: **Ardour3**. It's due for release any time soon (not that I know what that means), and it would be worth it simply for the fact that it'd get a lot more beta testers for the project. It's a bit hard to say whether it'll actually be out before Lucid is, but it seems a distinct possibility, and it'd be a real shame to see it missing from what looks to be a very nice ubuntu-studio release, just because it missed the feature freeze.

That said, I'm just heading towards my fourth hour compiling it for karmic, so it's not a walk in the park...

It uses waf to compile, build and install. If possible, it'd be good to be able to suffix it or something, so that it could be installed alongside 2.8.x (I have no idea how difficult that is)

---

### Post by prokoudine on 2010-02-07
> **naught101 said:**
> This isn't a request, so much as an idea: **Ardour3**. It's due for release any time soon
Oh, it's not. A3 is officially an alpha and recommended for closed testing only. Paul even asked not to spread the word about alpha testing. So what exactly are you trying to achieve? :)

---

### Post by philip5 on 2010-02-07
I don't know why there is no update of Hydrogen to 0.9.4, that is a fun and decent drum machine that now is made all in QT4 and is even nicer, in either Ubuntu or Debian. Anyway, I packaged it and uploaded it to Launchpad for Karmic as usuall. 

Here is the mandatory screenshot for my postings in this thread: :)

[[img]http://www.ubuntu-pics.de/thumb/41459/screenshot_013_X2B64S.png[/img]](http://www.ubuntu-pics.de/bild/41459/screenshot_013_X2B64S.png)


> **naught101 said:**
> 

It uses waf to compile, build and install. If possible, it'd be good to be able to suffix it or something, so that it could be installed alongside 2.8.x (I have no idea how difficult that is)

With a program like Ardour it might not be such a conflict and if you want to play it real safe and keep testing/develop releases like this appart then you can always compile it to be installed in /opt or something like that.

As the freeze for Lucid is close I guess we won't see any Ardour 3.0 in the official release at least.

---

### Post by naught101 on 2010-02-07
> **prokoudine said:**
> Oh, it's not. A3 is officially an alpha and recommended for closed testing only. Paul even asked not to spread the word about alpha testing. So what exactly are you trying to achieve? :)

o_O Whoops, I didn't realise it was closed. Ignore me. I'm still not used to the Ardour development model.

---

### Post by jimy_james on 2010-02-07
Just wanted to say. thanks a million philp5.  This ppa has everything I've been looking for.  Brilliant.

---

### Post by philip5 on 2010-02-07
> **jimy_james said:**
> Just wanted to say. thanks a million philp5.  This ppa has everything I've been looking for.  Brilliant.
You're welcome. It's good to hear that the PPA is appreciated and comes to use. I also like if someone notice me if I've misses to update something or if someone find other cool stuff that would benefits the PPA and people using it.

So keep on being creative and have fun! :D

---

### Post by naught101 on 2010-02-07
vmpk would be a good one. Though it doesn't seem to have jack support or midi out yet.

---

### Post by AutoStatic on 2010-02-08
> **philip5 said:**
> I don't know why there is no update of Hydrogen to 0.9.4, that is a fun and decent drum machine that now is made all in QT4 and is even nicer, in either Ubuntu or Debian. Anyway, I packaged it and uploaded it to Launchpad for Karmic as usuall.Hello Philip, 0.9.5-beta1 is the latest stable release. If you don't mind I've already uploaded it to [my own PPA]("https://launchpad.net/%7Eautostatic/+archive/ppa/+packages") with the help of your package files.

---

### Post by philip5 on 2010-02-08
> **AutoStatic said:**
> Hello Philip, 0.9.5-beta1 is the latest stable release. If you don't mind I've already uploaded it to [my own PPA]("https://launchpad.net/%7Eautostatic/+archive/ppa/+packages") with the help of your package files.
I don't mind but isn't it a bit contradictive to say that a beta is the latest stable?!?! :P

I noticed the beta1 too yesterday but I didn't package it yet. I think I'll update it to the beta1 on my site too.
> **naught101 said:**
> vmpk would be a good one. Though it doesn't seem to have jack support or midi out yet.
I'll look into that, but from a quick read in their site it looks like it have jack support or maybe that is just something they plan...

I get back to you guys on that one.

---

### Post by AutoStatic on 2010-02-08
> **philip5 said:**
> I don't mind but isn't it a bit contradictive to say that a beta is the latest stable?!?! :PYou're absolutely right :D

---

### Post by philip5 on 2010-02-08
> **AutoStatic said:**
> You're absolutely right :D
Just a little pointer. You shouldn't name your beta package hydrogen_0.9.5-beta1~autostatic0 as that will give you problems to auto update when you package the final. You should name it with a ~ instead of a - like this: hydrogen_0.9.5~beta1~autostatic0 as apt will think hydrogen_0.9.5~autostatic0 is an older package when you name it like in the first place. hydrogen_0.9.5~beta1-autostatic0 might be even better.

---

### Post by AutoStatic on 2010-02-08
Thanks for the pointer! That packaging stuff is not self-evident :D

---

### Post by philip5 on 2010-02-09
VMPK - Virtual MIDI Piano Keyboard ([http://vmpk.sourceforge.net](http://vmpk.sourceforge.net)) version 0.3.1 is now avalible for Karmic on my PPA at Launchpad.

"Virtual MIDI Piano Keyboard is a MIDI events generator and receiver. It doesn't produce any sound by itself, but can be used to drive a MIDI synthesizer (either hardware or software, internal or external). You can use the computer's keyboard to play MIDI notes, and also the mouse. You can use the Virtual MIDI Piano Keyboard to display the played MIDI notes from another instrument or MIDI file player. To do so, connect the other MIDI port to the input port of VMPK."

[[img]http://www.ubuntu-pics.de/thumb/41858/screenshot_014_Xf0ZYU.png[/img]](http://www.ubuntu-pics.de/bild/41858/screenshot_014_Xf0ZYU.png)

Next avalible app might not be so much for production but maybe more for fun or something (it can output to Jack). 

"KMid2 is a MIDI/Karaoke player for KDE4

 KMid was developed more than ten years ago, so it was time for a revamping.
 KMid2 is a rewrite from scratch, with a new architecture and also some new features.
 
 Some major features:
 * Plays MIDI and Karaoke files.
 * Playback to external hardware MIDI devices.
 * Allows to use software synths as well.
 * Tempo and volume controls.
 * Pitch (transpose) control.
 * Rhythm view (visual metronome).
 * Configurable character encoding, font and color for lyrics.
 * Playlists (song collections).
 * MIDI Mapper.
 * Channels window, with solo/muting controls and instrument selectors.
 * Piano player window, using VMPK artwork and technology.
 * Runs in Linux, using the ALSA Sequencer."

[[img]http://www.ubuntu-pics.de/thumb/41867/screenshot_015_3eqMFb.png[/img]](http://www.ubuntu-pics.de/bild/41867/screenshot_015_3eqMFb.png)

Have fun! :)

---

### Post by falkTX on 2010-02-10
> **naught101 said:**
> This isn't a request, so much as an idea: **Ardour3**. It's due for release any time soon (not that I know what that means), and it would be worth it simply for the fact that it'd get a lot more beta testers for the project. It's a bit hard to say whether it'll actually be out before Lucid is, but it seems a distinct possibility, and it'd be a real shame to see it missing from what looks to be a very nice ubuntu-studio release, just because it missed the feature freeze.

I guess you're in luck.
Download the Latest Lucid now - [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.iso](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.iso)

My Lucid (Bleeding-Edge) PPA - [https://launchpad.net/~falk-t-j/+archive/lucid-latest/](https://launchpad.net/~falk-t-j/+archive/lucid-latest/) - has the latest of latest:
- Ardour 3.0
- Blender 2.5
- Calf Plugins
- Ingen/Patchage (drobilla-lad)
- Hydrogen
- Kdenlive (with my patch for Jack Transport support)
- Ladish
- Laditools
- LMMS

And Games:
- Speed-Dreams
- Supertuxkart


Enjoy!

---

### Post by trulan on 2010-02-16
Rosegarden Thorn!
per this thread:
[http://ubuntuforums.org/showthread.php?t=1407005](http://ubuntuforums.org/showthread.php?t=1407005)

---

### Post by philip5 on 2010-02-16
Speaking about Rosegarden, I just uploaded Open Octave Midi 1.7.3 git 100215 ([http://www.openoctave.org/software](http://www.openoctave.org/software)) to my Launchpad repository for Karmic. Open Octave Midi is still in early development and is based on Rosegarden. Here is their own description:

> Open Octave Midi is the initial program under development in the Open Octave Project. It was chosen as such to provide an extensive range of tools for the composer who's workflow is heavily dependent on a midi working environment, particularly those users who write orchestral music. Currently, the team are working on the editors, and examining working technique right down to the last key or mouse stroke, with the intent of making the workflow as efficient as possible. Open Octave Midi is based around a main arrange window, and Matrix, Percussion, and Event List Editors. It's designed with only midi, and midi editing in mind. We haven't included audio, as Linux Audio already has a great program called Ardour, to handle audio needs, and we chose to not include notation, as this is such a complex component, we feel this can only really develop to a much greater potential as a standalone application within a Linux Audio professional suite.

Open Octave Midi has fairly simple goals: Midi recording and editing, in an environment to perform these tasks quickly and efficiently, using powerful tools at the foundation of the program. You won't find "Hollywood" features in Open Octave Midi, nor "clever" features to automate, and by nature of this particular technique, add a "mechanical" element to your recordings. What the user will have is simple and powerful tools, specifically designed within a total workflow oriented environment, to do the job day in day out, without problems.

And the mandatory screenshot: :)

[[img]http://www.ubuntu-pics.de/thumb/42937/screenshot_017_iYz3LC.png[/img]](http://www.ubuntu-pics.de/bild/42937/screenshot_017_iYz3LC.png)

---

### Post by philip5 on 2010-02-16
> **trulan said:**
> Rosegarden Thorn!
per this thread:
[http://ubuntuforums.org/showthread.php?t=1407005](http://ubuntuforums.org/showthread.php?t=1407005)
Done, Rosegarden 10.02 is now avalible for Karmic on my PPA.

Off topic: I think it looks ugly though. It's now a QT4 app that they tried hard to keep looking like a QT3 app...

---

### Post by philip5 on 2010-02-18
An open question to you all in this thread: 

Do you guys use Frescobaldi ([http://www.frescobaldi.org)?](http://www.frescobaldi.org)?) I noticed that they have been doing alot with it since the version that comes with Karmic. Is it a good app or what do you think? Is there any interest in getting a updated version or is that something that doesn't matter, more or less?

What do you guys think about it?

---

### Post by philip5 on 2010-02-19
Backported the updated version of sooperlooper 1.6.14 from Lucid to Karmic.

"SooperLooper is a live looping sampler capable of immediate loop recording, overdubbing, multiplying, reversing and more. It allows for multiple simultaneous multi-channel loops limited only by your computer's available memory.

The application is a standalone JACK client with an engine controllable via OSC and MIDI. It also includes a GUI which communicates with the engine via OSC (even over a network) for user-friendly control on a desktop. However, this kind of live performance looping tool is most effectively used via hardware (midi footpedals, etc) and the engine can be run standalone on a computer without a monitor."

[[img]http://www.ubuntu-pics.de/thumb/43279/screenshot_018_r35y7F.png[/img]](http://www.ubuntu-pics.de/bild/43279/screenshot_018_r35y7F.png)

---

### Post by mango42 on 2010-02-19
Wonderful - thanks very much for **sooperlooper**, philip5

As for frescobaldi, I have to admit to not having read sheet music for over 20 years now - it just comes into & out of my ears ;-)

---

### Post by AutoStatic on 2010-02-19
Same here, I don't use Lilypond or Frescobaldi or any other notation software, I can't read notes or sheet music.

---

### Post by philip5 on 2010-02-26
More requests of good, nice or interesting music apps, plugins, etc that you think are missing in Ubuntu (Karmic) are welcome. Either just updates to more cutting edge or brand new experiences are up for suggestion.

---

### Post by jsevi83 on 2010-02-26
Would be very nice to have EQ10Q, a LV2 Graphical Equalizer. It depends on lv2-C++-tools, which is also needed in karmic. Another suggestion would be a LV2 Plugin called VocProc, from version 0.2. In your repository the version 0.12.2 is a standalone application, not developed anymore. Thank you.

---

### Post by philip5 on 2010-02-26
> **jsevi83 said:**
> Would be very nice to have EQ10Q, a LV2 Graphical Equalizer. It depends on lv2-C++-tools, which is also needed in karmic. Another suggestion would be a LV2 Plugin called VocProc, from version 0.2. In your repository the version 0.12.2 is a standalone application, not developed anymore. Thank you.
I'll take a look on those requests this weekend and upload what I get working and looks promising.

More requests are welcome if you guys out there have any...

[edit]
EQ10Q is now uploaded to my Launchpad repository and that means that lv2-C++-tools 1.0.3 and Plotmm 0.1.2 also have been uploaded as EQ10Q depend on them.

Here is a screenshot of EQ10Q that is a lv2 plugin and have to be used with software that can use lv2 plugis (i.e Ardour). Have fun! :)

[[img]http://www.ubuntu-pics.de/thumb/44465/screenshot_019_Qyx92V.png[/img]](http://www.ubuntu-pics.de/bild/44465/screenshot_019_Qyx92V.png)

---

### Post by babarosa on 2010-02-27
Dear Philip5,

> More requests of good, nice or interesting music apps

Kindly I'd suggest:
JackBeat (v0.7.4), a loop rhythmic arranger, and swami (v2.0), a sf2 editor/manager could be of interest for the people.

Thanks and greetings,
Michael

---

### Post by philip5 on 2010-02-27
> **jsevi83 said:**
> Another suggestion would be a LV2 Plugin called VocProc, from version 0.2. In your repository the version 0.12.2 is a standalone application, not developed anymore. Thank you.
You guys now have vocproc-lv2 0.2 on my repository too. vocproc-lv2 is a separate package to the vocproc package as vocproc is standalone and works with jack. vocproc-lv2 only works with lv2 enabled apps.

Here is the sceenshot:

[[img]http://www.ubuntu-pics.de/thumb/44471/screenshot_020_6sE259.png[/img]](http://www.ubuntu-pics.de/bild/44471/screenshot_020_6sE259.png)

---

### Post by philip5 on 2010-02-27
> **babarosa said:**
> 
JackBeat (v0.7.4), a loop rhythmic arranger, and swami (v2.0), a sf2 editor/manager could be of interest for the people.

JackBeat 0.7.4 is now uploaded to my repository as a backport from Lucid.

I can only find a 0.9.4 version of swami and 2.0 code in trunk but the 2.0 code haven't been touched for 16 months so the project seams dead. Don't know how close to being finished either. Not sure if it's worth packaging 2.0 or if 0.9.4 is enough?

---

### Post by jsevi83 on 2010-02-27
Whow, thank you so much, that was fast. I just realized Gnome Wave Cleaner (gwc) is not updated in the ubuntu repositories. Version 0.21.10 is ready for almost a year. I don't know if it's worth the effort.

---

### Post by babarosa on 2010-02-28
Dear Philip5,

> I can only find a 0.9.4 version of swami and 2.0 code in trunk but the 2.0 code haven't been touched for 16 months so the project seams dead. Don't know how close to being finished either. Not sure if it's worth packaging 2.0 or if 0.9.4 is enough?

I compile swami v2.0 by myself because it was removed from the repos because of gtk+ issues. 
It seems to be a fine working application though. From time to time I get in contact with Josh Green, the developer. The project is not dead, but he has got few time to work on it.

Here is a screenshot:
[http://i64.servimg.com/u/f64/12/84/23/35/swami_10.png](http://i64.servimg.com/u/f64/12/84/23/35/swami_10.png)

My thanks and greetings,
Michael

---

### Post by Capoeira on 2010-03-02
@phillip5

I am using your PPA in KArmic but i can't install Amarok because of 3 dependency-problems

---

### Post by luctor on 2010-03-03
I've put up a PPA for Sonic Visualiser

[https://launchpad.net/~rghvdberg/+archive/sv](https://launchpad.net/~rghvdberg/+archive/sv)
 
> Sonic Visualiser is an application for viewing and analysing the contents of music audio files.
[http://sonicvisualiser.org/](http://sonicvisualiser.org/)

This PPA requires Philip Johnsson's ppa [https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra) for dependencies. (librubberband ,vamp,liblo0)

---

### Post by philip5 on 2010-03-03
> **Capoeira said:**
> @phillip5

I am using your PPA in KArmic but i can't install Amarok because of 3 dependency-problems
What are those problems? Hard to help you if you don't be more specific. Package names and versions that fail for you.

---

### Post by Capoeira on 2010-03-03
> **philip5 said:**
> What are those problems? Hard to help you if you don't be more specific. Package names and versions that fail for you.

ow, excuse me, i thougt it would be easy to reproduce

3 depencys from your amarok package require more updated versions than those in karmic:

amarok:
  Depends: kdebase-runtime (>=4:4.3.5) but 4:4.3.2-0ubuntu4.1 will be installed
  Depends: kdelibs5 (>=4:4.3.5) but 4:4.3.2-0ubuntu7.2 will be installed
  Depends: libplasma3 (>=4:4.3.5-0ubuntu1~karmic1) but 4:4.3.2-0ubuntu7.2 will be installed

(translated)

---

### Post by philip5 on 2010-03-03
> **Capoeira said:**
> ow, excuse me, i thougt it would be easy to reproduce

3 depencys from your amarok package require more updated versions than those in karmic:

amarok:
  Depends: kdebase-runtime (>=4:4.3.5) but 4:4.3.2-0ubuntu4.1 will be installed
  Depends: kdelibs5 (>=4:4.3.5) but 4:4.3.2-0ubuntu7.2 will be installed
  Depends: libplasma3 (>=4:4.3.5-0ubuntu1~karmic1) but 4:4.3.2-0ubuntu7.2 will be installed

(translated)
Ok, my repository is built against Primary Archive for Ubuntu - BACKPORTS (main, restricted, universe, multiverse), as you can see in the info about my PPA on my Launchpad site. It looks like you have only activated the Ubuntu main repository and not backports etc. Ubuntu main ships with kde 4.3.2 which is pretty old by now.

---

### Post by Capoeira on 2010-03-03
> **philip5 said:**
> Ok, my repository is built against Primary Archive for Ubuntu - BACKPORTS (main, restricted, universe, multiverse), as you can see in the info about my PPA on my Launchpad site. It looks like you have only activated the Ubuntu main repository and not backports etc. Ubuntu main ships with kde 4.3.2 which is pretty old by now.

OK, i have to excuse one more time.....I added the backports.....I didn't knew i had to activate them to have latest packages....thanks a lot

---

### Post by Capoeira on 2010-03-03
one wish from me for both ppa(s): Jkmeter

---

### Post by philip5 on 2010-03-04
> **Capoeira said:**
> one wish from me for both ppa(s): Jkmeter
I got that request before so I'll have a look at it as soon as I can. (maybe when I get home from work tonight)

---

### Post by philip5 on 2010-03-04
> **Capoeira said:**
> one wish from me for both ppa(s): Jkmeter
And here the little jack app is:
> 
Jkmeter is a horizontal or vertical bargraph level meter based on the  ideas of mastering guru Bob Katz.

This is the type of meter you want for live recording, mixing and mastering. It probably makes no sense to use it on all tracks of a DAW, where keeping digital level within limits is the main purpose of metering.

This release implements the K-20 meter. Future releases will include the K-14 meter as well. 

A K-meter displays both the true RMS level and the digital peak level. The ballistics as defined by Bob Katz are somewhat ambiguous. In this implementation the RMS meter is about 15% faster than an VU, but without the overshoot. This provides a good indication of subjective loudness.

Instead of providing extra gain for the RMS level, the K-meter displays it on the same scale as thedigital peak level, but puts the '0dB' mark and the color change well below the OdB full scale level. For the K-20 meter it is 20dB down, for the K-14 this is (surprise !) 14 dB. 

To use the meter as envisaged by Bob Katz, you should have a fixed monitoring level, adjusted so that pink noise indicating 0dB on the meter corresponds to 83 dB(C) (from each speaker) as indicated by an sound level meter. Note the (C) - not (A) - weighting.

As of release 0.4.0, both japa and jnoise provide a pink noise source at exactly this level.

The current release does not include the 22kHz lowpass filter required for frequencies such as 96kHz and higher.

And the screenshot:

[[img]http://www.ubuntu-pics.de/thumb/45255/screenshot_026_ZTbGmK.png[/img]](http://www.ubuntu-pics.de/bild/45255/screenshot_026_ZTbGmK.png)

---

### Post by Capoeira on 2010-03-04
great...

verry util for people who like to use the k-system

read more about it from the "master-master" himself: [http://www.digido.com/level-practices-part-2-includes-the-k-system.html](http://www.digido.com/level-practices-part-2-includes-the-k-system.html)

---

### Post by philip5 on 2010-03-07
Guitarix 0.06.0 is now avalible for Karmic on my Launchpad repository.

---

### Post by philip5 on 2010-03-12
An open question to you guys:
Do you see any point in porting Jack2 to Karmic or is it too early? Do most apps support jack2 as it is now or is it still considered experimental and non-standard?

I was just updating QjackCtl (localy and not on my PPA) to the latest version but that will probably mean that I have to update jackd to 0.118.0. In 0.118.0 they have changed the use of the realtime parameter to be compatible with jack2 as I understand it, using -r instead of -R. That is changed in the new QjackCtl which gives problems with older jackd (like the one that comes with Karmic).

---

### Post by babarosa on 2010-03-12
Hi Philip5,

"...Do you see any point in porting Jack2 to Karmic...?"

No, I don't. Jack2 never delivered solid performance _on my_ machine running Xubuntu v9.10 with rt-kernel.

I compile jackd 0.118 and qjackctl 0.3.6 (both are the latest versions) and _on my_ machine Xubuntu v9.10 with rt-kernel performs rock solid .

Greetings,
Michael

---

### Post by trulan on 2010-03-12
I agree, I see no reason to port Jack2 to Karmic.  Plus, there are already at least two ppa's that have this, frasten's ppa is the one I have been using.  There are a few key programs, such as Patchage, that don't work at all for me with with Jack .116, so I've been putting up with Jack2.  I will switch to Jack .118 if you package it.  Jack2 is not as stable for me.  Basically, I get a lot more xruns with Jack2 but they are smaller.

---

### Post by AutoStatic on 2010-03-12
I've never tried Jack2, I'm just very content with Jack1 and as long as things like Ladish are still heavily discussed and I don't have a use for netjack I'll stick to Jack1. The only thing where I could gain something with Jack2 might be multithreading.

---

### Post by philip5 on 2010-03-12
I guess that settle things then. I'll update jack in my repository for Karmic to Jack .118 when I get home tonight.

Any other updated upstream projects that I have missed? Must keep the repository alive you know, be the place where it all happen... ;)

---

### Post by trulan on 2010-03-12
> **AutoStatic said:**
> I've never tried Jack2, I'm just very content with Jack1 and as long as things like Ladish are still heavily discussed and I don't have a use for netjack I'll stick to Jack1. The only thing where I could gain something with Jack2 might be multithreading.
That's what I thought.  The unfortunate reality is, at least with Ffado, that I need to set firewire to 'non-threaded' (using rtirq) to get anything resembling stability with Jack2.  At least that seems to be the current state of affairs.

Philip, thanks for an excellent repository.

---

### Post by philip5 on 2010-03-13
> **trulan said:**
> 
Philip, thanks for an excellent repository.
You are very welcome. :p

I just uploaded jack-audio-connection-kit 0.118.0 to my repository for Karmic and I'm not 100% happy with the solution as it will need a few hands-on tweaks from the user to work as it should. Have been messing with some package scripts to automate this so users shouldn't have to bother with it but it didn't work as I wanted so I might add them as an update later on.

For now you have to manually add your user to the audio group (or the user that starts and runs jackd). 

**READ THIS FIRST BEFORE CHANGING NICE:**
*[http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-March/067904.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-March/067904.html)*

Then if you don't run a realtime kernel you need to add this:
```
@audio   -  rtprio     99
@audio   -  memlock    unlimited
@audio   -  nice      -10
```
to your:

/etc/security/limits.conf

You could experiment with the nice parameter from -5 to -20 or something.

This information is something that jackd will tell you to do if it fails to start so it's not as mysterious where the instructions come from.

I would be happy to get feedback on this update and if it gives any problems with other apps that are built against the old jack version in Karmic. If it just works its good to hear too...

[edit: added warning about nice]

---

### Post by trulan on 2010-03-13
Jack .118 installed successfully in 32 bit and 64 bit.  So far it is looking good!  Haven't found any issues yet.

I had done the limits.conf edits previously, and I didn't have to redo any of that when I upgraded.

---

### Post by AutoStatic on 2010-03-15
Setting renice is not necessary:

[quote=Paul Davis on the Linux Audio Users mailinglist]not pick on you jeremy, just wanting to make it more likely that
people find this via google: .... no! renice has NEVER been the right
way to make audio work. the fact that it happens, in a few cases, to
have some beneficial impact has apparently misled some people who
don't understand how this all works. nice and renice have absolutely
nothing to do with making sure that audio plays correctly. the
capability that they represent should not be used for this purpose,
and people who spread around patches to limits.conf that include it
are simply confusing people with an error.[/quote]

[http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-March/067904.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-March/067904.html)

---

### Post by philip5 on 2010-03-15
> **AutoStatic said:**
> Setting renice is not necessary:
[http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-March/067904.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-March/067904.html)
That is rather interesting! I can't say that I have any indepth knowledge about how jackd works and what/if there is any benifit from the nice setting in limits.conf. I just posted that instructions as it's what the program itself (jackd) and the developers recommends you to do when starting jackd.

What is even more interesting is that the jackd package in Lucid will add these settings automatically to your limits.conf when you install the jackd (and remove them when you uninstall jackd) package. If this is true about nice and that the use of nice/renice in this way shouldn't be spread and used as the author of that mail say then you now have a whole distribution with Lucid (and Debian Squeeze and Sid also do this) that will implement this solution for every user of jackd.

---

### Post by AutoStatic on 2010-03-15
Also bear in mind that Paul Davis is one of the authors of JACK.

```
11:26:17.881 JACK was started with PID=6585.
jackdmp 1.9.4
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
```

(BTW, this is on my Fedora 12 machine with the PlanetCCRMA repo enabled which has Jack2)

And from the same thread:
[quote=Paul Davis on the Linux Audio Users mailinglist]its a mistake that has been propagated around the net for a few years.
it has absolutely nothing useful to do with realtime, low latency
audio and should not be used by apps or system configuration for this
purpose. its very unfortunate that this myth took hold.[/quote]

---

### Post by philip5 on 2010-03-15
> **AutoStatic said:**
> Also bear in mind that Paul Davis is one of the authors of JACK.

```
11:26:17.881 JACK was started with PID=6585.
jackdmp 1.9.4
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
```

(BTW, this is on my Fedora 12 machine with the PlanetCCRMA repo enabled which has Jack2)

And from the same thread:

As far s I know it's only jackd 0.118.0 that have this recommendation about changes in limits.conf. Also only 0.118+svn packages in ubuntu and debian that have this as automatic changes in the limits.conf.

---

### Post by philip5 on 2010-03-16
Updated the snd program from 7.18 to 11.3 for Karmic. I don't know if it's a killer app for most people but some seam to like it. It's a gtk app with either jack or pulseaudio support, choose the package you like for the support.

> Snd is a powerful sound file editor that can be customized and extended using the Scheme programming language.

---

### Post by philip5 on 2010-03-17
Ported good old tapiir 0.7.1 to Karmic from Intrepid that some people might miss.

"Tapiir is a simple and flexible audio effects processor, inspired on the classical magnetic tape delay systems used since the early days of electro-acoustic music composition. It provides a graphical user interface consisting of six delay lines, or "taps", which can introduce an almost arbitrarily big or small delay to their inputs and can be fed back to each other.

A wide set of effects can be easily achieved by properly configuring and connecting the delay lines: complex echo patterns, resonances, filtering, etc. Delays, interconnections and gains can all be controlled in real time.

Tapiir requires the ALSA sound driver and the JACK sound daemon, and may be run to work with either of them."

A screenshot:

[[img]http://www.ubuntu-pics.de/thumb/47552/screenshot_033_9NXn3s.png[/img]](http://www.ubuntu-pics.de/bild/47552/screenshot_033_9NXn3s.png)

---

### Post by Capoeira on 2010-03-17
deleted

---

### Post by philip5 on 2010-03-24
Built a package of zynjacku 5.2 ([http://home.gna.org/zynjacku](http://home.gna.org/zynjacku)) which also include lv2rack for Karmic and is as always avalible on my PPA on Launchpad.

> **zynjacku** is JACK based, GTK (2.x) host for LV2 synths. It has one JACK MIDI input port (routed to all hosted synths) and one (two for stereo synths) JACK audio output port per plugin. Such design provides multi-timbral sound by running several synth plugins. 

**lv2rack** is a host for LV2 effect plugins. 

And a screenshot with two lv2-plugins activated in lv2rack and the gui it provides.

[[img]http://www.ubuntu-pics.de/thumb/48765/screenshot_036_gkVI14.png[/img]](http://www.ubuntu-pics.de/bild/48765/screenshot_036_gkVI14.png)

---

### Post by philip5 on 2010-03-25
Added package of sonic visualiser 1.7.1 ([http://sonicvisualiser.org](http://sonicvisualiser.org)) for karmic to my PPA on Launchpad.

> Sonic Visualiser is an application for inspecting and analysing the contents of music audio files. It combines powerful waveform and spectral visualisation tools with automated feature extraction plugins and annotation capabilities. 

The screenshot...

[[img]http://www.ubuntu-pics.de/thumb/48939/screenshot_037_HR7H5k.png[/img]](http://www.ubuntu-pics.de/bild/48939/screenshot_037_HR7H5k.png)

---

### Post by somnus520 on 2010-03-26
Thanx. lots off good things in this ppa you might just have maked live  more easy for me.. and i love your fst gui keep it rolling 

 
ladish could be cool if possible 
 
i got a little problem with slv2-9 

E: /var/cache/apt/archives/slv2-9_0.6.6-karmic~ppa2_i386.deb: trying to  overwrite '/usr/bin/lv2_inspect', which is also in package slv2-jack 0
E: /var/cache/apt/archives/slv2-9-dev_0.6.6-karmic~ppa2_i386.deb: trying  to overwrite '/usr/include/slv2/pluginui.h', which is also in package  libslv2-dev 0

guess i might be my old compiled drobilla-lad that need to be manually  un-installed
--------------------------
[oakley](http://*************************)  [oakley sunglasses](http://*************************)  [cheap oakley sunglasses](http://*************************)

---

### Post by DuggyFreddy on 2010-03-26
I was getting the same message, but referencing Audacity.  I looked through the versions of everything in synaptic, and made sure all of the dependencies and plugins, etc.  matched versions, deleting those that conflicted.  Then I rebooted, and everything was fine.  Hope that helps.

---

### Post by philip5 on 2010-03-26
> **somnus520 said:**
> Thanx. lots off good things in this ppa you might just have maked live  more easy for me.. and i love your fst gui keep it rolling 

 
ladish could be cool if possible 
 
i got a little problem with slv2-9 

E: /var/cache/apt/archives/slv2-9_0.6.6-karmic~ppa2_i386.deb: trying to  overwrite '/usr/bin/lv2_inspect', which is also in package slv2-jack 0
E: /var/cache/apt/archives/slv2-9-dev_0.6.6-karmic~ppa2_i386.deb: trying  to overwrite '/usr/include/slv2/pluginui.h', which is also in package  libslv2-dev 0

guess i might be my old compiled drobilla-lad that need to be manually  un-installed
--------------------------
[oakley](http://*************************)  [oakley sunglasses](http://*************************)  [cheap oakley sunglasses](http://*************************)
slv2-jack must be some 3rd party package that I have no control over to check if my packages conflict with its content. I try to solve conflicts against the official repositories you find my PPA depends on.

Otherwise feedback like this is always welcome if I have missed something as I can't test all packages in all combinations. :)

---

### Post by philip5 on 2010-03-26
> **DuggyFreddy said:**
> I was getting the same message, but referencing Audacity.  I looked through the versions of everything in synaptic, and made sure all of the dependencies and plugins, etc.  matched versions, deleting those that conflicted.  Then I rebooted, and everything was fine.  Hope that helps.
That is a solution but maybe not the best one, even though it's the only thing you you sometimes can do if you can't get the packages fixed. You should remember that any of those packages gets removed then the other might stop working as removal of any of the packages will also remove the file that the other might/will need. If you are unlucky making this as praxis then you will get a unstable system.

---

### Post by DuggyFreddy on 2010-03-26
P5, thanks for all of the great stuff on this ppa first of all.  I am pretty new to this, and I wasn't sure how to fix some of the stuff that came up after I updated from the ppa.  With the Audacity, I think that some stuff was not removed so I had two versions of the plugins and a library.  I removed the ones that were different from the new updated ones.  Is there typically some kind of cleanup like that after updating?  What is the best way to take care of it?  Thank you for all of your help on this thread.

---

### Post by philip5 on 2010-04-09
Added jack-capture 0.9.44 to my PPA on Launchpad for Karmic. I also updated guitarix to 0.07.1. It would be nice if some of you could test to use the jack-capture feature in guitarix to see if it work as it should. When I tried it guitarix gave me some errors. Not sure if it's a build problem or a bugg or something. Haven't digged into it that much yet. Maybe some feedback from you guys could enlight the recording part from guitarix.

Here is a screenshot from the jack-capture settings dialog and the latest (at the moment) guitarix.

[[img]http://www.ubuntu-pics.de/thumb/51423/screenshot_043_PHZcx5.png[/img]](http://www.ubuntu-pics.de/bild/51423/screenshot_043_PHZcx5.png) [[img]http://www.ubuntu-pics.de/thumb/51424/screenshot_045_3tXoLq.png[/img]](http://www.ubuntu-pics.de/bild/51424/screenshot_045_3tXoLq.png)

---

### Post by blablack on 2010-04-11
Hey Guys,

I don't know if the problem is coming from the way Ardour is compiled in your repository or from Ardour itself, but I can't get it to rewind (or even move the play cursor) when Ardour is using the Jack transport. No problem to do it with the Internal one, but as soon as I use Jack, I can't get it to move the play cursor. It always comes back to the same position.

To reproduce the issue, I just set Jack as the Transport and Ardour to be the Time Master.

Searching for a solution on Google, a few articles mentionned that it is a problem with Jack and that it should be downgraded. And in fact the version of Ardour/Jack in the official Ubuntu Repository don't have that problem.

Let me know if there is another solution or of the repository needs to be fixed.

Anyway, brilliant job nonetheless! I was compiling all the software manuall before (Ardour, Jack, Yoshimi, etc...) and it was starting to keep up with all the versions coming out!

---

### Post by trulan on 2010-04-11
One big improvement (for me at least) with the version of jack from philip5's repo is that patchage actually works when using jack with the firewire driver (ffado).  Patchage will just fold up if you try to use it with jack and ffado from karmic.  It's too bad if there's a regression with Ardour and jack transport.  Jack transport is one thing I haven't learned to use as of yet.  I'll have to play around with this a bit.

---

### Post by philip5 on 2010-04-13
Anyone got any more or updated requests or tips on media producing apps that could/should be uploaded on my PPA to be more avalible for the common user?

Maybe it's just a big wait for Lucid final to be released? :)

I could make a public note here too that about when Lucid turns final I will install it myself and most of my efforts will be doing the same for Lucid what I have been doing for Karmic as my main drive is to get as updated software as possible for myself and when doing that share my work to others via my PPA. That mean that the karmic updates will mostly come on requests as I won't spend much time with Karmic at the time I start using Lucid.

Not sure how many of you users of the PPA that won't go for Lucid for any reason when it's final that will find this as a problem.

---

### Post by AutoStatic on 2010-04-13
No not really, but I do have a suggestion, is it possible to link all the packages you upload to Jack 0.116.x instead of 0.118.x? I tried installing Yoshimi from your PPA but it needs Jack 0.118.x and I don't want to use Jack 0.118.x, I'm happy with 0.116.x

---

### Post by philip5 on 2010-04-13
> **AutoStatic said:**
> No not really, but I do have a suggestion, is it possible to link all the packages you upload to Jack 0.116.x instead of 0.118.x? I tried installing Yoshimi from your PPA but it needs Jack 0.118.x and I don't want to use Jack 0.118.x, I'm happy with 0.116.x
Not really I'm afraid as the dependency links to what version of the package its built against. I could override it of course but then I'm not sure if there would be any problems in an other end for people using 0.118.x. If it's a common problem or wish that makes people not to use the PPA then I could do it. The same thing would happen for about every package that use jack and would also need an override as default. Or maybe a regression to 0.116.x instead.

Is there any problems with 0.118.x or just happy with 0.116.x?

---

### Post by AutoStatic on 2010-04-13
No just happy. Haven't tried 0.118.x yet. But my systems are stable so I don't feel much like updating. Maybe I should just give it a go.

---

### Post by philip5 on 2010-04-14
Just uploaded Phasex 0.12.0 pre1 to my PPA on Launchpad for Karmic.

> PHASEX:
[P]hase [H]armonic [A]dvanced [S]ynthesis [EX]periment

PHASEX is an experimental software synthesizer for use with Linux/ALSA/JACK. The name comes partially from its experimental method of using phase offset modulation, where each oscillator can have its phase offset between right and left channels modulated by an LFO or another oscillator.

Please keep in mind that PHASEX is in an active state of development, and new features will be added from time to time. 

[http://www.sysex.net/phasex](http://www.sysex.net/phasex)

And here is a screenshot:

[[img]http://www.ubuntu-pics.de/thumb/52236/screenshot_049_ylXIsy.png[/img]](http://www.ubuntu-pics.de/bild/52236/screenshot_049_ylXIsy.png)

---

### Post by sgx on 2010-04-14
The sound and potential of phasex is outstanding. The gui has options, a tabbed gui that is not quite so overwhelming, and a netbook version. You can use the soundcard line-in as a sound source to modulate, great for
extra schmaltz on electric guitars, or whatever is currently on your line-in.
Cheers

---

### Post by sgx on 2010-04-14
> **philip5 said:**
> Anyone got any more or updated requests or tips on media producing apps that could/should be uploaded on my PPA to be more avalible for the common user?

Maybe it's just a big wait for Lucid final to be released? :)

I could make a public note here too that about when Lucid turns final I will install it myself and most of my efforts will be doing the same for Lucid what I have been doing for Karmic as my main drive is to get as updated software as possible for myself and when doing that share my work to others via my PPA. That mean that the karmic updates will mostly come on requests as I won't spend much time with Karmic at the time I start using Lucid.

Not sure how many of you users of the PPA that won't go for Lucid for any reason when it's final that will find this as a problem. Hi, there was a .wav player called zinf, simple to use, and used arrow keys to
easily navigate and preview vast sample collections, worlds easier than audacity, rezound, mplayer/xine variants etc. I believe it is still here:

[http://www.zinf.org/](http://www.zinf.org/)

Cheers

---

### Post by philip5 on 2010-04-15
> **sgx said:**
> The sound and potential of phasex is outstanding. The gui has options, a tabbed gui that is not quite so overwhelming, and a netbook version. You can use the soundcard line-in as a sound source to modulate, great for
extra schmaltz on electric guitars, or whatever is currently on your line-in.
Cheers

Yes it seem to be a good and promising piece of software. Too bad right now that there is such long build ques at Launchpad so my packages won't be built for an other 8-9 hours when I write this. Guess it's busy building stuff for the comming Lucid release. But the build is comming...

> **sgx said:**
> Hi, there was a .wav player called zinf, simple to use, and used arrow keys to
easily navigate and preview vast sample collections, worlds easier than audacity, rezound, mplayer/xine variants etc. I believe it is still here:

[http://www.zinf.org/](http://www.zinf.org/)

Cheers

I'll have a look at it when I get home after work this evening.

---

### Post by mango42 on 2010-04-15
Hi and very grateful thanks to you PPA'ers.

I've been searching for a MIDI synthesizer librarian program for you to consider packaging but so far have only turned up the Java-based JSynthLib, which doesn't seem to have progressed since 2005:-

[http://www.jsynthlib.org/](http://www.jsynthlib.org/)

---

### Post by babarosa on 2010-04-15
@mango42
I also wish there is something like "sounddiver". I help myself using wine plus windows-editors.

Remember our last communication concerning sysex-dumps using "amidi". Of course you also can transmit sysex-messages like bank change, arpeggiator on, ... using "amidi". Get the proper messages from the "midi implementation chart/list" of your synth model.

@philip5
Reading that you also will continue your precious work for v10.04 makes me jump around. Thanks to you and some other people my "bubble" (see the sticky thraed from stochastic) became a reality, delivering up-to-date ppas to my mind is the best way to keep ubuntu a competitive audio system.

Thank you very much for your addiction!
Michael

---

### Post by mango42 on 2010-04-16
> **babarosa said:**
> I also wish there is something like "sounddiver". I help myself using wine plus windows-editors.

Perhaps I have written myself into an ideological corner by not using any windows apps... ;-/

> Remember our last communication concerning sysex-dumps using "amidi". 

Yes I remember - and thanks once again ;-) 

I got quite a long way with **amidi** - so long as I remembered to use it *before* making any connections through Jack, Patchage or Aconnectgui (still a complete mystery trying to use those darned scissors - they never seem to work for me - a very curious little applet!) 

Since then, I've achieved a far better understanding of how **QTractor** handles Sysex (hey, I might even feel confident enough to add to its docs before too long ;) - not ideal (too many menus deep for on-the-fly changes, IMO) but it certainly does the job consistently, without any '*gotchas*'.

However, **amidi** is still tops for bulk dumps, IMO.

---

### Post by vininim on 2010-04-17
Installed files from hydrogen-svn-0.95~svn1705-0~ppa1:

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/hydrogen-svn
/usr/share/doc/hydrogen-svn/AUTHORS
/usr/share/doc/hydrogen-svn/changelog.Debian.gz
/usr/share/doc/hydrogen-svn/changelog.gz
/usr/share/doc/hydrogen-svn/copyright

Is this normal? :)

---

### Post by philip5 on 2010-04-17
> **vininim said:**
> Installed files from hydrogen-svn-0.95~svn1705-0~ppa1:

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/hydrogen-svn
/usr/share/doc/hydrogen-svn/AUTHORS
/usr/share/doc/hydrogen-svn/changelog.Debian.gz
/usr/share/doc/hydrogen-svn/changelog.gz
/usr/share/doc/hydrogen-svn/copyright

Is this normal? :)
No it's not normal as it looks like you installed a package that have missed to include all the files for hydrogen. Make the maintainer of the package (it's not my package or from my PPA) aware about it if he doesn't allready know.

---

### Post by vininim on 2010-04-17
According to synaptic's Origin, it's ppa:falk-t-j/lucid-latest 

falkTX will eventually read[*], no need to hurry. 


[*] Is there a way to report ppa related bugs on launchpad?

---

### Post by philip5 on 2010-04-18
> **vininim said:**
> According to synaptic's Origin, it's ppa:falk-t-j/lucid-latest 

falkTX will eventually read[*], no need to hurry. 


[*] Is there a way to report ppa related bugs on launchpad?

I think every PPA have a bug tracker against either the PPA or the maintainer. Usually I get my bug reports either here at the forum, IRC or by mail.

---

### Post by babarosa on 2010-04-21
Dear philip5,

would you mind adding the latest (v2.4.9) libgphoto2, gphoto2 and gtkam to your repo?

My thanks in advance and regards,
Michael

---

### Post by vervelover on 2010-04-21
Hi
Thanks for this amazing PPA, the only problem I have is that fst doesn't work in Lucid, I get a bad exe format error in wine. Any chance to see this fixed soon? I downgraded to wine 1.0.1 but it did not help..

---

### Post by falkTX on 2010-04-21
> **vervelover said:**
> Hi
Thanks for this amazing PPA, the only problem I have is that fst doesn't work in Lucid, I get a bad exe format error in wine. Any chance to see this fixed soon? I downgraded to wine 1.0.1 but it did not help..

Hi, I'm the author of 'FeSTige', a gui for fst. See:
[http://festige.sourceforge.net/](http://festige.sourceforge.net/)

I have an ubuntu ppa which contains festige and fst. fst was compiled with lash support and works on 64bit too.

---

### Post by philip5 on 2010-04-21
> **babarosa said:**
> Dear philip5,

would you mind adding the latest (v2.4.9) libgphoto2, gphoto2 and gtkam to your repo?

My thanks in advance and regards,
Michael

I'll have a look at it when I get home from work this evening...

[edit]
Just uploaded libgphoto2 2.4.9.1 to Launchpad to be built for Karmic on my PPA.

---

### Post by vervelover on 2010-04-22
@FalkTX

AMAZING! you PPA saved my life and my studio :) Great job!

---

### Post by vervelover on 2010-04-22
Just one more request: rosegarden crashes with segfault every time I press the open and save as buttons in Lucid, I guess it is because of some missing dependencies. I tried installing kdebase-bin, dolphin and some others with no success..

Do you know what dependencies I need? Would you build a rosegarden .deb in your repository with fixed dependencies?

Thanks A LOT
Alessio

---

### Post by falkTX on 2010-04-22
> **vervelover said:**
> Just one more request: rosegarden crashes with segfault every time I press the open and save as buttons in Lucid, I guess it is because of some missing dependencies. I tried installing kdebase-bin, dolphin and some others with no success..

Do you know what dependencies I need? Would you build a rosegarden .deb in your repository with fixed dependencies?

Thanks A LOT
Alessio

Rosegarden does not need kde now. Just Qt4, jack and alsa midi.
You should try GetDeb though, they have an updated version (10.02.1), while lucid version is 10.02.
[http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/)

---

### Post by falkTX on 2010-04-22
> **vervelover said:**
> @FalkTX

AMAZING! you PPA saved my life and my studio :) Great job!

Nice to know.

*Any suggestions on how to improve are welcome.*

---

### Post by vervelover on 2010-04-22
still no success even with the getdeb packages, I can only open a session by double-clicking on a previously created file..

---

### Post by falkTX on 2010-04-22
> **vervelover said:**
> still no success even with the getdeb packages, I can only open a session by double-clicking on a previously created file..

Try these ones:
[https://edge.launchpad.net/~falk-t-j/+archive/lucid/+sourcepub/1083467/+listing-archive-extra](https://edge.launchpad.net/~falk-t-j/+archive/lucid/+sourcepub/1083467/+listing-archive-extra)

You'll have to use "sudo dpkg -i *.deb".
Don't update after install.

Tell me if that works for you

---

### Post by vervelover on 2010-04-22
@falkTX

Thanks a lot for your help! I just found out that rosegarden only segfaults when opening or saving a file when you are not using the thorn style. I hate the thorn style, and also the same getdeb packages were working in karmic with no problems at all.. 

I just tried your packages but they still have the "no-thorn-style=segfault" issue..

---

### Post by falkTX on 2010-04-22
> **vervelover said:**
> @falkTX

Thanks a lot for your help! I just found out that rosegarden only segfaults when opening or saving a file when you are not using the thorn style. I hate the thorn style, and also the same getdeb packages were working in karmic with no problems at all.. 

I just tried your packages but they still have the "no-thorn-style=segfault" issue..

Try this:
- disable thorn style
- run "rosegarden -style plastique" and check if it still crashes

Maybe there's a bug in the Qt theme you're using ?

---

### Post by vervelover on 2010-04-23
Thanks a lot for your hint, I'm using the GTK theme and with the plastic theme the bug is not happenning, also tried the oxygen theme and it works as expected. That's a shame cause the GTK theme integrated perfectly into the desktop. Anyway thanks a lot for your help at least I've been able to workaround the issue! :guitar:

---

### Post by vervelover on 2010-04-24
Ok, one more thing :)
Since I updated to Lucid, I can't connect jack-midi to alsa-midi anymore. I'm using qjackctl from your ppa, and I already set "seq" in the midi prefs. There is no midi-through anymore in the midi connection tab, thus I can't connect midi-through to fst anymore. 

This is strange cause I was able to do that in karmic with no problems at all, and now on the same hardware it only works if I use a2jmidid..

Thanks a lot in advance for any help you can give me to workaround this issue!

---

### Post by trulan on 2010-04-24
Edit:  Whoops - you already have the 'seq' driver set.  I thought I had a quick answer but I was trying to be too quick...

---

### Post by vervelover on 2010-04-24
no problem thanks anyway :lolflag:

---

### Post by falkTX on 2010-04-25
My PPA has Jack2, which is unsupported in QJackCtl.
Any changes you make in QJackCtl WILL NOT affect Jack at all. This is very sad and I hope the author fixes it soon.

A quick solution is to use laditools/ladish.
Just install laditools, launch 'laditray', then stop jack and configure it.
When done, restart Jack (they call it "Studio").

That will let you configure Jack.
Jack2 uses '~/.config/jack/conf.xml' and not '~/.jackdrc', so...

But this works fine.
The Unstable PPA contains the latest git versions of ladish/laditools, if you want


EDIT: Rosegarden 10.04 is out, it's in GetDeb already

---

### Post by Pablo_F on 2010-04-26
> Any changes you make in QJackCtl WILL NOT affect Jack at all

FalkTX, Are you sure of this?
I have qjackctl 0.3.6 and jackd 1.9.5 (both built from sources) and I set up jack by means of qjackctl with no problem. 

The only thing (it is not a issue for me as I have always used a2jmidid anyway): I don't see midi through in jack MIDI either. 

However, is qjackctl to blame? I don't think so!

Try using ladiconf to set up jack and choose alsa seq driver as midi-driver (jack driver parameters button). I don't have jack midi through either, only jack midi capture and playback. I only have jack midi through if I launch a2j, which is the equivalent to qjackctl + a2jmidid

Now from the terminal, I launch jackd with the -Xseq option, it is exactly the same. No MIDI through in the jack MIDI connections.

This has nothing to do with qjackctl, which in my experience is fully compatible with both branches of jack.

I am upgrading to lucid soon and I will use your PPA :) Thank you!

Pablo

---

### Post by AutoStatic on 2010-04-26
> **falkTX said:**
> My PPA has Jack2, which is unsupported in QJackCtl.
Any changes you make in QJackCtl WILL NOT affect Jack at all. This is very sad and I hope the author fixes it soon.I use Jack2 (jackdmp 1.9.4) on my Fedora 12 machine and I can control that perfectly with QjackCtl 0.3.6

---

### Post by vervelover on 2010-04-26
I also have no troubles making connections in qjackctl, I'm in the same situation as Pablo_F's.. though I was not before upgrading to Lucid. Anyway I'll try Rosegarden 10.04 as soon as I can!

---

### Post by falkTX on 2010-04-26
Maybe it's just me, but QJackCtl settings do not change anything in jack...
I tried:
1. set buffer size to 4096
2. set sample rate to 48'000 Hz
3. Stop and start jack
And jack is still running with my ladiconf settings (1024bf, 44100sr)

Maybe I'm missing something?


EDIT: I can confirm the 'seq' midi prob. Jack2 appears to not support it yet (?)

---

### Post by philip5 on 2010-04-28
I just installed Lucid on my computer the other day and am about to start porting stuff for Lucid to my PPA and I think most of the updates from now on my PPA will be for Lucid as it's what I will use.

What do we Lucid users miss and what needs attention, updates or just available?

So far the impression of Kubuntu 10.04 that I use looks promising. No real problem that I have stumbled upon yet to fix. Looking gooooood... :)

---

### Post by falkTX on 2010-04-28
> **philip5 said:**
> I just installed Lucid on my computer the other day and am about to start porting stuff for Lucid to my PPA and I think most of the updates from now on my PPA will be for Lucid as it's what I will use.

What do we Lucid users miss and what needs attention, updates or just available?

So far the impression of Kubuntu 10.04 that I use looks promising. No real problem that I have stumbled upon yet to fix. Looking gooooood... :)

I think we should work together so there are no wasted efforts.
Are you willing to create a team for packaging? Then us will upload to the same PPA ?

---

### Post by philip5 on 2010-04-28
> **falkTX said:**
> I think we should work together so there are no wasted efforts.
Are you willing to create a team for packaging? Then us will upload to the same PPA ?
Yes, or we could have a "stable" team rolling release PPA that have gone thou some testing and have our own PPAs as testing ground? I bet we have a few users around here that are willing to test and maybe Autostatic want to contribute to a team PPA too?

---

### Post by falkTX on 2010-04-28
> **philip5 said:**
> Yes, or we could have a "stable" team rolling release PPA that have gone thou some testing and have our own PPAs as testing ground? I bet we have a few users around here that are willing to test and maybe Autostatic want to contribute to a team PPA too?

That seems a little too much work. I would recommend 1 stable PPA and 1 unstable, still as team upload; This is the method I use now. The unstable would have svn/git versions.

I'm currently busy working on KXStudio - [http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/) - but you have my full permission to copy the packages to a new team-PPA.
I just need some time to fix some stuff and then I'll help packaging and updating stuff

---

### Post by philip5 on 2010-04-28
What should we name the team then? And should we call the repos unstable and stable or experimental and stable?

Any good suggestions on name? In general I upload graphic production, music production, media players, some drivers and maybe something more so my contribution will not be just music production apps.

---

### Post by falkTX on 2010-04-29
> **philip5 said:**
> What should we name the team then? And should we call the repos unstable and stable or experimental and stable?

Any good suggestions on name? In general I upload graphic production, music production, media players, some drivers and maybe something more so my contribution will not be just music production apps.

Well... I've been thinking about this...
I cannot have packages in KXStudio that were not passed trough me (check, testing, etc), so users won't complain about something I didn't do.
I mean, at the moment, all the packages in KXStudio are from my PPAs, except for the lowlatency kernel, packaged by abogani.

But a simple solution is that I upload to my PPAs and also for a team-PPA. But my 'Lucid' PPA still has to be active, has this is the main repo used for KXStudio. It will be my private PPA. You can always copy packages from it, of course.
Please tell me if you're ok with that.

As for the name, "Multimedia Geeks" or anything else it's just fine. (I don't care much about the name).

---

### Post by hissyfut on 2010-04-30
just curious, how does this differ from ubuntustudio?

and is pulse audio necessary?

---

### Post by falkTX on 2010-04-30
> **hissyfut said:**
> just curious, how does this differ from ubuntustudio?

and is pulse audio necessary?

UbuntuStudio uses Gnome, KXStudio uses KDE. This is the main difference.
KXStudio is auto-setup for audio production and has some nice&custom KDE stuff.

PulseAudio is not needed but it's cool that it works with Jack.

---

### Post by jsevi83 on 2010-04-30
falkTX, there might be something wrong with the package eq10q-lv2 from your lucid ppa. It doen't have any dependencies (and it should), and it's the only lv2 plugin in your ppa which doesn't load in ardour.

---

### Post by falkTX on 2010-05-02
> **jsevi83 said:**
> falkTX, there might be something wrong with the package eq10q-lv2 from your lucid ppa. It doen't have any dependencies (and it should), and it's the only lv2 plugin in your ppa which doesn't load in ardour.

3 people now have complained about it... but it's ok.
The fix is already uploaded, just wait for the update (some hours)

---

### Post by jsevi83 on 2010-05-02
Thank you. I just realized that I cannot run fmit (free music instrument tuner). It seems not to work with jack2. Is there any chance to build fmit with support for jack2? I like it way better than lingot.

---

### Post by ronjouch on 2010-05-02
EDIT: I feel so dumb. This will be one more reminder for me to step away from problems and start with a fresh eye before thinking the problem is this or that. The problem was Totem/GStreamer was apparently putting too much gain for some reason (even though the max of the slider volume is 100%). All clear for VLC/Audacity, and playing with the volume slider in Totem (even putting it back at 100%) restored a correct gain. I'm trying to reproduce the problem to file a Totem/Gstreamer bug.
Anyway, thanks falkTX and philip5 for your amazing packages, good day everybody.

[I][COLOR="Silver"]Hello.

I recently installed Ubuntu(studio) 10.04, and have some audio issues; here is my problem.

When I hear my compo live in Ardour, everything's fine, but after export, the resulting file is awfully saturated (I tried different export formats but that's typically mono, wav, 24bits, 44.1kHz, best conversion quality).

The reason I'm asking for help here is because I updated lots of stuff from your PPA. I'm currently not even sure the problem comes from one of your packages (I did not test my vanilla ubuntu setup before adding your ppa :( ), I'm just starting here thinking you might have some ideas...
I did not have the problem on Ubuntu 9.10 with jack1 and have no idea if my problem comes from jack2 or Ardour or a library used during export or something else. So many things changed on my system that I have no idea what can be causing this.

Does anybody here has an idea? Or suggestions to help me isolate the source of the problem? Any help appreciated, guys, I'm totally lost and cannot do anything with this problem.

My setup:
- Clean install of Ubuntu 10.04 x86-32bits + ubuntustudio-audio* + linux-rt (2.6.31-10-rt)
- All the updates from falkTX ppa, including Ardour 2.8.7 on jackd 1.9.5 
- The sound card is a Edirol FA-66 using ffado 2.0.0, and I'm using the same JACK Connection Kit settings as I've been using for years, no xruns[/COLOR][/I]

---

### Post by sgx on 2010-05-02
> **ronjouch said:**
> EDIT: I feel so dumb. This will be one more reminder for me to step away from problems and start with a fresh eye before thinking the problem is this or that. The problem was Totem/GStreamer was apparently putting too much gain for some reason (even though the max of the slider volume is 100%). All clear for VLC/Audacity, and playing with the volume slider in Totem (even putting it back at 100%) restored a correct gain. I'm trying to reproduce the problem to file a Totem/Gstreamer bug.
Anyway, thanks falkTX and philip5 for your amazing packages, good day everybody.

Don't feel bad, linux makes even Bill Gates himself feel dumb :D

---

### Post by falkTX on 2010-05-03
> **jsevi83 said:**
> Thank you. I just realized that I cannot run fmit (free music instrument tuner). It seems not to work with jack2. Is there any chance to build fmit with support for jack2? I like it way better than lingot.

I'll do it, but that will take some time (all source is now waiting like 2 days to compile...:()

---

### Post by jsevi83 on 2010-05-03
Thanks a lot, I can wait as long as it takes.

---

### Post by falkTX on 2010-05-04
> **jsevi83 said:**
> Thanks a lot, I can wait as long as it takes.

Package has been build successfully. The error was that Jack2 doesn't have "jack_error_callback". I removed that function from the code and now it works.
It should only take a few moments to be available on the PPA

---

### Post by jsevi83 on 2010-05-05
Thanks again. It seems there is some problem with my laptop as fmit makes the system freeze when playing with the options. It also happened with lucid version of fmit and jack1, so I don't think it's related to your package. Lingot and other microphone apps work fine though. I cannot find the crash log. Any suggestions?

---

### Post by falkTX on 2010-05-05
> **jsevi83 said:**
> Thanks again. It seems there is some problem with my laptop as fmit makes the system freeze when playing with the options. It also happened with lucid version of fmit and jack1, so I don't think it's related to your package. Lingot and other microphone apps work fine though. I cannot find the crash log. Any suggestions?

"strace fmit" ?
I'll look into once I have some free time

---

### Post by jsevi83 on 2010-05-06
Well, I don't know what strace is, but I ran on the terminal "strace fmit" and it was woking without freezing my system. There was a huge output on the terminal. After that I ran fmit (without strace) and it crashed after two seconds. What should I do? Should I provide the output of strace?

---

### Post by falkTX on 2010-05-06
> **jsevi83 said:**
> Well, I don't know what strace is, but I ran on the terminal "strace fmit" and it was woking without freezing my system. There was a huge output on the terminal. After that I ran fmit (without strace) and it crashed after two seconds. What should I do? Should I provide the output of strace?

That would be too much output.
I found a simple solution, using a debugger, open a terminal and run:
```
gdb /usr/bin/fmit
r
```

If the program crashes you'll be able to see the specific function that makes it crash.
You can also run "bt" after the crash to print more info.
Press Ctrl+D to close the debugger.

---

### Post by jsevi83 on 2010-05-06
I followed your instructions and fmit didn't freeze my system while using it. I could close after a minute without a crash. This is the output:

Starting program: /usr/bin/fmit 
[Thread debugging using libthread_db enabled]
Free Music Instrument Tuner version 0.97.7 built at May  4 2010 15:31:47
Install directory '/usr'
CaptureThread: INFO: Built in transports
jack_client_new: deprecated
[Nuevo Thread 0x7ffff0877710 (LWP 8929)]
Cannot connect to server socket err = No existe el fichero ó directorio
Cannot connect to server socket
jack server is not running or cannot be started
[Thread 0x7ffff0877710 (LWP 8929) terminado]
CaptureThread: INFO:	N/A	JACK	Jack Audio Connection Kit
CaptureThread: INFO:	OK	ALSA	Advanced Linux Sound Architecture (lib:1.0.23)
CaptureThread: INFO:	OK	OSS	Open Sound System (lib:30802)
CaptureThread: INFO: using ALSA transport
CombedFT: INFO: window size=801 FFT size=1024 window size factor=1 zero padding factor=1
CombedFT: INFO: window size=3207 FFT size=4096 window size factor=4 zero padding factor=1
[Nuevo Thread 0x7fffec685710 (LWP 8930)]
CaptureThread: INFO: ALSA: try to set format to Signed 16 bit Little Endian success
CaptureThread: WARNING: ALSA: cannot set channel count to one (2 instead)
CaptureThread: INFO: format is signed integer 16bits with 2 channel(s)
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
[Thread 0x7fffec685710 (LWP 8930) terminado]

Program exited normally.

---

### Post by falkTX on 2010-05-07
> **jsevi83 said:**
> I followed your instructions and fmit didn't freeze my system while using it. I could close after a minute without a crash. This is the output:

Starting program: /usr/bin/fmit 
[Thread debugging using libthread_db enabled]
Free Music Instrument Tuner version 0.97.7 built at May  4 2010 15:31:47
Install directory '/usr'
CaptureThread: INFO: Built in transports
jack_client_new: deprecated
[Nuevo Thread 0x7ffff0877710 (LWP 8929)]
Cannot connect to server socket err = No existe el fichero ó directorio
Cannot connect to server socket
jack server is not running or cannot be started
[Thread 0x7ffff0877710 (LWP 8929) terminado]
CaptureThread: INFO:	N/A	JACK	Jack Audio Connection Kit
CaptureThread: INFO:	OK	ALSA	Advanced Linux Sound Architecture (lib:1.0.23)
CaptureThread: INFO:	OK	OSS	Open Sound System (lib:30802)
CaptureThread: INFO: using ALSA transport
CombedFT: INFO: window size=801 FFT size=1024 window size factor=1 zero padding factor=1
CombedFT: INFO: window size=3207 FFT size=4096 window size factor=4 zero padding factor=1
[Nuevo Thread 0x7fffec685710 (LWP 8930)]
CaptureThread: INFO: ALSA: try to set format to Signed 16 bit Little Endian success
CaptureThread: WARNING: ALSA: cannot set channel count to one (2 instead)
CaptureThread: INFO: format is signed integer 16bits with 2 channel(s)
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
[Thread 0x7fffec685710 (LWP 8930) terminado]

Program exited normally.

You have to make it crash if you want to know why it crashes.
It doesn't seem to crash in gdb, so does it still crashes when launched without gdb?

---

### Post by isaacj87 on 2010-05-07
Thanks for this! I really appreciate it. Now, I'm rocking the latest Ardour and Jack for my home studio. :)

---

### Post by jsevi83 on 2010-05-08
It seems that my system freezes when I run fmit by itself. If I run "strace fmit" or "gdb /usr/bin/fmit" it doesn't happen. I don't think it is a fmit crash, it's my system that hangs. And I don't know how to reproduce it with strace or gdb, it just happens three seconds after launching it.

At least I can use fmit launching it with gdb (as a workaround for now ;)

---

### Post by falkTX on 2010-05-09
> **jsevi83 said:**
> It seems that my system freezes when I run fmit by itself. If I run "strace fmit" or "gdb /usr/bin/fmit" it doesn't happen. I don't think it is a fmit crash, it's my system that hangs. And I don't know how to reproduce it with strace or gdb, it just happens three seconds after launching it.

At least I can use fmit launching it with gdb (as a workaround for now ;)

Maybe it works if you try some other prefixes: (?)
```
padsp fmit
LANG=C fmit

```

---

### Post by l0xin on 2010-05-09
Is there any chance of an updated [Freecycle]("http://freecycle.redsteamrecords.com/") package? The Lucid version seems to have been built without ALSA MIDI :(

---

### Post by jsevi83 on 2010-05-09
Thanks for your advice, I can run fmit with:
padsp fmit
LANG=C fmit

Both of them work, so I will just edit my launcher and problem solved.

---

### Post by falkTX on 2010-05-09
> **l0xin said:**
> Is there any chance of an updated [Freecycle]("http://freecycle.redsteamrecords.com/") package? The Lucid version seems to have been built without ALSA MIDI :(

I'll do this right away.
It seems a very good software!

---

### Post by l0xin on 2010-05-09
Great... I did try to compile it myself but ran into issues with QT. Hopefully you have more luck.

---

### Post by babarosa on 2010-05-09
Hello,

concerning "freecycle", I made the experience that the generated midi files are unreadable by all the available sequencers. The reason seems to be missing header data in the midi files generated by freecycle.

This post affirms my experience:
[http://lists.nongnu.org/archive/html/freecycle-users/2009-06/msg00001.html](http://lists.nongnu.org/archive/html/freecycle-users/2009-06/msg00001.html)

Slicing can also be achieved very fine with the "Rhythm Ferret" plugin included in Ardour.

---

### Post by psidrum on 2010-05-10
thanks for creating this, its great!

maybe you can also add these

[http://loopdub.sourceforge.net/](http://loopdub.sourceforge.net/)
[http://www.veejayhq.net/](http://www.veejayhq.net/)
[http://www.filter24.org/seq24/](http://www.filter24.org/seq24/)

---

### Post by falkTX on 2010-05-10
> **psidrum said:**
> thanks for creating this, its great!

maybe you can also add these

[http://loopdub.sourceforge.net/](http://loopdub.sourceforge.net/)
[http://www.veejayhq.net/](http://www.veejayhq.net/)
[http://www.filter24.org/seq24/](http://www.filter24.org/seq24/)

Sure. I'll do this later this week

---

### Post by Mr_Bumpy on 2010-05-11
Does anybody else notice that Rosegarden 10.04.2 is seriously more sluggish than 10.02 was?  It's unusable for me.  I've tried the getdeb.net package and compiling it from scratch with the same result.  [Here's the bug report I filed on it]("https://sourceforge.net/tracker/?func=detail&aid=2999755&group_id=4932&atid=104932")--I'm curious if anyone else is experiencing the issue.

---

### Post by hxcobd on 2010-05-11
I'm not seeing FST in the repos for Lucid, was that not added?

*edit- Nevermind, found it! Stupid case sensitivity.



Also, how does FST compare to DSSI-VST? Better or worse?

---

### Post by hxcobd on 2010-05-11
I'm rather unamused with these PPAs right now... They force JACK2 installs if you install FST, DSSI-VST, or a number of other packages, even if you already have JACK1 installed... And after this, it becomes impossible to remove either JACK1 or JACK2 without a huge myriad of other system software being removed with them, even completely unrelated stuff like Audacity, Orca, and MPlayer...

I'd basically be better off reinstalling Ubuntu than trying to reinstall all of the stuff it's going to remove, but one or the other has to happen, as my JACK won't function properly anymore due to the double JACK1/JACK2 install...

---

### Post by falkTX on 2010-05-11
> **hxcobd said:**
> I'm rather unamused with these PPAs right now... They force JACK2 installs if you install FST, DSSI-VST, or a number of other packages, even if you already have JACK1 installed... And after this, it becomes impossible to remove either JACK1 or JACK2 without a huge myriad of other system software being removed with them, even completely unrelated stuff like Audacity, Orca, and MPlayer...

I'd basically be better off reinstalling Ubuntu than trying to reinstall all of the stuff it's going to remove, but one or the other has to happen, as my JACK won't function properly anymore due to the double JACK1/JACK2 install...

My PPA is the one that has Jack2.
In my Jack2 package, it completely replaces Jack1. There is no double Jack1/Jack2.

You might (rarely) find an application that worked on Jack1 but not anymore on Jack2. If so - tell me and I'll fix it! (This happened with "fmit").

---

### Post by hxcobd on 2010-05-11
I don't mean to say that your packages installed JACK1 AND JACK2. Rather, either the FST or DSSI-VST package (can't remember which) installed JACK2 without UNINSTALLING JACK1. Obviously this resulted in a handful of errors within Synaptic, followed by weird Update Manager options.

Then, when trying to Remove or Completely Remove either JACK1 or JACK2, it's trying to remove 30+ other applications as well.

---

### Post by sgx on 2010-05-11
> **hxcobd said:**
> I'm rather unamused with these PPAs right now... They force JACK2 installs if you install FST, DSSI-VST, or a number of other packages, even if you already have JACK1 installed... And after this, it becomes impossible to remove either JACK1 or JACK2 without a huge myriad of other system software being removed with them, even completely unrelated stuff like Audacity, Orca, and MPlayer...

I'd basically be better off reinstalling Ubuntu than trying to reinstall all of the stuff it's going to remove, but one or the other has to happen, as my JACK won't function properly anymore due to the double JACK1/JACK2 install...
Hi, fst and dssi-vst mainly for ancient low powered computers, to use one vst at a time. Their integration into other larger apps is of dubious value if it brings unwanted changes to a stable modern system,
and though repetitious, Reaper with wineasio is one of the best options,
and won't be replaced by better solutions any time soon. You may want a selection of linux installs on usb-sticks, no one distro will be best at everything.
Cheers

---

### Post by sgx on 2010-05-11
Linux is best used as a warehouse store of tools, applied
in the real world without artificial limitations. Some choose to see it as a club, set apart from outside communities, an exlusive museum of singular interest, a view that can lead to unwanted frustrations.
Frustration and limitation are not healthy. Creative expression is. :)

---

### Post by jsevi83 on 2010-05-12
falkTX, I'm starting to use clementine player, and noticed that the ppa version has many more dependencies (xine related) than the package in the official webpage. Is there any reason/benefit? Which one should I use?

---

### Post by falkTX on 2010-05-12
> **jsevi83 said:**
> falkTX, I'm starting to use clementine player, and noticed that the ppa version has many more dependencies (xine related) than the package in the official webpage. Is there any reason/benefit? Which one should I use?

I would recommend using the package from my PPA.
It builds with the same libs we have in our PCs, so it will never have conflicts.

I'll look into the dependencies.
I know that Xine should not be needed anymore, clementine now uses GStreamer

EDIT: You're right. I removed the Xine dependencies (won't change anything at all).
Updated package is clementine_0.3-0ubuntu0+ppa3

---

### Post by jsevi83 on 2010-05-12
Thanks, you are fast!

edit: I just noticed that when using dynamicmultiband-lv2 in ardour there are only three bands, and band 4 and 5 are not working. I think it was working okay last time I used it (like three weeks ago).

---

### Post by hxcobd on 2010-05-13
Sgx is right; Falk, I apologize for the brash nature of my last post; after using your repo considerably more, I've come to greatly appreciate the huge variety of software (some of it VERY rare) you're offering.

Thanks for all your time and effort!

---

### Post by falkTX on 2010-05-13
> **psidrum said:**
> thanks for creating this, its great!

maybe you can also add these

[http://loopdub.sourceforge.net/](http://loopdub.sourceforge.net/)
[http://www.veejayhq.net/](http://www.veejayhq.net/)
[http://www.filter24.org/seq24/](http://www.filter24.org/seq24/)

loopdub - after checking the sources I noticed that it requires Steinberg ASIO SDK (non-free) to compile. This means I can't upload this, sorry.

veejayhq - package and upload. Will be available soon

seq24 - latest version already in Lucid

---

### Post by psidrum on 2010-05-14
thanks Falktx!

here is a dark kxstudio wallpaper to compliment the default theme that i made for anyone interested

[[IMG]http://img227.imageshack.us/img227/8131/kstudio.th.png[/IMG]](http://img227.imageshack.us/i/kstudio.png/)

---

### Post by falkTX on 2010-05-14
> **psidrum said:**
> thanks Falktx!

here is a dark kxstudio wallpaper to compliment the default theme that i made for anyone interested

[[IMG]http://img227.imageshack.us/img227/8131/kstudio.th.png[/IMG]](http://img227.imageshack.us/i/kstudio.png/)

Many thanks!
If you could upload it in other different sizes (1280, 1024, 1600, etc), I'll include in the "KXStudio-Artwork" package.

---

### Post by hxcobd on 2010-05-15
I am LOVING this PPA. So, so awesome. So many plugins and programs I had no idea even existed...

One problem I've noticed though:

the 'vst-plugin-all' package tries to install at least one vst in the directory:

/usr/lib32/vst/

Which doesn't exist on native 32-bit installs. I didn't notice which plugin in particular; wasn't paying attention. Must have been one of the last ones it tried to install.

---

### Post by psidrum on 2010-05-15
> **falkTX said:**
> Many thanks!
If you could upload it in other different sizes (1280, 1024, 1600, etc), I'll include in the "KXStudio-Artwork" package.

zipped file with all the resolutions

[download]("http://uploading.com/files/21a8c655/Kxstudio%2Bwallpapers.zip")

---

### Post by falkTX on 2010-05-16
> **hxcobd said:**
> I am LOVING this PPA. So, so awesome. So many plugins and programs I had no idea even existed...

One problem I've noticed though:

the 'vst-plugin-all' package tries to install at least one vst in the directory:

/usr/lib32/vst/

Which doesn't exist on native 32-bit installs. I didn't notice which plugin in particular; wasn't paying attention. Must have been one of the last ones it tried to install.

Thanks for the report, I'll look into this.

---

### Post by falkTX on 2010-05-16
> **psidrum said:**
> zipped file with all the resolutions

[download]("http://uploading.com/files/21a8c655/Kxstudio%2Bwallpapers.zip")

Many thanks.
I'll include it in an updated "kxstudio-artwork" package

---

### Post by mango42 on 2010-05-17
Hi,

Would any of you very kind PPA'ers be interested in packaging the latest Qtractor SVN from:-

[http://www.rncbc.org/snapshots/#qtractor](http://www.rncbc.org/snapshots/#qtractor)

qtractor-0.4.5.1568svn1565.tar.gz	700.7 KB	(717,496)	2010-05-15 16:01:31

?

Pushing my luck to the limit - 32 & 64 bit .debs for both Karmic & Lucid would make my month ;-)

Thanks for all you do!

ps: personally I'm not interested in VST's - prefer the CALF offerings ;-)

---

### Post by falkTX on 2010-05-17
> **mango42 said:**
> Hi,

Would any of you very kind PPA'ers be interested in packaging the latest Qtractor SVN from:-

[http://www.rncbc.org/snapshots/#qtractor](http://www.rncbc.org/snapshots/#qtractor)

qtractor-0.4.5.1568svn1565.tar.gz	700.7 KB	(717,496)	2010-05-15 16:01:31

?

Pushing my luck to the limit - 32 & 64 bit .debs for both Karmic & Lucid would make my month ;-)

Thanks for all you do!

ps: personally I'm not interested in VST's - prefer the CALF offerings ;-)


I'll do it right now!

I'll also update all SVN-based Debs too (I have a script :))

But, as you said, there won't be VST support for these.

---

### Post by sgx on 2010-05-17
> **mango42 said:**
> Hi,

Would any of you very kind PPA'ers be interested in packaging the latest Qtractor SVN from:-

[http://www.rncbc.org/snapshots/#qtractor](http://www.rncbc.org/snapshots/#qtractor)

qtractor-0.4.5.1568svn1565.tar.gz	700.7 KB	(717,496)	2010-05-15 16:01:31

?

Pushing my luck to the limit - 32 & 64 bit .debs for both Karmic & Lucid would make my month ;-)

Thanks for all you do!

ps: personally I'm not interested in VST's - prefer the CALF offerings ;-)

A while back I did some A/B testing comparing the big-name commercial
amp-sims against linux and winXXX freeware. My conclusions are framed by
my resolute ignorance regarding 'tone', and total inability to identify any legendary gear by listening. In addition, the tests were done
'in the cans', no real guitar amps. The guitar input was a clean preamped
tone, with a light hardware reverb. I also used the clean guitar preset
from zynaddsubfx, as the night was young :) A few opinions, in no meaningful order.

The freeware coders are amazing, regardless of platform. Intensity, clarity, grunge, filth, whatever label you like, the sound is all there, and in large quantity, from many different authors. The winXXX guys are
very public, and supportive of each other. Don't hear very much from
the linux devs.

The commercial coders are amazing. Vast quantities of gear are modeled,
and the polish, features, and depth one would expect for the sales price
is well within reason.

I really can't say 'this one sounds best', or 
'that one is easiest to use', there are so many variables, and so many unique and specific needs.  But an intelligent, well practiced musician has no excuse to sound lousy any more, thats for sure!

Folks in working bands might need to match the local competition, and
require commercial cloning apps, whereas knowledgeable solo artists
might find all they need for free, and pony up some donations to favorite authors. 

I'll actually use Rakararrack, and Freeamp 2.5/3.0 the most, rakarrack for both variety and quality, and freeamp for a certain piercing effect, like the sound just gets to the sweet spot faster, and with more precision, difficult to describe, like I said, I'm not a tone freak. 

Guitarix and calf-plugins, I spent less time with, and initial impressions are that they may be favourites for lots of users. LePou, and
AcmeBarGig also have some marvelous winXXX freeware, and most will work
in a wineasio setup, as do the commercial products.

Even old Creox has a home, as its my favorite for combos of
echo and tremolo, with a frosting of phaser.

Cheers :guitar:

---

### Post by falkTX on 2010-05-17
qtractor-vst is now available on the unstable PPA.
Almost every other package (in the unstable PPA) was updated.

Enjoy!

---

### Post by straypacket on 2010-05-17
> **philip5 said:**
> 
I have added so both Yoshimi and Arpage shows up in your menu but that's not standard and they don't have any icons yet so for the moment the icon looks like it does in your menu. I could change the icon to something more appealing if you like that is some general purpose icon on Ubuntu as a temporary solution until they make their own icons.


Hi there. I finally got an account here :)

In Arpage 0.3.3, there is now a PNG icon: ${prefix}/share/arpage/ui/arpage.png

I little rustic, but it's a start

---

### Post by philip5 on 2010-05-18
> **straypacket said:**
> Hi there. I finally got an account here :)

In Arpage 0.3.3, there is now a PNG icon: ${prefix}/share/arpage/ui/arpage.png

I little rustic, but it's a start

I used that icon for the menu in the arpage 0.3.3 package on my PPA. Did the same with the zonage icon. The new one is better than a generic anyway. :)

---

### Post by babarosa on 2010-05-18
May I politely ask once again for a package:

rakarrack for lucid _and_ jack1 - the one available at falktx's repo needs to install jack2.

Thanks to you for sharing your work with us, the ppa is wonderful!

---

### Post by mango42 on 2010-05-18
> **falkTX said:**
> I'll do it right now!

I'll also update all SVN-based Debs too (I have a script :))

But, as you said, there won't be VST support for these.

Nice one, **falkTX** - many thanks indeed. :KS

I wonder whether you and Rui know each other at all (sure, Portugal's a BIG country ;-)? I am fascinated by his sense of ergonomics, not to mention his coding skills.

------------------

@**sgx** Thanks for sharing your opinions - more in this vein would capture many budding Linux musos attention, IMO. My main gripe with VSTs is really nothing to do with the sound (which, thanks to early Deep Purple roady-ing, all gets filtered through my inbuilt organic tinnitus phaser anyway) but far more to do with the pixel-fiddling GUIs! Rakararrack is next on my list to try out...

Note to mods here: I know there's the Cafe 'down below' for general breeze-shooting but could not this UbuntuStudio area have its own sub-section right here for us noodlers/shredders to share such useful commentary? It sure would make a pleasant 'haute relivo' to such riveting subjects as ```
sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'
``` only to be told by Jack that it's 'very dangerous' ! :confused:

---

### Post by sgx on 2010-05-18
Rakarrack is more dangerous. It makes you forget what year it is, and how
young you is ;-)

---

### Post by falkTX on 2010-05-18
> **mango42 said:**
> Nice one, **falkTX** - many thanks indeed. :KS

I wonder whether you and Rui know each other at all (sure, Portugal's a BIG country ;-)? I am fascinated by his sense of ergonomics, not to mention his coding skills.


I tried the qtractor-svn myself, and although the changelog says it now supports LV2 UI, it doesn't. Same thing for DSSI (no fancy GUIs).

I don't know Rui, but I hope to meet him someday

---

### Post by philip5 on 2010-05-18
> **babarosa said:**
> May I politely ask once again for a package:

rakarrack for lucid _and_ jack1 - the one available at falktx's repo needs to install jack2.

Thanks to you for sharing your work with us, the ppa is wonderful!

It's now uploaded on my PPA for Lucid too.

---

### Post by psidrum on 2010-05-19
can this one be added too

[http://wired.sourceforge.net/](http://wired.sourceforge.net/)

looks interesting

---

### Post by falkTX on 2010-05-19
> **psidrum said:**
> can this one be added too

[http://wired.sourceforge.net/](http://wired.sourceforge.net/)

looks interesting

I tried that a long time ago...
Tried everything, but never got it to compile.

It seems a dead project to me, even the website isn't updated...

---

### Post by vervelover on 2010-05-19
@FalkTX

I reported a while ago that I could not see midi-through anymore in the jack midi connections in Lucid.. well now I've understood why: it's jack2 fault! 

If I revert to Lucid default jack (painful, had to reinstall LOTS of stuff because of broken dependencies), midi through appears where it should be! 

The problem is only with jack in your PPA, that forces me to a2jmidid. Also, I'm forced to install jack2 from your PPA beacause of a dependency in dssi-vst. Can you make dssi-vst not dependant on jack2?

---

### Post by falkTX on 2010-05-19
> **vervelover said:**
> @FalkTX

I reported a while ago that I could not see midi-through anymore in the jack midi connections in Lucid.. well now I've understood why: it's jack2 fault! 

If I revert to Lucid default jack (painful, had to reinstall LOTS of stuff because of broken dependencies), midi through appears where it should be! 

The problem is only with jack in your PPA, that forces me to a2jmidid. Also, I'm forced to install jack2 from your PPA beacause of a dependency in dssi-vst. Can you make dssi-vst not dependant on jack2?

I don't see any problem with a2jmidid, but anyway...

I'll let you guys know how to get the sources from my repo and rebuild it. Jack1/2 will depend on the version on _your_ system.

First, add the ppa source to "/etc/apt/sources.list":
```
deb-src http://ppa.launchpad.net/falk-t-j/lucid/ubuntu lucid main
```

And update (*sudo apt-get update*)

Now you can get any package and rebuild it with Jack1:
```
cd /some/folder
sudo apt-get build-dep <PACKAGE_NAME> #get the software needed to compile it
apt-get source <PACKAGE_NAME> #get the source
cd <PACKAGE_NAME>
debuild -rfakeroot #rebuild it

```

Enjoy

---

### Post by psidrum on 2010-05-21
Midi Through broken in Jack2??

hmm that needs to be fix,

because i can only use Midi Through to control a Wine VST from Seq24, without midi through i wont be able to control it or sequence windows VST with seq24

---

### Post by falkTX on 2010-05-21
> **psidrum said:**
> Midi Through broken in Jack2??

hmm that needs to be fix,

because i can only use Midi Through to control a Wine VST from Seq24, without midi through i wont be able to control it or sequence windows VST with seq24

It's not that midi is broken in Jack2. It's the _alsa emulation that is not implemented yet_.
You can still use Jack and ALSA for whatever you want, but, if you want the Jack-2-Alsa **midi** bridge, you have to use "a2jmidid" [Alsa2JackMidiDaemon, A-2-J-Midi-D].

I think users should get used to Jack2. It's very likely that 10.10 will have it.

---

### Post by trulan on 2010-05-21
I was one who was recommending staying with Jack1.  I gave Jack2 another spin this morning, and I think it works a lot better than it did a few months ago.   Jack2 had been pretty unstable when under heavy load using the ffado drivers (many more xruns than Jack1), but this seems to be much improved.  I'm still not ready to go into a recording session using Jack2, but I'm going to be using it for testing purposes.

---

### Post by psidrum on 2010-05-21
this would be a great addition too for the the video part

Ramen is a free node based video compositor, It works in full HDR color precision.

[https://launchpad.net/~gabriel-inv/+archive/ramenhdr](https://launchpad.net/~gabriel-inv/+archive/ramenhdr)
[http://ramenhdr.sourceforge.net/](http://ramenhdr.sourceforge.net/)

---

### Post by psidrum on 2010-05-21
> **falkTX said:**
> It's not that midi is broken in Jack2. It's the _alsa emulation that is not implemented yet_.
You can still use Jack and ALSA for whatever you want, but, if you want the Jack-2-Alsa **midi** bridge, you have to use "a2jmidid" [Alsa2JackMidiDaemon, A-2-J-Midi-D].

I think users should get used to Jack2. It's very likely that 10.10 will have it.

thnks for clarifying,

---

### Post by mango42 on 2010-05-25
Please ignore this.

---

### Post by sgx on 2010-05-25
I've tried that line on my wife occasionally, and it never works :)

---

### Post by rossco_50 on 2010-06-05
Hi,

I had been using the hydrogen svn version happily under Karmic, but upon upgrading to lucid the hydrogen svn package in the lucid bleeding edge PPA removes the ubuntustudio-audio metapackage on installation. 

If I remove hydrogen and reinstall ubuntustudio-audio the older version of hydrogen is installed. Should the metapackage not pull the SVN version from the bleeding edge repo? How do I get these to work together?

Thanks,

Ross

---

### Post by theclarkster on 2010-06-12
Hey all!

New here to the forums, and recently decided to make the switch from windows over to Linux.  I stumbled upon this neat little thread a few hours ago and have been trying to set up some good music software.  I'm trying to get Festige to run so I can use some VSTs.  I installed it in the software manager, but when I run it, nothing happens.  Is that what's supposed to happen?  Is it a separate window that runs outside of something like rosegarden? Or is there something I need to do to rosegarden to allow me to use it as a plugin?  As a sidenote, when I type festige into the terminal, I get the following:

Traceback (most recent call last):
  File "/usr/share/festige/festige.py", line 111, in <module>
    ladish = os.getenv(HOME)+"/.festige"
NameError: name 'HOME' is not defined

Thoughts?  I'm actually running Mint 9, so I'm not sure that has anything to do with the problem.  Anywho, thanks for all you fine people do to help noobs like myself out!

Travis

---

### Post by eric71 on 2010-06-13
I've never used festige, but I believe it is a stand alone jack eneabled program - so it would be hosting vst's or vsti's outside of Rosegarden. To host them as plugins inside of Rosegarden, try installing dssi-vst, which I believe is also available from this ppa. I think if your vsts are in a folder titled "vst" in your home folder, they should be seen in Rosegarden then.

---

### Post by falkTX on 2010-06-14
> **theclarkster said:**
> Hey all!

New here to the forums, and recently decided to make the switch from windows over to Linux.  I stumbled upon this neat little thread a few hours ago and have been trying to set up some good music software.  I'm trying to get Festige to run so I can use some VSTs.  I installed it in the software manager, but when I run it, nothing happens.  Is that what's supposed to happen?  Is it a separate window that runs outside of something like rosegarden? Or is there something I need to do to rosegarden to allow me to use it as a plugin?  As a sidenote, when I type festige into the terminal, I get the following:

Traceback (most recent call last):
  File "/usr/share/festige/festige.py", line 111, in <module>
    ladish = os.getenv(HOME)+"/.festige"
NameError: name 'HOME' is not defined

Thoughts?  I'm actually running Mint 9, so I'm not sure that has anything to do with the problem.  Anywho, thanks for all you fine people do to help noobs like myself out!

Travis

hmm, seems like it's an error from me. I'll fix it soon

---

### Post by theclarkster on 2010-06-14
@eric71:  Tried out dssi-vst for a bit, but kept getting crash reports from wine, todays update of FeSTige seemed to fix the crash.  Thanks!

@falkTX:  My update manager grabbed an update for FeSTige not too long ago.  I installed the update and BAM!  Opened up like a champ!  Thanks a million!  Now to start playing around with it....

Travis Clark

---

### Post by ronjouch on 2010-06-14
Hi there.

I saw a custom wine-1.2 popping up from your ppa ("1.2~rc3-0ubuntu1+winert1"). What specific patches/features does it include? For example, what is it going to bring to my REAPER on wine + wineasio?

Thanks again for your work! A goldmine!

---

### Post by kiwidoc66 on 2010-06-14
Hi FalkTX

I have an identical error to TheClarkster after building festige on a gentoo machine

davidg3@music ~/downloads/festige-0.4 $ festige
Traceback (most recent call last):
  File "/usr/share/festige/festige.py", line 111, in <module>
    ladish = os.getenv(HOME)+"/.festige"
NameError: name 'HOME' is not defined

Tried both python 2.6 and 3.1

---

### Post by falkTX on 2010-06-15
> **kiwidoc66 said:**
> Hi FalkTX

I have an identical error to TheClarkster after building festige on a gentoo machine

davidg3@music ~/downloads/festige-0.4 $ festige
Traceback (most recent call last):
  File "/usr/share/festige/festige.py", line 111, in <module>
    ladish = os.getenv(HOME)+"/.festige"
NameError: name 'HOME' is not defined

Tried both python 2.6 and 3.1

Just update, should be fixed by now.
If not, please report back again

---

### Post by falkTX on 2010-06-15
> **ronjouch said:**
> Hi there.

I saw a custom wine-1.2 popping up from your ppa ("1.2~rc3-0ubuntu1+winert1"). What specific patches/features does it include? For example, what is it going to bring to my REAPER on wine + wineasio?

Thanks again for your work! A goldmine!

It helps you get less xruns when running on low buffer sizes.
Edit your desktop file, or run manually with:
```
env WINERT=10 wine <app>
```
The WINERT value can be between -20 and 19, while the author, "JackWinter" from the #lad IRC, recommends using 10.

You can also run it with chrt, useful to get wine's graphic 2D painting a little faster:
```
chrt -f -p 1 env WINERT=10 wine <app>
```


With this I can safely run a heavy song while keeping 256 buffer size in FL Studio! 
(make sure u disable multi-core though, wine doesn't like it)

---

### Post by kiwidoc66 on 2010-06-15
Hi again - downloaded fresh tarball, same error sorry

---

### Post by falkTX on 2010-06-15
> **kiwidoc66 said:**
> Hi again - downloaded fresh tarball, same error sorry

ah, so you're using the sourceforge tarball one.
I fixed it in the PPA, but now I also uploaded the fixed one to sourceforge too.

Thanks for the report.

---

### Post by kiwidoc66 on 2010-06-16
Thanks - works well now.  BTW the link on the festige webpage points to the 4.0 tarball, not 4.1

---

### Post by falkTX on 2010-06-16
> **kiwidoc66 said:**
> Thanks - works well now.  BTW the link on the festige webpage points to the 4.0 tarball, not 4.1

You sure?
It's 0.4.1 here.

Can you try a refresh in your browser?

---

### Post by Steffen M on 2010-06-16
Hey, thanks so much for your work! Is it possible to add Ardour 2.8.9 for karmic to philip's repo? thanks a lot!

---

### Post by philip5 on 2010-06-16
> **Steffen M said:**
> Hey, thanks so much for your work! Is it possible to add Ardour 2.8.9 for karmic to philip's repo? thanks a lot!

It's building right now for karmic too so you'll have it available in a few minutes or so.

Have fun!

---

### Post by philip5 on 2010-06-19
Uploaded Spek 0.4 for both Lucid and Karmic to my PPA.

Spek &#8211; Acoustic Spectrum Analyser
[http://www.spek-project.org](http://www.spek-project.org)

[IMG]http://www.spek-project.org/flac.png[/IMG]

---

### Post by philip5 on 2010-06-23
If you like Rakarrack then don't miss the new 0.5.8 “Equinox” release. It got a bunch of new goodies to get your hands dirty with... :)

You find it among other places on my PPA for Lucid. (See info in my signature)

> NEWS
New Bank File format, we include a utility “rakconvert” to convert Bank files
to the new format.
New Effects:
Valve, Dual Flange, Ring, Exciter, Expander, DistBand, Arpie, Shuffle, Synthfilter,
VaryBand, Convolotron, Looper, MuTroMojo, Echoverse, CoilCrafter,
ShelfBoost, Vocoder, Sustainer, Sequence, Shifter, StompBox, Reverbtron,
Echotron.
New Features:
Tap Tempo.
Upsampling using libsamplerate by Erik de Castro Lopo.
Downsample intesive CPU effects.
Upsample Waveshapper.
ACI Analog Control Interface.
Waveshappers:
M.Saw, Compress, Overdrive, Soft, Super Soft, Gard Compress, Lmt-NoGain,
Hard Compress, FET, DynoFET, Valve1, Valve2, Diode clipper.
LFO Modulation:
M.Saw, L.Fractal.
Improvements:
GUI
DC Offset Filter at the input.
Tuner Callibration
Auto Connect jack input ports.
GUI and bug fixes.
The rakarrack team:
Josep Andreu - Ryan Billing - Douglas McClendon - Arnout Engelen

Have fun!

---

### Post by sgx on 2010-06-23
Thanks for making this available! Rakarrack may be the best audio app
in linux :guitar:

---

### Post by alvaromendes on 2010-06-24
my rakarrack dep:
rakarrack 0.5.8_Equinox - Copyright (c) Josep Andreu - Ryan Billing - Douglas McClendon - Arnout Engelen
Try 'rakarrack --help' for command-line options.
segmentation falt


does anyone know what is happening?

I tried compiling the source too, but the same problem occurs

---

### Post by philip5 on 2010-06-24
> **alvaromendes said:**
> my rakarrack dep:
rakarrack 0.5.8_Equinox - Copyright (c) Josep Andreu - Ryan Billing - Douglas McClendon - Arnout Engelen
Try 'rakarrack --help' for command-line options.
segmentation falt


does anyone know what is happening?

I tried compiling the source too, but the same problem occurs

It works perfect for me. My only guess is that somesystemfile might be corrupted on your system that it use. Otherwise I have no good idea why this would be. Non compatible dependencies could do this but shouldn't when you compile yourself.

---

### Post by AutoStatic on 2010-06-24
> **alvaromendes said:**
> my rakarrack dep:
rakarrack 0.5.8_Equinox - Copyright (c) Josep Andreu - Ryan Billing - Douglas McClendon - Arnout Engelen
Try 'rakarrack --help' for command-line options.
segmentation falt


does anyone know what is happening?

I tried compiling the source too, but the same problem occursYou have to delete/rename your old Rakarrack preferences directory* ~/.fltk/rakarrack.sf.net*

---

### Post by Steffen M on 2010-07-24
hi!
2 things: 

please add the new ardour 2.8.11 to phillips repo for karmic. thanks!  

and:
I have problems with the audacious package from phillip's repo. When  updating the following message occurs: (translated from German)

E:  /var/cache/apt/archives/audacious-plugins-extra_2.3-karmic~ppa1_i386.deb:  trying to overwrite »/usr/lib/audacious/Output/crossfade.so« which is  also part of package audacious-plugins 0

E: /var/cache/apt/archives/audacious-plugins_2.3-karmic~ppa1_i386.deb:  trying to overwrite »/usr/share/audacious/images/xiph.png« which is also  part of package audacious-plugins-extra 0

Do you have any idea what's going on? Since I don't need Audacious, is  there a way to remove the application without removing the whole  ubuntustudio-audio metapackage (this is what it always asks for)?

sorry for the newbie-ish question :)

---

### Post by AutoStatic on 2010-07-28
Update packages available for Rakarrack (0.6.x version from git), Yoshimi (0.058.1) and Guitarix (0.10.0 with the experimental widget enabled) in my PPA: [https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa)

---

### Post by falkTX on 2010-07-28
> **AutoStatic said:**
> Update packages available for Rakarrack (0.6.x version from git), Yoshimi (0.058.1) and Guitarix (0.10.0 with the experimental widget enabled) in my PPA: [https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa)

Hi there, some people have been doing this for some time, so I should warn:

Having "0.10.0-lucid~autostatic0 " as a package version is a bad thing!
That will override "0.10-0-1ubuntu1", which will break things once a new ubuntu version arrives (Maverick)

@AutoStatic:
I usually do it like "0.10-0ubuntu0" so it can be replaced on upgrade.
You could do it like this: "0.10.0-0lucid0~autostatic0", which is fine too.


Anyway, keep the good work

---

### Post by AutoStatic on 2010-07-28
Thanks falkTX! I will start renaming all my Lucid packages and upload them again, I don't want anyone to mess up their installs. Do you have a link by any chance about the versioning guidelines?

---

### Post by falkTX on 2010-07-28
> **AutoStatic said:**
> Thanks falkTX! I will start renaming all my Lucid packages and upload them again, I don't want anyone to mess up their installs. Do you have a link by any chance about the versioning guidelines?

hm, I don't have a link, I just asked the MOTUs on the IRC about how I should do it.

My prefered method is this:
*0.0.1-0ubuntu0+ppa1*
That will need a compatible source package (orig.tar.gz) and the build will fail if there's an "unrepresentable change to source" (quoted)

To force an update (like fixing an ubuntu bug), I do:
*0.0.1-0ubuntu1+fixed1*
This will make your package override the ubuntu one, but when a new ubuntu package comes, that will be used

For packages that have no orig.tar.gz:
*0.0.1-0ubuntu0~ppa1*
Using "~" in a package version will override the fact that you don't have an original source code archive, useful for git/svn packages

---

### Post by AutoStatic on 2010-07-28
Ok, thanks. I hope you don't mind I've also put up this info over here: [https://wiki.ubuntu.com/AutoStatic/PackagingVersioningScheme](https://wiki.ubuntu.com/AutoStatic/PackagingVersioningScheme)

---

### Post by falkTX on 2010-07-28
> **AutoStatic said:**
> Ok, thanks. I hope you don't mind I've also put up this info over here: [https://wiki.ubuntu.com/AutoStatic/PackagingVersioningScheme](https://wiki.ubuntu.com/AutoStatic/PackagingVersioningScheme)

hehe, it's cool :p

---

### Post by AutoStatic on 2010-08-03
LinuxSampler CVS checkout uploaded to my PPA: [https://launchpad.net/~autostatic/+archive/ppa/+packages](https://launchpad.net/~autostatic/+archive/ppa/+packages)

This CVS checkout of LinuxSampler has support for the SFZ format which makes it possible to use the Salamander Grand Piano sample pack: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-May/069495.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-May/069495.html)

Info on how to set it up: [http://wootangent.net/2010/05/the-salamander-grand-piano-and-linuxsampler-cvs/](http://wootangent.net/2010/05/the-salamander-grand-piano-and-linuxsampler-cvs/)

---

### Post by madeinfamous on 2010-08-05
allo all,

just to mention, the latest update "xserver-xorg-video-XXXX" broke my system, can't watch some movie with totem and/or vlc,

i revert back and it is ok now, but surely there is something wrong with your update ?

nice ppa by the way :)

if you need more info just ask.

---

### Post by falkTX on 2010-08-06
> **madeinfamous said:**
> allo all,

just to mention, the latest update "xserver-xorg-video-XXXX" broke my system, can't watch some movie with totem and/or vlc,

i revert back and it is ok now, but surely there is something wrong with your update ?

nice ppa by the way :)

if you need more info just ask.

Please give me more info, as the update works fine for me.

which package causes the issue? ...-video-ati or ...-video-intel ?

---

### Post by madeinfamous on 2010-08-06
allo falkTX,

"which package causes the issue? ...-video-ati or ...-video-intel ?"

i'm on a intel pc so i assume it's ****video-intel

my pc is dell inspiron 1525, ubuntu generic 10'04 amd64,

i've done the update in the morning, doing music all day, everything was working, then i sit on my couch to watch some movie and i couldn't :)

some crazy fuzzy line appears, the color is all wrong, i bet even my cam was not working but didn't try it,

maybe it's relate with gstreamer or some like it, i'm a craftsman, not a pc tech,  

i can reinstall the update and run some cmd if you provide them to me.

let me no & have a nice day

---

### Post by falkTX on 2010-08-06
> **madeinfamous said:**
> allo falkTX,

"which package causes the issue? ...-video-ati or ...-video-intel ?"

i'm on a intel pc so i assume it's ****video-intel

my pc is dell inspiron 1525, ubuntu generic 10'04 amd64,

i've done the update in the morning, doing music all day, everything was working, then i sit on my couch to watch some movie and i couldn't :)

some crazy fuzzy line appears, the color is all wrong, i bet even my cam was not working but didn't try it,

maybe it's relate with gstreamer or some like it, i'm a craftsman, not a pc tech,  

i can reinstall the update and run some cmd if you provide them to me.

let me no & have a nice day

hm, that's weird.
I have an Intel card here too, and it always worked fine for me.

Can you confirm that it is **really** the 'xserver-xorg-video-intel' that is causing issues?

---

### Post by madeinfamous on 2010-08-06
allo falkTX,

i confirm :)

[https://sites.google.com/site/nueusx/maj.png]("https://sites.google.com/site/nueusx/maj.png")

after applying the update this is what i see

[https://sites.google.com/site/nueusx/video-intel.png]("https://sites.google.com/site/nueusx/video-intel.png")

---

### Post by falkTX on 2010-08-06
> **madeinfamous said:**
> allo falkTX,

i confirm :)

[https://sites.google.com/site/nueusx/maj.png]("https://sites.google.com/site/nueusx/maj.png")

after applying the update this is what i see

[https://sites.google.com/site/nueusx/video-intel.png]("https://sites.google.com/site/nueusx/video-intel.png")

Ok, I'll then revert the changes

strange how it worked fine for me,
but anyway...

the fixed update ("xserver-xorg-video-intel_2.11.0-0ubuntu1+really2.9.1") will come soon

---

### Post by madeinfamous on 2010-08-06
gracias, merci, thank you,

i will add that it's not all movie, some .avi play fine when others dont,



and for something new, your jammin dont see my preset bank, (if i drag & drop one in the open windows it work fine)

 [https://sites.google.com/site/nueusx/jamin_preset.png]("https://sites.google.com/site/nueusx/jamin_preset.png")

the generic one see them, but use to much cpu, so if you have time to fix yours... you will made my day :guitar:

---

### Post by madeinfamous on 2010-08-14
thx falkTX,

"xserver-xorg-video-XXXX" all working fine! :)

so for the others, don't be afraid to add the ppa


also, can someone put this thread on "Sticky Threads" mode ?

i don't really understand why it hasn't been already :|

anyway, keep up the good work!  its all *fraking* good!

---

### Post by falkTX on 2010-08-16
> **madeinfamous said:**
> thx falkTX,

"xserver-xorg-video-XXXX" all working fine! :)

so for the others, don't be afraid to add the ppa


also, can someone put this thread on "Sticky Threads" mode ?

i don't really understand why it hasn't been already :|

anyway, keep up the good work!  its all *fraking* good!

Thanks!

Since I add/update many stuff, I now have a changelog of the main PPA:
[http://kxstudio.sourceforge.net/downloads/PPA-Changes](http://kxstudio.sourceforge.net/downloads/PPA-Changes)

My latest/unstable PPA has now more packages - seq24-bzr and gimp-git.


I have enough space on both PPAs (thanks Launchpad!), so feel free to request any new (opensource) package, even unstable ones.


Enjoy!

---

### Post by luctor on 2010-08-16
> **falkTX said:**
> 
I have enough space on both PPAs (thanks Launchpad!), so feel free to request any new (opensource) package, even unstable ones.
Enjoy!

Maybe you can include my Sonic Visualiser packages + vamp plugins ..
[https://launchpad.net/~rghvdberg/+archive/sv](https://launchpad.net/~rghvdberg/+archive/sv)

---

### Post by falkTX on 2010-08-16
@luctor:

I'll do it, thanks.

But last time I checked, some vamp plugins couldn't be compiled at all...
Check the ppa changelog at some later time to find which packages were added/updated

---

### Post by tehk on 2010-08-18
I have a messy problem. I started out with Kubuntu 10.04 and then added your repositories and upgraded all my packages to what KXstudio provides.

Before, I had jackd running and now jackdmp will not start. It took quite a bit of hacking to get my Native Instruments Audio8DJ card to work with jack and I had to write my own .asoundrc file for jack to recignize it. Here it is:

```
pcm_slave.DJ0 { pcm "hw:1,0,1" }


pcm.usb { 
	type plug
	slave DJ0
}


ctl.usb {
	type plug
	slave DJ0
}

pcm.multi {
	type multi;

	slaves.a.pcm "hw:1,0,0";
	slaves.a.channels 2;

	slaves.b.pcm "hw:1,0,1";
	slaves.b.channels 2;

	slaves.c.pcm "hw:1,0,2";
	slaves.c.channels 2;

	slaves.d.pcm "hw:1,0,3";
	slaves.d.channels 2;

	bindings.0.slave a;
	bindings.0.channel 0;
	bindings.1.slave a;
	bindings.1.channel 1;

	bindings.2.slave b;
	bindings.2.channel 0;
	bindings.3.slave b;
	bindings.3.channel 1;

	bindings.4.slave c;
	bindings.4.channel 0;
	bindings.5.slave c;
	bindings.5.channel 1;

	bindings.6.slave d;
	bindings.6.channel 0;
	bindings.7.slave d;
	bindings.7.channel 1;
}


ctl.multi {
	type hw;
	card 0;
}


pcm.ttable {
	type route;
	slave.pcm "multi";

	ttable.0.0 1;
	ttable.1.1 1;

	ttable.2.2 1;
	ttable.3.3 1;

	ttable.4.4 1;
	ttable.5.5 1;

	ttable.6.6 1;
	ttable.7.7 1;
}


ctl.ttable {
	type hw;
	card 0;
}

```

So, before the upgrade, I was able to start jack by making a call like this:

```
/usr/bin/jackd -R -dalsa -r 44100 -p1024 -n3 -i8 -o8 -dttable
```

Now, it was my understanding that from the documentation present, jack2 (jackdmp) should have the same invocation options. However, when I call it, here's the output I get:

```
jackdmp 1.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
control open "ttable" (No such file or directory)
control open "ttable" (No such file or directory)
audio_reservation_init
process 7338: arguments to dbus_message_new_method_call() were incorrect, assertion "_dbus_check_is_valid_path (path)" failed in file dbus-message.c line 1078.
This is normally a bug in some application using the D-Bus library.
Failed to acquire device name : Audio-1 error : Cannot allocate memory
Audio device ttable cannot be acquired, trying to open it anyway...
creating alsa driver ... ttable|ttable|1024|3|44100|8|8|nomon|swmeter|-|32bit
control open "ttable" (No such file or directory)
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server

```

I'm hoping there something really small I'm missing so I can get back on "the path" :)

---

### Post by falkTX on 2010-08-18
> **tehk said:**
> So, before the upgrade, I was able to start jack by making a call like this:

```
/usr/bin/jackd -R -dalsa -r 44100 -p1024 -n3 -i8 -o8 -dttable
```

Now, it was my understanding that from the documentation present, jack2 (jackdmp) should have the same invocation options. However, when I call it, here's the output I get:

```
jackdmp 1.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
control open "ttable" (No such file or directory)
control open "ttable" (No such file or directory)
audio_reservation_init
process 7338: arguments to dbus_message_new_method_call() were incorrect, assertion "_dbus_check_is_valid_path (path)" failed in file dbus-message.c line 1078.
This is normally a bug in some application using the D-Bus library.
Failed to acquire device name : Audio-1 error : Cannot allocate memory
Audio device ttable cannot be acquired, trying to open it anyway...
creating alsa driver ... ttable|ttable|1024|3|44100|8|8|nomon|swmeter|-|32bit
control open "ttable" (No such file or directory)
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server

```

I'm hoping there something really small I'm missing so I can get back on "the path" :)


Do you really need to set a asoundrc file to use your card?

Anyway, the "-R" option is not needed anymore, jack is run at realtime by default now.

Try using this command:
```
/usr/bin/jackd -d alsa -r 44100 -p 1024 -n 3 -i 8 -o 8 -d ttable
```

If it still fails, you can try to use the old jack1 (available at my ppa too), with this:
```
sudo apt-get install jack1-opt
jack1 jackd -d alsa -r 44100 -p 1024 -n 3 -i 8 -o 8 -d ttable
```
Then run all apps like this:
```
jack1 <app>
```

---

### Post by AutoStatic on 2010-08-18
As I needed FFADO from svn to be able to use our new soundcard I uploaded an updated package to my PPA. This package makes it fairly easy to use cards like the most recent Focusrite Saffire Pro series to work with Lucid. Install the ffado packages from my PPA and you should be good to go. Hopefully I named the package correctly, I'd still welcome a definitive guide/page/guideline/whatever on the Ubuntu versioning scheme.

[https://launchpad.net/~autostatic/+archive/ffado](https://launchpad.net/~autostatic/+archive/ffado)

---

### Post by trulan on 2010-08-18
> **AutoStatic said:**
> As I needed FFADO from svn to be able to use our new soundcard I uploaded an updated package to my PPA. This package makes it fairly easy to use cards like the most recent Focusrite Saffire Pro series to work with Lucid. Install the ffado packages from my PPA and you should be good to go. Hopefully I named the package correctly, I'd still welcome a definitive guide/page/guideline/whatever on the Ubuntu versioning scheme.

[https://launchpad.net/~autostatic/+archive/ffado]("https://launchpad.net/%7Eautostatic/+archive/ffado")
This may or may not be useful information to anyone, but this new packaging of Ffado should make it possible to use the new Juju firewire stack on Lucid.  You'll need to be running kernel 2.6.32 or newer, and you'll need to edit /etc/modprobe.d/blacklist-firewire.conf to select the new stack instead of the old one.  You'll also want to edit /etc/default/rtirq and change 'ohci1394' to 'firewire' in the names list.

Pros for the new stack:
Lower CPU usage, no more annoying permissions settings, better security.

Cons for the new stack:
Multiple devices (daisychaining) is not yet supported, support is slated to come in kernel 2.6.36.

Happy testing!

Edit:  Couldn't leave my hands off of it, I had to try it myself.  And - - - it doesn't work.  Oh, Autostatic's packaging of FFADO works fine, just not with the new firewire stack.  Suspected reasons are:
1. This FFADO package calls itself 2.0.0-svn*, and support with the new stack came with 2.0.1.  I assumed this build was of the 'latest' svn, but maybe it isn't.
2. The handling of the modules is much messier than I expected in Lucid.  I couldn't get things to load up properly automatically, I had to manually rmmod the legacy firewire modules and modprobe the new ones.  It's possible I got something wrong there (although I've used the new firewire stack in Maverick and in AVLinux-Debian Sid with no problems, so I don't think so.)
Anyway, that's the story there.

---

### Post by tehk on 2010-08-18
> **falkTX said:**
> Do you really need to set a asoundrc file to use your card?

Anyway, the "-R" option is not needed anymore, jack is run at realtime by default now.

Try using this command:
```
/usr/bin/jackd -d alsa -r 44100 -p 1024 -n 3 -i 8 -o 8 -d ttable
```

If it still fails, you can try to use the old jack1 (available at my ppa too), with this:
```
sudo apt-get install jack1-opt
jack1 jackd -d alsa -r 44100 -p 1024 -n 3 -i 8 -o 8 -d ttable
```
Then run all apps like this:
```
jack1 <app>
```

The realtime option makes no difference whatsoever. If you would have read over the error messages from when I attempted launching jackdmp, you would notice that it's unable to pick up the name of my card for some reason. So, your suggestion did not help much.

Also, yes, there is no other way to have jack1 launch without a custom crafted .asoundrc file for my device.

I think I'll take this up with the jack people. Thanks for trying.

---

### Post by AutoStatic on 2010-08-19
> **trulan said:**
> This FFADO package calls itself 2.0.0-svn*, and support with the new stack came with 2.0.1.  I assumed this build was of the 'latest' svn, but maybe it isn't.Hello trulan, it's revison 1881, about a week old. The lib is called 2.999.0 so I assume this is about 2.0.1. But I'll give 2.0.1 a try too, maybe that yields better results with the juju stack.

---

### Post by AutoStatic on 2010-08-19
Ok, the 2.0.1 branch doesn't have DICE support so it's not useful for me to upload 2.0.1 to my PPA since I need the version from trunk. But I can build packages and put them up somewhere. I did get some advice on the Python code for the mixer, probably the mixer in my package doesn't work well or maybe doesn't work at all.

---

### Post by madeinfamous on 2010-08-19
allo falkTX,

*"so feel free to request any new (opensource) package, even unstable ones"*

thx, but nothing really... except... maybe...

get rid of compiz in your ppa or stop messing with the default conf :|

lol, thx :)

a nice weekend to all!

---

### Post by marseille on 2010-08-19
I just want to say thank-you for ROSEGARDEN 10.04 :KS Having fun !!

---

### Post by falkTX on 2010-08-20
> **madeinfamous said:**
> allo falkTX,

*"so feel free to request any new (opensource) package, even unstable ones"*

thx, but nothing really... except... maybe...

get rid of compiz in your ppa or stop messing with the default conf :|

lol, thx :)

a nice weekend to all!

The compiz on my PPA was _copied_ from the official compiz PPA.
I just added the kde package again (why would they remove it anyway??)

---

### Post by mango42 on 2010-08-22
> **AutoStatic said:**
> Ok, the 2.0.1 branch doesn't have DICE support so it's not useful for me to upload 2.0.1 to my PPA since I need the version from trunk. But I can build packages and put them up somewhere. I did get some advice on the Python code for the mixer, probably the mixer in my package doesn't work well or maybe doesn't work at all.

I wonder how many pro24/40 users beside me are awaiting the results of yours and **trulan**'s (and UbuntuStudio PPA'ers everywhere) great efforts to untangle this Gordian Knot, or at least break through the JuJu veil?

It's all triple-Dutch to me but I have total faith that your tenacity will overcome all obstacles to firewire nirvana 'real soon now'

Grateful thanks for keeping an old muso fascinated :popcorn:

---

### Post by AutoStatic on 2010-08-22
Hello mango42, the juju stack can't be used with the Saffire Pro 24/40, you need FFADO from trunk and that branch doesn't have support for the new FireWire stack. So you can only use it with the old stack. You can grab a package of the svn trunk of FFADO here: [https://launchpad.net/~autostatic/+archive/ffado](https://launchpad.net/~autostatic/+archive/ffado)

Works fine for me, except for the mixer, that doesn't work yet. It starts up but adjusting stuff has no effect. No problem for me, I barely use it anyway.

---

### Post by mango42 on 2010-08-22
Wow! And all after two wheelbarrows full of beer - impressive :D

Do I need all the amd64 packages including libffado-dev_2.0.0... sorry to be awkward but I keep that machine away from the net, so it has to be .debs rather than synaptic, I guess.

Thanks so much for all you do.

---

### Post by AutoStatic on 2010-08-22
You don't need the dev packages. The packages have been tested on a 64-bits machine and the drivers work very well. Like I said, the mixer is not functional though. These packages shouldn't bork your system because they install and uninstall cleanly, big advantage of debs. So you can always downgrade again. What version of JACK are you using? It has been tested with Jack1, the version that comes with Lucid (0.118-something).

---

### Post by vervelover on 2010-08-22
Hi there,

this might have been covered already but it's a LONG thread so forgive me for not having read it all ;) I'm trying to have my fst plugins loaded in ladish with the right .fps state loaded, but I can't find any suitable command for this purpose. The Festige websites says the plugins state are now on auto-save on SIGUSR1, but what does that mean?

Thanks and keep up the amazing work!!

p.s. also, what is the command to load an Ardour project on startup? :lolflag:

---

### Post by falkTX on 2010-08-23
> **vervelover said:**
> Hi there,

this might have been covered already but it's a LONG thread so forgive me for not having read it all ;) I'm trying to have my fst plugins loaded in ladish with the right .fps state loaded, but I can't find any suitable command for this purpose. The Festige websites says the plugins state are now on auto-save on SIGUSR1, but what does that mean?

Thanks and keep up the amazing work!!

p.s. also, what is the command to load an Ardour project on startup? :lolflag:

Seems like you need to understand a little more about ladish, but no prob ;)

FeSTige has a custom built-in 'fst' with ladish support (the SIGUSR1 thing).
Basically it will auto-save it's state when received the SIGUSR1 signal:
```
killall -SIGUSR1 fst.exe.so
```

This way you can send this signal, close all VSTs and the next time you open them, they will be just like they were before.

The command to use this festige's fst is:
```
/usr/share/festige/fst/fst.exe </path/to/state-file> <VST-Plugin.dll>
```
*(It's ok if the 'state-file' doesn't exist when you first start fst)*

---

### Post by mango42 on 2010-08-23
> **AutoStatic said:**
> What version of JACK are you using? It has been tested with Jack1, the version that comes with Lucid (0.118-something).

Yep: .118+svn3796...

I will let you know how I get on, once I've solved a new issue with Firefox running the cpu at 100% in 10.04.1 and no flash plugins working ! Is this a move by adobe/g00gle to herd everyone into Chrome?

It never stops, does it? ;(

---

### Post by trulan on 2010-08-24
> **AutoStatic said:**
> Ok, the 2.0.1 branch doesn't have DICE support so it's not useful for me to upload 2.0.1 to my PPA
Ah, that makes sense - it's always nice to know why something doesn't work.   ;)

It's no big deal to me, I can always boot into Maverick if I feel the need to play with the new firewire stack - and I need to stick with the legacy firewire stack for the time being anyway, until they get daisychaining working.  Just my incessant need to tinker I guess...

---

### Post by blablack on 2010-08-29
Hi guys,

First of all, thanks for all the effort! I'm recording music with Linux for almost a year and you have no idea how you made my life way easier.

I used to compile everything manually and I realised few days ago that a lot of things were messed up (LV2 not working, impossible to use Ingen, etc...). I re-installed my ubuntu few days ago, set up the PPA, and in less than few minutes, I had all the tools back installed, everything working perfectly! Again thanks a lot for that.

A small question though. Did any of you got to load a DSSI plugin into Ingen? I succeeded to load LV2 plugins setting up the LV2_PATH variable, but even though I setup the DSSI_PATH variable, it doesn't display any entry in the plugins list. I am especially interested by the XY-Controller-DSSI and and the LL-Scope (I am trying to use Ingen as I used to use AlsaModularSynth, an oscilloscope would be really handy, and I'm trying to use the XY-Controller like Kork Kaos...).

Thanks in advance for the help.

At the same time, here is what I recorded so far:
[http://www.myspace.com/aviowhi]("http://www.myspace.com/aviowhi")
(Sorry for the crappy sound... Thank you Myspace). Except the guitars, everything is recorded using Linux instruments (especially Hydrogen and AlsaModularSynth). If anyone is interested by the AMS patches, let me know!

Thanks again,

Blablack

---

### Post by madeinfamous on 2010-08-29
@ blablack,

man you're good! sound good too! i like it!

i request you to register at [soundcloud]("http://soundcloud.com/") so i could enjoy a better sound (like a .flac format in download in respect of your copyright/copyleft licenses):)

there is option to link to your myspace, sort of...

anyway, i'm out of topic, so i'll end it here :)

---

### Post by mango42 on 2010-08-30
> **madeinfamous said:**
> i request you to register at [soundcloud]("http://soundcloud.com/") so i could enjoy a better sound (like a .flac format in download in respect of your copyright/copyleft licenses):)

there is option to link to your myspace, sort of...

anyway, i'm out of topic, so i'll end it here :)

++1 - excellent off topic post - **Soundcloud** is certainly the 'bees knees' and not a g00gle advert in sight!

Also coming up in the Open Source arena - brilliant alternatives to Farcebook, Twitter and other such demonic traps for the unwary:-

Bye bye twitter, hello [http://status.net/](http://status.net/)
Bye bye farcebook, hello [http://www.joindiaspora.com/index.html](http://www.joindiaspora.com/index.html)

and good riddance g00gle, hello [https://startpage.com/](https://startpage.com/)

Hey and kudos to **blablack** - Linux meets Black Sabbath? ;-)

---

### Post by jsevi83 on 2010-08-30
Maybe you could compile gnome-mplayer-0.9.99.rc1 for your bleeding-edge repository. I don't know if there is a final release coming soon.

---

### Post by falkTX on 2010-08-30
@blablack: I didn't know Ingen supported DSSI... 
There is not a single line about DSSI in the build log, but the Ingen page mentions DSSI... (strange)
I'll add 'dssi-dev' to the build depends anyway, just to be sure.

@jsevi83: I'll add it soon (package will be 'gnome-mplayer-svn')

---

### Post by blablack on 2010-08-30
And that's why I love Linux :D Nothing beats our community!

@madeinfamous and mango42: Thanks guys, I'll check soundcloud straight away! Have been looking for a while now on how to distribute my music with a better sound!

@faltfx: Upgraded, still no DSSI in sight... I'll try and compile ingen manually to see if there is no options to activate DSSI... I'll let you know if I find something!

---

### Post by blablack on 2010-08-31
About my DSSI question with Ingen, here might be the answer:
[http://dev.drobilla.net/ticket/379]("http://dev.drobilla.net/ticket/379")

Next time, I should RTFM before asking :)

---

### Post by JC Cheloven on 2010-08-31
Hi, I see the recent Traverso 0.49.2 in Falk's PPA. Thank you !

This release is mainly intended to fix a problem caused by a change in the behaviour of Qt libraries, but it's important, because that change made Traverso freeze on Lucid and other distros using latest Qt. 

@philip5 (in the event you keep reading this thread): version 0.49.2 also fixes a problem with fades out, which wasn't completely applied under certain circumstances. Also, it has translation to spanish (I did that). So, perhaps you may consider updating Traverso in your ppa as well, even though the 0.49.1 version in your ppa has the patch that makes it work in lucid.

Anyway, 0.49.2 is kind of an 'emergency' release. It's not the result of the (great) development effort invested in Traverso since 0.49.1. The 'true' new release should be out soon, but it's taking a bit longer than expected (hence the present release, to fill the gap).

JC

---

### Post by blablack on 2010-09-03
Hey guys,

Did anyone try the Lucid PPA against Maverick?

I really want to try the beta version, and I can live with the bugs for a month, but I can't live with softwares missing (thinking especially about LinuxSampler)...

---

### Post by falkTX on 2010-09-03
> **blablack said:**
> Hey guys,

Did anyone try the Lucid PPA against Maverick?

I really want to try the beta version, and I can live with the bugs for a month, but I can't live with softwares missing (thinking especially about LinuxSampler)...

I don't plan to make my PPA available for Maverick, mostly because of the KXStudio project (will not have a Maverick release).

BUT, I think I can create a new PPA with my packages compiled for Maverick (doesn't take much time, so...)


Just give me a few days and a Maverick PPA will be available, but I won't be able to test it myself.
Of course, I'll listen to any bug reports

---

### Post by shimoda on 2010-09-04
Hi!

I'm using this fantastic packages and I only have a minor problem...

After the upgrade, now in Kdenlive the thumbnails appear "crashed"...

[IMG]http://img707.imageshack.us/img707/4619/thumbsz.jpg[/IMG]

In terminal appear some messages, as:
> Diverting av_*_packet function calls to libavcodec. Recompile to improve performance

I tried the svn version of kdenlive, but I've the same problem... I don't know if its really something with libavcodec...

Someone with the same prob??:confused:

---

### Post by shimoda on 2010-09-04
UPDATE:

I don't know what are the consequencies of doing that, but it finally worked...

I did:

- Switch from libavcodec to libavcodec-extra
- Uninstall ffmpeg (uninstalls some packages)
- Disable falktx PPA
- Force Downgrade of libavcodec-extra (to ubuntustudio version)
- Install ffmpeg 
- Install the packages auto-uninstalled (mencoder and some other I can't remember)

Now works, but I can't upgrade the libavcodec/mencoder/etc... packages from falktx PPA

I did the change from libavcodec to libavcodec-extra because the forced uninstalled packages from the downgrade were a lot more with libavcodec (vlc, kino, xjadeo, openshot...)


Edit: UPDATE 2:
Confirmed!!

If I update ffmpeg with falkPPA, the thumbs appear broken again... It seems that there's some kind of problem with that ffmpeg and kdenlive... No one has the same problem?

---

### Post by houndi on 2010-09-05
Question though, what package method do you use? I'd like to know, first because I think packaging for Ubuntu doesn't seem as straightforward

---

### Post by houndi on 2010-09-05
For the non-geeks here, just add your ppa then download and click on install package? No need to uninstall anything? It's okay to install these debs over the top of previously installed packages?

---

### Post by AutoStatic on 2010-09-05
> **houndi said:**
> For the non-geeks here, just add your ppa then download and click on install package? No need to uninstall anything? It's okay to install these debs over the top of previously installed packages?You can add a PPA yes, personally I prefer to download separate packages. No need to uninstall, the package manager does that for you.

---

### Post by AutoStatic on 2010-09-05
> **houndi said:**
> Question though, what package method do you use? I'd like to know, first because I think packaging for Ubuntu doesn't seem as straightforwardIt doesn't seem straightforward at first glance but when you get to know all the tools a little it becomes way easier. Maybe it's best to read the Packaging Guide first: [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

And then get familiar with all the tools (debuild, dpkg-source, dh_make, pbuilder, etc.). I use pbuilder-dist myself, this allows me to test packages for several distro's and architectures on a single machine. Not only if they build properly, but also to check if the dependencies are set right in the debian/control files.

---

### Post by falkTX on 2010-09-05
> **shimoda said:**
> UPDATE:

I don't know what are the consequencies of doing that, but it finally worked...

I did:

- Switch from libavcodec to libavcodec-extra
- Uninstall ffmpeg (uninstalls some packages)
- Disable falktx PPA
- Force Downgrade of libavcodec-extra (to ubuntustudio version)
- Install ffmpeg 
- Install the packages auto-uninstalled (mencoder and some other I can't remember)

Now works, but I can't upgrade the libavcodec/mencoder/etc... packages from falktx PPA

I did the change from libavcodec to libavcodec-extra because the forced uninstalled packages from the downgrade were a lot more with libavcodec (vlc, kino, xjadeo, openshot...)


Edit: UPDATE 2:
Confirmed!!

If I update ffmpeg with falkPPA, the thumbs appear broken again... It seems that there's some kind of problem with that ffmpeg and kdenlive... No one has the same problem?


Thanks for letting me know,
I'll see what this error is about about and I'll report back ASAP

---

### Post by jsevi83 on 2010-09-14
Any news on gnome-mplayer-0.9.99.rc1? I tried to compile myself without success...

---

### Post by falkTX on 2010-09-15
> **jsevi83 said:**
> Any news on gnome-mplayer-0.9.99.rc1? I tried to compile myself without success...

Sorry I've been very busy lately,
and also because I dont have network access at home, sometimes it's hard to get everything done...

But don't worry, I haven't forgot about this (I have a TODO list on my desktop!)

---

### Post by falkTX on 2010-09-15
@shimoda:
The kdenlive thumbnails are now fixed (just needed to rebuild mlt against the new ffmpeg 0.6).

There may be other apps with wrong thumbnails/previews, you guys just let me know if you find any. (I can't test them all...)



@AutoStatic and philip5:
I've been talking to Scott on IRC about a team PPA for 11.04.
it's 11.04 because it gives us enough time to check/fix any package errors, or even fix bugs in the software itself.

Let me know what you think



@__everyone__:
I'll **not** make a Maverick PPA.
Sorry but I just dont have the time now, and if I'm going to create a new PPA, it will be for 11.04.
Because 11.04 development has not even start yet, it gives me the time I need right now... ;)

---

### Post by AutoStatic on 2010-09-15
FalkTX, I've already told Scott that I would really like to cooperate on setting up a collaborative 11.04 UbuStu PPA. Haven't been much on IRC lately, atm IRC is a bit too much distracting me, I do need to get some work done.
But I think a collaborative PPA is a very good idea. Count me in.

Best,

Jeremy

---

### Post by blablack on 2010-09-15
FalkTX, in addition of being a musician, I'm also a developer :-)

How complicated is it to maintain such a repository for Maverick? I can handle pretty well to compile software, but I never messed around building deb package, even less playing around repositories!

(I know you're busy, but) If you have scripts, or some kind of how-to, I can try and provide my fair share of work :-)

---

### Post by falkTX on 2010-09-18
> **AutoStatic said:**
> FalkTX, I've already told Scott that I would really like to cooperate on setting up a collaborative 11.04 UbuStu PPA. Haven't been much on IRC lately, atm IRC is a bit too much distracting me, I do need to get some work done.
But I think a collaborative PPA is a very good idea. Count me in.

Best,

Jeremy

Thanks!

I will be busy for the next few days too,
but I should be able to get working on this soon enough (maverick is not even released, so...)

We should discuss this some time soon

---

### Post by falkTX on 2010-09-18
> **blablack said:**
> FalkTX, in addition of being a musician, I'm also a developer :-)

How complicated is it to maintain such a repository for Maverick? I can handle pretty well to compile software, but I never messed around building deb package, even less playing around repositories!

(I know you're busy, but) If you have scripts, or some kind of how-to, I can try and provide my fair share of work :-)

do you have a gpg key?

try to create a testing PPA and make some basic packages.
(use some of these as base - [https://launchpad.net/~falk-t-j/+archive/kxstudio](https://launchpad.net/~falk-t-j/+archive/kxstudio)
they are mostly artwork and meta packages)

---

### Post by AutoStatic on 2010-09-19
@blablack:

Setting up a PPA: [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)
Packaging Guide: [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)
Versioning (far from complete): [https://wiki.ubuntu.com/AutoStatic/PackagingVersioningScheme](https://wiki.ubuntu.com/AutoStatic/PackagingVersioningScheme)

I use pbuilder-dist myself, packages take more time to compile for testing but it does allow me to upload packages that will build without failing.

Best,

Jeremy

---

### Post by blablack on 2010-09-19
@Autostatic and @FalkTX

Thanks guys, as soon as I can upgrade to Maverick I will have a better look at it all!

---

### Post by blablack on 2010-09-23
Hey guys,

Created my PPA for Maverick !
```
ppa:blablack/maverick-music
```

For the moment I have.............one library (libgig) and my plan is at least to add LinuxSampler, QSampler and Gigedit into my repository (easy packages, the packages can be created straight away).

@Autostatic and @FalkTX: To be honest, I wasn't expected such a system at all! To be sure I understand well what I am doing, can you correct me if I am wrong:
1. ```
debuild -S -sa
``` prepare the source code for Launchpad, it doesn't really compile anything.
2. ```
pbuilder-dist maverick i386 build *.dsc
``` simulates what's going to happen on the Launchpad servers (so I can test the compilation without wasting their resources and my time)
3. ```
dput
``` uploads the information to the Launchpad servers
4. Wait until the compilation on their side is completed.

So if I am right, my assumptions that I was supposed to compile the deb packages were wrong, right?

---

### Post by AutoStatic on 2010-09-23
> **blablack said:**
> Created my PPA for Maverick !
```
ppa:blablack/maverick-music
```Nickel!

> **blablack said:**
> @Autostatic and @FalkTX: To be honest, I wasn't expected such a system at all!PPA's are one of the reasons why I use Ubuntu and like it so much :)

> **blablack said:**
> So if I am right, my assumptions that I was supposed to compile the deb packages were wrong, right?Yes that's right, you don't need to compile anything yourself, well, only to test if the packages build correctly. Then you upload the whole bunch to Ubuntu's servers and they compile and publish the packages for you.

---

### Post by falkTX on 2010-09-24
@blablack:
Please read what AutoStatic wrote about the version naming:
[https://wiki.ubuntu.com/AutoStatic/PackagingVersioningScheme](https://wiki.ubuntu.com/AutoStatic/PackagingVersioningScheme)

I would recommend you to use something like:
*0.1.0-0ubuntu0+ppa1*
or 
*0.1.0-0ubuntu1~ppa1*

cause this way official Ubuntu packages will override yours (which is usually preferred),
and it will make sure the upgrade process works (from maverick->11.04)

---

### Post by blablack on 2010-09-27
@FalkTX

I changed the versionning, still not sure I got it right though...

Between the info in the link you provided and the warning Lintian is giving me when preparing the package with debuild, I am getting confused.

If you could check it out quickly and let me know!

Anyway, all linuxsampler is uploaded, as well as the LV2 version of the SWH plugins.

Started with the SVN version of Hydrogen now, fighting with SCons and PBuilder...

---

### Post by pbenerjee on 2010-09-28
Thanks Jeremy. That was useful

---

### Post by ronjouch on 2010-09-28
Hi falkTX, hi everybody.

Alessio, the current maintainer of the -rt, -realtime, and -lowlatency kernels, is planning to stop maintaining theses packages, and he mentioned [_on the mailing list_]("https://lists.ubuntu.com/archives/ubuntu-studio-users/2010-September/006588.html") he's looking for people able to take over this task.

Lots of great packaging things are happening here, so if that sounds exciting to you, by all means come and join the discussion.

Good day.

---

### Post by AutoStatic on 2010-09-29
That's bad news! I simply don't have the knowledge, time and drive to package and test kernels at the moment.

---

### Post by Penguin Studio on 2010-09-29
This topic post is absolutely a wonderful contribution work from you guys, my hat is off to all of you. I wasn't sure as to where to post this reply, because I noticed this forum is mostly about technical support. So, what I am here for is to let everyone know that, first I am a creative musician & promoter of musicians. I also promote and support open source platforms etc. I own the web site Jamacast, where musicians can meet and help each other out. This site is a work in progress of about 4 years now. When I discovered Ubuntu Studio I became impressed with the direction it is going! I just created a new show called "The Penguin Studio" where it will be an impromptu recording of some of the creative thoughts and ideas I have for music and other more fun things too. This show will also get into some technical tips and know how also. I am more focused on the creative side but I am also going to try to recruit other more techy heads to jump in to the show down the road for some quick toots blah blah blah. This is where I thought you guys might come in to play with this little venture. Keep in mind that this show is to be light hearted and for the beginning and struggling musicians out there, and not a gear head thing. If you are interested in helping out with this great because I think this is the kind of insight and image the open source needs to get out to the masses, and not just to be for how to fix issues. Lets show the world how we can be productive and creative with open source and hopefully lead this direction from a Ubuntu Studio point of view as a starting point. Here is the link to that shows starting point. It is a very rough impromptu non polished type of thing that the regular joe musicians can relate to. If this thing grows, some of you here could integrate cams and shows to this program in the future also. [http://www.ustream.tv/recorded/9884489](http://www.ustream.tv/recorded/9884489)
If this is considered spam or not appropriate for this forum , please delete and guide me to a better location for this effort, thanks and Groove On!!!

---

### Post by NightSprinter on 2010-10-06
I don't think this might be the appropriate place, but maybe someone can help me here.  I've installed the realtime kernels (both .31 and .33), the nvidia drivers from falkTX do run.  However, though, either shortly after I log in or before I can input my password my system locks up entirely.  Checking the virtual terminal shows numerous R/W issues on the disks.

What I don't get, is that on every other kernel type these R/W issues do not exist.  Am I doing something wrong for the kernel to cause this?  If anyone needs my system specifications, I'll gladly provide.

---

### Post by jsevi83 on 2010-10-10
I just saw in your bleeding edge repository this package: clementine-svn (0.4.2+svn2092-0~ppa1), compiled three days ago. But version 0.5.3 was released on the 29th of september. You can find it here: [http://code.google.com/p/clementine-player/downloads/list](http://code.google.com/p/clementine-player/downloads/list)

Is there any chance to get gnome-mplayer-svn?

---

### Post by shimoda on 2010-10-10
> **falkTX said:**
> @shimoda:
The kdenlive thumbnails are now fixed (just needed to rebuild mlt against the new ffmpeg 0.6).

There may be other apps with wrong thumbnails/previews, you guys just let me know if you find any. (I can't test them all...)

thanks **falkTX**!!!

One question... I'm starting to use Ardour 3 and seems to work very well! I read in its forums that for use VST is needed a special compiled version... Your version support VST?


EDIT: Sorry, I now see in synaptic the package Ardour VST! :) I also see that is a 32bit version... It has problems in 64bit systems?

---

### Post by falkTX on 2010-10-11
> **shimoda said:**
> thanks **falkTX**!!!

One question... I'm starting to use Ardour 3 and seems to work very well! I read in its forums that for use VST is needed a special compiled version... Your version support VST?


EDIT: Sorry, I now see in synaptic the package Ardour VST! :) I also see that is a 32bit version... It has problems in 64bit systems?

ArdourVST uses code from fst, and also uses Wine.
In order to load Windows 32bit plugins, it must be 32bit...
(there are not many 64bit VSTs out there)

And in Ubuntu, Wine is only available as 32bit


But, it works in 64bit systems just as it do in 32bit (you just need to get lots of lib32* packages).

---

### Post by falkTX on 2010-10-11
> **jsevi83 said:**
> I just saw in your bleeding edge repository this package: clementine-svn (0.4.2+svn2092-0~ppa1), compiled three days ago. But version 0.5.3 was released on the 29th of september. You can find it here: [http://code.google.com/p/clementine-player/downloads/list](http://code.google.com/p/clementine-player/downloads/list)

Is there any chance to get gnome-mplayer-svn?


I had my laptop broke, but now fixed again.

just give me some time...
*(I will package gnome-mplayer-svn, it's in my 'TODO' list)*

---

### Post by NightSprinter on 2010-10-11
falkTX, I attempted to compile VST support into the SVN version of Ardour3.  Problem is not only does scons fail, but atempting to configure VST support in complains that it won't build on a 64-bit system and tells me to compile for a 32-bit host instead.  Have you worked around that yet?

---

### Post by falkTX on 2010-10-12
> **NightSprinter said:**
> falkTX, I attempted to compile VST support into the SVN version of Ardour3.  Problem is not only does scons fail, but atempting to configure VST support in complains that it won't build on a 64-bit system and tells me to compile for a 32-bit host instead.  Have you worked around that yet?

Hehe, you have to build ArdourVST in a 32bit machine (or using a chroot), then copy/use the binaries in a 64bit OS.


Here's how it works for my package:
1 - package 'ardourvst' is compiled as 32bit only;
2 - package 'ardourvst-32bit' is made as 64bit only (as fake, it has no contents whatsoever). BUT, when you install it, it will download the 32bit deb and extract it to somewhere safe (/opt/ardourvst), and make a start script (/usr/bin/ardourvst) to easily start the app

'/usr/bin/ardourvst' contains:
```
#!/bin/bash

export LD_LIBRARY_PATH=/opt/ardourvst/lib/:$LD_LIBRARY_PATH
exec /opt/ardourvst/bin/ardourvst "$@"
```

---

### Post by jsevi83 on 2010-10-15
Just to let you know, gnome-mplayer-0.9.99.rc3 was released three days ago, and the final version 1.0 will hopefully be released next week, so maybe it's better to wait a bit longer to compile that.

---

### Post by AutoStatic on 2010-10-15
Uploaded [zita-resampler]("http://www.kokkinizita.net/linuxaudio/zita-resampler/resampler.html"), [zita-at1]("http://www.kokkinizita.net/linuxaudio/zita-at1-doc/quickguide.html") and [zita-rev1]("http://www.kokkinizita.net/linuxaudio/zita-rev1-doc/quickguide.html") to my PPA. Also uploaded a patched Hydrogen 0.9.5 RC1 with the SELECT_NEXT_PATTERN action enabled.

Best,

Jeremy

---

### Post by falkTX on 2010-10-15
hi AutoStatic,

I've been very busy lately preparing the new KXStudio update.
You don't mind me copying some of those packages, do you? *(btw, nice job!)*


Do you know anything about Natty PPA?
We should start a team and make some decisions ASAP

---

### Post by AutoStatic on 2010-10-15
> **falkTX said:**
> You don't mind me copying some of those packages, do you? *(btw, nice job!)*Thanks! And no problem, feel free to copy what you need.

> **falkTX said:**
> Do you know anything about Natty PPA?
We should start a team and make some decisions ASAPI've subscribed to both Ubuntu Studio mailinglists (devel and user) recently and I'll ask over there. Haven't been on IRC lately, much too distracting, way too much babbling folks who know s**t that I have to reply somehow, this urge is just too strong sometimes ;)
I'm very much in favor of joining forces, I really like the idea of an official Ubuntu Studio PPA.

---

### Post by shimoda on 2010-10-15
> **falkTX said:**
> ArdourVST uses code from fst, and also uses Wine.
In order to load Windows 32bit plugins, it must be 32bit...
(there are not many 64bit VSTs out there)

And in Ubuntu, Wine is only available as 32bit


But, it works in 64bit systems just as it do in 32bit (you just need to get lots of lib32* packages).

thanks for all your info!! Very clear! :)

One more thing, I installed the wineasio .deb from here:
[http://ubuntuforums.org/showthread.php?t=1241187](http://ubuntuforums.org/showthread.php?t=1241187)
And it worked well (for example in Reaper).

Now if I upgrade with wineasio 0.81 from your repos, seems to break things because in Reaper config appear Wineasio driver but without INs & OUTs, and is not usable... I've to reinstall the 0.74 deb...

I'm doing something wrong? I need to tweak something to make your 0.81 work?

thanks!!

---

### Post by falkTX on 2010-10-15
> **shimoda said:**
> thanks for all your info!! Very clear! :)

One more thing, I installed the wineasio .deb from here:
[http://ubuntuforums.org/showthread.php?t=1241187](http://ubuntuforums.org/showthread.php?t=1241187)
And it worked well (for example in Reaper).

Now if I upgrade with wineasio 0.81 from your repos, seems to break things because in Reaper config appear Wineasio driver but without INs & OUTs, and is not usable... I've to reinstall the 0.74 deb...

I'm doing something wrong? I need to tweak something to make your 0.81 work?

thanks!!

Hm... I'm not sure.

But if v0.74 works for you, just stick with that.
I'll test Reaper soon

There's also a new wineasio version coming out with jack-transport -> asio-timecode support, but that is for later...

---

### Post by jsevi83 on 2010-10-16
Clementine music player has official ppa repositories:

Stable releases  >  ppa:me-davidsansome/clementine

Development releases  >  ppa:me-davidsansome/clementine-dev

---

### Post by ztomic on 2010-10-16
wineasio 0.8.1 doesn't work for me.

```
#regsrv32 wineasio.dll
#Failed to load DLL wineasio.dll
```
I went back to previous version.

---

### Post by falkTX on 2010-10-17
> **jsevi83 said:**
> Clementine music player has official ppa repositories:

Stable releases  >  ppa:me-davidsansome/clementine

Development releases  >  ppa:me-davidsansome/clementine-dev

I dont like to have many PPAs installed,
so usually I just get everything I need into my PPAs.

I will update clementine soon, with projectm v2.0.1 now

---

### Post by falkTX on 2010-10-17
> **ztomic said:**
> wineasio 0.8.1 doesn't work for me.

```
#regsrv32 wineasio.dll
#Failed to load DLL wineasio.dll
```
I went back to previous version.

hm, I need to fix this asap.

Are you using 32 or 64bit?
Which deb did you use to install wineasio?

oh, and are you using wine1.2 or wine1.3?

---

### Post by shimoda on 2010-10-17
> **falkTX said:**
> Hm... I'm not sure.

But if v0.74 works for you, just stick with that.
I'll test Reaper soon

There's also a new wineasio version coming out with jack-transport -> asio-timecode support, but that is for later...

Wow that's really good news!

---

### Post by ztomic on 2010-10-17
> **falkTX said:**
> hm, I need to fix this asap.

Are you using 32 or 64bit?
Which deb did you use to install wineasio?

oh, and are you using wine1.2 or wine1.3?
64bit from your ppa with wine1.3 from ubuntu-wine ppa.

<Edit>
I updated Wine1.3 today and tried again. Still no luck.

---

### Post by shimoda on 2010-10-30
Hi!
I've a crash every time I try to stretch an audio file with Ardour 3... In terminal the error is:

```
glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: failed constructor

aborting...
RubberBandStretcher::~RubberBandStretcher: joining (channel 0x7fab2407d920)
Aborted

```

No probs with Ardour 2... 
I look in A3 bug reports and it not seems a known bug... Maybe some prob with the deb? Anyone can confirm this?

---

### Post by Pablo_F on 2010-10-30
ardour3 is changing every single day. At this moment it is not even in alpha stage. 

Cheers! Pablo

---

### Post by prokoudine on 2010-11-01
> **Pablo_F said:**
> ardour3 is changing every single day. At this moment it is not even in alpha stage.
It actually is at alpha stage and rapidly moving towards beta.

---

### Post by shimoda on 2010-11-04
one new question... :P

If I try to update to last version of audacious from falktx, it tries to remove ubuntustudio-audio...

I don't know what exactly does the package ubuntustudio-audio, but not seems a good thing to uninstall it... :confused:

---

### Post by falkTX on 2010-11-06
> **shimoda said:**
> one new question... :P

If I try to update to last version of audacious from falktx, it tries to remove ubuntustudio-audio...

I don't know what exactly does the package ubuntustudio-audio, but not seems a good thing to uninstall it... :confused:

thanks for reporting.

somehow the audacious-plugin package was not uploaded, making audacious uninstallable.

anyway, now fixed.


also fixed ubuntustudio-meta to allow installing wine1.3

---

### Post by falkTX on 2010-11-06
> **shimoda said:**
> Hi!
I've a crash every time I try to stretch an audio file with Ardour 3... In terminal the error is:

```
glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: failed constructor

aborting...
RubberBandStretcher::~RubberBandStretcher: joining (channel 0x7fab2407d920)
Aborted

```

No probs with Ardour 2... 
I look in A3 bug reports and it not seems a known bug... Maybe some prob with the deb? Anyone can confirm this?


I dont have network at home  for the moment, so that's why I didnt updated those svn/git packages as I used to...

But, you can easily build it yourself.
Here's how:

1 - install my scripts
```
sudo add-apt-repository ppa:falk-t-j/kxstudio
sudo apt-get update
sudo apt-get install kxstudio-scripts

```

2 - enable sources from the lucid-latest PPA:
```
sudo su root -c "echo 'deb http://ppa.launchpad.net/falk-t-j/lucid-latest/ubuntu lucid main
deb-src http://ppa.launchpad.net/falk-t-j/lucid-latest/ubuntu lucid main' > /etc/apt/sources.list.d/falk-t-j-lucid-latest-lucid.list"
sudo apt-get update
```

3 - get the sources of the packages you want to update:
```
#cd /some/path/to/a/folder
sudo apt-get build-dep ardour30 #or others, like blender25, qtractor-svn, etc
apt-get source ardour30
update-svn-deb
update-git-deb
```
Ignore the errors (if any) on the 'update-*-deb' process, and you should have pre-compiled debs of the latest checkout of those apps

Enjoy!

---

### Post by shimoda on 2010-11-07
> **falkTX said:**
> thanks for reporting.

somehow the audacious-plugin package was not uploaded, making audacious uninstallable.

anyway, now fixed.


also fixed ubuntustudio-meta to allow installing wine1.3

thanks for all your info!
No more dependencies probs!

I tried Wineasio again, this time with your wine (I use Reaper). Now seems to work, but when I go to "Preferences", Reaper freezes...
BUT, with "wineasio-beta" works well! 

What's exactly wineasio-beta? (wineasio 0.9?) 

PD: I'll try to compile Ardour 3 myself!! thanks!

---

### Post by falkTX on 2010-11-07
> **shimoda said:**
> thanks for all your info!
No more dependencies probs!

I tried Wineasio again, this time with your wine (I use Reaper). Now seems to work, but when I go to "Preferences", Reaper freezes...
BUT, with "wineasio-beta" works well! 

What's exactly wineasio-beta? (wineasio 0.9?) 

PD: I'll try to compile Ardour 3 myself!! thanks!

wineasio-beta is a branch from the original wineasio code,
hosted here:
[http://repo.or.cz/w/wineasio.git/](http://repo.or.cz/w/wineasio.git/)

it includes:
windows registry to change settings (besides environment variables)
ASIO timecode support, sync a host to jack-transport

---

### Post by vervelover on 2010-11-08
Hi falkTX,

I just wanted to ask a couple of things. This is one: is the Ardour in your repos any different from the one I build my self from source? Does that "withladish" mean that you built it with some specific adjustments for Ladish? Will it, for instance, autosave sessions on studio unloading?

Also, the Ardourvst package in your repo doesn't say "withladish", is it intentional? And is Ardour2 or Ardourvst a Level 1 compatible app?

One more question: it looks like vsts loaded in ladish with festige only autosave their state randomly on studio unloading. When I load the studio again, sometimes their last state is autoloaded, and sometimes not..

Thanks, you rock! :guitar:

---

### Post by falkTX on 2010-11-08
> **vervelover said:**
> Hi falkTX,

I just wanted to ask a couple of things. This is one: is the Ardour in your repos any different from the one I build my self from source? Does that "withladish" mean that you built it with some specific adjustments for Ladish? Will it, for instance, autosave sessions on studio unloading?

Also, the Ardourvst package in your repo doesn't say "withladish", is it intentional? And is Ardour2 or Ardourvst a Level 1 compatible app?

One more question: it looks like vsts loaded in ladish with festige only autosave their state randomly on studio unloading. When I load the studio again, sometimes their last state is autoloaded, and sometimes not..

Thanks, you rock! :guitar:

1. The Ardour package contains this patch:
[http://tracker.ardour.org/view.php?id=2990&nbn=3](http://tracker.ardour.org/view.php?id=2990&nbn=3)
It makes ardour auto-save on SIGUSR1 signal (ladish lv1 implementation)

2. the ardourvst also includes this patch

3. see the help->usage menu in festige.
you have to set a project folder to use festige properly in ladish.
also make sure you use the "fst" utility and ladish level is set to 1.
you should run festige like this: *(room name is optional)*
```
festige /path/to/ladish/project/folder [room-name]
```

---

### Post by jsevi83 on 2010-11-10
Gnome-mplayer 1.0.0 was released last week and it's already available in a ppa. So no need to care about that anymore. Thanks anyway

---

### Post by falkTX on 2010-11-10
> **jsevi83 said:**
> Gnome-mplayer 1.0.0 was released last week and it's already available in a ppa. So no need to care about that anymore. Thanks anyway

sorry, i've been really busy lately...

I really need to get internet at home,
but it's not easy when you work 3 months without being paid... :(

*(stupid Zon TVCabo!)*

---

### Post by vervelover on 2010-11-14
Hi,

I just realized that it's become mandatory to update wine to 1.3 in order to update festige and dssi-vst, but why? With VSTs you never know if they will keep working after you update wine, so I would prefer to stick with wine 1.2 for a long time, but still be able to update festige and dssi-vst..

---

### Post by sgx on 2010-11-14
Hi, just rename the .wine folder to Oldwine or what you like before installing a new wine, then copy the Steinberg/VstPlugins folders back to the new .wine folder.

I also have synaptic preferences save files in the cache, so I can backup
important .deb files in case a new one breaks something, and reinstall the working version manually   dpkg -i winexxx.deb  and any dependencies.
Cheers

---

### Post by SleepWalkerX on 2010-11-14
Thank you for taking time to port this software to the ppas!

---

### Post by falkTX on 2010-11-15
> **vervelover said:**
> Hi,

I just realized that it's become mandatory to update wine to 1.3 in order to update festige and dssi-vst, but why? With VSTs you never know if they will keep working after you update wine, so I would prefer to stick with wine 1.2 for a long time, but still be able to update festige and dssi-vst..

It shouldn't be mandatory, but optional.

I'll check this

---

### Post by barisurum on 2010-11-20
Hi falktx and thank you so much for this beautiful ppa! 

I've a problem with festige. Its fine with VSTi instruments but effects won't work. Is there a particular reason for this? or is there a different way to host the effects other than festige or ardourvst? My box is 64bit and ardourvst while being fine with vst effects, fails with ladspa and lv2 plugins. Ladspa plugins are nowhere to be found and lv2 have gui problems. No vst ardour plays fine with them. And one last question: where can I host the native linux vsts?

Thanks to everyone for their work in this ppa!

---

### Post by vervelover on 2010-11-21
@ FalkTX

Thanks for your efforts! 

One more issue here: when using kernel 2.6.32-24-lowlatency-pae from your repo, the fglrx driver with rt patch from your repo doesn't install, it gives me this error:

```
Error! Application of patch rt_preempt_33.patch failed
```

I only have that kernel installed, no other, but it gives me the same error also with 2.6.33 rt-pae from your repo.

I had to install the new 10.11 driver, but I have a huge issue with it, it crashes X everytime a play a video.

EDIT: I managed to make the 10.11 driver work by building the packages myself, now video playback is fine.

EDIT2: I realized that maybe I have to install jockey-gtk from your ppa, but I won't test this 'cause now everything is working..

---

### Post by falkTX on 2010-11-22
> **barisurum said:**
> Hi falktx and thank you so much for this beautiful ppa! 

I've a problem with festige. Its fine with VSTi instruments but effects won't work. Is there a particular reason for this? or is there a different way to host the effects other than festige or ardourvst? My box is 64bit and ardourvst while being fine with vst effects, fails with ladspa and lv2 plugins. Ladspa plugins are nowhere to be found and lv2 have gui problems. No vst ardour plays fine with them. And one last question: where can I host the native linux vsts?

Thanks to everyone for their work in this ppa!


Try using "dssi-vst" option instead of default "fst". Some VSTs dont work with fst but work on dssi-vst or vice-versa. just try both ways.

ArdourVST, even in a 64bit machine, is a 32bit app.
KXStudio has the paths auto-set for this, but in regular Ubuntu, you need to run:
```
export LADSPA_PATH=/usr/lib32/ladspa
export LV2_PATH=/usr/lib32/lv2
ardourvst
```
Make sure you have installed 'ladpsa-32bit' and 'lv2-32bit' packages.

For native linux VSTs, install the packages "vst-plugin-...".
(the hosts that support native vsts are qtractor, jost (32bit only), energyxt (32bit only) and renoise

---

### Post by falkTX on 2010-11-22
> **vervelover said:**
> @ FalkTX

Thanks for your efforts! 

One more issue here: when using kernel 2.6.32-24-lowlatency-pae from your repo, the fglrx driver with rt patch from your repo doesn't install, it gives me this error:

```
Error! Application of patch rt_preempt_33.patch failed
```

I only have that kernel installed, no other, but it gives me the same error also with 2.6.33 rt-pae from your repo.

I had to install the new 10.11 driver, but I have a huge issue with it, it crashes X everytime a play a video.

EDIT: I managed to make the 10.11 driver work by building the packages myself, now video playback is fine.

EDIT2: I realized that maybe I have to install jockey-gtk from your ppa, but I won't test this 'cause now everything is working..


Seems like I need to update the patch...

I'll look around.
Anyone has a link ?

---

### Post by sotdan on 2010-11-22
> **falkTX said:**
> Seems like I need to update the patch...

I'll look around.
Anyone has a link ?

 I have the same problem. I now installed the 2.6.33-29-realtime kernel and I'm still getting the error when trying to install the fglrx driver. I couldn't figure out how to install the new driver or just one without the rt patch.  Awesome PPA btw    

EDIT: After a lot of messing around I've removed all kernels except 2.6.32-26-preempt and completely removed fglrx and installed the new one from ATI's website it by building the packages myself. It works perfeclty. 

I might try to get it to work with a rt kernel another time.

---

### Post by marcoharder on 2010-11-25
Hi guys! Sorry for being a noob, but I've read somewhere that there is no realtime / rt / lowlatency kernel for 10.10 as Alessandro has gone on indefinite hiatus from the project. What I am getting from the recent posts that new developments here are present, and would like to confirm if any of the three kernels are now available, and if so where do I get them?

---

### Post by Gabriel Goujon on 2010-11-26
Hi all.
 
Yasterday installed KXStudio 64 bits, never used KDE, just Ubuntu Studio with to much problems unsolved about latency & configurations. KXStudio looks cool & appears to be easygoing, almost plug & play, with too much apps (like LV2Vocoder which I´ve tried to install before with no sucess, so I decided to give a try & stay forever with it once for all.
 
I´m Afraid, sorry, just a Guitar player who wants to make sounds with GNU/Linux without to much knowledge or experience in precisions like progaming, shell, configuration, KDE, etc. I´ve lost too much time trying to get good performance in this new CPU with US 10.10 & 10.04:
 
- Phenom II x2 a 3.1 GB
- 2 DDR3 2 GB each one, total 4 GB
- 1 Solid State disk up to 32 GB where are : / 20 GB, Home 10 GB & Swap 898 MB (the rest)
- 1 old ide Disk, 120 GB wich is in /home/Almacenamiento (for my Files) (all with ext4 format)
- Echo Audio Gina 24/96 PCI soundcard
 
I live in México, so I hope You understand my bad English. I´ll be grateful when you help me if I get in trouble. For example: Yasterday installed all the packages in the welcome & configuration Wizard, included the 2 Kernels provided. My question is: it was correct or with my hardware described I must install 1 of them?, Which one will be better?.
 
Thanks for all your effort, work, help and everything.
 
Cheers.

---

### Post by falkTX on 2010-11-27
> **Gabriel Goujon said:**
> Hi all.
 
Yasterday installed KXStudio 64 bits, never used KDE, just Ubuntu Studio with to much problems unsolved about latency & configurations. KXStudio looks cool & appears to be easygoing, almost plug & play, with too much apps (like LV2Vocoder which I´ve tried to install before with no sucess, so I decided to give a try & stay forever with it once for all.
 
I´m Afraid, sorry, just a Guitar player who wants to make sounds with GNU/Linux without to much knowledge or experience in precisions like progaming, shell, configuration, KDE, etc. I´ve lost too much time trying to get good performance in this new CPU with US 10.10 & 10.04:
 
- Phenom II x2 a 3.1 GB
- 2 DDR3 2 GB each one, total 4 GB
- 1 Solid State disk up to 32 GB where are : / 20 GB, Home 10 GB & Swap 898 MB (the rest)
- 1 old ide Disk, 120 GB wich is in /home/Almacenamiento (for my Files) (all with ext4 format)
- Echo Audio Gina 24/96 PCI soundcard
 
I live in México, so I hope You understand my bad English. I´ll be grateful when you help me if I get in trouble. For example: Yasterday installed all the packages in the welcome & configuration Wizard, included the 2 Kernels provided. My question is: it was correct or with my hardware described I must install 1 of them?, Which one will be better?.
 
Thanks for all your effort, work, help and everything.
 
Cheers.


First of all, thanks for trying KXStudio!
You should use the new Beta though (or wait a few days before the final 10.04.3 release)
The new version has some performance tweaks...

The kernel you use depends on what you do with your PC. The realtime kernel should be good for you (v2.6.33), just make sure you boot from it (hold 'Shift' key after you see the PC BIOS splash, then select the realtime kernel).

You should try to avoid the ext4 format though, it is known to be slow on 2.6.29-2.6.33 kernels. ext3 is good enough for now.

---

### Post by JackSchnippes on 2010-11-28
Hi FalkTX,

First of all, thank you for your work and of course all others involved in kxstudio! I really like having all those up-to-date packages... :D:D:D

I have a problem with wine1.3 version 1.3.6-0ubuntu1+rt1. I can't even run winecfg, because I always get this error:
```
$ winecfg
wine: virtual memory exhausted
$ wine --version
wine-1.3.6
```I removed wine completely and the .wine folder an reinstalled, but this didn't resolve the issue. I use regular lucid ubuntu 64bit with your repos, also kxstudio realtime kernel:
```
$ $ uname -a
Linux 2.6.33-29-realtime #1-Ubuntu SMP PREEMPT RT Wed Aug 4 17:22:37 UTC 2010 x86_64 GNU/Linux
```Thanks for any hints/tips! :KS


EDIT:
maybe it's a problem with my realtime priority settings?
```
$ ulimit -r
0
```
EDIT 2:
aaahhh! I wuz not a membah of teh audio group :) Fixed! Wine works again!

---

### Post by falkTX on 2010-11-29
> **JackSchnippes said:**
> Hi FalkTX,

First of all, thank you for your work and of course all others involved in kxstudio! I really like having all those up-to-date packages... :D:D:D

I have a problem with wine1.3 version 1.3.6-0ubuntu1+rt1. I can't even run winecfg, because I always get this error:
```
$ winecfg
wine: virtual memory exhausted
$ wine --version
wine-1.3.6
```I removed wine completely and the .wine folder an reinstalled, but this didn't resolve the issue. I use regular lucid ubuntu 64bit with your repos, also kxstudio realtime kernel:
```
$ $ uname -a
Linux 2.6.33-29-realtime #1-Ubuntu SMP PREEMPT RT Wed Aug 4 17:22:37 UTC 2010 x86_64 GNU/Linux
```Thanks for any hints/tips! :KS


EDIT:
maybe it's a problem with my realtime priority settings?
```
$ ulimit -r
0
```
EDIT 2:
aaahhh! I wuz not a membah of teh audio group :) Fixed! Wine works again!

hm... I got the same issues some days ago while testing a live-dvd ISO.

anyway, a new wine version is out, so I'll update it just in case

---

### Post by marcoharder on 2010-11-29
Would KXStudio have all the wireless drivers from the get-go?

---

### Post by falkTX on 2010-11-30
> **marcoharder said:**
> Would KXStudio have all the wireless drivers from the get-go?

hm... which drivers do you need?
I'll enable lucid-backports (alsa and wwlan), but if you're talking about restricted stuff (like nvidia, ati, broadcom, etc) I can't.

---

### Post by sawtdk on 2010-11-30
Hey falkTX :)

Just wanted to say thanks for plugins from TAL you upload. 
They are fantastic plugins.
Great work!

---

### Post by Gabriel Goujon on 2010-11-30
I thought it was going to be easy but not.

1.- I tried to install 10.04.3 beta from sourceforge, everything suppossed to be right until I tried to boot from hard disk. The screen stays with the logo. So reinstalled 10.04.2.

2.- On this new try, made ext3 for the partitions & just installed kernel 2.6.33-29-realtime (like FalkTX suggested me before), then got into the configuration wizard and followed the configure KXStudio part 3 tutorial from the oficial page, assured to do everything.

Next I assured  pulse-jack workaround worked, it was. 

Then tried this: kxstudio-session-start --config, which opened laidconf, made some configurations for my Echo Audio Gina 24/96 pci audio card and now is worse, recived message about to forget something from pulseaudio twice, first denied, second accepted. I'm getting [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] & [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]. I can't conect my Alesis QS6.1 trough the audio card, not even in the Audio connections from QJackctl.

Can you help me to correct things and make my sound card work?. I don't know what to do, feel lost & fool because ignore to much things. I just want to record some music in GNU-Linux (I really love it) since 2-3 months ago, but I've couldn't yet.

Thanks.

[B]     
[/B]

      [B]
[/B]

---

### Post by marcoharder on 2010-12-01
> **falkTX said:**
> hm... which drivers do you need?
I'll enable lucid-backports (alsa and wwlan), but if you're talking about restricted stuff (like nvidia, ati, broadcom, etc) I can't.

Here are my two wireless cards:

Realtek 8188SU USB b/g/n card
Ralink 2800 [or something; I remember having to put 'blacklist rtusb2800' in modprobe.d to get it working]

Thanks!

---

### Post by Selim873 on 2010-12-01
I was considering switching from the normal Ubuntu 10.10 release to Studio Edition for musical purposes.  Thanks!

---

### Post by falkTX on 2010-12-01
> **sawtdk said:**
> Hey falkTX :)

Just wanted to say thanks for plugins from TAL you upload. 
They are fantastic plugins.
Great work!

he, thanks.

I've updated the pack (added a few more plugins), link:
[http://sourceforge.net/projects/kxstudio/files/VST/tal-plugins_0.2.tar.gz/download](http://sourceforge.net/projects/kxstudio/files/VST/tal-plugins_0.2.tar.gz/download)

I mailed the devs, so they posted on their website about this too. ([http://kunz.corrupt.ch/](http://kunz.corrupt.ch/))

Cool stuff

---

### Post by falkTX on 2010-12-01
> **Gabriel Goujon said:**
> I thought it was going to be easy but not.

1.- I tried to install 10.04.3 beta from sourceforge, everything suppossed to be right until I tried to boot from hard disk. The screen stays with the logo. So reinstalled 10.04.2.

2.- On this new try, made ext3 for the partitions & just installed kernel 2.6.33-29-realtime (like FalkTX suggested me before), then got into the configuration wizard and followed the configure KXStudio part 3 tutorial from the oficial page, assured to do everything.

Next I assured  pulse-jack workaround worked, it was. 

Then tried this: kxstudio-session-start --config, which opened laidconf, made some configurations for my Echo Audio Gina 24/96 pci audio card and now is worse, recived message about to forget something from pulseaudio twice, first denied, second accepted. I'm getting [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] & [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]. I can't conect my Alesis QS6.1 trough the audio card, not even in the Audio connections from QJackctl.

Can you help me to correct things and make my sound card work?. I don't know what to do, feel lost & fool because ignore to much things. I just want to record some music in GNU-Linux (I really love it) since 2-3 months ago, but I've couldn't yet.

Thanks.

[B]     
[/B]

      [B]
[/B]

Try using "Jack2 Simple Config" instead ('j2sc' for short). I coded it, and it has a simple GUI.
Just make sure you use jackdbus and not jackd (j2sc doesnt support jackd).

You should come in IRC, #kxstudio channel, so we can talk in real-time.
I'm not always online though, so you need to be a little patient

---

### Post by Gabriel Goujon on 2010-12-01
Thanks FalkTX.

I did what suggested me (what I could understand), now is working[IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG]. Think it was when actualized jack2 apps in Synaptic, then got in the jack2sc, next run qjackctl, made the conections through Audio and magic was done, finally sound my Alesis QS6.1 directly to my card & SynAddSubFX alone with my sinth conected trough Midisport in Alsa tab. I'm happy.

Now I want to make some experiments with LV2Vocoder (where can I find it?), AMS (Alsa Modular Synth) and my voice before recording in Ardour for a song I had. How can I start only with AMS and LV2Vocoder?.

Another thing I learned today was getting in IRC #KXStudio channel with Konversation for the first time and just did an experiment to chat, it was awesome!. Never did it before & ignored about this modes to help us.

Thanks & Cheers, Finally fun begins!.

---

### Post by rusk911 on 2010-12-02
Can somebody help me to get ladish, ardourvst, hydrogen and festige working together?

I have a laptop with maverick. If I install ubuntustudio package - I can compile ardourvst. It works fine.
If I install newer jack from kxstudio ppa - I can get Ladish, festige,  but ardourvst do not work neither from repo nor compiled manually... And  all needed packages from ubuntustudio requires jack from oficial repo. I  can compile hydrogen, but cant get working ardourvst, it works only  with jack from ubuntustudio, and not works with ladish...

When I start ardurvst with jack 1.9.6 or with jackdbus within gladish it  stops with this fail whatever wine version used (1.2 and 1.3 tested):

Cannot mmap shm segment /jack-1000-0
 Map shared memory segments exception -2
 wine: Unhandled page fault on read access to 0x00000003 at address 0x7099f54c (thread 0026), starting debugger...
 Unhandled exception: page fault on read access to 0x00000003 in 32-bit code (0x7099f54c).
 Register dump:
  CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
  EIP:7099f54c ESP:0032fb70 EBP:0032fb98 EFLAGS:00010202(  R- --  I   - - - )
  EAX:ffffffff EBX:709b5ff4 ECX:000003f4 EDX:709b5ff4
  ESI:00000040 EDI:7ac10008
 Stack dump:
 0x0032fb70:  709ab288 00000000 00000000 29ab2200
 0x0032fb80:  0000000f 414a0000 7099f44b 709b5ff4
 0x0032fb90:  7ac10028 00000000 0032fc78 7099ea7c
 0x0032fba0:  7b54c510 709a4793 68a30165 00000001
 0x0032fbb0:  0032fccc 7e019c6c 7e019bb4 7e019afc
 0x0032fbc0:  7e019a44 7e01998c 7e0198f4 7e01988c
 Backtrace:
 =>0 0x7099f54c in libjack.so.0 (+0x2c54c) (0x0032fb98)
   1 0x7099ea7c in libjack.so.0 (+0x2ba7b) (0x0032fc78)
   2 0x7099eb85 jack_client_open+0x54() in libjack.so.0 (0x0032fca8)
   3 0x6882a01d _ZN13EngineControl14engine_runningEv+0x2c() in libardourgtk.so (0x0032fca8)
   4 0x6882a01d _ZN13EngineControl14engine_runningEv+0x2c() in libardourgtk.so (0x0032fca8)
   5 0x68666618 _ZN9ARDOUR_UI7startupEv+0x47() in libardourgtk.so (0x7dda7db0)
   6 0x686768cc  _ZN4sigc8internal10slot_call0INS_18bound_mem_functor0Iv9ARDOUR_UIEEvE7call_itEPNS0_8slot_repE+0x1b()  in libardourgtk.so (0x7dda7db0)
   7 0x79d54ba2 _ZN9Gtkmm2ext2UI3runER8Receiver+0x101() in libgtkmm2ext.so (0x0032fe34)
   8 0x688bd0c0 ardour_main+0x53f() in libardourgtk.so (0x0032fe50)
   9 0x68317947 main+0x26() in ardour_vst (0x0032fe90)
   10 0x7b8560ac call_process_entry+0xb() in kernel32 (0x0032fea8)
   11 0x7b8560ac call_process_entry+0xb() in kernel32 (0x0032fee8)
   12 0x7b856d4f start_process+0x5e(peb=0x7ffdf000)  [/build/buildd/wine1.3-1.3.8/dlls/kernel32/process.c:997] in kernel32  (0x0032fef8)
   13 0x7bc71990 call_thread_func+0xb() in ntdll (0x0032ffc8)
   14 0x7bc74530 call_thread_entry_point+0x6f(entry=0x7b856cf0,  arg=0x7ffdf000)  [/build/buildd/wine1.3-1.3.8/dlls/ntdll/signal_i386.c:2473] in ntdll  (0x0032ffe8)
   15 0x7bc49daa start_process+0x29(kernel_start=0x7b856cf0)  [/build/buildd/wine1.3-1.3.8/dlls/ntdll/loader.c:2610] in ntdll  (0x00000000)
 0x7099f54c: movl    0x4(%eax),%edx

---

### Post by falkTX on 2010-12-02
> **Gabriel Goujon said:**
> Thanks FalkTX.

I did what suggested me (what I could understand), now is working[IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG]. Think it was when actualized jack2 apps in Synaptic, then got in the jack2sc, next run qjackctl, made the conections through Audio and magic was done, finally sound my Alesis QS6.1 directly to my card & SynAddSubFX alone with my sinth conected trough Midisport in Alsa tab. I'm happy.

Now I want to make some experiments with LV2Vocoder (where can I find it?), AMS (Alsa Modular Synth) and my voice before recording in Ardour for a song I had. How can I start only with AMS and LV2Vocoder?.

Another thing I learned today was getting in IRC #KXStudio channel with Konversation for the first time and just did an experiment to chat, it was awesome!. Never did it before & ignored about this modes to help us.

Thanks & Cheers, Finally fun begins!.

For the vocoder, make sure it's installed first (open a package manager and search for 'vocoder'. I use "Muon")
Then you can use "LV2Rack" and start the vocoder.

I'll make some tutorial videos soon...

*PS: I love IRC too!*

---

### Post by falkTX on 2010-12-02
> **rusk911 said:**
> Can somebody help me to get ladish, ardourvst, hydrogen and festige working together?

I have a laptop with maverick. If I install ubuntustudio package - I can compile ardourvst. It works fine.
If I install newer jack from kxstudio ppa - I can get Ladish, festige,  but ardourvst do not work neither from repo nor compiled manually... And  all needed packages from ubuntustudio requires jack from oficial repo. I  can compile hydrogen, but cant get working ardourvst, it works only  with jack from ubuntustudio, and not works with ladish...

When I start ardurvst with jack 1.9.6 or with jackdbus within gladish it  stops with this fail whatever wine version used (1.2 and 1.3 tested):

Cannot mmap shm segment /jack-1000-0
 Map shared memory segments exception -2
 wine: Unhandled page fault on read access to 0x00000003 at address 0x7099f54c (thread 0026), starting debugger...
 Unhandled exception: page fault on read access to 0x00000003 in 32-bit code (0x7099f54c).
 Register dump:
...

This happened for me as well, and I think it's related to Jack2...
It works on 64bit though...

You can try using the "jack1-opt" package in my ppa (installs a copy of jack1 in /opt/), then stop jack and run:
```
jack1 jackd ...(options)
jack1 ardourvst
```

in this mode you'll need to start all apps with "jack1 <app>" prefix, so they can use the jack1 server instead of jack2.

I think maverick has both jack versions...? (never tested it), so you may want to just try compiling it against jack1 first

---

### Post by shimoda on 2010-12-02
Hi!

I've a doubt!

Since the first day, sometimes (maybe a lot of times) I hear clicks when playing sound (but not Xruns in jack), and I don't know what can be wrong...

I use qjackctl and pulse-jack... Works, but in messages window of qjack control appears:
```
[B]Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started[/B]
21:18:39.997 ALSA connection graph change.
21:18:40.031 JACK was started with PID=2134.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0,0|hw:0,0|256|2|44100|0|0|nomon|swmeter|soft-mode|16bit
Using ALSA driver ICE1712 running on card 0 - M Audio Delta 44 at 0xdf00, irq 18
etc
```

Is normal?
If I look at system messages log, there's:
```
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >JackSocketClientChannel read fail<
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >Cannot write socket fd = 19 err = Broken pipe<
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >Cannot write socket fd = 19 err = Broken pipe<
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >Could not read result type = 7<
Nov 27 09:58:01 studio pulseaudio[2195]: module-always-sink.c: Unable to load module-null-sink
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >Cannot write socket fd = 28 err = Broken pipe<
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >Cannot write socket fd = 28 err = Broken pipe<
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >Could not read result type = 7<
Nov 27 09:58:17 studio kernel: Kernel logging (proc) stopped.
Nov 27 09:58:49 studio pulseaudio[1840]: lock-autospawn.c: Cannot access autospawn lock.
Nov 27 09:58:53 studio pulseaudio[2286]: module-jack-sink.c: JACK error >Cannot use real-time scheduling (RR/5)(1: Operation not permitted)<
Nov 27 09:58:53 studio pulseaudio[2286]: module-jack-sink.c: JACK error >AcquireRealTime error<
```

I don't know if all of this is normal!
One other thing I consider strange is that I CAN start qjackctl in RT mode using a RT Kernel, but ALSO with a Generic Kernel...

Must I be worried with all those things?
Can the "clicks" when playing come from this errors?

thanks!

---

### Post by rusk911 on 2010-12-02
Thank you [falkTX]("http://ubuntuforums.org/member.php?u=423496") for reply!

Yes, maverick have both jacks in repo. But I'll continue game with compiling apps locally. Ardourvst compiles and runs normally with jackd2 from maverick ppa (jack 1.9.5).

---

### Post by rusk911 on 2010-12-02
I compiled and launched all my needs except ladish. It says that cant find some gdk stuff...

---

### Post by rusk911 on 2010-12-03
I understand the problem. Ardourvst crashes with jackdbus. If jackd started from qjackctl - ardourvst runs fine!

---

### Post by vervelover on 2010-12-15
@FalkTX

Sorry for pointing it out again, but wine 1.3 is still a mandatory dependency for festige and dssi-vst, and I can't update them on my lucid machine without getting rid of wine 1.2, which is something I'd really like to avoid..

Thanks again for your work!

---

### Post by Fardin on 2010-12-15
> **falkTX said:**
> Hi there community!

We decided to help non-geek guys (and girls) that need good software out-of-the-box.
We prepared 3 specials PPAs for audio production (apps, plugins and tools).

For Karmic, use philip5 PPA:
[https://launchpad.net/~philip5/+archive/extra]("https://launchpad.net/%7Ephilip5/+archive/extra")
```
ppa:philip5/extra
```For Lucid, use my PPA:
[https://launchpad.net/~falk-t-j/+archive/lucid/]("https://launchpad.net/%7Efalk-t-j/+archive/lucid/")
```
ppa:falk-t-j/lucid
```For Lucid, bleeding-edge packages: (*)
[https://launchpad.net/~falk-t-j/+archive/lucid-latest/]("https://launchpad.net/%7Efalk-t-j/+archive/lucid-latest/")
```
ppa:falk-t-j/lucid-latest
```

The easiest way to install this PPA is through Synaptic.
Open it in System->Administration->Synaptic

Go to Settings->Repositories.
On the 2nd tab, "Other Software" add the PPA code (one of the displayed before)

Then click on the big "Reload" button.


You can check the web pages for a list of the packages available

I maintain a changelog of my main Lucid PPA:
[http://kxstudio.sourceforge.net/downloads/PPA-Changes](http://kxstudio.sourceforge.net/downloads/PPA-Changes)


Enjoy making music!


*(*) This PPA depends on ppa:falk-t-j/lucid*

Hello

OK I may be one of the most non geek guys, so please bare with my basic questions:

1. How do I know which one (Karmic, Lucid, Lucid bleeding, etc.) applys to my system (xubuntu)?

2. Has the "directions of how to install" changed from the first post? (There have been lots of discussions on this post, any change or improvement has taken place since then?)

Thanks

---

### Post by falkTX on 2010-12-16
> **vervelover said:**
> @FalkTX

Sorry for pointing it out again, but wine 1.3 is still a mandatory dependency for festige and dssi-vst, and I can't update them on my lucid machine without getting rid of wine 1.2, which is something I'd really like to avoid..

Thanks again for your work!

I really though this was fixed already...

Give me some time, I'll fix it soon

---

### Post by AutoStatic on 2010-12-21
falkTX: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-December/074859.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-December/074859.html)

Just FYI but you might consider removing it from your Lucid (Bleeding-Edge) PPA or at least add a warning to it like the Arch guys are doing: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-December/074897.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-December/074897.html)

Edit: or just leave it there: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-December/074941.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-December/074941.html)

Best,

Jeremy

---

### Post by falkTX on 2010-12-22
> **AutoStatic said:**
> falkTX: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-December/074859.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-December/074859.html)

Just FYI but you might consider removing it from your Lucid (Bleeding-Edge) PPA or at least add a warning to it like the Arch guys are doing: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-December/074897.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-December/074897.html)

Edit: or just leave it there: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-December/074941.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-December/074941.html)

Best,

Jeremy

Hey Jeremy
Nice to see you!

Thanks for the tip, I'll update the ardour3 package and add that warning (copy-pasted :) )

---

### Post by binger on 2010-12-24
> **shimoda said:**
> Hi!

I've a doubt!

Since the first day, sometimes (maybe a lot of times) I hear clicks when playing sound (but not Xruns in jack), and I don't know what can be wrong...

I use qjackctl and pulse-jack... Works, but in messages window of qjack control appears:
```
[B]Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started[/B]
21:18:39.997 ALSA connection graph change.
21:18:40.031 JACK was started with PID=2134.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0,0|hw:0,0|256|2|44100|0|0|nomon|swmeter|soft-mode|16bit
Using ALSA driver ICE1712 running on card 0 - M Audio Delta 44 at 0xdf00, irq 18
etc
```

Is normal?
If I look at system messages log, there's:
```
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >JackSocketClientChannel read fail<
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >Cannot write socket fd = 19 err = Broken pipe<
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >Cannot write socket fd = 19 err = Broken pipe<
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >Could not read result type = 7<
Nov 27 09:58:01 studio pulseaudio[2195]: module-always-sink.c: Unable to load module-null-sink
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >Cannot write socket fd = 28 err = Broken pipe<
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >Cannot write socket fd = 28 err = Broken pipe<
Nov 27 09:58:01 studio pulseaudio[2195]: module-jack-source.c: JACK error >Could not read result type = 7<
Nov 27 09:58:17 studio kernel: Kernel logging (proc) stopped.
Nov 27 09:58:49 studio pulseaudio[1840]: lock-autospawn.c: Cannot access autospawn lock.
Nov 27 09:58:53 studio pulseaudio[2286]: module-jack-sink.c: JACK error >Cannot use real-time scheduling (RR/5)(1: Operation not permitted)<
Nov 27 09:58:53 studio pulseaudio[2286]: module-jack-sink.c: JACK error >AcquireRealTime error<
```

I don't know if all of this is normal!
One other thing I consider strange is that I CAN start qjackctl in RT mode using a RT Kernel, but ALSO with a Generic Kernel...

Must I be worried with all those things?
Can the "clicks" when playing come from this errors?

thanks!


I am having the same issue with pulseaudo-module-jack.  Did you find a solution?

---

### Post by vervelover on 2010-12-25
@FalkTX

I just found out that also lmms-vst has a mandatory wine 1.3 dependency..

---

### Post by bikodog on 2010-12-26
Wow, this thread has become huge!

(Maybe this is buried somewhere in the previous posts..but I cannot locate through forum search.)

KX-Studio is fantastic in the fact that everything works great with my hardware (all credit to FalkTX and others!). The only problem is that it uses the KDE desktop (which i despise).

I attempted over the past few days to install KX-Studio and then install a pure-gnome desktop; but it became a mess. Is there anyone out there who has successfully setup a "G"X-studio variant? Are there others interested in this?

---

### Post by AutoStatic on 2010-12-26
Try [Dream Studio]("http://dream.dickmacinnis.com/forum/") or [Tango Studio]("http://tangostudio.tuxfamily.org/en/tangostudio").

---

### Post by falkTX on 2010-12-27
> **bikodog said:**
> Wow, this thread has become huge!

(Maybe this is buried somewhere in the previous posts..but I cannot locate through forum search.)

KX-Studio is fantastic in the fact that everything works great with my hardware (all credit to FalkTX and others!). The only problem is that it uses the KDE desktop (which i despise).

I attempted over the past few days to install KX-Studio and then install a pure-gnome desktop; but it became a mess. Is there anyone out there who has successfully setup a "G"X-studio variant? Are there others interested in this?

I have plans to support Gnome, LXDE and even KDE3, but it may take a while...

But what's about to come *really soon* is a new Team PPA (not just me), that supports all Ubuntu versions since Lucid (ie, Lucid, Maverick and Natty).

I'll let you guys know when it's ready for use.

---

### Post by falkTX on 2010-12-27
> **vervelover said:**
> @FalkTX

I just found out that also lmms-vst has a mandatory wine 1.3 dependency..

Sorry I've been quite busy lately.

I assure you this will get fixed today! ;)

---

### Post by bdlandry on 2010-12-27
Tried Ksxstudio and had to give up on that particular distro for a few reasons, not to criticize as others may have a better experience ... just to let you know one person's experience in case it helps you in your development or someone else with their installation.

1) I don't like the KDE experience (probably because I'm used to gnome, and I run this on my 42" LCD and I am used to configuring the UI to be usable on that sized screen from across the room.)

2) I could run the LiveCD with no problems, but when I installed the distro everything went to heck .. biggest problem was it seemed to lose pulseaudio (I'd get a message that it wasn't found and if I wanted to stop attempting to load it on startup.) Sometimes pulseaudio would start on reboot, but mostly it didn't. Whenever it failed to find pulseaudio I can not start Jack as well.

3) Seemed to hang too often .. if I went away and came back to the computer for a while, it often stopped responding at all.

Finally I decided to just load standard Ubuntu 10.4 and load load the Kxstudio packages from the PPA's.

This seems to work much better for me, although I'm not sure if I have everything configured as it should be, but so far it seems to work for my limited testing.

Here's what I do.

1) Boot up (I configured Gnome to log me in automatically, but  Kxstudio has changed that to prompted me for ID and password ... The first time through I logged in under the default session, KDE, and it complained and hung, so I rebooted and changed to Gnome, which allowed me to log in without issue.

2) When I finish logging in I open a terminal and run "kxstudio-session-start --full-start". After running that command I can run ladish session manager and connect things up through jack, while other apps that run through pulseaudio seem to continue to work as expected.

cheers

---

### Post by falkTX on 2010-12-28
> **bdlandry said:**
> Tried Ksxstudio and had to give up on that particular distro for a few reasons, not to criticize as others may have a better experience ... just to let you know one person's experience in case it helps you in your development or someone else with their installation.

1) I don't like the KDE experience (probably because I'm used to gnome, and I run this on my 42" LCD and I am used to configuring the UI to be usable on that sized screen from across the room.)

2) I could run the LiveCD with no problems, but when I installed the distro everything went to heck .. biggest problem was it seemed to lose pulseaudio (I'd get a message that it wasn't found and if I wanted to stop attempting to load it on startup.) Sometimes pulseaudio would start on reboot, but mostly it didn't. Whenever it failed to find pulseaudio I can not start Jack as well.

3) Seemed to hang too often .. if I went away and came back to the computer for a while, it often stopped responding at all.

Finally I decided to just load standard Ubuntu 10.4 and load load the Kxstudio packages from the PPA's.

This seems to work much better for me, although I'm not sure if I have everything configured as it should be, but so far it seems to work for my limited testing.

Here's what I do.

1) Boot up (I configured Gnome to log me in automatically, but  Kxstudio has changed that to prompted me for ID and password ... The first time through I logged in under the default session, KDE, and it complained and hung, so I rebooted and changed to Gnome, which allowed me to log in without issue.

2) When I finish logging in I open a terminal and run "kxstudio-session-start --full-start". After running that command I can run ladish session manager and connect things up through jack, while other apps that run through pulseaudio seem to continue to work as expected.

cheers

Hi there,
first of all, thanks for being honest.

KDE has a nasty bug that causes the '~/.kde' folder to be create as root on the first login... :(
KXStudio works around this by create that folder for the user, but, if you are on gnome and then install KDE, you'll get that bug...
You can simply remove that folder and create it again as a regular user, then the login issue will be gone.

After install, the 2nd login in KXStudio (after seen the welcome screen setup) is kinda broken, so things will only work properly on the 3rd time...

I understand the Gnome/KDE thing... most users are used to gnome, as it is the default DE in Ubuntu.
I made the change some time ago, after realizing that most the apps I really used were 'K' (k3b, kdenlive, dolphin, yakuake, amarok...)
This is one of the reasons why I'm in the process of rebranding KXStudio, to make it not just KDE... but I still have some work to do before announcing anything.

---

### Post by bdlandry on 2010-12-28
Yeah, I noticed the .kde problem and just changed ownership manually.

I haven't gone too far into the process so I have lots more to do, discover, and learn.

I'll play around a bit more in its current configuration just to familiarize myself with the apps and jack capabilities, but my next step will probably be installing the real time kernel and getting that working.

Looking forward to your next release of Kxstudio (or whatever you will be calling it.) Keep up the excellent work.

---

### Post by bikodog on 2010-12-29
> **falkTX said:**
> I have plans to support Gnome, LXDE and even KDE3, but it may take a while...

But what's about to come *really soon* is a new Team PPA (not just me), that supports all Ubuntu versions since Lucid (ie, Lucid, Maverick and Natty).

I'll let you guys know when it's ready for use.

Great news! Thanks!

---

### Post by ken78724 on 2011-01-01
FalkTX, once kxstudio 10.04.02 lucid runs, why can I walk away and come back to a notice my OS must ? continue in a different mode for that session? During these 10-15 occasions I don't seem to lose anything. Appears if I can recoup my work. But there's a fear or the repeated question, "Will the next crash be fatal?"

Kenneth :guitar:

---

### Post by AutoStatic on 2011-01-01
foo-yc20 is now available in my PPA.

[http://code.google.com/p/foo-yc20/](http://code.google.com/p/foo-yc20/)
[https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa)

Best,

Jeremy

---

### Post by AutoStatic on 2011-01-05
neil and so-synth-lv2 are now available in my PPA.

[http://sites.google.com/site/neilsequencer/](http://sites.google.com/site/neilsequencer/)
[https://github.com/jeremysalwen/So-synth-LV2](https://github.com/jeremysalwen/So-synth-LV2)
[https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa)

Best,

Jeremy

---

### Post by shimoda on 2011-01-06
> **binger said:**
> I am having the same issue with pulseaudo-module-jack.  Did you find a solution?

No, sorry... No solution yet...:-(

---

### Post by phredbull on 2011-01-09
Hi, I'm trying to add your repo to my sources, but when I refresh synaptic, I get this message:
```
Failed to fetch http://ppa.launchpad.net/falk-t-j/lucid/ubuntu/dists/isadora/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```
I'm using Mint Isadora Fluxbox. I had successfully enabled this PPA before, but this is a new install. I also tried the bleeding-edge PPA with the same result.
:confused:

---

### Post by tehk on 2011-01-17
anyone else had any issues like this >> 
[http://ardour.org/node/4139](http://ardour.org/node/4139)
???

I can't get ardour 2 or 3 to run anymore. It works when I compile from source, but both packaged versions are shot :X

---

### Post by AutoStatic on 2011-01-18
IR: LV2 Convolution Reverb packages now available in my PPA (latest version).

[https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa)
[http://factorial.hu/plugins/lv2/ir](http://factorial.hu/plugins/lv2/ir)

Best,

Jeremy

---

### Post by falkTX on 2011-01-18
> **AutoStatic said:**
> IR: LV2 Convolution Reverb packages now available in my PPA (latest version).

[https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa)
[http://factorial.hu/plugins/lv2/ir](http://factorial.hu/plugins/lv2/ir)

Best,

Jeremy

Haha,
I was going to say the same... :lolflag:

Anyway, Jeremy, I think it's time to announce the new PPAs...

---

### Post by AutoStatic on 2011-01-18
Yeah you're right, saves us from doing the same job :)

---

### Post by falkTX on 2011-01-18
> **AutoStatic said:**
> Yeah you're right, saves us from doing the same job :)

ok, I'll create a new thread for it though, cause this one already has 50 pages...


EDIT: New Thread created -> [http://ubuntuforums.org/showthread.php?t=1670196](http://ubuntuforums.org/showthread.php?t=1670196)
Please continue the conversation there. (or not, if you're still using the old repos)

---

### Post by shimoda on 2011-01-22
Laditools can't be upgraded...

Requires "python-wmdocklib"...

(I'm using the old falkx-PPA... With newer PPAs there are a lot of packages with this problem...)

Any ideas?

---

### Post by falkTX on 2011-01-22
> **shimoda said:**
> Laditools can't be upgraded...

Requires "python-wmdocklib"...

(I'm using the old falkx-PPA... With newer PPAs there are a lot of packages with this problem...)

Any ideas?

hey there

you should use both PPAs for the moment, as I'll soon start deleting packages from the "old" ones.

thanks for reporting the error, will be fixed very soon!
;)

---

### Post by Kitoo on 2011-02-02
I'd like to thank the Kxstudio team for making life easier for musicians . I've been an ubuntu user for many years but don't have experience compiling packages. Now I can focus on making music :guitar:

Having said that, I'm trying to get the latest version of hydrogen installed in my ubuntu studio maverik (love it) that I got from the [here,]("https://launchpad.net/%7Ekxstudio-team/+archive/latest/+sourcepub/1478699/+listing-archive-extra") but I'm having an issue. While installing it, I noticed that it has a dependency on jackd1 and by installing jackd1, it uninstalls jackd2. So, I went to the hydrogen website and when reading the [instructions]("http://trac.assembla.com/hydrogen/wiki/development%3Aqt4compile") for downloading and installing the svn, I noticed that it requires libjack-dev instead of libjack-jackd2-dev. If I installed libjack-dev, it would automatically uninstall the jackd2 package!

Is there a way to compile hydrogen to work with jackd2? If so, please show me the way! I need the latest version because it allows me to record my edrum in "song mode" and this feature is not available in hydrogen 0.9.4.

I would appreciate any help!

---

### Post by tehk on 2011-02-04
Could someone list out all the falktx ppa's so that I can re-add them and go back to using ardour3? I removed them from my system (thought they were conflicting with the kxstudio ppa's) in order to determine why Ardour kept seg faulting on launch. It turns out that the problem was with libraptor and librdf0. See here >> [http://ardour.org/node/4139#comment-24399](http://ardour.org/node/4139#comment-24399)

Anyway, the KxStudio page used to list all the falktx ppa's which had ardour3 and now they only list the KxStudio PPA's which do not.

---

