---
title: "Undefined Symbols with Wireshark/Tshark"
date: 2013-09-25
forum: Server Platforms
---

### Post by Jon_Mantis on 2013-09-25
I have a 12.04 LTS amd64 install on a headless server and I am trying to get tshark running.  I seem to have a number of library issues with a few programs I've installed and I can't find any info online.  As far as I know I haven't messed with any of the libraries or installed anything by hand from source.  Almost all my issues are with libg* modules undefined symbols of some sort.

So to start, I install tshark from the repository, try to run it and get this error:

tshark: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0: undefined symbol: g_private_replace

When I downloaded the wireshark source and tried to configure, I get this error:

checking for GTK+ - version >= 2.12.0 and < 3.0... no
*** Could not run GTK+ test program, checking why...
*** The test program compiled, but did not run. This usually means
*** that the run-time linker is not finding GTK+ or finding the wrong
*** version of GTK+. If it is not finding GTK+, you'll need to set your
*** LD_LIBRARY_PATH environment variable, or edit /etc/ld.so.conf to point
*** to the installed location  Also, make sure you have run ldconfig if that
*** is required on your system
***
*** If you have an old version installed, it is best to remove it, although
*** you may also be able to get things to work by modifying LD_LIBRARY_PATH
configure: error: Neither Qt nor GTK+ 2.12.0 or later are available, so Wireshark can't be compiled

I find this in the config.log.

./conftest: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0: undefined symbol: g_signal_accumulator_first_wins


I have libgtk2.0-dev installed and I'm just really confused why I'm having library issues with packages installed from the repository.

I appreciate any help with this, I'm completely stumped.

Jonathan

---

