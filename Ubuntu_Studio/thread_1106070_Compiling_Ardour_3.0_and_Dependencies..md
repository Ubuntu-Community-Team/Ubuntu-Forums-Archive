---
title: "Compiling Ardour 3.0 and Dependencies."
date: 2009-03-25
forum: Ubuntu Studio
---

### Post by jonobo on 2009-03-25
Ubuntu 7.04.

Okay - i'm running into trouble again and again while trying to install Ardour 3.0 Alpha from svn - actually i'm still stuck at the long list of requirements.

If anybody is interested please help me out ;)

I'm documenting the full process over here (still chaotic):
[http://ooommm.org/sudelwiki/index.php?title=Install_Ardour_3.0_svn_Version_on_Ubuntu_Feisty_Fawn_7.04](http://ooommm.org/sudelwiki/index.php?title=Install_Ardour_3.0_svn_Version_on_Ubuntu_Feisty_Fawn_7.04)

Okay - here we go with the first point where i'm stuck right now:

I need gtk+-2.0 >= 2.12.1.

I try to install gtk+-2.14.7, but that needs three other libraries/programs that i'm missing:

Requested 'glib-2.0 >= 2.17.6' but version of GLib is 2.12.11
Requested 'pango >= 1.20' but version of Pango is 1.16.2
Requested 'cairo >= 1.6' but version of cairo is 1.4.2

I installed glib-2.2.3 and that seems to have worked.

I try to install pango-1.2.5 and get this Error-Message:
```
checking for GLIB - version >= 2.1.3... 
*** 'pkg-config --modversion glib-2.0' returned 2.2.3, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** Glib 2.1.3 or better is required. The latest version of
*** Glib is always available from ftp://ftp.gtk.org/.
```

My little Error-Analysis:
[LIST]
[*]i installed a new glib version 5 minutes ago
[*]pkg-config returns new version
[*]but the program still finds the old GLIB 2.12.11
[LIST]
[*]which i can't uninstall because of lot#s of dependencies in synaptic package manager
[/LIST]
[*]so there is this LD_LIBRARY_PATH environment variable
[LIST]
[*]find out everything about it on ubuntu
[*]check /etc/ls.so.conf
[*]check ldconfig[/INDENT]
[/LIST]
[/LIST]

So to make a long story short - how do i get Pango running or how do i explain Pango where to find the right version of GLIB?

---

### Post by thorgal on 2009-03-25
hehe, you're forcing your luck ;)

listen, your 7.04 distro is far from being bleeding edge ... the ardour 3.0 code is the most bleeding edge you can think of. All your incremental manual library updates will sum up to one thing: a BIG dist-upgrade. I'm afraid you have only two options:

- stick to what you have or ...
- make a big dist-upgrade. I don't know about ubuntu too much, the only time I did it, it ****** up the whole OS (hardy to intrepid upgrade). I will never go ubuntu again :lol:

---

### Post by jonobo on 2009-03-25
Ha, thorgal again - you already worked enough today :]

Dist-Upgrade is not an option, because, i already changed this system way too much, i just started out with this Ubuntu 7.04 and it somehow grew into what i got now.

So you think the way to get this running is just looooong, or impossible?

Isn't there a way to have different versions of libraries at the same time? I guess i simply need to point something somehow - but i don't know what and how 'til now :]

But, yeah, i'm willing to waaaaaiiiiiiiiit for Ardour 3.0, and actually i don't even have the time now, because there iz production-work to do.

But, if there is a hint - let me have it :[]

---

### Post by thorgal on 2009-03-25
I am not saying it is IMPOSSIBLE, but it's a fight between way too many dependencies to go through, and your patience :D

I don't know ... maybe you could try (WARNING: this is a dangerous zone) :

```

sudo apt-get build-dep ardour

```

... I did not say anything ... :-\"

---

### Post by jonobo on 2009-03-25
Okay - i give myself 7 hours to solve that problem :]

Any help appreciated.

If i would try "sudo apt-get build-dep ardour" for which version of ardour would apt-get then try to solve the dependencies?   I guess for 0.99 or somethin ;) Correct me if i'm wrong.

