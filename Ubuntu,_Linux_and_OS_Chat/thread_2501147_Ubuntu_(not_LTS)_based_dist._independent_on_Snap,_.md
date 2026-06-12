---
title: "Ubuntu (not LTS) based dist. independent on Snap, FlatPak &amp; AppImage?"
date: 2024-09-24
forum: Ubuntu, Linux and OS Chat
---

### Post by ruwolf on 2024-09-24
Hello.

I love Debian & Ubuntu for their huge repositories, package dependency system, package managers like Aptitude or Synaptic, alien converter, documentation and support.

I hate Snap, FlatPak and similar uneaten disk space eaters.

Please, is there Ubuntu (non-LTS) based distribution independent on Snap, FlatPak & AppImage?

I need all packages, at least one web-browser supporting WebDriver for Selenium from standard archive format (e.g. .deb).

Mint was like that, but they switched to LTS.

Debian is Great, but not very often updated.

Have Manjaro similarly big repository like Xubuntu?

---

### Post by grahammechanical on 2024-09-24
> Please, is there Ubuntu (non-LTS) based distribution independent on Snap, FlatPak & AppImage?


May be. I do not think that Flatpak or Applimage apps will run on Ubuntu without special extra software being installed. Ubuntu itself has special software called snapd that will make it possible to run snap packaged apps. If we do not install any snap apps we will not get that extra software that you dislike so.

Ubuntu now comes with certain applications that are snap packages by default. Such as Firefox; Thunderbird; snap store/app store/software centre.

There may be a Linux distribution that has nothing has to do with Canonical's snap software but it may have Flatpak software by default. 

Regards






There may be distributions based upon Ubuntu that do not have the Ubuntu software that

---

### Post by guiverc on 2024-09-24
> **ruwolf said:**
> Hello.

I love Debian & Ubuntu for their huge repositories, package dependency system, package managers like Aptitude or Synaptic, alien converter, documentation and support.

I hate Snap, FlatPak and similar uneaten disk space eaters.

Please, is there Ubuntu (non-LTS) based distribution independent on Snap, FlatPak & AppImage?

