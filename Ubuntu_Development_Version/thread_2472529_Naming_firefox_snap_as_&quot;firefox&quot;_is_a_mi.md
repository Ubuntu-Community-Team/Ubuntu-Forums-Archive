---
title: "Naming firefox snap as &quot;firefox&quot; is a mistake"
date: 2022-03-02
forum: Ubuntu Development Version
---

### Post by FarJumper on 2022-03-02
Naming a new firefox deb package which is actually a snap as "firefox" is a mistake. Number of reasons:

* It's named as firefox, which clashes with the non-snap version
* The version number chosen so that it's always wins
* You are forcing users to switch to snap, not giving a chance to use another options (PPAs)

The solution would be to package it as "firefox-snap". Any reason why we don't do that?

---

### Post by corradoventu on 2022-03-02
Up to now you can have both firefox .deb and snap, they don't conflict an can be run at the same time
```
corrado@corrado-p5-jj-0203:~$ snap list firefox
Name     Version   Rev   Tracking         Publisher  Notes
firefox  97.0.1-1  1025  latest/stable/…  mozilla&#10003;   -
corrado@corrado-p5-jj-0203:~$ apt policy firefox
firefox:
  Installed: 97.0.1+build1-0ubuntu1
  Candidate: 97.0.1+build1-0ubuntu1
  Version table:
 *** 97.0.1+build1-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
corrado@corrado-p5-jj-0203:~$ 

```

---

### Post by FarJumper on 2022-03-02
not in `proposed`:

