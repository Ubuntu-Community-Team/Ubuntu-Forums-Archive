---
title: "Backport GnuCash 3.x from Debian to Bionic"
date: 2019-09-23
forum: Repositories &amp; Backports
---

### Post by Tommy on 2019-09-23
I have been trying to learn enough about packaging to get the latest GnuCash from Debian (bullseye / buster) to build on Bionic. UNFORTUNATELY it is quite challenging. 

I want to be able to produce a package that will build in a PPA or a clean Bionic sbuild SO I have a bunch of VirtualBox VMs and a couple of sbuild chroots set up to test various things. Unfortunately I also know very little about this.

I have started several times over the past year, but I will describe one procedure that should be straightforward.

Because I'm coming from Debian, I thought it might be useful to have Debian around....

Created a Debian 10 "buster" VM and set up sbuild ([older info]("https://wiki.ubuntu.com/SimpleSbuild")) ([newer info]("https://wiki.ubuntu.com/SecurityTeam/BuildEnvironment")) (The first wiki page is somewhat outdated so I also used part of the newer page.)

Create a local apt proxy using [COLOR=#333333]apt-cacher-ng.[/COLOR] 

Create a sid and a bionic chroot for sbuild.

In the Debian environment, create a directory and CD to it

```
$ cd ~/src/gnucash/bullseye37/
```

Go to [Debian Package Tracker]("http://tracker.debian.org/gnucash") and grab the latest GnuCash (currently version 3.7) [NOTE if you are following along in an Ubuntu environment, you'll want to install the debian-keyring package first]:

```
$ dget http://deb.debian.org/debian/pool/main/g/gnucash/gnucash_3.7-1.dsc
```

Verify that the package builds in sid (maybe half an hour on a moderately fast machine, unless you pre-loaded the dependencies, in which case it may be much faster). 

```
$ sbuild -Avs -d sid-amd64 gnucash_3.7-1.dsc
```

It builds fine in sid.  **HOWEVER**

```
sbuild -Avs -d bionic-amd64 gnucash_3.7-1.dsc
```

The package won't even try to build in bionic, so create a new version of the package. ( also committed the debian folder in to git just for practice.)

```
$ cd gnucash-3.7/debian
$ git init
$ git add .
$ git commit -a
$ dch --nmu 
```

Lower the version of debhelper in debian/control from 12 to 11 (because bionic doesn't have debhelper 12).

Here's where it gets much harder -- I can watch the package fail in bionic:


> $ sbuild -Avs -d bionic-amd64

dpkg-source: info: using options from gnucash-3.7/debian/source/options: --extend-diff-ignore=(^|/)(src/scm/build-config.scm)$
dh clean --buildsystem=cmake --with python3,aqbanking --builddirectory=.build
dh: unable to load addon python3: Can't locate Debian/Debhelper/Sequence/python3.pm in @INC (you may need to install the Debian::Debhelper::Sequence::python3 module) (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.28.1 /usr/local/share/perl/5.28.1 /usr/lib/x86_64-linux-gnu/perl5/5.28 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.28 /usr/share/perl/5.28 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) at (eval 12) line 1.
BEGIN failed--compilation aborted at (eval 12) line 1.

make: *** [debian/rules:33: clean] Error 2
E: Failed to clean source directory /home/twt/src/gnucash/bullseye37/gnucash-3.7 (/home/twt/src/gnucash/bullseye37/gnucash_3.7-1~01.dsc)
$ 


**NOTE** I also have a "normal" Bionic VM and the package fails to build in a completely different way. But for now let's stick with sbuild....

My first thought is maybe somehow the package is missing dh-python (which includes the python3 module for debhelper). But NO -- dh-python is a dependency right there near the top of debian/control.

**Red herring?**
After lots and lots of Google and DuckDuckGo searches I found a possibly relevant bug:

The version of [boost in Bionic]("https://bugs.launchpad.net/ubuntu/+source/cmake/+bug/1831869") [has a bug]("https://github.com/boostorg/python/issues/204") where it cannot "see" [the correct python headers]("https://gitlab.kitware.com/cmake/cmake/merge_requests/201"), but that bug was [fixed in later versions]("https://gitlab.kitware.com/cmake/cmake/issues/18030")


I'm pretty sure most folks who hit this bug just find a way to upgrade the buggy library so they can build, but my goal has been to get it to build in "clean" Bionic. I figure I can do anything to the source code or the debian package commands, but I don't know what to try.

---

### Post by Tommy on 2019-09-23
For fun, I just created a minimal Bionic VM. (Minimal Xubuntu environment)

Similar process to above...

```
$ sudo apt install virtualbox-guest-dkms
$ sudo apt install virtualbox-guest-x11
$ sudo apt install devscripts build-essential
$ sudo apt-get build-dep gnucash
$ sudo apt install debian-keyring
```
[unmet dependencies because Bionic has GnuCash 2.x]
```
$ sudo apt install cmake googletest libboost-dev libboost-date-time-dev libboost-filesystem-dev libboost-locale-dev libboost-regex-dev libgtk-3-dev libgwengui-gtk3-dev libwebkit2gtk-4.0-dev python3-dev swig texinfo 
```

try to build

```
$ dpkg-buildpackage
```

starts pretty well, then 

> 
/usr/bin/cmake -E cmake_link_script CMakeFiles/cmTC_18613.dir/link.txt --verbose=1
/usr/bin/cc -g -O2 -fdebug-prefix-map=/home/twt/src/dch37/gnucash-3.7=. -fstack-protector-strong -Wformat -Werror=format-security -Wdate-time -D_FORTIFY_SOURCE=2   -Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-z,now  CMakeFiles/cmTC_18613.dir/feature_tests.c.o  -o cmTC_18613 
make[3]: Leaving directory '/home/twt/src/dch37/gnucash-3.7/.build/CMakeFiles/CMakeTmp'
make[2]: Leaving directory '/home/twt/src/dch37/gnucash-3.7/.build/CMakeFiles/CMakeTmp'

    Feature record: C_FEATURE:1c_function_prototypes
    Feature record: C_FEATURE:0c_restrict
    Feature record: C_FEATURE:0c_static_assert
    Feature record: C_FEATURE:0c_variadic_macros
    cd .build && tail -v -n \+0 CMakeFiles/CMakeError.log
==> CMakeFiles/CMakeError.log <==
Compiling the CXX compiler identification source file "CMakeCXXCompilerId.cpp" failed.
Compiler: /usr/bin/c++ 
Build flags: -g;-O2;-fdebug-prefix-map=/home/twt/src/dch37/gnucash-3.7=.;-fstack-protector-strong;-Wformat;-Werror=format-security;-Wno-error=stringop-truncation;-Wdate-time;-D_FORTIFY_SOURCE=2
Id flags:  

The output was:
1
[B]cc1plus: error: -Werror=stringop-truncation: no option -Wstringop-truncation
[/B]
Compiling the CXX compiler identification source file "CMakeCXXCompilerId.cpp" failed.
Compiler: /usr/bin/c++ 
Build flags: -g;-O2;-fdebug-prefix-map=/home/twt/src/dch37/gnucash-3.7=.;-fstack-protector-strong;-Wformat;-Werror=format-security;-Wno-error=stringop-truncation;-Wdate-time;-D_FORTIFY_SOURCE=2
Id flags: -c 

The output was:
1
[B]cc1plus: error: -Werror=stringop-truncation: no option -Wstringop-truncation
[/B]
Compiling the CXX compiler identification source file "CMakeCXXCompilerId.cpp" failed.
Compiler: /usr/bin/c++ 
Build flags: -g;-O2;-fdebug-prefix-map=/home/twt/src/dch37/gnucash-3.7=.;-fstack-protector-strong;-Wformat;-Werror=format-security;-Wno-error=stringop-truncation;-Wdate-time;-D_FORTIFY_SOURCE=2
Id flags: --c++ 

The output was:
1
[B]c++: error: unrecognized command line option &#8216;--c++&#8217;
[/B]
Compiling the CXX compiler identification source file "CMakeCXXCompilerId.cpp" failed.
Compiler: /usr/bin/c++ 
Build flags: -g;-O2;-fdebug-prefix-map=/home/twt/src/dch37/gnucash-3.7=.;-fstack-protector-strong;-Wformat;-Werror=format-security;-Wno-error=stringop-truncation;-Wdate-time;-D_FORTIFY_SOURCE=2
Id flags: --ec++ 

The output was:
1
[B]c++: error: unrecognized command line option &#8216;--ec++&#8217;; did you mean &#8216;-Weffc++&#8217;?
[/B]
Determining if the CXX compiler works failed with the following output:
Change Dir: /home/twt/src/dch37/gnucash-3.7/.build/CMakeFiles/CMakeTmp

Run Build Command:"/usr/bin/make" "cmTC_6e359/fast"
make[2]: Entering directory '/home/twt/src/dch37/gnucash-3.7/.build/CMakeFiles/CMakeTmp'
/usr/bin/make -f CMakeFiles/cmTC_6e359.dir/build.make CMakeFiles/cmTC_6e359.dir/build
make[3]: Entering directory '/home/twt/src/dch37/gnucash-3.7/.build/CMakeFiles/CMakeTmp'
Building CXX object CMakeFiles/cmTC_6e359.dir/testCXXCompiler.cxx.o
/usr/bin/c++    -g -O2 -fdebug-prefix-map=/home/twt/src/dch37/gnucash-3.7=. -fstack-protector-strong -Wformat -Werror=format-security -Wno-error=stringop-truncation -Wdate-time -D_FORTIFY_SOURCE=2    -o CMakeFiles/cmTC_6e359.dir/testCXXCompiler.cxx.o -c /home/twt/src/dch37/gnucash-3.7/.build/CMakeFiles/CMakeTmp/testCXXCompiler.cxx
cc1plus: error: -Werror=stringop-truncation: no option -Wstringop-truncation
CMakeFiles/cmTC_6e359.dir/build.make:65: recipe for target 'CMakeFiles/cmTC_6e359.dir/testCXXCompiler.cxx.o' failed
make[3]: *** [CMakeFiles/cmTC_6e359.dir/testCXXCompiler.cxx.o] Error 1
make[3]: Leaving directory '/home/twt/src/dch37/gnucash-3.7/.build/CMakeFiles/CMakeTmp'
Makefile:126: recipe for target 'cmTC_6e359/fast' failed
make[2]: *** [cmTC_6e359/fast] Error 2
make[2]: Leaving directory '/home/twt/src/dch37/gnucash-3.7/.build/CMakeFiles/CMakeTmp'


dh_auto_configure: cd .build && cmake .. -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_VERBOSE_MAKEFILE=ON -DCMAKE_BUILD_TYPE=None -DCMAKE_INSTALL_SYSCONFDIR=/etc -DCMAKE_INSTALL_LOCALSTATEDIR=/var -DCMAKE_EXPORT_NO_PACKAGE_REGISTRY=ON -DCMAKE_FIND_PACKAGE_NO_PACKAGE_REGISTRY=ON -DCMAKE_INSTALL_RUNSTATEDIR=/run -Wdev -DCMAKE_VERBOSE_MAKEFILE=ON -DCMAKE_BUILD_TYPE=Release "-DCMAKE_CXX_FLAGS=-g -O2 -fdebug-prefix-map=/home/twt/src/dch37/gnucash-3.7=. -fstack-protector-strong -Wformat -Werror=format-security -Wno-error=stringop-truncation -Wdate-time -D_FORTIFY_SOURCE=2" -DWITH_PYTHON=ON -DCMAKE_INSTALL_LIBDIR=/usr/lib/x86_64-linux-gnu/gnucash returned exit code 1
debian/rules:45: recipe for target 'override_dh_auto_configure' failed
make[1]: *** [override_dh_auto_configure] Error 255
make[1]: Leaving directory '/home/twt/src/dch37/gnucash-3.7'
debian/rules:33: recipe for target 'build' failed
[B]make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build subprocess returned exit status 2
[/B]twt@BionicMinimalVM:~/src/dch37/gnucash-3.7$ 


---

### Post by acheronuk on 2019-09-27
debhelper 12 is in bionic backports, so there is no need to lower that build requirement if you build in a env with that repo enabled (sbuild/PPA etc).

If you inspect the debian changelog, you will see the entry:

Build with "-Wno-error=stringop-truncation" to fixed FTBFS with GCC-9

which tallies with your later errors. Bionic has GCC-7 which will not know about that option from later GCC. If in debian/rules you comment out the line:

export DEB_CXXFLAGS_MAINT_APPEND= -Wno-error=stringop-truncation

then things might build.

---

### Post by Tommy on 2019-09-28
That's excellent! Thank you so much for the helpful suggestions! 

My goal is to create a package that's buildable and usable in a Bionic or Bionic-derived system, probably also including "child" distros like Mint. 

How do I indicate the package requires backported packages to build (or run) **besides** specifying the dependency version numbers in the debian/control file? Or is that all?

I'm assuming I need to tinker with sbuild to tell it to use the backports repository. I know I can manually put files into the chroot's /etc/apt/sources.list.d and /etc/apt/preferences.d/ (to "pin" backports). Is that my only option or is there a command I should use (such as when I first set up the chroot)? 
EDIT: I somehow missed that nowadays backports are activated by default in Bionic. SO I don't need to worry with pinning.

When I get to the point of trying a PPA, what do I need to do to tell a PPA to load backports?

---

### Post by Tommy on 2019-10-01
Update: I've figured out how to add bionic-backports to the chroot (I wasn't able to get it to work when creating it so I manually added a bionic-backports.list file to /etc/apt/sources.list.d/ containing the two lines

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports main restricted universe multiverse


With a newly-generated sbuild chroot I was able to build a [patched cmake]("https://launchpad.net/~costamagnagianfranco/+archive/ubuntu/costamagnagianfranco-ppa/+packages") to fix [the bug I'm suspicious of]("https://bugs.launchpad.net/ubuntu/+source/cmake/+bug/1831869") but either that's not the problem or I have additional problems because I'm still stuck at the same place for the sbuild compile. 

Thank you again for the assistance; I'm making very slow progress.

---

### Post by Tommy on 2019-10-04
Today's update... after trying and trying I have finally worked through lots of permutations and realized a basic fact -- the clean command where the build fails MUST be looking in the dsc file for its initial debhelper setup. I was taking a huge shortcut as I worked through permutations... but having those parameters in the dsc is essential.

```
$ sbuild -Avs -d eoan-amd64 gnucash_3.7-1ubuntu1.dsc
```

I know this must seem pretty basic but it has stymied me for a week now...

EDIT: I still have not figured out how to get sbuild to pull debhelper from bionic-backports. That's the next challenge, I guess.
EDIT2: after lots of reading and head scratching / banging I realized I haven't seen anything build in a week SO I'm taking the eoan gnucash 3.7 package and trying and trying to get it to build on a clean eoan sbuild chroot... turns out I am still doing something wrong. 
sbuild -d eoan-amd64 gnucash_3.7-1ubuntu1.dsc
fails its tests with lots of warnings...
EDIT3: well it turns out the eoan package for gnucash CANNOT build (at the moment?) unless the eoan-proposed repository is active. I figured that out by looking at the build log in launchpad... !
EDIT4: even after adding eoan-proposed (and watching it pull in updated packages from that repository) it still fails just after the python tests.

---

### Post by Tommy on 2019-10-07
Is it just me, or does the latest eoan package of GnuCash 3.7 not build even in an eoan build environment? 

I have tried sbuild in eoan and disco and today I tried pbuilder just in case I'm doing something wrong, and in both cases it gets a good start and builds for many minutes but then fails at least one of the tests. Next I'm going to try again with a fresh copy of the source package, but I've been getting it from launchpad so that should be good, right?

---

### Post by acheronuk on 2019-10-07
It builds on launchpad (or did a few days ago).

[https://launchpad.net/~rikmills/+archive/ubuntu/bionic/+sourcepub/10572002/+listing-archive-extra](https://launchpad.net/~rikmills/+archive/ubuntu/bionic/+sourcepub/10572002/+listing-archive-extra)

---

### Post by Tommy on 2019-10-08
> **acheronuk said:**
> It builds on launchpad (or did a few days ago).

[https://launchpad.net/~rikmills/+archive/ubuntu/bionic/+sourcepub/10572002/+listing-archive-extra](https://launchpad.net/~rikmills/+archive/ubuntu/bionic/+sourcepub/10572002/+listing-archive-extra)

Thanks for the pointer. I'm going to go on a little rant (explanation) here, partly for me... ;-)

I WAS able to build a few days ago, too... SO I blew away my build chroots, and created a new debian sid one... 

```
$mk-sbuild sid
```
... (lots of lines)
```
Done building sid-amd64.

 To CHANGE the golden image: sudo schroot -c source:sid-amd64 -u root
 To ENTER an image snapshot: schroot -c sid-amd64
 To BUILD within a snapshot: sbuild -A -d sid-amd64 PACKAGE*.dsc
 To BUILD for : sbuild -A -d sid-amd64 --host  PACKAGE*.dsc

$ 
$ cd ~/src/gnucash/bullseye37
$ sbuild sid-amd64 gnucash_3.7-1.dsc
**Only one build is permitted**
$
```

:frown: "**Only one build is permitted**" was a new one to me. I found a few matching AskUbuntu topics with that message in their titles. And a Launchpad bug. But none of them seemed to be directly relevant. 
EXCEPT... they were talking about missing packages. I vaguely remembered noticing some sync issues with apt...

SO as a side-track I learned more about apt-cacher-ng. Helpfully when you use the mk-sbuild script the created sbuild chroots have the apt-cacher-ng proxiness inserted into the /etc/apt/apt.conf.d/ directory of every chroot. 

HOWEVER I was on a major sidetrack, trying pbuilder just in case it was an sbuild issue, and despite a couple of hours of kicking I could not get pbuilder to respect apt-cacher-ng completely -- pbuilder ALWAYS wants its own package cache. (This is annoying to me because I'm doing all this in a VM and you know how easy it is to fill up a virtual hard drive and how relatively hard it is to "virtually" install a larger one...) But even though I had messed around much of the day I still wasn't getting any successful builds with pbuilder OR sbuild.

But with that little hint I learned how to manage the apt caches in apt-cacher-ng -- I opened a browser into [http://127.0.0.1:3142/](http://127.0.0.1:3142/) and found the link low on the page to start managing its repo caches. I blew away all the funky ones I had created accidentally by putting weird apt lines into the various sbuild chroots; and I kicked at it for a few minutes until ... I still had ONE error in one of the eoan caches having to do with localization... so maybe the upstream repo was just stuck somehow. SO apt-cacher-ng has trouble updating then that trouble propagates to the chroots and then... 

Today I'm looking in apt-cacher-ng and it is having trouble with different repos from yesterday. But I'm just pruning things apt-cacher-ng can't verify. So there's less and less to check. I am hoping it will ultimately fix everything. I just need to be especially cognizant that sid and eoan are unstable at this time. (Well sid can be unstable any time, right?) ;-)

OH and there's a final missing piece above... for some reason a lot of the time you can get away with

sbuild [chroot] [package].dsc

HOWEVER it seems to be that when the chroot has a bad apt download in it, apparently you get the "Only one build is permitted" message. The "workaround"(?) is to be more explicit...

sbuild **-c** [chroot] [package].dsc

And the build will start and (seem to?) update the apt cache for the build and start building. Not that it necessarily SUCCEEDS... :-(

EDIT: And updating the chroot with sbuild-update does nothing to help the error...
```
$ sbuild-update -udcar sid-amd64
sid-amd64: Performing update.
Hit:1 http://deb.debian.org/debian sid InRelease
Reading package lists... Done
sid-amd64: Performing dist-upgrade.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sid-amd64: Performing clean.
sid-amd64: Performing autoclean.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sid-amd64: Performing autoremove.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sbuild sid-amd64 gnucash_3.7-1.dsc
Only one build is permitted
$ 
```

EDIT2: I deleted the sid chroot (using the commands in sbuild-destroychroot) and it still fails. The only problem I note on the newly-created chroot is that it complains that it doesn't set the locale. I'm not sure whether it has ever set the locale in an sbuild chroot.

```
Processing triggers for libc-bin (2.29-2) ...W: --force-yes is deprecated, use one of the options starting with --allow instead.
Hit:1 http://deb.debian.org/debian sid InRelease
Reading package lists... Done
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
0 value set
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
0 value set
Reading package lists... Done
```



At some point I may file a bug against sbuild about the unhelpfulness of the "**Only one build is permitted**" message. It might help if I knew just a bit more about how that happens...

---

### Post by Tommy on 2019-10-08
UPDATE: finally a successful "experimental" build -- I can build the Ubuntu eoan 3.7 package under Debian Buster. Now I'm hoping I can replicate the successful rikmills PPA build referenced above.

$ sbuild -c buster-amd64 gnucash_3.7-1ubuntu1.dsc
...

+------------------------------------------------------------------------------+
| Cleanup                                                                      |
+------------------------------------------------------------------------------+


Purging /<<BUILDDIR>>
Not cleaning session: cloned chroot in use


+------------------------------------------------------------------------------+
| Summary                                                                      |
+------------------------------------------------------------------------------+


Build Architecture: amd64
Build Type: binary
Build-Space: 1234724
Build-Time: 829
Distribution: bionic
Host Architecture: amd64
Install-Time: 382
Job: /home/twt/src/gnucash/eoan37/gnucash_3.7-1ubuntu1.dsc
Lintian: fail
Machine Architecture: amd64
Package: gnucash
Package-Time: 1232
Source-Version: 1:3.7-1ubuntu1
Space: 1234724
Status: successful
Version: 1:3.7-1ubuntu1
--------------------------------------------------------------------------------
Finished at 2019-10-08T16:21:40Z
Build needed 00:20:32, 1234724k disk space
$

---

### Post by Tommy on 2019-10-09
SO I created a new VM with bionic, copied Rik Mills' PPA version, and it built properly using dpkg-buildpackage (NOT sbuild or pbuilder)

Every attempt to build Ubuntu versions in the sbuild environment I was using failed in the tests phase. 

The Debian versions built properly; just not the Ubuntu versions. 

MAYBE because the VM was a Debian Buster VM???? I don't see why.....
There must be some weird things going on in the sbuild environments.

But I am going to take this as a success. I just want to replicate it with a "properly constructed" debian package.

---

### Post by Tommy on 2019-10-09
Here is a TESTED & WORKING procedure for building GnuCash 3.7 on Ubuntu Bionic

REQUIREMENTS
An Ubuntu Bionic installation with bionic-backports activated. (I used a minimal Xubuntu VM for this setup)

1) Create a source directory

```
$ mkdir bionic37
$ cd bionic37
```

2) Get the latest Ubuntu package

```
$ dget https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/gnucash/1:3.7-1ubuntu1/gnucash_3.7-1ubuntu1.dsc
```

2b) Move into the directory created by the source package

```
$ cd gnucash-3.7
```

3) Comment out a build flag line in debian/rules so it will build in Bionic

```
$ sed -i 's/export DEB_CXXFLAGS/#export DEB_CXXFLAGS/' debian/rules
```

4) Make this your custom version

```
$ dch --nmu
```

4b) Edit the new version at the top so it reads something like gnucash (1:3.7-1ubuntu18.04~1)

4c) Add a comment under your name saying something like "Commented out DEB_CXXFLAGS instruction in debian/rules"

4d) Save and exit the editor.

