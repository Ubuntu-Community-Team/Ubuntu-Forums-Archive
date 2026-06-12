---
title: "Working of apt?"
date: 2010-01-15
forum: Ubuntu Dev Link Forum
---

### Post by kapmsd on 2010-01-15
Hi guys!!
I am doing a project in Ubuntu.
For my project,i need to know the working of Advanced Packaging Tool(apt)?
Where I can get the source code of apt?
Thanks in advance for ur inputs!!

---

### Post by andrewc6l on 2010-01-15
This is pretty meta:

```
apt-get install apt-src
```

You'll probably want to watch carefully to see where it installs the source to - probably somewhere like /usr/src/apt, but I'm not sure.

---

### Post by kapmsd on 2010-01-16
[COLOR="Yellow"][COLOR="Olive"]"Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl junit4 libxine1-x librdf0
  kdebase-runtime-data-common liblucene-java libgda3-common eclipse-rcp junit
  kdebase-runtime libxine1-misc-plugins kdelibs5 libxcb-xv0 libtext-glob-perl
  libqt4-qt3support libgdl-gnome-1-0 libswt3.2-gtk-java clamav-base
  libcarp-clan-perl kde-icons-oxygen libxine1-bin librasqal0 libclamav5
  libsoprano4 kdebase-runtime-bin-kde4 libxine1-ffmpeg libgmp3c2 libkonq5
  kdelibs5-data python-bittorrent libgif4 libxcb-shape0 libqt4-sql
  galeon-common libstreamanalyzer0 libphonon4 libmozjs0d libxine1-plugins
  libxvmc1 libkonq5-templates libgda3-3 libstreams0 libraptor1
  eclipse-platform liblucene-java-doc libxul-common libjsch-java
  libswt3.2-gtk-jni libxcb-shm0 kdebase-runtime-data kde4libs-bin
  libnumber-compare-perl libgdl-1-0 libbit-vector-perl libxine1-console
  libgdl-1-common libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev libapt-pkg-perl libtimedate-perl patch
Suggested packages:
  debian-keyring diff-doc
Recommended packages:
  fakeroot build-essential
The following NEW packages will be installed:
  apt-src dpkg-dev libapt-pkg-perl libtimedate-perl patch
0 upgraded, 5 newly installed, 0 to remove and 31 not upgraded.
Need to get 809kB of archives.
After this operation, 2523kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe libapt-pkg-perl 0.1.21build3 [87.9kB]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main patch 2.5.9-4 [95.6kB]
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe apt-src 0.25.1-0.1 [36.4kB]
Fetched 809kB in 4s (184kB/s)
Selecting previously deselected package libapt-pkg-perl.
(Reading database ... 150360 files and directories currently installed.)
Unpacking libapt-pkg-perl (from .../libapt-pkg-perl_0.1.21build3_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package apt-src.
Unpacking apt-src (from .../apt-src_0.25.1-0.1_all.deb) ...
Setting up libapt-pkg-perl (0.1.21build3) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up apt-src (0.25.1-0.1) ..."

[/COLOR][/COLOR]

I got this when running ur command.
I don know where the source file was installed????

---

### Post by cariboo on 2010-01-16
Look for the source in /usr/src. I have no idea what you plan on doing with the source, but wouldn't it be better if you started with something simple like:

```
man apt-get
```

---

### Post by kapmsd on 2010-01-16
I don have it in /usr/src.
My pjt is mainly abt system restore concept in linux.
I have already posted few threads reg this idea in this forum regarding the usefulness of my idea.
To start,
                I need to know how apt maintains a private DB in our sys,downloads the packages from the archives,check dependencies et al.
Waiting for ur inputs guys!!!

---

### Post by Penguin Guy on 2010-01-16
> **kapmsd said:**
> I don have it in /usr/src.
My pjt is mainly abt system restore concept in linux.
I have already posted few threads reg this idea in this forum regarding the usefulness of my idea.
To start,
                I need to know how apt maintains a private DB in our sys,downloads the packages from the archives,check dependencies et al.
Waiting for ur inputs guys!!!
Take a look in [COLOR="Green"]/var/cache/apt/archives[/COLOR] - that's where the private database is. As for how it checks dependancies:
```

Package: example-package
Version: 1.7-1
Architecture: any
Priority: optional
Architecture: all
Installed-Size: 45544
**Depends: a-program-we-need, another-program-we-need**
Maintainer: Maintainer Name <maintainer@website.com>
Homepage: http://www.website.com/example-package
Description: An example package.

```
To find your apt source, try running: [COLOR="Green"]find / -iname apt 2>/dev/null[/COLOR]
Although I believe it downloads into the current directory by default.

---

### Post by kapmsd on 2010-01-17
Thanks a lot for ur input.

PRIVATE DB:

Whenever we install a package using sudo apt-get install,the files are downloaded in /var/cache/apt/archives and installed.
         The private DB I am referring here is how apt keeps track of which packages are installed, which are not installed and which are available for installation.

CHECK DEPENDENCIES:
I want the source code of it for more details.

I ll take a look into it and post back here within few days.

---

### Post by SevenMachines on 2010-01-18
i apologise if i've misunderstood what you're looking to do but if you're looking for the actual source code of apt then to automatically download this into your current directory
$apt-get source apt

but apt in itself is a front end to dpkg for deb packages so you may also want
$apt-get source dpkg

* you will obviously need the source repository enabled (you can do this easily in synaptic)

---

### Post by SevenMachines on 2010-01-18
installing libapt-pkg-doc and looking at the docs it installs in /usr/share/doc/libapt-pkg-doc might also be helpful

---

### Post by kapmsd on 2010-01-19
Thanks a lot for ur inputs.
I ll take a look at it and post back here.

---

