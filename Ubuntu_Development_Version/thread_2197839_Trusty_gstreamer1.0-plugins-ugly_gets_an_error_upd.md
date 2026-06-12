---
title: "Trusty gstreamer1.0-plugins-ugly gets an error updating"
date: 2014-01-05
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-01-05
I got some updates a while ago and also got this error along with them:

```
(Reading database ... 247293 files and directories currently installed.)
Unpacking gstreamer1.0-plugins-ugly:amd64 (from .../gstreamer1.0-plugins-ugly_1.2.2-1ubuntu2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/gstreamer1.0-plugins-ugly_1.2.2-1ubuntu2_amd64.deb (--unpack):
 trying to overwrite '/usr/share/locale/sl/LC_MESSAGES/.mo', which is also in package gstreamer0.10-plugins-ugly:amd64 0.10.19-2ubuntu2
Errors were encountered while processing:
 /var/cache/apt/archives/gstreamer1.0-plugins-ugly_1.2.2-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Tried the following to no avail:
```
$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update
```

---

### Post by Cavsfan on 2014-01-05
I see from this that the package is in Proposed although I do not have Proposed software sources checked. :???:
[https://launchpad.net/ubuntu/+source/gst-plugins-ugly1.0/1.2.2-1ubuntu2/+build/5411887](https://launchpad.net/ubuntu/+source/gst-plugins-ugly1.0/1.2.2-1ubuntu2/+build/5411887)

---

### Post by mc4man on 2014-01-05
will be fixed, probably will result in a new 0.10 & 1.0 ugly packages
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-ugly1.0/+bug/1266141](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-ugly1.0/+bug/1266141)

(it was not in proposed

[https://launchpad.net/ubuntu/+source/gst-plugins-ugly1.0/1.2.2-1ubuntu2/+publishinghistory](https://launchpad.net/ubuntu/+source/gst-plugins-ugly1.0/1.2.2-1ubuntu2/+publishinghistory)

---

### Post by d-cosner on 2014-01-05
Interesting..... I wonder what the current policy is about testing proposed and getting it into the main repo? It used to be that so many people had to try and confirm a proposed package.

---

### Post by mc4man on 2014-01-05
> **d-cosner said:**
> Interesting..... I wonder what the current policy is about testing proposed and getting it into the main repo? It used to be that so many people had to try and confirm a proposed package.
by & large -proposed is not for testing, mainly for holding on deps.

So in this case new package was uploaded to proposed 23 hrs ago & then deleted & released to universe by a 'robot' an hr. later as there were no dep issues - 
 > Removal requested 22 hours ago.
Deleted 22 hours ago by Ubuntu Archive Robot

moved to release



---

### Post by Ian_Worrall on 2014-01-06
What worked for me was:-

```

sudo apt-get remove --purge gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer1.0-plugins-ugly

```

I generally use vlc instead of totem anyway, so it hopefully won't break things too badly.

---

### Post by xc3RnbFO8P on 2014-01-06
This is update today, gstreamer0.10-plugins-ugly just hangs there after update.

[[img]http://farm8.staticflickr.com/7432/11797953445_14f790e2aa_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/11797953445/)
[update 06012014](http://www.flickr.com/photos/96052779@N07/11797953445/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by craig10x on 2014-01-06
[COLOR=#000000]IT IS FIXED GUYS! I JUST RAN THE SOFTWARE UPDATER AGAIN AND THIS TIME IT CAME UP WITH BOTH THE FIX AND SOME NEW UBUNTU BASE UPDATES....YOU JUST HAVE TO RUN SOFTWARE UPDATER AGAIN (MANUALLY).... [/COLOR]:grin:

The bug report now shows it as fixed and released...

---

### Post by Cavsfan on 2014-01-06
I think it was just a glitch in the system. I seen a cat walk by and then I seen another cat that looked just like the first one walk by. ;)

I was able to re-install gstreamer1.0-plugins-ugly just now without a hitch.
But, now it wants to autoremove all of these packages that I don't really want to get rid of and I don't know why.

```
The following packages were automatically installed and are no longer required:
  argyll browser-plugin-gnash caribou caribou-antler dconf-editor dconf-tools finger fonts-cantarell gdebi gdebi-core gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gkbd-3.0 gir1.2-gnomedesktop-3.0 gir1.2-gtop-2.0 gir1.2-mutter-3.0 gir1.2-nmgtk-1.0 gir1.2-polkit-1.0 gir1.2-rest-0.7 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-tracker-0.16 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gir1.2-zpj-0.0 gjs gnash gnash-common gnome-backgrounds gnome-color-manager gnome-core gnome-dictionary gnome-documents gnome-games
  gnome-icon-theme-extras gnome-nettool gnome-online-accounts gnome-packagekit gnome-packagekit-data gnome-packagekit-session gnome-shell gnome-shell-common gnome-shell-extensions gnome-tweak-tool
  gstreamer0.10-ffmpeg gtk2-engines hamster-applet hamster-indicator inkscape libbonoboui2-0 libbonoboui2-common libboost-iostreams1.54.0 libboost-program-options1.54.0 libboost-thread1.54.0 libcaribou-common
  libcaribou-gtk-module libcaribou-gtk3-module libcaribou0 libcolord-gtk1 libdiscid0 libdmapsharing-3.0-2 libfftw3-3 libgdict-1.0-6 libgdict-common libgdm libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0
  libgnomeui-common libgsf-1-114 libgsf-1-common libgsl0ldbl libgtkmm-2.4-1c2a libgupnp-av-1.0-2 libgupnp-dlna-2.0-3 libicc2 libimdi0 libiptcdata0 libjemalloc1 libmagick++5 libmutter0b librygel-core-2.0-1
  librygel-renderer-2.0-1 librygel-renderer-gst-2.0-1 librygel-server-2.0-1 libsofia-sip-ua-glib3 libsofia-sip-ua0 libtracker-extract-0.16-0 libtracker-miner-0.16-0 libtracker-sparql-0.16-0 libzapojit-0.0-0
  mutter-common perlmagick python-appindicator python-gnome2 python-numpy python-pyatspi python-pyorbit python-uniconvertor python-wnck python3-mako python3-markupsafe rhythmbox-plugins rygel rygel-playbin
  rygel-preferences sound-juicer telepathy-rakia tracker tracker-extract tracker-gui tracker-miner-fs tracker-utils unoconv
Use 'apt-get autoremove' to remove them.

```

I wonder what the deal is with that.

---

### Post by xc3RnbFO8P on 2014-01-06
> **craig10x said:**
> [COLOR=#000000]IT IS FIXED GUYS! I JUST RAN THE SOFTWARE UPDATER AGAIN AND THIS TIME IT CAME UP WITH BOTH THE FIX AND SOME NEW UBUNTU BASED UPDATES....YOU JUST HAVE TO RUN SOFTWARE UPDATER AGAIN (MANUALLY).... [/COLOR]:grin:

The bug report now shows it as fixed and released...

well I updated it with Synaptic Package Manager :)

[[img]http://farm3.staticflickr.com/2885/11799527555_ca41b08d1a_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/11799527555/)
[Screenshot from 2014-01-06 15:54:57](http://www.flickr.com/photos/96052779@N07/11799527555/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by Cavsfan on 2014-01-06
I fixed the problem by:
** sudo apt-get autoremove**

Then opening SPM and entered gnome-shell, ticked it and a bunch of other gnome related stuff, installed all of that, rebooted and it's all good.

---

### Post by Cavsfan on 2014-01-06
I meant to say thanks for the replies. At least I know it wasn't just affecting me, which is always good.

---

