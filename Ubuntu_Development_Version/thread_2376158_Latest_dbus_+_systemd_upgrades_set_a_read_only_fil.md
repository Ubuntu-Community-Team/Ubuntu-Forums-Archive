---
title: "Latest dbus + systemd upgrades set a read only filesystem"
date: 2017-10-30
forum: Ubuntu Development Version
---

### Post by dino99 on 2017-10-30
Warning about the proposed dbus & systemd updates on Bionic, as that ends with a read only filesystem, and startx also fails.

Looks like it is related to the tmpfiles right change in systemd:

 [ Michael Biebl ]
  * New upstream version 235
    - cryptsetup-generator: use remote-cryptsetup.target when _netdev is
      present (Closes: #852534)
    - tmpfiles: change btmp mode 0600 &#8594; 0660 (Closes: #870638)

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1728773](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1728773)

---

### Post by dino99 on 2017-10-31
Feedback

due to a shared /home partition, that was in fact a transitional conflict with the old settings.

---

### Post by rrnbtter on 2017-10-31
Greetings, 
Proposed = off.
Latest update removes gnome-shell and gdm3 and reboots to a text console login. After login I reinstalled gnome-shell and gdm3 from the prompt and it boots back to normal gnome/gdm3/wayland. 
Note: I keep a backup of var/cache/archives.

---

### Post by harry332 on 2017-10-31
rrnbetter,

And what update that might be.
No such issue here and I have proposed on with all the updates available from the main server.

---

### Post by dino99 on 2017-10-31
@harry
systemd 235 was available into proposed archive, but has been blocked by the dev (see report link above)

---

### Post by rrnbtter on 2017-10-31
Greetings,
@harry332

here it is.
The following packages were automatically installed and are no longer required:
  gir1.2-totemplparser-1.0 liba52-0.7.4 libaacs0 libass9 libavcodec57
  libavutil55 libbasicusageenvironment1 libbdplus0 libbluray2 libcddb2
  libchromaprint1 libcrystalhd3 libdc1394-22 libdca0 libdvbpsi10 libdvdnav4
  libdvdread4 libebml4v5 libfaad2 libgme0 libgroupsock8 libicu57:i386
  libiso9660-10 libiso9660-8 libkate1 liblivemedia58 liblua5.2-0 libmad0
  libmatroska6v5 libmp3lame0 libmpcdec6 libmpeg2-4 libopenjp2-7
  libopenmpt-modplug1 libopenmpt0 libproxy-tools libqt5dbus5 libqt5network5
  libresid-builder0c2a libsdl-image1.2 libshine3 libsidplay2 libsnappy1v5
  libsoxr0 libssh-gcrypt-4 libssh2-1 libswresample2 libtwolame0 libupnp6
  libusageenvironment3 libvcdinfo0 libvdpau1 libvlc-bin libvlc5 libvlccore8
  libx264-148 libx265-130 libxcb-xinerama0 libxvidcore4 libzvbi-common
  libzvbi0 mesa-vdpau-drivers vdpau-driver-all vlc-bin vlc-data vlc-l10n
  vlc-plugin-base vlc-plugin-notify vlc-plugin-samba vlc-plugin-video-splitter
  vlc-plugin-visualization
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  caribou gdm3 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-webkit2-4.0 gnome-control-center gnome-getting-started-docs
  gnome-online-accounts gnome-session-bin gnome-shell gnome-user-docs
  gnome-user-guide gstreamer1.0-clutter-3.0 libcheese-gtk25 libcheese8
  libclutter-1.0-0 libclutter-gst-3.0-0 libclutter-gtk-1.0-0 libcogl-pango20
  libcogl-path20 libcogl20 libgoa-backend-1.0-1 libqt5gui5 libqt5opengl5
  libqt5printsupport5 libqt5svg5 libqt5widgets5 libqt5x11extras5
  libwebkit2gtk-4.0-37 libyelp0 mutter qt5-gtk-platformtheme ubuntu-docs
  ubuntu-release-upgrader-gtk ubuntu-session update-manager update-notifier
  virtualbox-qt vlc vlc-plugin-qt vlc-plugin-skins2 vlc-plugin-video-output
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-libinput xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev
  xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-qxl
  xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware
  yelp zenity
