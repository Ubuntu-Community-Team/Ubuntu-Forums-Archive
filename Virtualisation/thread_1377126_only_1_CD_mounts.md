---
title: "only 1 CD mounts"
date: 2010-01-09
forum: Virtualisation
---

### Post by hyburn on 2010-01-09
hey folks.

Im trying to a install a game that requires multiple CD's to install, but when I put the second CD in the drive, its still showing up as the first CD.

how can I let VirtualBox mount more than 1 CD?

---

### Post by hyburn on 2010-01-09
the windows client is a guest account inside of ubuntu, running through Virtualbox

---

### Post by fouadatmeh on 2010-01-10
Hello,

which version of VirtualBox are you using?? as here in version 3.1 I can add several virutal cd drives and each one with a separate image (or host drive)..
I believe this is a relatively new feature, but I am not sure when did they start implelemting it.

---

### Post by hyburn on 2010-01-11
how do I add myself to the group of users. I think I already did. something is up with my machine and its F-in with my head. AAARRRRRRGGGGGG

---

### Post by fouadatmeh on 2010-01-11
which group of users???

---

### Post by hyburn on 2010-01-12
should I use my acetone to mount to my virtual drives? if so. how do I let my guest windows OS identify the virtual drives?

---

### Post by fouadatmeh on 2010-01-12
No need for acetone or any other utilities.. now what version of vbox are you using..
coz on v3.1 you can add another CD drive for the guest as follows ( so you can mount the two cd's at the same time):
-Shut down your guest OS > right click on the guest machine name > click on "settings" > select "storage" > click on the cd with the + sign next to it (next the "IDE Controller") > select the iso image you want to mount in the 2nd drive > start your guest.

Hope that works..

---

### Post by hyburn on 2010-01-14
I went to this

[http://ubuntuforums.org/archive/index.php/t-6509.html](http://ubuntuforums.org/archive/index.php/t-6509.html)

to try to learn how to create an ISO. but I get this message

I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: Missing pathspec.
Usage: genisoimage [options] -o file directory ...

Use genisoimage -help
to get a list of valid options.

Report problems to [email]debburn-devel@lists.alioth.debian.org[/email].

---

### Post by hyburn on 2010-01-14
oh and my virtual box is 1.5.6

how do I upgrade it?

---

### Post by Dayofswords on 2010-01-14
update manager should do it,
what are you doing running such an old version anyways?

---

### Post by hyburn on 2010-01-14
it says my system is up to date

---

### Post by fouadatmeh on 2010-01-14
Hello,
You can download the latest version from this link:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by hyburn on 2010-01-15
now how do I remove my old virtualbox? and will I need to re-install my windows XP guest OS?

---

### Post by fouadatmeh on 2010-01-15
You can remove it from the add/remove programs, or from synaptec package manager..
Or even better, install it over the old version (which I do whenever there is an upgrade).

**you shouldn't lose your settings, but just to be on the safe side, do an export of your virtual machines' settings.

---

### Post by hyburn on 2010-01-16
upon running my new sun virtualbox I get this message

Failed to create the VirtualBox COM object.
The application will now terminate.
Error in /home/hyburn/.VirtualBox/VirtualBox.xml (line 3) -- Cannot handle settings version '1.2-linux'.
/home/vbox/vbox-3.1.2/src/VBox/Main/VirtualBoxImpl.cpp[420] (nsresult VirtualBox::init()).

---

### Post by hyburn on 2010-01-16
should I change line 3 to my newest version of Vbox?

---

### Post by fouadatmeh on 2010-01-16
Hello,
This is where I sadly say "I don't know" :(
I tried removing the /home/fouad/.VirtualBox folder and when virtualbox started again, it started clean whith no config.
so try moving or renaming the whole .Virtualbox folder and start vbox, then configure your machines one by one using the virtual hdd's from your machines (probably located inside this folder).

---

