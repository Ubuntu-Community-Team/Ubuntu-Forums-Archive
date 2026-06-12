---
title: "minimal X11 over ssh?"
date: 2009-03-26
forum: Server Platforms
---

### Post by lavinog on 2009-03-26
I just setup a new server that runs off of a CF card so I want to minimize wasted space.
I want to install Xorg so I can use X over ssh while I am at school.
If I try and apt-get xorg, I get about 100M in dependencies.
```
The following NEW packages will be installed:
  defoma fontconfig-config libdrm2 libfontconfig1 libfontenc1 libfreetype6 libfs6 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libhal1 libice6 libpciaccess0
  libpixman-1-0 libpng12-0 libsm6 libxaw7 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxkbfile1 libxmu6 libxpm4 libxrandr2
  libxrender1 libxt6 libxtrap6 libxtst6 libxv1 libxxf86dga1 libxxf86misc1 libxxf86vm1 mdetect ttf-dejavu ttf-dejavu-core ttf-dejavu-extra x11-apps
  x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils xbitmaps xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings xfonts-scalable
  xfonts-utils xinit xinput xorg xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-kbd
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nv xserver-xorg-video-openchrome xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb
  xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware
  xserver-xorg-video-voodoo xterm
0 upgraded, 99 newly installed, 0 to remove and 0 not upgraded.
Need to get 32.1MB of archives.
After this operation, 93.5MB of additional disk space will be used.

```
Many of the packages look like video drivers, since this is a headless server, are they really needed?
Is there a way to forward X apps without all of the bulk?
Could I just manually delete the drivers that are not needed?

---

### Post by cariboo on 2009-03-26
Just install the packages you need, for instance synatic and it will install enough to allow you to use X forwarding, then when you want to run synaptic type:

```
ssh -X user@server
```

then at the prompt type:

```
sudo synaptic
```

I personally use mc to do all file operations, for me it works well.

Jim

---

### Post by HermanAB on 2009-03-26
You don't X on the server. You need X on your school PC.  SSH will forward X requests from the server to your PC.

For example, install gedit on the server, then do:
ssh -X -C -c blowfish user@server 'gedit /etc/fstab'

Cheers,

Herman

---

### Post by BkkBonanza on 2009-03-26
Ya but.
Installing gedit brings 135 MB in dependencies with it too.
Hmmm.

---

### Post by Xiong Chiamiov on 2009-03-27
> **BkkBonaza said:**
> Ya but.
Installing gedit brings 135 MB in dependencies with it too.
Hmmm.
That's because gedit is a core gnome utility.

---

