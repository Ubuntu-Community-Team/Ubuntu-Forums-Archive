---
title: "Audacious 2.0 Alpha2 Released"
date: 2009-04-18
forum: The Cafe
---

### Post by Kosimo on 2009-04-18
Hello Guys, 
Audacious has quietly released the first alpha of the 2.x series. It doesn't have a change log and the only thing we know is that there is a new skinned skin compatibility and audio improvements. 

Get it here: [http://audacious-media-player.org/](http://audacious-media-player.org/)


Edit: Finally is stable! 

Here the .deb's created by Flavio!

**[Audacious 2.0.1-Stable.deb]("http://www.flapane.com/unixmac/Ubuntu/audacious_2/audacious_2.0.1-1_i386.deb")**

**[Audacious 2.0.1-Stable Plugins.deb]("http://www.flapane.com/unixmac/Ubuntu/audacious_2/audacious-plugins_2.0.1-1_i386.deb")**

Here some screenshots:

[IMG]http://kosimo.googlepages.com/Audacious2Alpha1.png[/IMG]


[IMG]http://kosimo.googlepages.com/Audacious2Alpha1-2.png[/IMG]

---

### Post by Kosimo on 2009-04-18
After using it for a While I can confirm the audio quality improvements respect 1.5.1, and is much louder.

---

### Post by andrewabc on 2009-04-18
Hopefully it is done before ubuntu 9.10. Which means done by first of September at latest.

---

### Post by wingnux on 2009-04-18
Does it have a media library like winamp 5, rhytmbox, amarok... ?

---

### Post by Kosimo on 2009-04-18
> **wingnux said:**
> Does it have a media library like winamp 5, rhytmbox, amarok... ?

No, Audacious works only with playlists

---

### Post by RiceMonster on 2009-04-18
Fantastic, I've been looking forward to audacious 2 for a while. Can't wait to try this out.

---

### Post by pwnst*r on 2009-04-18
audio *improvements*?  it must have been inferior before then. and i'm not sure how you gauge loudness unless you a/b tested it that way in a controlled environment.  raising the db level is perceived as "sounding better", which is why there is so much compression going on in recording techniques today sadly.

---

### Post by gorthaug on 2009-04-21
Hi, Kosimo i can't download the deb files, i gets a page that say "This is a private file. Divshare staff disabled access to this file."

Can you fix this? please! :D

---

### Post by nenolod on 2009-04-25
there are semi-official builds in my Debian sid "goodies" repo.

use "deb [http://petrie.dereferenced.org/archive](http://petrie.dereferenced.org/archive) unstable/"

they are slightly newer than alpha1 too. i intend to autobuild them nightly soon until we hit beta. :)

you probably need jaunty for these. i havent tested them. the sources are there for rebuilding, though.

audacious2 is basically a major rewrite of the codebase to fix the remaining XMMSisms.

---

### Post by And1945 on 2009-04-26
Sweet!

I was messing around with some svn/cvn tool that didnt do its job or whatever. thank you!

> 
This is a private file.
Divshare staff disabled access to this file.


---

### Post by Kosimo on 2009-04-30
Audacious 2.0 Alpha2 has just been released

