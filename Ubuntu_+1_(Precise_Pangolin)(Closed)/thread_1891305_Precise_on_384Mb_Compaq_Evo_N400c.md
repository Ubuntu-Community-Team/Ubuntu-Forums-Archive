---
title: "Precise on 384Mb Compaq Evo N400c"
date: 2011-12-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by frncz on 2011-12-05
Hello

I successfully installed (clean install) Precise alpha 1 on a 384Mb Compaq Evo N400c with 160Gb disk. I could not use USB install - the machine does not pick up the USB. I had to use the CD on the docking station, on which I had burned the I386 alternate ISO. the standard ISO was too big to fit on the CD. It took a few goes, and did not recognise the WiFi card.
After connecting via a wired connection and downloading all updates I found that the wifi card was recognised.
It all seems to work fine. I have not observed much difference compared to Oneiric. The UNITY icons do not seem to shrink to 32 pixel, even after trying to do this in ccsm.
It is still a pretty slow machine. I wish I could put more RAM in it, it would then be quite usable.
Mike

---

### Post by paul_in_london on 2011-12-05
You could always try a minimal install and see if that's any more usable. See my post (#6) in this thread:

```
ubuntuforums.org/showthread.php?t=1845284&highlight=frugal+install
```

Once you've installed and booted into the minimal (CLI) environment you could install the gnome-related packages etc. that I suggested there or the basic Xfce or LXDE packages.

---

### Post by frncz on 2011-12-05
Thanks Paul

Your link is for oneiric and amd64. Do you have a precise link, for 386?

Cheers

Mike

---

### Post by kaldor on 2011-12-05
> **frncz said:**
> Do you have a precise link, for 386?

All daily builds are [_here_]("http://cdimage.ubuntu.com/daily-live/current/").You can grab whatever image you need. 

Hopefully this is what you are looking for.

---

### Post by paul_in_london on 2011-12-05
> **frncz said:**
> Thanks Paul

Your link is for oneiric and amd64. Do you have a precise link, for 386?

Cheers

Mike

No worries. Go here for Precise (i386) netboot:

```
archive.ubuntu.com/ubuntu/ubuntu/dists/precise/main/installer-i386/current/images/netboot/
```

You want the **mini.iso**.

Another couple of links for info:

```
ubuntuforums.org/showthread.php?t=1155961]
```

```
wiki.dennyhalim.com/debian-minimal-desktop-installation
```

EDIT: Another link:

```
forums.debian.net/viewtopic.php?t=18875
```

Just bear in mind that packages are sometimes superseded or renamed.

One way of getting info about a package is (taking **gnome-core** as an example):

```
paul@precise-64:~$ apt-cache show gnome-core
Package: gnome-core
Priority: optional
Section: universe/gnome
Installed-Size: 42
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Architecture: amd64
Source: meta-gnome3
Version: 1:3.0+5ubuntu1
Depends: brasero (>= 3.0), dconf-gsettings-backend (>= 0.7.5), dconf-tools (>= 0.7.5), empathy (>= 3.0), eog (>= 3.0), epiphany-browser (>= 3.0), evince (>= 3.0), evolution-data-server (>= 3.0), fonts-cantarell, sound-theme-freedesktop, gcalctool (>= 6.0), gconf2 (>= 2.32), gdm (>= 3.0), glib-networking (>= 2.28.7), gnome-backgrounds (>= 3.0), gnome-bluetooth (>= 3.0), gnome-contacts, gnome-control-center (>= 1:3.0), gnome-disk-utility (>= 3.0), gnome-icon-theme (>= 3.0), gnome-icon-theme-extras (>= 3.0), gnome-icon-theme-symbolic (>= 3.0), gnome-keyring (>= 3.0), libpam-gnome-keyring (>= 3.0), gnome-menus (>= 3.0), synaptic, gnome-panel (>= 3.0), gnome-power-manager (>= 3.0), gnome-screensaver (>= 3.0), gnome-session (>= 3.0), gnome-session-fallback (>= 3.0), gnome-settings-daemon (>= 3.0), gnome-shell (>= 3.0), gnome-system-monitor (>= 3.0), gnome-terminal (>= 3.0), gnome-themes-standard (>= 3.0), gnome-user-guide (>= 3.0), gnome-user-share (>= 3.0), baobab (>= 3.0), gnome-dictionary (>= 3.0), gnome-screenshot (>= 3.0), gnome-search-tool | tracker-gui, gnome-system-log (>= 3.0), gnome-font-viewer (>= 3.0), gsettings-desktop-schemas (>= 3.0), gstreamer0.10-plugins-base (>= 0.10.34), gstreamer0.10-plugins-good (>= 0.10.29), gstreamer0.10-pulseaudio (>= 0.10.29), libgail-3-common (>= 3.0) | libgtk-3-common (>= 3.2), gucharmap (>= 1:3.0), gvfs-backends (>= 1.8), libcanberra-pulse, metacity (>= 1:2.34), nautilus (>= 3.0), network-manager-gnome (>= 0.9), notification-daemon (>= 0.7), policykit-1-gnome, pulseaudio, totem (>= 3.0), vino (>= 3.0), yelp (>= 3.0), zenity (>= 3.0)
Suggests: gnome
Filename: pool/universe/m/meta-gnome3/gnome-core_3.0+5ubuntu1_amd64.deb
Size: 4188
MD5sum: 0ef1970f1f13fad59e666712b24cd564
SHA1: 6e5145944e2951a69a4e909cf9729f0ee6470ef9
SHA256: 6e691184796da3058af86ae59aff8eddee7bf8af1cca43392b4148abf75e36c3
Description-en: The GNOME Desktop Environment -- essential components
 These are the core components of the GNOME Desktop environment, an
 intuitive and attractive desktop.
 .
 This meta-package depends on a basic set of programs, including a file
 manager, an image viewer, a web browser, a video player and other
 tools.
 .
 It contains the official &#8220;core&#8221; modules of the GNOME desktop.
Description-md5: c7dafd3a169eb4a931ca43611d929be2
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

paul@precise-64:~$
```