Doesn't Debian meet those requirements by default?  Alas it has no non-LTS; but if that was required I'd likely just use *testing* (currently that'll be *trixie* or what will be 13).

There can be *slight* differences in an installed Debian system depending on which installer you opt to use (*two choices are offered, selected at download time just as Ubuntu offers*), but to me both would provide what you're after.

Ubuntu too has ISOs that will install a *snapd free* system; though with Ubuntu the *snap* infrastructure is not disabled (*just not installed*), but multiple Ubuntu *developers* & *members* have blogged how to make this permanent (*their blogs being picked up by Planet Ubuntu feeds; a number of which got mentioned in UWN why is maybe how I became aware of them*). So you could install a Ubuntu system without *snapd*, then quite easily prevent its install as has been documented; though personally I think I'd just install the system anyway, and remove *snapd* & do what the bloggers wrote about anyway.

Flatpak & Appimage isn't *enabled* by default in either Ubuntu or Debian; Debian doesn't enable *snapd* either by default.

I don't see why you need to go elsewhere (*ie. do you need a based-on system*). My 2c.

---

### Post by ian-weisser on 2024-09-24
Looks like you have already done the research.

There is no unknown distro that also free and has a huge amount of packaged software. You saw the choices.

Time to revisit your requirements and prioritize your wish list.

---

### Post by Rubi1200 on 2024-09-24
Unless you are absolutely adamant on sticking with Ubuntu or Debian, I suggest taking a look at Arch or Arch-based distros.

You mention Manjaro, but my personal recommendation would be EndeavourOS.

There are large repositories, including the packages you mention, and installing means learning a few basic pacman commands to get up and running.

---

### Post by ruwolf on 2024-09-27
Thank you all for your answers.

I will try Pop_OS, they use Ubuntu as base, now they quite late for upgrading, but allegedly only due their Cosmic DE development. (It is quite small company.)

---

### Post by ne29914 on 2024-09-27
Just install (x)ubuntu and kill/uninstall snapd immediately. Then you're fine. AFAIK, neither Flatpak nor Appimage are there by default. I haven't seen them.

---

### Post by ruwolf on 2024-09-28
But Xubuntu without snapd has not any web-browser supporting WebDriver for Selenium; or has some?

I have tried Pop_OS and temporarily changed my mind. Now I will try SparkyLinux..

---

### Post by volteos on 2024-10-18
You don't need to use snaps on Ubuntu. When you install apps via apt, they're not snap packs.

Also if you want stability I'd recommend staying on LTS and not hopping off of it. Also Debian sucks, both as a community and an OS for general use. I'm betting they still use their crappy outdated installer.

---

### Post by VMC on 2024-10-19
My snap-less, flat-less Ubuntu size is 4.2GB. The Arch install is far greater. I couldn't get Arch under 5GB if I cut off its arms & legs.
I will most likely always use Ubuntu. As of right now, Snap is just an vestigial organ, like Appendix.

---

### Post by 1fallen on 2024-10-19
> **VMC said:**
>  I couldn't get Arch under 5GB if I cut off its arms & legs.

:lolflag:

But My server is under 5 gigs
Desktop is a different story though
```
[FONT=monospace][COLOR=#000000] df / [/COLOR]
Filesystem              Type  Size  Used Avail Use% Mounted on 
zpcachyos/ROOT/cos/root zfs   408G   13G  396G   3% /


[/FONT]
```

---

### Post by TheFu on 2024-10-20
> **volteos said:**
> You don't need to use snaps on Ubuntu. When you install apps via apt, they're not snap packs.

This is easily proven to be false.   Remove Firefox.  Install it again using **sudo apt install firefox** The snap will be installed.
Same for lxd and chromium and vlc.  There may be "some" packages that don't have a "snap-transitional .deb package, but the major ones all do to "help" people. 

For a clear example, 
```
$ dpkg -l lxd
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-========================================
ii  lxd            1:0.10       all          Transitional package - lxd -> **snap (lxd)**
```
and
```
$ snap list
Name    Version         Rev    Tracking       Publisher   Notes
bare    1.0             5      latest/stable  canonical&#10003;  base
core18  20240920        2846   latest/stable  canonical&#10003;  base
core20  20240705        2379   latest/stable  canonical&#10003;  base
core22  20240904        1621   latest/stable  canonical&#10003;  base
**lxd     5.21.2-2f4ba6b  30131  5.21/stable    canonical&#10003;  -**
scrcpy  v1.25           399    latest/stable  sisco311    -
snapd   2.63            21759  latest/stable  canonical&#10003;  snapd
```

I'd prefer to have a non-snap version of lxd.  Please.  Exactly how can I have that, easily, on Ubuntu?  The answer is, it isn't possible.  

I'd love to know, if things have actually changed.

Oh, and AppImages do not require any extra software installed to work normally.  Just grab the program-version.AppImage, chmod +x that file and run it.  No sandbox or container, but no hassles either.

---

### Post by VMC on 2024-10-21
> **TheFu said:**
> This is easily proven to be false.   Remove Firefox.  Install it again using **sudo apt install firefox** The snap will be installed.
Same for lxd and chromium and vlc.  There may be "some" packages that don't have a "snap-transitional .deb package, but the major ones all do to "help" people. 

For a clear example, 
```
$ dpkg -l lxd
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-========================================
ii  lxd            1:0.10       all          Transitional package - lxd -> **snap (lxd)**
```
and
```
$ snap list
Name    Version         Rev    Tracking       Publisher   Notes
bare    1.0             5      latest/stable  canonical&#10003;  base
core18  20240920        2846   latest/stable  canonical&#10003;  base
core20  20240705        2379   latest/stable  canonical&#10003;  base
core22  20240904        1621   latest/stable  canonical&#10003;  base
**lxd     5.21.2-2f4ba6b  30131  5.21/stable    canonical&#10003;  -**
scrcpy  v1.25           399    latest/stable  sisco311    -
snapd   2.63            21759  latest/stable  canonical&#10003;  snapd
```

I'd prefer to have a non-snap version of lxd.  Please.  Exactly how can I have that, easily, on Ubuntu?  The answer is, it isn't possible.  

I'd love to know, if things have actually changed.

Oh, and AppImages do not require any extra software installed to work normally.  Just grab the program-version.AppImage, chmod +x that file and run it.  No sandbox or container, but no hassles either.

```
$ dpkg -l lxd
dpkg-query: no packages found matching lxd
```
```
$ snap list
Command 'snap' not found, but can be installed with:
sudo apt install snapd
```

---

### Post by TheFu on 2024-10-21
> **VMC said:**
> ```
$ dpkg -l lxd
dpkg-query: no packages found matching lxd
```
```
$ snap list
Command 'snap' not found, but can be installed with:
sudo apt install snapd
```

Now, run 
```
sudo apt install lxd
```
and run those 2 commands again.  You'll see a snap package was installed even though you used "apt", not "snap install".  THAT's my main issue with snaps.  They are being sneaky and there's no way to prevent "transitional packages from pulling in snap infra even after it has clearly be manually removed by the admin on the system.

Anyway, I gave up fighting the battle. Mint doesn't do this and it is enough like Ubuntu in other ways for my desktop needs.

---

### Post by 1fallen on 2024-10-21
I finally have it at bay currently with:
```
cat <<EOF | sudo tee /etc/apt/preferences.d/nosnap.pref Package: snapd Pin: release a=* Pin-Priority: -10 EOF
```

You can use apt hold, but I find it still trys to sneak in . Banish from the OS is better. :P
```
sudo cat /etc/apt/preferences.d/nosnap.pref
Package: snapd
Pin: release a=*
Pin-Priority: -10

```
```
 sudo apt install lxd
Package lxd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Error: Package 'lxd' has no installation candidate

```
```
sudo apt install snapd
Package snapd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Error: Package 'snapd' has no installation candidate

```
There Much Better Now......

---

### Post by Norm24 on 2024-10-21
> This is easily proven to be false. Remove Firefox. Install it again using sudo apt install firefox The snap will be installed.

This is not entirely accurate.After removing all Snap packages that I did want to use I either downloaded the .deb packages from source or used a trusted PPA.Perfect example of this is Firefox,I simply removed the Snap version of FF downloaded the Ubuntuzilla PPA+signing key then sudo apt install firefox-mozilla-build and no snap installed and I will always get the latest Mozilla build of FF.This applies to TB and SeaMonkey as well,same for LibreOffice,Edge and a myriad of other packages.With many other packages I simply downloaded the .deb from source and installed with Gdebi and no snap installed.

As an end user who's been with Ubuntu essentially from the beginning I don't like to muck around to deeply and screw things up,I'm not one to just start entering lines of code in terminal to change things that might screw up a basic install.I've had issues with snaps since they were introduced and have been doing exactly what I posted in the above paragraph since snaps first came on the scene.The only snaps installed on my pc are the core components that were installed when I installed Ubuntu(Mate) and like I said I'm not going to screw around in terminal to change that and risk breaking my current install.

---

### Post by 1fallen on 2024-10-21
> **Norm24 said:**
> .The only snaps installed on my pc are the core components that were installed when I installed Ubuntu(Mate) and like I said I'm not going to screw around in terminal to change that and risk breaking my current install.

And "No One" will force you to, Relax!
I have been around since the year 2005, and I wouldn't do or write anything with intent to break anyone's system.

Just sharing my prefs, no more no less. Your free to do as you  please. and I won't bitch about it.

---

### Post by grahammechanical on 2024-10-21
> They are being sneaky and there's no way to prevent "transitional  packages from pulling in snap infra even after it has clearly be  manually removed by the admin on the system

We are the Borg. Resistance is futile. You will be assimilated into the hive mind. :) If that does not work, watch out for the Daleks. Exterminate! Exterminate! :)

