---
title: "Rhythmbox 0.9.5 is here!"
date: 2006-06-18
forum: The Cafe
---

### Post by SlugO on 2006-06-18
So Rhythmbox 0.9.5 is finally out. As usual it has several bug fixes and new features
but my favorite feature is the long overdue support for displaying album art :D
Changelog is [here]("http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/0.9/rhythmbox-0.9.5.news") and you can download the source [here]("http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/0.9/rhythmbox-0.9.5.tar.bz2").

Could someone make a .deb? I made one for myself with checkinstall but I don't think it's good enough to share, couldn't enable all the things...

---

### Post by mostwanted on 2006-06-18
I was wondering, when are they going to change the layout into something better? I think gigantic progress bar needs to go, it takes way too much space on my small CRT screen.

---

### Post by xXx 0wn3d xXx on 2006-06-18
I'll build a debian package. Just give me a few seconds.

Edit: There are tons of dependency problems with this package. I can solve most but here is when stuff goes wrong and I can't fix it.

> checking for RHYTHMBOX... configure: error: Package requirements (  gtk+-2.0 >= 2.6.0                                        libgnomeui-2.0  libglade-2.0                                             gnome-vfs-2.0 >= 2.7.  gnome-vfs-module-2.0) were not met:

No package 'gtk+-2.0' found
No package 'libgnomeui-2.0' found
No package 'libglade-2.0' found


---

### Post by djmdave on 2006-06-18
[quote="from the changelog"]* allow ipod renaming, ejection, deletion and [COLOR=Red]_**transfer**_[/COLOR] (Christophe Fergeau)[/quote] 
Is that transfer to and from ipods like banshee can do, or just copying from the ipod?

---

### Post by kanem on 2006-06-18
[QUOTE=djmdave]Is that transfer to and from ipods like banshee can do, or just copying from the ipod?[/QUOTE]Excerpts from the development list:
> On behalf of the Rhythmbox developers, I'm proud to announce the sixth
release of the Rhythmbox 0.9 series...

Notable new features include:
...
- Partial iPod write support [1]
...
[1] off by default, pass --enable-ipod-writing to enable.

---

### Post by Lord Illidan on 2006-06-18
Hey guys, thanks for da link. Trying to compile it, however it stops here:
```

checking for TOTEM_PLPARSER... configure: error: totem playlist parsing library not found or too old
```

---

### Post by pertti on 2006-06-18
Have you installed the build dependencies first? If not sure, try:

```
sudo apt-get build-dep rhythmbox
```

I have compiled it successfully, but without album art support. It seems that album art is implemented through a python plugin. By default, rhythmbox isn't configured with python support, but when I try to enable it I get this error:

```

./configure --enable-python
...
checking whether we can build a shared library depending on libpython... no
configure: error: Python support explicity requested, but not found

```

Am I missing any package? There are couple of packages called libpythonize (which are KDE-related), but no libpython.

Thanks in advance!

---

### Post by Lord Illidan on 2006-06-18
10x for the suggestion. Downloading and installing as I type.

---

### Post by xXx 0wn3d xXx on 2006-06-18
[ Rythmbox 9.5 fresh from the compilier. ](www.megaupload.com/?d=PPF6MJEP)

---

### Post by artelsj on 2006-06-18
The .deb installed wonderfully. What do I have to do next to get the art display plugin working? (Thanks).

---

### Post by gamma on 2006-06-18
I stopped using Rhythmbox because they broke the interface. Why is there tons of whitespace between the nativation buttons when the gigantic progress bar could fit nicely in that space and save some space. Kind of like there isn't a need for 2 panels for the default gnome desktop, but anyways :P.

Use banshee...

---

### Post by Johnsie on 2006-06-19
I just checked out Rythmbox 0.9.5 and banshee. I think RB has a better GUI and is easier to organizer your music but I like that banshee has a record to cd function. 

Oh well... I'm yet to find the perfect media player  for Ubuntu.. Amarok was pretty close but then they went and changed the whole GUI.

There's things I like about all of them but I want one that has all the feaures in one, looks good and is good at sorting music out properly.

---

