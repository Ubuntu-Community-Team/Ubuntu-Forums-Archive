---
title: "Cinnamon in Raring Ringtail"
date: 2013-02-15
forum: Ubuntu Development Version
---

### Post by zika on 2013-02-15
What would be preffered way of installing Cinnamon in RR...?
At my place (due to G3 and ricotz) I get:
```
:~$ sudo apt-get install cinnamon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: libgjs0-libmozjs185-1.0
E: Unable to correct problems, you have held broken packages.
``````
:~$ sudo apt-get install libgjs0-libmozjs185-1.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgjs0-libmozjs185-1.0 is a virtual package provided by:
  libgjs0c 1.35.4-0ubuntu1~raring1 [Not candidate version]
  libgjs0c 1.34.0-0ubuntu1 [Not candidate version]

E: Package 'libgjs0-libmozjs185-1.0' has no installation candidate
```
No, ppa:gwendal-lebihan-dev/cinnamon-stable did not help...

---

### Post by mc4man on 2013-02-15
```
sudo apt-get install cinnamon caribou
```
no ppa
Then possibly file bug on no caribou dep or not working in absence of caribou (not needed to install but needed to run

edit: to show
> $ sudo apt-get -s install cinnamon caribou
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-shell-common gtk2-engines-pixbuf libqt4-opengl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cinnamon-common gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-gkbd-3.0 gir1.2-muffin-3.0
  gir1.2-networkmanager-1.0 gir1.2-polkit-1.0 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs libcaribou-common libcaribou0
  libgjs0c libmozjs185-1.0 libmuffin0 muffin-common python-pyatspi python-pyatspi2
The following NEW packages will be installed:
  caribou cinnamon cinnamon-common gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-gkbd-3.0 gir1.2-muffin-3.0
  gir1.2-networkmanager-1.0 gir1.2-polkit-1.0 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs libcaribou-common libcaribou0
  libgjs0c libmozjs185-1.0 libmuffin0 muffin-common python-pyatspi python-pyatspi2
0 upgraded, 20 newly installed, 0 to remove and 19 not upgraded.
Inst muffin-common (1.1.2-1 Ubuntu:13.04/raring [all])
Inst libmuffin0 (1.1.2-1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-muffin-3.0 (1.1.2-1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-networkmanager-1.0 (0.9.7.995+git201301311547.17123fc-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst libmozjs185-1.0 (1.8.5-1.0.0+dfsg-4 Ubuntu:13.04/raring [amd64])
Inst libgjs0c (1.34.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst cinnamon-common (1.6.7-2 Ubuntu:13.04/raring [all])
Inst gjs (1.34.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-accountsservice-1.0 (0.6.29-1ubuntu5 Ubuntu:13.04/raring [amd64])
Inst gir1.2-xkl-1.0 (5.2.1-1ubuntu2 Ubuntu:13.04/raring [amd64])
Inst gir1.2-gkbd-3.0 (3.6.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-polkit-1.0 (0.105-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-upowerglib-1.0 (0.9.19-1ubuntu4 Ubuntu:13.04/raring [amd64])
Inst cinnamon (1.6.7-2 Ubuntu:13.04/raring [amd64])
Inst libcaribou-common (0.4.4-1ubuntu1 Ubuntu:13.04/raring [all])
Inst libcaribou0 (0.4.4-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst gir1.2-caribou-1.0 (0.4.4-1ubuntu1 Ubuntu:13.04/raring [amd64])
Inst python-pyatspi (2.7.2+dfsg-2ubuntu1 Ubuntu:13.04/raring [all])
Inst python-pyatspi2 (2.7.2+dfsg-2ubuntu1 Ubuntu:13.04/raring [all])
Inst caribou (0.4.4-1ubuntu1 Ubuntu:13.04/raring [all])
Conf muffin-common (1.1.2-1 Ubuntu:13.04/raring [all])
Conf libmuffin0 (1.1.2-1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-muffin-3.0 (1.1.2-1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-networkmanager-1.0 (0.9.7.995+git201301311547.17123fc-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf libmozjs185-1.0 (1.8.5-1.0.0+dfsg-4 Ubuntu:13.04/raring [amd64])
Conf libgjs0c (1.34.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf cinnamon-common (1.6.7-2 Ubuntu:13.04/raring [all])
Conf gjs (1.34.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-accountsservice-1.0 (0.6.29-1ubuntu5 Ubuntu:13.04/raring [amd64])
Conf gir1.2-xkl-1.0 (5.2.1-1ubuntu2 Ubuntu:13.04/raring [amd64])
Conf gir1.2-gkbd-3.0 (3.6.0-0ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-polkit-1.0 (0.105-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-upowerglib-1.0 (0.9.19-1ubuntu4 Ubuntu:13.04/raring [amd64])
Conf cinnamon (1.6.7-2 Ubuntu:13.04/raring [amd64])
Conf libcaribou-common (0.4.4-1ubuntu1 Ubuntu:13.04/raring [all])
Conf libcaribou0 (0.4.4-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf gir1.2-caribou-1.0 (0.4.4-1ubuntu1 Ubuntu:13.04/raring [amd64])
Conf python-pyatspi (2.7.2+dfsg-2ubuntu1 Ubuntu:13.04/raring [all])
Conf python-pyatspi2 (2.7.2+dfsg-2ubuntu1 Ubuntu:13.04/raring [all])
Conf caribou (0.4.4-1ubuntu1 Ubuntu:13.04/raring [all])

---

### Post by kansasnoob on 2013-02-15
Hmmm, I knew Cinnamon had been added to the repos some time ago:

> cinnamon (1.6.7-2) unstable; urgency=low

  * new patch: network-user-connection.patch
    Set connections and passwords as user-owned, following matching changes
    in nm-applet and gnome-control-center. (Closes: #698571)
  * **[COLOR="Red"]Remove caribou as dependency[/COLOR]**. (LP: #1106062) 
  * Restrict libgudev-glib-dev and libnm-glib-dev build-dependencies to
    Linux platforms: should fix the build on FreeBSD and Hurd.

 -- Nicolas Bourdaud <nicolas.bourdaud@gmail.com>  Thu, 07 Feb 2013 13:40:30 +0100

cinnamon (1.6.7-1) unstable; urgency=low

  * New upstream cinnamon_1.6.7
     - Fix keyboard settings applet. (Closes: #695217)
  * Remove the useless dependency of cinnamon on cups-pk-helper
  * Update debian/watch: stop using redirector (thanks to Bart Martens)
  * Add libgl1-mesa-dev as build depends: should fix build on ARM
  * Build bluetooth support only on Linux architectures.
  * Add python-dbus and python-imaging dependencies. (Closes: #693935)
  * Do not install browser plugin in multiarch folder. (Closes: #695338) 
  * Install translation files in the standard folder. (Closes: #695286)
    new patch: fix-gettext-files-path.patch
  * Move packaging git repo to Alioth. 
  * Use rpath to fix the use of libgnome-bluetooth. (Closes: #695408)
     - update: disable-bluetooth-applet-hack.patch

 -- Nicolas Bourdaud <nicolas.bourdaud@gmail.com>  Tue, 11 Dec 2012 18:24:48 +0100

cinnamon (1.6.2-1) unstable; urgency=low

  * **[COLOR="Red"]Initial release[/COLOR]**. (Closes: #657395)

 -- Nicolas Bourdaud <nicolas.bourdaud@gmail.com>  **[COLOR="Red"]Thu, 01 Nov 2012[/COLOR]** 17:49:55 +0100

But I've yet to actually try it in Raring :redface:

---

### Post by zika on 2013-02-15
> **mc4man said:**
> ```
sudo apt-get install cinnamon caribou
```
no ppa
Then possibly file bug on no caribou dep or not working in absence of caribou (not needed to install but needed to run

edit: to showNot that I did not think about that...```
:~$ sudo apt-get install cinnamon caribou
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: libgjs0-libmozjs185-1.0
E: Unable to correct problems, you have held broken packages.
```

---

### Post by macstevejb on 2013-02-15
Cinnamon should work using the nightly build from this ppa:

[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-nightly](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-nightly)

regards :P

---

### Post by zika on 2013-02-15
> **macstevejb said:**
> Cinnamon should work using the nightly build from this ppa:

[https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-nightly](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-nightly)

regards :PAfter turning that PPA on and after update I still get:```
zika@zika:~$ sudo apt-get install cinnamon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: libgjs0-libmozjs185-1.0
            Recommends: nemo but it is not going to be installed
            Recommends: cinnamon-screensaver but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```A bit different but the same problem persists...
To prevent ambiguity:
```
:~$ sudo apt-get install cinnamon caribou
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: libgjs0-libmozjs185-1.0
            Recommends: nemo but it is not going to be installed
            Recommends: cinnamon-screensaver but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by jbicha on 2013-02-15
> **zika said:**
> 
```
$ sudo apt-get install cinnamon

The following packages have unmet dependencies:
 cinnamon : Depends: libgjs0-libmozjs185-1.0
E: Unable to correct problems, you have held broken packages.
```
This sounds like you are using the Ricotz testing PPA which uses mozjs188 (which does fix some bugs but we may have to wait for 13.10 for it to get into Ubuntu). If you want to use Cinnamon, you'll either need to rebuild Cinnamon yourself (or in a PPA that depends on the Ricotz testing PPA) or ppa-purge that PPA.

---

### Post by zika on 2013-02-15
> **jbicha said:**
> This sounds like you are using the Ricotz testing PPA which uses mozjs188 (which does fix some bugs but we may have to wait for 13.10 for it to get into Ubuntu). If you want to use Cinnamon, you'll either need to rebuild Cinnamon yourself (or in a PPA that depends on the Ricotz testing PPA) or ppa-purge that PPA.
Yes, I use Ricotz's testing... I thought that there might be some shortcut, but...
My path is clear... Thank You...
Update&#8321;:It was not worthy... Purged Ricotz's testing PPA and installed Cinnamon just to learn that it does not work: blank screen with cursor... Terminal opens but... For the record, I've been using Cinnamon earlier, not just as spice... ;)

---

### Post by mc4man on 2013-02-15
For what it's worth, (not much really),  it does start up & run on a non-modded 13.04 install

Though at least here it still does need caribou/libcaribou0 installed to actually start up
(another crappy Debian maintainer package in Ubuntu

---

### Post by fantab on 2013-02-16
I am using Cinnamon on my Raring along with Unity... I actually wanted to check out Nemo... but to have that I had to install Cinnamon.

I am using a stable ppa: [https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable)

It is working flawlessly AFAIK. I had a issue when 'cinnamon-settings' was not launching but that got fixed with recent python updates...

As for the problem you are having: I checked Synaptic and I have **libgjs0c** and I don't have *libgjs0-libmoxjs185-1.0* in Synaptic or in my repos.

Try installing Cinnamon from the stable ppa above...

---

### Post by zika on 2013-02-16
I've tried stable, nightly, raring...
I've tried with/without caribou...
Same thing: black screen, terminal is working, keyboard shortcuts from gnome work but no menu, no Alt-F2, nothing...
I'll investigate libgjs0c when I get enough patience and spare time to do that... ;)
(Update&#8321;: Yes I have libgjs0c installed...)
Thank You for all support...

---

### Post by superchar42 on 2013-02-18
Cinnamon is running fine for me.

---

### Post by lorimer on 2013-02-19
I have the same problem as zika.  I installed the alpha a few weeks ago and went straight to Cinnamon.  Everything was great until I ran updates on Thursday night.  Cinnamon stopped working.  I had also installed Steam Thursday night and thought that might be the problem, so I blew away the alpha and started from scratch (overkill, I know, but is is my play laptop).  A clean install with no additional repos/PPA's did not work with cinnamon.  I keep hoping it is a library mis-match as a part of the dev cycle.  Hopefully an update will soon fix things.

---

### Post by TREESofRIGHTEOUSNESS on 2013-02-21
I also saw it in the repos and installed it in 13.04 to test it out, but all I get is my background image and some windows that don't have a decorator.....  not sure what happened there.... I'll try installing caribou to see if that helps.... though an onscreen keyboard doesn't seem like that would be the issue...  I am also experiencing issues with Unity, though.  However... Lxde is working beautifully!!

---

### Post by TREESofRIGHTEOUSNESS on 2013-02-21
Wow... an on screen keyboard not being installed cause me to have NO panel????  That is great!  I like that the Menu functions just like the dash... very neat

---

### Post by lorimer on 2013-02-21
It was caribou for me as well.  I tried installing the python dependencies for caribou, but they did not fix the problem.  I ended up installing all of caribou to get back to the happiness of Cinnamon.

---

### Post by Pablo Picasso on 2013-02-24
I've been running Cinnamon nightly on 13.04 for a couple of days with no issues but one, in fact it has fixed a wireless issue and an issue with my Logitech Performance mouse. I'm enjoying the new settings mode in Cinnamon and the breadcrumb navigation. There is still the issue of dueling file browsers causing missing desktop icons, but I used the easy workaround of deleting the Nautilus autostart file.

I recently took the plunge and bought a laptop, erased Windows 8 and installed a number of distros. I managed to get Ubuntu 12.10 to install and use the SSD cache as /. My machine now boots in 25 seconds and is way faster than W8 plus it has 750Gb storage.  I went on to replace W7 on my workstation with Mint Nadia Cinnamon. I think I prefer Ubuntu spiced with Cinnamon. I had a hard time installing Mint on RAID arrays. I managed to do it but, it shouldn't be so hard.

I'm not going back to "Windows". 
Loving Linux. 
Thank you.

---

### Post by Pierre771 on 2013-05-16
Hello

Cinnamon is incompatible with Gnome Shell 3.8

---

### Post by Elfy on 2013-05-16
Closed - this is rather old to drag back - better to start again for saucy.

---