I read something about LD_LIBRARY_PATH and shared libraries in general:
[http://www.techfak.uni-bielefeld.de/rechner/sharedlib.html](http://www.techfak.uni-bielefeld.de/rechner/sharedlib.html)
[http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html](http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html)

Okay, i begin to understand, slowly, i can have different versions of the same library at the same time, but the programs need to know where to find their desired version. In Ubuntu that can somehow be defined in the 
/etc/ld.so.conf
and after that i guess i have to run 
ldconfig 
to update aka to let the system know that there are new library-paths available

But i guess there might be some things like version-conflicts, like, how does a program X know which library-version to use, A or B. Questions over questions, but no giving up in sight.

Forum-Postings about Ubuntu & LD_LIBRARY_PATH:
* [http://ubuntuforums.org/showthread.php?t=13218](http://ubuntuforums.org/showthread.php?t=13218)

So i have to set the LD_LIBRARY_PATH in a way that the Pango-Configure-Script knows where to find the new GLIB-Version. Is that possible, if yes, how?

If not, what's the right way to tell the Pango-Configure-Script (and future other libraries and programs) where to find the new GLIB-Version?

Where is the new GLIB-Version anyway?
Gonna look for that right now.

---

### Post by jonobo on 2009-03-25
Okay - reduced to one question:

How do i find out into which directories "make install" copied the files to?

In this case:
tar xjvf glib-2.2.3.tar.bz2
cd glib-2.2.3/
./configure
make
sudo make install

---

### Post by thorgal on 2009-03-25
```

./configure --help | grep prefix

```

... you're wasting your time ... :)

---

### Post by jonobo on 2009-03-25
I love wasting time - for learning - but you are right, it is not very productive, but that doesn't matter right now - i want to understand.

I simply deinstalled and reinstalled glib and did a:
sudo make install > target.txt

So i could look up where the files did go.

Which lead me to this info:
```
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.

```

So glib-2.2.3 should be in /usr/local/lib

But if i understood right normally Linux looks only here for the Libraries by default:
/usr/lib 
/lib 

Maybe i'm wrong, but adding /usr/local/lib to /etc/ld.so.conf and running ldconfig couldn't do any harm, couldn't it?

I will know soon.

---

### Post by thorgal on 2009-03-25
you're right: get your hands dirty and learn :D
been through that kind of crap so long ago ... reminds me of the time I was compiling apps like mxaudio or xanim on sun solaris 2.4 ... I learned my lesson since then :)

---

### Post by jonobo on 2009-03-25
By the way, what is the essence of the lesson you learned and which OS are you using now?

So i made one step forward.

./configure of Pango runs through, but make spills Errors.

Doesn't seem to be my fault by now, but i'm not sure, something with freetype and a lot of other stuff.
```

jobo@ybox:~/pango-1.2.5$ make
make  all-recursive
make[1]: Entering directory `/home/jobo/pango-1.2.5'
Making all in pango
make[2]: Entering directory `/home/jobo/pango-1.2.5/pango'
Making all in opentype
make[3]: Entering directory `/home/jobo/pango-1.2.5/pango/opentype'
/bin/bash ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -DPANGO_ENABLE_ENGINE -DSYSCONFDIR=\"/usr/local/etc\" -DLIBDIR=\"/usr/local/lib\" -DG_DISABLE_DEPRECATED -DG_DISABLE_CAST_CHECKS -pthread -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include   -I/usr/include/freetype2  -I../..    -g -O2 -Wall -c ftxopen.c
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -DPANGO_ENABLE_ENGINE -DSYSCONFDIR=\"/usr/local/etc\" -DLIBDIR=\"/usr/local/lib\" -DG_DISABLE_DEPRECATED -DG_DISABLE_CAST_CHECKS -pthread -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/freetype2 -I../.. -g -O2 -Wall -c ftxopen.c  -fPIC -DPIC -o .libs/ftxopen.o
ftxopen.c:18:40: error: freetype/internal/ftstream.h: No such file or directory
ftxopen.c:19:40: error: freetype/internal/ftmemory.h: No such file or directory
ftxopen.c:20:39: error: freetype/internal/tttypes.h: No such file or directory
In file included from ftxopen.h:25,
                 from ftxopen.c:24:
/usr/include/freetype2/freetype/freetype.h:20:2: error: #error "`ft2build.h' hasn't been included yet!"
/usr/include/freetype2/freetype/freetype.h:21:2: error: #error "Please always use macros to include FreeType header files."
/usr/include/freetype2/freetype/freetype.h:22:2: error: #error "Example:"
/usr/include/freetype2/freetype/freetype.h:23:2: error: #error "  #include <ft2build.h>"
/usr/include/freetype2/freetype/freetype.h:24:2: error: #error "  #include FT_FREETYPE_H"
ftxopen.c: In function 'Load_LangSys':
ftxopen.c:44: warning: implicit declaration of function 'ACCESS_Frame'
ftxopen.c:47: warning: implicit declaration of function 'GET_UShort'
ftxopen.c:51: warning: implicit declaration of function 'FORGET_Frame'
ftxopen.c:55: warning: implicit declaration of function 'ALLOC_ARRAY'
ftxopen.c:55: error: expected expression before 'FT_UShort'
ftxopen.c:60: warning: implicit declaration of function 'FREE'
ftxopen.c:39: warning: unused variable 'memory'
ftxopen.c: In function 'Load_Script':
ftxopen.c:95: warning: implicit declaration of function 'FILE_Pos'
ftxopen.c:107: warning: implicit declaration of function 'FILE_Seek'
ftxopen.c:141: error: expected expression before 'TTO_LangSysRecord'
ftxopen.c:151: warning: implicit declaration of function 'GET_ULong'
ftxopen.c: In function 'Load_ScriptList':
ftxopen.c:225: error: expected expression before 'TTO_ScriptRecord'
ftxopen.c: In function 'Load_Feature':
ftxopen.c:322: error: expected expression before 'FT_UShort'
ftxopen.c:305: warning: unused variable 'memory'
ftxopen.c: In function 'Load_FeatureList':
ftxopen.c:374: error: expected expression before 'TTO_FeatureRecord'
ftxopen.c: In function 'Load_Lookup':
ftxopen.c:587: error: 'FALSE' undeclared (first use in this function)
ftxopen.c:587: error: (Each undeclared identifier is reported only once
ftxopen.c:587: error: for each function it appears in.)
ftxopen.c:603: error: expected expression before 'TTO_SubTable'
ftxopen.c:610: error: 'TRUE' undeclared (first use in this function)
ftxopen.c: In function 'Load_LookupList':
ftxopen.c:701: error: expected expression before 'TTO_Lookup'
ftxopen.c:703: error: expected expression before 'FT_UShort'
ftxopen.c: In function 'Load_Coverage1':
ftxopen.c:790: error: expected expression before 'FT_UShort'
ftxopen.c:774: warning: unused variable 'memory'
ftxopen.c: In function 'Load_Coverage2':
ftxopen.c:839: error: expected expression before 'TTO_RangeRecord'
ftxopen.c:823: warning: unused variable 'memory'
ftxopen.c: In function 'Load_ClassDef1':
ftxopen.c:1078: error: expected expression before 'FT_UShort'
ftxopen.c:1095: error: 'TRUE' undeclared (first use in this function)
ftxopen.c:1051: warning: unused variable 'memory'
ftxopen.c: In function 'Load_ClassDef2':
ftxopen.c:1144: error: expected expression before 'TTO_ClassRangeRecord'
ftxopen.c:1167: error: 'TRUE' undeclared (first use in this function)
ftxopen.c:1123: warning: unused variable 'memory'
ftxopen.c: In function 'Load_ClassDefinition':
ftxopen.c:1198: error: expected expression before 'FT_Bool'
ftxopen.c:1226: error: 'TRUE' undeclared (first use in this function)
ftxopen.c:1195: warning: unused variable 'memory'
ftxopen.c: In function 'Load_EmptyClassDefinition':
ftxopen.c:1243: error: expected expression before 'FT_Bool'
ftxopen.c:1247: error: 'FALSE' undeclared (first use in this function)
ftxopen.c:1249: error: expected expression before 'FT_UShort'
ftxopen.c:1240: warning: unused variable 'memory'
ftxopen.c: In function 'Load_Device':
ftxopen.c:1425: error: expected expression before 'FT_UShort'
ftxopen.c:1400: warning: unused variable 'memory'
make[3]: *** [ftxopen.lo] Error 1
make[3]: Leaving directory `/home/jobo/pango-1.2.5/pango/opentype'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jobo/pango-1.2.5/pango'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jobo/pango-1.2.5'
make: *** [all-recursive-am] Error 2

```

---

### Post by thorgal on 2009-03-25
the lesson I learned ? to avoid what you're doing :D :D

I used Sun Solaris for my work, some IRIX boxes as well at some point, well you know, unix in a time when linux was not yet ready for mass production ... then we decided to try out linux Slackware in my research group, tired of buying expensive licences for these commercial unices ... it was a weird time (kernel 1.x or so, I don't really remember). Anyway, it was a start ... 

there were funny compilation systems at the time, some home made makefiles you had to edit by hand, that depended on your compiler, architecture, etc. Then came the Imake system ... was great at the time ... but then eventually came the autotool stuff: horrible to set up as a package maintainer but as a user, it was great to have. It is still in use but nowadays, there are other things out there (scons, waf, cmake, etc).

So, about your attempt: compiling a bleeding edge software that requires bleeding edge tools and libraries on an already old-fashioned environment ... is just masochism to me :) that's the lesson you're learning now :D

Why don't you install a bleeding edge distro on a different disk partition ? the time you;re spending figuring out the dependencies will match or even surpass the time you install a new OS next to your older one.

Believe me, it's much more worth it than what you're trying to do :)