### Post by kpolice on 2006-06-19
[QUOTE=xXx 0wn3d xXx][ Rythmbox 9.5 fresh from the compilier. ](www.megaupload.com/?d=PPF6MJEP)[/QUOTE]

Could you upload it anywhere else like rapidshare?? I cant download anything from megaupload :S

---

### Post by Johnsie on 2006-06-19
I'll upload it to [http://steeky.com/downloads](http://steeky.com/downloads)

---

### Post by Johnsie on 2006-06-19
uhhh... sorry I took so long to mirror that... Had a bit of a domestic lol :-)

---

### Post by cbudden on 2006-06-19
Here is a package I made. [http://cbudden.sitesled.com/rhythmbox_0.9.5-1_i386.deb](http://cbudden.sitesled.com/rhythmbox_0.9.5-1_i386.deb)

---

### Post by Lord Illidan on 2006-06-19
All said and done, it still does not compare to Amarok.

---

### Post by Johnsie on 2006-06-19
I'm thinking that too Lord... I wish amrok had cd burning though... video would be nice too but I don't think that's one of their goals.

---

### Post by Johnsie on 2006-06-19
Oops I just realised Amarok does have burning.... Nice :-)

---

### Post by zeus77 on 2006-06-19
Several people above have encountered problems compiling the latest Rhythmbox.  These problems are all related to the fact that you don't have the correct "dev" packages installed.  Here's a quick howto to compile/install your very own copy of the latest Rhythmbox...

1. Download latest source code from the [Rhythmbox site]("http://ftp.gnome.org/pub/GNOME/sources/rhythmbox/").    Get the .tar.gz version, and put it on the desktop.  Right click on the .tar.gz file on the desktop, and select "Extract Here".  

2. If you don't already have build-essential and checkinstall, go to a terminal and type
```
sudo apt-get install build-essential checkinstall
```

3. Rhythmbox relies on the presence of a bunch of dev packages to compile with all the features.  The following will do the trick (on a virgin Dapper-i386 install, this totals 77 packages including dependencies, taking 59 MB):
```
sudo apt-get install libxml-parser-perl libgtk2.0-dev libgnomevfs2-dev libgnomeui-dev libtotem-plparser-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libnautilus-burn-dev libmusicbrainz4-dev libnotify-dev python2.4-dev python-gtk2-dev libsoup2.2-dev libgpod-dev check
```

4. Then, to compile and install, do this at the terminal
```
cd ~/Desktop/rhythmbox-0.9.5
./configure 
make
sudo checkinstall
```

5. Now, you can trash the stuff on the desktop (the .tar.gz file and the directory) if you want.  You're done!  Give it a try.

---

### Post by Gustav on 2006-06-19
I would recommend using 'sudo checkinstall' instead of 'sudo make install'.

It creates a deb package that once it's installed can easely be removed with synaptic or apt-get. (The 'make install' way forces you to remove files manually if you want to remove the program)

---

### Post by zeus77 on 2006-06-19
[QUOTE=Gustav]I would recommend using 'sudo checkinstall' instead of 'sudo make install'.[/QUOTE]

Thanks, I changed it above.

---

### Post by arguy337 on 2006-06-19
Hey, I'm getting this error while downloading those libraries:

```
The following packages have unmet dependencies:
  libgnomevfs2-dev: Depends: libavahi-client-dev but it is not going to be installed or
                             hurd but it is not installable
                    Depends: libdbus-1-dev but it is not going to be installed or
                             hurd but it is not installable
  libnautilus-burn-dev: Depends: libhal-dev but it is not going to be installed
                        Depends: libdbus-glib-1-dev but it is not going to be installed
  libnotify-dev: Depends: libdbus-glib-1-dev (>= 0.23) but it is not going to be installed
E: Broken packages

```

What can I do to fix this?

---

### Post by amoore on 2006-06-20
Im new to Rythm box and  I've just installed the rhythmbox-0.9.5_0.9.5-1_i386.deb listed here in this board because, I wanted to get the album art to show on my mp3s. My mp3s were incoded in iTunes and have the album art attached to the id tags but I can figure out how to get album art to show in Rythm box or how to activate this feature in Rythm box. My album art does show up in Banshee but Rythm box just feels more snapy. Any sugestions?

