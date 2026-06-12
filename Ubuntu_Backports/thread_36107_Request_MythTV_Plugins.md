---
title: "Request: MythTV Plugins"
date: 2005-05-21
forum: Ubuntu Backports
---

### Post by crmanski on 2005-05-21
Hello,
I am testing out the MythTV package and noticed that the latest version is in backports  , but the plugins: mythvideo, mythphone, mythgallery, mythbrowser, mythdvd, mythgame, mythmusic, mythnews, mythweather, mythweb are still at the original hoary verions.  Could these be updated as well?

Thanks in advance.
crmanski

Edit:
I forgot to mention that there are packages here...
[http://dijkstra.csh.rit.edu/~mdz/debian/dists/unstable/mythtv/binary-i386/](http://dijkstra.csh.rit.edu/~mdz/debian/dists/unstable/mythtv/binary-i386/)
but I think because of naming convention they cause a conflict witht he backports version.

Preparing to replace mythvideo 0.17-1 (using mythvideo_0.18-3_i386.deb) ...
Unpacking replacement mythvideo ...
dpkg: dependency problems prevent configuration of mythvideo:
 mythvideo depends on mythtv-frontend (>= 0.18-1); however:
  Version of mythtv-frontend on system is 0.18-1~5.04ubp1.
 mythvideo depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 mythvideo depends on libqt3c102-mt (>= 3:3.3.4); however:
  Version of libqt3c102-mt on system is 3:3.3.3-7ubuntu3.
dpkg: error processing mythvideo (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

---

### Post by A-star on 2005-05-29
Supporting this request.
Backporting plugins would be really usefull.

---

### Post by chaumurky on 2005-05-31
[QUOTE=crmanski]Hello,
I am testing out the MythTV package and noticed that the latest version is in backports  , but the plugins: mythvideo, mythphone, mythgallery, mythbrowser, mythdvd, mythgame, mythmusic, mythnews, mythweather, mythweb are still at the original hoary verions.  Could these be updated as well?

Thanks in advance.
crmanski

Edit:
I forgot to mention that there are packages here...
[http://dijkstra.csh.rit.edu/~mdz/debian/dists/unstable/mythtv/binary-i386/](http://dijkstra.csh.rit.edu/~mdz/debian/dists/unstable/mythtv/binary-i386/)
but I think because of naming convention they cause a conflict witht he backports version.

Preparing to replace mythvideo 0.17-1 (using mythvideo_0.18-3_i386.deb) ...
Unpacking replacement mythvideo ...
dpkg: dependency problems prevent configuration of mythvideo:
 mythvideo depends on mythtv-frontend (>= 0.18-1); however:
  Version of mythtv-frontend on system is 0.18-1~5.04ubp1.
 mythvideo depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
 mythvideo depends on libqt3c102-mt (>= 3:3.3.4); however:
  Version of libqt3c102-mt on system is 3:3.3.3-7ubuntu3.
dpkg: error processing mythvideo (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:[/QUOTE]
 Damn, just realised that too. I wonder if removing version 0.18-1 and installing version 0.17-1 will bork my setup...

---

### Post by scoultas on 2005-06-05
I'd also be grateful if the MythPlugins packages were updated to 18-3.  I seem to have
MythVideo working by installing the debian version from [http://dijkstra.csh.rit.edu/~mdz/debian/dists/unstable/mythtv/binary-i386/](http://dijkstra.csh.rit.edu/~mdz/debian/dists/unstable/mythtv/binary-i386/), 
though I got the same errors as crmanski during installation.  Synaptic now considers this package to be 'broken'.  I tried changing my repositories to Breezy, in case this made a difference, but it didn't.  Still all the other plugins to go though!

---

### Post by jdong on 2005-06-05
Ok, I'll build these for Extras.

---

### Post by jdong on 2005-06-05
```

metaiomp4.cpp:207: error: 'struct mp4ff_callback_t' has no member named 'read'
metaiomp4.cpp:208: error: 'struct mp4ff_callback_t' has no member named 'seek'
metaiomp4.cpp: In member function `virtual int
   MetaIOMP4::getTrackLength(QString)':
metaiomp4.cpp:386: error: 'struct mp4ff_callback_t' has no member named 'read'
metaiomp4.cpp:387: error: 'struct mp4ff_callback_t' has no member named 'seek'
make[3]: *** [metaiomp4.o] Error 1
make[3]: Leaving directory `/home/jdong/ubp-compile-temp/mythplugins-0.18/mythmusic/mythmusic'
make[2]: *** [sub-mythmusic] Error 2
make[2]: Leaving directory `/home/jdong/ubp-compile-temp/mythplugins-0.18/mythmusic'
make[1]: *** [sub-mythmusic] Error 2
make[1]: Leaving directory `/home/jdong/ubp-compile-temp/mythplugins-0.18'
make: *** [build-stamp] Error 2
Build FAILED... 512
Do you want to rebuild w/o dep checks, or get a shell? [Y/s/n] ?n
Traceback (most recent call last):
  File "/usr/local/bin/ubp-build.py", line 270, in ?
    build()
  File "/usr/local/bin/ubp-build.py", line 170, in build
    raise Exception("Build command FAILED")
Exception: Build command FAILED

```

Doesn't like to build.

---

### Post by scoultas on 2005-06-05
JDong, I notice in the README for mythmusic source the following instructions : 

 __NB__: As of March 5, 2004, you can build and install FAAD2 v2.0
            final, but you must manually copy mp4ff_int_types.h from faad2/common/mp4ff/
            to your usr/local/include/ directory.

I searched for more information, and it appears that most faad2 distributions forget to put mp4ff_int_types.h anywhere, which is needed by mp4ff.h. 

Could you possibly try again, first copying this file?

Thanks,

Steven

---

### Post by jdong on 2005-06-06
Thanks for investigation. Can you file this as a bug report with Ubuntu? I can't make such changes at my end without causing a massive developer conflict ;)

---

### Post by scoultas on 2005-06-06
Raised as a bug - hope I've described it correctly : 

[https://bugzilla.ubuntu.com/show_bug.cgi?id=11548](https://bugzilla.ubuntu.com/show_bug.cgi?id=11548)

Does this mean the package cannot be built until a fix for this problem is made available?

Could the rest of the mythplugins could still be built by using 

./configure --disable-mythmusic     ?

---

### Post by chaumurky on 2005-06-07
[QUOTE=jdong]Thanks for investigation. Can you file this as a bug report with Ubuntu? I can't make such changes at my end without causing a massive developer conflict ;)[/QUOTE]


LOL! I hate politics!  :wink:

---

### Post by tr4veler on 2005-09-06
Any updates on getting the plugins to match Mythtv?  In breezy they are still at .17.

I tried to pin dijkstra.csh.rit.edu at 1000 and install from there but thouse packages require libnqc3c102-mt

*Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable*

Trying to pull libqc3c102 from debian and install; it results in

[I]dpkg: considering removing libqt3-mt in favour of libqt3c102-mt ...
dpkg: no, cannot remove libqt3-mt (--auto-deconfigure will help):
 libqt3-mt-mysql depends on libqt3-mt (>= 3:3.3.4)
  libqt3-mt is to be removed.
dpkg: regarding libqt3c102-mt_3.3.4-3_i386.deb containing libqt3c102-mt:
 libqt3c102-mt conflicts with libqt3-mt
  libqt3-mt (version 3:3.3.4-8ubuntu3) is installed.
dpkg: error processing libqt3c102-mt_3.3.4-3_i386.deb (--install):
 conflicting packages - not installing libqt3c102-mt
Errors were encountered while processing:
 libqt3c102-mt_3.3.4-3_i386.deb
[/I]

All I realy want is mythweb :-(

---

### Post by chaumurky on 2005-09-11
[QUOTE=tr4veler]
All I realy want is mythweb :-([/QUOTE]
 They're not in Breezy either. What's more, version 17 of the base files **aren't** in Breezy. :-(

---

### Post by leech on 2005-09-21
To get around the dependency on libqt3c102-mt you'll need to rebuild the packages, which is extremely easy, as long as you have the deb-src file for they mythtv packages, you can just do an 'apt-get build-dep <package name>' and then a 'apt-get source -b <package name>'  

I did this on my standard debian system.  Which I later on broke... now I'm reinstalling with Breezy.

Leech

---

### Post by tr4veler on 2005-09-23
Started to do that and you know what... Mythweb is updated to .18, sweet.  Thank you packagers!  Now all I need is the v.2 Air2PC drivers compiled into the stock kernal and I'll be out of the customizing business for a while   \\:D/

---

### Post by NeoFax on 2005-09-23
Apt-build does not work as it requires libmyth-0.17 which is not installed as 0.18.1 is.

---

### Post by SimonRowland on 2005-10-24
This is on a box with a Ubuntu 5.10 default install, MythTV, and very little else on it.

Mythgame and Mythvideo both need to have their dependencies updated to the libqt3-mt found in Ubuntu 5.10, instead of libqt3c102-mt.

In the future, perhaps an automated tool that searches for broken package dependencies might be useful?


root@shuttle:~# apt-get install mythgame 
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythgame: Depends: libqt3c102-mt (>= 3:3.3.3) but it is not installable
E: Broken packages


root@shuttle:~# apt-get install mythphone                               
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythphone: Depends: libestools1.2c102 but it is not installable
             Depends: libqt3c102-mt (>= 3:3.3.3) but it is not installable
E: Broken packages


root@shuttle:~# apt-get install libqt3c102-mt 
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate


root@shuttle:~# dpkg --list | grep libqt3-mt
ii  libqt3-mt                             3.3.4-8ubuntu5                       Qt GUI Library (Threaded runtime version), V
ii  libqt3-mt-mysql                       3.3.4-8ubuntu5                       MySQL database driver for Qt3 (Threaded)

---