5) Upgrade debhelper

```
$ sudo apt install debhelper/bionic-backports
```

6) Build the package

```
$ dpkg-buildpackage
```

7) You will see the package files in the bionic37 directory, ready to install. 
```
$ sudo dpkg -i *.deb *.ddeb

$ sudo apt install -f

```

The dpkg -i command attempts to install gnucash .deb files and the .ddeb debugging files. In a fresh installation, the dpkg -i command will fail because of missing dependencies, so the second command will install the missing dependencies and finish installing gnucash.

---

### Post by Tommy on 2019-10-09
[B]I am still trying to figure out why I can't get sbuild to work.
[/B]
$ sudo apt install ubuntu-dev-tools sbuild apt-cacher-ng auto-apt-proxy

(the last one I haven't used before)

$ sudo adduser twt sbuild

log out and back in

$ mk-sbuild bionic

add backport to the build environment

$ sudo schroot -c source:bionic-amd64 -u root

(bionic-amd64) # cd /etc/apt/sources.list.d/ 
(bionic-amd64) # cat > bionic-backports.list

[paste the following two lines into the file, and then type ctrl-D]
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse

(bionic-amd64) # apt update ; apt upgrade
...
(bionic-amd64) # exit


Create a source directory

$ mkdir bionicSbuild
$ cd bionicSbuild

Get the latest Ubuntu package

$ dget [https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/gnucash/1:3.7-1ubuntu1/gnucash_3.7-1ubuntu1.dsc](https://launchpad.net/ubuntu/+archive/primary/+sourcefiles/gnucash/1:3.7-1ubuntu1/gnucash_3.7-1ubuntu1.dsc)

$ cd gnucash-3.7

Comment out a build flag line in debian/rules

$ sed -i 's/export DEB_CXXFLAGS/#export DEB_CXXFLAGS/' debian/rules

Make this a special version

$ dch --nmu

A: edit new version so it reads something like gnucash (1:3.7-1ubuntu18.04~sbuild)

B: add comment under your name saying something like "Commented out DEB_CXXFLAGS instruction in debian/rules"

C: save and exit the editor

$ sbuild --build-dep-resolver=aptitude -c bionic-amd64



**the package build fails lots of tests **

**Here are a few** (snippets below)

The following tests FAILED:
     60 - test-gnc-timezone (Failed)

3/127 Testing: test-print-parse-amount
3/127 Test: test-print-parse-amount
Command: "/<<PKGBUILDDIR>>/.build/bin/test-print-parse-amount"
Directory: /<<PKGBUILDDIR>>/.build/libgnucash/app-utils/test
"test-print-parse-amount" start time: Oct 09 19:28 UTC
Output:
----------------------------------------------------------
<WARNING> (qof) [gnc_numeric_mul()] Value too large to represent as int64_t
<WARNING> (qof) [gnc_numeric_mul()] Value too large to represent as int64_t
<WARNING> (qof) [gnc_numeric_mul()] Value too large to represent as int64_t
... about two dozen of these
<WARNING> (qof) [gnc_numeric_mul()] Value too large to represent as int64_t
Executed 6187 tests. All tests passed.
<end of output>
Test time =   0.03 sec
----------------------------------------------------------
----------------------------------------------------------
<CRITICAL> (gnc.engine) void xaccAccountSetCommodity(Account*, gnc_commodity*): assertion 'GNC_IS_COMMODITY(com)' failed
Executed 42 tests. All tests passed.
<end of output>
Test time =   0.03 sec
----------------------------------------------------------
OK
/qof/qofbook/shutting down: OK
/qof/qofbook/set get data: OK
/qof/qofbook/get collection: OK
/qof/qofbook/foreach collection: 
(/<<PKGBUILDDIR>>/.build/bin/test-qof:30951): gnc.engine-CRITICAL **: 19:28:37.310: void qof_book_foreach_collection(const QofBook*, QofCollectionForeachCB, gpointer): assertion 'book' failed

(/<<PKGBUILDDIR>>/.build/bin/test-qof:30951): gnc.engine-CRITICAL **: 19:28:37.310: void qof_book_foreach_collection(const QofBook*, QofCollectionForeachCB, gpointer): assertion 'cb' failed
OK
/qof/qofbook/set data finalizers: OK
/qof/qofbook/mark closed: OK

----------------------------------------------------------

/qof/gnc-date/gnc time64 to iso8601 buff: OK
/qof/gnc-date/gnc dmy2time64: <FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 1257-7-2: Year is out of valid range: 1400..10000
<FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 2017-2-29: Day of month is not valid for year
<FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 2017-2-33: Day of month value is out of range 1..31
<FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 2017-13-29: Month number is out of range 1..12
OK
/qof/gnc-date/gnc dmy2time64 end: <FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 1257-7-2: Year is out of valid range: 1400..10000
<FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 2017-2-29: Day of month is not valid for year
<FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 2017-2-33: Day of month value is out of range 1..31
<FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 2017-13-29: Month number is out of range 1..12
OK
/qof/gnc-date/gnc dmy2time64 Neutral: <FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 1257-7-2: Year is out of valid range: 1400..10000
<FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 2017-2-29: Day of month is not valid for year
<FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 2017-2-33: Day of month value is out of range 1..31
<FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 2017-13-29: Month number is out of range 1..12
OK
/qof/gnc-date/time64 to gdate: OK
/qof/gnc-date/gdate to time64: <FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 1257-7-2: Year is out of valid range: 1400..10000
<FATAL CRITICAL> (GLib) g_date_get_year: assertion 'g_date_valid (d)' failed
<FATAL CRITICAL> (GLib) g_date_get_month: assertion 'g_date_valid (d)' failed
<FATAL CRITICAL> (GLib) g_date_get_day: assertion 'g_date_valid (d)' failed
<FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 0-0-0: Day of month value is out of range 1..31
<FATAL CRITICAL> (GLib) g_date_get_year: assertion 'g_date_valid (d)' failed
<FATAL CRITICAL> (GLib) g_date_get_month: assertion 'g_date_valid (d)' failed
<FATAL CRITICAL> (GLib) g_date_get_day: assertion 'g_date_valid (d)' failed
<FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 0-0-0: Day of month value is out of range 1..31
<FATAL CRITICAL> (GLib) g_date_get_year: assertion 'g_date_valid (d)' failed
<FATAL CRITICAL> (GLib) g_date_get_month: assertion 'g_date_valid (d)' failed
<FATAL CRITICAL> (GLib) g_date_get_day: assertion 'g_date_valid (d)' failed
<FATAL WARNING> (qof.engine) [gnc_dmy2time64_internal()] Date computation error from Y-M-D 0-0-0: Day of month value is out of range 1..31
OK
/qof/gnc-date/gnc time64 get day start: OK
/qof/gnc-date/gnc time64 get day end: OK
/qof/qof-string-cache/string-cache: OK
<end of output>
Test time =   0.01 sec
----------------------------------------------------------



...........................................
----------------------------------------------------------------------
Ran 43 tests in 0.185s

OK
<end of output>
Test time =   0.39 sec
----------------------------------------------------------
Test Passed.
"python-bindings" end time: Oct 09 19:29 UTC
"python-bindings" time elapsed: 00:00:00
----------------------------------------------------------

End testing: Oct 09 19:29 UTC
+ exit 2
debian/rules:92: recipe for target 'override_dh_auto_test' failed
make[1]: *** [override_dh_auto_test] Error 2
make[1]: Leaving directory '/<<PKGBUILDDIR>>'
debian/rules:33: recipe for target 'build' failed
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build subprocess returned exit status 2
--------------------------------------------------------------------------------
Build finished at 2019-10-09T19:29:18Z

Finished
--------


+------------------------------------------------------------------------------+
| Cleanup                                                                      |
+------------------------------------------------------------------------------+

Purging /<<BUILDDIR>>
Not cleaning session: cloned chroot in use
E: Build failure (dpkg-buildpackage died)

+------------------------------------------------------------------------------+
| Summary                                                                      |
+------------------------------------------------------------------------------+

Build Architecture: amd64
Build Type: binary
Build-Space: n/a
Build-Time: 1055
Distribution: UNRELEASED
Fail-Stage: build
Host Architecture: amd64
Install-Time: 844
Job: /home/twt/src/bionicSbuild/gnucash_3.7-1ubuntu18.04~sbuild.dsc
Machine Architecture: amd64
Package: gnucash
Package-Time: 1908
Source-Version: 1:3.7-1ubuntu18.04~sbuild
Space: n/a
Status: attempted
Version: 1:3.7-1ubuntu18.04~sbuild
--------------------------------------------------------------------------------
Finished at 2019-10-09T19:29:18Z
Build needed 00:31:48, no disk space



EDIT: I assumed maybe I'm missing some major dependencies with sbuild so I tried the following but it failed in the same way:

$ sbuild --build-dep-resolver=aptitude -d bionic -c bionic-amd64 gnucash_3.7-1ubuntu18.04~sbuild.dsc

---