---

### Post by artelsj on 2006-06-20
After compiling Rhythmbox myself, with --enable-python, I could enable the album art plugin in Rhythmbox... Album art is displayed in the same spot as in iTunes.

---

### Post by 3saul on 2006-06-20
Does anybody have a .deb that has ipod writing and tag editing enabled?

---

### Post by arguy337 on 2006-06-20
Nice, finally got it working by downgrading those files and compiling.
It's not my favorite player but it works fast and "snappy".

---

### Post by pertti on 2006-06-20
[QUOTE=amoore]Im new to Rythm box and  I've just installed the rhythmbox-0.9.5_0.9.5-1_i386.deb listed here in this board because, I wanted to get the album art to show on my mp3s. My mp3s were incoded in iTunes and have the album art attached to the id tags but I can figure out how to get album art to show in Rythm box or how to activate this feature in Rythm box. My album art does show up in Banshee but Rythm box just feels more snapy. Any sugestions?[/QUOTE]

This happens to me also. I haven't done any Python ever, but after skimming through the plugin source code it seems that it searches and retrieves covers from Amazon, but it doesn't look for images encoded in the file tags. Images fetched from Amazon go to ~/.gnome2/rhythmbox/covers.

Maybe this will improve in the next version, maybe it's time to learn some Python :).

---

### Post by zachtib on 2006-06-20
[QUOTE=3saul]Does anybody have a .deb that has ipod writing and tag editing enabled?[/QUOTE]

ya, just gimme somewhere to put it

---

### Post by mlind on 2006-06-20
I made a little tut about compiling RB 0.9.5 and new music-applet for it.
[http://www.ubuntuforums.org/showthread.php?t=200762](http://www.ubuntuforums.org/showthread.php?t=200762)

---

### Post by maubp on 2006-06-22
Thanks **zeus77**, those instructions worked great for me :)

---

### Post by amoore on 2006-06-22
The how to worked great I also added --enable-python --with-dapp during ./configer 

Does anyone know who to get or enable bule remote for Rhythmbox?

Blue remote is a bluetooth remote for Rhythm box. The link for it is dead for it on the Rhythmbox web page. Any sugestions?

---

### Post by | MM | on 2006-06-22
Hi,

Using [mikes package]("http://www.mikesplanet.net/?p=37") I'm getting some dependency errors.

```
(Reading database ... 79204 files and directories currently installed.)
Preparing to replace rhythmbox 0.9.4.1-0ubuntu1 (using rhythmbox_0.9.5-1~dapper1_i386.deb) ...
Unpacking replacement rhythmbox ...
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on libpango1.0-0 (>= 1.12.3); however:
  Version of libpango1.0-0 on system is 1.12.2-0ubuntu3.
 rhythmbox depends on libsoup2.2-8 (>= 2.2.93); however:
  Version of libsoup2.2-8 on system is 2.2.92-0ubuntu1.
dpkg: error processing rhythmbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rhythmbox

```

Where do i get these updates?

---

### Post by xXx 0wn3d xXx on 2006-06-22
> **| MM |]Hi,

Using [mikes package]("http://www.mikesplanet.net/?p=37") I'm getting some dependency errors.

```
(Reading database ... 79204 files and directories currently installed.)
Preparing to replace rhythmbox 0.9.4.1-0ubuntu1 (using rhythmbox_0.9.5-1~dapper1_i386.deb) ...
Unpacking replacement rhythmbox ...
dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on libpango1.0-0 (>= 1.12.3) said:**
> 
In terminal:
[QUOTE]sudo apt-get build-dep rythmbox

---

### Post by | MM | on 2006-06-22
```
matthew@ubuntu:~$ sudo apt-get build-dep rythmbox
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for rythmbox
matthew@ubuntu:~$

```

:S
Should this be doable from the Dapper Repo's ... or do i have to another repo ... ?

---

### Post by xXx 0wn3d xXx on 2006-06-22
[QUOTE=| MM |]```
matthew@ubuntu:~$ sudo apt-get build-dep rythmbox
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for rythmbox
matthew@ubuntu:~$