Regards

---

### Post by VMC on 2024-10-22
> **1fallen2 said:**
> I finally have it at bay currently with:
```
cat <<EOF | sudo tee /etc/apt/preferences.d/nosnap.pref Package: snapd Pin: release a=* Pin-Priority: -10 EOF
```

You can use apt hold, but I find it still trys to sneak in . Banish from the OS is better. :P
```
sudo cat /etc/apt/preferences.d/nosnap.pref
Package: snapd
Pin: release a=*
Pin-Priority: -10

```
```
 sudo apt install lxd
Package lxd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Error: Package 'lxd' has no installation candidate

```
```
sudo apt install snapd
Package snapd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Error: Package 'snapd' has no installation candidate

```
There Much Better Now......

Yes, indeed! That 'nosnap.pref' is the way to go.

---

### Post by VMC on 2024-10-22
Removing snaps the proper way will not 'screw things up', as you say. My Firefox is installed from apt.

---

### Post by Norm24 on 2024-10-28
> **1fallen2 said:**
> And "No One" will force you to, Relax!
I have been around since the year 2005, and I wouldn't do or write anything with intent to break anyone's system.

Just sharing my prefs, no more no less. Your free to do as you  please. and I won't bitch about it.


The below quote wasn't even yours and I responded to it in a very rational calm way.No relaxation needed on my part.

