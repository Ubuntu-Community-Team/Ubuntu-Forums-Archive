---
title: "Cannot Install or Uninstall Anything"
date: 2012-08-04
forum: Server Platforms
---

### Post by cosmarchy on 2012-08-04
Hi,

I've had this problem with installing and goes around in circles.  for example when I try to install xrdp, I get this:
> user@ubuntu:~$ sudo apt-get install xrdp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libcups2 : Breaks: libcups2:i386 (!= 1.5.3-0ubuntu2) but 1.5.3-0ubuntu1 is to be installed
 libcups2:i386 : Breaks: libcups2 (!= 1.5.3-0ubuntu1) but 1.5.3-0ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

so naturally, I try > user@ubuntu:~$ apt-get -f install to try and fix the problems and get this:
> E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
user@ubuntu:~$ sudo -s
root@ubuntu:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libcups2:i386
Suggested packages:
  cups-common:i386
The following packages will be upgraded:
  libcups2:i386
1 upgraded, 0 newly installed, 0 to remove and 119 not upgraded.
16 not fully installed or removed.
Need to get 0 B/173 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libcups2:i386 (--configure):
 libcups2:i386 1.5.3-0ubuntu1 cannot be configured because libcups2:amd64 is in a different version (1.5.3-0ubuntu2)
dpkg: dependency problems prevent configuration of libgtk2.0-0:i386:
 libgtk2.0-0:i386 depends on libcups2 (>= 1.4.0); however:
  Package libcups2:i386 is not configured yet.
dpkg: error processing libgtk2.0-0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librsvg2-common:i386:
 librsvg2-common:i386 depends on libgtk2.0-0 (>= 2.21.5); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing librsvg2-common:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libcups2 (--configure):
 libcups2:amd64 1.5.3-0ubuntu2 cannot be configured because libcups2:i386 is in a different version (1.5.3-0ubuntu1)
dpkg: dependency problems prevent configuration of libcanberra-gtk0:i386:
 libcanberra-gtk0:i386 depends on libgtk2.0-0 (>= 2.24.0); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing libcanberra-gtk0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcupsimage2:i386:
 libcupsimage2:i386 depends on libcups2 (>= 1.4.0); however:
  Package libcups2:i386 is not configured yet.
dpkg: error processing libcupsimage2:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail18:i386:
 libgail18:i386 depends on libgtk2.0-0 (= 2.24.10-0ubuntu6); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing libgail18:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk2-engines:i386:
 gtk2-engines:i386 depends on libgtk2.0-0 (>= 2.19.7-2); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing gtk2-engines:i386 (--configure):
 dependency pNo apport report written because the error message indicates it's a follow-up error from a previous failure.
                              No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                               roblems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk2-engines-murrine:i386:
 gtk2-engines-murrine:i386 depends on libgtk2.0-0 (>= 2.24.5-4); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing gtk2-engines-murrine:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtk2-engines-pixbuf:i386:
 gtk2-engines-pixbuf:i386 depends on libgtk2.0-0 (= 2.24.10-0ubuntu6); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing gtk2-engines-pixbuf:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ibus-gtk:i386:
 ibus-gtk:i386 depends on libgtk2.0-0 (>= 2.24.5-4); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing ibus-gtk:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcanberra-gtk-module:i386:
 libcanberra-gtk-module:i386 depends on libcanberra-gtk0 (>= 0.2); however:
  Package libcanberra-gtk0:i386 is not configured yet.
 libcanberra-gtk-module:i386 depends on libgtk2.0-0 (>= 2.24.5-4); however:
  Package libgtk2.0-0:i386 is not configured yet.
dpkg: error processing libcanberra-gtk-module:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgail-common:i386:
 libgail-common:i386 depends on libgail18 (= 2.24.10-0ubuntu6); however:
  Package libgail18:i386 is not configured yet.
dpkg: error processing libgail-common:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs-multiarch:i386:
 ia32-libs-multiarch:i386 depends on gtk2-engines; however:
  Package gtk2-engines:i386 is not configured yet.
 ia32-libs-multiarch:i386 depends on gtk2-engines-murrine; however:
  Package gtk2-engines-murrine:i386 is not configured yet.
 ia32-libs-multiarch:i386 depends on gtk2-engines-pixbuf; however:
  Package gtk2-engines-pixbuf:i386 is not configured yet.
 ia32-libs-multiarch:i386 depends on ibus-gtk; however:
  Package ibus-gtk:i386 is not configured yet.
 ia32-libs-multiarch:i386 depends on libcanberra-gtk-module; however:
  Package libcanberra-gtk-module:i386 is not configured yet.
 ia32-libs-multiarch:i386 depends on libcups2; however:
  Package libcups2:i386 is not configured yet.
 ia32-libs-multiarch:i386 depends on libcupsimage2; however:
  Package libcupsimage2:i386 is not configured yet.
 ia32-libs-multiarch:i386 depends on libgail-common; however:
  Package libgail-common:i386 is not configured yet.
 ia32-libs-multiarch:i386 depends on libgtk2.0-0; however:
  Package libgtk2.0-0:i386 is not configured yet.
 ia32-libs-multiarch:i386 depends on librsvg2-common; however:
  Package librsvg2-common:i386 is not configured yet.
dpkg: error processing ia32-libs-multiarch:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on ia32-libs-multiarch; however:
  Package ia32-libs-multiarch is not installed.
  Package ia32-libs-multiarch:i386 is not configured yet.
dpkg: error processing ia32-libs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of teamviewer7:
 teamviewer7 depends on ia32-libs; however:
  Package ia32-libs is not configured yet.
dpkg: error processing teamviewer7 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libcups2:i386
 libgtk2.0-0:i386
 librsvg2-common:i386
 libcups2
 libcanberra-gtk0:i386
 libcupsimage2:i386
 libgail18:i386
 gtk2-engines:i386
 gtk2-engines-murrine:i386
 gtk2-engines-pixbuf:i386
 ibus-gtk:i386
 libcanberra-gtk-module:i386
 libgail-common:i386
 ia32-libs-multiarch:i386
 ia32-libs
 teamviewer7
E: Sub-process /usr/bin/dpkg returned an error code (1)

This happens with anything I try to install / uninstall and has only just recently started happening.  I am using Kubuntu Server v12.

Anyone know how to fix it?  

Thanks

---

### Post by thnewguy on 2012-08-04
You might try running "apt-get clean all" prior to running "apt-get -f install".

---

### Post by Sergius14 on 2012-08-04
Also when you run apt-get -f install, it was without sudo.

The error you got was because or maybe the lack or permissions (sudo) or maybe because you have another Window doing some operations (like update manager).


E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by sblandford on 2012-08-08
I just had a similar issue. Somehow libcups2 was a different version installed to libcups2.i386. Both are required since I have wine1.4 installed.

To resolve it I downloaded the same version of both and installed them manually to bring them both to the same version.

```
sudo apt-get download libcups2
sudo apt-get download libcups2:i386
sudo dpkg -i libcups2_1.5.3-0ubuntu3_i386.deb
sudo dpkg -i libcups2_1.5.3-0ubuntu3_amd64.deb
```

---

### Post by cosmarchy on 2012-08-08
I really don't understand what is going on but I got totally fed up with it last night and turned it off.  today when I get in ans switch it on, it has miraculously fixed itself like nothing was wrong in the first place...WTF????
 
I shall keep this advice fresh in my mind, however just in case all is not what it seems.
 
Thanks guys :)

---