```

$ apt policy firefox
firefox:
  Installed: 97.0.1+build1-0ubuntu1
  Candidate: 1:1snap1-0ubuntu1
  Version table:
     1:1snap1-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-proposed/main amd64 Packages
 *** 97.0.1+build1-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by corradoventu on 2022-03-02
After update  with proposed enabled my firefox deb disappeared and only the snap version remain.

---

### Post by ajgreeny on 2022-03-02
> The solution would be to package it as "firefox-snap". Any reason why we don't do that? 
We (ie Ubuntu or this forum) don't do that because we do not create the snap packages as far as I'm aware; I believe they all come from another organisation, though I will admit that I do not have any snaps on my Xubuntu installs (20.04 and 22.04) and if it is possible I will not allow them on my system.

This post is just my personal thoughts on snaps and not Canonical's or Ubuntuforum's way of running the systems they create, but this is just about the first and only time that I think Canonical or Ubuntu have chosen a path down which I do not wish to go.
I find all snaps too cumbersome to use, to slow to start, even after a first very, very slow start, they take away my ability to manage them myself as far as upgrades of the snap are concerned, and stop me accessing files on my drives if not where the snap infrastructure allows them, and they seem to use so much more disk space than a normal install.

I am aware of all the arguments for and against snaps, but I'm sorry, I will try as hard as I can not to have to use them.
It's up to all users to make their own choice about this and I'm sure many will just continue to use what is most easily available, probably snaps.

---

### Post by grahammechanical on 2022-03-02
> You are forcing users to switch to snap, not giving a chance to use another options (PPAs)

I am not forcing anybody! You are complaining to the wrong people. Please consider these two quotations from the Debian website

> Mozilla provides an official [FlatPak]("https://wiki.debian.org/FlatPak") at [FlatHub]("https://flathub.org/apps/details/org.mozilla.firefox").

> Mozilla provides an official Snap package for Firefox:

[https://wiki.debian.org/Firefox](https://wiki.debian.org/Firefox)

Flatpak and Snap have similar aims. And then there is Appimage which takes a different approach.

[https://appimage.github.io/Firefox7](https://appimage.github.io/Firefox7)

Whether  we like it or not there have been developments for years to break from  the packaging division in Linux. Redhat Package Manager = rpm. Debian  package format = deb. 

Regards

---

### Post by zika on 2022-03-02
You could, always, use [https://www.mozilla.org/en-US/firefox/linux/](https://www.mozilla.org/en-US/firefox/linux/). One simple symbolic link or, even, alias, and You have Firefox that updates /upgrades itself... Less than few minutes and job done.

---

### Post by mIk3_08 on 2022-03-03
> **FarJumper said:**
> Naming a new firefox deb package which is actually a snap as "firefox" is a mistake. Number of reasons:
* It's named as firefox, which clashes with the non-snap version
* The version number chosen so that it's always wins
* You are forcing users to switch to snap, not giving a chance to use another options (PPAs)

The solution would be to package it as "firefox-snap". Any reason why we don't do that? 
Actually, this is great. But how about the other packages/apps do we have to name them as snap as well? 
I think, canonical have to discuss about this matter. regards

---

### Post by grahammechanical on 2022-03-03
I have had both the snap and deb versions of Firefox on my system. As  stated above they do not clash. They do use the same icons. Well, they  would wouldn't they? So, we get two Firefox icons in Activities. I ended  the confusion by making sure that the icon in the Dash was for the  version I preferred to use.

The latest versions of Ubuntu install  the snap version by default. The upgrade from 20.04 to 22.04 will  remove the deb version and install the snap version. There is no  confusion. I do not think that new users who install 22.04 will notice  what package type of Firefox they have on their system.

I have  the feeling that developers of major applications will prefer to package  their application as Flatpak and Snap rather then as rpm & deb  because Flatpak and Snap are distribution independent. If it is easier  and less time consuming upgrading an application that is Flatpak and  Snap packaged than when it is rpm and deb packaged then I think that  developers will in time make the change. This will be especially true if  getting a Flatpak or Snap into a distribution's app store is easier and  quicker than for rpm and deb.

Regards

---

### Post by mIk3_08 on 2022-03-03
> **grahammechanical said:**
> I have had both the snap and deb versions of Firefox on my system. As  stated above they do not clash. 
If this is the case, both runs well so what's the matter? The question is, are they safe to use? But if there are some anomalies in some parts of where they came from then why should we continue using it. 
I think the thing that differs is the 
```
firefox: /usr/bin/firefox /usr/lib/firefox /etc/firefox /snap/bin/firefox /usr/share/man/man1/firefox.1.gz
```
The big thing to this is the build structures. Canonical has to do something about this. Thus this involves security purposes?

---

### Post by grahammechanical on 2022-03-03
> The question is, are they safe to use? 

The answer is: safer to use.

> 
[LIST]
[*]**Sandboxed applications**: one of Flatpak&#8217;s main goals is to increase the security of desktop systems by isolating applications from one another. This is achieved using sandboxing and means that, by default, applications that are run with Flatpak have limited access to the host environment.
[/LIST]

[https://docs.flatpak.org/en/latest/introduction.html#issues-of-current-model-of-packaging](https://docs.flatpak.org/en/latest/introduction.html#issues-of-current-model-of-packaging)

> that snap command file is not the actual application, but rather a link  to the real application under the isolation and confinement rules of the  snap&#8217;s default restricted environment, plus any allowances granted to  it via the interface system.

[https://snapcraft.io/docs/snap-format](https://snapcraft.io/docs/snap-format)

Regards

---

### Post by kurt18947 on 2022-03-06
> **grahammechanical said:**
> 
I have  the feeling that developers of major applications will prefer to package  their application as Flatpak and Snap rather then as rpm & deb  because Flatpak and Snap are distribution independent. If it is easier  and less time consuming upgrading an application that is Flatpak and  Snap packaged than when it is rpm and deb packaged then I think that  developers will in time make the change. This will be especially true if  getting a Flatpak or Snap into a distribution's app store is easier and  quicker than for rpm and deb.

Regards

I think you're correct. My understanding is that the push to snaps (and maybe flatpaks?) was prompted by Mozilla, not Canonical/Ubuntu.

---

### Post by jbicha on 2022-03-08
> **kurt18947 said:**
> I think you're correct. My understanding is that the push to snaps (and maybe flatpaks?) was prompted by Mozilla, not Canonical/Ubuntu.

I think the truth is that it's both. Mozilla has strong opinions on how their browser should be distributed and it's easiest on Ubuntu for that to be done in a snap.

Meanwhile, it is a lot more practical for Canonical to support Firefox on an extended support distro for 10 years if they can use Snaps.

---

### Post by zebra2 on 2022-03-08
It is my understanding that snap is default with Ubuntu 22.04. If not then 22.10.   Hence if it isn't a mistake to call Firefox.deb "Firefox", and it isn't a mistake to call Firefox.rpm "Firefox, then it most definitely is not a mistake to call Firefox.snap "Firefox" especially since it is snap that is default.  I don't take issue with any of the discussions in this thread. I just have a problem with the word "mistake" in the OP.  The use of firefox as a snap and addressed as "Firefox" was intentional and not a mistake.  It is slowly sinking into my mind that this isn't going to go away. The "snap" thing. No mistake about it. Or not!

---

### Post by FarJumper on 2022-03-12
> **zebra2 said:**
> It is my understanding that snap is default with Ubuntu 22.04. If not then 22.10.   Hence if it isn't a mistake to call Firefox.deb "Firefox", and it isn't a mistake to call Firefox.rpm "Firefox, then it most definitely is not a mistake to call Firefox.snap "Firefox" especially since it is snap that is default.  I don't take issue with any of the discussions in this thread. I just have a problem with the word "mistake" in the OP.  The use of firefox as a snap and addressed as "Firefox" was intentional and not a mistake.  It is slowly sinking into my mind that this isn't going to go away. The "snap" thing. No mistake about it. Or not!

Just to clarify. The word "mistake" was not about naming it as firefox but for a tandem of two changes: a) naming snap as firefox + b) bumping the version to "1:1snap1-0ubuntu1" which will always be on top of any other version coming from any other PPAs. Having said that, I sincerely worried for all users who won't have options anymore to use other sources starting from the moment this change is propagated from "proposed" to "main". It's not against using snaps or anything, it's about freedom to have a choice.

---

### Post by Claus7 on 2022-03-12
Hello,

having installed daily jammy in virtualbox, I noticed that (almost) any application available was a snap one. The available options offered (e.g. libreoffice) were only different snap versions without a deb one. Only firefox had two icons for some reason. In order to install flashback first I had to install synaptic via command line: (edit)
sudo apt install synaptic -y
found here: (edit)
[https://www.linuxcapable.com/how-to-install-synaptic-package-manager-on-ubuntu-22-04-lts/](https://www.linuxcapable.com/how-to-install-synaptic-package-manager-on-ubuntu-22-04-lts/)
and then proceed as usual, whereas, up to now, I had the ability to install synaptic via gui using software, yet now software is snap and synaptic was nowhere to be found.

In other words: I do not think that it is just firefox, yet for almost all applications snap is now the default. No?
I do not know if this is like that because jammy is still under development.

Regards!

---

### Post by zebra2 on 2022-03-13
I completely understand the OP in post #15, no question about it.  I have been using the Development version of Ubuntu as my primary install since Ubuntu 9.10 and mostly with 'proposed' enabled since it first appeared. Point is I would have had a serious problematic experience without the somewhat brilliant and knowledgeable users on this and other forums.  To date I have never asked a single question or asked for a single solution on this forum. The answers were there for the googling.  Problem is that I am myself am an experienced technical minded user. 

One should know that the original intent for Ubuntu was for it to be a free OS for African school children. It is on that platform that I have spent numerous hours with the help of the very smart users on this forum to keep this crazy and problem infected path I choose moving forward and delightfully usable. 

It seems to me though that the intention of Shuttleworth was from the beginning that Ubuntu be a Linux OS that didn't require quite as much expended brain power just to keep it booting and usable. Snap packages it seems to me is an attempt to remove the needs of the end user to be saddled with continuous updates.  Printers just self install without downloading drivers or running scripts from the command prompt or tweaking config files. A user can have update kernels automatically updated with the user not even being aware that they exist. 

I am sympathetic with the OP so far as post #15 is concerned but if Mark Shuttleworth and his team continue on the current path I might just take a break from solving problems with Ubuntu and perhaps have a normal conversion with my wife for a change. 
PS. Sorry about your loss of freedom of choice there guy. Life is difficult.

---

### Post by jbicha on 2022-03-16
> **Claus7 said:**
> I noticed that (almost) any application available was a snap one. 

Regards!

The "Ubuntu Software" app now is itself a snap named snap-store and it only installs snaps.

You would need to use the command line to install an app that can install traditional packages. I suggest

```
sudo apt install gnome-software
```

but you could install synaptic instead if you prefer.

---

### Post by Claus7 on 2022-03-16
Hello,

> **jbicha said:**
> The "Ubuntu Software" app now is itself a snap named snap-store and it only installs snaps.

You would need to use the command line to install an app that can install traditional packages. I suggest

```
sudo apt install gnome-software
```

but you could install synaptic instead if you prefer.

this is what I guessed, thank you for the verification.

Regards!

---

### Post by yaminb on 2022-03-22
I'm a little unfamiliar with the details, but why was apt modified to be a front for some snap packages.

Conceptually in my mind, apt is for managing .deb. Snap and flatpak both have their own management tools. Mixing things up just generates confusion in my mind. 
Was this just done for users, or are there deeper dependency management issues where this is beneficial?

I should say, I have no issues with flatpak or snap. I personally try to have as many apps as flatpak/snap as possible. But in my head, if I really wanted something as a .deb, I'd use apt. if it's not available in .deb, just let me know. No need to automatically install the snap. It's too much confusion.

---

### Post by Frogs Hair on 2022-03-23
Ubuntu Budgie has added the Firefox ESR .deb to its welcome application along with a many other browser choices some snap and some not.

---

### Post by #&amp;thj^% on 2022-03-23
> **Frogs Hair said:**
> **_Ubuntu Budgie_** has added the Firefox ESR .deb to its welcome application along with a many other browser choices some snap and some not.

Alright you twisted my arm, now I have to take a peek, see what has Frogs Hair has been using.

---

### Post by ajgreeny on 2022-03-24
I have just found that even Xubuntu 22.04 is now offering the snap version only of firefox, with no alternative if you wish to not use snaps, other than downloading the .tar.gx direct from Mozilla and pointing your own firefox.desktop file to the executable in the extracted archive, or perhaps using a PPA which I have not yet investigated..

At the moment I have just downloaded the tar.gz and I'm running that in the same way that I do in Debian Unstable. It is self updating so there is no danger of dropping behind.

My only uncertainty is whether or not Mozilla will continue to offer the archive in this way; time will tell!

---

### Post by sgage on 2022-03-24
Same thing in Ubuntu MATE - deb package replaced by snap, and the deb package only installs the snap (and snapd if necessary). I, too, am now running the tar.gz from Mozilla. I do not want snap and all of its bloat and layers of stuff scattered all over the place.

---

### Post by #&amp;thj^% on 2022-03-24
I'm not sure about Frogs Hair but my Budgie still has the .deb
```
snap list
Name                   Version   Rev    Tracking         Publisher     Notes
core20                 20220304  1376   latest/stable    canonical&#10003;    base
snapd                  2.54.4    15177  latest/stable    canonical&#10003;    snapd
ubuntu-budgie-welcome  0.16.11   380    latest/stable/&#8230;  ubuntubudgie  classic
```
I Lied :(
```
Upgrade to the firefox snap                                               &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Starting in Ubuntu 22.04, all new releases of firefox are only available  &#9474; 
 &#9474; to Ubuntu users through the snap package.                                 &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; This package update will transition your system over to the snap by       &#9474; 
 &#9474; installing it.                                                            &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; It is recommended to close all open firefox windows before proceeding to  &#9474; 
 &#9474; the upgrade.                                                              &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                                  <Ok>                      