> This is easily proven to be false. Remove Firefox. Install it again using sudo apt install firefox The snap will be installed.

---

### Post by 1fallen on 2024-10-28
> **Norm24 said:**
> The below quote wasn't even yours and I responded to it in a very rational calm way.No relaxation needed on my part.

This is what I replied back to also in a clam tone, just for accuracy.
> **Norm24 said:**
> .The only snaps installed on my pc are the core  components that were installed when I installed Ubuntu(Mate) and like I  said I'm not going to screw around in terminal to change that and risk  breaking my current install.
Happy to hear no relaxation needed. ;)

---

### Post by TheFu on 2024-10-29
> **Norm24 said:**
> This is not entirely accurate.After removing all Snap packages that I did want to use I either downloaded the .deb packages from source or used a trusted PPA.Perfect example of this is Firefox,I simply removed the Snap version of FF downloaded the Ubuntuzilla PPA+signing key then sudo apt install firefox-mozilla-build and no snap installed and I will always get the latest Mozilla build of FF.This applies to TB and SeaMonkey as well,same for LibreOffice,Edge and a myriad of other packages.With many other packages I simply downloaded the .deb from source and installed with Gdebi and no snap installed.

As an end user who's been with Ubuntu essentially from the beginning I don't like to muck around to deeply and screw things up,I'm not one to just start entering lines of code in terminal to change things that might screw up a basic install.I've had issues with snaps since they were introduced and have been doing exactly what I posted in the above paragraph since snaps first came on the scene.The only snaps installed on my pc are the core components that were installed when I installed Ubuntu(Mate) and like I said I'm not going to screw around in terminal to change that and risk breaking my current install.

Yes, there are workarounds.  But there are workarounds for most things.  If you remove the firefox snap, remove snapd, then runs **sudo apt install firefox**, it will come back as a snap.  THAT's the point.
Nobody is going to remember to install firefox-mozilla-build or some other odd package name.  And should we really suggest that anyone use a PPA like Ubuntuzilla?  That's a judgement call. Before I gave up on Ubuntu desktops, I was installing the official Mozilla PPA and loading firefox-esr ... to me, that was too much hassle. We shouldn't have to fight with our distros over dumb things like snaps.

We show CLI commands here because they are complete and fast. There are GUI methods, if you prefer. We just don't want to have to post 10 screen captures, edit those 10 images to point out things, then write a paragraph for each when 2 CLI commands just does the right thing. It is about efficiency.

---