```

:S
Should this be doable from the Dapper Repo's ... or do i have to another repo ... ?[/QUOTE]
Do you have the multiverse and universe repositories enabled ? See the "Extra repositories for Breezy/Dapper" in my signature or auto generate a sources.list [ here. ](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by mlind on 2006-06-22
[QUOTE=| MM |]```
matthew@ubuntu:~$ sudo apt-get build-dep rythmbox
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for rythmbox
matthew@ubuntu:~$

```

:S
Should this be doable from the Dapper Repo's ... or do i have to another repo ... ?[/QUOTE]

yup, but it's **rhythmbox**

---

### Post by | MM | on 2006-06-23
oops :P

---

### Post by doclivingston on 2006-06-23
Anyone who wants a .deb of the latest Rhythmbox, with all the options enabled, and even more ipod support might want to look at [http://cipherfunk.org/diary/archives/monthly/2006-06.html#e2006-06-23T11_07_59.htm](http://cipherfunk.org/diary/archives/monthly/2006-06.html#e2006-06-23T11_07_59.htm)

Paul Drain has compiled [.debs](ftp://cipherfunk.org/pub/random_cruft/rhythmbox-with-ipod-support-for-dapper/) for Dapper with the extended ipod support patch, which hasn't landed in cvs yet. It supports transcoding, editing playlists on the ipod and a few other things, but doesn't have "automatic sync" yet.


For people without an ipod, they are just good quality debs with all the options. For people with an iPod it has even better iPod support, but be warned there may be bugs that eat the tracks on your iPods (we haven't had any reported so far, but you never know).

If you do try his debs with your iPod, leaving a comment on [Gnome bug 310774](http://bugzilla.gnome.org/show_bug.cgi?id=310774) would be much appreciated, whether any problems you had or just a "works for me".

---

### Post by SlugO on 2006-06-25
Thanks for the link doc, the .deb from that site works great :D

---

### Post by rbrugman on 2006-06-25
Another vote for Amarok here.  Only thing I wish it had (that should be working after the Google Summer of Code) ends is DAAP support so I can listen to the music on my server.  As far as an audio player though, Amarok kicks all ***

---

### Post by SlugO on 2006-06-26
I wonder why Rhythmbox 0.9.5 doesn't seem to be updating my music
collection automatically even though it's checked in the options... :-k
It worked fine with 0.9.4.

---

### Post by tool462rules on 2006-06-28
i used one of the packages, the one that says xx owned xx in the deb.
CD playing is not supported and tries to play all the songs and fails, anyone give me any help, or it's back to 0.9.3...

---

### Post by mlind on 2006-06-28
[QUOTE=tool462rules]i used one of the packages, the one that says xx owned xx in the deb.
CD playing is not supported and tries to play all the songs and fails, anyone give me any help, or it's back to 0.9.3...[/QUOTE]

Get it from edgy repository or build it yourself using this [guide]("http://www.ubuntuforums.org/showthread.php?t=200762")

---

### Post by humansuit on 2006-06-30
[QUOTE=SlugO]I wonder why Rhythmbox 0.9.5 doesn't seem to be updating my music
collection automatically even though it's checked in the options... :-k
It worked fine with 0.9.4.[/QUOTE]

Yeah, same problem here. Not nice.

---

### Post by leeyee on 2006-07-11
I'm wondering when will the repos involve rhythmbox 0.9.5? Looking forward it....

---

### Post by bruce89 on 2006-07-11
> **leeyee said:**
> I'm wondering when will the repos involve rhythmbox 0.9.5? Looking forward it....
[https://launchpad.net/products/dapper-backports/+bug/50477](https://launchpad.net/products/dapper-backports/+bug/50477)

---

### Post by afon on 2006-08-12
Thanks for deb package ;)

---

### Post by psyeye on 2006-08-17
Hi!

> **doclivingston said:**
> Paul Drain has compiled [.debs](ftp://cipherfunk.org/pub/random_cruft/rhythmbox-with-ipod-support-for-dapper/) for Dapper with the extended ipod support patch, which hasn't landed in cvs yet. It supports transcoding, editing playlists on the ipod and a few other things, but doesn't have "automatic sync" yet.

Whenever I copy files to my iPod Shuffle with this version of Rhythmbox, the files are copied, I can play them from within Rhythmbox - but not with my Shuffle. :confused: 

Anybody experienced that? Or does anybody know how to init my iPod so it works?


thanks for any hint!
psyeye

---

### Post by idn on 2006-08-20
I am getting an error when I try to 'make' the source code

link: cannot find the library `/usr/lib/libXrender.la' or unhandled argument `/usr/lib/libXrender.la'


