---
title: "Lubuntu updates added 'gnome-session'"
date: 2013-12-05
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-12-05
I actually noticed this the other day:

```
Commit Log for Tue Dec  3 06:00:01 2013


Upgraded the following packages:
cups-filters (1.0.41-0ubuntu1) to 1.0.41-2
gir1.2-soup-2.4 (2.44.1-1) to 2.44.2-1
ifupdown (0.7.46.1ubuntu1) to 0.7.47.1ubuntu1
klibc-utils (2.0.1-3.1ubuntu2) to 2.0.2-1ubuntu1
libcupsfilters1 (1.0.41-0ubuntu1) to 1.0.41-2
libffi6 (3.0.13-9ubuntu1) to 3.0.13-10
libfontembed1 (1.0.41-0ubuntu1) to 1.0.41-2
libklibc (2.0.1-3.1ubuntu2) to 2.0.2-1ubuntu1
liblightdm-gobject-1-0 (1.9.3-0ubuntu1) to 1.9.4-0ubuntu1
libobrender29 (3.5.2-4) to 3.5.2-5
libobt2 (3.5.2-4) to 3.5.2-5
libsoup-gnome2.4-1 (2.44.1-1) to 2.44.2-1
libsoup2.4-1 (2.44.1-1) to 2.44.2-1
lightdm (1.9.3-0ubuntu1) to 1.9.4-0ubuntu1
linux-generic (3.12.0.4.6) to 3.12.0.5.7
linux-headers-generic (3.12.0.4.6) to 3.12.0.5.7
linux-image-generic (3.12.0.4.6) to 3.12.0.5.7
[B]openbox (3.5.2-4) to 3.5.2-5
[/B]
**[COLOR="#FF0000"]Installed the following packages:[/COLOR]**
gnome-desktop3-data (3.8.4-0ubuntu1)
[B]gnome-session (3.9.90-0ubuntu3)
gnome-session-bin (3.9.90-0ubuntu3)
gnome-session-common (3.9.90-0ubuntu3)
gnome-settings-daemon (3.8.6.1-0ubuntu2)[/B]
gstreamer0.10-pulseaudio (0.10.31-3+nmu1ubuntu3)
hwdata (0.249-1)
libgnome-desktop-3-7 (3.8.4-0ubuntu1)
libpulsedsp (1:4.0-0ubuntu6)
libsystemd-journal0 (204-5ubuntu6)
libwacom-common (0.8-1)
libwacom2 (0.8-1)
linux-headers-3.12.0-5 (3.12.0-5.13)
linux-headers-3.12.0-5-generic (3.12.0-5.13)
linux-image-3.12.0-5-generic (3.12.0-5.13)
linux-image-extra-3.12.0-5-generic (3.12.0-5.13)
**openbox-gnome-session (3.5.2-5)**
pulseaudio (1:4.0-0ubuntu6)
pulseaudio-module-x11 (1:4.0-0ubuntu6)
pulseaudio-utils (1:4.0-0ubuntu6)
rtkit (0.10-3)
session-migration (0.2)

```

I thought that seemed odd and I'm going to have to wipe out that install soon so I wanted to record that for posterity in case it's a recurrent thing :)

---

### Post by vasa1 on 2013-12-05
And how come you got pulseaudio? Have you installed some additional software? Or is Lubuntu 14.04 going to have pulseaudio by default?

---

### Post by infectedorganism on 2013-12-05
> **kansasnoob said:**
> I actually noticed this the other day:

```
Commit Log for Tue Dec  3 06:00:01 2013


Upgraded the following packages:
cups-filters (1.0.41-0ubuntu1) to 1.0.41-2
gir1.2-soup-2.4 (2.44.1-1) to 2.44.2-1
ifupdown (0.7.46.1ubuntu1) to 0.7.47.1ubuntu1
klibc-utils (2.0.1-3.1ubuntu2) to 2.0.2-1ubuntu1
libcupsfilters1 (1.0.41-0ubuntu1) to 1.0.41-2
libffi6 (3.0.13-9ubuntu1) to 3.0.13-10
libfontembed1 (1.0.41-0ubuntu1) to 1.0.41-2
libklibc (2.0.1-3.1ubuntu2) to 2.0.2-1ubuntu1
liblightdm-gobject-1-0 (1.9.3-0ubuntu1) to 1.9.4-0ubuntu1
libobrender29 (3.5.2-4) to 3.5.2-5
libobt2 (3.5.2-4) to 3.5.2-5
libsoup-gnome2.4-1 (2.44.1-1) to 2.44.2-1
libsoup2.4-1 (2.44.1-1) to 2.44.2-1
lightdm (1.9.3-0ubuntu1) to 1.9.4-0ubuntu1
linux-generic (3.12.0.4.6) to 3.12.0.5.7
linux-headers-generic (3.12.0.4.6) to 3.12.0.5.7
linux-image-generic (3.12.0.4.6) to 3.12.0.5.7
[B]openbox (3.5.2-4) to 3.5.2-5
[/B]
**[COLOR=#FF0000]Installed the following packages:[/COLOR]**
gnome-desktop3-data (3.8.4-0ubuntu1)
[B]gnome-session (3.9.90-0ubuntu3)
gnome-session-bin (3.9.90-0ubuntu3)
gnome-session-common (3.9.90-0ubuntu3)
gnome-settings-daemon (3.8.6.1-0ubuntu2)[/B]
gstreamer0.10-pulseaudio (0.10.31-3+nmu1ubuntu3)
hwdata (0.249-1)
libgnome-desktop-3-7 (3.8.4-0ubuntu1)
libpulsedsp (1:4.0-0ubuntu6)
libsystemd-journal0 (204-5ubuntu6)
libwacom-common (0.8-1)
libwacom2 (0.8-1)
linux-headers-3.12.0-5 (3.12.0-5.13)
linux-headers-3.12.0-5-generic (3.12.0-5.13)
linux-image-3.12.0-5-generic (3.12.0-5.13)
linux-image-extra-3.12.0-5-generic (3.12.0-5.13)
**openbox-gnome-session (3.5.2-5)**
pulseaudio (1:4.0-0ubuntu6)
pulseaudio-module-x11 (1:4.0-0ubuntu6)
pulseaudio-utils (1:4.0-0ubuntu6)
rtkit (0.10-3)
session-migration (0.2)

```

I thought that seemed odd and I'm going to have to wipe out that install soon so I wanted to record that for posterity in case it's a recurrent thing :)

I noticed this too. I kept the openbox update, but purged all the gnome packages that came with that update.

---

### Post by kansasnoob on 2013-12-05
> **vasa1 said:**
> And how come you got pulseaudio? Have you installed some additional software? Or is Lubuntu 14.04 going to have pulseaudio by default?

I had done very little with this, the installation info is:

```
Lubuntu 14.04 "Trusty Tahr" - Alpha i386 (20131129)
```

And apt info:

