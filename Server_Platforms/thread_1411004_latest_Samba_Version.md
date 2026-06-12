---
title: "latest Samba Version"
date: 2010-02-19
forum: Server Platforms
---

### Post by mcarrara on 2010-02-19
When I use apt-get to install Samba the latest version is 3.0.26??????.  The current stable version is 3.4.5 and 3.5 is about ready to be released.  Is there anywhere I can get a deb package any newer that the one in APT? or will I have to compile from source?

Mark

---

### Post by doas777 on 2010-02-19
you can enable the backport and proposed repositories, but i'm notsure a canidate has been packaged for hardy. enable them and do an update to see.
usually most of the software versions for apps and services are fixed at time of distro release, and not changed until the next release 6months later. since you are still on 8.04 it is likely that you may be able to get a newer version with intrepid, jaunty, or karmic. 
there is always the option to pull it from the upstream if you like though.

---

### Post by mcarrara on 2010-02-19
How would I pull form the upstream?  Just change the line in apt.conf from hardy to something like karmic?

Mark

---

### Post by doas777 on 2010-02-19
> **mcarrara said:**
> How would I pull form the upstream?  Just change the line in apt.conf from hardy to something like karmic?

Mark

if they have a ppa repo then you could just set it in your sources.lst but if they don't you will have to go to their site to get a deb, or compile the source from release or svn. 
this may be of some help:
[http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)

---

### Post by mcarrara on 2010-02-19
I decided to install from source and it went easy enough.  I just hope I got all the ./configure options set correctly.

Mark

---

