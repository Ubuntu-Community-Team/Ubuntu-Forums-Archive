---
title: "How many PPAs do you have enabled ?"
date: 2013-04-08
forum: Ubuntu, Linux and OS Chat
---

### Post by GameX2 on 2013-04-08
Hi,


Many people say that a Linux user should avoid adding PPAs if possible.
But how much is too much?  They are software with PPAs that do not have  an equivalent in the repositories.  I was wondering if I have *too many* PPAs.  How many do you have ?

I've got these:

[http://img163.imageshack.us/img163/9113/sourcesw.png](http://img163.imageshack.us/img163/9113/sourcesw.png)

SNES9x, CDEmu, Gedit-Plugins, Cinnamon Desktop, GRUB-Customizer, Ubuntu  Tweak, Clementine Music Lens, Wine 1.5, Gloobus Preview (A "Quick Look" Mac OS X function equivalent), Boot-Repair, Dropbox, GNOME3, Bookmark Lens,  Dolphin Emulator and Python (I use an older Blender version, 2.49b; it's  needed).

I think that's a lot..
How many PPAs do have have in your Sources ?

---

### Post by deadflowr on 2013-04-08
Does google-chrome count?

Otherwise, surprisingly none.

But that doesn't mean I'm against the PPA system, it just means I'm totally fine with the packages provided in the repos as of now.

I don't think you have too many. It just means you would rather have newer, or sometimes unavailable in the repo, packages.

Nothing wrong with that.

---

### Post by monkeybrain2012 on 2013-04-08
> **GameX2 said:**
> Hi,


Many people say that a Linux user should avoid adding PPAs if possible.
  

I ignore them, usually fear mongerings by ultra conservative users (the kind who tell you to only use LTS and hope that 10.04 will be supported for 100 years :)). I have lots of ppas especially for multimedia stuffs for which the repo versions are not only outdated, but sometimes broken or otherwise crippled. I want new features and bug fixes rather than "stability" in the sense of predictability crippled or broken. IMO the risk is vastly exaggerated provided you use ppa only for end user applications but not system components (I have had issues with xorg-edgers in some machines but ppa-purge fixed it.

---

### Post by samsom63 on 2013-04-08
I don't see why there would be a "maximal" number of installed PPAs...Do as you please, I also enjoy quite "a few" programmes that way :)

---

### Post by pqwoerituytrueiwoq on 2013-04-08
all i expect to be using as of 13.04 are these
xfce 4.12 (only has 1 pacakges last i checked for raring)
getdeb/playdeb (using the quantal version here, till raring is added)
medibuntu
xswat
i also enable Canonical parters and independent that are disabled by default

---

### Post by Jakin on 2013-04-08
Amarok-experimental
handbrake
cairo-dock stable
Chromium stable
Steam
LibreOffice
Google Earth
Webupd8
Kubuntu Backports
grub customizer
spotify

---

### Post by Frogs Hair on 2013-04-08
I have been using theme PPAs the last few releases because I can shop from synaptic and view at pictures on gnome look. I am ruining the Unity Tweak Tool which has 13,04 source and use dockbarx on XFCE also .  [http://ppa.webupd8.org/post/45438344458/dockbarx-packages-now-available-for-ubuntu-13-04-raring](http://ppa.webupd8.org/post/45438344458/dockbarx-packages-now-available-for-ubuntu-13-04-raring). It possible one could end up with dependency problems if conflicting packages were installed.

---

### Post by zer010 on 2013-04-08
Apparently, I only have two.
ubuntu-x-swat
bumblebee

Care to take a guess as to why? -_-

---

### Post by drawkcab on 2013-04-09
More than a few...mostly to enable multimedia support on certain machines as well as a few apps that I need.

---

### Post by Roasted on 2013-04-09
The only one I have enabled is Gnome3 on 13.04 to get a sense of Gnome 3.8. I'm not against PPAs at all, but when I see random PPAs that aren't entirely necessary (such as a theme or something) I don't exactly think highly of that. PPAs for more core functionality is something I feel a bit differently about though.

---

### Post by Max Blyss on 2013-04-09
I add a couple for some themes and icons, Google Chrome, etc...  Prob 5 or so currently.  Have used others / more in the past with no problems.

---

### Post by Moose on 2013-04-09
As many as I require..?

This is a strange question. ahaha ;)

---

### Post by rrich1974 on 2013-04-09
i only have PPAs for google chrome (the best browser ever), wine and caffeine (i dont understand why such a useful piece of software is missing from the software center)....
and now, i am thinking about adding a smplayer PPA because i am not pleased by my actual smplayer.

---

### Post by Perfect Storm on 2013-04-09
Moved from ubuntu 12.10 to testing Ubuntu 13.04 beta, so I don't have many PPAs available (yet).
Got;
Google chrome
Steam
medibuntu
and private ppas for stuff I bought in Ubuntu Software Center.

---

### Post by ka55o5 on 2013-04-09
> **GameX2 said:**
> How many PPAs do have have in your Sources ?
Besides using [sources]("https://help.ubuntu.com/community/SourcesList"), imo it's better to use [add-apt-repository]("https://help.ubuntu.com/community/Repositories/Ubuntu") - where everything will go into separate files @ **/etc/apt/sources.list.d**

.. just neater that way. :-d

> **monkeybrain2012 said:**
> I ignore them [..]
The system can *easily* be compromised, by using teh wrong repo. ;$ Sometimes, though, there'll be a [warning]("http://forums.avg.com/us-en/avg-forums?sec=thread&act=show&id=227512").

PS.
> **Roasted said:**
> I'm not against PPAs at all, but when I see random PPAs that aren't entirely necessary [..]+1

---

### Post by iamkuriouspurpleoranj on 2013-04-10
None. Unless Medibuntu counts.

---

### Post by pinballwizard on 2013-04-10
> **GameX2 said:**
> Hi,


Many people say that a Linux user should avoid adding PPAs if possible.


Then I'd contend that there's a huge gap between Ubuntu users and Linux users.

---

### Post by monkeybrain2012 on 2013-04-10
> **ka55o5 said:**
> 

The system can *easily* be compromised, by using teh wrong repo. ;$ Sometimes, though, there'll be a [warning]("http://forums.avg.com/us-en/avg-forums?sec=thread&act=show&id=227512").



How easy is "easily"? I think you exaggerated. It would be risky if you install from random repositories, but it is as safe as it can be if you install from reputable ppas such as those hosted on Launchpad or the google-chrome (google-earth) ppa Your link is from AVG, I wouldn't install such thing on Linux in the first place.

Edited: Also you can minimize risk of breakage if you only use ppas for end user software without a lot of external dependencies (as opposed to system components) and install ppa-purge just in case (I only have to purge some "high risk" ppas such as xorg-edgers or Unity on a few occasions but even then there was no irreparable damage, purged and rebooted I was back in business)

---

### Post by evilsoup on 2013-04-10
> **monkeybrain2012 said:**
> I ignore them, usually fear mongerings by ultra conservative users (the kind who tell you to only use LTS and hope that 10.04 will be supported for 100 years :)). I have lots of ppas especially for multimedia stuffs for which the repo versions are not only outdated, but sometimes broken or otherwise crippled. I want new features and bug fixes rather than "stability" in the sense of predictability crippled or broken. IMO the risk is vastly exaggerated provided you use ppa only for end user applications but not system components (I have had issues with xorg-edgers in some machines but ppa-purge fixed it.

The main point is that you should be careful which PPAs you enable - those linked from the official websites of projects are probably safe, but do bear in mind that anyone can set one up, and there is no vetting process at launchpad to stop them from disguising malware or spyware as something benign. You are essentially trusting the owner of the PPA with root access to your computer.

---

### Post by TeamRocket1233c on 2013-04-10
Cinnamon, E17, and MATE are the major ones, I also have a few theme PPAs as well.

---

### Post by Version Dependency on 2013-04-10
A few...the ones probably many of you also have...VirtualBox, Steam, Opera, playdeb, etc.

---

### Post by TeamRocket1233c on 2013-04-10
Virtualbox is already in the repos.

---

### Post by iamkuriouspurpleoranj on 2013-04-10
Ubuntu is quite complete and I don't think there's ever a need for PPAs. For OpenSUSE and Arch, this kind of thing is more necessary. OpenSUSE for example has neither Eclipse nor NetBeans in its standard repos.

---

### Post by TeamRocket1233c on 2013-04-10
There's still some stuff that you need the PPAs for: most notably, Cinnamon, MATE, and E17.

---

### Post by monkeybrain2012 on 2013-04-10
> **TeamRocket1233c said:**
> Virtualbox is already in the repos.

Only if you don't need features from the Oracle version.

---

### Post by andrew.46 on 2013-04-10
No PPAs here, I build the applications I need. That way I know who to blame when it goes wrong :)

---

### Post by Cheesemill on 2013-04-11
VirtualBox
Steam
Oracle Java (WebUpd8)

Strictly speaking the only one that is a PPA is Java, the others aren't hosted on Launchpad so they should just be called repositories.

---

### Post by BrokenKingpin on 2013-04-12
None at the moment actually. I usually have a few (XBMC, etc.), but as of right now I can get what I need from the standard repos.

---

### Post by iamkuriouspurpleoranj on 2013-04-12
Think Cinnamon's in 13.04. If you want MATE with Ubuntu run Mint.

E17?
[[img]http://ompldr.org/taTJuYg[/img]](http://ompldr.org/vaTJuYg/e17.png)

Need I say more?

---

### Post by scouser73 on 2013-04-15
Here you go.

[IMG]http://ompldr.org/vaTNuaA/PPAs.png[/IMG]

---

### Post by slickymaster on 2013-04-15
Just two: Chrome and Cairo Dock.

---

### Post by angryfirelord on 2013-04-15
> **monkeybrain2012 said:**
> I ignore them, usually fear mongerings by ultra conservative users (the kind who tell you to only use LTS and hope that 10.04 will be supported for 100 years :)). I have lots of ppas especially for multimedia stuffs for which the repo versions are not only outdated, but sometimes broken or otherwise crippled. I want new features and bug fixes rather than "stability" in the sense of predictability crippled or broken. IMO the risk is vastly exaggerated provided you use ppa only for end user applications but not system components (I have had issues with xorg-edgers in some machines but ppa-purge fixed it.
It depends. The main issue in adding 3rd party repositories is that you're trusting that the package maintainer will still keep a sane list of dependencies. Suppose you add two PPAs where the first program requires library foo at version 1.5, but the other program requires it at version 1.6. You can easily spawn a dependency hell if the package maintainer didn't set the program's dependencies properly.

This is an example of what can go wrong: [http://askubuntu.com/questions/9793/ppa-build-failed-because-of-unmet-dependencies-of-another-package-in-the-same-pp]("http://askubuntu.com/questions/9793/ppa-build-failed-because-of-unmet-dependencies-of-another-package-in-the-same-pp")

Of course, if your PPA doesn't work, you can always compile the program from source. Because of the large amounts of packages already available, you can easily grab all of the dependencies using build-dep and then compile the program from there.

---

### Post by ka55o5 on 2013-04-18
> **monkeybrain2012 said:**
> [QUOTE=ka55o5;12596025]The system can *easily* be compromised, by using teh wrong repo. ;$How easy is "easily"?[/QUOTE]
Hey, I think evilsoup elaborated nicely right [underneath your post]("http://ubuntuforums.org/showthread.php?t=2133555&page=2&p=12596806&viewfull=1#post12596806").

&& just btw., looking for the [source-o-matic]("https://answers.launchpad.net/ubuntu-nl-website/+question/22521"); found a nice link there, to:
```
http://repogen.simplylinux.ch/
```

---

### Post by Erik1984 on 2013-04-18
None on my 'real' install of Ubuntu 12.10. In the virtual install of 12.10 I have added the MATE repository to my sources.list. But as it's not hosted on Launchpad I don't know if it's technically a PPA?

---

