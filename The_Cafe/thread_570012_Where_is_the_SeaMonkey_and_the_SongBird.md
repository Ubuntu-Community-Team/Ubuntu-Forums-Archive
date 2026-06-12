---
title: "Where is the SeaMonkey and the SongBird?"
date: 2007-10-07
forum: The Cafe
---

### Post by RAV TUX on 2007-10-07
```
ravtux@CafeLinux:~$ sudo apt-get install seamonkey
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package seamonkey
ravtux@CafeLinux:~$ sudo apt-get install songbird
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package songbird

```

---

### Post by n3tfury on 2007-10-07
knocking boots?

---

### Post by p_quarles on 2007-10-07
Iceape is in the Debian stable repo, but I suppose you knew that already. I've always guessed that Ubuntu doesn't distribute it because their versions of the Mozilla products are special builds, and there's probably not a huge amount of demand. 

As for Songbird, isn't that still Alpha?

---

### Post by aysiu on 2007-10-07
They don't have packages in the Ubuntu repositories, as far as I know.

---

### Post by RAV TUX on 2007-10-07
> **aysiu said:**
> They don't have packages in the Ubuntu repositories, as far as I know.Not even in Gutsy?...whats the best way to install them?

---

### Post by smartboyathome on 2007-10-07
I would say using the installer from the site.

---

### Post by n3tfury on 2007-10-07
> **p_quarles said:**
> 

As for Songbird, isn't that still Alpha?

it is and as such it's SUPER buggy.  has potential, but i'll wait it out.

---

### Post by RAV TUX on 2007-10-07
> **p_quarles said:**
> Iceape is in the Debian stable repo, but I suppose you knew that already. I've always guessed that Ubuntu doesn't distribute it because their versions of the Mozilla products are special builds, and there's probably not a huge amount of demand. 

  

Actually I didn't know that, IceApe is in Ubuntu Gutsy also! Thanks I just installed the IceApe! ;)

```
ravtux@CafeLinux:~$ sudo apt-get install iceape 
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxtrap-dev libxmuu-dev libxv-dev x11proto-video-dev x11proto-trap-dev
  x11proto-record-dev x11proto-randr-dev libxpm-dev libxrandr-dev libxtst-dev
  x-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  iceape-browser iceape-mailnews
Suggested packages:
  iceape-calendar latex-xft-fonts iceape-dom-inspector
Recommended packages:
  iceape-chatzilla iceape-gnome-support
The following NEW packages will be installed:
  iceape iceape-browser iceape-mailnews
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 11.8MB of archives.
After unpacking 36.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com gutsy/universe iceape-browser 1.1.4-1ubuntu2 [9797kB]
Get:2 http://us.archive.ubuntu.com gutsy/universe iceape-mailnews 1.1.4-1ubuntu2 [1951kB]
Get:3 http://us.archive.ubuntu.com gutsy/universe iceape 1.1.4-1ubuntu2 [29.9kB]
Fetched 11.8MB in 1m11s (165kB/s)
Selecting previously deselected package iceape-browser.
(Reading database ... 164264 files and directories currently installed.)
Unpacking iceape-browser (from .../iceape-browser_1.1.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package iceape-mailnews.
Unpacking iceape-mailnews (from .../iceape-mailnews_1.1.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package iceape.
Unpacking iceape (from .../iceape_1.1.4-1ubuntu2_all.deb) ...
Setting up iceape-browser (1.1.4-1ubuntu2) ...
Updating iceape chrome registry...done.

Setting up iceape-mailnews (1.1.4-1ubuntu2) ...
Updating iceape chrome registry...done.

Setting up iceape (1.1.4-1ubuntu2) ...
```

> **p_quarles said:**
> 

As for Songbird, isn't that still Alpha?I guess SongBird is a different story?

---

### Post by aysiu on 2007-10-07
> **RAV TUX said:**
> Not even in Gutsy?...whats the best way to install them?
I'd try one of these methods:
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

And, no, I don't think they're in the repositories, even in Gutsy.

---

### Post by RAV TUX on 2007-10-07
> **RAV TUX said:**
> Actually I didn't know that, IceApe is in Ubuntu Gutsy also! Thanks I just installed the IceApe! ;)

