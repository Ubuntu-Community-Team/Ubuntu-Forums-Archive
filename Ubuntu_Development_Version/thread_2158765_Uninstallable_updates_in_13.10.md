---
title: "Uninstallable updates in 13.10"
date: 2013-06-30
forum: Ubuntu Development Version
---

### Post by Deucalion29710 on 2013-06-30
I have a daily build of 13.10 and in update manager when I check for updates it takes a really long time to find the updates, and when it does find them I see a "Ubuntu Base" and another update that I cannot select or install.  Is there any fix for this?  Also, with these daily builds, should I receive updates as the daily uploads are added?

---

### Post by Iowan on 2013-06-30
Moved to Ubuntu+1

---

### Post by vinibali on 2013-06-30
if you got problems, try to select another software update host at the system control->software updates or if u have a package what u cant mark for install, install it from the terminal. i got a system-usermode-switch(?) update about a month ago, and installed "manually".
you also can update the system with the following command:
sudo apt-get install update
sudo apt-get install upgrade

---

### Post by zika on 2013-06-30
> **Deucalion29710 said:**
> I have a daily build of 13.10 and in update manager when I check for updates it takes a really long time to find the updates, and when it does find them I see a "Ubuntu Base" and another update that I cannot select or install.  Is there any fix for this?  Also, with these daily builds, should I receive updates as the daily uploads are added?You've taken one snapshot (daily image) and it lives now as a normal install.. If You upgrade it You are (almost) up to a daily image for that day... Frequency and extent of upgrade is in Your hands...
Which server are You using?
Again, You can control almost all variables in that process..
Be sure to read about dist-upgrade (partial upgrade) in sticky thread in U+1...
Since You've taken a plunge into U+1 You should be able to distinguish what is preferable partial and what is not... Be very carefull...

---

