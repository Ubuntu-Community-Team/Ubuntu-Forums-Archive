---
title: "Ubuntu 18.04 Unity: Unity7Maintainers PPA or Universe ?"
date: 2018-04-06
forum: Ubuntu Development Version
---

### Post by bbogert24 on 2018-04-06
So far in 18.04 I have not been able to get compiz working with Unity (works for flashback though).

After seeing the previous "18.04 Compiz not working" post I grabbed the Unity iso from a referenced
link and installed it and compiz works fine.

Since I was originally using Unity from Universe I am wondering if needed updates to get it working
are waiting on approval/submission into Universe or if I need to keep running the PPA  ?

In other words should I build off of the PPA or use the Universe repository and wait for the updates ?

Thanks,

---

### Post by dino99 on 2018-04-06
'universe' is maintained by the community, not ubuntu itself as it has made the choice to stop unity and chosen gnome as the default.
If you are an unity activist, then you will be 'alone' with other activists, to deal with all the problems :(

---

### Post by kc1di on 2018-04-06
The quickest way will most likely be the PPA - as unity is no longer an Ubuntu developed Desktop.

---

### Post by mc4man on 2018-04-06
Here I use the Ubuntu image, then install unity, compiz & it works just fine. So not sure what " I have not been able to get compiz working with Unity" is supposed to mean.
No real need for that ppa, if you want all related packages then also install the ubuntu-unity-desktop package.
Otherwise you can pick & choose useful additions to just installing unity package.

---

### Post by monkeybrain20122 on 2018-04-06
> **mc4man said:**
>  if you want all related packages then also install the ubuntu-unity-desktop package.
.

I have a pending update for ubuntu-unity-desktop, it is trying to install a whole bunch of things that don't seem to be related to unity-desktop such as ffmpeg, mpv, libmpv, gnome-mpv, youtube-dl and a bunch of other stuffs. I find it a bit odd.

---

### Post by mc4man on 2018-04-06
> **monkeybrain20122 said:**
> I have a pending update for ubuntu-unity-desktop, it is trying to install a whole bunch of things that don't seem to be related to unity-desktop such as ffmpeg, mpv, libmpv, gnome-mpv, youtube-dl and a bunch of other stuffs. I find it a bit odd.

I don't use that package myself as I prefer to add manually & as I'm using nemo don't want nautilus, ect. (nor all those useless fonts, update stuff, libreoffice, ect...
But this is what it would do here - 
> $ sudo apt install ubuntu-unity-desktop
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  apturl apturl-common deja-dup fonts-indic fonts-liberation2 fonts-mlym fonts-smc fonts-smc-manjari fonts-thai-tlwg
  fonts-tlwg-garuda fonts-tlwg-garuda-ttf fonts-tlwg-kinnari fonts-tlwg-kinnari-ttf fonts-tlwg-laksaman
  fonts-tlwg-laksaman-ttf fonts-tlwg-loma fonts-tlwg-loma-ttf fonts-tlwg-mono fonts-tlwg-mono-ttf fonts-tlwg-norasi
  fonts-tlwg-norasi-ttf fonts-tlwg-purisa fonts-tlwg-purisa-ttf fonts-tlwg-sawasdee fonts-tlwg-sawasdee-ttf
  fonts-tlwg-typewriter fonts-tlwg-typewriter-ttf fonts-tlwg-typist fonts-tlwg-typist-ttf fonts-tlwg-typo fonts-tlwg-typo-ttf
  fonts-tlwg-umpush fonts-tlwg-umpush-ttf fonts-tlwg-waree fonts-tlwg-waree-ttf gir1.2-appindicator3-0.1 gnome-mahjongg
  gnome-mines gnome-orca gnome-screensaver gnome-software gnome-software-common gnome-software-plugin-snap gnome-sudoku
  libboost-locale1.65.1 libepubgen-0.1-1 libgnome-games-support-1-3 libgnome-games-support-common liblouis-data liblouis14
  liborcus-0.13-0 libreoffice-avmedia-backend-gstreamer libreoffice-base-core libreoffice-calc libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk3 libreoffice-impress libreoffice-math
  libreoffice-ogltrans libreoffice-pdfimport libreoffice-style-breeze libreoffice-style-galaxy libreoffice-style-tango
  libreoffice-writer nautilus nautilus-share onboard onboard-common onboard-data orca python3-distupgrade python3-louis
  python3-uno python3-update-manager remmina remmina-common remmina-plugin-rdp remmina-plugin-secret remmina-plugin-vnc snapd
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-software uno-libs3 update-manager update-manager-core
  update-notifier update-notifier-common ure vino

As far as what you mentioned - the repo mpv installs a whole bunch of stuff including everything you mentioned plus additional worthless packages. 
So that's where that is coming from..

---

### Post by bbogert24 on 2018-04-06
Folks,

What I mean't by compiz is not working is that CCSM (compizconfig-settings-manager) and compiz-plugins-extra have
no effect on the desktop when changed.

The reason I can't use the default Ubuntu and just add Unity is that the snaps for gnome 3.26 and a few gnome apps take
up close to 700Mb of disk space I need for apps (stupid 4Gb limit, ISO9660 level3 is supposed to support 8Tb).

Since posting I have been spending my time trying to get Unity working on a mini install and after the last reply I was
finally able to compiz-plugins-extra and CCSM to work on the mini (e.g. ubuntu-unity-desktop).

So it looks like the ubuntu-unity-desktop fixed the problem for the mini at least. My beta1 build seems to be
a lost cause so I am going to rebuild from a clean mini install and use the ubuntu-unity-desktop instead of the
unity-session that I used previously and see what happens.

At least I am learning how to build using the mini.iso

Thanks for all of your help

---

### Post by monkeybrain20122 on 2018-04-06
> **bbogert24 said:**
> Folks,

What I mean't by compiz is not working is that CCSM (compizconfig-settings-manager) and compiz-plugins-extra have
no effect on the desktop when changed.

The reason I can't use the default Ubuntu and just add Unity is that the snaps for gnome 3.26 and a few gnome apps take
up close to 700Mb of disk space I need for apps (stupid 4Gb limit, ISO9660 level3 is supposed to support 8Tb).

Since posting I have been spending my time trying to get Unity working on a mini install and after the last reply I was
finally able to compiz-plugins-extra and CCSM to work on the mini (e.g. ubuntu-unity-desktop).

So it looks like the ubuntu-unity-desktop fixed the problem for the mini at least. My beta1 build seems to be
a lost cause so I am going to rebuild from a clean mini install and use the ubuntu-unity-desktop instead of the
unity-session that I used previously and see what happens.

At least I am learning how to build using the mini.iso

Thanks for all of your help

Did you try the unity-respin iso? [https://community.ubuntu.com/t/new-ubuntu-unity-iso/2146](https://community.ubuntu.com/t/new-ubuntu-unity-iso/2146) 
Works well here.

---

### Post by bbogert24 on 2018-04-07
First thank you for the unity-respin it's what caused the original question PPA or Universe in the first place.

The unity-respin worked properly with CCSM and compiz-plugins-extra but in my beta1 respin it wouldn't
do a thing (e.g. no effect on the desktop at all).

I saw that the unity-respin was pulling from PPA and I was pulling from Universe so I wondered if there
might me outstanding updates or if there was a greater problem with Universe.

It turns out that I was using the wrong meta package for Unity (I was using unity-session) and should
have been using ubuntu-unity-desktop.

I spent most of yesterday installing from mini and trying to get CCSM etc working. 

The key was the addition of ubuntu-unity-desktop tip.

After that I did a clean mini install and added xorg, xserver-xorg and alsa first
then installed ubuntu-unity-desktop and xserver-xorg-input-synaptics and
lastly lightdm.

Everything works as expected now and I learned how to build from mini.:D

Thanks again for your help and your hard work

---

### Post by mc4man on 2018-04-07
Just tried one, seemed straightforward. After install just ran this, blue is for touchpad machines only
```
sudo apt install unity compiz-plugins compizconfig-settings-manager lightdm notify-osd [COLOR="#0000CD"]xserver-xorg-input-synaptics[/COLOR]
```
Then rebooted, all was fine.
To do some initial garbage collection afterwards- 
```
sudo apt purge gdm3 gnome-shell
```

---

### Post by mc4man on 2018-04-07
> **monkeybrain20122 said:**
> I have a pending update for ubuntu-unity-desktop, it is trying to install a whole bunch of things that don't seem to be related to unity-desktop such as ffmpeg, mpv, libmpv, gnome-mpv, youtube-dl and a bunch of other stuffs. I find it a bit odd.

Looking closer I see that metapackage does recommend gnome-mpv. So that's what caused what you saw. 
gnome-mpv recommends youtube-dl, youtube-dl recommends ffmpeg & phantomjs, phantomjs recommends a bunch of others, ect.
Not sure of the thinking here... I've had a longstanding bug on the inadvisability  of recommending youtube-dl for the repo mpv/libmpv but that's gone nowhere..

It also recommends ffmpegthumbnailer, not sure about that either, not that it can't work but (at least in past) nautilus was coded to use the totem thumbnailer only.

---

### Post by monkeybrain20122 on 2018-04-07
> **mc4man said:**
> Looking closer I see that metapackage does recommend gnome-mpv. So that's what caused what you saw. 
gnome-mpv recommends youtube-dl, youtube-dl recommends ffmpeg & phantomjs, phantomjs recommends a bunch of others, ect.
Not sure of the thinking here... I've had a longstanding bug on the inadvisability  of recommending youtube-dl for the repo mpv/libmpv but that's gone nowhere..

It also recommends ffmpegthumbnailer, not sure about that either, not that it can't work but (at least in past) nautilus was coded to use the totem thumbnailer only.

 I see. ubuntu-unity-desktop is pre-installed (I use the iso) and removing it would autoremove many things which if autoremoved would break the system, however, upgrading it and then removing other recommended junks was ok.

yeah agreed no point installing youtube-dl from repo since it quickly gets outdated and useless, pip is easy anyway.

---

