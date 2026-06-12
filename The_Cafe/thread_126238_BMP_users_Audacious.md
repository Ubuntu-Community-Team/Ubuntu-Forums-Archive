---
title: "BMP users: Audacious"
date: 2006-02-06
forum: The Cafe
---

### Post by bored2k on 2006-02-06
[CENTER][IMG]http://img154.imageshack.us/img154/9237/a7lx.png[/IMG][/CENTER]

I think it's worth giving a shot. > 
** What is Audacious?**

Audacious is a fork of beep-media-player 0.9.7.1.

**Why did you fork beep-media-player?**

First off, the fork has no political reasons, it is based entirely on technical merit. It's based on a few issues:

    * There have been some quirks in beep-media-player that have annoyed users. (ID3v2 tag handling can be buggy for some users.)
    * BMP classic is no longer actively maintained by the development team.
    * We had our own ideas about how a player should be designed, which we wanted to try in a production environment.
    * Beep lacked functionality that is useful for people who do streaming, such as the songchange plugin from XMMS. 

Therefore, a fork seemed most logical as a choice for accomplishing our goals. descender &c have done very good work, but their ideas for a next-generation beep do not align with ours. 
[http://audacious.nenolod.net/Main_Page](http://audacious.nenolod.net/Main_Page)

---

### Post by TechSonic on 2006-02-06
libbinio1c2
libid3-3.8.3c2a
libjack0.100.0-0
libtag1c2a
libvisual0.2

Can't be installed because those packages couldn't be installed.

---

### Post by bored2k on 2006-02-06
What about Dapper? I just compiled it and it went well (not on Ubuntu though :/).

---

### Post by TechSonic on 2006-02-06
I don't have a way of Downloading Dapper to even try it.  All I know is that those packages aren't offered in the repos and all my searches keep coming up with those packages but with ended development and no install instructions.  All I get is this weird make install crud.

Theres an idea for a new program, one of those compilers for those things. Nice GUI interface.  Import source, click on build and your done. I'd love a program like that.

---

### Post by TechSonic on 2006-02-06
I got it installed without a problem on Fedora 4 and PCLinuxOS thats running on my other computers.  Although they are all setup with all the installable features.  o.o

---

### Post by newuser111 on 2006-02-06
the debian/ubuntu deb cannot be installed on breezy without changing a lot of dependencies

the redhat/fedora rpm can be alien'd into an installable deb however

---

### Post by awakatanka on 2006-02-06
[QUOTE=TechSonic]I don't have a way of Downloading Dapper to even try it.  All I know is that those packages aren't offered in the repos and all my searches keep coming up with those packages but with ended development and no install instructions.  All I get is this weird make install crud.

Theres an idea for a new program, one of those compilers for those things. Nice GUI interface.  Import source, click on build and your done. I'd love a program like that.[/QUOTE]
maybe this something for you if you are on KDE : [http://www.kde-apps.org/content/show.php?content=17183](http://www.kde-apps.org/content/show.php?content=17183)

But think if it doesn't work on CLI it doesn't work on a GUI to.

---

### Post by TechSonic on 2006-02-06
Ok for anyone wanting to just download, here [http://www.techsonic.net/apps/audacious_0.1.2-2.2_i386.deb](http://www.techsonic.net/apps/audacious_0.1.2-2.2_i386.deb)
sudo dpkg -i audacious_0.1.2-2.2_i386.deb
Done, look in Sound & Video

---

### Post by TechSonic on 2006-02-06
[QUOTE=newuser111]the debian/ubuntu deb cannot be installed on breezy without changing a lot of dependencies

the redhat/fedora rpm can be alien'd into an installable deb however[/QUOTE]


Should of said something earlier, before I went through all the trouble of doing it from source..  Oh well, previous post has a quicky install deb.

---

### Post by Sheinar on 2006-02-06
I checked it out not long after it was originally forked. Even though it's basically just BMP with a new name and a new default skin, it's worth using now that the original BMP is no longer being developed.

It's definitely more useable as an audio player than BMPx is in it's current state.

---

### Post by lisa-m on 2006-02-11
I been using this for a while, i got almost all of it working, on ubuntu breezy, like libvisual, dbus, gconf, id3tag and all that. I'm using the current version 0.2. It was a breezy for me to have up and running. The only things i need to know was ./configure, make and make install. I think this should make it to official ubuntu repository for dapper. It beats bmp and bmpx and xmms in my opinion.

---

### Post by ice60 on 2006-02-11
hi, has BMP been discontinued? if it has i suppose i should change to something else because there won't be any security fixes if any exploits are found.

 i have 3/4 other players i use regularly, but if i uninstall BMP i'll need something to work with Streamtuner. what should i use?

i was looking at this earlier today. i don't if it's helpful for anyone?
[http://ralph.n3rds.net/index.php?/archives/137-Audacious-Media-Player.html](http://ralph.n3rds.net/index.php?/archives/137-Audacious-Media-Player.html)

---

### Post by papangul on 2006-02-11
[QUOTE=bored2k]
I think it's worth giving a shot. 
[http://audacious.nenolod.net/Main_Page](http://audacious.nenolod.net/Main_Page)[/QUOTE]
Thanks a lot, just the one I needed. For sometime I was searching about how to play flacs in bmp. Problem solved.

---

### Post by zi99y on 2006-02-27
anyone got a mirror for that deb? I'm just getting "bandwidth limit exceeded" when I follow the link. ta

---

### Post by super on 2006-02-27
*libtag1c2a* is my major dependancy problem.
what the heck is it? it seems that eclair depends on it also.

i'm running dapper

---

### Post by jhellen on 2006-04-30
This was the result in Dapper Beta2. It's incredible how difficult it is to install an application :???: This should be included instead of that BMP.

$ sudo dpkg -i audacious_0.1.2-2.2_i386.deb
Password:
dpkg-deb: `audacious_0.1.2-2.2_i386.deb' is not a debian format archive
dpkg: error processing audacious_0.1.2-2.2_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 audacious_0.1.2-2.2_i386.deb

---

### Post by BoyOfDestiny on 2006-04-30
[QUOTE=jhellen]This was the result in Dapper Beta2. It's incredible how difficult it is to install an application :???: This should be included instead of that BMP.

$ sudo dpkg -i audacious_0.1.2-2.2_i386.deb
Password:
dpkg-deb: `audacious_0.1.2-2.2_i386.deb' is not a debian format archive
dpkg: error processing audacious_0.1.2-2.2_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 audacious_0.1.2-2.2_i386.deb[/QUOTE]

0.1.2?
1.0.0 is out...
[http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page)

Anyway I hear ya, I installed from source (which is "easy" after you've gotten it to work once.) Since all the dependencies are in, it's just a matter of 
./configure
make
checkinstall (or make install)

Anyway, it is better than beep IMHO too. I don't think they'll put it in at this late stage... The best bet is for backports perhaps...

P.S. The feature I'm waiting for is changing subtunes for nsf's and gbs... Other than that the player it top notch...

Edit: Oh yeah, have you tried using gdebi? I thought this is the new way for people to install .debs graphically... Also, the error your got implies something is wrong with the deb itself...

---

### Post by jhellen on 2006-04-30
Tried to compile that 1.00 version and got this:

checking for glib-2.0 >= 2.6.0 gtk+-2.0 >= 2.6.0 gthread-2.0 pango... yes
checking GTK_CFLAGS... -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0
checking GTK_LIBS... -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lcairo -lX11 -lgthread-2.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
checking for libglade-2.0 >= 2.3.1... configure: error: Cannot find libglade

Click n run ](*,)

---

### Post by OffHand on 2006-04-30
I tried to install in through the synaptic but that didn't work.
When compiling it it cannot find alsa which obviously is installed.
It will make an install file though but I want it to compile it with alsa.
Anyone know what I might be missing?
What exactly makes this a better player than beep?

Edit: any other advantages than the ones mentioned in the OP.

@ jhellen: search for libglade in the synaptic and install
libglade 2-0
libglade2.0-cil
libglade2-dev

---

### Post by BoyOfDestiny on 2006-04-30
Ok relax, you said it couldn't find libglade. Fire up synaptic get libglade2-dev. Any time it gives you an error about something missing, search for it in synaptic (usually it's the -dev of something with a similar name). Make sure you have build-essential installed too...

As for it being better than beep. For me it's the plugins that come out of the box (the esoteric ones like nsf, gbs, spc, sid, adplug, psf, etc... The only one I had to install seperately is uade, which plays about 180 amiga formats...) Also I've got hardware midi support with this (just have to load a soundfont with asfxload).

It supports formats for average folks too, ogg, flac, mp3, etc etc without having to deal with installing the plugins seperately...

Check out the screen cap (shows the plugins)

---

### Post by OffHand on 2006-04-30
[QUOTE=BoyOfDestiny]
As for it being better than beep. For me it's the plugins that come out of the box (the esoteric ones like nsf, gbs, spc, sid, adplug, psf, etc... The only one I had to install seperately is uade, which plays about 180 amiga formats...) Also I've got hardware midi support with this (just have to load a soundfont with asfxload).

It supports formats for average folks too, ogg, flac, mp3, etc etc without having to deal with installing the plugins seperately...

Check out the screen cap (shows the plugins)[/QUOTE]
Looks interesting. Do you you know what could be the thing with not wanting to compile with alsa?

---

### Post by BoyOfDestiny on 2006-04-30
[QUOTE=subsonic_shadow]Looks interesting. Do you you know what could be the thing with not wanting to compile with alsa?[/QUOTE]

Hmm...  install
libasound2-dev

---

### Post by OffHand on 2006-04-30
[QUOTE=BoyOfDestiny]Hmm...  install
libasound2-dev[/QUOTE]
I managed to compile alsa with it and I installed it but it didn't want to launch  ](*,)

---

### Post by DoktorSeven on 2006-04-30
Argh.  Thing crashed on me several times and would occasionally get "hung" on the current song when I press "next song" unless I hit it several times quickly.  

Why, oh, why can't I get rid of XMMS?? *cries*

---

### Post by BoyOfDestiny on 2006-04-30
[QUOTE=subsonic_shadow]I managed to compile alsa with it and I installed it but it didn't want to launch  ](*,)[/QUOTE]

If you run it from terminal, does it complain it can't find libaudacious.so? (or something like that)

This will solve it, (from the audacious faq)

[B]sudo su
echo '/usr/local/lib' >> /etc/ld.so.conf
ldconfig
exit[/B]

Anyway, we could make a simple script (or just a list of commands) to use the svn of audacious to download the stable release, (optionally of course, people could just download the tar.gz and decompress it)
get dependences (apt-get install blah blah) then ./configure 
make 
make install

I already have my build environment set, but if you guys are interested here is a start. If we can tweak it a bit more, it will be worth posting as a how-to...

Also, don't forget to have universe enabled (and maybe multiverse)

**sudo apt-get install build-essential libbinio-dev libglade2-dev libflac-dev libasound2-dev libogg-dev autoconf automake1.9 libvorbis-dev libvisual0.2-dev libresid-builder-dev libtagc0-dev libsidplay2-dev libmad0-dev libgtk2.0-dev**

For those without midi cards, and want midi, get timidity
It's a larger download because of the freepats soundfont thing... It's optional either way. :) If you have hardware midi you are set.

[B]./configure
make
sudo make install[/B]

Ok, please comment here if something is missing. Also it's fine to run the apt-get install command over and over. It will say blah blah is already installed, then it will install the other stuff (+dependencies, all you need is -dev and it will get the main library)

P.S. I can vouch that audacious is stable under dapper (both 32-bit and 64-bit) :)

---

### Post by OffHand on 2006-05-01
[QUOTE=BoyOfDestiny]If you run it from terminal, does it complain it can't find libaudacious.so? (or something like that)

This will solve it, (from the audacious faq)

[B]sudo su
echo '/usr/local/lib' >> /etc/ld.so.conf
ldconfig
exit[/B]

Anyway, we could make a simple script (or just a list of commands) to use the svn of audacious to download the stable release, (optionally of course, people could just download the tar.gz and decompress it)
get dependences (apt-get install blah blah) then ./configure 
make 
make install

I already have my build environment set, but if you guys are interested here is a start. If we can tweak it a bit more, it will be worth posting as a how-to...

Also, don't forget to have universe enabled (and maybe multiverse)

**sudo apt-get install build-essential libbinio-dev libglade2-dev libflac-dev libasound2-dev libogg-dev autoconf automake1.9 libvorbis-dev libvisual0.2-dev libresid-builder-dev libtagc0-dev libsidplay2-dev libmad0-dev libgtk2.0-dev**

For those without midi cards, and want midi, get timidity
It's a larger download because of the freepats soundfont thing... It's optional either way. :) If you have hardware midi you are set.

[B]./configure
make
sudo make install[/B]

Ok, please comment here if something is missing. Also it's fine to run the apt-get install command over and over. It will say blah blah is already installed, then it will install the other stuff (+dependencies, all you need is -dev and it will get the main library)

P.S. I can vouch that audacious is stable under dapper (both 32-bit and 64-bit) :)[/QUOTE]
I'll try it again in a few hours from this post and report back. I first need to relax a bit.