### Post by VMC on 2024-10-29
you dont need ppa, just go to  firefox and get firefox browser:
[https://www.google.com/search?q=firefox&client=firefox-b-1-d&sca_esv=746687e9b17ac835&ei=vAYhZ4yZBsuhkPIP56adoQ4&ved=0ahUKEwiM546I-7OJAxXLEEQIHWdTJ-QQ4dUDCA8&uact=5&oq=firefox&gs_lp=Egxnd3Mtd2l6LXNlcnAiB2ZpcmVmb3gyChAAGIAEGEMYigUyDRAAGIAEGLEDGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyEBAAGIAEGLEDGEMYgwEYigUyCBAAGIAEGLEDMgoQABiABBhDGIoFMggQABiABBixAzIKEAAYgAQYQxiKBUjfGVC5B1iXGHACeAGQAQCYAWWgAeUDqgEDNi4xuAEDyAEA-AEBmAIJoAKXBMICChAAGLADGNYEGEfCAg0QABiABBiwAxhDGIoFwgIOEAAYsAMY5AIY1gTYAQHCAhMQLhiABBiwAxhDGMgDGIoF2AEBwgIWEC4YgAQYsQMY0QMYQxiDARjHARiKBcICCxAuGIAEGLEDGIMBwgILEC4YgAQYsQMY1AKYAwDiAwUSATEgQIgGAZAGELoGBggBEAEYCZIHAzguMaAHmDE&sclient=gws-wiz-serp](https://www.google.com/search?q=firefox&client=firefox-b-1-d&sca_esv=746687e9b17ac835&ei=vAYhZ4yZBsuhkPIP56adoQ4&ved=0ahUKEwiM546I-7OJAxXLEEQIHWdTJ-QQ4dUDCA8&uact=5&oq=firefox&gs_lp=Egxnd3Mtd2l6LXNlcnAiB2ZpcmVmb3gyChAAGIAEGEMYigUyDRAAGIAEGLEDGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyChAAGIAEGEMYigUyEBAAGIAEGLEDGEMYgwEYigUyCBAAGIAEGLEDMgoQABiABBhDGIoFMggQABiABBixAzIKEAAYgAQYQxiKBUjfGVC5B1iXGHACeAGQAQCYAWWgAeUDqgEDNi4xuAEDyAEA-AEBmAIJoAKXBMICChAAGLADGNYEGEfCAg0QABiABBiwAxhDGIoFwgIOEAAYsAMY5AIY1gTYAQHCAhMQLhiABBiwAxhDGMgDGIoF2AEBwgIWEC4YgAQYsQMY0QMYQxiDARjHARiKBcICCxAuGIAEGLEDGIMBwgILEC4YgAQYsQMY1AKYAwDiAwUSATEgQIgGAZAGELoGBggBEAEYCZIHAzguMaAHmDE&sclient=gws-wiz-serp)

---

### Post by Norm24 on 2024-10-29
> **TheFu said:**
> Yes, there are workarounds.  But there are workarounds for most things.  If you remove the firefox snap, remove snapd, then runs **sudo apt install firefox**, it will come back as a snap.  THAT's the point.
Nobody is going to remember to install firefox-mozilla-build or some other odd package name.  And should we really suggest that anyone use a PPA like Ubuntuzilla?  That's a judgement call. Before I gave up on Ubuntu desktops, I was installing the official Mozilla PPA and loading firefox-esr ... to me, that was too much hassle. We shouldn't have to fight with our distros over dumb things like snaps.

We show CLI commands here because they are complete and fast. There are GUI methods, if you prefer. We just don't want to have to post 10 screen captures, edit those 10 images to point out things, then write a paragraph for each when 2 CLI commands just does the right thing. It is about efficiency.

As far as the Ubuntuzilla PPA goes why not suggest using it?How could doing a one time install of a package called firefox-mozilla-build be odd and hard to remember?Firefox-mozilla-build is exactly what it implies...it's the Mozilla build of their browser Firefox,Nanotube's been maintaining that PPA for more years than 90% of the posters here have been members including yourself.Once the PPA is installed and you install FF you never have to worry about it again,when a new version is ready either update via CLI or GUI.

If you find all this to be a hassle and consider it fighting with your distro well THAT's on you.Not everybody's like you,some of us are just straight up end users.For someone who doesn't like snaps or Ubuntu desktops you sure spend a lot of your time telling people how to use it and why you dislike it in the same response,kinda like being a car salesman and telling the buyer it's garbage after the sale.

Have a good day.

---

