---
title: "apt-get update - 404 Not Found"
date: 2005-09-29
forum: Repositories &amp; Backports
---

### Post by angelot on 2005-09-29
Hi!
For a couple of days I've got this error-message when I 'apt-get update'.
Am I doing anything wrong or is it just down?
```
http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz  404 Not Found
http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz  404 Not Found
http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz  404 Not Found
http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz  404 Not Found
```
Thanks!
Angelot

---

### Post by angelot on 2005-09-29
I need the 'sun-j2sdk1.5'-package, but all I get with 'apt-cache search sun-j2' is sun-j2re1.5

Does this have anything to do with the errors I have with 'apt-get update' or do I have to add a new site to my repository...?

Help?

---

### Post by heimo on 2005-09-29
I believe it's about backports project becoming official and moving to ubuntu.com servers. You can change backports repositories to point
```
http://us.archive.ubuntu.com/ubuntu/dists/hoary-backports/
``` Please replace us with your nearest / local mirror (two character country code).


EDIT: [COLOR=Red]this post contains errors :)[/COLOR]

---

### Post by angelot on 2005-09-29
Tried with:
```
deb http://no.archive.ubuntu.com/ubuntu/dists/hoary-backports/ hoary-backports main universe multiverse restricted
deb http://no.archive.ubuntu.com/ubuntu/dists/hoary-backports/ hoary-extras main universe multiverse restricted
```

Failed...

---

### Post by angelot on 2005-09-29
This is my sources.list:
```
deb http://no.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://no.archive.ubuntu.com/ubuntu hoary main restricted
deb http://no.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://no.archive.ubuntu.com/ubuntu hoary universe
deb-src http://no.archive.ubuntu.com/ubuntu hoary universe
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
deb http://no.archive.ubuntu.com/ubuntu/dists/hoary-backports/ hoary-backports main universe multiverse restricted
deb http://no.archive.ubuntu.com/ubuntu/dists/hoary-backports/ hoary-extras main universe multiverse restricted
# deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
# deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
## VideoLan.org MediaPlayer update
deb http://download.videolan.org/pub/videolan/debian sarge main
deb-src http://download.videolan.org/pub/videolan/debian sarge main
```
If it can help...

---

### Post by heimo on 2005-09-29
Oh, sorry... My mistake... :) Of course it's something like this:

```
deb http://no.archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse

```

---

### Post by angelot on 2005-09-29
No it's not your fault - I'm stiil a newbie....

It works!

But```
# deb http://no.archive.ubuntu.com/ubuntu hoary-extras main restricted universe multiverse
``` won't...

If it's official now maybe they need no extras....

---

### Post by heimo on 2005-09-29
There seems to be "extras"-stuff on mirrormax servers (I never use these extras), so you should be able to use your old sources line for that.

---

### Post by angelot on 2005-09-29
This works:```
deb http://no.archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
```

But I still can't find the 'sun-j2sdk1.5'-package with 'apt-cache search sun-j2'... Where is it? What can I add to my sources.list to find it?

---

### Post by heimo on 2005-09-29
I'm afraid java has been removed. These talk about jre instead of sdk, but maybe these apply (at least the tower-net.de repository seems to have sdk):
[http://www.ubuntuforums.org/showthread.php?t=68718]("http://www.ubuntuforums.org/showthread.php?t=68718")
[http://www.ubuntuforums.org/showthread.php?t=70087]("http://www.ubuntuforums.org/showthread.php?t=70087")

EDIT: I don't know anything about this tower-net -repository (who maintains it, who did the packaging). Probably ok, but you should always ask these questions when using external (other than official) repositories.

---

### Post by angelot on 2005-09-29
I found this guide on [http://student.cosy.sbg.ac.at/~amayer/files/How-to-install-Java-on-Debian.html:](http://student.cosy.sbg.ac.at/~amayer/files/How-to-install-Java-on-Debian.html:)
```
How to install Java on Debian
The best way to install Java on Debian is using java-package. That way, you will be able to install other Java applications from the Debian repository with the usual apt-get method, such as ant or JEdit.
Do the following:
* Install the package java-package, from contrib:
apt-get install java-package
* Download the Sun JDK installer for Linux, from http://java.sun.com/j2se/.
* Create the Debian package. Be sure you are not root:
fakeroot make-jpkg jdk-1_5_0_01-linux-i586.bin
(change to the name of your downloaded archive)
* Install the Debian package. Become root and run this:
dpkg -i sun-j2sdk1.5-1_5_0+update01.deb
That's it!
```
This is much the same you wrote, but this is a more straight-forward guide. With this you can build a static j2sdk-package by yourself. I got some errors since when I was not root, but the deb-package was buildt - and when I installed it as root I got no error-messages...
Thanks for all the help - I got it now!

---

### Post by heimo on 2005-09-29
> [http://student.cosy.sbg.ac.at/~amayer/files/How-to-install-Java-on-Debian.html](http://student.cosy.sbg.ac.at/~amayer/files/How-to-install-Java-on-Debian.html)

Great! Thanks for the link. And welcome to Ubuntuforums! :D

---

