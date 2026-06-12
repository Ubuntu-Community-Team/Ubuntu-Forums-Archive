---
title: "Sorry, Ubuntu 12.10 has experienced an internal error"
date: 2012-05-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jerrylamos on 2012-05-18
So I get these on quantal quetzal on most boots on four different pc's.  Apport churns for a while then the window disappears....?

Then if I look in /var/crash there is:

_usr_lib_gnome-settings-daemon_gnome-settings-daemon.1000.crash
_usr_lib_gnome-settings-daemon_gnome-settings-daemon.1000.upload
_usr_lib_gnome-settings-daemon_gnome-settings-daemon.1000.uploaded

Uploaded to where???

Jerry

p.s. Not a showstopper I do wonder where the crash reports if any are going, or maybe apport is crashing.

---

### Post by jppr on 2012-05-18
[https://launchpad.net/ubuntu/quantal/+source/apport/2.1-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/apport/2.1-0ubuntu1)

---

### Post by hannysabbagh on 2012-05-19
remove apport and relax if you don't want to report the bugs:
sudo apt-get remove apport
sudo apt-get remove apport-gtk

thanks.

---

### Post by lonniehenry on 2012-05-19
Better to bug the problem and get it fixed for all the other users.  That is the purpose of using a developement version of Ubuntu. Ignored problems don't get solved.  Please contribute to the cause.

---

### Post by hannysabbagh on 2012-05-19
most of the error massages in the development releases of Ubuntu are not real bugs (some bad code on apport it self) of course if an app crashed while you are using it you shall report about it, but the 'fake' error massages are too noisy.. removing apport doesn't mean to ignore real bugs ;)

thanks

---

### Post by jbicha on 2012-05-20
There's no need to remove apport. Just open **/etc/default/apport **and set it to **enabled=0**

---

### Post by zika on 2012-05-20
> **jbicha said:**
> There's no need to remove apport. Just open **/etc/default/apport **and set it to **enabled=0**Or```
echo 'manual' | sudo tee /etc/init/apport.override
```
(somehow easier to maintain and remember later, at least for me... ;))

---

### Post by jerrylamos on 2012-05-20
> **lonniehenry said:**
> Better to bug the problem and get it fixed for all the other users.  That is the purpose of using a developement version of Ubuntu. Ignored problems don't get solved.  Please contribute to the cause.

Usually there are a bunch of bugs in pre-Alpha Alpha Beta.  I tend to file a launchpad bug on those that cause something not to work, showstopper, etc.  In this thread case the message pops up and after a while goes away.  Apport tries to do something then ends.  Now there is some other info in "Details" however the text won't copy and screen saver images are too big to post normally.  

Off to look for some other bugs - install is always ripe for bugs, but there isn't a lubuntu i386 quetzal yet.  I'm running -2D quetzal on another pc.

Jerry

---

### Post by jerrylamos on 2012-05-20
Got some more info on this minor interruption:

Executable path
  /usr/lib/gbine-settings-daemon/gnome-settings-daemon
Package
  gnome-settings-daemon 3.4.1-0ubuntu2
Problem Type
  Crash
Title
  [mouse]-gnome-settings-daemon crashed with SIGSEV in gdk_device_manager_list_devices@plt()

I think I got that copied by hand correctly since copy text doesn't work on that type of graphic pulldown window.  

Seems to me there must be thousands of crashes of this type already reported in Launchpad.

Jerry

---

