---
title: "KDE 4.4 beta 2"
date: 2009-12-21
forum: The Cafe
---

### Post by isaacj87 on 2009-12-21
Woot! 

KDE SC 4.4 reaches its 2nd beta. You can read the release announcement here: [http://kde.org/announcements/announce-4.4-beta2.php]("http://kde.org/announcements/announce-4.4-beta2.php")

I've been running it for a day or so and it feels pretty good. Haven't had any crashes with plasma or anything. It basically feels like 4.3 with a little more pizazz and polish. Looking forward to the final! :)

---

### Post by RiceMonster on 2009-12-21
Excellent, it's getting closer. I'm really excited for this release. Looks like it's going to be great!

---

### Post by NoaHall on 2009-12-21
Brings a few nice features to KDE, for sure.

---

### Post by ikkefc3 on 2009-12-24
Plasma feels a lot smoother. Also: if you disable plugins in some QT webkit browser (e.g. Arora or Rekonq), scrolling goes a lot smoother without flash elements.
KDE 4.4 SC beta 2 is some less complet than on the Opensuse build service (e.g.  no virtuoso backend for nepomuk), but it's a lot better than KDE SC 4.3.4 I think.

---

### Post by Xbehave on 2009-12-24
Compositing is back :D

Does anybody else have these issues? and for bonus points fixes?
I have a problem with alt+f2 lag when compositing is enabled
I have no settings for individual desktop effects
Powerdevil does not show my list of profiles if the list extends below the bottom of the box (not a 4.4b2 issue)

Also there is a known bug (not sure where it started) that may confuse you, but is easy to work around:
if you right click an unlocked plasma panel and try add widget, nothing happens.

---

### Post by Shpongle on 2009-12-24
> **ricemonster said:**
> excellent, it's getting closer. I'm really excited for this release. Looks like it's going to be great!

+1

---

### Post by SuperSonic4 on 2009-12-24
It is working well under the hood too. There have been a few problems - mostly that Pulseaudio is needed to load KDM

---

### Post by Pasdar on 2009-12-24
Pulseaudio is not even used in Kubuntu right? At least I dont have it in my kubuntu install.

---

### Post by SuperSonic4 on 2009-12-24
> **Pasdar said:**
> Pulseaudio is not even used in Kubuntu right? At least I dont have it in my kubuntu install.

Correct, although this could be my install as I'm using an unofficial [arch] repo. I believe Pulse may be introduced

---

### Post by Xbehave on 2009-12-24
**_[SIZE="5"][kubuntu announcement]("http://www.kubuntu.org/news/kde-sc-4.4-beta-2")[/SIZE]_**

> **SuperSonic4 said:**
> It is working well under the hood too. There have been a few problems - mostly that Pulseaudio is needed to load KDM
Not here, but i don't have pa installed
```
ii  kdm                                       4:4.3.85-0ubuntu1~karmic1~ppa3            KDE Display Manager for X11
un  pulseaudio                                <none>                                    (no description available)

```
the update put it as default output but kdm still worked and kde just fell back.

---

### Post by RiceMonster on 2009-12-24
I don't even think there are any Qt/KDE Pulse Audio tools. Aren't they all developed for GNOME?

---

### Post by Giant Speck on 2009-12-24
I want to try the beta, but I don't want to screw it up like all the other times I've tried to install a KDE beta.   :(

---

### Post by Xbehave on 2009-12-24
I think there are the lucid liveCDs
If you are familiar with the CLI, you can install it using the ppa then use apt-pinning and aptitude to revert back to the previous version, however changing versions can mess up settings so either make a new user or backup ~/.kde ~/.local

so far i've only run into superficial problems nothing big at all (in 4.4b2, there were a couple of more serious bugs in 4.4b1) [my problems are described on page1 i'm not sure if anybody else has them]

---

### Post by AICollector on 2009-12-24
I was under the impression that KDE's Phonon was a replacement for Pulse?

Also, in this beta, can anyone check that programs like VLC and the restricted Flash plugin can acutally work? That's what drove me away from Kubuntu in the first place; that either KDE sounds would work, or VLC and Flash would emit sounds, not both :P

I would check myself, but I don't have the bandwidth the fiddle around with distros anymore :(

---

### Post by RiceMonster on 2009-12-24
> **AICollector said:**
> I was under the impression that KDE's Phonon was a replacement for Pulse?

Phonon is an API rather than a sound server.

---

### Post by hoppipolla on 2009-12-24
I still cant wait for 4.4 final release! ^_^

Im weighing up whether to install this but I wanna make sure I dont break my set up as I have it just the way I like it and I dont wanna risk the instability! I'll definitely have my eye on this one though as it should be epic! :)

---

### Post by Pasdar on 2009-12-24
You guys should try out 64bit kubuntu. Nothing has crashed on me, everything works, performance is up by a great deal too.

32bit was also stable, but I always had some crash issues just after installing for some reason.

---

### Post by sototallycarl on 2009-12-24
I have always had problems running KDE 4 on top of an Ubuntu Install, release or beta.

