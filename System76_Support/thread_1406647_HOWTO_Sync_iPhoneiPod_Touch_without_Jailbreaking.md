---
title: "HOWTO: Sync iPhone/iPod Touch without Jailbreaking"
date: 2010-02-14
forum: System76 Support
---

### Post by Lee_Machine on 2010-02-14
So I was checking out Google Buzz, and adding people to follow when I came across this thing called iFUSE, plus some other libraries such as libiphone, and libimobiledevice. It lets you browse through the filesystem, and sync audio files without having to jailbreak. I know this sounds too good to be true, but it works! :p

First a disclaimer, this in no way is as fast,or as manageable as iTunes. For example podcasts don't go in the podcast section. Also iFUSE is not considered stable yet. 

But it's a start....one that will have to start over when iPhone OS 4.0 comes out. 

So here is how...

    
Installing iFuse (for Ubuntu Karmic only)

Add the PPA

```
sudo add-apt-repository ppa:pmcenery/ppa

```

Update your system with the new files

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Now install all other dependencies.

```
sudo apt-get install gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 ifuse libgpod-dev libgpod-common libiphone0 libiphone-dev libimobiledevice0 libimobiledevice-dev libplist++1 libplist-utils python-plist libusb-1.0-0 libusb-1.0-0-dev libusbmuxd1 usbmuxd

```

Now you must add your user to the FUSE group. Replace username with your username.

```
useradd -G fuse username

```

Now just plug in your iPhone/iTouch and it will mount as two different things. A camera, and a cell phone, both of which will have icons on the desktop. 

To add songs you cannot just drag, and drop. You must use Rhythmbox. It will show up on the side pane as a device. You can add, or remove songs here. When done, it will auto sync.

Enjoy, and again iFUSE is not considered stable yet.  


Credits go to Paul McEnery, and all others who work on this project.

Further reading...