### Post by sanderj on 2013-09-25
What is the output of:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install tshark
```

Post the output here.

---

### Post by Jon_Mantis on 2013-09-25
Sure:

root@hal:/installed_software/wireshark-1.10.2# sudo apt-get update|less
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
Hit [http://linux.dell.com](http://linux.dell.com)  Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Hit [http://linux.dell.com](http://linux.dell.com)  Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
Hit [http://linux.dell.com](http://linux.dell.com)  Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Ign [http://linux.dell.com](http://linux.dell.com)  Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages
Ign [http://linux.dell.com](http://linux.dell.com)  Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Reading package lists...

root@hal:/installed_software/wireshark-1.10.2# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@hal:/installed_software/wireshark-1.10.2# apt-get install tshark
Reading package lists... Done
Building dependency tree
Reading state information... Done
tshark is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-41 linux-image-3.2.0-41-generic linux-headers-3.2.0-41-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@hal:/installed_software/wireshark-1.10.2# tshark
tshark: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0: undefined symbol: g_private_replace

Thanks!

---

### Post by sanderj on 2013-09-26
Disclaimer: I'm now going into trial-and-erro mode:

What is your output of:

```
sander@flappie:~$ ll /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0
lrwxrwxrwx 1 root root 26 sep  1 21:15 /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 -> libgmodule-2.0.so.0.3600.0
sander@flappie:~$
```

The above is on my Ubuntu 13.04 64-bit

---

### Post by Jon_Mantis on 2013-09-26
No problem, I'm lost as well.  Usually I can search to solve my problems but this one is obscure.  This is an important server though and rebuilding it would not be simple so I appreciate the help.

Slightly different version on my end but it's the x64 library:

root@hal:/n2# ll /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0
lrwxrwxrwx 1 root root 26 Jun  6  2012 /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 -> libgmodule-2.0.so.0.3200.3

So correct me if I'm wrong, but aren't unresolved symbols a problem where a binary has been compiled against a different version of a binary?  I haven't installed any other libg* modules or any custom modules on the system.  I also looked in /usr/local/lib/ for anything suspicious and couldn't find anything.

The only thing I could think possibly was perhaps this was compiled against some 32bit libraries or something but looking at the package details that wasn't the case.  I'm stumped since this was a fresh install of 12.04 LTS.

Thanks,
Jonathan

---

### Post by sanderj on 2013-09-27
A few more trial-and-error checks:

```
sander@flappie:~$ what-provides /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0
libglib2.0-0:amd64: /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0
libglib2.0-0:amd64: /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3600.0
sander@flappie:~$ 
```

Can you reinstall that? 

```
sander@flappie:~$ what-source libglib2.0-0
glib2.0
sander@flappie:~$
```

---

### Post by Jon_Mantis on 2013-09-27
So it looks like there are two sources of glib2.0 in my sources but I can't figure out which is which.  Looks like we're getting closer though:

root@hal:~# what-provides /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0
libglib2.0-0: /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0
libglib2.0-0: /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3200.3



root@hal:~# what-source libglib2.0-0
glib2.0
glib2.0


root@hal:~# apt-cache show glib2.0|less
Package: libglib2.0-0
Priority: required
Section: libs
Installed-Size: 3740
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: glib2.0
Version: 2.32.3-0ubuntu1
Replaces: libglib2.0-dev (<< 2.23.2-2)
Depends: libc6 (>= 2.15), libffi6 (>= 3.0.4), libpcre3 (>= 8.10), libselinux1 (>= 1.32), zlib1g (>= 1:1.2.2)
Pre-Depends: multiarch-support
Recommends: libglib2.0-data, shared-mime-info
Conflicts: bamfdaemon (<= 0.2.92-0ubuntu1), libzeitgeist-gio, wncksyncdaemon
Breaks: gdm3 (<< 3.0.3), gnome-control-center (<< 1:3), gnome-session (<< 3.0.0-3), gvfs (<< 1.8), libgtk-3-0 (<< 3.0.12)
Filename: pool/main/g/glib2.0/libglib2.0-0_2.32.3-0ubuntu1_amd64.deb
Size: 1198996
MD5sum: c95739d4b8ae8f233e2d173cbe3ae24a
SHA1: 07eddae27a9d21c1f8e500bab5c59b170166c093
SHA256: c6c63001dc9cdddf04a0295726024541da42cdd086e7ca9bc6b940dda4665bd6
Description-en: GLib library of C routines
 GLib is a library containing many useful C routines for things such
 as trees, hashes, lists, and strings.  It is a useful general-purpose
 C library used by projects such as GTK+, GIMP, and GNOME.
 .
 This package contains the shared libraries.
Multi-Arch: same
Homepage: [http://www.gtk.org/](http://www.gtk.org/)
Description-md5: f44de6293be1aa02cd13d73f591580a9
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: minimal


Package: libglib2.0-0
Priority: required
Section: libs
Installed-Size: 3732
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: glib2.0
Version: 2.32.1-0ubuntu2
Replaces: libglib2.0-dev (<< 2.23.2-2)
Depends: libc6 (>= 2.15), libelf1 (>= 0.131), libffi6 (>= 3.0.4), libpcre3 (>= 8.10), libselinux1 (>= 1.32), zlib1g (>= 1:1.2.2)
Pre-Depends: multiarch-support
Recommends: libglib2.0-data, shared-mime-info
Conflicts: bamfdaemon (<= 0.2.92-0ubuntu1), libzeitgeist-gio, wncksyncdaemon
Breaks: gdm3 (<< 3.0.3), gnome-control-center (<< 1:3), gnome-session (<< 3.0.0-3), gvfs (<< 1.8), libgtk-3-0 (<< 3.0.12)
Filename: pool/main/g/glib2.0/libglib2.0-0_2.32.1-0ubuntu2_amd64.deb
Size: 1198750
MD5sum: aa6d31168cb5e09d7e02cac1707c92c2
SHA1: 0ba908ba29f7da7f14c7c5afad8a94403d1d3019
SHA256: cd38a8eb484988292cccfadf4acb090e9d8a15f9d5b549724056550ad4d5b677
Description-en: GLib library of C routines
 GLib is a library containing many useful C routines for things such
 as trees, hashes, lists, and strings.  It is a useful general-purpose
 C library used by projects such as GTK+, GIMP, and GNOME.
 .
 This package contains the shared libraries.
Multi-Arch: same
Homepage: [http://www.gtk.org/](http://www.gtk.org/)
Description-md5: f44de6293be1aa02cd13d73f591580a9
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: minimal

---

### Post by Jon_Mantis on 2013-09-27
Looks like these two sources are the source of the slightly different glib2.0 versions.  As far as I know I haven't touched the sources.list and don't know why these are both here or what the deal is:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

---

