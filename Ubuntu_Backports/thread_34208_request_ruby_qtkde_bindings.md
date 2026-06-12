---
title: "request: ruby qt/kde bindings"
date: 2005-05-13
forum: Ubuntu Backports
---

### Post by jcs296 on 2005-05-13
The Qt and KDE bindings for Ruby (korundum and qtruby) are part of the official KDE bindings, but these are not in the Ubuntu repos.  I've had trouble compiling them myself, but I'm sure someone a bit more experienced than I could create it easily since they're in the other Debian repositories.  Thanks

---

### Post by ltmon on 2005-05-13
I just tried compiling qtruby with the ruby1.8 package in the repositories.  It compiled fine, but none of my ruby scripts could get past "require 'Qt'".

`require': No such file to load -- Qt (LoadError)

So I removed ruby1.8 and compiled 1.8.2 from the source on ruby-lang.org.  After this, however I couldn't compile qtruby-1.0.9 with this.

At this stage I gave up for now.

Let me know if you have any better success.

L.

---

### Post by jcs296 on 2005-05-14
I got it to work!  Turns out using the kdebindings package from kde.org did the trick. Downlad the current bindings from:
[http://download.kde.org/download.php?url=unstable/snapshots/kdebindings.tar.bz2](http://download.kde.org/download.php?url=unstable/snapshots/kdebindings.tar.bz2) 
This actually includes bindings for a bunch of other languages including python and java. Here are the instructions, I apologize if they are simplistic or overly explanatory, but I'm new to this.

In order to compile the ruby qt and kde bindings, unzip the file and cd into the created directory (called 'kdebindings-[date-of-package]')
in the top level directory, run './configure'  It'll tell you that you can't compile certan language bindings if you don't have the dependencies; the relevant packages I had installed are all listed at the bottom of this email.

after running ./configure in the base directory: 

for each of the 'smoke', 'qtruby' and 'korundum' directories (smoke must be first, qtruby and korundum can be in either order):
1) cd into the directory
2) (as root) make && make install

And it works.  I haven't gotten around to confirming korundum programs work, but it installed without errors.  And qtruby programs work.  


what I installed before running this (probably not all required):

ruby1.8 & dependencies for Ruby on Rails
libqt3-headers (3:3.3.3-7ubuntu3)
libqt3c102 (3:3.3.3-7ubuntu3)
automake1.6 (1.6.3-11)
kdevelop3 (4:3.2.0-0ubuntu1)
kdevelop3-data (4:3.2.0-0ubuntu1)
kdevelop3-plugins (4:3.2.0-0ubuntu1)
kdevelop3-doc (4:3.2.0-0ubuntu1)
qt3-doc (3:3.3.3-7ubuntu3)
qt3-designer (3:3.3.3-7ubuntu3)
automake1.9 (1.9.4-1)
g++ (4:3.3.5-1)
g++-3.3 (1:3.3.5-8ubuntu2)
libstdc++5-3.3-dev (1:3.3.5-8ubuntu2)
libx11-dev (6.8.2-10)
libxext-dev (6.8.2-10)
libxi-dev (6.8.2-10)
libxkbfile-dev (6.8.2-10)
x-dev (6.8.2-10)
zlib1g-dev (1:1.2.2-4ubuntu1)
qt3-dev-tools (3:3.3.3-7ubuntu3)
libqt3-mt-dev (3:3.3.3-7ubuntu3)
comerr-dev (2.1-1.35-8ubuntu2)
kdebase-dev (4:3.4.0-0ubuntu18)
kdelibs4-dev (4:3.4.0-0ubuntu3.1)
libqt3-mt-dev (3:3.3.3-7ubuntu3)

libaudio-dev (1.7-2ubuntu1)
libexpat1-dev (1.95.8-1)
libfontconfig1-dev (2.2.3-4ubuntu7)
libfreetype6-dev (2.1.7-2.3)
libice-dev (6.8.2-10)
libjpeg62-dev (6b-9)
liblcms1-dev (1.13-1)
libmng-dev (1.0.8-1)
libpng12-dev (1.2.8rel-1)
libsm-dev (6.8.2-10)
libxcursor-dev (1.1.3-1)
libxft-dev (2.1.2-6ubuntu1)
libxinerama-dev (6.8.2-10)
libxmu-dev (6.8.2-10)
libxrandr-dev (6.8.2-10)
libxrender-dev (0.9.0-0ubuntu4)
libxt-dev (6.8.2-10)
libxv-dev (6.8.2-10)
render-dev (0.9-0ubuntu1)
xlibmesa-gl-dev (6.8.2-10)
xlibmesa-glu-dev (6.8.2-10)
xlibs-static-dev (6.8.2-10)

---

### Post by ltmon on 2005-05-14
Good work jcs296.

I'm downloading now, and hope I have the same success.  Hopefully the bindings will be put into main for Breezy ... there are so many apps we can't use without them.

Cheers,

L.

---

### Post by jcs296 on 2005-05-14
It would be great if they were included... I don't know of any programs that use the ruby bindings, but if they aren't common there's no incentive to develop with them. Also, the korundum bindings function properly.

Good luck with your install,
Joe

---

### Post by ltmon on 2005-05-14
I got smoke compiled and installed, and I'm now trying with qtruby.  

Unfortunately I get a string of errors kicked of by

"can't find ruby.h"

Which would usually indicate to me that I need some kind of libruby-devel package.  Any idea what this package might be?

Cheers,

L.

EDIT: Silly me.  Found it.  ruby1.8-dev

EDIT Again: Still the same error.  Any ideas? :-?

---

### Post by ltmon on 2005-05-15
Well I finally installed Korundum by using a handful of packages from Debian testing.  I only had to do one "--force-depends" when installing libsmoke, as it depended on a minor revision of libc6 higher than that provided in Kubuntu, and I didn't want to upgrade such a major library.  It seems to work fine despite this.

For reference, you can get all the packages from [here](http://packages.debian.org/testing/source/kdebindings).

The packages I installed were:

libkorundum0-ruby1.8_3.3.2-1_i386.deb
libsmokekde1_3.3.2-1_i386.deb
libqt0-ruby1.8_3.3.2-1_i386.deb
libsmokeqt1_3.3.2-1_i386.deb
libruby1.8_1.8.2-7_i386.deb

The good news I guess is that Debian testing contains a working kdebindings section, and that the effort to put this into Breezy main or universe should hopefully be minimal.

Cheers,

L.

---

### Post by jcs296 on 2005-05-16
Good to hear that it worked - odd that mine worked and yours didn't...perhaps I had some random extra package installed that did the trick? In any case I appreciate the help with getting it to work, and it's good to hear that the binding will (likely) be in Breezy.  Now back to coding after the package management detour,

Joe

---

### Post by GeneralZod on 2005-07-21
I didn't see a denial from the backports team, so I wonder if it's still a candidate for backporting?

---