### Post by zika on 2013-06-30
> **vinibali said:**
> if you got problems, try to select another software update host at the system control->software updates or if u have a package what u cant mark for install, install it from the terminal. i got a system-usermode-switch(?) update about a month ago, and installed "manually".
you also can update the system with the following command:
sudo apt-get install update
sudo apt-get install upgrade
[COLOR=#000000]Be sure to read about dist-upgrade (partial upgrade) in sticky thread in U+1...[/COLOR]
[COLOR=#000000]Since You've taken a plunge into U+1 You should be able to distinguish what is preferable partial and what is not... Be very carefull...
Yes, manual install from CLI is an option...[/COLOR]

---

### Post by grahammechanical on 2013-06-30
What we see with Update Manager in 13.10 is an attempt to make the description of the packages less like a foreign language to ordinary uses. Packages to be updated are also in categories. If you click on the little arrow to the left of Ubuntu base the category will expand and by scrolling down you will see all the packages to be updated in that category.

Those items marked for update can be unchecked but items listed to be updated but not yet ready cannot be ticked to be updated. They are just not yet in the repositories. But they will be available in a day or two.

I would say it is normal for the development branch to have packages to be in the list but not marked for download. I just ran Update Manager and I noticed that some Linux kernel files were listed but not marked for download. That, I assume is because, there are other files that go with a kernel update and they are not yet in the repositories.

We get something similar when we update through the terminal. We are told of packages held back.

Regards.

---

### Post by zika on 2013-07-01
> **grahammechanical said:**
> What we see with Update Manager in 13.10 is an attempt to make the description of the packages less like a foreign language to ordinary uses. Packages to be updated are also in categories. If you click on the little arrow to the left of Ubuntu base the category will expand and by scrolling down you will see all the packages to be updated in that category.

Those items marked for update can be unchecked but items listed to be updated but not yet ready cannot be ticked to be updated. They are just not yet in the repositories. But they will be available in a day or two.

I would say it is normal for the development branch to have packages to be in the list but not marked for download. I just ran Update Manager and I noticed that some Linux kernel files were listed but not marked for download. That, I assume is because, there are other files that go with a kernel update and **they are not yet in the repositories**.

We get something similar when we update through the terminal. We are told of packages held back.

Regards.
No, in order to get a **new** kernel You have to accept partial (dist) upgrade... Even though they are all ready and willing... Alternative is manual install package-by-package...
We've elaborated all that in several sticky threads about partial...
Making new names is not new for 13.10 as far as I remember...

---

### Post by FiremanEd on 2013-07-01
Will a daily zsync run everyday eliminate above issues?

---

### Post by zika on 2013-07-01
> **FiremanEd said:**
> Will a daily zsync run everyday eliminate above issues?
What issues? If it is about kernel: no... That is not an issue it is a feature... It has been and it will be, I hope...

---

### Post by FiremanEd on 2013-07-01
Thank you zika.

---

### Post by Harry33 on 2013-07-02
> **zika said:**
> What issues? If it is about kernel: no... That is not an issue it is a feature... It has been and it will be, I hope...

This so called feature (IMO an erraneous behaviour :() only applies to UM.
There are no partial upgrades in Synaptic. If an important package is not available, Synaptic will not let any partial installation to occur. However, regarding kernel, it will automatically draw in the necessary packages.

And once again I emphasize, Synaptic is the only working program (if manual installation is not counted here) for upgrading development branch distros.

---

### Post by zika on 2013-07-02
> **Harry33 said:**
> This so called feature (IMO an erraneous behaviour :() only applies to UM.
There are no partial upgrades in Synaptic. If an important package is not available, Synaptic will not let any partial installation to occur. However, regarding kernel, it will automatically draw in the necessary packages.

And once again I emphasize, Synaptic is the only working program (if manual installation is not counted here) for upgrading development branch distros.
I beg to differ... There are several examples on this Forum I gave that contradicts written...
You can select which kind of upgrade You want to try in Synaptic...
Not to mention apt-get and aptitude...

---

### Post by Harry33 on 2013-07-02
> **zika said:**
> I beg to differ... There are several examples on this Forum I gave that contradicts written...
You can select which kind of upgrade You want to try in Synaptic...
Not to mention apt-get and aptitude...

Yes I wrote "if manual installation is not counted here", so that much about apt-get or aptitude.
Also, there is absolutely no need for trying to select a different kind of upgrade in Synaptic.
The basic way in Synaptic works very well. It also shows any missing dependencies before the actual installation.

He goes: "If it already works fine, do not try to fix it."

---

### Post by zika on 2013-07-02
> **Harry33 said:**
> Yes I wrote "if manual installation is not counted here", so that much about apt-get or aptitude.
Also, there is absolutely no need for trying to select a different kind of upgrade in Synaptic.
The basic way in Synaptic works very well. It also shows any missing dependencies before the actual installation.

He goes: "If it already works fine, do not try to fix it."I did not get what You mean by &#8222;manual installation&#8220;... Now I'm a bit closer to getting it...
There were situations here in U+1 where &#8222;basic way&#8220; was not able to resolve state... 
Update&#8321;:
Right now I have following choice (in Synaptic also, I hate posting pictures...):
```
:~$ sudo apt-get upgrade Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libmirserver0 unity-system-compositor
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libmirserver0
The following packages will be upgraded:
  unity-system-compositor
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 55.4 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
```
Basic upgrade shows nothing...
Example is not quite nice but it shows the difference...

Never mind, I'm sure we understand each other, even before this discussion...
Everybody has its own tools and perception about those tools...

---

### Post by Harry33 on 2013-07-02
> **zika said:**
> I did not get what You mean by „manual installation“... Now I'm a bit closer to getting it...
There were situations here in U+1 where „basic way“ was not able to resolve state... 
Update&#8321;:
Right now I have following choice (in Synaptic also, I hate posting pictures...):
```
:~$ sudo apt-get upgrade Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libmirserver0 unity-system-compositor
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libmirserver0
The following packages will be upgraded:
  unity-system-compositor
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 55.4 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
```
Basic upgrade shows nothing...
Example is not quite nice but it shows the difference...

Never mind, I'm sure we understand each other, even before this discussion...
Everybody has its own tools and perception about those tools...

Sure we understand each other :).
It is true that Synaptic stumbles also when a bit more complicated downgrading is to be done.

---

### Post by zika on 2013-07-02
> **Harry33 said:**
> Sure we understand each other :).
It is true that Synaptic stumbles also when a bit more complicated **downgrading** is to be done.Was this downgrading?

---

### Post by zika on 2013-07-02
Here is a better example:
```
:~$ sudo apt-get dist-upgrade Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libunity-common libunity-core-6.0-6
The following NEW packages will be installed:
  libunity-core-6.0-7 libunity-scopes-json-def-desktop libvdpau1 mplayer2
  unity-scopes-master-default
The following packages have been kept back:
  libmirserver0 unity-system-compositor
The following packages will be upgraded:
  gir1.2-unity-5.0 libunity9 unity unity-common unity-scope-home
  unity-services youtube-dl
7 upgraded, 5 newly installed, 2 to remove and 2 not upgraded.
Need to get 3,853 kB of archives.
After this operation, 3,304 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
```(it is the same in Synaptic... Again, I'm just more comfortable paste-ing from CLI...)
Without SmartUpgrade libunity9 could not be installed... Not even weeks ahead, never... ;)

Off topic: Unity works nicely, I've lost indicators a week ago, no time to fiddle with that... Just start gnome-panel... ;)
If You know quick fix, do share...

Just as a joke:
Interesting choice (for a guy with ATI)...: ```
The following packages will be REMOVED:  xserver-xorg-input-all xserver-xorg-input-synaptics xserver-xorg-video-all
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-r128 xserver-xorg-video-radeon
The following NEW packages will be installed:
  libmirclient1
The following packages have been kept back:
  libmirserver0 unity-system-compositor
The following packages will be upgraded:
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-fbdev
  xserver-xorg-video-mga xserver-xorg-video-modesetting
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau
  xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware
21 upgraded, 1 newly installed, 9 to remove and 2 not upgraded.
Need to get 0 B/3,163 kB of archives.
After this operation, 2,841 kB disk space will be freed.
Do you want to continue [Y/n]? n
```

---

### Post by Harry33 on 2013-07-03
> **zika said:**
> Was this downgrading?

I meant a number of cases where I have had to downgrade a few packages in order to get my system up again.
Synaptic can be used after a breaking upgrade if done before booting or rebooting.
But like I said above, not always. Sometimes Synaptic cannot resolve complicated dependencies (this is a dependency hell we are in you know :popcorn:).

For those cases I use terminal and Synaptic both.
If that does not work and rebooting will not bring system up, I will use chrooting with terminal.

---

