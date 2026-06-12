---
title: "upgraded to 16.04 and pd-extended vanished from my programs and synaptic"
date: 2016-08-09
forum: Ubuntu Studio
---

### Post by thevmgas on 2016-08-09
i just upgraded to ubuntu studio 16.04 and noticed that pd extended was gone
came across this message in syanptic when trying to install it again
"pd-extended:
Package pd-extended has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

also from terminal:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pd-extended is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'pd-extended' has no installation candidate
```

????

```
W: The repository 'cdrom://Ubuntu-Studio 14.04.5 LTS _Trusty Tahr_ - Release amd64 (20160803.1) trusty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/eighthave/pd-extended/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: [http://ppa.launchpad.net/eighthave/pd-extended/ubuntu/dists/trusty/Release.gpg:](http://ppa.launchpad.net/eighthave/pd-extended/ubuntu/dists/trusty/Release.gpg:) Signature by key 24D13CBC7B4061FA59C676A2D63D3D09C39F5EEB uses weak digest algorithm (SHA1)
W: The repository 'http://apt.puredata.info/releases xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://apt.puredata.info/releases trusty Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch cdrom://Ubuntu-Studio 14.04.5 LTS _Trusty Tahr_ - Release amd64 (20160803.1)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Failed to fetch [http://ppa.launchpad.net/eighthave/pd-extended/ubuntu/dists/xenial/main/source/Sources](http://ppa.launchpad.net/eighthave/pd-extended/ubuntu/dists/xenial/main/source/Sources)  404  Not Found
E: Failed to fetch [http://apt.puredata.info/releases/dists/xenial/main/source/Sources](http://apt.puredata.info/releases/dists/xenial/main/source/Sources)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by CrocoDuck on 2016-08-09
Seems to me that pd-extended is not a package available in [default Ubuntu repositories]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=pd-extended&searchon=names"). Did you installed it adding an external repo, like described [here]("http://puredata.info/docs/faq/debian")? Then, try adding the repo again.

---

### Post by thevmgas on 2016-08-22
i moved pd-extended from an old hdd to the usr/lb on my current machine
was working fine and now all of a sudden it is gone
getting this error

"busy@busy100:~$ /usr/lib/pd-extended/pd-extendeddisabling real-time priority due to missing pd-watchdog (/usr/lib/bin/pd-watchdog)
Error in startup script: couldn't read file "/usr/lib/tcl//pd-gui.tcl": no such file or directory


"

---

### Post by RossGammon on 2016-08-23
pd-extended has never been packaged for Debian, although there has been some interest:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=708476](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=708476)

You seem to be missing some files that would normally be installed  when you install pd-extended. Or there is s dependency on another  package (pd-watchdog?). This is normally managed by the package  management system.

It is not generally a good idea to manually  move files around under /usr/lib. This is where the system files live.  As CrocoDuck says, it is best to install the third-party .deb file with a  package management tool. Or if you build and install it from source, by  convention all the libraries & binary files go in /usr/local so  that they don't interfere with the system install files.

I would recommend tidying up, and starting again with a deb file, or building from source

---

### Post by CrocoDuck on 2016-08-23
> **RossGammon said:**
> pd-extended has never been packaged for Debian, although there has been some interest:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=708476](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=708476)

You seem to be missing some files that would normally be installed  when you install pd-extended. Or there is s dependency on another  package (pd-watchdog?). This is normally managed by the package  management system.

It is not generally a good idea to manually  move files around under /usr/lib. This is where the system files live.  As CrocoDuck says, it is best to install the third-party .deb file with a  package management tool. Or if you build and install it from source, by  convention all the libraries & binary files go in /usr/local so  that they don't interfere with the system install files.

I would recommend tidying up, and starting again with a deb file, or building from source

100% agree. I add that it is not wise to attempt to install software just by copying binaries in place. It could work for very simple programs but usually dependencies need to be satisfied or the software needs to be built against specific flags and architectures. Not to mention the risk of installing malware, that it is much higher if you don't use a package manager. I would imagine that the upgrade you did purged dependencies or otherwise required files for pd-extended to work. I advise you to follow the instructions I linked from the PD website. It is easy and after that your pd-extended will be updated automatically. Once the software is installed through the package manager you don't have to fear upgrades anymore: the system is aware of the installed binaries and all the files and dependencies they need and it will keep things consistent.

---