And you don't even need to install all of **gnome-core**. Look at the "Depends" line and pick the bits you want - e.g. you might not want **brasero** etc.

---

### Post by ventrical on 2011-12-06
I just built a system with a 600MHz PIII and Precise works just great!!  with Unity 2D .

---

### Post by paul_in_london on 2011-12-06
Another link I meant to add yesterday (this one has installation screenshots):

[Modest Spec or Barebones Installation of Ubuntu](www.psychocats.net/ubuntu/minimal)

---

### Post by jbicha on 2011-12-07
gnome-core is the Debian metapackage for GNOME; Ubuntu uses ubuntu-desktop which has different choices.

---

### Post by paul_in_london on 2011-12-07
> **jbicha said:**
> gnome-core is the Debian metapackage for GNOME; Ubuntu uses ubuntu-desktop which has different choices.

Yes, I know what you're saying. I just got into the habit of only installing some (or all) of the **gnome-core** dependencies along with certain dependencies of **ubuntu-desktop** such as alsa-base and ubuntu-artwork.

**gnome-core (precise)**:

```
**Depends**: brasero (>= 3.0), dconf-gsettings-backend (>= 0.7.5), dconf-tools (>= 0.7.5),\
empathy (>= 3.0), eog (>= 3.0), epiphany-browser (>= 3.0),\
evince (>= 3.0), evolution-data-server (>= 3.0),\
fonts-cantarell, sound-theme-freedesktop, gcalctool (>= 6.0),\
gconf2 (>= 2.32), gdm (>= 3.0), glib-networking (>= 2.28.7),\
gnome-backgrounds (>= 3.0), gnome-bluetooth (>= 3.0),\
gnome-contacts, gnome-control-center (>= 1:3.0),\
gnome-disk-utility (>= 3.0),gnome-icon-theme (>= 3.0),\
gnome-icon-theme-extras (>= 3.0),\
gnome-icon-theme-symbolic (>= 3.0), gnome-keyring (>= 3.0),\
libpam-gnome-keyring (>= 3.0), gnome-menus (>= 3.0),\
synaptic, gnome-panel (>= 3.0), gnome-power-manager (>= 3.0),\
gnome-screensaver (>= 3.0), gnome-session (>= 3.0),\
gnome-session-fallback (>= 3.0), gnome-settings-daemon (>= 3.0),\ gnome-shell (>= 3.0),\
gnome-system-monitor (>= 3.0),\
gnome-terminal (>= 3.0), gnome-themes-standard (>= 3.0),\
gnome-user-guide (>= 3.0), gnome-user-share (>= 3.0),\
baobab (>= 3.0), gnome-dictionary (>= 3.0),
gnome-screenshot (>= 3.0),\
gnome-search-tool | tracker-gui,\
gnome-system-log (>= 3.0), gnome-font-viewer (>= 3.0),\
gsettings-desktop-schemas (>= 3.0),\
gstreamer0.10-plugins-base (>= 0.10.34),\
gstreamer0.10-plugins-good (>= 0.10.29),\
gstreamer0.10-pulseaudio (>= 0.10.29),\
libgail-3-common (>= 3.0) | libgtk-3-common (>= 3.2),\
gucharmap (>= 1:3.0), gvfs-backends (>= 1.8), libcanberra-pulse,\
metacity (>= 1:2.34), nautilus (>= 3.0),\
network-manager-gnome (>= 0.9), notification-daemon (>= 0.7),\
policykit-1-gnome,\
pulseaudio, totem (>= 3.0), vino (>= 3.0), yelp (>= 3.0),\
zenity (>= 3.0)
```

**ubuntu-desktop (precise)**:

```
**Depends**: alsa-base, alsa-utils, anacron, at-spi2-core, baobab, bc, ca-certificates,\
checkbox-gtk, dc, dmz-cursor-theme, doc-base, eog, evince,\
file-roller, foomatic-db-compressed-ppds, foomatic-filters,\
gcalctool, gedit, genisoimage, ghostscript-x,\
gnome-control-center,\
gnome-font-viewer, gnome-media, gnome-menus, gnome-nettool,\
gnome-power-manager, gnome-screenshot, gnome-search-tool,
gnome-session, gnome-session-canberra, gnome-system-log,
gnome-system-monitor, gnome-terminal, gstreamer0.10-alsa,
gstreamer0.10-plugins-base-apps, gstreamer0.10-pulseaudio,\
gucharmap, gvfs-bin, gwibber, inputattach,\
language-selector-gnome,
launchpad-integration, lftp, libatk-adaptor,\
libgd2-xpm, libnotify-bin, libpam-ck-connector,\
libsasl2-modules, libsdl1.2debian, libxp6, lightdm,\
nautilus, nautilus-sendto, notify-osd, nvidia-common,\
openprinting-ppds, pnm2ppa, pulseaudio, rarian-compat,\
rfkill, seahorse, software-center, software-properties-gtk,\
ssh-askpass-gnome, system-config-printer-gnome,\
ttf-dejavu-core, ttf-freefont, ubuntu-artwork,\
ubuntu-extras-keyring, ubuntu-sounds,\
unity, unity-2d, unity-greeter, unzip,\
update-manager, update-notifier,\
wireless-tools, wpasupplicant,\
x-ttcidfont-conf, xdg-user-dirs, xdg-user-dirs-gtk,\
xdiagnose, xkb-data, xorg, xterm, yelp, zenity, zip
```

---