```

---

### Post by guiverc on 2022-03-24
> **Frogs Hair said:**
> Ubuntu Budgie has added the Firefox ESR .deb to its welcome application along with a many other browser choices some snap and some not.

I **really** like the idea of that.

---

### Post by vicshrike on 2022-03-25
The firefox-snap crashes now and then for me. Have you noticed anything similar? Has happened on 21.10 too.

---

### Post by guiverc on 2022-03-25
> **vicshrike said:**
> The firefox-snap crashes now and then for me. Have you noticed anything similar? Has happened on 21.10 too.

The only thing I've noticed is the `systemd-oomd` (out-of-memory) can force-quit apps under certain conditions, I've noticed this impacts *snaps* the most, for me that's *chromium*, *telegram* & now *firefox*.

Example of what to look for is  (in `journalctl` or the* systemd journal*)

```
Feb 15 17:10:20 d960-ubu2 systemd-oomd[949]: Killed /user.slice/user-1000.slice/user@1000.service/app.slice/snap.chromium.chromium.82bbbfd7-c79b-4b57-b425-e543631ca054.scope due to memory p>
```

or an example of `firefox`

```
Mar 24 16:04:39 d960-ubu2 systemd-oomd[854]: Killed /user.slice/user-1000.slice/user@1000.service/app.slice/snap.firefox.firefox.7ff805ad-0523-4c96-ae6e-d6e168e1e41b.scope due to memory pressure for /user.slice/user-1000.slice/user@1000.service being 50.53% > 50.00% for > 20s with reclaim activity
```


I'd suggest checking for entries like that in your logs.
[I]
A recent bug report was filed about this behavior - [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1966381](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1966381)[/I]

---

### Post by mIk3_08 on 2022-03-25
> **Frogs Hair said:**
> Ubuntu Budgie has added the Firefox ESR .deb to its welcome application along with a many other browser choices some snap and some not.
I don't have any idea of this Firefox ESR .deb. what thus this mean? I am very noob about this. regards and cheers.

---

### Post by Frogs Hair on 2022-03-25
> **mIk3_08 said:**
> I don't have any idea of this Firefox ESR .deb. what thus this mean? I am very noob about this. regards and cheers.

Firefox extended support release based on an older version of Firefox. There is currently a PPA which U-Budgie has has linked to is its welcome app and install with a click.    Midori and Gnome Web are also included.

You can add this ppa and remove the snap for any Ubuntu flavor.  

[https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa)

[https://www.mozilla.org/en-US/firefox/enterprise/](https://www.mozilla.org/en-US/firefox/enterprise/)

---

### Post by MyMurry on 2022-03-25
For the ppa firefox-next I got it running with this file:

/etc/apt/preferences.d/firefox-next

```
Package: *
Pin: release o=LP-PPA-mozillateam-firefox-next
Pin-Priority: 1002
```


snap remove firefox
sudo apt update && sudo apt upgrade

---

### Post by mIk3_08 on 2022-03-26
> **Frogs Hair said:**
> Firefox extended support release based on an older version of Firefox. There is currently a PPA which U-Budgie has has linked to is its welcome app and install with a click.    Midori and Gnome Web are also included.
You can add this ppa and remove the snap for any Ubuntu flavor.
[https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa)
[https://www.mozilla.org/en-US/firefox/enterprise/](https://www.mozilla.org/en-US/firefox/enterprise/)

Thanks for the info Frogs Hair. This is a brilliant idea. This is cool.  Regards and cheers

---

### Post by mohegan on 2022-03-31
For me, Firefox snap is bad. I prefer a deb version.
So, I use the Firefox ESR ppa :

[LIST]
[*]sudo add-apt-repository ppa:mozillateam/ppa
[*]sudo vim /etc/apt/preferences.d/firefox-next
[INDENT]Package: *
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1002
[/INDENT]
[*]sudo apt update
[*]sudo apt install firefox
[/LIST]

---