```
ravtux@CafeLinux:~$ sudo apt-get install iceape 
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxtrap-dev libxmuu-dev libxv-dev x11proto-video-dev x11proto-trap-dev
  x11proto-record-dev x11proto-randr-dev libxpm-dev libxrandr-dev libxtst-dev
  x-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  iceape-browser iceape-mailnews
Suggested packages:
  iceape-calendar latex-xft-fonts iceape-dom-inspector
Recommended packages:
  iceape-chatzilla iceape-gnome-support
The following NEW packages will be installed:
  iceape iceape-browser iceape-mailnews
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 11.8MB of archives.
After unpacking 36.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com gutsy/universe iceape-browser 1.1.4-1ubuntu2 [9797kB]
Get:2 http://us.archive.ubuntu.com gutsy/universe iceape-mailnews 1.1.4-1ubuntu2 [1951kB]
Get:3 http://us.archive.ubuntu.com gutsy/universe iceape 1.1.4-1ubuntu2 [29.9kB]
Fetched 11.8MB in 1m11s (165kB/s)
Selecting previously deselected package iceape-browser.
(Reading database ... 164264 files and directories currently installed.)
Unpacking iceape-browser (from .../iceape-browser_1.1.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package iceape-mailnews.
Unpacking iceape-mailnews (from .../iceape-mailnews_1.1.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package iceape.
Unpacking iceape (from .../iceape_1.1.4-1ubuntu2_all.deb) ...
Setting up iceape-browser (1.1.4-1ubuntu2) ...
Updating iceape chrome registry...done.

Setting up iceape-mailnews (1.1.4-1ubuntu2) ...
Updating iceape chrome registry...done.

Setting up iceape (1.1.4-1ubuntu2) ...
```I guess SongBird is a different story?

I installed the suggested packages for IceApe also:

```
Suggested packages:
  iceape-calendar latex-xft-fonts iceape-dom-inspector
Recommended packages:
  iceape-chatzilla iceape-gnome-support
```Except for iceape-calendar

This is what I got when trying to install the IceApe calendar:

```
ravtux@CafeLinux:~$ sudo apt-get install iceape-calendar
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package iceape-calendar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package iceape-calendar has no installation candidate
```Does anybody know the right name or candidate for the IceApe calendar?

or where I can get it at?

---

### Post by RAV TUX on 2007-10-07
> **aysiu said:**
> I'd try one of these methods:
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

And, no, I don't think they're in the repositories, even in Gutsy.

Thanks aysiu I have the IceApe(Debian version of the SeaMonkey) installed, I will try your link for the SongBird.

---

### Post by p_quarles on 2007-10-07
> **RAV TUX said:**
> Does anybody know the right name or candidate for the IceApe calendar?

or where I can get it at?
That one is in the Debian stable main repo (and the package name = "iceape-calendar"). I s'pose you could try temporarily enabling that repository to install the one package. I honestly don't know whether that's a good idea or not, though. :)

---

