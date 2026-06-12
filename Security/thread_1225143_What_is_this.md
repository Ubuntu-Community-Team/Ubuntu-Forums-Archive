---
title: "What is this"
date: 2009-07-28
forum: Security
---

### Post by dragos2 on 2009-07-28
What is this ? Ubuntu Server 8.04 64 bit

```

someuserhere   30287  0.2  0.0 122384  5236 ?        S    05:55   0:55 /usr/bin/pulseaudio --log-target=syslog

```

---

### Post by cb951303 on 2009-07-28
if you're asking what is pulseaudio then it's a sound server/proxy.

---

### Post by rannable on 2009-07-28
damn, you beat me to it :)

---

### Post by dragos2 on 2009-07-28
> **cb951303 said:**
> if you're asking what is pulseaudio then it's a sound server/proxy.

I should have been more clear, what is that process on my server? :)

---

### Post by cdenley on 2009-07-28
> **dragos2 said:**
> I should have been more clear, what is that process on my server? :)

If it is running on a server, it is still a sound server/proxy. If you're asking why it is installed on a server, it was probably installed as a dependency. I don't have that process on any of my hardy servers. Did you by any chance install java on your server? Post this output:
```

dpkg-query -f='${Package}\n${Depends}\n' -W|grep pulse

```

---

### Post by igorzwx on 2009-07-28
Perhaps, pulse has nothing to do on a server.
I is a security risk.

---

### Post by cariboo on 2009-07-28
I would suggest that you have the ubuntu desktop installed on your server. All sorts of unneeded progams are installed when you install the desktop

---

### Post by igorzwx on 2009-07-28
I can imagine that pulse is now included to server too.
A kind of innovation.

---

### Post by cariboo on 2009-07-28
Pulse is not installed by default using the server version.

@igorzwx

I take it you don't like pulse. :)

---

### Post by igorzwx on 2009-07-28
I am not a masochist.

Have your tried OSS4?
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by cariboo on 2009-07-29
<offtopic>

Sound has worked for me since I built this computer. I've installed every version since 6.06 and I am currently running 9.10, and have never needed to remove pulse.

</offtopic>

---

### Post by dragos2 on 2009-07-29
> **cdenley said:**
> If it is running on a server, it is still a sound server/proxy. If you're asking why it is installed on a server, it was probably installed as a dependency. I don't have that process on any of my hardy servers. Did you by any chance install java on your server? Post this output:
```

dpkg-query -f='${Package}\n${Depends}\n' -W|grep pulse

```

Yes, there is gnome-core, but I am wondering why that user use that program..
And yes, there is Java installed.

