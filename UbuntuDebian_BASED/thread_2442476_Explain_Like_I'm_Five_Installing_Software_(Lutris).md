---
title: "Explain Like I'm Five: Installing Software (Lutris)"
date: 2020-05-04
forum: Ubuntu/Debian BASED
---

### Post by nightyngale on 2020-05-04
**Relevant Info**
[LIST]
[*]Using [LXLE]("https://lxle.net/") distro based on Ubuntu 18.04.4
[*]Completely new to Linux
[/LIST]

Hello, Ubuntu Forums. I have an old laptop that came with Windows 7 that I decided I wanted to try Linux on, rather than upgrading to Windows 10, as Windows tends to run very slowly. After looking at available distros, I decided I wanted a lightweight distro based on Ubuntu, and settled on LXLE. So far I've been doing basic tasks like browsing the internet and installing downloaded packages with my package manager just fine. Today, however, I decided I wanted to see if this laptop could run games, now that it's running more smoothly than it ever has on Windows. I found [Lutris]("https://lutris.net/"), which has the games I'm looking for, and went to download it.

This is where I got confused. Lutris said to install [Wine]("https://wiki.winehq.org/Download"). When looking at the Wine download page, I assumed I needed to install a "binary package" for Ubuntu. I navigated to the Ubuntu page, and was met with the following message: **"Ubuntu 18.04/Linux Mint 19.x do not provide FAudio, which is a dependency of current Wine." **Not yet knowing my Ubuntu version, I read past it at first and followed the first two steps on the page.


[LIST=1]
[*]I enabled 32 bit architecture with the command: ```
sudo dpkg --add-architecture i386
```
[*]I downloaded and added the repository key with the command: ```
wget -O - [https://dl.winehq.org/wine-builds/winehq.key](https://dl.winehq.org/wine-builds/winehq.key) | sudo apt-key add -
```
[/LIST]

Then I needed to know my Ubuntu version to proceed any further. After a brief Google search, I used the command "**lsb_release -a**" and found out I'm running 18.04.4 LTS. Which brought me back to the warning message above, about the FAudio dependency not being provided with my version. I assumed this meant I would have to download FAudio separately. I clicked through a few links and ended up [here]("https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/"), which is where I got totally lost. I did some more Google searches about using the Open Build System, downloading packages from PPAs, and installing software through a package manager, but none of it seemed like it was what I was looking for.

I've never installed a program that wasn't "download x file and double click to run," having come from Windows. Could someone please explain to me, in detail and step-by-step, what I'll need to do from here to finish downloading and installing FAudio, Wine, and Lutris?

---

### Post by coffeecat on 2020-05-04
LXLE

*Thread moved to **Ubuntu/Debian based** sub-forum.*

---

### Post by CatKiller on 2020-05-04
> **nightyngale said:**
> I've never installed a program that wasn't "download x file and double click to run," having come from Windows. Could someone please explain to me, in detail and step-by-step, what I'll need to do from here to finish downloading and installing FAudio, Wine, and Lutris?

In this specific case, that's what the Wine project are saying you should do:

> The quickest and easiest way to satisfy the new dependency is to download and install both the i386 and amd64 libfaudio0 packages before attempting to upgrade or install a WineHQ package. By installing the downloaded packages locally, you will not have to add the OBS repository. This only has to be done once.

.deb file are how software is stored in the repositories and transferred to your package manager to be installed. Here, the Wine people are saying that, because the WineHQ version needs this library, which won't get updates, you can get away with just grabbing the .deb files manually and installing them rather than the usual method of giving your package manager an additional source of software packages.

They're saying to go [here](https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/xUbuntu_18.04/) and grab the libfaudio0 .deb file from both the AMD64 and i386 directories and install them, which will then satisfy the WineHQ Wine version's dependencies.

For later versions of Ubuntu, including 20.04 LTS, this library is provided by the standard Ubuntu repositories, so you don't need to do this step, but 18.04 came out in 2018, before WineHQ needed this library.

---

### Post by nightyngale on 2020-05-04
Ah. That makes sense now that I look at it again. >.< I've installed the packages now and successfully installed Wine and Lutris. Thank you so much!

---