I have installed all the dependancies

---

### Post by mlind on 2006-08-20
> **idn said:**
> I am getting an error when I try to 'make' the source code

link: cannot find the library `/usr/lib/libXrender.la' or unhandled argument `/usr/lib/libXrender.la'


I have installed all the dependancies

This is the third time I've seen this error reported, are you using Dapper or Edgy? That file doesn't exist for either distribution. 
I've never seen that error myself. How did you configure rhythmbox? Have you tried running autogen.sh to generate new Makefiles ?

---

### Post by idn on 2006-08-20
I am using dapper at the moment - if its X related maybe it has something to do with XGL or compiz. when I run autogen.sh I get the following error:

Checking for required M4 macros...
  libtool.m4 not found
  glib-gettext.m4 not found
  intltool.m4 not found
  pkg.m4 not found
  gtk-doc.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build rhythmbox
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

---

### Post by mlind on 2006-08-20
> **idn said:**
> I am using dapper at the moment - if its X related maybe it has something to do with XGL or compiz. when I run autogen.sh I get the following error:

Checking for required M4 macros...
  libtool.m4 not found
  glib-gettext.m4 not found
  intltool.m4 not found
  pkg.m4 not found
  gtk-doc.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build rhythmbox
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?


Yeah, you're probably using some package as build dependency which is built against older libxrender-dev. Make sure you're not intalling build dependencies from any 3rd party repositories.
Is your libxrender-dev package 1:0.9.0.2-0ubuntu2 ?

(I'm guessing you have libcairo2 from 3rd party repository)

---

### Post by idn on 2006-08-20
Yeah I have the same version of libxrender as you mentioned above and yes I am using cairo from another repo to get xgl up and running.

Fixed: 

 ./configure --enable-python

That should get it working

---

### Post by idn on 2006-08-21
Fixed!!!!

[http://ubuntuforums.org/showthread.php?t=238449](http://ubuntuforums.org/showthread.php?t=238449). However I cant seem to get the playlist and cover art plugins to work - they are not listed in the plugins list when rb starts up

---

### Post by mlind on 2006-08-21
> **idn said:**
> Fixed!!!!

[http://ubuntuforums.org/showthread.php?t=238449](http://ubuntuforums.org/showthread.php?t=238449). However I cant seem to get the playlist and cover art plugins to work - they are not listed in the plugins list when rb starts up

Yeah, that same libcairo2 issue seems to pop out frequently. I think you should just get the source package from edgy or debian and build that with your distribution. At least it should make plugins work normally.

---

### Post by SlugO on 2006-08-25
Yay! The latest development version from some repo finally updates my collection automatically.

I have to say that I'm quite annoyed by how "lazy" the Last.fm plugin is. It usually puts atleast half a dozen songs to queue before it bothers to submit them. It doesn't even submit them when I close Rhythmbox, usually takes a couple of restarts to get them there. This is **really** annoying. I want the song to show up on the page the second it's past the 50% mark like in Windows. Having to wait for atleast half an hour is not good...

---

### Post by mlind on 2006-08-25
> **SlugO said:**
> Yay! The latest development version from some repo finally updates my collection automatically.

I have to say that I'm quite annoyed by how "lazy" the Last.fm plugin is. It usually puts atleast half a dozen songs to queue before it bothers to submit them. It doesn't even submit them when I close Rhythmbox, usually takes a couple of restarts to get them there. This is **really** annoying. I want the song to show up on the page the second it's past the 50% mark like in Windows. Having to wait for atleast half an hour is not good...

I haven't got this problem, except on rare occasions when last.fm server is down. I'm using a CVS build too.

---

