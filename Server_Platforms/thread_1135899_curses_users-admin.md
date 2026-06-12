---
title: "curses users-admin?"
date: 2009-04-24
forum: Server Platforms
---

### Post by lavinog on 2009-04-24
I am setting up samba on a server, and I have to make some new users.
I got used to users-admin (gui way). I find it handy to see all of the user information at once instead of cat /etc/passwd

On this server though I don't know if I want to install all of the gnome dependencies required for gnome-system-tools:
```
sudo apt-get install gnome-system-tools 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  acl aspell aspell-en dictionaries-common fontconfig gamin gconf2 gconf2-common gnome-keyring gnome-mime-data gnome-mount hal hal-info hicolor-icon-theme libaspell15 libatk1.0-0 libatk1.0-data
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-glib1 libcairo2 libdatrie0 libenchant1c2a libfontenc1 libgamin0 libgconf2-4 libgnome-keyring0 libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-extra libgp11-0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libhal-storage1 libhal1 libhunspell-1.2-0 libidl0 libjpeg62 libnet-dbus-perl libnotify1 liboobs-1-4 liborbit2 libpam-gnome-keyring
  libpango1.0-0 libpango1.0-common libpixman-1-0 libpolkit-gnome0 libsexy2 libsmbclient libsmbios-bin libsmbios2 libstartup-notification0 libthai-data libthai0 libtie-ixhash-perl libtiff4 libwnck-common
  libwnck22 libx86-1 libxcb-render-util0 libxcb-render0 libxcomposite1 libxdamage1 libxfont1 libxi6 libxinerama1 libxml-twig-perl libxml-xpath-perl libxrandr2 libxres1 myspell-en-us notification-daemon
  pm-utils policykit-gnome powermgmt-base radeontool shared-mime-info system-tools-backends vbetool x-ttcidfont-conf xfonts-encodings xfonts-utils

```

I was wondering if there is a ncurses based tool for user management?

---

### Post by capscrew on 2009-04-24
[Linuxconf]("http://linux.softpedia.com/get/System/System-Administration/Linuxconf-18.shtml")

---