### Post by user1397 on 2007-10-07
Rav, you can always check if there is a certain package available for whatever version of ubuntu in [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by p_quarles on 2007-10-07
> **ubuntuman001 said:**
> Rav, you can always check if there is a certain package available for whatever version of ubuntu in [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Even easier (I think) is:
```
apt-cache search *keyword(s)*
```

---

### Post by FuturePilot on 2007-10-07
> **p_quarles said:**
> Even easier (I think) is:
```
apt-cache search *keyword(s)*
```

That's what I do.

---

### Post by smartboyathome on 2007-10-07
> **p_quarles said:**
> That one is in the Debian stable main repo (and the package name = "iceape-calendar"). I s'pose you could try temporarily enabling that repository to install the one package. I honestly don't know whether that's a good idea or not, though. :)

That is not a good idea. Instead, you might want to update your apt-get sources, and THEN install it. I usually get that error when the package has been updated on the server and not on my package list.

---

### Post by RAV TUX on 2007-10-07
> **ubuntuman001 said:**
> Rav, you can always check if there is a certain package available for whatever version of ubuntu in [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Thanks for the link I have added Gutsy package searches to my Firefox search bar.

> **p_quarles said:**
> Even easier (I think) is:
```
apt-cache search *keyword(s)*
```

Thanks I like this way best.

> **FuturePilot said:**
> That's what I do.

I can see why.

> **smartboyathome said:**
> That is not a good idea. Instead, you might want to update your apt-get sources, and THEN install it. I usually get that error when the package has been updated on the server and not on my package list.

Thanks for the 411, updating now.

---

### Post by 23meg on 2007-10-07
> **FuturePilot said:**
> That's what I do.

You can't search for packages in other releases than the one you're using with apt-cache, though. For that, you need [madison-lite]("http://packages.ubuntu.com/feisty/admin/madison-lite").

---

### Post by RAV TUX on 2007-10-07
> **smartboyathome said:**
> That is not a good idea. Instead, you might want to update your apt-get sources, and THEN install it. I usually get that error when the package has been updated on the server and not on my package list.

tried the update and still is not available, searched the Gutsy packages and it's not listed.

It must not be available? ;)

---

### Post by FuturePilot on 2007-10-07
> **23meg said:**
> You can't search for packages in other releases than the one you're using with apt-cache, though. For that, you need [madison-lite]("http://packages.ubuntu.com/feisty/admin/madison-lite").

Hey, that's cool!:)
Now I want to try it:p

---

### Post by misfitpierce on 2007-10-07
Songbird can be found at getdeb.net

---

### Post by RAV TUX on 2007-10-07
> **misfitpierce said:**
> Songbird can be found at getdeb.net
ahhh...Thank you!....there now and I have bookmarked the website! ;)

---

### Post by p_quarles on 2007-10-07
> **smartboyathome said:**
> That is not a good idea. Instead, you might want to update your apt-get sources, and THEN install it. I usually get that error when the package has been updated on the server and not on my package list.
I was guessing it was a bad idea, given that you could seriously confuse your apt-available file. Have you tried this? I'm curious enough to give it a go myself when I'm prepared to bork my system.

> **RAV TUX said:**
> tried the update and still is not available, searched the Gutsy packages and it's not listed.

It must not be available? ;)
One more reason to love Debian: packages available via standard http:
[http://packages.debian.org/etch/iceape-calendar](http://packages.debian.org/etch/iceape-calendar)

---

### Post by RAV TUX on 2007-10-07
> **misfitpierce said:**
> Songbird can be found at getdeb.net

> **RAV TUX said:**
> ahhh...Thank you!....there now and I have bookmarked the website! ;)

...and someone has been kind enough to have created a YubNub command line prompt

```
getdeb
```

Thanks, I was just going to create it and I found out it has already been done, good to see more people are using YubNub and command lines for the web! ;)

[http://yubnub.org/](http://yubnub.org/)

---

### Post by user1397 on 2007-10-07
> **p_quarles said:**
> Even easier (I think) is:
```
apt-cache search *keyword(s)*
```

> **FuturePilot said:**
> That's what I do.yea but that only works for whatever version of ubuntu you have installed, that's why I said for "any" version.

---

### Post by RAV TUX on 2007-10-07
> **misfitpierce said:**
> Songbird can be found at getdeb.net


I just wanted to Thank You the Songbird install from getdeb works flawlessly!

Here a screenshot tour of the SongBird Install:

** Installing Songbird 0.2.5.1 in Xubuntu 7.10 (e17 Smoke Theme, Circuit animated background)**
[[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_snapshot62.png[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?album=lastup&cat=0&pos=2")

**                                                 Setting up Songbird 0.2.5.1 in Xubuntu 7.10 (e17 Smoke Theme)**
[[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_songbird.png[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?album=lastup&cat=0&pos=4")
[B]
Songbird 0.2.5.1 in Xubuntu 7.10 (e17 Smoke Theme)[/B]
[[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_snapshot63.png[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?album=lastup&cat=0&pos=3")

**                                                 Songbird 0.2.5.1, GNOME ALSA-Mixer in Xubuntu 7.10 (e17 Smoke Theme)**
[[IMG]http://cafelinux.org/OptickleArt/albums/userpics/normal_snapshot66.png[/IMG]]("http://cafelinux.org/OptickleArt/displayimage.php?album=lastup&cat=0&pos=0")

---

### Post by picpak on 2007-10-07
IceApe is in Gutsy now? That's good, because to get it for Feisty I had emailed getdeb to compile debs for it.

---