The following packages have been kept back:
  libmirclient9 libmirclient9:i386 libmircommon7 libmircommon7:i386
0 upgraded, 0 newly installed, 60 to remove and 4 not upgraded.
After this operation, 151 MB disk space will be freed.
Do you want to continue? [Y/n] 

This was in proposed Sunday. It didn't show up in with proposed off until today. I had been install regular updates from Main until this appeared. Since it was removing gdm and gnome shell I knew I would get a "no boot" but gave it a shot anyway. Results "no boot".  Reinstalled gdm and gnome-shell from the prompt and I'm right back where I started but the system seems much soother now. It may have replaced some config files.
FYI

---

### Post by harry332 on 2017-10-31
rrnbtter,

Still not sure what was the package that tried to cause that kind of uninstallation procedure.
I have all the updates/upgrades installed from the proposed repo and no such kind of behaviour, no uninstallations, my setup is working really fine.

---

### Post by harry332 on 2017-10-31
dino 99,

OK fine, I have that version of systemd (235-2ubuntu1) installed and I have ubsolutely no issues with my setup.
I reckon that update is "block-proposed" but not "blocked". It is still available in the bionic-proposed repo right now.

---

### Post by rrnbtter on 2017-10-31
Greetings, 
I'm just wondering if they are proposing removing gnome and wayland to fall back to xorg due to new users and others having problems with wayland incompatible software from the xorg menu. I like what I have but at the same time I have switched to wayland compatible applications or am using the few workarounds.

---

### Post by jbicha on 2017-10-31
> **rrnbtter said:**
> Greetings, 
Proposed = off.
Latest update removes gnome-shell and gdm3 and reboots to a text console login.

Please read through
```

/var/log/apt/history.log

```

I suspect you had third-party packaged installed from a PPA.

> **rrnbtter said:**
> Greetings, 
I'm just wondering if they are proposing removing gnome

No.

> **rrnbtter said:**
> Greetings, 
I'm just wondering if they are proposing removing gnome and wayland to  fall back to xorg due to new users and others having problems with  wayland incompatible software from the xorg menu.

I'm sure it will be discussed but honestly I think the Ubuntu Desktop team and other developers are fairly happy with Ubuntu defaulting to Wayland with a Ubuntu on Xorg option available. Obviously, we're working to make Wayland more reliable and featureful. I don't think anyone is working on fixing Synaptic (try gnome-packagekit or just apt or maybe even aptitude or just use Ubuntu on Xorg).

Similarly, no one is really working on GParted. GNOME Disks may end up being the replacement there.

I think gufw was working years ago, but one of the developers thought the code was too difficult to use and switched from PolicyKit to pkexec so he'll probably need to switch back.

---

### Post by rrnbtter on 2017-10-31
Greetings,
@jbicha
Thanks, these updates were already available in proposed as verified by harry332. I am just going to wait it out and give them time to fix the problem. I don't have any ppa's enabled and those add/remove packages will result in a no boot situation.  That in itself is not a problem but I have already fixed it once and don't care to fix it again.  
The current problem is that with proposed unchecked the "proposed" update packages are still listed in the update que (and they should not be). If the problem persists I will delete my sources.list and start over.

---

### Post by rrnbtter on 2017-10-31
Greetings,
OK, I fixed it!
Solution
1. sudo rm /var/lib/apt/lists/*
2. abandon "apt-get" and use "apt update"
3. to check upgradeable files "apt list --upgradable"
4. if all looks good then "apt upgrade"
Now all updates installed with proposed enabled. No errors.

---

### Post by lisati on 2017-11-01
Thread closed by request.

---