And you don't have to lose the old partition, you can keep it for the data you have already in it (home directory, etc). Just my advice ... I won't help you more on your compilation attempt ... maybe someone else can prove me wrong ? ... wait and see ...

---

### Post by jonobo on 2009-03-25
Okay - i give up.

One dependency after the other is screaming in my face and saying: STOP HERE!

Thanks thorgal for all the help, but it wasn't a complete waste.

At least i got a brand new JACK running fine.

I learned about the LD_LIBRARY_PATH, about checking where "make install" puts all the files and other stuff about shared libraries and about the respect we should pay to the people who developed things like "package management systems".

But one day, i'm gonna use Ardour 3.0, i already see it in my mind's eye, wonderful MIDI-Composing, i'm cooooooomiiiiiiiiiiiiing...

... damn it was just a dream.

Back to sample-based loop-cutting on Ardour 2.5 - but at least: Back to the Music. 

:guitar:

:popcorn:

:KS:KS:KS

FIREWORK.

Where is the "Thread Solved"-Button? DOH!

---

### Post by thorgal on 2009-03-25
it was a courageous try ... even if a little naive :D
yeah, you learned a few things. 

By the way, that's why I always go for debian sid as a distro of choice. I regularly update it, I don't depend on the 6 months cycle Ubuntu imposes (Ubuntu does this for good reasons, but I don't feel I need this). Sure there are some ubuntu users that are using their OS like debian (since it's debian based :) ).

I have ardour 3.0 compiled somewhere on my HD (I don't install it, no no no! it would just be a mistake, instead, I use the ardev script Paul Davis prepared for precisely testing new versions without having to install them!). I have not tried it in a while now, but maybe I should update it one of these days, it's been a few months since I tried it.

Really, if you want to try out the newer versions of ardour (and other softs), just install another linux distro next to your older one. It wouldn't hurt at all, would it ? :)

---

### Post by jonobo on 2009-03-25
HD = Full.

But you are right, i could make some space somehow somewhere - and then master the comparedly easy task (i guess) of installing another Distribution, mabye a Debian, maybe just a new Ubuntu.

Another Hack on another Day.

Thanks again and back to the Beat.

Rock on!

:KS:guitar::KS

---

### Post by thorgal on 2009-03-26
> **jonobo said:**
> and then master the comparedly easy task (i guess) of installing another Distribution
compared to what you wanted to do above, it's a child's play! :D

so, time to clean up this over-filled HD :)

Cheers! and back to the music ... (I first have to get over a bad bronchitis ...)

---