Does Kubuntu proper fix this?

I tried KDE 4.4b2 and Plasma crashed, Chromium didn't work at all and I would get rot so bad (after just an few hours) I would have to force restart my machine. Sadly this isn't much different from KDE 4.3 official releases.

I looks pretty, I really like the thinking behind everything that is KDE and every few months I install it and get disappointed since I can't actually use it day to day.

---

### Post by AICollector on 2009-12-24
I'll go back to KDE when it does three things;


1. Interact with mobile broadband dongles the same way Gnome's network manager does.

2. Have a fully functional release that has ALL sounds working by default.

3. Has a properly working Ubuntu One client.

4. Has the software centre.

---

### Post by hoppipolla on 2009-12-24
> **sototallycarl said:**
> I have always had problems running KDE 4 on top of an Ubuntu Install, release or beta.

Does Kubuntu proper fix this?

I tried KDE 4.4b2 and Plasma crashed, Chromium didn't work at all and I would get rot so bad (after just an few hours) I would have to force restart my machine. Sadly this isn't much different from KDE 4.3 official releases.

I looks pretty, I really like the thinking behind everything that is KDE and every few months I install it and get disappointed since I can't actually use it day to day.
This is kinda odd, do you have unusual hardware or something? And Plasma should fully recover after a crash, at least it does in 4.3.4 o.O

---

### Post by ctrlmd on 2009-12-24
#-onow i have to download KDE distro.

---

### Post by hoppipolla on 2009-12-24
> **AICollector said:**
> I'll go back to KDE when it does three things;


1. Interact with mobile broadband dongles the same way Gnome's network manager does.

2. Have a fully functional release that has ALL sounds working by default.

3. Has a properly working Ubuntu One client.

4. Has the software centre.
Just use the combo of apps and DE that you prefer. I love KDE but I also use Synaptic, Pidgin, Chrome, The GIMP, Filezilla... Gnome just gets a bit more attention from third party developers at the moment and thats totally cool so long as the apps run on KDE and look nice themed :)

---

### Post by Xbehave on 2009-12-24
> **AICollector said:**
> I'll go back to KDE when it does three things;


1. Interact with mobile broadband dongles the same way Gnome's network manager does.

2. Have a fully functional release that has ALL sounds working by default.

3. Has a properly working Ubuntu One client.

4. Has the software centre.
1) just use nm-applet, NM development is very gnome centric
2) I've never had any problems, so i doubt this is kde related
3) It does, just use the gnome ubuntu1 client
4) It does, just install software centre
5) Comments like that won't be missed tbh, especially as they have nothing to do with the thread 4.4b2

speaking of kde 4.4 betas does anybody else have trouble with the powerdevil?

---

### Post by SuperSonic4 on 2009-12-24
Also installing *phonon-backend-mplayer* solved my problem with sound although was probably just my machine

Can't comment on powerdevil as the laptop isn't on

---

### Post by Icehuck on 2009-12-24
> **Xbehave said:**
> 

speaking of kde 4.4 betas does anybody else have trouble with the powerdevil?

I'm not having any problems with it, but in the past it's always been Console-Kit not working.

---

### Post by Xbehave on 2009-12-24
> **SuperSonic4 said:**
> Also installing *phonon-backend-mplayer* solved my problem with sound although was probably just my machine

Can't comment on powerdevil as the laptop isn't on
no phonon-mplayer here in kubuntu land (unless somebody can ppa me up), but phonon-backend-xine seams to do the trick here though (well in 4.4b2 in 4.4b1 something was messed up for a while, but then fixed)

I've gone back to kpowersave for kde3 amazed it's still in repos, as it's allows more direct control.

> I'm not having any problems with it, but in the past it's always been Console-Kit not working.
I think it was just the battery monitor widget that was playing up, not the actual power management after switching everything seams fine.

---

### Post by SuperSonic4 on 2009-12-24
> **Xbehave said:**
> no phonon-mplayer here in kubuntu land (unless somebody can ppa me up), but phonon-backend-xine seams to do the trick here though (well in 4.4b2 in 4.4b1 something was messed up for a while, but then fixed)

I've gone back to kpowersave for kde3 amazed it's still in repos, as it's allows more direct control.


I think it was just the battery monitor widget that was playing up, not the actual power management after switching everything seams fine.

Yeah, it's good thing, it's in the AUR on arch and my problem probably came from the repo. Kubuntu did well not installing it. If you want the mplayer backend you may have to compile it from svn although I'd leave it if Phonon works perfectly in kubuntu

---

### Post by Giant Speck on 2009-12-24
I tried to install 4.4b2 using the instructions on the Kubuntu webpage; however, I'm kind of stuck due to a problem with kde-window-manager.

I added the kubuntu-ppa repository and ran a [FONT=Courier New]sudo apt-get upgrade[/FONT] and [FONT=Courier New]sudo apt-get dist-upgrade[/FONT].  Everything was fine until it tried to install kde-window-manager