[http://audacious-media-player.org/](http://audacious-media-player.org/)

---

### Post by flapane on 2009-05-10
Woops I didn't see this thread, I suppose it's better to post the message here :P

Just compiled and debianized the 2.0 beta and its plugins on hardy i386 (it is supposed to work on newer versions) at [nix.flapane.com]("http://nix.flapane.com") in Ubuntu folder.
edit: detailed post, translation on the left sidebar: [link]("http://www.flapane.com/blog/2009/04/audacious-20-alpha1-appena-rilasciato-e-compilato-il-deb-per-ubuntu/")

---

### Post by flapane on 2009-05-14
2.0.1 stable just compiled at the address at the post above.

---

### Post by Kosimo on 2009-05-14
> **flapane said:**
> 2.0.1 stable just compiled at the address at the post above.

Thanks for your job!

I've updated the .deb links

---

### Post by Rikz on 2009-05-14
Seems like libmowgli, libmcs and libcddb packages are missing from dependencies.

---

### Post by super.rad on 2009-05-14
any .debs for 64bit yet?

---

### Post by flapane on 2009-05-15
> **Rikz said:**
> Seems like libmowgli, libmcs and libcddb packages are missing from dependencies.

Maybe it's better to add the deps in the first post of the thread:
> #

dep: dbus
    Sistema per messaggi interprocesso semplici 

#

dep: gtk2-engines-pixbuf
    Tema basato su pixbuf per GTK+ 2.x 

#

dep: libatk1.0-0 (>= 1.20.0)
    Toolkit ATK per l'accessibilità 

#

dep: libaudclient1
    audacious D-Bus remote control library 

#

dep: libc6 (>= 2.7-1)
    Libreria C GNU: librerie condivise
    also a virtual package provided by libc6-udeb 

#

dep: libcairo2 (>= 1.5.14)
    The Cairo 2D vector graphics library 

#

dep: libdbus-1-3 (>= 1.1.1)
    Sistema per messaggi interprocesso semplici 

#

dep: libdbus-glib-1-2 (>= 0.74)
    Sistema per messaggi interprocesso semplici (libreria condivisa basata su GLib) 

#

dep: libglib2.0-0 (>= 2.16.0)
    Libreria di funzioni C GLib 

#

dep: libgtk2.0-0 (>= 2.12.0)
    The GTK+ graphical user interface library 

#

dep: libice6 (>= 1:1.0.0)
    X11 Inter-Client Exchange library 

#

dep: libmcs1
    Abstraction library to store configuration settings (BSD-licensed) 

#

dep: libmowgli1
    a high performance development framework for C 

#

dep: libpango1.0-0 (>= 1.20.0)
    Layout and rendering of internationalized text 

#

dep: libsamplerate0
    audio rate conversion library 

#

dep: libsm6
    X11 Session Management library 

#

dep: libx11-6
    X11 client-side library 



In the next version I'll add them while building the package

---

### Post by Kosimo on 2009-05-15
> **flapane said:**
> Maybe it's better to add the deps in the first post of the thread:


In the next version I'll add them while building the package


Are them official ubuntu dependencies?

---

### Post by flapane on 2009-05-15
Yep.
I added them in the 1.5.1 deb, I haven't done yet with v2 as it still was an alpha/beta, until yesterday.

---

### Post by Kosimo on 2009-05-15
> **flapane said:**
> Yep.
I added them in the 1.5.1 deb, I haven't done yet with v2 as it still was an alpha/beta, until yesterday.

Strange... As I could install your Audacious 2 deb without any problem...  Probably because I've installed 1.5.1 from synaptic before, so I already had those dependencies installed.


ps: Ma tu si'nnapuletano? :D

---

### Post by flapane on 2009-05-15
Yes if you previously installed old version you shouldn't have problems.
Please try to add the link to the blog post also in the first post thanks.

ps Si sono napulitano e tanti napulitani in estate vanno a Barçelona :P

---

### Post by Stiff on 2009-05-17
It is high cpu load (it jumps up to 70%) of process audacious2 when i play music, when output plugin is alsa over default channel with enabled dmix. Player version 2.0.1, installed from deb packages from first message of the topic. System ubuntu 9.04.
With version from repository cpu load is normal (8-10%)

---

### Post by Stiff on 2009-05-17
I discovered, that cpu load is high when the sample rate of track is not equal to the sound card's sample rate, than player should convert sample rate. For example, my card supports rate 44100 hz, and if i play sound with sample rate 48000 hz the player will convert it, increasing cpu loading. 
[[IMG]http://img196.imageshack.us/img196/4460/40944890.th.png[/IMG]](http://img196.imageshack.us/my.php?image=40944890.png)

---

### Post by flapane on 2009-05-17
Interesting... report the bug on audacious web site

---

### Post by m_ad on 2009-05-17
I had to quit using Audacious a few months back when I couldn't load a m3u file through nautilus. Is this fixed?

---

### Post by oomingmak on 2009-05-17
> **flapane said:**
> In the next version** I'll add them while building the package**
[SIZE=3]Thank you!!![/SIZE]

I've been driven crazy by dependencies with Audacious. I could never get it to work.

I thought that running a deb would make things easier, but every deb I've ever seen for Audacious ends up having stuff missing, so you have to hunt down and install dependencies (which rather defeats the simplicity of using a deb package).

I look forward to your next fully self-contained package.

Thanks.

---

### Post by flapane on 2009-05-18
You're welcome.

---

### Post by Jungleboss on 2009-05-22
Anyone having a link to 64 bit versions?

---

### Post by koleoptero on 2009-05-22
Thank you for the debs, quite helpfu. Cheers:D

---

### Post by crashcookie on 2009-05-24
> **Stiff said:**
> I discovered, that cpu load is high when the sample rate of track is not equal to the sound card's sample rate, than player should convert sample rate. For example, my card supports rate 44100 hz, and if i play sound with sample rate 48000 hz the player will convert it, increasing cpu loading. 
[[IMG]http://img196.imageshack.us/img196/4460/40944890.th.png[/IMG]]("http://img196.imageshack.us/my.php?image=40944890.png")

you can compile from source with no sample rate conversion, maybe that helps

bar@naomi:~$ ./configure

[SNIP]

Configuration:

  Install path:                           /usr/local
  Current Audacious executable:           /usr/bin/audacious
  Use one plugin dir:                     
  Allow user plugin dir:                  yes

  Automatic character code detection:     yes
  Sample rate conversion:                 no
  D-Bus support:                          yes
  Session management (eggsm)              yes
  XSPF playlists                          yes

  SSE2:                                   yes
  AltiVec:                                no

---

### Post by zika on 2009-05-27
Is there in WWW world .deb of Audacious 2.01 (whatever is the number for the newest version) for 64-bit Jaunty?
Thank You in advance ... :)

---

### Post by super.rad on 2009-05-27
I've had a search around and can't find one. Not even in karmic repo's yet

---

### Post by zika on 2009-05-28
What is the penalty if I force architecture to 32-bit in this case ... ?

update: it messed things up badly, it took me some time to recover 1.5.1 ... not recommended ... :)

---

### Post by JoZ3 on 2009-05-31
check the PPA by [dupondje]("http://ubuntuforums.org/member.php?u=465590"):

deb [http://ppa.launchpad.net/dupondje/ppa/ubuntu](http://ppa.launchpad.net/dupondje/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/dupondje/ppa/ubuntu](http://ppa.launchpad.net/dupondje/ppa/ubuntu) jaunty main

---

### Post by zika on 2009-05-31
> **JoZ3 said:**
> check the PPA by [dupondje]("http://ubuntuforums.org/member.php?u=465590"):

deb [http://ppa.launchpad.net/dupondje/ppa/ubuntu](http://ppa.launchpad.net/dupondje/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/dupondje/ppa/ubuntu](http://ppa.launchpad.net/dupondje/ppa/ubuntu) jaunty main
Cool! Thank You, I've installed it and now I have to check it out ... :)

---

### Post by BopNiblets on 2009-06-05
Any Last.fm for this version?

I see the xmms2-scrobbler in Package Manager, would that work?

Also, I just noticed it doesn't scroll to the song in the playlist when it's played, if I'm at the top of the playlist and it starts on a new song at the bottom, it stays showing the top... :(

---

### Post by logos34 on 2009-06-05
does the older crossfade-plugin work with it?

---

### Post by Xylar Wasterend on 2009-06-11
Been trying to compile Audacious 2.0.1 from source, finding one library after another, with no luck. In spite of using the [fix from the FAQ page for libmowgli]("http://audacious-media-player.org/faq#id23"), it still gives me the error.

```
skyalmian@alcyone:~/Desktop$ export PKG_CONFIG_PATH="/usr/X11R6/lib/pkgconfig:/usr/local/lib/pkgconfig:/usr/lib/pkgconfig"
skyalmian@alcyone:~/Desktop$ cd audacious-2.0.1
skyalmian@alcyone:~/Desktop/audacious-2.0.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether we need an implib... no
checking for shared library system... GNU
checking if you are running Apple-GCC... no
checking whether make sets $(MAKE)... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ranlib... ranlib
checking for strerror in -lcposix... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for feof_unlocked... yes
checking for fgets_unlocked... yes
checking for getc_unlocked... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for style of include used by make... GNU
checking for GNU make... make
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of gcc... none
checking for strerror in -lcposix... (cached) no
checking whether byte ordering is bigendian... no
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for rm... /bin/rm
checking for mv... /bin/mv
checking for cp... /bin/cp
checking for ar... /usr/bin/ar
checking for tr... /usr/bin/tr
checking for ranlib... /usr/bin/ranlib
checking for GLIB... yes
checking for GTHREAD... yes
checking for GTK... yes
checking for PANGO... yes
checking for CAIRO... yes
checking for MOWGLI... no
configure: error:
Cannot find libmowgli! If you are using binary packages based system, check that you
have the corresponding -dev/devel packages installed.
http://www.atheme.org/projects/mowgli.shtml
```[quote="Audacious FAQ"]You probably installed to /usr/local. This means that the pkg-config metadata for those libraries were also installed to /usr/local. The following code will provide a hint to pkg-config as where it can find the SDKs for those libraries:[/quote]
Only, it didn't put it in /usr/local. libmowgli's installed files:
```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libmowgli1
/usr/share/doc/libmowgli1/copyright
/usr/share/doc/libmowgli1/changelog.Debian.gz
/usr/lib
/usr/lib/libmowgli.so.1.0.0
/usr/lib/libmowgli.so.1
```

---

### Post by foogoo on 2009-06-18
Did anyone else have a problem getting ALSA to work with 2.0.1? I installed the plugins without error but ALSA refuses to show up as an output option. Worked fine with 1.5.1.

It also decided out of the blue to start opening multiple instances for every file I double-clicked on in nautilus, despite having the "allow_multiple_instances" value in the config set to FALSE.

---

### Post by flapane on 2009-06-26
To the developer or someone other:
Notice me by mail or pm whenever 2.1 has become stable, and I'll compile it as usual, on Hardy i386.

---

### Post by philip5 on 2009-07-09
I have (among a bunch of other updated packages) the latest 2.1.0 version (for the moment) of Audacious and the plugins pack on my repo for ubuntu 9.04 (jaunty) for anyone who like to give it a try.

You find my repo at the url in my signature and at the site you also find instructions on how to add the repo if you have any problems with that.

Have fun!

---

### Post by zika on 2009-07-09
2.1.0 from dupondje ppa works great on Karmic ... :)

---

### Post by flapane on 2009-07-13
> **Kosimo said:**
> Hello Guys, 
Audacious has quietly released the first alpha of the 2.x series. It doesn't have a change log and the only thing we know is that there is a new skinned skin compatibility and audio improvements. 

Get it here: [http://audacious-media-player.org/](http://audacious-media-player.org/)


Edit: Finally is stable! 

Here the .deb's created by Flavio!

**[Audacious 2.0.1-Stable.deb]("http://www.flapane.com/unixmac/Ubuntu/audacious_2/audacious_2.0.1-1_i386.deb")**

**[Audacious 2.0.1-Stable Plugins.deb]("http://www.flapane.com/unixmac/Ubuntu/audacious_2/audacious-plugins_2.0.1-1_i386.deb")**


Fresh debs of 2.1 for Hardy, as usual at nix.flapane.com !

---