[http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)
[http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+MakeTechEasier+(Make+Tech+Easier](http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+MakeTechEasier+(Make+Tech+Easier))
[https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa)

---

### Post by Noah0504 on 2010-02-14
Hmm, I might have to look into this.  I just wish Apple wouldn't have to be such goons about their products.  Oh well, if anything, I might just keep my iPod Touch for the apps and portability and grab another iPod Classic for music.

---

### Post by eddietours on 2010-02-14
you can look into the Cowon MP it support most audio and video format I love it

---

### Post by Lee_Machine on 2010-02-14
> **Noah0504 said:**
> Hmm, I might have to look into this.  I just wish Apple wouldn't have to be such goons about their products.  Oh well, if anything, I might just keep my iPod Touch for the apps and portability and grab another iPod Classic for music.

True, when my iPhone contract ends in May I'm getting an Android phone.

---

### Post by kayvortex on 2010-02-15
The interesting thing about this is libimobiledevice0. According to aptitude:
> Package: libimobiledevice0
New: yes
State: not installed
Version: 0.9.7-1ubuntu1~ppa1
Priority: optional
Section: libs
Maintainer: Paul McEnery <pmcenery@gmail.com>
Uncompressed Size: 172k
Depends: libc6 (>= 2.8 ), libgcrypt11 (>= 1.4.2), libglib2.0-0 (>= 2.14.1),
         libgnutls26 (>= 2.7.14-0), libplist1, libtasn1-3 (>= 1.6-0),
         libusb-1.0-0 (>= 2:1.0.3), libusbmuxd1, libxml2 (>= 2.6.27)
[COLOR="Red"]Conflicts: libiphone0
Replaces: libiphone0[/COLOR]
Description: Library for communicating with Apple i mobile devices
 libimobiledevice is a library that talks the native Apple USB protocols that
 the Apple i mobile devices use. Unlike other projects, libimobiledevice does
 not depend on using any existing libraries from Apple.

I had already installed iFuse and the various libs used to access the iPhone, and when I tried to do a system update today aptitude was warning me of broken dependencies.
Doing a "aptitude --simulate full-upgrade" eventually leads to:
> The following NEW packages will be installed:
  libimobiledevice0{a} libusbmuxd1{a} 
The following packages will be REMOVED:
  libgcrypt11-dev{u} libgnutls-dev{u} libgpg-error-dev{u} libiphone-dev{a} 
  [COLOR="Red"]libiphone0{a} libplist-dev{u} libplist0{u}[/COLOR] libtasn1-3-dev{u} 
  [COLOR="Red"]libusb-1.0-0-dev{u} libusbmux-dev{u} libusbmux0{u}[/COLOR] 
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common flashplugin-installer 
  foomatic-filters ifuse libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 
  libcupsmime1 libcupsppdc1 libgpod-common libgpod4 libplist1 tor 
  tor-geoipdb 
18 packages upgraded, 2 newly installed, 11 to remove and 0 not upgraded.
Need to get 6,679kB of archives. After unpacking 5,386kB will be freed.

This is interesting. That's quite a few libs to remove that apparently were needed for iFuse to run. Perhaps they've just all been bundled into libimobiledevice0. The website for libimobiledevice is [here]("http://libimobiledevice.org/"), and it apparently supersedes the old wiki [here]("http://matt.colyer.name/projects/iphone-linux/"); so perhaps that's true.

Also, the old jonabeck repo seems to have the same packages as the PPA for Paul McEnery. I think I'll try to do an aptitude upgrade, with the repos as they are, replacing libiphone0 and see if I can still access my iPhone. So, if anyone else is in the same position and apprehensive, stay tuned...

---

### Post by darknexus85 on 2010-02-16
Hi
Libimobiledevice0 superceeds libiphone0, yes. Ignore libiphone0 and simply install libimobiledevice0 in its place and you should be fine. All of the packages now depend on libimobiledevice0 and run with that instead. I've got it working here with this setup and there doesn't seem to really be any issues apart from the usual caveats involving Apple devices and Linux.
One final note: I had to reboot my machine before this would allow me to transfer content to my iPhone 3gs. The reason is that the Dbus service needs to take in some new configurations, and for some reason simply telling Dbus to reload its configurations wouldn't do the trick for me. A total restart of Dbus, given how much Ubuntu depends on it even for service management now, is almost a reboot anyway so just rebooting was quicker.

hth

---

### Post by kayvortex on 2010-02-18
darknexus85: thanks for the info.

OK, not so straightforward, but not too much of a problem either. Letting aptitude resolve the complaints,
```
sudo aptitude full-upgrade
```
leads to:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages are BROKEN:
  libiphone-dev 
The following NEW packages will be installed:
  libimobiledevice0{a} libusbmuxd1{a} 
The following packages will be REMOVED:
  libiphone0{a} 
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common firefox firefox-3.5 
  firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support 
  flashplugin-installer foomatic-filters ifuse libcups2 libcupscgi1 
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libgpod-common 
  libgpod4 libplist-dev libplist1 libxml2 libxml2-dev libxml2-utils 
  python-libxml2 tor tor-geoipdb xulrunner-1.9.1 
  xulrunner-1.9.1-gnome-support 
30 packages upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 19.4MB of archives. After unpacking 160kB will be used.
The following packages have unmet dependencies:
  libiphone-dev: Depends: libiphone0 (= 0.9.4-1ubuntu3~k) but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
libiphone-dev

Score is 119

Accept this solution? [Y/n/q/?] 
The following NEW packages will be installed:
  libimobiledevice0{a} libusbmuxd1{a} 
The following packages will be REMOVED:
  libgcrypt11-dev{u} libgnutls-dev{u} libgpg-error-dev{u} libiphone-dev{a} 
  libiphone0{a} libplist-dev{u} libplist0{u} libtasn1-3-dev{u} 
  libusb-1.0-0-dev{u} libusbmux-dev{u} libusbmux0{u} 
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common firefox firefox-3.5 
  firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support 
  flashplugin-installer foomatic-filters ifuse libcups2 libcupscgi1 
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libgpod-common 
  libgpod4 libplist1 libxml2 libxml2-dev libxml2-utils python-libxml2 tor 
  tor-geoipdb xulrunner-1.9.1 xulrunner-1.9.1-gnome-support 
29 packages upgraded, 2 newly installed, 11 to remove and 0 not upgraded.
Need to get 19.4MB of archives. After unpacking 5,366kB will be freed.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libxml2-dev 2.7.5.dfsg-1ubuntu1.1 [826kB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main libplist1 1.1-0ubuntu1~ppa1 [18.2kB] 
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main libusbmuxd1 1.0.1-0ubuntu1~k [11.7kB]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main ifuse 0.9.7-1ubuntu1~ppa1 [11.5kB]   
Get:5 [http://deb.torproject.org](http://deb.torproject.org) karmic/main tor 0.2.1.23-2~karmic+1 [1,376kB]   
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main libimobiledevice0 0.9.7-1ubuntu1~ppa1 [43.3kB]
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main libgpod4 0.7.3+git20100203+teuf-master-0ubuntu1~ppa1 [263kB]
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main libgpod-common 0.7.3+git20100203+teuf-master-0ubuntu1~ppa1 [102kB]
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libxml2 2.7.5.dfsg-1ubuntu1.1 [868kB]
Get:10 [http://deb.torproject.org](http://deb.torproject.org) karmic/main tor-geoipdb 0.2.1.23-2~karmic+1 [803kB]
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libcups2 1.4.1-5ubuntu2.2 [219kB]
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libcupscgi1 1.4.1-5ubuntu2.2 [31.6kB]
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libcupsdriver1 1.4.1-5ubuntu2.2 [22.2kB]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libcupsimage2 1.4.1-5ubuntu2.2 [53.2kB]
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libcupsmime1 1.4.1-5ubuntu2.2 [15.5kB]
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libcupsppdc1 1.4.1-5ubuntu2.2 [60.1kB]
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main cups-common 1.4.1-5ubuntu2.2 [1,420kB]
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main cups-bsd 1.4.1-5ubuntu2.2 [36.7kB]
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main cups-client 1.4.1-5ubuntu2.2 [120kB]
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main cups 1.4.1-5ubuntu2.2 [1,909kB]
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main foomatic-filters 4.0.3-0ubuntu2.1 [145kB]
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main firefox-3.5-branding 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 [207kB]
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main xulrunner-1.9.1-gnome-support 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1 [47.8kB]
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main xulrunner-1.9.1 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1 [9,095kB]
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main firefox-3.5-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 [93.7kB]
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main firefox-3.5 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 [961kB]
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main firefox 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 [73.5kB]
Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main firefox-gnome-support 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 [73.4kB]
Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse flashplugin-installer 10.0.45.2ubuntu0.9.10.1 [19.6kB]
Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main libxml2-utils 2.7.5.dfsg-1ubuntu1.1 [89.5kB]
Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main python-libxml2 2.7.5.dfsg-1ubuntu1.1 [408kB]
Fetched 19.4MB in 46s (419kB/s)                                                 
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 195659 files and directories currently installed.)
Removing libiphone-dev ...
Removing libgnutls-dev ...
Removing libgcrypt11-dev ...
Removing libgpg-error-dev ...
Removing libplist-dev ...
Processing triggers for man-db ...
(Reading database ... 195574 files and directories currently installed.)
Preparing to replace libxml2-dev 2.7.5.dfsg-1ubuntu1 (using .../libxml2-dev_2.7.5.dfsg-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libxml2-dev ...
Preparing to replace libxml2 2.7.5.dfsg-1ubuntu1 (using .../libxml2_2.7.5.dfsg-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libxml2 ...
Preparing to replace libplist1 1.0-1ubuntu3~k (using .../libplist1_1.1-0ubuntu1~ppa1_amd64.deb) ...
Unpacking replacement libplist1 ...
Selecting previously deselected package libusbmuxd1.
Unpacking libusbmuxd1 (from .../libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb) ...
[COLOR="Red"]dpkg: error processing /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k[/COLOR]
Preparing to replace ifuse 0.9.4-1ubuntu3~k (using .../ifuse_0.9.7-1ubuntu1~ppa1_amd64.deb) ...
Unpacking replacement ifuse ...
Processing triggers for man-db ...
[COLOR="Red"]Errors were encountered while processing:
 /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:[/COLOR]
Setting up libxml2 (2.7.5.dfsg-1ubuntu1.1) ...

[COLOR="Red"]dpkg: dependency problems prevent configuration of ifuse:
 ifuse depends on libimobiledevice0; however:
  Package libimobiledevice0 is not installed.
 ifuse depends on libusbmuxd1; however:
  Package libusbmuxd1 is not installed.
dpkg: error processing ifuse (--configure):
 dependency problems - leaving unconfigured[/COLOR]
Setting up libplist1 (1.1-0ubuntu1~ppa1) ...

Setting up libxml2-dev (2.7.5.dfsg-1ubuntu1.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ifuse
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

Current status: 1 broken [+1], 25 updates [-5].

OK, so I try running:
```
sudo aptitude install -f
```
leading to:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  libimobiledevice0{a} libusbmuxd1{a} 
The following packages will be REMOVED:
  libiphone0{a} libplist0{u} libtasn1-3-dev{u} libusb-1.0-0-dev{u} 
  libusbmux-dev{u} libusbmux0{u} 
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common firefox firefox-3.5 
  firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support 
  flashplugin-installer foomatic-filters libcups2 libcupscgi1 
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libgpod-common 
  libgpod4 libxml2-utils python-libxml2 tor tor-geoipdb xulrunner-1.9.1 
  xulrunner-1.9.1-gnome-support 
The following partially installed packages will be configured:
  ifuse 
25 packages upgraded, 2 newly installed, 6 to remove and 0 not upgraded.
Need to get 0B/17.7MB of archives. After unpacking 1,909kB will be freed.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 195573 files and directories currently installed.)
Removing libiphone0 ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
hal start/running, process 23069
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 195568 files and directories currently installed.)
Unpacking libusbmuxd1 (from .../libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb) ...
[COLOR="Red"]dpkg: error processing /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k[/COLOR]
Selecting previously deselected package libimobiledevice0.
Unpacking libimobiledevice0 (from .../libimobiledevice0_0.9.7-1ubuntu1~ppa1_amd64.deb) ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
hal start/running, process 23198
[COLOR="Red"]Errors were encountered while processing:
 /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ifuse:
 ifuse depends on libusbmuxd1; however:
  Package libusbmuxd1 is not installed.
dpkg: error processing ifuse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libimobiledevice0:
 libimobiledevice0 depends on libusbmuxd1; however:
  Package libusbmuxd1 is not installed.
dpkg: error processing libimobiledevice0 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ifuse
 libimobiledevice0[/COLOR]
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

Current status: 2 broken [+1].

Hmm. I try:
```
sudo aptitude clean
sudo aptitude full-upgrade
```
thinking that there may be a problem with the downloaded .deb file, and even replacing the old jonabeck repo with the new ppa repo, but the problem persists.

The solution, in my case at least, is to remove ifuse and the packages that it depends on, and then do a full-upgrade again:
```
sudo aptitude purge ifuse
sudo aptitude full-upgrade
sudo aptitude install -f
sudo aptitude install ifuse
sudo aptitude install -f
```
**N.B.** The commands above will **only** work for package maintainer that is able to detect unused packages and automatically remove them, which *aptitude* is capable of. If you use *apt-get*, you will probably have to select all the packages that it tried to remove manually and remove them yourself before installing any other packages.

OK then. Aptitude now finishes fine without encountering any problems. If your reading this, then your probably more concerned about whether gtkpod still works: I'll leave any Rythmbox issues (and any general Apple complaints, like darknexus85 already mentioned). Well, "sudo ifuse *mount_point*" now mounts the iphone filesystem readable only to root, which is undesirable since you'd now have to run "gksudo gtkpod" to read it.

The easiest solution is this: add yourself to the "fuse" group: System->Administration->Users and Groups. Click on "Click to make changes" to invoke root privileges. Then, locate the "fuse" group, Click on "Properties" and check the box next to your username. There's pictures on what to do [here]("http://maketecheasier.com/sync-iphone-with-rhythmbox/2010/02/13?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+MakeTechEasier+%28Make+Tech+Easier"). The advantage of doing this is that you no longer need to invoke root privileges to mount your iphone.
Next, run (you can change "/mnt/iphone" to whatever you want):
```

sudo mkdir -vp /mnt/iphone
sudo chown -v *your_username*:fuse /mnt/iphone

```
Now, you can run:
```

ifuse /mnt/iphone

```
and run gtkpod as normal. I've tried using gtkpod and tried to sync my iphone, and it works OK as it did before. Post if you have any problems and I, or someone here, will try to help.

---

### Post by jdb on 2010-02-18
> **kayvortex said:**
> 

**N.B.** The commands above will **only** work for package maintainer that is able to detect unused packages and automatically remove them, which *aptitude* is capable of. If you use *apt-get*, you will probably have to select all the packages that it tried to remove manually and remove them yourself before installing any other packages.



apt-get autoremove

will also remove unused packages.

You have to be careful with automatic removes though,
anything not installed with a package manager is removed.

This is what I get with that option:

```
10:10:33 /root apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cython dpatch gap gap-character-tables gap-core gap-dev gap-doc gap-guava
  gap-libs gap-online-help gap-prim-groups gap-small-groups gap-trans-groups
  genus2reduction gfan gfortran gfortran-4.4 global gmp-ecm gnuplot
  gnuplot-nox gnuplot-x11 graphviz groff ipython lcalc libamd2.2.0
  libatlas3gf-base libblas-dev libblas3gf libboost-python1.38.0 libbz2-dev
  libcdd-test libcdd0 libdsdp-5.8gf libecm0 libfftw3-3 libflint-1.011
  libfplll0 libgfortran3 libgivaro0 libglpk0 libgmp3-dev libgmpxx4ldbl libiml0
  liblapack-dev liblapack3gf liblinbox0 libm4ri-0.0.20080521 libmpfi0
  libncurses5-dev libnetpbm10 libntl-5.4.2 libpari2-gmp libpcre3-dev
  libpcrecpp0 libpolybori-0.5.0-0 libpolybori-dev libqd2c2a libreadline-dev
  libreadline6-dev libsingular-3-0-4-3 libsingular-dev libsymmetrica-2.0
  libumfpack5.4.0 libyaml-0-1 libzn-poly-0.8 linux-headers-2.6.31-17
  linux-headers-2.6.31-17-generic maxima maxima-share mercurial
  mercurial-common netpbm palp pari-extra pari-gp patchutils python-antlr
  python-cvxopt python-dateutil python-excelerator python-foolscap python-gd
  python-gnuplot python-gnutls python-matplotlib python-matplotlib-data
  python-moinmoin python-networkx python-numpy python-pexpect python-polybori
  python-processing python-pygraphviz python-pyparsing python-rpy python-scipy
  python-sqlalchemy python-sympy python-transaction python-twisted
  python-twisted-conch python-twisted-lore python-twisted-mail
  python-twisted-news python-twisted-runner python-twisted-web2
  python-twisted-words python-tz python-wxgtk2.8 python-wxversion python-yaml
  python-zc.lockfile python-zconfig python-zdaemon python-zodb
  python-zope.event python-zope.exceptions python-zope.proxy
  python-zope.testing python2.4 r-base r-base-core r-base-dev r-base-html
  r-base-latex r-cran-boot r-cran-cluster r-cran-codetools r-cran-foreign
  r-cran-kernsmooth r-cran-lattice r-cran-matrix r-cran-mgcv r-cran-nlme
  r-cran-rpart r-cran-survival r-cran-vr r-recommended scons singular sqlite3
  sympow tachyon
0 upgraded, 0 newly installed, 145 to remove and 0 not upgraded.
After this operation, 751MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

I almost did it by accident once :lolflag:

jdb

---

### Post by kayvortex on 2010-02-18
*jdb*: Thanks for the warning. I'm not an expert on package maintainer quirks, but I'd hope that issuing "apt-get autoremove package"/"aptitude purge package" would understand to only remove the unused dependencies for that package and not just everything. (That's an impressive almost-mistake! How did you install those packages, if you don't mind me asking? How far down the install toolchain does one have to go before the front-ends begin to make misunderstandings like that?)

In any case, I think a decent list of packages to remove would be: ifuse libplist0 libplist-dev libiphone0 libiphone0-dev libusbmux0 libusbmux-dev, since these are not packages likely to be used by anything other than an Apple device if you don't trust or can't use the auto-remove approach. However, to anyone wanting to follow any actions here, or anywhere else for that matter, heed *jdb*'s warning and always pay attention to the output of any particular program and amend your following actions accordingly (and ask if you don't know what to do next).

---

### Post by jdb on 2010-02-18
> **kayvortex said:**
> *jdb*: How did you install those packages, if you don't mind me asking?

Sage is a really cool math package that integrates almost all the good open source math apps.
It rivals Matlab which is a REALLY expensive program.

At any rate, I installed sagemath using synaptic & got a whole boatload of errors when I tried to use it.
After a little time on Google I found the fix was installing the whole thing from source.
It was very easy (untar it & run make) but it took a couple hours to complete.

Before I installed sage from source I removed sagemath and ran 'apt-get autoremove'.
I ran 'apt-get autoremove' a second time & it came back clean.

After I installed sage from source it worked perfectly but 'apt-get autoremove' gave me the output I posted before.


jdb

---

### Post by kayvortex on 2010-02-18
Wow, all those apps from source. That must have taken a bit of time!

Sage, eh? Hmm, that *might* have been useful had I known it existed half a year ago! I was doing Runge-Kutta numerics on classical dynamic systems in the complex plane. I had built a very quick C++ program doing the Runge-Kutta steps (GSL) and combined it with the MPFR library, but I couldn't find a library that took elliptic cn functions with complex arguments. In the end, I had to build an interface to the MATLAB kernel for the actual cn calculations (which was painfully slow and quite buggy), and had to *cough* *cough* "acquire" a version of Matlab...

Man, if only they opened Matlab up; I can only wonder what good it would do to academia!

---

### Post by jdb on 2010-02-18
> **kayvortex said:**
> 
Man, if only they opened Matlab up; I can only wonder what good it would do to academia!

Do a little googling on Sage, I think you'll be surprised at what it will handle and how fast it is.

jdb

---

### Post by kayvortex on 2010-02-18
> Do a little googling on Sage, I think you'll be surprised at what it will handle and how fast it is.

Thanks for the heads up: I'll check it out.

---

### Post by owenll on 2010-02-20
> **Lee_Machine said:**
> So I was checking out Google Buzz, and adding people to follow when I came across this thing called iFUSE, plus some other libraries such as libiphone, and libimobiledevice. It lets you browse through the filesystem, and sync audio files without having to jailbreak. I know this sounds too good to be true, but it works! :p
Thanks for this post, it is really appreciated. Transferring music to my iPod Touch was a nuisance as it was the only thing left I couldn't do in Ubuntu (recently got kdenlive to work for editing videos, that was my other reason for booting into XP partition).

Followed your instructions and they worked very well. Currently transferring files bought recently from AmazonMP3 to iPod Touch using Rhythmbox. :)

---

### Post by Scarfnoogan on 2010-02-20
This is great, but I'm having one small minor problem....

my music doesn't sync to the phone, I see the phone and the current playlist in Rhythmbox and I can add music to it, but it doesn't transfer to the phone, is there a setting I'm missing or something?

---

### Post by axmac on 2010-02-21
Excellent set of instructions, thanks. The original post plus the follow-ups allowed me to get my iphone (firmware 3.1.3) hooked up in 9.10.

My objective was syncing podcasts. I found that although gtkpod let me sync podcasts I'd already downloaded, it transferred them as regular music files. (They didn't appear in the podcast area of the iphone ipod app)

So I tried gPodder, which does all the nifty auto-download of feeds I want, plus syncs them to my iPhone as actual podcasts. Yay!

NB although I get two iphone devices when I connect my iphone, I have to ifuse in order for gtfpod/gpodder to acquire the iphone. Next step is to figure out how to get ifuse to run when the iphone is mounted, and disable one of the auto-mount drives I'm getting now. (Just one is enough for getting photos off, and they just clutter the side pane.)

---

### Post by LinuXGo on 2010-02-27
Hi, guys I've read your instructions about syncing the ipod touch to the computer using iFuse program but there's a minor problem that I encounter while completing the task of adding the music to my device. The sync is well done, its able to detect my device but I can't seem to add music to the device. I've installed rythmbox and I try to drag the folder to my device using the program but nothing happen. I click on the device tab on rythmbox and try to add music in it but there's nothing. How do I resolve this problem?

---

### Post by gazreen on 2010-03-12
Thank you very much Lee_Machine.. It works perfectly. The only mistake I made was choosing an iPhone. When my contract ends, I'll an android phone for sure.

---

### Post by superfrogman94 on 2010-03-12
Looks Like Lucid Will Support iPhone/iPod Touch Out Of The Box. :D

[http://www.webupd8.org/2010/02/confirmed-ubuntu-1004-supports-iphone.html](http://www.webupd8.org/2010/02/confirmed-ubuntu-1004-supports-iphone.html)

not only will you be able to open in nautilus but you will also be able to use Rhythmbox
to sync it.

---

### Post by antispin on 2010-03-12
That was a great HOWTO but probably worth noting that this will only work correctly if you don't have a passcode set on your iPhone.

As I discovered. Eventually. ;)

---

### Post by superfrogman94 on 2010-03-13
Actually i think it does work with a passcode, you just have to make sure its not locked when you want it to mount it

---

### Post by serlex on 2010-03-18
Followed as instructed, however when I connect my iphone 3gs, I'm only getting it as a camera :(

---

### Post by mathewd on 2010-04-20
I just bought an ipod touch with firmware 3.1.3, and while installing all the mentioned library files has allowed me to mount the ipod touch and remove photos/music from it, i'm unable to actually transfer files TO the ipod and have them read. they are physically on the ipod, but the device seems unable to read them.

for photos, the "Photos" app counts that i have the correct number of photos, but refuses to display them or acknowledge them with a thumbnail like the photos downloaded via wifi via the ipod.

for music, the touch (at least in 3.1.3?) has a wacky file system structure. music inside the itunes data storage is sorted into "F##" folders, each folder containing 3 song files. i dont know why the heck it does this unless specifically to prevent us from sending files over. needless to say, the music player on the ipod touch doesnt see the files at all.

so... how are those of you with the 3.1.3. firmware managing to get music/photos transferred to your iphones/ipod touches? 

thanks much for any info/suggestions

---

### Post by secretspicy15 on 2010-04-23
you're prolly going to have to use something like gtkpod to put stuff on there. i still have old (2.xx) firmware on mine, but it doest that thing with the F folders too; that's just the apple way of doing things.

you can't just drag music and drop it into the file structure. after mounting it with ifuse, then run gtkpod and you can transfer music with that. (supposedly all these otehr blokes can do it with rhythmbox too, but i've had no luck.) all this business about dragging and dripping music on is a bit misleading -- you DO drag and drop it, but that's WITHIN gtkpod or rhythmbox, NOT nautilus.

---

### Post by DeepThought42 on 2010-04-25
Hi,

this guide woked perfectly for me but I have one issue: Neither Rhythmbox nor gtkPod show my songs I've bought over iTunes unless I've connected the iPhone once with original iTunes after I've bought some songs.

Is there anyway to get this working?

---

### Post by jepong on 2010-04-27
has anyone implemented this on kubuntu and amarok?

---

### Post by jeff.nitt on 2010-04-28
Can someone help me get past this error:

The following packages have unmet dependencies:
  libimobiledevice-dev: Depends: libusbmuxd-dev but it is not going to be installed
E: Broken packages

---

### Post by thomasaaron on 2010-04-28
Open a terminal and run...

sudo apt-get install -f
sudo apt-get update
sudo apt-get --assume-yes dist-upgrade

Does that fix it?

---

### Post by jeff.nitt on 2010-04-29
Thanks but it did not work 
I tried to install the missing dev and this is the result

jeff@jeff-desktop:~$ sudo apt-get install libusbmux-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libusbmux-dev

---

### Post by thomasaaron on 2010-04-29
What version of Ubuntu are you running? 

Judging by the above posts, it sounds like it should be available in 9.10.I'm running 10.04, though, and can't find it in synaptic.

---

### Post by SupremeOverlord on 2010-04-29
I seem to be a little stuck here.  I have ubuntu 10.04 and I went through the steps above.  When I plug my iPod touch 3g in it mounts as an iPod.  When I run ifuse /media/iPod that works fine.  But gtkpod cannot load my iPod.  It says that it cannot read the database.  It appears in the sidebar of rhythmbox, but none of the songs on the iPod are listed.  When I try to drag a file onto it, nothing happens.  When I right click the icon for the iPod and try to view properties, rhythmbox crashes.  I have no idea where to go from here.  Is there anyone who can point me in the right direction? :confused:

---

### Post by jeff.nitt on 2010-05-02
It just updated to 10.04 but I get the same error

---

### Post by MyR on 2010-08-10
I would also like help with this.
I have an 8gb ipod touch 3rd generation 3.1.3 firmware

Ubuntu 9.10 ...

Does the ipod need to have an existing database? I haven't loaded anything on it yet.

---

