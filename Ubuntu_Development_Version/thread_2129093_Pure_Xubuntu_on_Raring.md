---
title: "Pure Xubuntu on Raring"
date: 2013-03-25
forum: Ubuntu Development Version
---

### Post by slickymaster on 2013-03-25
I've noticed that Raring comes packed with a ton of gnome packages and I'm wondering about the practicability and safety, in what system's stability is concerned, of doing something like "[Getting Back to a Pure Xubuntu]("http://www.psychocats.net/ubuntu/purexubuntu")".

---

### Post by grahammechanical on 2013-03-25
As far as I can see that tutorial is a kind of reverse engineering. Install Xubuntu. Add Ubuntu Desktop or one of the other desktops). Note the packages installed. Mark these as the packages to remove to get back to a "pure" Xubuntu.

> [COLOR=#000000][FONT=bitstream vera sans]These removal commands were created based on what Ubuntu, Kubuntu, etc. packages were added to a default Xubuntu installation.[/FONT][/COLOR]

I suggest that there is a big difference between 12.10 and 13.04. To answer your question you must re-run the experiment on a "pure" Xubuntu Raring Ringtail. I am one of those people who think that "pure" Xubuntu is Xubuntu installed from a Xubuntu ISO image. If I wanted to try out Xubuntu or any of the others I would install them on another partition and test from there. Right now I have Ubuntu Kylin on a USB stick. I do not think it sensible to install other desktops over a "pure" install of a Ubuntu flavour.

Regards.

---

### Post by ventrical on 2013-03-25
> **grahammechanical said:**
> As far as I can see that tutorial is a kind of reverse engineering. Install Xubuntu. Add Ubuntu Desktop or one of the other desktops). Note the packages installed. Mark these as the packages to remove to get back to a "pure" Xubuntu.



I suggest that there is a big difference between 12.10 and 13.04. To answer your question you must re-run the experiment on a "pure" Xubuntu Raring Ringtail. I am one of those people who think that "pure" Xubuntu is Xubuntu installed from a Xubuntu ISO image. If I wanted to try out Xubuntu or any of the others I would install them on another partition and test from there. Right now I have Ubuntu Kylin on a USB stick. I do not think it sensible to install other desktops over a "pure" install of a Ubuntu flavour.

Regards.

In my experience there is always a chance of interfection of depends, meaning that  getting back to a pure Xubuntu is almost impossible (is possible if you are willing to spend the downtime cleaning it up). This also goes for other distros or flavours. If I have Ubuntu (unity default) and install Xubuntu-desktop it will interfect Unity, and vis a versa. Kubuntu is especially problematic in both scenarios. It will completely interfect a Unity default install . Cairo -doc has also regressed in this area.. especially with Quantal and Raring.

---

### Post by slickymaster on 2013-03-25
> **grahammechanical said:**
> As far as I can see that tutorial is a kind of reverse engineering. Install Xubuntu. Add Ubuntu Desktop or one of the other desktops). Note the packages installed. Mark these as the packages to remove to get back to a "pure" Xubuntu
.../
/...
I suggest that there is a big difference between 12.10 and 13.04. To answer your question you must re-run the experiment on a "pure" Xubuntu Raring Ringtail. I am one of those people who think that "pure" Xubuntu is Xubuntu installed from a Xubuntu ISO image. If I wanted to try out Xubuntu or any of the others I would install them on another partition and test from there. Right now I have Ubuntu Kylin on a USB stick. I do not think it sensible to install other desktops over a "pure" install of a Ubuntu flavour.
Regards.

I agree with you, it's a sort of reverse engineering. 

But, I have a pure Xubuntu Raring Ringtail (installed from a Xubuntu ISO image), running on a VirtualBox, but nevertheless after removing some gnome packages, when I run
```
dpkg --get-selections | grep gnome
```
I get this much
```
gir1.2-gnomebluetooth-1.0   install
gnome-accessibility-themes   install
gnome-bluetooth     install
gnome-calculator    install
gnome-control-center    install
gnome-control-center-data   install
gnome-desktop-data    install
gnome-desktop3-data    install
gnome-icon-theme    install
gnome-icon-theme-symbolic   install
gnome-keyring     install
gnome-menus     install
gnome-session-bin    install
gnome-settings-daemon    install
gnome-system-tools    install
gnome-time-admin    install
gnome-user-guide    install
gnome-user-share    install
gstreamer0.10-gnomevfs:i386   install
language-pack-gnome-en    install
language-pack-gnome-en-base   install
language-selector-gnome    install
libgnome-bluetooth11    install
libgnome-control-center1   install
libgnome-desktop-3-4    install
libgnome-keyring-common    install
libgnome-keyring0:i386    install
libgnome-menu-3-0    install
libgnomekbd-common    install
libgnomekbd8     install
libgnomevfs2-0:i386    install
libgnomevfs2-common    install
libgnomevfs2-extra:i386    install
libp11-kit-gnome-keyring:i386   install
libpam-gnome-keyring:i386   install
libsoup-gnome2.4-1:i386    install
network-manager-gnome    install
network-manager-pptp-gnome   install
policykit-1-gnome    install
python-gnomekeyring    install
system-config-printer-gnome  
```

---

### Post by slickymaster on 2013-03-25
> **ventrical said:**
> In my experience there is always a chance of interfection of depends, meaning that  getting back to a pure Xubuntu is almost impossible (is possible if you are willing to spend the downtime cleaning it up). This also goes for other distros or flavours. If I have Ubuntu (unity default) and install Xubuntu-desktop it will interfect Unity, and vis a versa. Kubuntu is especially problematic in both scenarios. It will completely interfect a Unity default install . Cairo -doc has also regressed in this area.. especially with Quantal and Raring.

That was my primary intention/idea, even though the time I would spent on trying to achieve it. But then the doubt cross my mind if doing it I would completely mess up the system due to the possibility of interference of depends.
That was the reason that led me to this thread. I thought that maybe someone had tried it and I was just searching for some feedback on the attempt.

I think my question is dully answered. Thank you both on your considerations.

---

### Post by vasa1 on 2013-03-25
> **slickymaster said:**
> I agree with you, it's a sort of reverse engineering. 

But, I have a pure Xubuntu Raring Ringtail (installed from a Xubuntu ISO image), running on a VirtualBox, but nevertheless after removing some gnome packages, when I run
```
dpkg --get-selections | grep gnome
```
I get this much
...
If I may ... Several GNOME packages are used by both "pure" Xubuntu and "pure" Lubuntu because they're most suited for the job or there's nothing *lighter* available.
For example, both Xubuntu and Lubuntu come with evince and network-manager-gnome, as does Ubuntu. But neither Xubuntu nor Lubuntu use gnome-terminal or gnome-screenshot. Instead, they have their own (presumably) lighter versions.

---

### Post by slickymaster on 2013-03-25
> **vasa1 said:**
> If I may ... Several GNOME packages are used by both "pure" Xubuntu and "pure" Lubuntu because they're most suited for the job or there's nothing *lighter* available.
For example, both Xubuntu and Lubuntu come with GNOME's Evince, as does Ubuntu. But neither Xubuntu nor Lubuntu use gnome-terminal or gnome-screenshot. Instead, they have their own (presumably) lighter versions.

Exactly. And that's why I was wondering if anyone had tried it and thus providing some pointers concerning on what packages you really shouldn't mess with, and the ones you could freely remove.

---