---

### Post by OffHand on 2006-05-01
I managed to compile it now. I also had to use the commands you found in the FAQ.
During 'make' I got a few error messages. The log is in the file attached to this message. Maybe you or someone else know what these errors are.
First 2 times I launched it I couldn't move it but now it seems to work ok.
Thanks

---

### Post by BoyOfDestiny on 2006-05-01
[QUOTE=subsonic_shadow]I managed to compile it now. I also had to use the commands you found in the FAQ.
During 'make' I got a few error messages. The log is in the file attached to this message. Maybe you or someone else know what these errors are.
First 2 times I launched it I couldn't move it but now it seems to work ok.
Thanks[/QUOTE]

Looks ok to me, just warnings, not errors.

---

### Post by encho on 2006-05-16
Never had any luck with compiling, even with all dev packages in the world ](*,) 
But this howto helped, just installed dependencies, and downloaded deb package and it worked: [http://www.ubuntuforums.org/showthread.php?t=162947](http://www.ubuntuforums.org/showthread.php?t=162947)

Tested it with mp3, ogg, m3u, everything is perfect, just need some skins. But will settle for default one for now.

---

### Post by papangul on 2006-06-03
Perhaps not many people use alsaplayer but it very useful and the quality is very good:
[http://www.alsaplayer.org/features.php3](http://www.alsaplayer.org/features.php3)
I used audacious earlier to play individual/streaming files. Now I'm a very satisfied user of alsaplayer.

---

### Post by y0ssarian on 2006-06-03
Has anyone installed an audioscrobbler plugin for audacious yet? I found this [http://aur.archlinux.org/packages/audacious-scrobbler/audacious-scrobbler/]("http://aur.archlinux.org/packages/audacious-scrobbler/audacious-scrobbler/") which is just a a patched xmms plugin; however, I am unsure as to how the patch works. Can anyone explain how this works or point me in the direction of another plugin?

---

### Post by shrimphead on 2006-06-04
[QUOTE=BoyOfDestiny]
Check out the screen cap (shows the plugins)[/QUOTE]

I know this is a bit off topic but where did you get that wall?

---

### Post by bored2k on 2006-06-04
[QUOTE=y0ssarian]Has anyone installed an audioscrobbler plugin for audacious yet? I found this 
http://aur.archlinux.org/packages/audacious-scrobbler/audacious-scrobbler/[/URL] which is just a a patched xmms plugin; however, I am unsure as to how the patch works. Can anyone explain how this works or point me in the direction of another plugin?[/QUOTE][http://aur.archlinux.org/packages/audacious-scrobbler/audacious-scrobbler/audacious-scrobbler-0.3.8.1-autoconf.patch](http://aur.archlinux.org/packages/audacious-scrobbler/audacious-scrobbler/audacious-scrobbler-0.3.8.1-autoconf.patch)
[URL="http://aur.archlinux.org/packages/audacious-scrobbler/audacious-scrobbler/"]
That's a plugin for ArchLinux, not Ubuntu.
```

http://aur.archlinux.org/packages/audacious-scrobbler/audacious-scrobbler/xmms-scrobbler_0.3.8.1.orig.tar.gz
patch -Np1 -i ../audacious-scrobbler-**$pkgver**-autoconf.patch
./configure --prefix=/usr
```I extracted that from the PKGBUILD of that package, so that might or might not work.

---

### Post by Kimm on 2006-06-04
I'm having trubble with Audacious 1.0 and 1.1dr1
The player freezes if I'm using Alsa output (but still plays). Using ESD fixes that though...

You realy should have a look at the latest BMPx (from source), its acctually quite nice.

---

### Post by nenolod on 2006-06-10
Hi! I'm one of the developers of Audacious. (no, really, I am -- I stumbled onto this through google.)

Audacious has had a scrobbler plugin integrated since 0.2.1. However, you will need MusicBrainz and CURL installed. You will also need the development packages for these installed as well.

Once those requirements have been satisfied, the Scrobbler plugin will work.

Kimm: Please file a bug on our bug tracker, available at [http://bugs.audacious-media-player.org](http://bugs.audacious-media-player.org) . We will attempt to fix it before Audacious 1.1 is released.

Thanks, and have a great weekend. :)

---

### Post by BoyOfDestiny on 2006-06-10
[QUOTE=shrimphead]I know this is a bit off topic but where did you get that wall?[/QUOTE]

Here ya go.

[http://ausanime.com/gallery/thumbnails.php?album=search&type=full&search=winry](http://ausanime.com/gallery/thumbnails.php?album=search&type=full&search=winry)

As for Kimm's problem, I use it with ALSA exclusively (1.0 then 1.1) and it works great... I don't have ESD enabled at all, not sure if that matters... I would launch audacious from a terminal and see if any errors are spat out...

Also, nenolod, you rock. 

Audacious hands down, my favorite player.

---

### Post by Technoviking on 2006-06-13
I have made a package for Audacious 1.1dr2.
[http://www.ubuntuforums.org/showthread.php?p=1133529#post1133529](http://www.ubuntuforums.org/showthread.php?p=1133529#post1133529)

---

### Post by BoyOfDestiny on 2006-06-13
Audacious 1.1dr2 supports (well works for what I've tested) subtunes for nsfe, gbs, etc!
I'm one happy camper! If somone wants a 64-bit deb without dependencies (checkinstall 1.6.0), let me know and I'll post it... :)

---

### Post by tonyisntcreative on 2006-06-15
Looks good, I might install soon.  I'm still using BMP, though.

One question....the docklet thing is just like a system tray icon and will take it off of your window list WHILE still on top (like in winamp), correct?  If so I'm installing for sure.

---

### Post by el_Salmon on 2006-06-16
[QUOTE=nenolod]Hi! I'm one of the developers of Audacious. (no, really, I am -- I stumbled onto this through google.)

Audacious has had a scrobbler plugin integrated since 0.2.1. However, you will need MusicBrainz and CURL installed. You will also need the development packages for these installed as well.

Once those requirements have been satisfied, the Scrobbler plugin will work.
[/QUOTE]

What Ubuntu packages are these (Musicbrainz and CURL) ?

Ubuntu Linux has several libmusicbrainz-N packages.

---

### Post by Kimm on 2006-06-16
My issue with Audacious has been fixed now.
In DR2 it was replaced by another one though... Audacious on average uses 20% of the CPU, at all times.
And I lost my perfect SVN Build :'(

Bit i filed it as a bugg, so I expect to see if fixed soon :)

---

### Post by el_Salmon on 2006-06-17
lastfm plugin from BMP works fine for me in Audacious:

```
$ sudo apt-get install beep-media-player-scrobbler
$  sudo cp /usr/lib/bmp/General/libbmp_scrobbler.so /usr/lib/audacious/General/

```

---

### Post by Kimm on 2006-06-17
Doesnt Audacious have its own Audio Scrobbler pluggin? ^.-

---

### Post by el_Salmon on 2006-06-17
[QUOTE=Kimm]Doesnt Audacious have its own Audio Scrobbler pluggin? ^.-[/QUOTE]
Yes, but it doesn't in Ubuntu package.

---

### Post by Kimm on 2006-06-17
Ah, that explains it.

---

