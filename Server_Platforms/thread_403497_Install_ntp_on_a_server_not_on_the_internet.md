---
title: "Install ntp on a server not on the internet"
date: 2007-04-07
forum: Server Platforms
---

### Post by auberginepop on 2007-04-07
I have an Ubuntu server running on a closed network. I now need to add the ntp daemon to the server but cannot do this with the usual apt-get as the server cannot hit the net.

How do I download the necessary files on another machine and then transfer them so that the server can now install them?

---

### Post by elst on 2007-04-07
Try the "download" option of aptitude on the system with the Internet connection. The man page for aptitude says:

> 
       download
              Downloads the .deb file for the given package to the current directory.

              By default, the version which would be installed with &#8216;&#8216;aptitude install&#8217;&#8217; is downloaded.


Advice is to use aptitude rather than apt-get these days, although apt-get still works, of course.

EDIT: You can then copy the packages across to the other system, and use "sudo dpkg -i <packages>" to install them.

---

### Post by auberginepop on 2007-04-09
Thanks your solution worked a treat.

Out of interest, why do you say aptitude is preferable to apt-get?

---

### Post by elst on 2007-04-09
It has more sophisticated dependency resolution, which helps your system stay in good order. The Debian Release Notes say a bit more:

[http://www.debian.org/releases/stable/i386/release-notes/ch-whats-new.en.html#s-pkgmgmt](http://www.debian.org/releases/stable/i386/release-notes/ch-whats-new.en.html#s-pkgmgmt)

---