```
The following packages have unmet dependencies:             
  kdebase-workspace: Depends: kde-window-manager (>= 4:4.3.85-0ubuntu1~karmic1~ppa3) but 4:4.3.2-0ubuntu7.1 is installed                                            
E: Unmet dependencies. Try using -f.  
```

When I run [FONT=Courier New]sudo apt-get -f install[/FONT], I get the following:

```
jesse@jesse:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev libaudio-dev kdebase-runtime-data-common
  x11proto-xinerama-dev comerr-dev x11proto-render-dev libxmu-headers
  libxrender-dev libkadm5srv6 libkrb5-dev libglu1-xorg-dev libsqlite0-dev
  libgssrpc4 libfontconfig1-dev libqt4-phonon-dev libxcursor-dev
  kdebase-runtime-bin-kde4 x11proto-randr-dev libssl-dev libxt-dev libxmu-dev
  libjpeg62-dev xlibmesa-gl-dev liblcms1-dev libpq-dev libxrandr-dev
  libexpat1-dev libxft-dev libkdb5-4 libmng-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kde-window-manager
The following packages will be upgraded:
  kde-window-manager
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
155 not fully installed or removed.
Need to get 0B/1,725kB of archives.
After this operation, 987kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  kde-window-manager
Install these packages without verification [y/N]? y
(Reading database ... 283157 files and directories currently installed.)
Preparing to replace kde-window-manager 4:4.3.2-0ubuntu7.1 (using .../kde-window-manager_4%3a4.3.85-0ubuntu1~karmic1~ppa3_i386.deb) ...
Unpacking replacement kde-window-manager ...
dpkg: error processing /var/cache/apt/archives/kde-window-manager_4%3a4.3.85-0ubuntu1~karmic1~ppa3_i386.deb (--unpack):
 trying to overwrite '/usr/share/kde4/config/aurorae.knsrc', which is also in package kwin-style-aurorae 0:0.2.1-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/kde-window-manager_4%3a4.3.85-0ubuntu1~karmic1~ppa3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

:?

---

### Post by Giant Speck on 2009-12-24
Nevermind, I fixed it!

I had to uninstall kwin-style-aurorae.

---

### Post by samjh on 2009-12-25
> **SuperSonic4 said:**
> It is working well under the hood too. There have been a few problems - mostly that Pulseaudio is needed to load KDMThat should not be the case.  KDM in its vanilla form is not, and never has been, dependent on PulseAudio.

> **AICollector said:**
> I was under the impression that KDE's Phonon was a replacement for Pulse?Phonon is a multimedia API to enable cross-platform playback of multimedia content.  PulseAudio is an audio server which works at a much lower level.

The stack basically looks like this:
```
|------------------------------------------------------------|
|               Application: eg. MPlayer, VLC                |
|------------------------------------------------------------|
|               Multimedia Framework: eg. Phonon             |
|     Lower-level Framework: GStreamer, Xine-lib, libVLC     |
|------------------------------------------------------------|
|         Sound server: eg. PulseAudio, arTs, ESD            |
|------------------------------------------------------------|
|                   Backend: eg. ALSA, OSS                   |
|------------------------------------------------------------|
|        Hardware driver: provided by ALSA, OSS, etc.        |
|------------------------------------------------------------|
|                          Device                            |
|------------------------------------------------------------|
```That is a very simplified version of the Linux sound stack, and some of those layers overlap depending on the specific implementation.  For example, Phonon performs limited functions as a sound server, but is heavily dependent on libraries like GStreamer and Xine for actual playback and recording.

> **AICollector said:**
> Also, in this beta, can anyone check that programs like VLC and the restricted Flash plugin can acutally work? That's what drove me away from Kubuntu in the first place; that either KDE sounds would work, or VLC and Flash would emit sounds, not both :PThat sounds like an issue particular to you or your setup.  I (frankly, most users) have not had problems using Adobe's Flash player or VLC on recent KDE versions (eg. 4.2 and later).

> **RiceMonster said:**
> I don't even think there are any Qt/KDE Pulse Audio tools. Aren't they all developed for GNOME?Phonon's PulseAudio support has been implemented for KDE 4.4, courtesy of Colin Guthrie.

---

### Post by Xbehave on 2009-12-25
> **Giant Speck said:**
> Nevermind, I fixed it!

I had to uninstall kwin-style-aurorae.
Try using aptitude for updates, it will fix stuff like this.

---

### Post by hoppipolla on 2009-12-26
> **Xbehave said:**
> Try using aptitude for updates, it will fix stuff like this.
or Synaptic? Thats pretty much all I ever use apart from terminal commands and scripts :)

---

### Post by t.rei on 2010-01-05
> **Giant Speck said:**
> Nevermind, I fixed it!

I had to uninstall kwin-style-aurorae.

Thanks for the info - solved it for me, too:

error was with:
```
/var/cache/apt/archives/kde-window-manager_4%3a4.3.85-0ubuntu1~karmic1~ppa3_i386.deb
```

resolved by:
```

sudo dpkg -r kwin-style-aurorae
sudo apt-get -f install

```

---