BURP! PCManFM is a mess right now :(

But there is an old "apt" log;

```
lance@lance-desktop:~$ ls /var/log/apt
history.log  history.log.1.gz  term.log  term.log.1.gz

```

So I'll use the synaptic logs:

```
Commit Log for Sat Nov 30 09:58:24 2013


Upgraded the following packages:
apparmor (2.8.0-0ubuntu34) to 2.8.0-0ubuntu35
foomatic-db-compressed-ppds (20130912-1fakesync1) to 20131129-1
initscripts (2.88dsf-41ubuntu3) to 2.88dsf-41ubuntu4
libapparmor-perl (2.8.0-0ubuntu34) to 2.8.0-0ubuntu35
libapparmor1 (2.8.0-0ubuntu34) to 2.8.0-0ubuntu35
libglib2.0-0 (2.39.1-0ubuntu1) to 2.39.1-0ubuntu2
libglib2.0-bin (2.39.1-0ubuntu1) to 2.39.1-0ubuntu2
libglib2.0-data (2.39.1-0ubuntu1) to 2.39.1-0ubuntu2
libgraphite2-3 (1.2.3-1) to 1.2.4-1
libtimedate-perl (1.2000-1) to 2.3000-1
openprinting-ppds (20130912-1fakesync1) to 20131129-1
sysv-rc (2.88dsf-41ubuntu3) to 2.88dsf-41ubuntu4
sysvinit-utils (2.88dsf-41ubuntu3) to 2.88dsf-41ubuntu4

```

```
Commit Log for Sat Nov 30 11:46:33 2013


Completely removed the following packages:
grub-gfxpayload-lists
grub-pc
grub2-common

Installed the following packages:
grub (0.97-29ubuntu66)

```

```
Commit Log for Mon Dec  2 10:21:34 2013


Upgraded the following packages:
libelfg0 (0.8.13-4) to 0.8.13-5
liblwp-protocol-https-perl (6.04-1) to 6.04-2
libnautilus-extension1a (1:3.8.2-0ubuntu3) to 1:3.8.2-0ubuntu4
libnm-gtk-common (0.9.8.0-1ubuntu5) to 0.9.8.0-1ubuntu6
libnm-gtk0 (0.9.8.0-1ubuntu5) to 0.9.8.0-1ubuntu6
libpcap0.8 (1.4.0-2) to 1.5.1-1
libwww-perl (6.05-1) to 6.05-2
nautilus-data (1:3.8.2-0ubuntu3) to 1:3.8.2-0ubuntu4
network-manager-gnome (0.9.8.0-1ubuntu5) to 0.9.8.0-1ubuntu6
xserver-xorg-input-evdev (1:2.7.3-0ubuntu3.1) to 1:2.8.2-1ubuntu1

```

```
Commit Log for Mon Dec  2 17:42:51 2013


Upgraded the following packages:
usb-creator-common (0.2.50) to 0.2.51
usb-creator-gtk (0.2.50) to 0.2.51

```

```
Commit Log for Tue Dec  3 06:00:01 2013


Upgraded the following packages:
cups-filters (1.0.41-0ubuntu1) to 1.0.41-2
gir1.2-soup-2.4 (2.44.1-1) to 2.44.2-1
ifupdown (0.7.46.1ubuntu1) to 0.7.47.1ubuntu1
klibc-utils (2.0.1-3.1ubuntu2) to 2.0.2-1ubuntu1
libcupsfilters1 (1.0.41-0ubuntu1) to 1.0.41-2
libffi6 (3.0.13-9ubuntu1) to 3.0.13-10
libfontembed1 (1.0.41-0ubuntu1) to 1.0.41-2
libklibc (2.0.1-3.1ubuntu2) to 2.0.2-1ubuntu1
liblightdm-gobject-1-0 (1.9.3-0ubuntu1) to 1.9.4-0ubuntu1
libobrender29 (3.5.2-4) to 3.5.2-5
libobt2 (3.5.2-4) to 3.5.2-5
libsoup-gnome2.4-1 (2.44.1-1) to 2.44.2-1
libsoup2.4-1 (2.44.1-1) to 2.44.2-1
lightdm (1.9.3-0ubuntu1) to 1.9.4-0ubuntu1
linux-generic (3.12.0.4.6) to 3.12.0.5.7
linux-headers-generic (3.12.0.4.6) to 3.12.0.5.7
linux-image-generic (3.12.0.4.6) to 3.12.0.5.7
openbox (3.5.2-4) to 3.5.2-5

Installed the following packages:
gnome-desktop3-data (3.8.4-0ubuntu1)
gnome-session (3.9.90-0ubuntu3)
gnome-session-bin (3.9.90-0ubuntu3)
gnome-session-common (3.9.90-0ubuntu3)
gnome-settings-daemon (3.8.6.1-0ubuntu2)
gstreamer0.10-pulseaudio (0.10.31-3+nmu1ubuntu3)
hwdata (0.249-1)
libgnome-desktop-3-7 (3.8.4-0ubuntu1)
libpulsedsp (1:4.0-0ubuntu6)
libsystemd-journal0 (204-5ubuntu6)
libwacom-common (0.8-1)
libwacom2 (0.8-1)
linux-headers-3.12.0-5 (3.12.0-5.13)
linux-headers-3.12.0-5-generic (3.12.0-5.13)
linux-image-3.12.0-5-generic (3.12.0-5.13)
linux-image-extra-3.12.0-5-generic (3.12.0-5.13)
openbox-gnome-session (3.5.2-5)
pulseaudio (1:4.0-0ubuntu6)
pulseaudio-module-x11 (1:4.0-0ubuntu6)
pulseaudio-utils (1:4.0-0ubuntu6)
rtkit (0.10-3)
session-migration (0.2)

```

```
Commit Log for Thu Dec  5 06:01:45 2013


Upgraded the following packages:
bsdutils (1:2.20.1-5.1ubuntu9) to 1:2.20.1-5.1ubuntu10
ghostscript (9.10~dfsg-0ubuntu3) to 9.10~dfsg-0ubuntu4
ghostscript-x (9.10~dfsg-0ubuntu3) to 9.10~dfsg-0ubuntu4
gnome-desktop3-data (3.8.4-0ubuntu1) to 3.8.4-0ubuntu2
gnome-session (3.9.90-0ubuntu3) to 3.9.90-0ubuntu4
gnome-session-bin (3.9.90-0ubuntu3) to 3.9.90-0ubuntu4
gnome-session-common (3.9.90-0ubuntu3) to 3.9.90-0ubuntu4
grub-common (2.00-20) to 2.00-21
grub-pc-bin (2.00-20) to 2.00-21
initramfs-tools (0.103ubuntu2) to 0.103ubuntu3
initramfs-tools-bin (0.103ubuntu2) to 0.103ubuntu3
initscripts (2.88dsf-41ubuntu4) to 2.88dsf-41ubuntu5
kmod (15-0ubuntu2) to 15-0ubuntu5
libaudit-common (1:2.2.2-1ubuntu4) to 1:2.3.2-2ubuntu1
libaudit1 (1:2.2.2-1ubuntu4) to 1:2.3.2-2ubuntu1
libblkid1 (2.20.1-5.1ubuntu9) to 2.20.1-5.1ubuntu10
libbsd0 (0.6.0-1) to 0.6.0-1ubuntu1
libestr0 (0.1.9-0ubuntu1) to 0.1.9-0ubuntu2
libexif12 (0.6.21-1) to 0.6.21-1ubuntu1
libexpat1 (2.1.0-4) to 2.1.0-4ubuntu1
libgmp10 (2:5.1.2+dfsg-2ubuntu1) to 2:5.1.2+dfsg-3ubuntu2
libgnome-desktop-3-7 (3.8.4-0ubuntu1) to 3.8.4-0ubuntu2
libgnutls-openssl27 (2.12.23-1ubuntu4) to 2.12.23-1ubuntu5
libgnutls26 (2.12.23-1ubuntu4) to 2.12.23-1ubuntu5
libgpg-error0 (1.12-0.2) to 1.12-0.2ubuntu1
libgs9 (9.10~dfsg-0ubuntu3) to 9.10~dfsg-0ubuntu4
libgs9-common (9.10~dfsg-0ubuntu3) to 9.10~dfsg-0ubuntu4
libidn11 (1.28-1ubuntu1) to 1.28-1ubuntu2
libkmod2 (15-0ubuntu2) to 15-0ubuntu5
liblightdm-gobject-1-0 (1.9.4-0ubuntu1) to 1.9.5-0ubuntu1
libmount1 (2.20.1-5.1ubuntu9) to 2.20.1-5.1ubuntu10
libpcre3 (1:8.31-2) to 1:8.31-2ubuntu2
libpipeline1 (1.2.4-1) to 1.2.5-1
libplymouth2 (0.8.8-0ubuntu10) to 0.8.8-0ubuntu11
libpoppler-glib8 (0.24.3-0ubuntu1) to 0.24.3-0ubuntu3
libpoppler43 (0.24.3-0ubuntu1) to 0.24.3-0ubuntu3
libpopt0 (1.16-8) to 1.16-8ubuntu1
libraw1394-11 (2.1.0-1) to 2.1.0-1ubuntu1
libselinux1 (2.2.1-1ubuntu1) to 2.2.1-1ubuntu2
libssl1.0.0 (1.0.1e-3ubuntu1) to 1.0.1e-4ubuntu2
libtasn1-3 (2.14-3) to 2.14-3ubuntu1
libtelepathy-glib0 (0.22.0-1) to 0.22.0-1ubuntu2
libusb-0.1-4 (2:0.1.12-23.3) to 2:0.1.12-23.3ubuntu1
libuuid1 (2.20.1-5.1ubuntu9) to 2.20.1-5.1ubuntu10
libx11-6 (2:1.6.2-1ubuntu1) to 2:1.6.2-1ubuntu2
libx11-data (2:1.6.2-1ubuntu1) to 2:1.6.2-1ubuntu2
libx11-xcb1 (2:1.6.2-1ubuntu1) to 2:1.6.2-1ubuntu2
libxcb-dri2-0 (1.9.1-3ubuntu1) to 1.9.1-3.1ubuntu1
libxcb-glx0 (1.9.1-3ubuntu1) to 1.9.1-3.1ubuntu1
libxcb-render0 (1.9.1-3ubuntu1) to 1.9.1-3.1ubuntu1
libxcb-shape0 (1.9.1-3ubuntu1) to 1.9.1-3.1ubuntu1
libxcb-shm0 (1.9.1-3ubuntu1) to 1.9.1-3.1ubuntu1
libxcb-xfixes0 (1.9.1-3ubuntu1) to 1.9.1-3.1ubuntu1
libxcb1 (1.9.1-3ubuntu1) to 1.9.1-3.1ubuntu1
lightdm (1.9.4-0ubuntu1) to 1.9.5-0ubuntu1
memtest86+ (4.20-1.1ubuntu5) to 4.20-1.1ubuntu6
module-init-tools (15-0ubuntu2) to 15-0ubuntu5
mount (2.20.1-5.1ubuntu9) to 2.20.1-5.1ubuntu10
obconf (1:2.0.4+git20130908-1) to 1:2.0.4+git20130908-2
openssl (1.0.1e-3ubuntu1) to 1.0.1e-4ubuntu2
plymouth (0.8.8-0ubuntu10) to 0.8.8-0ubuntu11
plymouth-label (0.8.8-0ubuntu10) to 0.8.8-0ubuntu11
plymouth-theme-ubuntu-text (0.8.8-0ubuntu10) to 0.8.8-0ubuntu11
poppler-utils (0.24.3-0ubuntu1) to 0.24.3-0ubuntu3
python3-software-properties (0.92.28) to 0.92.29
rsyslog (7.4.4-1ubuntu1) to 7.4.4-1ubuntu2
software-properties-common (0.92.28) to 0.92.29
software-properties-gtk (0.92.28) to 0.92.29
sysv-rc (2.88dsf-41ubuntu4) to 2.88dsf-41ubuntu5
sysvinit-utils (2.88dsf-41ubuntu4) to 2.88dsf-41ubuntu5
ubuntu-drivers-common (1:0.2.84) to 1:0.2.87
util-linux (2.20.1-5.1ubuntu9) to 2.20.1-5.1ubuntu10
uuid-runtime (2.20.1-5.1ubuntu9) to 2.20.1-5.1ubuntu10
xserver-common (2:1.14.3-5ubuntu1) to 2:1.14.4-1ubuntu1
xserver-xorg-core (2:1.14.3-5ubuntu1) to 2:1.14.4-1ubuntu1
xserver-xorg-video-modesetting (0.8.0-1) to 0.8.1-1

Installed the following packages:
python3-pycurl (7.19.0-5ubuntu8)

```

That's a full history because I do use synaptic as my work-horse during dev :)

---

### Post by zika on 2013-12-05
This doesn't look to me (or I was not thorough enough in roaming thorough these lists) as a complete history...
Grub2 was purged, replaced with grub then suddenly grub2 is being upgraded... I'm stymied as TeX would say...

---

### Post by kansasnoob on 2013-12-05
> **zika said:**
> This doesn't look to me (or I was not thorough enough in roaming thorough these lists) as a complete history...
Grub2 was purged, replaced with grub then suddenly grub2 is being upgraded... I'm stymied as TeX would say...

I switch to grub from grub2 in my complex multi-boots because of this:

[http://ubuntuforums.org/showthread.php?t=2101763](http://ubuntuforums.org/showthread.php?t=2101763)

So not all grub-pc packages and files are purged, just those needed to make a functioning multi-boot with minimal effort :)

---

### Post by zika on 2013-12-05
I'm obviously missing something about grub(2) but its late and it is not important since You're happy with Your config so...
Read You next morning, or better to say noon, after some proper work done.

---

### Post by kansasnoob on 2013-12-05
From a lateral install of Ubuntu 12.04 I can post the full logs, history:

```
Start-Date: 2013-12-03  06:01:13
Commandline: /usr/sbin/synaptic
Install: openbox-gnome-session:i386 (3.5.2-5, automatic), pulseaudio:i386 (4.0-0ubuntu6, automatic), gstreamer0.10-pulseaudio:i386 (0.10.31-3+nmu1ubuntu3, automatic), hwdata:i386 (0.249-1, automatic), gnome-session-common:i386 (3.9.90-0ubuntu3, automatic), linux-image-extra-3.12.0-5-generic:i386 (3.12.0-5.13, automatic), linux-image-3.12.0-5-generic:i386 (3.12.0-5.13, automatic), gnome-settings-daemon:i386 (3.8.6.1-0ubuntu2, automatic), gnome-session-bin:i386 (3.9.90-0ubuntu3, automatic), session-migration:i386 (0.2, automatic), rtkit:i386 (0.10-3, automatic), linux-headers-3.12.0-5:i386 (3.12.0-5.13, automatic), libpulsedsp:i386 (4.0-0ubuntu6, automatic), libgnome-desktop-3-7:i386 (3.8.4-0ubuntu1, automatic), gnome-session:i386 (3.9.90-0ubuntu3, automatic), libwacom2:i386 (0.8-1, automatic), libwacom-common:i386 (0.8-1, automatic), libsystemd-journal0:i386 (204-5ubuntu6, automatic), pulseaudio-module-x11:i386 (4.0-0ubuntu6, automatic), linux-headers-3.12.0-5-generic:i386 (3.12.0-5.13, automatic), gnome-desktop3-data:i386 (3.8.4-0ubuntu1, automatic), pulseaudio-utils:i386 (4.0-0ubuntu6, automatic)
Upgrade: libfontembed1:i386 (1.0.41-0ubuntu1, 1.0.41-2), gir1.2-soup-2.4:i386 (2.44.1-1, 2.44.2-1), libcupsfilters1:i386 (1.0.41-0ubuntu1, 1.0.41-2), libklibc:i386 (2.0.1-3.1ubuntu2, 2.0.2-1ubuntu1), lightdm:i386 (1.9.3-0ubuntu1, 1.9.4-0ubuntu1), liblightdm-gobject-1-0:i386 (1.9.3-0ubuntu1, 1.9.4-0ubuntu1), libsoup2.4-1:i386 (2.44.1-1, 2.44.2-1), libobrender29:i386 (3.5.2-4, 3.5.2-5), libsoup-gnome2.4-1:i386 (2.44.1-1, 2.44.2-1), cups-filters:i386 (1.0.41-0ubuntu1, 1.0.41-2), libobt2:i386 (3.5.2-4, 3.5.2-5), libffi6:i386 (3.0.13-9ubuntu1, 3.0.13-10), linux-generic:i386 (3.12.0.4.6, 3.12.0.5.7), linux-image-generic:i386 (3.12.0.4.6, 3.12.0.5.7), linux-headers-generic:i386 (3.12.0.4.6, 3.12.0.5.7), openbox:i386 (3.5.2-4, 3.5.2-5), ifupdown:i386 (0.7.46.1ubuntu1, 0.7.47.1ubuntu1), klibc-utils:i386 (2.0.1-3.1ubuntu2, 2.0.2-1ubuntu1)
End-Date: 2013-12-03  06:04:16

Start-Date: 2013-12-05  06:02:21
Commandline: /usr/sbin/synaptic
Install: python3-pycurl:i386 (7.19.0-5ubuntu8, automatic)
Upgrade: bsdutils:i386 (2.20.1-5.1ubuntu9, 2.20.1-5.1ubuntu10), libpoppler-glib8:i386 (0.24.3-0ubuntu1, 0.24.3-0ubuntu3), libx11-xcb1:i386 (1.6.2-1ubuntu1, 1.6.2-1ubuntu2), libselinux1:i386 (2.2.1-1ubuntu1, 2.2.1-1ubuntu2), kmod:i386 (15-0ubuntu2, 15-0ubuntu5), libraw1394-11:i386 (2.1.0-1, 2.1.0-1ubuntu1), initscripts:i386 (2.88dsf-41ubuntu4, 2.88dsf-41ubuntu5), ghostscript:i386 (9.10~dfsg-0ubuntu3, 9.10~dfsg-0ubuntu4), libgmp10:i386 (5.1.2+dfsg-2ubuntu1, 5.1.2+dfsg-3ubuntu2), libaudit-common:i386 (2.2.2-1ubuntu4, 2.3.2-2ubuntu1), libxcb-render0:i386 (1.9.1-3ubuntu1, 1.9.1-3.1ubuntu1), initramfs-tools:i386 (0.103ubuntu2, 0.103ubuntu3), libxcb-glx0:i386 (1.9.1-3ubuntu1, 1.9.1-3.1ubuntu1), libx11-data:i386 (1.6.2-1ubuntu1, 1.6.2-1ubuntu2), software-properties-gtk:i386 (0.92.28, 0.92.29), libxcb-xfixes0:i386 (1.9.1-3ubuntu1, 1.9.1-3.1ubuntu1), libxcb-shape0:i386 (1.9.1-3ubuntu1, 1.9.1-3.1ubuntu1), libexif12:i386 (0.6.21-1, 0.6.21-1ubuntu1), libmount1:i386 (2.20.1-5.1ubuntu9, 2.20.1-5.1ubuntu10), rsyslog:i386 (7.4.4-1ubuntu1, 7.4.4-1ubuntu2), libblkid1:i386 (2.20.1-5.1ubuntu9, 2.20.1-5.1ubuntu10), xserver-xorg-core:i386 (1.14.3-5ubuntu1, 1.14.4-1ubuntu1), gnome-session-common:i386 (3.9.90-0ubuntu3, 3.9.90-0ubuntu4), python3-software-properties:i386 (0.92.28, 0.92.29), ubuntu-drivers-common:i386 (0.2.84, 0.2.87), grub-common:i386 (2.00-20, 2.00-21), libxcb-shm0:i386 (1.9.1-3ubuntu1, 1.9.1-3.1ubuntu1), sysv-rc:i386 (2.88dsf-41ubuntu4, 2.88dsf-41ubuntu5), libusb-0.1-4:i386 (0.1.12-23.3, 0.1.12-23.3ubuntu1), mount:i386 (2.20.1-5.1ubuntu9, 2.20.1-5.1ubuntu10), lightdm:i386 (1.9.4-0ubuntu1, 1.9.5-0ubuntu1), gnome-session-bin:i386 (3.9.90-0ubuntu3, 3.9.90-0ubuntu4), liblightdm-gobject-1-0:i386 (1.9.4-0ubuntu1, 1.9.5-0ubuntu1), libbsd0:i386 (0.6.0-1, 0.6.0-1ubuntu1), xserver-common:i386 (1.14.3-5ubuntu1, 1.14.4-1ubuntu1), libpcre3:i386 (8.31-2, 8.31-2ubuntu2), libx11-6:i386 (1.6.2-1ubuntu1, 1.6.2-1ubuntu2), xserver-xorg-video-modesetting:i386 (0.8.0-1, 0.8.1-1), util-linux:i386 (2.20.1-5.1ubuntu9, 2.20.1-5.1ubuntu10), uuid-runtime:i386 (2.20.1-5.1ubuntu9, 2.20.1-5.1ubuntu10), libxcb-dri2-0:i386 (1.9.1-3ubuntu1, 1.9.1-3.1ubuntu1), libgs9:i386 (9.10~dfsg-0ubuntu3, 9.10~dfsg-0ubuntu4), libestr0:i386 (0.1.9-0ubuntu1, 0.1.9-0ubuntu2), openssl:i386 (1.0.1e-3ubuntu1, 1.0.1e-4ubuntu2), plymouth:i386 (0.8.8-0ubuntu10, 0.8.8-0ubuntu11), libgnome-desktop-3-7:i386 (3.8.4-0ubuntu1, 3.8.4-0ubuntu2), libgnutls26:i386 (2.12.23-1ubuntu4, 2.12.23-1ubuntu5), gnome-session:i386 (3.9.90-0ubuntu3, 3.9.90-0ubuntu4), grub-pc-bin:i386 (2.00-20, 2.00-21), plymouth-label:i386 (0.8.8-0ubuntu10, 0.8.8-0ubuntu11), libexpat1:i386 (2.1.0-4, 2.1.0-4ubuntu1), libgs9-common:i386 (9.10~dfsg-0ubuntu3, 9.10~dfsg-0ubuntu4), obconf:i386 (2.0.4+git20130908-1, 2.0.4+git20130908-2), poppler-utils:i386 (0.24.3-0ubuntu1, 0.24.3-0ubuntu3), libgpg-error0:i386 (1.12-0.2, 1.12-0.2ubuntu1), libpopt0:i386 (1.16-8, 1.16-8ubuntu1), libtelepathy-glib0:i386 (0.22.0-1, 0.22.0-1ubuntu2), memtest86+:i386 (4.20-1.1ubuntu5, 4.20-1.1ubuntu6), plymouth-theme-ubuntu-text:i386 (0.8.8-0ubuntu10, 0.8.8-0ubuntu11), sysvinit-utils:i386 (2.88dsf-41ubuntu4, 2.88dsf-41ubuntu5), initramfs-tools-bin:i386 (0.103ubuntu2, 0.103ubuntu3), libpoppler43:i386 (0.24.3-0ubuntu1, 0.24.3-0ubuntu3), libgnutls-openssl27:i386 (2.12.23-1ubuntu4, 2.12.23-1ubuntu5), software-properties-common:i386 (0.92.28, 0.92.29), libtasn1-3:i386 (2.14-3, 2.14-3ubuntu1), libxcb1:i386 (1.9.1-3ubuntu1, 1.9.1-3.1ubuntu1), libpipeline1:i386 (1.2.4-1, 1.2.5-1), libidn11:i386 (1.28-1ubuntu1, 1.28-1ubuntu2), gnome-desktop3-data:i386 (3.8.4-0ubuntu1, 3.8.4-0ubuntu2), libuuid1:i386 (2.20.1-5.1ubuntu9, 2.20.1-5.1ubuntu10), ghostscript-x:i386 (9.10~dfsg-0ubuntu3, 9.10~dfsg-0ubuntu4), libssl1.0.0:i386 (1.0.1e-3ubuntu1, 1.0.1e-4ubuntu2), libaudit1:i386 (2.2.2-1ubuntu4, 2.3.2-2ubuntu1), libkmod2:i386 (15-0ubuntu2, 15-0ubuntu5), libplymouth2:i386 (0.8.8-0ubuntu10, 0.8.8-0ubuntu11), module-init-tools:i386 (15-0ubuntu2, 15-0ubuntu5)
End-Date: 2013-12-05  06:06:04
```

Archived history.1:

```
Start-Date: 2013-11-29  16:44:32
Commandline: apt-get --yes --no-install-recommends install linux-generic adduser apt apt-utils base-files base-passwd bash bsdutils busybox-initramfs bzip2 console-setup coreutils cpio cron dash debconf debconf-i18n debianutils dh-python diffutils dmsetup dpkg e2fslibs e2fsprogs eject file findutils gcc-4.8-base gnupg gpgv grep gzip hostname ifupdown init-system-helpers initramfs-tools initramfs-tools-bin initscripts insserv iproute2 iputils-ping isc-dhcp-client isc-dhcp-common kbd keyboard-configuration klibc-utils kmod less libacl1 libapt-inst1.5 libapt-pkg4.12 libarchive-extract-perl libattr1 libaudit-common libaudit1 libblkid1 libbsd0 libbz2-1.0 libc-bin libc6 libcap2 libcomerr2 libdb5.3 libdbus-1-3 libdevmapper1.02.1 libdrm2 libestr0 libexpat1 libffi6 libfribidi0 libgcc1 libgcrypt11 libgdbm3 libgnutls-openssl27 libgnutls26 libgpg-error0 libjson-c2 libjson0 libklibc libkmod2 liblocale-gettext-perl liblockfile-bin liblockfile1 liblog-message-simple-perl liblzma5 libmagic1 libmodule-pluggable-perl libmount1 libncurses5 libncursesw5 libnewt0.52 libnih-dbus1 libnih1 libp11-kit0 libpam-modules libpam-modules-bin libpam-runtime libpam0g libpcre3 libplymouth2 libpng12-0 libpod-latex-perl libpopt0 libprocps1 libpython3-stdlib libpython3.3-minimal libpython3.3-stdlib libreadline6 libselinux1 libsemanage-common libsemanage1 libsepol1 libslang2 libsqlite3-0 libss2 libssl1.0.0 libstdc++6 libtasn1-3 libterm-ui-perl libtext-charwidth-perl libtext-iconv-perl libtext-soundex-perl libtext-wrapi18n-perl libtinfo5 libudev1 libusb-0.1-4 libustr-1.0-1 libuuid1 locales lockfile-progs login logrotate lsb-base lsb-release makedev mawk mime-support module-init-tools mount mountall multiarch-support ncurses-base ncurses-bin net-tools netbase netcat-openbsd ntpdate passwd perl perl-base perl-modules plymouth procps python3 python3-minimal python3.3 python3.3-minimal readline-common resolvconf rsyslog sed sensible-utils sudo sysv-rc sysvinit-utils tar tzdata ubuntu-keyring ubuntu-minimal ucf udev upstart ureadahead util-linux vim-common vim-tiny whiptail xkb-data zlib1g accountsservice apparmor apt-transport-https bash-completion bind9-host bsdmainutils busybox-static ca-certificates command-not-found command-not-found-data dbus dmidecode dnsutils dosfstools ed friendly-recovery ftp fuse geoip-database gettext-base gir1.2-glib-2.0 groff-base hdparm info install-info iptables iputils-tracepath irqbalance iso-codes krb5-locales language-selector-common libaccountsservice0 libapparmor-perl libapparmor1 libasn1-8-heimdal libasprintf0c2 libbind9-90 libcap-ng0 libcurl3-gnutls libdbus-glib-1-2 libdns99 libedit2 libelf1 libfuse2 libgck-1-0 libgcr-3-common libgcr-base-3-1 libgeoip1 libgirepository-1.0-1 libglib2.0-0 libglib2.0-data libgssapi-krb5-2 libgssapi3-heimdal libhcrypto4-heimdal libheimbase1-heimdal libheimntlm0-heimdal libhx509-5-heimdal libidn11 libisc95 libisccc90 libisccfg90 libk5crypto3 libkeyutils1 libkrb5-26-heimdal libkrb5-3 libkrb5support0 libldap-2.4-2 liblwres90 libnfnetlink0 libnuma1 libpam-systemd libparted0debian1 libpcap0.8 libpci3 libpipeline1 libpolkit-gobject-1-0 libroken18-heimdal librtmp0 libsasl2-2 libsasl2-modules libsasl2-modules-db libsystemd-daemon0 libsystemd-login0 libusb-1.0-0 libwind0-heimdal libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 libxext6 libxml2 libxmuu1 libxtables10 lshw lsof ltrace man-db manpages memtest86+ mlocate mtr-tiny nano ntfs-3g openssh-client openssl parted pciutils plymouth-theme-ubuntu-text popularity-contest powermgmt-base ppp pppconfig pppoeconf psmisc python-apt-common python3-apt python3-commandnotfound python3-dbus python3-distupgrade python3-gdbm python3-gi python3-update-manager rsync sgml-base shared-mime-info strace systemd-services systemd-shim tcpdump telnet time ubuntu-release-upgrader-core ubuntu-standard ufw update-manager-core usbutils uuid-runtime wget xauth xml-core app-install-data apport-gtk aptdaemon-data apturl apturl-common aspell aspell-en at-spi2-core cups-driver-gutenprint dconf-cli desktop-file-utils dictionaries-common dmz-cursor-theme dnsmasq-base evince evince-common evolution-data-server-common file-roller firefox fonts-liberation fonts-nanum gconf-service gconf-service-backend gconf2 gconf2-common gcr gdebi-core gir1.2-atk-1.0 gir1.2-dbusmenu-glib-0.4 gir1.2-dee-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-gtk-3.0 gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-notify-0.7 gir1.2-pango-1.0 gir1.2-soup-2.4 gir1.2-unity-5.0 gir1.2-vte-2.90 gir1.2-webkit-3.0 gir1.2-wnck-3.0 glib-networking glib-networking-common glib-networking-services gnome-accessibility-themes gnome-disk-utility gnome-keyring gsettings-desktop-schemas gstreamer0.10-nice gstreamer0.10-plugins-base gstreamer0.10-plugins-good gucharmap gvfs gvfs-backends gvfs-common gvfs-daemons gvfs-fuse gvfs-libs ibus im-config indicator-application iputils-arping language-selector-gnome libaa1 libappindicator3-1 libaspell15 libassuan0 libasyncns0 libatasmart4 libavc1394-0 libbluetooth3 libburn4 libcaca0 libcairo-perl libcamel-1.2-45 libcanberra-gtk3-0 libcanberra0 libcap2-bin libcdio-cdda1 libcdio-paranoia1 libcdio13 libcdparanoia0 libclutter-1.0-0 libclutter-gtk-1.0-0 libcogl-pango12 libcogl12 libcrack2 libcurl3 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdee-1.0-4 libdevmapper-event1.02.1 libdiscid0 libdjvulibre-text libdjvulibre21 libdv4 libebook-contacts-1.2-0 libedataserver-1.2-18 libenca0 libenchant1c2a libencode-locale-perl libept1.4.12 libevdocument3-4 libevent-2.0-5 libevview3-3 libfarstream-0.1-0 libfile-listing-perl libflac8 libframe6 libgail-3-0 libgconf-2-4 libgcr-ui-3-1 libgeis1 libgeoclue0 libglib-perl libgnome-bluetooth11 libgnome-keyring-common libgnome-keyring0 libgpgme11 libgpm2 libgpod4 libgrail6 libgrip0 libgsf-1-114 libgsf-1-common libgsm1 libgssdp-1.0-3 libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base1.0-0 libgstreamer0.10-0 libgstreamer1.0-0 libgtk2-perl libgtkspell0 libgtop2-7 libgtop2-common libgucharmap-2-90-7 libgupnp-1.0-4 libgupnp-igd-1.0-4 libgxps2 libharfbuzz-icu0 libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhunspell-1.3-0 libibus-1.0-5 libical1 libicu48 libiec61883-0 libimobiledevice4 libindicator3-7 libindicator7 libio-html-perl libisofs6 libjack-jackd2-0 libjavascriptcoregtk-3.0-0 libjs-jquery libjson-glib-1.0-0 libjson-glib-1.0-common libjte1 libkpathsea6 liblircclient0 liblua5.2-0 liblvm2app2.2 liblwp-mediatypes-perl liblwp-protocol-https-perl libmeanwhile1 libmhash2 libminiupnpc8 libmng1 libmnl0 libmtp-common libmtp-runtime libmtp9 libnatpmp1 libnautilus-extension1a libneon27-gnutls libnet-http-perl libnetfilter-conntrack3 libnice10 libnl-route-3-200 libnm-glib-vpn1 libnm-glib4 libnm-gtk-common libnm-gtk0 libnm-util2 libnotify4 libnspr4 libnss3 libogg0 libopenobex1 libopts25 libopus0 liborc-0.4-0 libpango-perl libpisock9 libplist1 libpoppler-glib8 libportaudio2 libproxy1 libpulse-mainloop-glib0 libpulse0 libpurple0 libpwquality-common libpwquality1 libquadmath0 libquvi-scripts libquvi7 libraptor2-0 librasqal3 libraw1394-11 librdf0 libschroedinger-1.0-0 libsdl1.2debian libsecret-1-0 libsecret-common libsgutils2-2 libshout3 libsndfile1 libsoup-gnome2.4-1 libsoup2.4-1 libspectre1 libspeex1 libt1-5 libtag1-vanilla libtag1c2a libtelepathy-glib0 libtheora0 libtidy-0.99-0 libudisks2-0 libuniconf4.6 libunity-protocol-private0 libunity-scopes-json-def-desktop libunity9 libupower-glib1 libusbmuxd2 libva1 libvdpau1 libvisual-0.4-0 libvorbis0a libvorbisenc2 libvorbisfile3 libvte-2.90-9 libvte-2.90-common libvte-common libvte9 libwavpack1 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwebp4 libwhoopsie0 libwmf0.2-7 libwnck-3-0 libwnck-3-common libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwvstreams4.6-base libwvstreams4.6-extras libwww-perl libwww-robotrules-perl libxapian22 libxml-parser-perl libxslt1.1 libxss1 libyajl2 libzephyr4 mobile-broadband-provider-info modemmanager mtools nautilus-data network-manager network-manager-gnome ntp obex-data-server p11-kit pidgin pidgin-data pm-utils python-apt python-aptdaemon python-aptdaemon.gtk3widgets python-cairo python-chardet python-cups python-cupshelpers python-debian python-defer python-gnomekeyring python-gobject python-gtk2 python-libxml2 python-notify python-pkg-resources python-pycurl python-six python-smbc python-xdg python3-aptdaemon.gtk3widgets python3-chardet python3-debian python3-six python3-software-properties simple-scan software-properties-common software-properties-gtk sound-theme-freedesktop syslinux syslinux-common syslinux-legacy system-config-printer-common system-config-printer-gnome transmission-common transmission-gtk ttf-wqy-microhei ubuntu-release-upgrader-gtk udisks udisks2 unattended-upgrades update-manager update-notifier update-notifier-common upower usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd whoopsie wvdial xdg-user-dirs xdg-user-dirs-gtk xdg-utils xul-ext-ubufox zenity zenity-common zram-config abiword abiword-common ace-of-penguins audacious audacious-plugins audacious-plugins-data blueman ffmpegthumbnailer galculator gdebi gecko-mediaplayer giblib1 gksu gnome-mplayer gnome-system-tools gnome-time-admin gnumeric gnumeric-common gpicview guvcview hardinfo indicator-application-gtk2 leafpad liba52-0.7.4 libabiword-3.0 libass4 libaudclient2 libaudcore1 libavcodec54 libavformat54 libavresample1 libavutil52 libbinio1ldbl libbluray1 libbs2b0 libcddb2 libchamplain-0.12-0 libchamplain-gtk-0.12-0 libcompfaceg1 libcue1 libdca0 libdirectfb-1.2-9 libdvdnav4 libdvdread4 libexo-1-0 libexo-common libexo-helpers libfaad2 libffmpegthumbnailer4 libfluidsynth1 libgda-5.0-4 libgda-5.0-common libgksu2-0 libgmlib1 libgmtk1 libgmtk1-data libgoffice-0.10-10 libgoffice-0.10-10-common libguess1 libloudmouth1-0 libmad0 libmms0 libmodplug1 libmowgli2 libmp3lame0 libmpg123-0 libmusicbrainz3-6 libnet-dbus-perl libonig2 liboobs-1-5 libopenjpeg2 libots0 libpostproc52 libswscale2 libts-0.0-0 libwv-1.2-4 libx264-123 libxfce4ui-1-0 libxfce4util-common libxfce4util6 libxfconf-0-2 libxml-twig-perl libxvidcore4 light-locker lubuntu-core lubuntu-default-session lubuntu-desktop lubuntu-software-center lxappearance lxappearance-obconf lxinput lxlauncher lxpanel-indicator-applet-plugin lxrandr lxsession-default-apps lxshortcut lxtask lxterminal mplayer2 mtpaint obconf python-gudev python-pysqlite2 scrot sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins synaptic system-tools-backends transmission tsconf xfburn xfce-keyboard-shortcuts xfce4-notifyd xfce4-power-manager xfce4-power-manager-data xfconf xpad
Install: busybox-static:i386 (1.21.0-1ubuntu1), libdatrie1:i386 (0.2.7.1-1, automatic), gir1.2-notify-0.7:i386 (0.7.6-1ubuntu1), lubuntu-software-center:i386 (0.0.8-0ubuntu1), libgssapi-krb5-2:i386 (1.11.3+dfsg-3ubuntu2), libsystemd-daemon0:i386 (204-5ubuntu6), gconf-service:i386 (3.2.6-0ubuntu1), libfm-gtk-data:i386 (1.1.2.2-1, automatic), nautilus-data:i386 (3.8.2-0ubuntu3), command-not-found-data:i386 (0.3ubuntu8), libfontconfig1:i386 (2.11.0-0ubuntu2, automatic), libx264-123:i386 (0.123.2189+git35cf912-1ubuntu3), libvisual-0.4-0:i386 (0.4.0-5), python-gtk2:i386 (2.24.0-3ubuntu1), python-pkg-resources:i386 (0.6.49-2ubuntu1), libffmpegthumbnailer4:i386 (2.0.8-1), libsgutils2-2:i386 (1.36-1), libglib2.0-data:i386 (2.39.1-0ubuntu1), libpoppler-glib8:i386 (0.24.3-0ubuntu1), xz-utils:i386 (5.1.1alpha+20120614-2ubuntu1, automatic), cups-driver-gutenprint:i386 (5.2.9-1ubuntu2), libapparmor1:i386 (2.8.0-0ubuntu34), consolekit:i386 (0.4.5-3.1ubuntu2, automatic), libfontembed1:i386 (1.0.41-0ubuntu1, automatic), libx11-xcb1:i386 (1.6.2-1ubuntu1, automatic), libflac8:i386 (1.3.0-2), light-locker:i386 (1.0.0-0ubuntu1), network-manager:i386 (0.9.8.4-0ubuntu3), manpages:i386 (3.54-1ubuntu1), libcap-ng0:i386 (0.7.3-1ubuntu1), liblcms1:i386 (1.19.dfsg-1.2ubuntu3, automatic), libgnome-bluetooth11:i386 (3.8.1-2ubuntu2), libpython2.7-minimal:i386 (2.7.6-2ubuntu1, automatic), xserver-xorg-input-synaptics:i386 (1.7.1-0ubuntu1, automatic), abiword-common:i386 (3.0.0-1), libmpfr4:i386 (3.1.2-1, automatic), ed:i386 (1.9-2), python-debian:i386 (0.1.21+nmu2ubuntu1), xserver-xorg-video-tdfx:i386 (1.4.5-1, automatic), libopts25:i386 (5.18-2ubuntu1), libsm6:i386 (1.2.1-2, automatic), python3-commandnotfound:i386 (0.3ubuntu8), nano:i386 (2.2.6-1ubuntu1), libgdk-pixbuf2.0-0:i386 (2.30.1-0ubuntu2, automatic), python3-debian:i386 (0.1.21+nmu2ubuntu1), libcdio-paranoia1:i386 (0.83-4.1), libpurple0:i386 (2.10.7-0ubuntu4.2), libraw1394-11:i386 (2.1.0-1), libxml-parser-perl:i386 (2.41-1build3), hardinfo:i386 (0.5.1-1.2ubuntu1), lxsession-default-apps:i386 (0.4.9.2-0ubuntu6), libgoffice-0.10-10:i386 (0.10.8-1), libgstreamer0.10-0:i386 (0.10.36-1.2ubuntu1), libxkbfile1:i386 (1.0.8-1, automatic), xserver-xorg-video-vmware:i386 (13.0.1-0ubuntu2, automatic), libwvstreams4.6-base:i386 (4.6.1-7), python-aptdaemon.gtk3widgets:i386 (1.1.1-1ubuntu1), python3-six:i386 (1.4.1-1), linux-firmware:i386 (1.117, automatic), libkrb5-3:i386 (1.11.3+dfsg-3ubuntu2), liblua5.2-0:i386 (5.2.2-3), bash-completion:i386 (2.0-1ubuntu3), libjasper1:i386 (1.900.1-14, automatic), libdaemon0:i386 (0.14-2build1, automatic), libsasl2-2:i386 (2.1.25.dfsg1-17build1), libsndfile1:i386 (1.0.25-7ubuntu1), dnsmasq-base:i386 (2.67-1), libjs-jquery:i386 (1.7.2+dfsg-2ubuntu1), tsconf:i386 (1.0-11), libdns99:i386 (9.9.3.dfsg.P2-4ubuntu1), libxss1:i386 (1.2.2-1), libportaudio2:i386 (19+svn20111121-2), libwps-0.2-2:i386 (0.2.9-2), libkpathsea6:i386 (2013.20130729.30972-2), lxsession:i386 (0.4.9.2-0ubuntu6, automatic), libassuan0:i386 (2.1.1-1), liblwp-mediatypes-perl:i386 (6.02-1), libnettle4:i386 (2.7.1-1, automatic), gir1.2-wnck-3.0:i386 (3.4.7-0ubuntu2), xdg-user-dirs-gtk:i386 (0.10-1ubuntu1), krb5-locales:i386 (1.11.3+dfsg-3ubuntu2), galculator:i386 (2.1.2-1), ppp:i386 (2.4.5-5.1ubuntu2), friendly-recovery:i386 (0.2.25), libgnome-keyring-common:i386 (3.8.0-2), libv4l-0:i386 (1.0.0-1, automatic), ghostscript:i386 (9.10~dfsg-0ubuntu3, automatic), libharfbuzz0a:i386 (0.9.19-1, automatic), libcroco3:i386 (0.6.8-2, automatic), libck-connector0:i386 (0.4.5-3.1ubuntu2, automatic), dconf-service:i386 (0.18.0-1, automatic), update-notifier:i386 (0.148), libk5crypto3:i386 (1.11.3+dfsg-3ubuntu2), libgstreamer-plugins-base1.0-0:i386 (1.2.1-2ubuntu1), python2.7:i386 (2.7.6-2ubuntu1, automatic), libcupsmime1:i386 (1.7.0-0ubuntu2, automatic), python-pycurl:i386 (7.19.0-5ubuntu8), modemmanager:i386 (0.6.0.0.really-0ubuntu7), wvdial:i386 (1.61-4.1), libgucharmap-2-90-7:i386 (3.8.2-3), libmtp9:i386 (1.1.6-20-g1b9f164-1ubuntu2), libdconf1:i386 (0.18.0-1, automatic), libfluidsynth1:i386 (1.1.6-2), libxp6:i386 (1.0.2-1), libsdl1.2debian:i386 (1.2.15-5ubuntu2), lxsession-logout:i386 (0.4.9.2-0ubuntu6, automatic), libhttp-message-perl:i386 (6.06-1), dbus-x11:i386 (1.6.18-0ubuntu2, automatic), libnm-glib4:i386 (0.9.8.4-0ubuntu3), libldb1:i386 (1.1.16-1, automatic), libmng1:i386 (1.0.10-3build1), libxml2:i386 (2.9.1+dfsg1-3ubuntu2), strace:i386 (4.8-1ubuntu2), libgxps2:i386 (0.2.2-2ubuntu2), aptdaemon-data:i386 (1.1.1-1ubuntu1), libquvi-scripts:i386 (0.4.20-1), fuse:i386 (2.9.2-4ubuntu3), audacious-plugins-data:i386 (3.4.1-1build1), libgmp10:i386 (5.1.2+dfsg-2ubuntu1, automatic), python-libxml2:i386 (2.9.1+dfsg1-3ubuntu2), libvte-2.90-common:i386 (0.34.9-1ubuntu1), libgupnp-igd-1.0-4:i386 (0.2.2-1), libfm-gtk3:i386 (1.1.2.2-1, automatic), glib-networking-common:i386 (2.38.1-1), transmission-gtk:i386 (2.82-0ubuntu1), libbluray1:i386 (0.4.0-1), libnet-dbus-perl:i386 (1.0.0-2build1), libminiupnpc8:i386 (1.6-3ubuntu2), pidgin:i386 (2.10.7-0ubuntu4.2), libpython2.7-stdlib:i386 (2.7.6-2ubuntu1, automatic), libxcb-render0:i386 (1.9.1-3ubuntu1, automatic), ftp:i386 (0.17-28), libburn4:i386 (1.3.2-1), libgtk-3-bin:i386 (3.8.7-0ubuntu1, automatic), libxklavier16:i386 (5.2.1-1ubuntu2, automatic), xserver-xorg-video-sis:i386 (0.10.7-0ubuntu4, automatic), libcamel-1.2-45:i386 (3.10.1-2ubuntu2), libxfce4util-common:i386 (4.10.1-1), ssl-cert:i386 (1.0.33, automatic), python3-gdbm:i386 (3.3.3-1), syslinux-common:i386 (4.05+dfsg-6+deb7u3ubuntu1), gucharmap:i386 (3.8.2-3), systemd-services:i386 (204-5ubuntu6), libgeoclue0:i386 (0.12.99-2ubuntu5), libxcb-glx0:i386 (1.9.1-3ubuntu1, automatic), libsane:i386 (1.0.23-3ubuntu1, automatic), libpcsclite1:i386 (1.8.6-3ubuntu1b1, automatic), libxrender1:i386 (0.9.8-1, automatic), libdbusmenu-gtk3-4:i386 (12.10.3+14.04.20131125-0ubuntu1), libdjvulibre21:i386 (3.5.25.4-2), libkeyutils1:i386 (1.5.6-1), libavc1394-0:i386 (0.5.4-2), libx11-data:i386 (1.6.2-1ubuntu1), libgrip0:i386 (0.3.7+13.10.20130628-0ubuntu1), libasyncns0:i386 (0.8-4ubuntu1), lxtask:i386 (0.1.4-3.1ubuntu1), libterm-ui-perl:i386 (0.38-1), libgmlib1:i386 (1.0.8-3), zenity:i386 (3.8.0-1), libunity-scopes-json-def-desktop:i386 (7.1.3+14.04.20131106-0ubuntu1), libgraphite2-3:i386 (1.2.3-1, automatic), libfile-listing-perl:i386 (6.04-1), libglapi-mesa:i386 (9.2.2-1ubuntu1, automatic), libcloog-isl4:i386 (0.18.1-3, automatic), libgssdp-1.0-3:i386 (0.14.6-1), libupower-glib1:i386 (0.9.23-2), python-dbus:i386 (1.2.0-2, automatic), tcpdump:i386 (4.4.0-1ubuntu1), x11-xfs-utils:i386 (7.7~1ubuntu1, automatic), libcupsimage2:i386 (1.7.0-0ubuntu2, automatic), software-properties-gtk:i386 (0.92.28), xfce-keyboard-shortcuts:i386 (4.10.0-5), dbus:i386 (1.6.18-0ubuntu2), libkrb5-26-heimdal:i386 (1.6~git20120403+dfsg1-3ubuntu0.2), libv4lconvert0:i386 (1.0.0-1, automatic), libpango1.0-0:i386 (1.36.0-1ubuntu1, automatic), xorg:i386 (7.7+1ubuntu6), libmtp-runtime:i386 (1.1.6-20-g1b9f164-1ubuntu2), libsecret-common:i386 (0.15-2ubuntu1), libatk1.0-data:i386 (2.10.0-2, automatic), libsecret-1-0:i386 (0.15-2ubuntu1), gnumeric:i386 (1.12.6-2), libtdb1:i386 (1.2.12-1, automatic), xfce4-power-manager:i386 (1.2.0-2ubuntu1), xinit:i386 (1.3.2-1, automatic), libxcb-xfixes0:i386 (1.9.1-3ubuntu1, automatic), gir1.2-unity-5.0:i386 (7.1.3+14.04.20131106-0ubuntu1), libgcr-base-3-1:i386 (3.10.1-1), libmhash2:i386 (0.9.9.9-4), libxcb-shape0:i386 (1.9.1-3ubuntu1, automatic), humanity-icon-theme:i386 (0.6.4, automatic), libenca0:i386 (1.15-1), libijs-0.35:i386 (0.35-8build1, automatic), libdv4:i386 (1.0.0-6), libexif12:i386 (0.6.21-1, automatic), libxt6:i386 (1.1.4-1, automatic), ubuntu-standard:i386 (1.310), xserver-xorg-video-sisusb:i386 (0.9.6-2, automatic), xfonts-encodings:i386 (1.0.4-1ubuntu1, automatic), bsdmainutils:i386 (9.0.5ubuntu1), libreadline5:i386 (5.2+dfsg-2, automatic), printer-driver-pnm2ppa:i386 (1.13+nondbs-0ubuntu3), lxlauncher:i386 (0.2.2-3ubuntu2), liblog-message-simple-perl:i386 (0.10-1), libnl-3-200:i386 (3.2.16-0ubuntu1, automatic), libwayland-client0:i386 (1.3.0-1, automatic), libsane-common:i386 (1.0.23-3ubuntu1, automatic), gir1.2-soup-2.4:i386 (2.44.1-1), libxxf86dga1:i386 (1.1.4-1, automatic), python-gobject-2:i386 (2.28.6-12, automatic), libwavpack1:i386 (4.70.0-1), libva1:i386 (1.2.1-2), firefox:i386 (25.0+build3-0ubuntu0.13.10.1), libmnl0:i386 (1.0.3-3), python-minimal:i386 (2.7.5-5ubuntu1, automatic), libpwquality1:i386 (1.2.3-1), transmission-common:i386 (2.82-0ubuntu1), libmenu-cache-bin:i386 (0.5.1-1, automatic), xserver-xorg-video-savage:i386 (2.3.6-0ubuntu3, automatic), ace-of-penguins:i386 (1.4-0ubuntu2), libxcomposite1:i386 (0.4.4-1, automatic), gir1.2-javascriptcoregtk-3.0:i386 (2.2.1-2ubuntu2), libcupsfilters1:i386 (1.0.41-0ubuntu1, automatic), python-gi:i386 (3.10.2-1, automatic), iputils-tracepath:i386 (20121221-1ubuntu1), libxv1:i386 (1.0.9-1, automatic), geoip-database:i386 (20131118-1), libxxf86vm1:i386 (1.1.3-1, automatic), iptables:i386 (1.4.20-2ubuntu1), libt1-5:i386 (5.1.2-3.6), libdca0:i386 (0.0.5-6), libmusicbrainz3-6:i386 (3.0.2-2.1), libgd3:i386 (2.1.0-3, automatic), fonts-nanum:i386 (3.020-3), libgtk2.0-0:i386 (2.24.22-1ubuntu1, automatic), libjte1:i386 (1.19-1ubuntu1), libdrm-intel1:i386 (2.4.49-2, automatic), libnss3:i386 (3.15.3-1), libgtop2-7:i386 (2.28.5-2), libpixman-1-0:i386 (0.30.2-2, automatic), xserver-xorg-core:i386 (1.14.3-5ubuntu1, automatic), gnome-mplayer:i386 (1.0.8-2), libabiword-3.0:i386 (3.0.0-1), libvte-2.90-9:i386 (0.34.9-1ubuntu1), libhcrypto4-heimdal:i386 (1.6~git20120403+dfsg1-3ubuntu0.2), libjson-glib-1.0-common:i386 (0.16.2-1), fonts-freefont-ttf:i386 (20120503-1), libgstreamer-plugins-base0.10-0:i386 (0.10.36-1.1ubuntu1), libclutter-gtk-1.0-0:i386 (1.4.4-3), lubuntu-default-settings:i386 (0.35), libcurl3:i386 (7.33.0-1ubuntu1), python3-dbus:i386 (1.2.0-2), apport-gtk:i386 (2.12.7-0ubuntu1), libgtk-3-0:i386 (3.8.7-0ubuntu1, automatic), libogg0:i386 (1.3.1-1), libdjvulibre-text:i386 (3.5.25.4-2), libproxy1:i386 (0.4.11-0ubuntu4), man-db:i386 (2.6.5-2), python3-software-properties:i386 (0.92.28), libasn1-8-heimdal:i386 (1.6~git20120403+dfsg1-3ubuntu0.2), libgirepository-1.0-1:i386 (1.38.0-0ubuntu1), libxslt1.1:i386 (1.1.28-2), rfkill:i386 (0.5-1ubuntu1), libmpg123-0:i386 (1.15.3-1ubuntu1), xserver-xorg-video-mga:i386 (1.6.2-1fakesync1, automatic), libegl1-mesa:i386 (9.2.2-1ubuntu1, automatic), anacron:i386 (2.3-19ubuntu2), gvfs-libs:i386 (1.19.2-0ubuntu1), libarchive13:i386 (3.1.2-5ubuntu1, automatic), libqpdf13:i386 (5.0.1-1, automatic), liborc-0.4-0:i386 (0.4.18-1), libxmu6:i386 (1.1.1-1, automatic), upower:i386 (0.9.23-2), linux-image-extra-3.12.0-4-generic:i386 (3.12.0-4.12, automatic), giblib1:i386 (1.2.4-9), gnome-icon-theme-symbolic:i386 (3.10.1-1, automatic), libwv-1.2-4:i386 (1.2.9-3), libsamplerate0:i386 (0.1.8-5ubuntu1, automatic), libatasmart4:i386 (0.19-3), fontconfig:i386 (2.11.0-0ubuntu2, automatic), ubuntu-drivers-common:i386 (0.2.84, automatic), libxcb-shm0:i386 (1.9.1-3ubuntu1, automatic), libhunspell-1.3-0:i386 (1.3.2-6ubuntu1), xfonts-base:i386 (1.0.3, automatic), libpwquality-common:i386 (1.2.3-1), libraptor2-0:i386 (2.0.11-1), libpackagekit-glib2-16:i386 (0.8.12-1ubuntu1, automatic), pciutils:i386 (3.1.9-6ubuntu11), gpicview:i386 (0.2.4-1), libgbm1:i386 (9.2.2-1ubuntu1, automatic), libevview3-3:i386 (3.10.3-0ubuntu1), libpcap0.8:i386 (1.4.0-2), linux-image-3.12.0-4-generic:i386 (3.12.0-4.12, automatic), xserver-xorg-video-r128:i386 (6.9.1-1, automatic), mobile-broadband-provider-info:i386 (20130915-1), gir1.2-freedesktop:i386 (1.38.0-0ubuntu1), libquadmath0:i386 (4.8.2-1ubuntu2), libwmf0.2-7:i386 (0.2.8.4-10.3ubuntu1), libxinerama1:i386 (1.1.3-1, automatic), libwebkitgtk-3.0-0:i386 (2.2.1-2ubuntu2), liburi-perl:i386 (1.60-1, automatic), python-apt-common:i386 (0.9.1), libxmuu1:i386 (1.1.1-1), app-install-data:i386 (13.10.1), gstreamer0.10-plugins-good:i386 (0.10.31-3+nmu1ubuntu3), libjbig2dec0:i386 (0.11+20120125-1ubuntu1, automatic), lightdm:i386 (1.9.3-0ubuntu1), gnome-time-admin:i386 (3.0.0-2ubuntu2), libneon27-gnutls:i386 (0.30.0-1), synaptic:i386 (0.80.4), language-selector-gnome:i386 (0.118), libfaad2:i386 (2.7-8), libpod-latex-perl:i386 (0.61-1), python-talloc:i386 (2.1.0-1, automatic), dconf-cli:i386 (0.18.0-1), libgtk2-perl:i386 (1.248-1), systemd-shim:i386 (5-0ubuntu2), libhttp-cookies-perl:i386 (6.00-2), libpangoft2-1.0-0:i386 (1.36.0-1ubuntu1, automatic), librsvg2-2:i386 (2.40.0-1, automatic), libdrm-radeon1:i386 (2.4.49-2, automatic), audacious-plugins:i386 (3.4.1-1build1), libfarstream-0.1-0:i386 (0.1.2-1ubuntu2), obex-data-server:i386 (0.4.6-0ubuntu2), packagekit:i386 (0.8.12-1ubuntu1, automatic), libtalloc2:i386 (2.1.0-1, automatic), lxshortcut:i386 (0.1.2-3), libcdparanoia0:i386 (3.10.2+debian-11), libdbusmenu-glib4:i386 (12.10.3+14.04.20131125-0ubuntu1), libsasl2-modules-db:i386 (2.1.25.dfsg1-17build1), audacious:i386 (3.4.1-1), libwww-perl:i386 (6.05-1), liblightdm-gobject-1-0:i386 (1.9.3-0ubuntu1, automatic), libisccc90:i386 (9.9.3.dfsg.P2-4ubuntu1), libuniconf4.6:i386 (4.6.1-7), libjbig0:i386 (2.0-2ubuntu1, automatic), scrot:i386 (0.8-13), libvorbisfile3:i386 (1.3.2-1.3), fonts-liberation:i386 (1.07.3-3), libaa1:i386 (1.4p5-41), libept1.4.12:i386 (1.0.12), liblzo2-2:i386 (2.06-1.2, automatic), libtext-soundex-perl:i386 (3.4-1build1), libxfont1:i386 (1.4.6-1, automatic), libnfnetlink0:i386 (1.0.1-2), libxdmcp6:i386 (1.1.1-1), libebook-contacts-1.2-0:i386 (3.10.1-2ubuntu2), policykit-desktop-privileges:i386 (0.16, automatic), libcaca0:i386 (0.99.beta18-1ubuntu4), libavresample1:i386 (9.10-1ubuntu1), xserver-common:i386 (1.14.3-5ubuntu1, automatic), gnome-system-tools:i386 (3.0.0-2ubuntu2), python-aptdaemon:i386 (1.1.1-1ubuntu1), libxkbcommon0:i386 (0.3.1-2, automatic), libdirectfb-1.2-9:i386 (1.2.10.0-5), libgnome-keyring0:i386 (3.8.0-2), dmz-cursor-theme:i386 (0.4.3ubuntu1), plymouth-theme-lubuntu-logo:i386 (0.42), libtevent0:i386 (0.9.19-1, automatic), libappindicator3-1:i386 (12.10.1+13.10.20130920-0ubuntu2), libnautilus-extension1a:i386 (3.8.2-0ubuntu3), libpolkit-agent-1-0:i386 (0.105-4ubuntu1, automatic), libbluetooth3:i386 (4.101-0ubuntu8b1), libcolord1:i386 (1.0.2-1, automatic), ltrace:i386 (0.5.3-2.1ubuntu3), libxatracker1:i386 (9.2.2-1ubuntu1, automatic), libkrb5support0:i386 (1.11.3+dfsg-3ubuntu2), x11-utils:i386 (7.7+1, automatic), xserver-xorg-video-neomagic:i386 (1.2.8-1, automatic), ubuntu-release-upgrader-gtk:i386 (0.209), libjson-glib-1.0-0:i386 (0.16.2-1), sylpheed-i18n:i386 (3.4.0~beta5-1ubuntu1), libcogl-pango12:i386 (1.14.0-3), libgtk2.0-common:i386 (2.24.22-1ubuntu1, automatic), sylpheed-plugins:i386 (3.4.0~beta5-1ubuntu1), gir1.2-vte-2.90:i386 (0.34.9-1ubuntu1), libopus0:i386 (1.0.3-0ubuntu1), aptdaemon:i386 (1.1.1-1ubuntu1, automatic), libexo-common:i386 (0.10.2-2), python-cups:i386 (1.9.63-0ubuntu1), libnm-gtk0:i386 (0.9.8.0-1ubuntu5), cups:i386 (1.7.0-0ubuntu2, automatic), libvte-common:i386 (0.28.2-5ubuntu1), gecko-mediaplayer:i386 (1.0.8-4ubuntu1), libpython-stdlib:i386 (2.7.5-5ubuntu1, automatic), libwrap0:i386 (7.6.q-24, automatic), libavahi-common-data:i386 (0.6.31-2ubuntu5, automatic), libcairo-perl:i386 (1.104-1), python3-chardet:i386 (2.0.1-1), lubuntu-desktop:i386 (0.52), lxappearance-obconf:i386 (0.2.0-4ubuntu2), libfuse2:i386 (2.9.2-4ubuntu3), evolution-data-server-common:i386 (3.10.1-2ubuntu2), libelf1:i386 (0.157-1ubuntu1), lxterminal:i386 (0.1.11-4ubuntu3), libharfbuzz-icu0:i386 (0.9.19-1), libcairo-gobject2:i386 (1.12.16-0ubuntu2, automatic), sound-theme-freedesktop:i386 (0.8-1), libfm-data:i386 (1.1.2.2-1, automatic), gir1.2-dee-1.0:i386 (1.2.7+13.10.20130924.1-0ubuntu1), gir1.2-dbusmenu-glib-0.4:i386 (12.10.3+14.04.20131125-0ubuntu1), libnetfilter-conntrack3:i386 (1.0.4-1), ffmpegthumbnailer:i386 (2.0.8-1), policykit-1-gnome:i386 (0.105-1ubuntu4, automatic), libcap2-bin:i386 (2.22-1.2ubuntu2), gsfonts:i386 (8.11+urwcyr1.0.7~pre44-4.2ubuntu1, automatic), libkdc2-heimdal:i386 (1.6~git20120403+dfsg1-3ubuntu0.2, automatic), libdvdread4:i386 (4.2.0+20130219-2ubuntu2), libclutter-1.0-0:i386 (1.14.4-3), mtools:i386 (4.0.18-1ubuntu1), transmission:i386 (2.82-0ubuntu1), update-manager:i386 (0.196.2), libx11-6:i386 (1.6.2-1ubuntu1), lxpanel:i386 (0.6.1-0ubuntu1), libxrandr2:i386 (1.4.1-1ubuntu1, automatic), cups-common:i386 (1.7.0-0ubuntu2, automatic), syslinux-legacy:i386 (3.63+dfsg-2ubuntu5), libavahi-client3:i386 (0.6.31-2ubuntu5, automatic), genisoimage:i386 (1.1.11-2ubuntu3, automatic), libsoup2.4-1:i386 (2.44.1-1), patch:i386 (2.7.1-4, automatic), x11-common:i386 (7.7+1ubuntu6, automatic), xserver-xorg-video-modesetting:i386 (0.8.0-1, automatic), gtk3-engines-unico:i386 (1.0.3daily13.05.30-0ubuntu1, automatic), libmeanwhile1:i386 (1.0.2-4.1), gnome-keyring:i386 (3.10.1-1ubuntu3), xserver-xorg-video-siliconmotion:i386 (1.7.7-2, automatic), libgmtk1:i386 (1.0.8-3), libimobiledevice4:i386 (1.1.5-2), xserver-xorg-video-cirrus:i386 (1.5.2-1, automatic), fontconfig-config:i386 (2.11.0-0ubuntu2, automatic), libpostproc52:i386 (0.git20120821-4), packagekit-backend-aptcc:i386 (0.8.12-1ubuntu1, automatic), hicolor-icon-theme:i386 (0.12-1ubuntu2, automatic), xfce4-power-manager-data:i386 (1.2.0-2ubuntu1), libiec61883-0:i386 (1.2.0-0.1ubuntu2), parted:i386 (2.3-16ubuntu1), gir1.2-gtk-3.0:i386 (3.8.7-0ubuntu1), xml-core:i386 (0.13+nmu2), libcanberra-gtk3-0:i386 (0.30-0ubuntu2), libisc95:i386 (9.9.3.dfsg.P2-4ubuntu1), libxfce4util6:i386 (4.10.1-1), libstartup-notification0:i386 (0.12-3, automatic), libavutil52:i386 (9.10-1ubuntu1), librdf0:i386 (1.0.16-3), libhttp-negotiate-perl:i386 (6.00-2), libgrail6:i386 (3.1.0daily13.06.05-0ubuntu1), mtpaint:i386 (3.40-1ubuntu1), libobrender29:i386 (3.5.2-4, automatic), libsoup-gnome2.4-1:i386 (2.44.1-1), xfconf:i386 (4.10.0-2), libxvmc1:i386 (1.0.8-1ubuntu1, automatic), libchamplain-0.12-0:i386 (0.12.5-1), uuid-runtime:i386 (2.20.1-5.1ubuntu9), libpolkit-backend-1-0:i386 (0.105-4ubuntu1, automatic), glib-networking-services:i386 (2.38.1-1), libbind9-90:i386 (9.9.3.dfsg.P2-4ubuntu1), x11-xserver-utils:i386 (7.7+0ubuntu2, automatic), ubuntu-release-upgrader-core:i386 (0.209), lubuntu-artwork-14-04:i386 (0.42, automatic), libdevmapper-event1.02.1:i386 (1.02.77-6ubuntu1), xfburn:i386 (0.4.3-6ubuntu1), gsettings-desktop-schemas:i386 (3.8.0-1ubuntu1), xserver-xorg-video-nouveau:i386 (1.0.10-1ubuntu1, automatic), cups-filters:i386 (1.0.41-0ubuntu1, automatic), libhtml-tree-perl:i386 (5.03-1), libjpeg8:i386 (8c-2ubuntu8, automatic), xserver-xorg-video-openchrome:i386 (0.3.3-1, automatic), gnome-accessibility-themes:i386 (3.8.4-0ubuntu1), libobt2:i386 (3.5.2-4, automatic), popularity-contest:i386 (1.57ubuntu1), libgcr-ui-3-1:i386 (3.10.1-1), libtimedate-perl:i386 (1.2000-1, automatic), python-apt:i386 (0.9.1), libsmbclient:i386 (4.0.10+dfsg-4ubuntu2, automatic), libcupsppdc1:i386 (1.7.0-0ubuntu2, automatic), pm-utils:i386 (1.4.1-13), libhdb9-heimdal:i386 (1.6~git20120403+dfsg1-3ubuntu0.2, automatic), libxcb-dri2-0:i386 (1.9.1-3ubuntu1, automatic), xbitmaps:i386 (1.1.1-2, automatic), libdee-1.0-4:i386 (1.2.7+13.10.20130924.1-0ubuntu1), libcogl12:i386 (1.14.0-3), libwebkitgtk-3.0-common:i386 (2.2.1-2ubuntu2), iputils-arping:i386 (20121221-1ubuntu1), libwnck22:i386 (2.30.7-0ubuntu3, automatic), lubuntu-artwork:i386 (0.42), system-tools-backends:i386 (2.10.2-1ubuntu1), apport:i386 (2.12.7-0ubuntu1, automatic), libloudmouth1-0:i386 (1.4.3-10), libgs9:i386 (9.10~dfsg-0ubuntu3, automatic), libaspell15:i386 (0.60.7~20110707-1build1), libevent-2.0-5:i386 (2.0.21-stable-1), linux-headers-3.12.0-4:i386 (3.12.0-4.12, automatic), libglib2.0-0:i386 (2.39.1-0ubuntu1), gdebi:i386 (0.9.1ubuntu1), mlocate:i386 (0.26-1ubuntu1), libedit2:i386 (3.1-20130712-2), libisl10:i386 (0.12.1-2, automatic), libxpm4:i386 (3.5.10-1, automatic), libgpm2:i386 (1.20.4-6.1), libmms0:i386 (0.6.2-3ubuntu1), wireless-tools:i386 (30~pre9-8ubuntu1), psmisc:i386 (22.20-1ubuntu2), libisofs6:i386 (1.3.2-1ubuntu1), ntp:i386 (4.2.6.p5+dfsg-3ubuntu2), elementary-icon-theme:i386 (2.7.1-0ubuntu6, automatic), libcupscgi1:i386 (1.7.0-0ubuntu2, automatic), simple-scan:i386 (3.11.1.1-0ubuntu1), gvfs:i386 (1.19.2-0ubuntu1), indicator-application:i386 (12.10.1+14.04.20131125-0ubuntu1), libnm-glib-vpn1:i386 (0.9.8.4-0ubuntu3), printer-driver-gutenprint:i386 (5.2.9-1ubuntu2, automatic), gir1.2-atk-1.0:i386 (2.10.0-2), libldap-2.4-2:i386 (2.4.31-1+nmu2ubuntu5), pppoeconf:i386 (1.20ubuntu1), libts-0.0-0:i386 (1.0-11), libgee2:i386 (0.6.8-1, automatic), gstreamer0.10-nice:i386 (0.1.4-1), libgphoto2-6:i386 (2.5.2-0ubuntu5, automatic), liblwres90:i386 (9.9.3.dfsg.P2-4ubuntu1), libspeex1:i386 (1.2~rc1-7ubuntu2), python-gnomekeyring:i386 (2.32.0+dfsg-3), alsa-base:i386 (1.0.25+dfsg-0ubuntu4), libdbusmenu-gtk4:i386 (12.10.3+14.04.20131125-0ubuntu1), libgtop2-common:i386 (2.28.5-2), libnet-http-perl:i386 (6.06-1), gir1.2-gdkpixbuf-2.0:i386 (2.30.1-0ubuntu2), ibus:i386 (1.5.3-6ubuntu4), libpango-1.0-0:i386 (1.36.0-1ubuntu1, automatic), libopenobex1:i386 (1.5-2.1), sgml-base:i386 (1.26+nmu4ubuntu1), mplayer2:i386 (2.0-701-gd4c5b7f-2), openssl:i386 (1.0.1e-3ubuntu1), libsystemd-login0:i386 (204-5ubuntu6), gir1.2-gudev-1.0:i386 (204-5ubuntu6), network-manager-gnome:i386 (0.9.8.0-1ubuntu5), libxfixes3:i386 (5.0.1-1ubuntu1, automatic), libwpd-0.9-9:i386 (0.9.9-1), libavahi-common3:i386 (0.6.31-2ubuntu5, automatic), usb-creator-gtk:i386 (0.2.50), libdrm-nouveau2:i386 (2.4.49-2, automatic), gir1.2-pango-1.0:i386 (1.36.0-1ubuntu1), gtk2-engines-pixbuf:i386 (2.24.22-1ubuntu1, automatic), linux-generic:i386 (3.12.0.4.6), xorg-docs-core:i386 (1.7-1, automatic), libhtml-parser-perl:i386 (3.71-1build1), lxsession-data:i386 (0.4.9.2-0ubuntu6, automatic), dosfstools:i386 (3.0.24-1), gconf-service-backend:i386 (3.2.6-0ubuntu1), libusbmuxd2:i386 (1.0.8-2ubuntu1), libsasl2-modules:i386 (2.1.25.dfsg1-17build1), libgsf-1-common:i386 (1.14.27-2ubuntu1), libpango-perl:i386 (1.224-2), lshw:i386 (02.16-2), gcr:i386 (3.10.1-1), libgpgme11:i386 (1.4.3-0.1ubuntu2), libid3tag0:i386 (0.15.1b-10build3, automatic), liblcms2-2:i386 (2.5-0ubuntu1, automatic), cups-server-common:i386 (1.7.0-0ubuntu2, automatic), libfm3:i386 (1.1.2.2-1, automatic), libgstreamer1.0-0:i386 (1.2.1-1), python3-update-manager:i386 (0.196.2), iso-codes:i386 (3.48-1), hdparm:i386 (9.43-1ubuntu3), libperl5.18:i386 (5.18.1-4build1, automatic), libwnck-common:i386 (2.30.7-0ubuntu3, automatic), wget:i386 (1.14-2ubuntu1), libunity9:i386 (7.1.3+14.04.20131106-0ubuntu1), libasound2:i386 (1.0.27.2-3ubuntu1, automatic), libutempter0:i386 (1.1.5-4build1, automatic), libapparmor-perl:i386 (2.8.0-0ubuntu34), libmad0:i386 (0.15.1b-8ubuntu1), libjpeg-turbo8:i386 (1.3.0-0ubuntu1, automatic), python3-aptdaemon.gtk3widgets:i386 (1.1.1-1ubuntu1), xpad:i386 (4.1-1ubuntu4), libatk-bridge2.0-0:i386 (2.10.0-1, automatic), libjavascriptcoregtk-3.0-0:i386 (2.2.1-2ubuntu2), libvorbis0a:i386 (1.3.2-1.3), libmpc3:i386 (1.0.1-1ubuntu1, automatic), libexo-helpers:i386 (0.10.2-2), gnome-icon-theme:i386 (3.10.0-0ubuntu1, automatic), libgda-5.0-4:i386 (5.0.3-2ubuntu1), openssh-client:i386 (6.4p1-1), xserver-xorg-video-intel:i386 (2.99.904-0ubuntu2, automatic), libglib2.0-bin:i386 (2.39.1-0ubuntu1, automatic), libpam-systemd:i386 (204-5ubuntu6), xfce4-notifyd:i386 (0.2.4-2), libibus-1.0-5:i386 (1.5.3-6ubuntu4), xinput:i386 (1.6.0-1, automatic), avahi-daemon:i386 (0.6.31-2ubuntu5, automatic), python-chardet:i386 (2.0.1-2build1), cpp:i386 (4.8.1-2ubuntu3, automatic), libbinio1ldbl:i386 (1.4+dfsg1-1), bluez:i386 (4.101-0ubuntu8b1, automatic), lubuntu-default-session:i386 (0.35), libcrack2:i386 (2.9.0-2), libxext6:i386 (1.3.2-1), libframe6:i386 (2.5.0daily13.06.05-0ubuntu1), xserver-xorg-video-mach64:i386 (6.9.4-1, automatic), libcurl3-gnutls:i386 (7.33.0-1ubuntu1), libxft2:i386 (2.3.1-1, automatic), usb-modeswitch:i386 (1.2.3+repack0-1ubuntu3), plymouth-label:i386 (0.8.8-0ubuntu10, automatic), accountsservice:i386 (0.6.35-0ubuntu1), libjack-jackd2-0:i386 (1.9.9.5+20130622git7de15e7a-1ubuntu1), lxinput:i386 (0.3.2-1), leafpad:i386 (0.8.18.1-4), libisccfg90:i386 (9.9.3.dfsg.P2-4ubuntu1), system-config-printer-common:i386 (1.4.2+20130920-0ubuntu2), evince-common:i386 (3.10.3-0ubuntu1), libgs9-common:i386 (9.10~dfsg-0ubuntu3, automatic), xfonts-utils:i386 (7.7~1ubuntu1, automatic), libcanberra0:i386 (0.30-0ubuntu2), libgail-3-0:i386 (3.8.7-0ubuntu1), libxau6:i386 (1.0.8-1), libltdl7:i386 (2.4.2-1.3ubuntu2, automatic), libxcb-util0:i386 (0.3.8-2build1, automatic), sylpheed-doc:i386 (20120629-1), telnet:i386 (0.17-36build2), udisks2:i386 (2.1.1-1), obconf:i386 (2.0.4+git20130908-1), libaio1:i386 (0.3.109-4, automatic), usb-modeswitch-data:i386 (20120815-2), dnsutils:i386 (9.9.3.dfsg.P2-4ubuntu1), libguess1:i386 (1.1-3), abiword:i386 (3.0.0-1), python3-apport:i386 (2.12.7-0ubuntu1, automatic), libusb-1.0-0:i386 (1.0.17-1), poppler-utils:i386 (0.24.3-0ubuntu1, automatic), libthai-data:i386 (0.1.20-1, automatic), libatspi2.0-0:i386 (2.10.1-0ubuntu1, automatic), xserver-xorg-input-all:i386 (7.7+1ubuntu6, automatic), linux-image-generic:i386 (3.12.0.4.6, automatic), gir1.2-glib-2.0:i386 (1.38.0-0ubuntu1), liblircclient0:i386 (0.9.0-0ubuntu3), libglu1-mesa:i386 (9.0.0-2, automatic), x11-apps:i386 (7.7+1ubuntu1, automatic), libaccountsservice0:i386 (0.6.35-0ubuntu1), linux-headers-generic:i386 (3.12.0.4.6, automatic), libieee1284-3:i386 (0.2.11-12, automatic), libvdpau1:i386 (0.7-1), libgl1-mesa-dri:i386 (9.2.2-1ubuntu1, automatic), libwhoopsie0:i386 (0.2.24.1), unzip:i386 (6.0-9ubuntu1, automatic), desktop-file-utils:i386 (0.22-1ubuntu1), libcompfaceg1:i386 (1.5.2-5), libgupnp-1.0-4:i386 (0.20.8-1), libicu48:i386 (4.8.1.1-13+nmu1ubuntu1), inputattach:i386 (1.4.6-1), apturl-common:i386 (0.5.2ubuntu2), libdvdnav4:i386 (4.2.0+20130225-4), libxaw7:i386 (1.0.11-1, automatic), libnice10:i386 (0.1.4-1), libwayland-server0:i386 (1.3.0-1, automatic), libroken18-heimdal:i386 (1.6~git20120403+dfsg1-3ubuntu0.2), x11-session-utils:i386 (7.6+2ubuntu1, automatic), gdebi-core:i386 (0.9.1ubuntu1), libgda-5.0-common:i386 (5.0.3-2ubuntu1), libtelepathy-glib0:i386 (0.22.0-1), python-xdg:i386 (0.25-3), lxappearance:i386 (0.5.2-1ubuntu2), libdbus-glib-1-2:i386 (0.100.2-1), libgdk-pixbuf2.0-common:i386 (2.30.1-0ubuntu2, automatic), linux-sound-base:i386 (1.0.25+dfsg-0ubuntu4, automatic), libmenu-cache3:i386 (0.5.1-1, automatic), gir1.2-webkit-3.0:i386 (2.2.1-2ubuntu2), lubuntu-icon-theme:i386 (0.42, automatic), xserver-xorg-input-wacom:i386 (0.23.0-0ubuntu1, automatic), libnm-util2:i386 (0.9.8.4-0ubuntu3), libpulse0:i386 (4.0-0ubuntu6), memtest86+:i386 (4.20-1.1ubuntu5), libgeoip1:i386 (1.5.1-2ubuntu1), xserver-xorg-video-fbdev:i386 (0.4.3-0ubuntu3, automatic), libice6:i386 (1.0.8-2, automatic), time:i386 (1.7-24), x11-xkb-utils:i386 (7.7~1ubuntu1, automatic), lsof:i386 (4.86+dfsg-1ubuntu2), shared-mime-info:i386 (1.2-0ubuntu1), libfs6:i386 (1.0.5-1, automatic), libgcr-3-common:i386 (3.10.1-1), libgeis1:i386 (2.2.16+13.10.20130919.4-0ubuntu1), libavahi-glib1:i386 (0.6.31-2ubuntu5, automatic), file-roller:i386 (3.10.2.1-0ubuntu1), libzephyr4:i386 (3.1.2-1), language-selector-common:i386 (0.118), ttf-wqy-microhei:i386 (0.2.0-beta-1.1ubuntu4), libxfce4ui-1-0:i386 (4.10.0-5), libxtables10:i386 (1.4.20-2ubuntu1), libmowgli2:i386 (1.0.0-1ubuntu1), python-notify:i386 (0.1.1-3ubuntu1), libhttp-date-perl:i386 (6.02-1), samba-libs:i386 (4.0.10+dfsg-4ubuntu2, automatic), lubuntu-core:i386 (0.52), python3-apt:i386 (0.9.1), libopenjpeg2:i386 (1.3+dfsg-4.6ubuntu2), libpciaccess0:i386 (0.13.2-1, automatic), xserver-xorg-video-all:i386 (7.7+1ubuntu6, automatic), libchamplain-gtk-0.12-0:i386 (0.12.5-1), python-cupshelpers:i386 (1.4.2+20130920-0ubuntu2), python2.7-minimal:i386 (2.7.6-2ubuntu1, automatic), plymouth-theme-lubuntu-text:i386 (0.42), libarchive-extract-perl:i386 (0.68-1), libical1:i386 (1.0-0ubuntu1), libgmtk1-data:i386 (1.0.8-3), install-info:i386 (5.1.dfsg.1-4ubuntu1), libwebp4:i386 (0.3.0-3), libwww-robotrules-perl:i386 (6.01-1), plymouth-theme-ubuntu-text:i386 (0.8.8-0ubuntu10), gstreamer0.10-plugins-base:i386 (0.10.36-1.1ubuntu1), libpolkit-gobject-1-0:i386 (0.105-4ubuntu1), libhx509-5-heimdal:i386 (1.6~git20120403+dfsg1-3ubuntu0.2), bind9-host:i386 (9.9.3.dfsg.P2-4ubuntu1), crda:i386 (1.1.2-1ubuntu2, automatic), libquvi7:i386 (0.4.1-1ubuntu2), lxrandr:i386 (0.1.2-3), pppconfig:i386 (2.3.19ubuntu1), libass4:i386 (0.10.1-3), libtidy-0.99-0:i386 (20091223cvs-1.2), libpangox-1.0-0:i386 (0.0.2-4, automatic), libtag1-vanilla:i386 (1.9.1-2), poppler-data:i386 (0.4.6-4, automatic), libiw30:i386 (30~pre9-8ubuntu1, automatic), update-notifier-common:i386 (0.148), whoopsie:i386 (0.2.24.1), acl:i386 (2.2.52-1, automatic), libcdio-cdda1:i386 (0.83-4.1), libencode-locale-perl:i386 (1.03-1), libaudcore1:i386 (3.4.1-1), libonig2:i386 (5.9.1-1), libgif4:i386 (4.1.6-10ubuntu1, automatic), libcups2:i386 (1.7.0-0ubuntu2, automatic), libshout3:i386 (2.3.1-3), python3-packagekit:i386 (0.8.12-1ubuntu1, automatic), libheimbase1-heimdal:i386 (1.6~git20120403+dfsg1-3ubuntu0.2), libgksu2-0:i386 (2.0.13~pre1-6ubuntu3), python-pysqlite2:i386 (2.6.3-3), libtiff5:i386 (4.0.3-5ubuntu1, automatic), libllvm3.3:i386 (3.3-5ubuntu4, automatic), xserver-xorg-video-radeon:i386 (7.2.0-0ubuntu10, automatic), cups-ppdc:i386 (1.7.0-0ubuntu2, automatic), libpoppler43:i386 (0.24.3-0ubuntu1, automatic), libnl-route-3-200:i386 (3.2.16-0ubuntu1), libglib-perl:i386 (1.302-1), gir1.2-packagekitglib-1.0:i386 (0.8.12-1ubuntu1, automatic), libbs2b0:i386 (3.1.0+dfsg-2ubuntu1), libpangocairo-1.0-0:i386 (1.36.0-1ubuntu1, automatic), xserver-xorg-video-s3:i386 (0.6.5-0ubuntu3.1, automatic), libwvstreams4.6-extras:i386 (4.6.1-7), wireless-regdb:i386 (2013.02.13-1ubuntu1, automatic), blueman:i386 (1.23+update1-2ubuntu1), libio-socket-ssl-perl:i386 (1.76-2ubuntu1, automatic), libpython2.7:i386 (2.7.6-2ubuntu1, automatic), libgssapi3-heimdal:i386 (1.6~git20120403+dfsg1-3ubuntu0.2), python-six:i386 (1.4.1-1), system-config-printer-gnome:i386 (1.4.2+20130920-0ubuntu2), libmodule-pluggable-perl:i386 (4.8-1), python-gobject:i386 (3.10.2-1), dmidecode:i386 (2.12-2), libwpg-0.2-2:i386 (0.2.2-1), libenchant1c2a:i386 (1.6.0-10), xserver-xorg-video-qxl:i386 (0.1.1-0ubuntu2, automatic), gconf2:i386 (3.2.6-0ubuntu1), libgoffice-0.10-10-common:i386 (0.10.8-1), groff-base:i386 (1.22.2-3), ca-certificates:i386 (20130906), libdiscid0:i386 (0.6.1-2), xserver-xorg-input-evdev:i386 (2.7.3-0ubuntu3.1, automatic), libvte9:i386 (0.28.2-5ubuntu1), libxdamage1:i386 (1.1.4-1ubuntu1, automatic), xterm:i386 (297-1ubuntu1), usbutils:i386 (007-2), python-smbc:i386 (1.0.13-0ubuntu4), python-cairo:i386 (1.8.8-1ubuntu4), libxcursor1:i386 (1.1.14-1, automatic), alsa-utils:i386 (1.0.27.1-1ubuntu1, automatic), libnl-genl-3-200:i386 (3.2.16-0ubuntu1, automatic), libmp3lame0:i386 (3.99.5+repack1-3), xdg-user-dirs:i386 (0.15-1ubuntu2), lightdm-gtk-greeter:i386 (1.6.1-0ubuntu1), xserver-xorg-video-vesa:i386 (2.3.3-1, automatic), libcddb2:i386 (1.3.2-4fakesync1), libcdio13:i386 (0.83-4.1), libnm-gtk-common:i386 (0.9.8.0-1ubuntu5), software-properties-common:i386 (0.92.28), libatk1.0-0:i386 (2.10.0-2, automatic), gettext-base:i386 (0.18.3.1-1ubuntu1), libmtp-common:i386 (1.1.6-20-g1b9f164-1ubuntu2), libfreetype6:i386 (2.5.1-1ubuntu1, automatic), update-manager-core:i386 (0.196.2), gvfs-daemons:i386 (1.19.2-0ubuntu1), python3-problem-report:i386 (2.12.7-0ubuntu1, automatic), libxml-twig-perl:i386 (3.39-1ubuntu1), libswscale2:i386 (9.10-1ubuntu1), libplist1:i386 (1.10-1), python:i386 (2.7.5-5ubuntu1, automatic), libparted0debian1:i386 (2.3-16ubuntu1), libgconf-2-4:i386 (3.2.6-0ubuntu1), libxres1:i386 (1.0.7-1, automatic), libnspr4:i386 (4.9.5-1ubuntu1), ttf-ubuntu-font-family:i386 (0.80-0ubuntu6, automatic), libcue1:i386 (1.4.0-1), apturl:i386 (0.5.2ubuntu2), libgutenprint2:i386 (5.2.9-1ubuntu2, automatic), openbox:i386 (3.5.2-4), python3-pkg-resources:i386 (0.6.49-2ubuntu1, automatic), python-defer:i386 (1.0.6-2), gir1.2-ibus-1.0:i386 (1.5.3-6ubuntu4), unattended-upgrades:i386 (0.79.3ubuntu8), libxtst6:i386 (1.2.2-1, automatic), libasprintf0c2:i386 (0.18.3.1-1ubuntu1), gnome-icon-theme-full:i386 (3.10.0-0ubuntu1, automatic), wpasupplicant:i386 (1.0-3ubuntu4, automatic), libxapian22:i386 (1.2.15-2), sylpheed:i386 (3.4.0~beta5-1ubuntu1), libglamor0:i386 (0.5.1-0ubuntu7, automatic), lubuntu-lxpanel-icons:i386 (0.42, automatic), evince:i386 (3.10.3-0ubuntu1), foomatic-db-compressed-ppds:i386 (20130912-1fakesync1), linux-headers-3.12.0-4-generic:i386 (3.12.0-4.12, automatic), libmtdev1:i386 (1.1.4-1ubuntu1, automatic), libnuma1:i386 (2.0.9~rc5-1), python-dbus-dev:i386 (1.2.0-2, automatic), python-gudev:i386 (147.2-3), python3-xkit:i386 (0.5.0ubuntu1, automatic), udisks:i386 (1.0.4-8ubuntu1), xul-ext-ubufox:i386 (2.8-0ubuntu1), libgck-1-0:i386 (3.10.1-1), libunity-protocol-private0:i386 (7.1.3+14.04.20131106-0ubuntu1), xserver-xorg-video-trident:i386 (1.3.6-0ubuntu4, automatic), im-config:i386 (0.21ubuntu4), ntfs-3g:i386 (2013.1.13AR.1-2ubuntu1), pidgin-data:i386 (2.10.7-0ubuntu4.2), ufw:i386 (0.33-0ubuntu4), libvorbisenc2:i386 (1.3.2-1.3), xserver-xorg:i386 (7.7+1ubuntu6, automatic), libgphoto2-port10:i386 (2.5.2-0ubuntu5, automatic), rsync:i386 (3.1.0-2), aspell:i386 (0.60.7~20110707-1build1), liboobs-1-5:i386 (3.0.0-1), libtag1c2a:i386 (1.9.1-2), libtheora0:i386 (1.1.1+dfsg.1-3.1), libindicator3-7:i386 (12.10.2+14.04.20131125-0ubuntu1), libxcb1:i386 (1.9.1-3ubuntu1), libpipeline1:i386 (1.2.4-1), xserver-xorg-input-mouse:i386 (1.9.0-1, automatic), libudisks2-0:i386 (2.1.1-1), libasound2-data:i386 (1.0.27.2-3ubuntu1, automatic), dconf-gsettings-backend:i386 (0.18.0-1, automatic), info:i386 (5.1.dfsg.1-4ubuntu1), libevdocument3-4:i386 (3.10.3-0ubuntu1), libwbclient0:i386 (4.0.10+dfsg-4ubuntu2, automatic), libxfconf-0-2:i386 (4.10.0-2), librasqal3:i386 (0.9.30-1), policykit-1:i386 (0.105-4ubuntu1, automatic), libxvidcore4:i386 (1.3.2-9ubuntu1), guvcview:i386 (1.7.1-1ubuntu1), lxmenu-data:i386 (0.1.2-2, automatic), libyajl2:i386 (2.0.4-4), xserver-xorg-video-ati:i386 (7.2.0-0ubuntu10, automatic), libpulse-mainloop-glib0:i386 (4.0-0ubuntu6), libmodplug1:i386 (0.8.8.4-4), libpaper1:i386 (1.1.24+nmu2ubuntu2, automatic), libidn11:i386 (1.28-1ubuntu1), openprinting-ppds:i386 (20130912-1fakesync1), pcmanfm:i386 (1.1.2-1, automatic), usbmuxd:i386 (1.0.8-2ubuntu1), python3-gi:i386 (3.10.2-1), usb-creator-common:i386 (0.2.50), libavformat54:i386 (9.10-1ubuntu1), powermgmt-base:i386 (1.31build1), indicator-application-gtk2:i386 (12.10.0.1-0ubuntu2), libindicator7:i386 (12.10.2+14.04.20131125-0ubuntu1), libots0:i386 (0.5.0-2.1ubuntu1), ghostscript-x:i386 (9.10~dfsg-0ubuntu3), libwnck-3-common:i386 (3.4.7-0ubuntu2), libhtml-tagset-perl:i386 (3.20-2), gnome-disk-utility:i386 (3.10.0-1ubuntu1), libpangoxft-1.0-0:i386 (1.36.0-1ubuntu1, automatic), gnumeric-common:i386 (1.12.6-2), libedataserver-1.2-18:i386 (3.10.1-2ubuntu2), libelfg0:i386 (0.8.13-4, automatic), foomatic-filters:i386 (4.0.17-1ubuntu1), libnatpmp1:i386 (20110808-3ubuntu2), cpp-4.8:i386 (4.8.2-1ubuntu2, automatic), xauth:i386 (1.0.7-1ubuntu1), glib-networking:i386 (2.38.1-1), liblvm2app2.2:i386 (2.02.98-6ubuntu1), dictionaries-common:i386 (1.20.4), gvfs-fuse:i386 (1.19.2-0ubuntu1), libio-html-perl:i386 (1.00-1), cups-daemon:i386 (1.7.0-0ubuntu2, automatic), libavcodec54:i386 (9.10-1ubuntu1), libwnck-3-0:i386 (3.4.7-0ubuntu2), gconf2-common:i386 (3.2.6-0ubuntu1), libgsm1:i386 (1.0.13-4), irqbalance:i386 (1.0.6-2), libspectre1:i386 (0.2.7-2), librsvg2-common:i386 (2.40.0-1, automatic), lxpanel-indicator-applet-plugin:i386 (0.6.1-0ubuntu1), gvfs-backends:i386 (1.19.2-0ubuntu1), libcairo2:i386 (1.12.16-0ubuntu2, automatic), python3-defer:i386 (1.0.6-2, automatic), liblwp-protocol-https-perl:i386 (6.04-1), xserver-xorg-input-vmmouse:i386 (13.0.0-1, automatic), zip:i386 (3.0-8, automatic), mtr-tiny:i386 (0.85-2), p11-kit:i386 (0.20.1-2ubuntu1), apparmor:i386 (2.8.0-0ubuntu34), libwind0-heimdal:i386 (1.6~git20120403+dfsg1-3ubuntu0.2), xserver-xorg-glamoregl:i386 (0.5.1-0ubuntu7, automatic), libnet-ssleay-perl:i386 (1.55-1build1, automatic), libgpod4:i386 (0.8.2-7ubuntu4), libthai0:i386 (0.1.20-1, automatic), gtk2-engines:i386 (2.20.2-2ubuntu2, automatic), libimlib2:i386 (1.4.5-1ubuntu2, automatic), libgtk-3-common:i386 (3.8.7-0ubuntu1, automatic), gvfs-common:i386 (1.19.2-0ubuntu1), libfontenc1:i386 (1.1.2-1, automatic), syslinux:i386 (4.05+dfsg-6+deb7u3ubuntu1), bc:i386 (1.06.95-8, automatic), gtk2-engines-murrine:i386 (0.98.2-0ubuntu2, automatic), libxi6:i386 (1.7.1.901-1ubuntu1, automatic), libgsf-1-114:i386 (1.14.27-2ubuntu1), zenity-common:i386 (3.8.0-1), librtmp0:i386 (2.4+20121230.gitdf6c518-1), libgtkspell0:i386 (2.0.16-1ubuntu6), libexo-1-0:i386 (0.10.2-2), libwayland-cursor0:i386 (1.3.0-1, automatic), libpci3:i386 (3.1.9-6ubuntu11), aspell-en:i386 (7.1-0-1), libschroedinger-1.0-0:i386 (1.0.11-2), liba52-0.7.4:i386 (0.7.4-16build1), ubuntu-extras-keyring:i386 (2010.09.27), zram-config:i386 (0.1), command-not-found:i386 (0.3ubuntu8), cups-client:i386 (1.7.0-0ubuntu2, automatic), gksu:i386 (2.0.2-6ubuntu2), libaudclient2:i386 (3.4.1-1), libvpx1:i386 (1.2.0-2, automatic), libpisock9:i386 (0.12.5-6ubuntu1), libavahi-core7:i386 (0.6.31-2ubuntu5, automatic), libgl1-mesa-glx:i386 (9.2.2-1ubuntu1, automatic), python3-distupgrade:i386 (0.209), libnotify4:i386 (0.7.6-1ubuntu1), at-spi2-core:i386 (2.10.1-0ubuntu1), libheimntlm0-heimdal:i386 (1.6~git20120403+dfsg1-3ubuntu0.2), apt-transport-https:i386 (0.9.13.1~ubuntu1), xdg-utils:i386 (1.1.0~rc1-2ubuntu7), libgudev-1.0-0:i386 (204-5ubuntu6, automatic), python3-aptdaemon:i386 (1.1.1-1ubuntu1, automatic), fonts-dejavu-core:i386 (2.33+svn2514-3ubuntu1, automatic)
End-Date: 2013-11-29  16:46:47

Start-Date: 2013-11-29  16:47:02
Commandline: apt-get --yes --no-install-recommends install lupin-casper apt-clone archdetect-deb b43-fwcutter cryptsetup cryptsetup-bin dmraid dpkg-repack ecryptfs-utils firefox-locale-bn firefox-locale-cs firefox-locale-de firefox-locale-en firefox-locale-es firefox-locale-fr firefox-locale-hu firefox-locale-it firefox-locale-ja firefox-locale-nl firefox-locale-pl firefox-locale-pt firefox-locale-ru firefox-locale-zh-hans gir1.2-appindicator3-0.1 gir1.2-json-1.0 gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 gparted grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common keyutils kpartx kpartx-boot language-pack-bn language-pack-bn-base language-pack-cs language-pack-cs-base language-pack-de language-pack-de-base language-pack-en language-pack-en-base language-pack-es language-pack-es-base language-pack-fr language-pack-fr-base language-pack-gnome-bn language-pack-gnome-bn-base language-pack-gnome-cs language-pack-gnome-cs-base language-pack-gnome-de language-pack-gnome-de-base language-pack-gnome-en language-pack-gnome-en-base language-pack-gnome-es language-pack-gnome-es-base language-pack-gnome-fr language-pack-gnome-fr-base language-pack-gnome-hu language-pack-gnome-hu-base language-pack-gnome-it language-pack-gnome-it-base language-pack-gnome-ja language-pack-gnome-ja-base language-pack-gnome-nl language-pack-gnome-nl-base language-pack-gnome-pl language-pack-gnome-pl-base language-pack-gnome-pt language-pack-gnome-pt-base language-pack-gnome-ru language-pack-gnome-ru-base language-pack-gnome-xh language-pack-gnome-xh-base language-pack-gnome-zh-hans language-pack-gnome-zh-hans-base language-pack-hu language-pack-hu-base language-pack-it language-pack-it-base language-pack-ja language-pack-ja-base language-pack-nl language-pack-nl-base language-pack-pl language-pack-pl-base language-pack-pt language-pack-pt-base language-pack-ru language-pack-ru-base language-pack-xh language-pack-xh-base language-pack-zh-hans language-pack-zh-hans-base libatkmm-1.6-1 libatm1 libcairomm-1.0-1 libcryptsetup4 libdebconfclient0 libdebian-installer4 libdmraid1.0.0.rc16 libecryptfs0 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libido3-0.1-0 libnss3-1d libpangomm-1.4-1 libpython3.3 libsigc++-2.0-0c2a libtimezonemap1 lvm2 os-prober pptp-linux python3-cairo python3-gi-cairo python3-icu python3-pam rdate setserial ubiquity ubiquity-casper ubiquity-frontend-gtk ubiquity-ubuntu-artwork watershed feh libjpeg-progs libjpeg-turbo-progs linux-wlan-ng linux-wlan-ng-doc ubiquity-slideshow-lubuntu
Install: casper:i386 (1.336ubuntu1, automatic), firefox-locale-pl:i386 (25.0+build3-0ubuntu0.13.10.1), firefox-locale-pt:i386 (25.0+build3-0ubuntu0.13.10.1), ecryptfs-utils:i386 (103-0ubuntu2), gparted:i386 (0.16.2-1ubuntu1), ubiquity-frontend-gtk:i386 (2.17.0), language-pack-zh-hans-base:i386 (13.10+20131012), language-pack-gnome-ru-base:i386 (13.10+20131012), ubiquity-slideshow-lubuntu:i386 (75), cryptsetup-bin:i386 (1.6.1-1ubuntu1), gir1.2-timezonemap-1.0:i386 (0.4.1), libido3-0.1-0:i386 (13.10.0+14.04.20131127-0ubuntu1), lvm2:i386 (2.02.98-6ubuntu1), firefox-locale-ru:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-pl-base:i386 (13.10+20131012), language-pack-gnome-fr-base:i386 (13.10+20131012), dmraid:i386 (1.0.0.rc16-4.2ubuntu1), lupin-casper:i386 (0.55), dpkg-repack:i386 (1.37), pptp-linux:i386 (1.7.2-7), language-pack-de-base:i386 (13.10+20131012), keyutils:i386 (1.5.6-1), language-pack-gnome-bn-base:i386 (13.10+20131012), language-pack-gnome-pt-base:i386 (13.10+20131012), user-setup:i386 (1.48ubuntu1, automatic), language-pack-ru-base:i386 (13.10+20131012), language-pack-fr-base:i386 (13.10+20131012), gir1.2-json-1.0:i386 (0.16.2-1), libtimezonemap1:i386 (0.4.1), grub-gfxpayload-lists:i386 (0.6), language-pack-bn-base:i386 (13.10+20131012), language-pack-cs-base:i386 (13.10+20131012), grub-common:i386 (2.00-20), python3-gi-cairo:i386 (3.10.2-1), libatkmm-1.6-1:i386 (2.22.7-2), language-pack-pt-base:i386 (13.10+20131012), laptop-detect:i386 (0.13.7ubuntu2, automatic), os-prober:i386 (1.61ubuntu1), apt-clone:i386 (0.3.1~ubuntu6), libcryptsetup4:i386 (1.6.1-1ubuntu1), language-pack-gnome-it-base:i386 (13.10+20131012), language-pack-xh-base:i386 (13.10+20131012), grub-pc:i386 (2.00-20), samba-common:i386 (4.0.10+dfsg-4ubuntu2, automatic), libdebconfclient0:i386 (0.185ubuntu1), libjpeg-progs:i386 (8c-2ubuntu8), firefox-locale-zh-hans:i386 (25.0+build3-0ubuntu0.13.10.1), libatm1:i386 (2.5.1-1.5), ubiquity:i386 (2.17.0), python3-pam:i386 (0.4.2-13.1ubuntu1), language-pack-gnome-es-base:i386 (13.10+20131012), language-pack-it-base:i386 (13.10+20131012), language-pack-gnome-bn:i386 (13.10+20131012), language-pack-gnome-cs-base:i386 (13.10+20131012), rdate:i386 (1.2-5), language-pack-gnome-cs:i386 (13.10+20131012), language-pack-bn:i386 (13.10+20131012), gir1.2-appindicator3-0.1:i386 (12.10.1+13.10.20130920-0ubuntu2), archdetect-deb:i386 (1.95ubuntu1), language-pack-gnome-de:i386 (13.10+20131012), libdmraid1.0.0.rc16:i386 (1.0.0.rc16-4.2ubuntu1), cryptsetup:i386 (1.6.1-1ubuntu1), language-pack-cs:i386 (13.10+20131012), language-pack-gnome-en:i386 (13.10+20131012), linux-wlan-ng-doc:i386 (0.2.9+dfsg-5), language-pack-de:i386 (13.10+20131012), language-pack-gnome-es:i386 (13.10+20131012), libjpeg-turbo-progs:i386 (1.3.0-0ubuntu1), language-pack-gnome-fr:i386 (13.10+20131012), language-pack-en:i386 (13.10+20131012), kpartx-boot:i386 (0.4.9-3ubuntu7), libglibmm-2.4-1c2a:i386 (2.38.1-0ubuntu1), language-pack-es:i386 (13.10+20131012), language-pack-gnome-xh-base:i386 (13.10+20131012), libpython3.3:i386 (3.3.3-3), language-pack-fr:i386 (13.10+20131012), cifs-utils:i386 (6.0-1ubuntu2, automatic), language-pack-gnome-zh-hans-base:i386 (13.10+20131012), language-pack-gnome-hu:i386 (13.10+20131012), linux-wlan-ng:i386 (0.2.9+dfsg-5), grub2-common:i386 (2.00-20), grub-pc-bin:i386 (2.00-20), language-pack-es-base:i386 (13.10+20131012), language-pack-gnome-it:i386 (13.10+20131012), language-pack-hu:i386 (13.10+20131012), language-pack-gnome-ja-base:i386 (13.10+20131012), language-pack-gnome-ja:i386 (13.10+20131012), language-pack-it:i386 (13.10+20131012), libecryptfs0:i386 (103-0ubuntu2), language-pack-ja:i386 (13.10+20131012), ubiquity-casper:i386 (1.336ubuntu1), libcairomm-1.0-1:i386 (1.10.0-1ubuntu2), libnss3-1d:i386 (3.15.3-1), language-pack-nl-base:i386 (13.10+20131012), language-pack-en-base:i386 (13.10+20131012), watershed:i386 (7), language-pack-gnome-nl:i386 (13.10+20131012), firefox-locale-bn:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-nl:i386 (13.10+20131012), firefox-locale-cs:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-gnome-hu-base:i386 (13.10+20131012), language-pack-gnome-zh-hans:i386 (13.10+20131012), binutils:i386 (2.23.91.20131123-1ubuntu1, automatic), language-pack-gnome-pl:i386 (13.10+20131012), firefox-locale-de:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-gnome-pt:i386 (13.10+20131012), setserial:i386 (2.17-48), kpartx:i386 (0.4.9-3ubuntu7), libpangomm-1.4-1:i386 (2.34.0-1), language-pack-ja-base:i386 (13.10+20131012), firefox-locale-en:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-pl:i386 (13.10+20131012), firefox-locale-es:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-pt:i386 (13.10+20131012), localechooser-data:i386 (2.49ubuntu4, automatic), language-pack-gnome-ru:i386 (13.10+20131012), feh:i386 (2.3-2), firefox-locale-fr:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-ru:i386 (13.10+20131012), libgtkmm-2.4-1c2a:i386 (2.24.4-1), firefox-locale-hu:i386 (25.0+build3-0ubuntu0.13.10.1), libdebian-installer4:i386 (0.88ubuntu1), firefox-locale-it:i386 (25.0+build3-0ubuntu0.13.10.1), firefox-locale-ja:i386 (25.0+build3-0ubuntu0.13.10.1), python3-icu:i386 (1.5-2ubuntu2), python3-cairo:i386 (1.10.0+dfsg-3), libsigc++-2.0-0c2a:i386 (2.2.10-0.2ubuntu1), language-pack-hu-base:i386 (13.10+20131012), language-pack-zh-hans:i386 (13.10+20131012), ubiquity-ubuntu-artwork:i386 (2.17.0), language-pack-gnome-pl-base:i386 (13.10+20131012), language-pack-gnome-xh:i386 (13.10+20131012), b43-fwcutter:i386 (018-2), language-pack-gnome-nl-base:i386 (13.10+20131012), language-pack-gnome-de-base:i386 (13.10+20131012), language-pack-xh:i386 (13.10+20131012), gir1.2-xkl-1.0:i386 (5.2.1-1ubuntu2), language-pack-gnome-en-base:i386 (13.10+20131012), firefox-locale-nl:i386 (25.0+build3-0ubuntu0.13.10.1)
End-Date: 2013-11-29  16:48:37

Start-Date: 2013-11-30  08:17:21
Install: wamerican:i386 (7.1-1), hunspell-en-us:i386 (20070829-4ubuntu3), wbritish:i386 (7.1-1)
End-Date: 2013-11-30  08:17:44

Start-Date: 2013-11-30  08:19:08
End-Date: 2013-11-30  08:19:09

Start-Date: 2013-11-30  08:21:12
Purge: casper:i386 (1.336ubuntu1), firefox-locale-pl:i386 (25.0+build3-0ubuntu0.13.10.1), firefox-locale-pt:i386 (25.0+build3-0ubuntu0.13.10.1), ecryptfs-utils:i386 (103-0ubuntu2), gparted:i386 (0.16.2-1ubuntu1), ubiquity-frontend-gtk:i386 (2.17.0), language-pack-zh-hans-base:i386 (13.10+20131012), language-pack-gnome-ru-base:i386 (13.10+20131012), ubiquity-slideshow-lubuntu:i386 (75), cryptsetup-bin:i386 (1.6.1-1ubuntu1), gir1.2-timezonemap-1.0:i386 (0.4.1), lvm2:i386 (2.02.98-6ubuntu1), firefox-locale-ru:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-pl-base:i386 (13.10+20131012), language-pack-gnome-fr-base:i386 (13.10+20131012), dmraid:i386 (1.0.0.rc16-4.2ubuntu1), lupin-casper:i386 (0.55), dpkg-repack:i386 (1.37), pptp-linux:i386 (1.7.2-7), language-pack-de-base:i386 (13.10+20131012), keyutils:i386 (1.5.6-1), language-pack-gnome-bn-base:i386 (13.10+20131012), language-pack-gnome-pt-base:i386 (13.10+20131012), user-setup:i386 (1.48ubuntu1), language-pack-ru-base:i386 (13.10+20131012), language-pack-fr-base:i386 (13.10+20131012), gir1.2-json-1.0:i386 (0.16.2-1), libtimezonemap1:i386 (0.4.1), language-pack-bn-base:i386 (13.10+20131012), language-pack-cs-base:i386 (13.10+20131012), python3-gi-cairo:i386 (3.10.2-1), language-pack-pt-base:i386 (13.10+20131012), laptop-detect:i386 (0.13.7ubuntu2), apt-clone:i386 (0.3.1~ubuntu6), libcryptsetup4:i386 (1.6.1-1ubuntu1), language-pack-gnome-it-base:i386 (13.10+20131012), language-pack-xh-base:i386 (13.10+20131012), samba-common:i386 (4.0.10+dfsg-4ubuntu2), libdebconfclient0:i386 (0.185ubuntu1), libjpeg-progs:i386 (8c-2ubuntu8), firefox-locale-zh-hans:i386 (25.0+build3-0ubuntu0.13.10.1), ubiquity:i386 (2.17.0), python3-pam:i386 (0.4.2-13.1ubuntu1), language-pack-gnome-es-base:i386 (13.10+20131012), language-pack-it-base:i386 (13.10+20131012), language-pack-gnome-bn:i386 (13.10+20131012), language-pack-gnome-cs-base:i386 (13.10+20131012), rdate:i386 (1.2-5), language-pack-gnome-cs:i386 (13.10+20131012), language-pack-bn:i386 (13.10+20131012), gir1.2-appindicator3-0.1:i386 (12.10.1+13.10.20130920-0ubuntu2), archdetect-deb:i386 (1.95ubuntu1), language-pack-gnome-de:i386 (13.10+20131012), libdmraid1.0.0.rc16:i386 (1.0.0.rc16-4.2ubuntu1), cryptsetup:i386 (1.6.1-1ubuntu1), language-pack-cs:i386 (13.10+20131012), linux-wlan-ng-doc:i386 (0.2.9+dfsg-5), language-pack-de:i386 (13.10+20131012), language-pack-gnome-es:i386 (13.10+20131012), libjpeg-turbo-progs:i386 (1.3.0-0ubuntu1), language-pack-gnome-fr:i386 (13.10+20131012), kpartx-boot:i386 (0.4.9-3ubuntu7), language-pack-es:i386 (13.10+20131012), language-pack-gnome-xh-base:i386 (13.10+20131012), language-pack-fr:i386 (13.10+20131012), cifs-utils:i386 (6.0-1ubuntu2), language-pack-gnome-zh-hans-base:i386 (13.10+20131012), language-pack-gnome-hu:i386 (13.10+20131012), linux-wlan-ng:i386 (0.2.9+dfsg-5), language-pack-es-base:i386 (13.10+20131012), language-pack-gnome-it:i386 (13.10+20131012), language-pack-hu:i386 (13.10+20131012), language-pack-gnome-ja-base:i386 (13.10+20131012), language-pack-gnome-ja:i386 (13.10+20131012), language-pack-it:i386 (13.10+20131012), libecryptfs0:i386 (103-0ubuntu2), language-pack-ja:i386 (13.10+20131012), ubiquity-casper:i386 (1.336ubuntu1), language-pack-nl-base:i386 (13.10+20131012), watershed:i386 (7), language-pack-gnome-nl:i386 (13.10+20131012), firefox-locale-bn:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-nl:i386 (13.10+20131012), firefox-locale-cs:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-gnome-hu-base:i386 (13.10+20131012), language-pack-gnome-zh-hans:i386 (13.10+20131012), binutils:i386 (2.23.91.20131123-1ubuntu1), language-pack-gnome-pl:i386 (13.10+20131012), firefox-locale-de:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-gnome-pt:i386 (13.10+20131012), setserial:i386 (2.17-48), kpartx:i386 (0.4.9-3ubuntu7), language-pack-ja-base:i386 (13.10+20131012), language-pack-pl:i386 (13.10+20131012), firefox-locale-es:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-pt:i386 (13.10+20131012), localechooser-data:i386 (2.49ubuntu4), language-pack-gnome-ru:i386 (13.10+20131012), feh:i386 (2.3-2), firefox-locale-fr:i386 (25.0+build3-0ubuntu0.13.10.1), language-pack-ru:i386 (13.10+20131012), firefox-locale-hu:i386 (25.0+build3-0ubuntu0.13.10.1), firefox-locale-it:i386 (25.0+build3-0ubuntu0.13.10.1), firefox-locale-ja:i386 (25.0+build3-0ubuntu0.13.10.1), python3-icu:i386 (1.5-2ubuntu2), python3-cairo:i386 (1.10.0+dfsg-3), language-pack-hu-base:i386 (13.10+20131012), language-pack-zh-hans:i386 (13.10+20131012), ubiquity-ubuntu-artwork:i386 (2.17.0), language-pack-gnome-pl-base:i386 (13.10+20131012), language-pack-gnome-xh:i386 (13.10+20131012), b43-fwcutter:i386 (018-2), language-pack-gnome-nl-base:i386 (13.10+20131012), language-pack-gnome-de-base:i386 (13.10+20131012), language-pack-xh:i386 (13.10+20131012), gir1.2-xkl-1.0:i386 (5.2.1-1ubuntu2), firefox-locale-nl:i386 (25.0+build3-0ubuntu0.13.10.1)
End-Date: 2013-11-30  08:24:25

Start-Date: 2013-11-30  08:24:29
End-Date: 2013-11-30  08:24:29

Start-Date: 2013-11-30  08:25:30
Install: gstreamer1.0-fluendo-mp3:i386 (0.10.23.debian-3), libopenal1:i386 (1.14-4ubuntu1, automatic), freepats:i386 (20060219-1, automatic), libgstreamer-plugins-bad1.0-0:i386 (1.2.1-1ubuntu1, automatic), libspandsp2:i386 (0.0.6~pre21-1ubuntu2, automatic), libzvbi0:i386 (0.2.35-2, automatic), gstreamer0.10-plugins-bad:i386 (0.10.23-7ubuntu2), libzvbi-common:i386 (0.2.35-2, automatic), libchromaprint0:i386 (0.7-2build1, automatic), libgstreamer-plugins-good1.0-0:i386 (1.2.1-1ubuntu1, automatic), gstreamer0.10-plugins-ugly:i386 (0.10.19-2), libwildmidi1:i386 (0.2.3.4-2.1ubuntu2, automatic), libfftw3-single3:i386 (3.3.3-5ubuntu1, automatic), ubuntu-restricted-addons:i386 (17), gstreamer1.0-plugins-ugly:i386 (1.2.1-1), libflite1:i386 (1.4-release-7, automatic), libofa0:i386 (0.9.3-5, automatic), libfftw3-double3:i386 (3.3.3-5ubuntu1, automatic), libdc1394-22:i386 (2.2.1-2, automatic), libopencore-amrnb0:i386 (0.1.3-2, automatic), libkate1:i386 (0.4.1-1, automatic), libcdaudio1:i386 (0.99.12p2-13, automatic), libvo-aacenc0:i386 (0.1.3-1, automatic), libtwolame0:i386 (0.3.13-1build1, automatic), libsidplay1:i386 (1.36.59-5ubuntu1, automatic), libfftw3-3:i386 (3.3.3-5ubuntu1, automatic), libslv2-9:i386 (0.6.6+dfsg1-2, automatic), libgles2-mesa:i386 (9.2.2-1ubuntu1, automatic), libopenal-data:i386 (1.14-4ubuntu1, automatic), libwildmidi-config:i386 (0.2.3.4-2.1ubuntu2, automatic), libopencore-amrwb0:i386 (0.1.3-2, automatic), libsbc1:i386 (1.1-2, automatic), libgomp1:i386 (4.8.2-1ubuntu2, automatic), chromium-codecs-ffmpeg-extra:i386 (29.0.1547.65-0ubuntu2), libspeexdsp1:i386 (1.2~rc1-7ubuntu2, automatic), gstreamer0.10-fluendo-mp3:i386 (0.10.23.debian-3), libgstreamer-plugins-bad0.10-0:i386 (0.10.23-7ubuntu2, automatic), libmimic0:i386 (1.0.4-2.1build1, automatic), libnspr4-0d:i386 (4.9.5-1ubuntu1, automatic), gstreamer1.0-plugins-base:i386 (1.2.1-2ubuntu1, automatic), libzbar0:i386 (0.10+doc-9build1, automatic), flashplugin-installer:i386 (11.2.202.327ubuntu0.13.10.1), libdirac-encoder0:i386 (1.0.2-6ubuntu1, automatic), libvo-amrwbenc0:i386 (0.1.3-1, automatic), libmpcdec6:i386 (0.1~r459-1ubuntu1, automatic), gstreamer1.0-libav:i386 (1.2.1-1), libasound2-plugins:i386 (1.0.27-2ubuntu2, automatic), libmpeg2-4:i386 (0.5.1-5, automatic), libsoundtouch0:i386 (1.7.1-4, automatic), libgme0:i386 (0.5.5-2, automatic), gstreamer1.0-plugins-bad:i386 (1.2.1-1ubuntu1), liboil0.3:i386 (0.3.17-2ubuntu3, automatic), libsrtp0:i386 (1.4.5~20130609~dfsg-1, automatic)
End-Date: 2013-11-30  08:26:47

Start-Date: 2013-11-30  09:58:28
Commandline: /usr/sbin/synaptic
Upgrade: libglib2.0-data:i386 (2.39.1-0ubuntu1, 2.39.1-0ubuntu2), libapparmor1:i386 (2.8.0-0ubuntu34, 2.8.0-0ubuntu35), initscripts:i386 (2.88dsf-41ubuntu3, 2.88dsf-41ubuntu4), libgraphite2-3:i386 (1.2.3-1, 1.2.4-1), sysv-rc:i386 (2.88dsf-41ubuntu3, 2.88dsf-41ubuntu4), libtimedate-perl:i386 (1.2000-1, 2.3000-1), libglib2.0-0:i386 (2.39.1-0ubuntu1, 2.39.1-0ubuntu2), libapparmor-perl:i386 (2.8.0-0ubuntu34, 2.8.0-0ubuntu35), libglib2.0-bin:i386 (2.39.1-0ubuntu1, 2.39.1-0ubuntu2), sysvinit-utils:i386 (2.88dsf-41ubuntu3, 2.88dsf-41ubuntu4), foomatic-db-compressed-ppds:i386 (20130912-1fakesync1, 20131129-1), openprinting-ppds:i386 (20130912-1fakesync1, 20131129-1), apparmor:i386 (2.8.0-0ubuntu34, 2.8.0-0ubuntu35)
End-Date: 2013-11-30  09:59:56

Start-Date: 2013-11-30  11:46:38
Commandline: /usr/sbin/synaptic
Install: grub:i386 (0.97-29ubuntu66)
Purge: grub-gfxpayload-lists:i386 (0.6), grub-pc:i386 (2.00-20), grub2-common:i386 (2.00-20)
End-Date: 2013-11-30  11:46:55

Start-Date: 2013-12-02  10:21:40
Commandline: /usr/sbin/synaptic
Upgrade: nautilus-data:i386 (3.8.2-0ubuntu3, 3.8.2-0ubuntu4), libpcap0.8:i386 (1.4.0-2, 1.5.1-1), libwww-perl:i386 (6.05-1, 6.05-2), libnautilus-extension1a:i386 (3.8.2-0ubuntu3, 3.8.2-0ubuntu4), libnm-gtk0:i386 (0.9.8.0-1ubuntu5, 0.9.8.0-1ubuntu6), network-manager-gnome:i386 (0.9.8.0-1ubuntu5, 0.9.8.0-1ubuntu6), xserver-xorg-input-evdev:i386 (2.7.3-0ubuntu3.1, 2.8.2-1ubuntu1), libnm-gtk-common:i386 (0.9.8.0-1ubuntu5, 0.9.8.0-1ubuntu6), libelfg0:i386 (0.8.13-4, 0.8.13-5), liblwp-protocol-https-perl:i386 (6.04-1, 6.04-2)
End-Date: 2013-12-02  10:22:29

Start-Date: 2013-12-02  17:42:55
Commandline: /usr/sbin/synaptic
Upgrade: usb-creator-gtk:i386 (0.2.50, 0.2.51), usb-creator-common:i386 (0.2.50, 0.2.51)
End-Date: 2013-12-02  17:43:06
```

---

### Post by kansasnoob on 2013-12-05
> **zika said:**
> I'm obviously missing something about grub(2) but its late and it is not important since You're happy with Your config so...
Read You next morning, or better to say noon, after some proper work done.

I understand "proper work". I messed up and left some irrigation tubing lying on the ground until after the hard freeze :(

It will expand enough to deal with freezing but deer use this area to migrate and their hooves will shatter it if I don't get it thawed and put up properly.

So what should have been two hours work turned into a weeks worth of bone-chilling work ............ just because I forgot!

---

### Post by zika on 2013-12-06
> **kansasnoob said:**
> I understand "proper work". I messed up and left some irrigation tubing lying on the ground until after the hard freeze :(

It will expand enough to deal with freezing but deer use this area to migrate and their hooves will shatter it if I don't get it thawed and put up properly.

So what should have been two hours work turned into a weeks worth of bone-chilling work ............ just because I forgot!Just be patient and persistent... You will not forget it next winter... ;)
I'm keeping my fingers crossed for You...

---

### Post by kansasnoob on 2013-12-06
****Regarding that grub thing, which is off-topic, here's an example after installing Lubuntu 20131205 i386:

```
lance@lance-desktop:~$ cat /boot/grub/grub.cfg | grep menuentry
menuentry 'Ubuntu, with Linux 3.2.0-57-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-57-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-56-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-56-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-55-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-55-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-54-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-54-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-53-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-53-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-52-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-52-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-51-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-51-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-49-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-49-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-48-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-48-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-45-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-45-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-44-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-44-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-43-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-43-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-41-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-41-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-40-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.2.0-40-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-5-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-5-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-4-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-4-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-3-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-3-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-2-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-2-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-1-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-1-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.11.0-12-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.11.0-12-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), memtest86+ (on /dev/sda1)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, kernel 3.11.0-13-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, kernel 3.11.0-13-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, kernel 3.11.0-12-generic (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, kernel 3.11.0-12-generic (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, memtest86+ (on /dev/sda10)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-4-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-4-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), memtest86+ (on /dev/sda11)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-43-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 12.10, kernel 3.5.0-43-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.04, kernel 3.8.0-33-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.04, kernel 3.8.0-33-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, kernel 3.11.0-13-generic (on /dev/sda14)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, kernel 3.11.0-13-generic (recovery mode) (on /dev/sda14)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, kernel 3.11.0-12-generic (on /dev/sda14)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, kernel 3.11.0-12-generic (recovery mode) (on /dev/sda14)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, memtest86+ (on /dev/sda14)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.04, kernel 3.8.0-33-generic (on /dev/sda15)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.04, kernel 3.8.0-33-generic (recovery mode) (on /dev/sda15)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-5-generic (on /dev/sda16)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-5-generic (recovery mode) (on /dev/sda16)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-4-generic (on /dev/sda16)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-4-generic (recovery mode) (on /dev/sda16)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), memtest86+ (on /dev/sda16)" --class gnu-linux --class gnu --class os {
[B][COLOR="#FF0000"]menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-4f7a8d0e-7d87-4d24-82ef-81ad7c06f150 (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.12.0-5-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.12.0-5-generic-advanced-4f7a8d0e-7d87-4d24-82ef-81ad7c06f150 (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu, with Linux 3.12.0-5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.12.0-5-generic-recovery-4f7a8d0e-7d87-4d24-82ef-81ad7c06f150 (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch) (14.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-f49bbc53-3369-47cf-89ae-c25795762898 (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-5-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.12.0-5-generic--f49bbc53-3369-47cf-89ae-c25795762898 (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-5-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.12.0-5-generic-root=UUID=f49bbc53-3369-47cf-89ae-c25795762898 ro single-f49bbc53-3369-47cf-89ae-c25795762898 (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), memtest86+ (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--f49bbc53-3369-47cf-89ae-c25795762898 (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, memtest86+ (on /dev/sda10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--c6d1da41-e700-4278-b8e7-4d470e8df6ac (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), memtest86+ (on /dev/sda11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--a74a6c45-9501-4e55-b40e-84b4f0cd5019 (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, memtest86+ (on /dev/sda14)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--0187ffde-3293-4161-a6d5-3a9d82a7210a (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch) (14.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-02f5697f-b002-4f2f-acb0-4014f05c4d33 (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-5-generic (on /dev/sda16)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.12.0-5-generic--02f5697f-b002-4f2f-acb0-4014f05c4d33 (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), kernel 3.12.0-5-generic (recovery mode) (on /dev/sda16)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.12.0-5-generic-root=UUID=02f5697f-b002-4f2f-acb0-4014f05c4d33 ro single-02f5697f-b002-4f2f-acb0-4014f05c4d33 (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu Trusty Tahr (development branch), memtest86+ (on /dev/sda16)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--02f5697f-b002-4f2f-acb0-4014f05c4d33 (on /dev/sda17)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, memtest86+ (on /dev/sda3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/memtest86+.bin--c646b420-fe32-4894-9c54-37877c9891cd (on /dev/sda17)" --class gnu-linux --class gnu --class os {[/COLOR][/B]
menuentry "Ubuntu 13.04, kernel 3.8.0-27-generic (on /dev/sda18)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.04, kernel 3.8.0-27-generic (recovery mode) (on /dev/sda18)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, kernel 3.11.0-13-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, kernel 3.11.0-13-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, kernel 3.11.0-12-generic (on /dev/sda3)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, kernel 3.11.0-12-generic (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
menuentry "Ubuntu 13.10, memtest86+ (on /dev/sda3)" --class gnu-linux --class gnu --class os {

```

The garbled mess is highlighted ;)

But since that's off-topic I wish you would open a new thread instead of discussing it here. I know Colin Watson has no intention of fixing it.

---

