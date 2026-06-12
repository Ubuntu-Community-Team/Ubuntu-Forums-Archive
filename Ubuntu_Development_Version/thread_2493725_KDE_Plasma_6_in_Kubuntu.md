---
title: "KDE Plasma 6 in Kubuntu"
date: 2023-12-22
forum: Ubuntu Development Version
---

### Post by enricobe on 2023-12-22
Hello, is there any way to install a Plasma 6 version of Kubuntu? Alpha, Beta, Core, Backports etc versions are fine too.

I can't find any way to have Plasma 6 on Kubuntu

---

### Post by #&amp;thj^% on 2023-12-22
You would have to build it from source: [https://community.kde.org/Get_Involved/development/Build_software_with_kdesrc-build#Plasma](https://community.kde.org/Get_Involved/development/Build_software_with_kdesrc-build#Plasma)
So far these OS's have it as an option:
Fedora
KaOS ISO
KaOS Install
KDE Neon Unstable ISO
Nix Flake
openSUSE Krypton

---

### Post by enricobe on 2023-12-22
Thanks, I've seen the KDE webpage reporting the distro, but I would like to test it on the Ubuntu base (Neon Unstable is always broken) :)
I suppose there is no way to have Plasma 6 on ubuntu at the moment, so I'll go for KaOS

---

### Post by MAFoElffen on 2023-12-22
On building it in Noble Kubuntu, I get this error:
```

Building ki18n from frameworks 92/142)
           Fetching remote changes to ki18n
           Merging ki18n changes from branch master
           Source update complete for ki18n: no files affected
             Rebuilding because last configure failed
           Preparing build system for ki18n.
           Old build system cleaned, starting new build system.
           Running cmake targeting Kate - Ninja...
           Unable to configure ki18n with KDE Cmake
ki18n didn't build, stopping here

```
That is where I am stuck at the moment on Noble.

---

### Post by #&amp;thj^% on 2023-12-22
So close, but no bananas, I thought somewhere it would fail.
I thought that was helpful MAFoElffen, you saved me some time.

---

### Post by MAFoElffen on 2023-12-22
::Whispered In Low Hushes:: --> This morning's OpenSUSE Krypton Daily Build installs with KDE 6.0 Beta 2...

(EDIT: Dang. took forever to install, & pegs 8GB RAM down to a halt.)

---

### Post by Ganton on 2024-01-19
> > KDE Plasma 6 in Kubuntu 

> [https://community.kde.org/Get_Involved/development/Build_software_with_kdesrc-build](https://community.kde.org/Get_Involved/development/Build_software_with_kdesrc-build)

I found that "The default configuration of kdesrc-build requires Qt version 6.5. Kubuntu 23.10 has Qt version 6.4.2" on [https://community.kde.org/Get_Involved/development/More#Kubuntu_23.10](https://community.kde.org/Get_Involved/development/More#Kubuntu_23.10)

The same happens nowadays with Noble ([https://packages.ubuntu.com/Qt6Core](https://packages.ubuntu.com/Qt6Core)).

Edit: 
    
For having Qt 6.6, there is the option of using kdesrc-build to build KDE Plasma 6 and Qt 6 ([https://community.kde.org/Get_Involved/development/More#Build_Qt_using_kdesrc-build](https://community.kde.org/Get_Involved/development/More#Build_Qt_using_kdesrc-build)).

---

### Post by zoopgoop on 2024-05-13
> **MAFoElffen said:**
> On building it in Noble Kubuntu, I get this error:
```

Building ki18n from frameworks 92/142)
           Fetching remote changes to ki18n
           Merging ki18n changes from branch master
           Source update complete for ki18n: no files affected
             Rebuilding because last configure failed
           Preparing build system for ki18n.
           Old build system cleaned, starting new build system.
           Running cmake targeting Kate - Ninja...
           Unable to configure ki18n with KDE Cmake
ki18n didn't build, stopping here

```
That is where I am stuck at the moment on Noble.

I had this issue, and it turned out I had my `qt-install-directory` set improperly, so it couldn't find Qt's custom cmake functions.

I installed via the QT Online Installer ([https://doc.qt.io/qt-6/qt-online-installation.html](https://doc.qt.io/qt-6/qt-online-installation.html) - you need an account). After running `kde-builder --generate-config`, uncomment the line `qt-install-dir` in `~/.config/kdesrc-buildrc`, and set it like this:

```

[FONT=monospace][COLOR=#000000]qt-install-dir ~/Qt/6.7.1/gcc_64[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]
[/COLOR]
(Replace ~/Qt with wherever you installed it - that's the default, and of course if you installed a different version of Qt, pick that). This will let it properly import CMAKE. I also recommend setting your `PKG_CONFIG_PATH` to `~/Qt/6.7.1/gcc_64/pkgconfig`.

Note: I don't recommend using the easy installation from the Qt installer, I was missing several important things (e.g. the Qt 5 compatibility module) - I recommend doing a custom installation and selecting everything under one version.

After this, you mostly just have to play dependency whack-a-mole.
[/FONT]

---

### Post by IanW on 2024-05-13
As this is currently the Oracular forum, I should point out that the release schedule says QT6.6.2 was due to be added to 24.10 on May 2nd.
KDE Framework 6 is due to join it on May 16th.

---

### Post by microcris on 2024-07-12
Helo!

It is being packed in [https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/experimental](https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/experimental)
Does anyone have tried it?

So far, for me, SDDM only shows the mouse pointer. To have a plasma session I have to run startplasma-wayland.

Edit:
[It is working]("https://drive.google.com/file/d/1zpNnMls7ZN7V_ScQUKJ75XvYGcIZRh80/view?usp=sharing")

Had to get the sddm package from debian. For an experimental release, it is quite good

---

### Post by enricobe on 2024-07-28
Hello, I switched to another distro in these months. 
I tried to download the daily 24.10 ISO today, but it still ships Plasma 5.27. :(

> **microcris said:**
> Helo!

It is being packed in [https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/experimental](https://launchpad.net/~kubuntu-ppa/+archive/ubuntu/experimental)
Does anyone have tried it?

So far, for me, SDDM only shows the mouse pointer. To have a plasma session I have to run startplasma-wayland.

Edit:
[It is working]("https://drive.google.com/file/d/1zpNnMls7ZN7V_ScQUKJ75XvYGcIZRh80/view?usp=sharing")

Had to get the sddm package from debian. For an experimental release, it is quite good

Are you using it daily? Does it work fine?

---

### Post by enricobe on 2024-08-31
Just for information: the daily ISOs now include Plasma 6

[https://cdimage.ubuntu.com/kubuntu/daily-live/current/](https://cdimage.ubuntu.com/kubuntu/daily-live/current/)

---