gstreamer0.10-pulseaudio
libc6 (>= 2.7-1), libglib2.0-0 (>= 2.16.0), libgstreamer-plugins-base0.10-0 (>= 0.10.0), libgstreamer0.10-0 (>= 0.10.14), libpulse0 (>= 0.9.8), libxml2
libbonobo2-0 (>= 2.15.0), libc6 (>= 2.7-1), libespeak1 (>= 1.27), libglib2.0-0 (>= 2.15.4), liborbit2 (>= 1:2.14.10), libstdc++6, pulseaudio-utils
libpulse-browse0
libavahi-client3 (>= 0.6.13), libavahi-common3 (>= 0.6.10), libc6 (>= 2.4), libcap1, libpulse0 (>= 0.9.8)
libpulse0
libpulsecore5
libsdl1.2debian-alsa (= 1.2.13-1ubuntu1) | libsdl1.2debian-all (= 1.2.13-1ubuntu1) | libsdl1.2debian-esd (= 1.2.13-1ubuntu1) | libsdl1.2debian-arts (= 1.2.13-1ubuntu1) | libsdl1.2debian-oss (= 1.2.13-1ubuntu1) | libsdl1.2debian-nas (= 1.2.13-1ubuntu1) | libsdl1.2debian-pulseaudio (= 1.2.13-1ubuntu1)
pulseaudio
adduser, libasound2 (>> 1.0.14), libc6 (>= 2.4), libcap1, libdbus-1-3 (>= 1.1.1), libflac8, libltdl3 (>= 1.5.2-2), libogg0, liboil0.3 (>= 0.3.1), libpulsecore5, libsamplerate0, libsndfile1, libwrap0, lsb-base (>= 3), sysv-rc (>= 2.86.ds1-14.1ubuntu2)
pulseaudio-esound-compat
libc6 (>= 2.4), libcap1, libpulsecore5
pulseaudio-module-gconf
libc6 (>= 2.4), libcap1, libflac8, libgconf2-4 (>= 2.13.5), libglib2.0-0 (>= 2.16.0), libltdl3 (>= 1.5.2-2), libogg0, liboil0.3 (>= 0.3.0), libpulsecore5, libsamplerate0, libsndfile1
pulseaudio-module-hal
hal, libc6 (>= 2.2.5), libcap1, libdbus-1-3 (>= 1.1.1), libhal1 (>= 0.5.8.1), libpulsecore5
pulseaudio-module-x11
libc6 (>= 2.4), libcap1, libice6 (>= 1:1.0.0), libpulsecore5, libsm6, libx11-6, pulseaudio-utils
pulseaudio-utils
libavahi-client3 (>= 0.6.13), libavahi-common3 (>= 0.6.10), libc6 (>= 2.4), libcap1, libflac8, libice6 (>= 1:1.0.0), libogg0, libpulse-browse0, libpulse0, libsm6, libsndfile1, libx11-6
acpi, acpi-support, acpid, alacarte, alsa-base, alsa-utils, anacron, avahi-daemon, bc, ca-certificates, consolekit, cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gutenprint, dc, dcraw, desktop-file-utils, doc-base, eog, evince, fast-user-switch-applet, file-roller, foomatic-db, foomatic-db-engine, foomatic-filters, gcalctool, gconf-editor, gdebi, gdm, gedit, genisoimage, ghostscript-x, gimp-python, gnome-about, gnome-app-install, gnome-applets, gnome-control-center, gnome-icon-theme, gnome-media, gnome-menus, gnome-netstatus-applet, gnome-nettool, gnome-panel, gnome-pilot-conduits, gnome-power-manager, gnome-session, gnome-spell, gnome-system-monitor, gnome-system-tools, gnome-terminal, gnome-themes, gnome-utils, gnome-volume-manager, gstreamer0.10-alsa, gstreamer0.10-plugins-base-apps, gstreamer0.10-pulseaudio, gtk2-engines, gtk2-engines-pixbuf, gucharmap, hal, hotkey-setup, hwtest-gtk, language-selector, launchpad-integration, lftp, libgl1-mesa-glx, libglut3, libgnome2-perl, libgnomevfs2-bin, libgnomevfs2-extra, libpt-1.10.10-plugins-v4l, libpt-1.10.10-plugins-v4l2, libsasl2-modules, libxp6, metacity, nautilus, nautilus-cd-burner, nautilus-sendto, notification-daemon, openprinting-ppds, pnm2ppa, powermanagement-interface, pulseaudio, pulseaudio-esound-compat, readahead, rss-glx, screen, screensaver-default-images, scrollkeeper, seahorse, smbclient, software-properties-gtk, ssh-askpass-gnome, synaptic, system-config-printer-gnome, tangerine-icon-theme, tsclient, ttf-bitstream-vera, ttf-dejavu-core, ttf-freefont, ubuntu-artwork, ubuntu-sounds, unzip, update-manager, update-notifier, usplash, usplash-theme-ubuntu, x-ttcidfont-conf, xdg-user-dirs, xdg-user-dirs-gtk, xkb-data, xorg, xscreensaver-data, xscreensaver-gl, xterm, yelp, zenity, zip

---

### Post by igorzwx on 2009-07-29
QUOTE:
"Sound has worked for me since I built this computer. I've installed every version since 6.06 and I am currently running 9.10, and have never needed to remove pulse."

Have you tried Skype and Ekiga with pulse?
Do you have noise, delay, latency when you use Skype and Ekiga
with PulseAudio?
Do you have a quadro core or else?

---

### Post by cdenley on 2009-07-29
I'm guessing it was installed as a dependency for java. The openjdk-6-jre package depends on libpulse0. However, I think the openjdk-6-jre-headless package exists so dependencies like these aren't installed on a headless server. Try removing openjdk-6-jre and pulse packages.
```

sudo apt-get remove openjdk-6-jre libpulse0 pulseaudio-utils gstreamer0.10-pulseaudio pulseaudio

```

---

### Post by koenn on 2009-07-29
> **igorzwx said:**
> I can imagine that pulse is now included to server too.
A kind of innovation.
so server admins can have a login sound too. after all, they are humans beings.

---

### Post by dragos2 on 2009-07-30
> **cdenley said:**
> I'm guessing it was installed as a dependency for java. The openjdk-6-jre package depends on libpulse0. However, I think the openjdk-6-jre-headless package exists so dependencies like these aren't installed on a headless server. Try removing openjdk-6-jre and pulse packages.
```

sudo apt-get remove openjdk-6-jre libpulse0 pulseaudio-utils gstreamer0.10-pulseaudio pulseaudio

```

There is Sun JDK not Open JDK.

Afterall the software on the server that uses Sun JDK does not work on Open JDK.

So it seems it is a dependency, then I leave it like that.

Thank you all.

---

