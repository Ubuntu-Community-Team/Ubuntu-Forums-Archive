---
title: "APT  Unmet Dependencies Errors"
date: 2006-12-23
forum: Repositories &amp; Backports
---

### Post by Pray on 2006-12-23
I'm using 6.10 Edgy and when I try to install software with apt-get it brings up error's. If I try to install "ubuntu-desktop", it brings the following up.
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnomesword: Depends: libgail17 (>= 1.6.6) but it is not installable
              Depends: libgnutls11 (>= 1.0.16) but it is not installable
  ubuntu-desktop: Depends: alacarte but it is not going to be installed
                  Depends: apport-gtk but it is not going to be installed
                  Depends: bug-buddy but it is not going to be installed
                  Depends: contact-lookup-applet but it is not going to be installed
                  Depends: deskbar-applet but it is not going to be installed
                  Depends: desktop-file-utils but it is not going to be installed
                  Depends: ekiga but it is not going to be installed
                  Depends: eog but it is not going to be installed
                  Depends: esound but it is not going to be installed
                  Depends: evince but it is not going to be installed
                  Depends: evolution but it is not going to be installed
                  Depends: evolution-exchange but it is not going to be installed
                  Depends: evolution-plugins but it is not going to be installed
                  Depends: evolution-webcal but it is not going to be installed
                  Depends: f-spot but it is not going to be installed
                  Depends: file-roller but it is not going to be installed
                  Depends: firefox but it is not going to be installed
                  Depends: firefox-gnome-support but it is not going to be installed
                  Depends: gaim but it is not going to be installed
                  Depends: gcalctool but it is not going to be installed
                  Depends: gconf-editor but it is not going to be installed
                  Depends: gdebi but it is not going to be installed
                  Depends: gdm but it is not going to be installed
                  Depends: gedit but it is not going to be installed
                  Depends: gimp but it is not going to be installed
                  Depends: gimp-print but it is not going to be installed
                  Depends: gimp-python but it is not going to be installed
                  Depends: gnome-about but it is not going to be installed
                  Depends: gnome-app-install but it is not going to be installed
                  Depends: gnome-applets but it is not going to be installed
                  Depends: gnome-btdownload but it is not going to be installed
                  Depends: gnome-control-center but it is not going to be installed
                  Depends: gnome-cups-manager but it is not going to be installed
                  Depends: gnome-icon-theme but it is not going to be installed
                  Depends: gnome-keyring-manager but it is not going to be installed
                  Depends: gnome-media but it is not going to be installed
                  Depends: gnome-menus but it is not going to be installed
                  Depends: gnome-netstatus-applet but it is not going to be installed
                  Depends: gnome-nettool but it is not going to be installed
                  Depends: gnome-panel but it is not going to be installed
                  Depends: gnome-pilot-conduits but it is not going to be installed
                  Depends: gnome-power-manager but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: gnome-spell but it is not going to be installed
                  Depends: gnome-system-monitor but it is not going to be installed
                  Depends: gnome-system-tools but it is not going to be installed
                  Depends: gnome-terminal but it is not going to be installed
                  Depends: gnome-themes but it is not going to be installed
                  Depends: gnome-utils but it is not going to be installed
                  Depends: gnome-volume-manager but it is not going to be installed
                  Depends: gnome2-user-guide but it is not going to be installed
                  Depends: gstreamer0.10-alsa but it is not going to be installed
                  Depends: gstreamer0.10-esd but it is not going to be installed
                  Depends: gstreamer0.10-plugins-base-apps but it is not going to be installed
                  Depends: gthumb but it is not going to be installed
                  Depends: gtk2-engines but it is not going to be installed
                  Depends: gucharmap but it is not going to be installed
                  Depends: hal-device-manager but it is not going to be installed
                  Depends: hwdb-client-gnome but it is not going to be installed
                  Depends: language-selector but it is not going to be installed
                  Depends: libgnome2-perl but it is not going to be installed
                  Depends: libgnomevfs2-bin but it is not going to be installed
                  Depends: libgnomevfs2-extra but it is not going to be installed
                  Depends: libpt-plugins-v4l but it is not going to be installed
                  Depends: libpt-plugins-v4l2 but it is not going to be installed
                  Depends: metacity but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Depends: nautilus-cd-burner but it is not going to be installed
                  Depends: nautilus-sendto but it is not going to be installed
                  Depends: notification-daemon but it is not going to be installed
                  Depends: openoffice.org-evolution but it is not going to be installed
                  Depends: openoffice.org-gnome but it is not going to be installed
                  Depends: rhythmbox but it is not going to be installed
                  Depends: rss-glx but it is not going to be installed
                  Depends: screensaver-default-images but it is not going to be installed
                  Depends: serpentine but it is not going to be installed
                  Depends: sound-juicer but it is not going to be installed
                  Depends: ssh-askpass-gnome but it is not going to be installed
                  Depends: synaptic but it is not going to be installed
                  Depends: tangerine-icon-theme but it is not going to be installed
                  Depends: tomboy but it is not going to be installed
                  Depends: totem but it is not going to be installed
                  Depends: totem-mozilla but it is not going to be installed
                  Depends: tsclient but it is not going to be installed
                  Depends: ubuntu-artwork but it is not going to be installed
                  Depends: ubuntu-docs but it is not going to be installed
                  Depends: ubuntu-sounds but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Depends: usplash-theme-ubuntu but it is not going to be installed
                  Depends: vino but it is not going to be installed
                  Depends: xsane but it is not going to be installed
                  Depends: xscreensaver-data but it is not going to be installed
                  Depends: xscreensaver-gl but it is not going to be installed
                  Depends: xvncviewer but it is not going to be installed
                  Depends: yelp but it is not going to be installed
                  Depends: zenity but it is not going to be installed
                  Recommends: brltty-x11 but it is not going to be installed
                  Recommends: gnome-accessibility-themes but it is not going to be installed
                  Recommends: gnome-games but it is not going to be installed
                  Recommends: gnome-mag but it is not going to be installed
                  Recommends: gnome-orca but it is not going to be installed
                  Recommends: gnome-screensaver but it is not going to be installed
                  Recommends: onboard but it is not going to be installed
                  Recommends: scim but it is not going to be installed
                  Recommends: scim-gtk2-immodule but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
Not sure how to fix this, I've tried apt-get clean and checking the man pages but I can't see anyway to fix it, any help would be greatly appreciated, thanks in advance.

---

### Post by bapoumba on 2006-12-30
This may be a little late, but could you post the output to **cat /etc/apt/sources.list** ?

---

