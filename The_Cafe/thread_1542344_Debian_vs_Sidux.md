---
title: "Debian vs Sidux"
date: 2010-07-30
forum: The Cafe
---

### Post by mamamia88 on 2010-07-30
Which do you think is more suitable for a noob like me who has only used ubuntu really on a consistent basis?  running off sidux live cd and am impressed by how fast it is with xcfe.  but i prefer a gnome desktop

---

### Post by snowpine on 2010-07-30
Sidux does not support Gnome and is definitely **not** a "noob" distro. Debian does support Gnome and is very, very stable; however you may find that the applications are a lot older (about 2 years) compared with Ubuntu (Firefox 3.0, OpenOffice 2.4, etc).

What's wrong with Ubuntu, I'm curious why you want to switch? ;) Have you considered Mint?

---

### Post by mamamia88 on 2010-07-30
no real reason i want to switch besides having just tried sidux off a live cd and am super impressed by how fast it is even off the cd.

---

### Post by snowpine on 2010-07-30
> **mamamia88 said:**
> no real reason i want to switch besides having just tried sidux off a live cd and am super impressed by how fast it is even off the cd.

I like sidux too (not currently using it, but have in the past). It is one of those distros where you absolutely 100% have to read [the manual]("http://manual.sidux.com/") and follow the instructions exactly. If that is your personality type, then sidux could be a good fit for you.

Remember that you can set up a dual boot (or triple boot if you have Windows too) and have 2 different Linux distros, one that is stable and familiar, and one that you are trying for fun. This is what I do. :)

---

### Post by mamamia88 on 2010-07-30
yeah i have a second harddrive bay in my laptop and a few spare harddrives laying around maybe i'll set up a dualboot

---

### Post by Zoot7 on 2010-07-30
Sidux is a good choice if you don't want to deal with the potential problems Debian Sid will present to you. (Mind you it has stabilized a bit since the Experimental repo was added) From what I hear, it does (for the most part) manage to adequately tame Sid.

---

### Post by khelben1979 on 2010-07-30
> **snowpine said:**
> Sidux does not support Gnome and is definitely **not** a "noob" distro. Debian does support Gnome and is very, very stable; however you may find that the applications are a lot older (about 2 years) compared with Ubuntu (Firefox 3.0, OpenOffice 2.4, etc).

What's wrong with Ubuntu, I'm curious why you want to switch? ;) Have you considered Mint?

This old argument saying that Debian has old applications isn't really valid. It's easy to activate backports which gives you fresh applications even on the old Debian Lenny system.

Also, Debian testing "Squeeze" is in my opinion, more stable than any Ubuntu version.

XFCE can be installed and used with Debian as any other Linux distribution. My current squeeze installation on my old Powerbook G3 lombard lacks both Gnome and KDE and because of low RAM (128MB) I use XFCE as my main desktop enviroment at the present. Requires low RAM and runs just fine on this old machine.

---

### Post by snowpine on 2010-07-30
> **khelben1979 said:**
> This old argument saying that Debian has old applications isn't really valid. It's easy to activate backports which gives you fresh applications even on the old Debian Lenny system.

Also, Debian testing "Squeeze" is in my opinion, more stable than any Ubuntu version.

I am well aware of the different Debian "branches" (typing this from Sid) but I would definitely recommend Stable over Testing for a self-proclaimed Linux "noob." Stable + Backports is a great suggestion! :)

