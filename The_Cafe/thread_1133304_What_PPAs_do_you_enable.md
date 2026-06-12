---
title: "What PPAs do you enable?"
date: 2009-04-22
forum: The Cafe
---

### Post by gnomeuser on 2009-04-22
Personally I have:

Updated Telepathy and Empathy packages:
[http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu)

Updated Banshee packages:
[http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu)

Pulseaudio 0.9.15 (because I want to correctly configure my 5.1 and have better stability)
[http://ppa.launchpad.net/themuso/ppa/ubuntu](http://ppa.launchpad.net/themuso/ppa/ubuntu)

Updated X drivers:
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu)

---

### Post by Namtabmai on 2009-04-22
Wine, I don't really run many windows applications but it's worth running the dev release.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by BGFG on 2009-04-22
How safe are PPA's ? with growing FOSS popularity, could we begin to see malicious PPA's. Something i wonder...

I currently have Docky and Exaile PPA's enabled.

Edit: on re-check I currently have SMPlayer. 
binary:
[http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu)
Source:
[http://ppa.launchpad.net/rvm/ppa/ubuntu](http://ppa.launchpad.net/rvm/ppa/ubuntu)

---

### Post by gnomeuser on 2009-04-22
> **BGFG said:**
> How safe are PPA's ? with growing FOSS popularity, could we begin to see malicious PPA's. Something i wonder...

I currently have Docky and Exaile PPA's enabled.

It depends on how you look at it, all PPAs are signed with their own key. You can thus be sure when you install them that the packages have passed through that PPA. What someone puts in a PPA is though entirely up to them and as such no safer than how much you trust them. In the PPA you can see the data that went through the build system so you can track what goes on your system down to the specific code changes. Given the signing you can also be reasonably sure that the package you install is the package you inspect in the PPA.

Still I only enable PPAs from people I trust and I know to do good work that can be counted on.

As a packager your name is right on there, it can be tracked down to you. Doing anything evil would leave a very clear trail of breadcrumbs to your door. If anyone was caught doing this he would instantly be experiencing the full wrath of the community.

---

### Post by pelle.k on 2009-04-22
I'm pretty satisfied with jaunty as it is. Also, i usually just download the package i want from the PPA instead of adding the repo. I have had enough surprises with regressions (winehq repo), and rolling updates from arch linux. The reason i run ubuntu is because it's in a "frozen" state. If i introduce new packages to the system i prefer to do it selectively.
Having said that, i will probably update gnome-do when it hits 0.8.2 though. ( [https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa) )

---

### Post by Tibuda on 2009-04-22
I use these:
[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)
[https://launchpad.net/~transmissionbt-beta/+archive/ppa](https://launchpad.net/~transmissionbt-beta/+archive/ppa)
[https://launchpad.net/~globalmenu-team/+archive/ppa](https://launchpad.net/~globalmenu-team/+archive/ppa)
[https://launchpad.net/~spring/+archive/ppa](https://launchpad.net/~spring/+archive/ppa)

In intrepid I also had the do-testers PPA.

---

### Post by ghindo on 2009-04-22
[LIST][*]Midori ([https://launchpad.net/~midori/+archive/ppa](https://launchpad.net/~midori/+archive/ppa)) (Dependent on the Webkit PPA)
[*]Webkit ([https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa))
[*]Chromium ([https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)) (Very unstable)
[*]Shutter ([https://launchpad.net/~shutter/+archive/ppa](https://launchpad.net/~shutter/+archive/ppa))
[*]Daily Mozilla builds (Firefox 3.5/3.6) ([https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa))[/LIST]I was actually thinking about starting a thread like this.  I'm really interested to see what other people use!

---

### Post by Aaron44126 on 2009-04-22
Quite a few...  Here's all my extra repos (not all are PPA).

Google (though I don't use anything from that one at the moment), Medibuntu, MkvToolNix, NX, Opera, Pidgin, Shutter, Ubuntu Tweak, VirtualBox, and Wine.  I think this is a really great way of distributing software!  Hope to see more people distributing their application through PPA (or an off-site Debian repository) in the future.

```
deb http://dl.google.com/linux/deb/ stable non-free #Google

deb http://packages.medibuntu.org/ jaunty free #Medibuntu free
deb-src http://packages.medibuntu.org/ jaunty free #Medibuntu free

deb http://packages.medibuntu.org/ jaunty non-free #Medibuntu non-free
deb-src http://packages.medibuntu.org/ jaunty non-free #Medibuntu non-free

deb http://www.bunkus.org/ubuntu/intrepid/ ./ #MkvToolNix INTREPID
deb-src http://www.bunkus.org/ubuntu/intrepid/ ./ #MkvToolNix INTREPID

deb http://ppa.launchpad.net/freenx-team/ubuntu jaunty main #NX
deb-src http://ppa.launchpad.net/freenx-team/ubuntu jaunty main #NX

deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 postscript-ricoh #OpenPrinting Ricoh drivers

deb http://deb.opera.com/opera/ stable non-free #Opera

deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main #Pidgin
deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty main #Pidgin

deb http://ppa.launchpad.net/shutter/ppa/ubuntu jaunty main #Shutter
deb-src http://ppa.launchpad.net/shutter/ppa/ubuntu jaunty main #Shutter

deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main #Ubuntu Tweak
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main #Ubuntu Tweak

deb http://download.virtualbox.org/virtualbox/debian intrepid non-free #VirtualBox INTREPID

deb http://wine.budgetdedicated.com/apt jaunty main #WineHQ
```

---

### Post by Mr. Picklesworth on 2009-04-23
Lots!


Medibuntu:
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

Bleeding edge banshee:
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) jaunty main

Gnome Do:
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) jaunty main

Telepathy:
deb [http://ppa.launchpad.net/telepathy/ubuntu](http://ppa.launchpad.net/telepathy/ubuntu) jaunty main

Webkit Stuff (including early epiphany-webkit 2.27, which is the version that may actually become stable this time):
deb [http://ppa.launchpad.net/webkit-team/ubuntu](http://ppa.launchpad.net/webkit-team/ubuntu) jaunty main

Wine:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main

Mono:
deb [http://ppa.launchpad.net/mono-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/mono-ubuntu/ppa/ubuntu) jaunty main

Gwibber:
deb [http://ppa.launchpad.net/gwibber-team/ppa/ubuntu](http://ppa.launchpad.net/gwibber-team/ppa/ubuntu) jaunty main

Vala:
deb [http://ppa.launchpad.net/vala-team/ppa/ubuntu](http://ppa.launchpad.net/vala-team/ppa/ubuntu) jaunty main

Breathe icon set:
deb [http://ppa.launchpad.net/breathe-dev/ppa/ubuntu](http://ppa.launchpad.net/breathe-dev/ppa/ubuntu) jaunty main

Bleeding edge liferea (which uses webkit!):
deb [http://ppa.launchpad.net/liferea/ppa/ubuntu](http://ppa.launchpad.net/liferea/ppa/ubuntu) jaunty main

Midori:
deb [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) jaunty main

Chromium:
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main


I love my PPAs. And web browsers, apparently :)

---

### Post by rileinc on 2009-04-23
Deluge: [https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)
Exaile: [https://launchpad.net/~exaile-devel/+archive/ppa](https://launchpad.net/~exaile-devel/+archive/ppa)
IPlist: [https://launchpad.net/~ssakar/+archive/ppa](https://launchpad.net/~ssakar/+archive/ppa)
Open Office: [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)
Mono (includes moonlight): [https://launchpad.net/~mono-ubuntu/+archive/ppa](https://launchpad.net/~mono-ubuntu/+archive/ppa)
Compiz: [https://launchpad.net/~compiz/+archive/ppa](https://launchpad.net/~compiz/+archive/ppa)
Gnome Do: [https://launchpad.net/~do-core/+archive/ppa](https://launchpad.net/~do-core/+archive/ppa)
Wine: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)
Dropbox: [http://www.getdropbox.com/downloading?os=lnx](http://www.getdropbox.com/downloading?os=lnx)

---

### Post by ubuntu27 on 2009-04-23
Since I have Ubuntu 8.10 (Intrepid Ibex) **OpenOffice.org Scribblers**:
[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)


[Shutter]("http://shutter-project.org/") Team:
[https://launchpad.net/~shutter/+archive/ppa](https://launchpad.net/~shutter/+archive/ppa)


PPA for Pidgin Developers:
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)


[Ubuntu Tweak]("http://ubuntu-tweak.com/"):

[http://ubuntu-tweak.com/2008/01/22/ubuntu-tweak-has-repository-now.html](http://ubuntu-tweak.com/2008/01/22/ubuntu-tweak-has-repository-now.html)

---

### Post by spcwingo on 2009-04-23
I use a few:

```
1) Ubuntu Tweak: deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main #Ubuntu Tweak
2) Wine: deb http://wine.budgetdedicated.com/apt hardy main #Wine
3) Medibuntu: deb http://packages.medibuntu.org/ hardy free non-free #Medibuntu
4) Virtualbox: deb http://download.virtualbox.org/virtualbox/debian hardy non-free
5) Remastersys: deb http://www.remastersys.klikit-linux.com/repository remastersys/
6) Ypops: deb http://tskariah.net78.net/ubuntu ubuntu main
7) Deluge: deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu hardy main
8) gtkhash: deb http://ppa.launchpad.net/nicolai-spohrer/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/nicolai-spohrer/ppa/ubuntu hardy main
9) Google: deb http://dl.google.com/linux/deb/ stable non-free #google
10) unetbootin: deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/gezakovacs/ppa/ubuntu hardy main

11) --># PulseAudio Fixes - http://ubuntuforums.org/showthread.php?t=789578
deb http://ppa.launchpad.net/psyke83/ubuntu hardy main
deb-src http://ppa.launchpad.net/psyke83/ubuntu hardy main

```

---

### Post by directhex on 2009-04-23
> **Mr. Picklesworth said:**
> Mono:
deb [http://ppa.launchpad.net/mono-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/mono-ubuntu/ppa/ubuntu) jaunty main

I have to ask... who the hell are these people? We've *never* heard of or from them within the Debian Mono Group. They certainly don't maintain Mono in Ubuntu as their PPA claims (I do!)

---

### Post by itreius on 2009-04-23
Usually it's mozilla-daily (to get the latest beta of firefox, be it firefox-3.5 or firefox-3.6), and chromium-browser.

---

### Post by gnomeuser on 2009-04-23
> **directhex said:**
> I have to ask... who the hell are these people? We've *never* heard of or from them within the Debian Mono Group. They certainly don't maintain Mono in Ubuntu as their PPA claims (I do!)

As I remember the effort was start with the sole purpose of providing 2.0 for Intrepid. Perhaps though it should carry some bigger warnings such as "not DMG approved"

---

### Post by amitabhishek on 2009-04-23
Call me ignorant but what are PPAs?

---

### Post by gnomeuser on 2009-04-23
> **amitabhishek said:**
> Call me ignorant but what are PPAs?

Personal Package Archives. Typically a PPA would be used by developers or maintainers of a given application to ensure that users have the latest version (or to do pre SRU testing of fixes). E.g. if you look at an application like Banshee, it is very likely that it will have important bugfixes and feature updates in the lifetime of an Ubuntu release but policy does not easily allow to push these to the stable repos. Since upstream is only interested in supporting thr latest release this poses a problem. PPAs are a way to address this.

Now at their base, they are a some what bad idea as well as a good one. It is easy to cause a lot of problems this way but it is also a powerful tool to let users and developer do important testing and upgrades.

Naturally they do no big favors to QA which is a problem.

---

### Post by Laibcoms on 2009-04-23
Now that Jaunty has been released, I started activating the PPAs I use.. the following are:

> 
Mozilla Team
    [https://launchpad.net/~mozillateam]("https://launchpad.net/%7Emozillateam")
    deb [http://ppa.launchpad.net/mozillateam/ppa/ubuntu](http://ppa.launchpad.net/mozillateam/ppa/ubuntu) jaunty main
    deb-src [http://ppa.launchpad.net/mozillateam/ppa/ubuntu](http://ppa.launchpad.net/mozillateam/ppa/ubuntu) jaunty main
    KEY: gpg --keyserver pgp.mit.edu --recv CE49EC21 && gpg --export -a CE49EC21 | sudo apt-key add -

Ubuntu Mozilla Daily Build
    [https://launchpad.net/~ubuntu-mozilla-daily]("https://launchpad.net/%7Eubuntu-mozilla-daily")
    deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
    deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
    KEY: gpg --keyserver pgp.mit.edu --recv 247510BE && gpg --export -a 247510BE | sudo apt-key add -

OpenOffice.org Scribblers (don't use for Jaunty [yet??])
    [https://launchpad.net/~openoffice-pkgs]("https://launchpad.net/%7Eopenoffice-pkgs")
    deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
    deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
    KEY: gpg --keyserver pgp.mit.edu --recv 247D1CFF && gpg --export -a 247D1CFF | sudo apt-key add -

Get Dropbox (file sync)
    deb [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) jaunty main
    deb-src [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) jaunty main
    KEY: gpg --keyserver pgp.mit.edu --recv 3565780E && gpg --export -a 3565780E | sudo apt-key add -

WINE
    [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
    deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
    KEY: [http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg](http://wine.budgetdedicated.com/apt/Scott%20Ritchie.gpg)

WebKit (dependency of Midori PPA)
    [https://launchpad.net/~webkit-team]("https://launchpad.net/%7Ewebkit-team")
    deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
    deb-src [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
    KEY: gpg --keyserver keyserver.ubuntu.com --recv 2D9A3C5B && gpg --export -a 2D9A3C5B | sudo apt-key add -

Midori (requires WebKit PPA)
    [https://launchpad.net/~midori]("https://launchpad.net/%7Emidori")
    deb [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) jaunty main
    deb-src [http://ppa.launchpad.net/midori/ppa/ubuntu](http://ppa.launchpad.net/midori/ppa/ubuntu) jaunty main
    KEY: gpg --keyserver keyserver.ubuntu.com --recv A69241F1 && gpg --export -a A69241F1 | sudo apt-key add -

Pidgin
    [https://launchpad.net/%7Epidgin-developers](https://launchpad.net/%7Epidgin-developers)
    deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main
    deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main
    KEY: gpg --keyserver keyserver.ubuntu.com --recv A1F196A8 && gpg --export -a A1F196A8 | sudo apt-key add -

CompizFusion
    [https://launchpad.net/~compiz]("https://launchpad.net/%7Ecompiz")
    deb [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) jaunty main
    deb-src [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) jaunty main
    KEY: gpg --keyserver keyserver.ubuntu.com --recv 42C24D89 && gpg --export -a 42C24D89 | sudo apt-key add -

Ubuntu-Tweak
    [https://launchpad.net/~tualatrix]("https://launchpad.net/%7Etualatrix")
    deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main
    deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main
    KEY: gpg --keyserver keyserver.ubuntu.com --recv 0624A220 && gpg --export -a 0624A220 | sudo apt-key add -

Google
    [http://www.google.com/linuxrepositories/testrepo.html](http://www.google.com/linuxrepositories/testrepo.html)
    deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free
    KEY: [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub)

Medibuntu
    deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
    deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
Not yet activated (re-thinking)
> 
Cairo-Dock
Scribus && ScribusNG


---

