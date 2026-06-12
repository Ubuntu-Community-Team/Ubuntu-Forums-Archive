---
title: "libSoundTouch lost in Jaunty"
date: 2009-06-28
forum: Ubuntu Studio
---

### Post by CVarin on 2009-06-28
After upgrading my Dell Latitude D530 from Intrepid to jaunty, Audacity will not load, exiting with the error:
audacity: error while loading shared libraries: libSoundTouch.so.1: cannot open shared object file: No such file or directory

I tried reinstalling Audacity with no luck. I tried ReZound and got an identical message.  Gnusound restarts the entire X-windows system, leaving me at the login prompt.

I tried using apt to install libSoundTouch and got the following:
****~$ sudo apt-get install libsoundtouch1-dev libsoundtouch1c2 soundstretch
[sudo] password for ****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsoundtouch1c2 is already the newest version.
libsoundtouch1c2 set to manually installed.
soundstretch is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsoundtouch1-dev: Depends: libsoundtouch1c2 (= 1.3.1-2) but 1.3.1-mb1 is to be installed
E: Broken packages


Any suggestions?  An alternative working sound editor?  Any help appreciated.

---