[http://backports.org](http://backports.org)

---

### Post by harlan on 2010-07-30
> **mamamia88 said:**
> Which do you think is more suitable for a noob like me who has only used ubuntu really on a consistent basis?  running off sidux live cd and am impressed by how fast it is with xcfe.  but i prefer a gnome desktop

sidux is a really fast distro, but not for noobs because is debian sid based (that's the reason behind the sidux mascot, a scorpion, warning about the risks of using it).
Debian testing with xfce would suit your needs, and if you're a gnome fan, then a gnome-core install instead a complete gnome environment is also a good option.

---

### Post by Ewingo401 on 2010-07-30
I've been running sidux for the past few months.  As long as you don't mind doing things the sidux way (and honestly, the things they ask you to do differently aren't all that extreme.) and don't mind checking the forums for warnings before doing a dist-upgrade, you should have a very enjoyable experience.  It is much faster than Ubuntu, and in most cases has much more up to date software without having to add 3rd party repos.

The one downside is that breakage is much more likely than in a distro like Ubuntu, that's just the nature of a rolling release distro.  That's not to say that breakage is frequent, but it can and does happen occasionally.  Fixes however, are usually very swift.

---

### Post by Zoot7 on 2010-07-30
> **harlan said:**
> a gnome-core install instead a complete gnome environment is also a good option.
I fell into that trap before with those ugly metapackages like **gnome** and **gnome-desktop-environment**, just look at all the crud the former metapackage would pull in:
```
mark@mark-xps:~$ apt-cache depends gnome
gnome
  Depends: gnome-desktop-environment
 |Depends: gdm3
  Depends: gdm-themes
  Depends: gnome-themes-extras
  Depends: gnome-games
  Depends: libpam-gnome-keyring
  Depends: gstreamer0.10-plugins-ugly
  Depends: gstreamer0.10-ffmpeg
 |Depends: rhythmbox-plugins
  Depends: banshee
 |Depends: rhythmbox-plugin-cdrecorder
  Depends: banshee
  Depends: synaptic
  Depends: system-config-printer
  Depends: totem-mozilla
  Depends: epiphany-extensions
  Depends: gedit-plugins
  Depends: evolution-plugins
 |Depends: evolution-exchange
  Depends: <evolution-mapi>
  Depends: evolution-webcal
  Depends: software-center
  Depends: gnome-codec-install
  Depends: transmission-gtk
  Depends: arj
  Depends: avahi-daemon
 |Depends: tomboy
  Depends: gnote
  Suggests: gnome-dbg
  Suggests: openoffice.org-gnome
  Suggests: openoffice.org-evolution
  Recommends: gnome-games-extra-data
  Recommends: network-manager-gnome
  Recommends: gnome-office
  Recommends: update-notifier
  Recommends: remmina
  Recommends: hal-cups-utils
  Recommends: gthumb
 |Recommends: liferea
 |Recommends: evolution-rss
  Recommends: blam
  Recommends: menu-xdg
  Recommends: gdebi
  Recommends: mozilla-plugin-gnash
  Conflicts: <gnome-cups-manager>
```

---

### Post by harlan on 2010-07-31
> **Zoot7 said:**
> I fell into that trap before with those ugly metapackages like **gnome** and **gnome-desktop-environment**, just look at all the crud the former metapackage would pull in:
```
mark@mark-xps:~$ apt-cache depends gnome
gnome
  Depends: gnome-desktop-environment
 |Depends: gdm3
  Depends: gdm-themes
  Depends: gnome-themes-extras
  Depends: gnome-games
  Depends: libpam-gnome-keyring
  Depends: gstreamer0.10-plugins-ugly
  Depends: gstreamer0.10-ffmpeg
 |Depends: rhythmbox-plugins
  Depends: banshee
 |Depends: rhythmbox-plugin-cdrecorder
  Depends: banshee
  Depends: synaptic
  Depends: system-config-printer
  Depends: totem-mozilla
  Depends: epiphany-extensions
  Depends: gedit-plugins
  Depends: evolution-plugins
 |Depends: evolution-exchange
  Depends: <evolution-mapi>
  Depends: evolution-webcal
  Depends: software-center
  Depends: gnome-codec-install
  Depends: transmission-gtk
  Depends: arj
  Depends: avahi-daemon
 |Depends: tomboy
  Depends: gnote
  Suggests: gnome-dbg
  Suggests: openoffice.org-gnome
  Suggests: openoffice.org-evolution
  Recommends: gnome-games-extra-data
  Recommends: network-manager-gnome
  Recommends: gnome-office
  Recommends: update-notifier
  Recommends: remmina
  Recommends: hal-cups-utils
  Recommends: gthumb
 |Recommends: liferea
 |Recommends: evolution-rss
  Recommends: blam
  Recommends: menu-xdg
  Recommends: gdebi
  Recommends: mozilla-plugin-gnash
  Conflicts: <gnome-cups-manager>
```


gnome-core has less dependencies than gnome metapackage
[PHP]# apt-cache depends gnome-core
gnome-core
  Depende: eog
  Depende: gedit
  Depende: gnome-applets
  Depende: gnome-control-center
  Depende: gnome-icon-theme
  Depende: gnome-menus
  Depende: gnome-panel
  Depende: gnome-power-manager
  Depende: gnome-session
  Depende: gnome-settings-daemon
  Depende: gnome-terminal
  Depende: gvfs
 |Depende: metacity
  Depende: mutter
  Depende: nautilus
  Depende: yelp
  Sugiere: gnome-desktop-environment[/PHP]

---

### Post by Zoot7 on 2010-08-01
> **harlan said:**
> gnome-core has less dependencies than gnome metapackage

And gnome-core is all you really need.

---

