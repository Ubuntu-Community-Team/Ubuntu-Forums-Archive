---
title: "Today apt want remove a lot of useful applications"
date: 2023-07-08
forum: Ubuntu Development Version
---

### Post by corradoventu on 2023-07-08
Today apt want remove a lot of useful applications. Is this the result of this discussion?
[https://discourse.ubuntu.com/t/rethinking-ubuntu-desktop-a-more-thoughtful-default-installation/36736/56](https://discourse.ubuntu.com/t/rethinking-ubuntu-desktop-a-more-thoughtful-default-installation/36736/56)
If yes Ubuntu will become too poor for a novice user who won't be able to find applications that are essential

```
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  aisleriot baobab branding-ubuntu cheese cheese-common file-roller gir1.2-rb-3.0 gnome-mahjongg gnome-mines gnome-sudoku
  gnome-video-effects gstreamer1.0-clutter-3.0 guile-3.0-libs libavahi-ui-gtk3-0 libcdr-0.1-1 libchamplain-0.12-0
  libchamplain-gtk-0.12-0 libcheese-gtk25 libcheese8 libclutter-gst-3.0-0 libdmapsharing-4.0-3 libevent-2.1-7 libfreehand-0.1-1
  libfreerdp-client2-2 libgnome-games-support-1-3 libgnome-games-support-common libgpod-common libgpod4 libgupnp-igd-1.0-4 libixml10
  liblc3-0 libminiupnpc17 libmspub-0.1-1 libmujs2 libnatpmp1 libpagemaker-0.0-0 libqqwing2v5 libreoffice-calc libreoffice-draw
  libreoffice-gnome libreoffice-gtk3 libreoffice-impress librhythmbox-core10 libsdl-image1.2 libsdl1.2debian libsgutils2-1.46-2
  libupnp13 libvisio-0.1-1 lp-solve media-player-info python3-mako python3-renderpm python3-reportlab-accel remmina remmina-common
  remmina-plugin-rdp remmina-plugin-secret remmina-plugin-vnc rhythmbox rhythmbox-data rhythmbox-plugin-alternative-toolbar
  rhythmbox-plugins shotwell shotwell-common simple-scan transmission-common transmission-gtk
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
corrado@corrado-n03-mm-0607:~$ 
```

---

### Post by jbicha on 2023-07-08
Please file a bug against ubuntu-desktop . That effect was not intended.

I expect that this issue won't affect people who use the usual Ubuntu tool to upgrade to the new release closer to the Ubuntu 23.10 release date, but it might not be fixable for those already using Ubuntu 23.10 early.

You could manually "install" the apps on that line that you want to keep.

---

### Post by guiverc on 2023-07-08
Thanks for posting this C[COLOR=#000000]orradoventu[/COLOR], and thanks Jeremy for reply[I]..

[/I]I'll have to pay *more* attention to my own upgrades.. I didn't suffer those removals, but my box is also *bloated* down with lubuntu-desktop, xubuntu-desktop & more.

( I pay particularly focus to the Lubuntu packages ; less so others )

Let us know the bug report, I'm interested.  On my own system I don't have `branding-ubuntu` installed (see only reverse depends on ubuntu-unity-desktop & ubuntukylin-desktop) but have transmission-common installed; picking a couple of packages to look up on my own box.

---

### Post by corradoventu on 2023-07-09
My bug: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/2026637](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/2026637)

---

### Post by corradoventu on 2023-07-17
Installing from last ISO all the apps listed above are MISSING so you will have something like a MINIMAL installation

---

### Post by guiverc on 2023-07-17
I really welcomed/appreciated Julian Andres Klode (juliank)'s explaining why.  To me at least it makes sense. 

We've (*I'm thinking Lubuntu here*) provided links like [https://discourse.lubuntu.me/t/dropping-trojita-k3b-fcitx-from-lubuntu-jammy-22-04-seed/3044](https://discourse.lubuntu.me/t/dropping-trojita-k3b-fcitx-from-lubuntu-jammy-22-04-seed/3044) before for those upgrading from prior releases that may notice (*and not appreciate*) such behavior.

Bug reports like yours are often how they get noticed... esp. when it's not a particular package that was listed on the *seed* file (*but included due to depends/suggest etc*)

---

