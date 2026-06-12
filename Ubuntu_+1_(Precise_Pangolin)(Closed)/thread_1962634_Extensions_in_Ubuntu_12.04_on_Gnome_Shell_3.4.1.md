---
title: "Extensions in Ubuntu 12.04 on Gnome Shell 3.4.1"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by erik1001 on 2012-04-21
Hello. I'm trying to install some extensions of Gnome Shell 3.4.1 in Ubuntu 12.04 but there are some problems. 

I've installed "gnome-shell-extensions" and "gnome-shell-extensions-common", but I have this error:
```
@home-PC:~$ sudo add-apt-repository ppa:webupd8team/gnome3
You are about to add the following PPA to your system:
 GNOME 3 WebUpd8 PPA

Packages: Epiphany Browser (and extensions), GNOME Documents, GNOME Shell Extensions (official, but includes patches to prevent some crashes and to get some of the official extensions to work with the latest stable GNOME Shell), Tracker, WebKitGTK+, GPaste GNOME Shell clipboard manager, Mailnag GNOME3 mail notifier, other unofficial GNOME Shell extensions such as Pidgin Shell Extension, MediaPlayer, noa11y, Weather, System Monitor applet, Extended Places Menu, etc.
 More info: https://launchpad.net/~webupd8team/+archive/gnome3
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.59FXd8mSRR --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 7B2C3B0889BF5709A105D03AC2518248EEA14886
gpg: requesting key EEA14886 from hkp server keyserver.ubuntu.com
gpg: key EEA14886: "Launchpad VLC" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
suricactus@home-PC:~$ sudo apt-get install gnome-shell-extensions-workspace-indicator 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell-extensions-workspace-indicator : Depends: gnome-shell-extensions-common but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
I've tried installing them from the terminal, synaptic and software center, but I didn't succeed so I need your help. 
Thanks in advance.

---

### Post by neu5eeCh on 2012-04-21
You're still using a product that hasn't been officially released, so dependency warnings like these are to be expected. Not all PPA's are set up yet for 12.04. [See above]("http://ubuntuforums.org/showthread.php?t=1859240").

---

### Post by erik1001 on 2012-04-21
Yes, I know but I thought they should be fixed already because Ubuntu 12.04 is released officially on April 26th.

---

### Post by neu5eeCh on 2012-04-21
> **erik1001 said:**
> Yes, I know but I thought they should be fixed already because Ubuntu 12.04 is released officially on April 26th.

I've tried a couple PPAs that give me the same results. Package versions and that sort of thing, I'm guessing, are still being tweaked right up to the last week or so.

---

### Post by Yellow Pasque on 2012-04-21
> **erik1001 said:**
> Yes, I know but I thought they should be fixed already because Ubuntu 12.04 is released officially on April 26th.
It all depends on the PPA maintainer. Some are very reliable at keeping their PPA's updated, while others don't bother.

---

### Post by xebian on 2012-04-21
Added that ppa to check it out.  Installing gnome-shell-extensions is all you need.  It conflicts/replaces the one ( and many others) you are trying to install.

You can enable them in the advanced settings.

```
Package: gnome-shell-extensions          
New: yes
State: installed
Automatically installed: yes
Version: 3.4.0+git20120414.5ca9f35a-0ubuntu1~webupd8-0
Priority: optional
Section: gnome
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Uncompressed Size: 842 k
Depends: dconf-gsettings-backend | gsettings-backend, gnome-shell (>= 3.4.0~),
         gir1.2-gtop-2.0
Conflicts: gnome-shell-extensions-alternate-tab,
           gnome-shell-extensions-alternate-tab,
           gnome-shell-extensions-alternative-status-menu,
           gnome-shell-extensions-alternative-status-menu,
           gnome-shell-extensions-apps-menu, gnome-shell-extensions-apps-menu,
           gnome-shell-extensions-auto-move-windows,
           gnome-shell-extensions-auto-move-windows,
           gnome-shell-extensions-dock, gnome-shell-extensions-dock,
           gnome-shell-extensions-drive-menu, gnome-shell-extensions-drive-menu,
           gnome-shell-extensions-gajim, gnome-shell-extensions-gajim,
           gnome-shell-extensions-native-window-placement,
           gnome-shell-extensions-native-window-placement,
           gnome-shell-extensions-places-menu,
           gnome-shell-extensions-places-menu,
           gnome-shell-extensions-system-monitor,
           gnome-shell-extensions-system-monitor,
           gnome-shell-extensions-user-theme, gnome-shell-extensions-user-theme,
           gnome-shell-extensions-windows-navigator,
           gnome-shell-extensions-windows-navigator,
           gnome-shell-extensions-workspace-indicator,
           gnome-shell-extensions-workspace-indicator,
           gnome-shell-extensions-xrandr-indicator,
           gnome-shell-extensions-xrandr-indicator
Replaces: gnome-shell-extensions-alternate-tab,
          gnome-shell-extensions-alternate-tab,
          gnome-shell-extensions-alternative-status-menu,
          gnome-shell-extensions-alternative-status-menu,
          gnome-shell-extensions-apps-menu, gnome-shell-extensions-apps-menu,
          gnome-shell-extensions-auto-move-windows,
          gnome-shell-extensions-auto-move-windows, gnome-shell-extensions-dock,
          gnome-shell-extensions-dock, gnome-shell-extensions-drive-menu,
          gnome-shell-extensions-drive-menu, gnome-shell-extensions-gajim,
          gnome-shell-extensions-gajim,
          gnome-shell-extensions-native-window-placement,
          gnome-shell-extensions-native-window-placement,
          gnome-shell-extensions-places-menu,
          gnome-shell-extensions-places-menu,
          gnome-shell-extensions-system-monitor,
          gnome-shell-extensions-system-monitor,
          gnome-shell-extensions-user-theme, gnome-shell-extensions-user-theme,
          gnome-shell-extensions-windows-navigator,
          gnome-shell-extensions-windows-navigator,
          gnome-shell-extensions-workspace-indicator,
          gnome-shell-extensions-workspace-indicator,
          gnome-shell-extensions-xrandr-indicator,
          gnome-shell-extensions-xrandr-indicator
Description: Extensions to extend functionality of GNOME Shell (common files)
 The GNOME Shell redefines user interactions with the GNOME desktop. In
 particular, it offers new paradigms for launching applications, accessing
 documents, and organizing open windows in GNOME. Later, it will introduce a new
 applets eco-system and offer new solutions for other desktop features, such as
 notifications and contacts management. The GNOME Shell is intended to replace
 functions handled by the GNOME Panel and by the window manager in previous
 versions of GNOME. The GNOME Shell has rich visual effects enabled by new
 graphical technologies. 
 
 GNOME Shell is extensible using extensions. This package contains official
 GNOME Shell extensions.

```

---

### Post by erik1001 on 2012-04-21
Oh thank you very much. I saw that I'm able to manage them from advanced settings, but before I've tried to install new extensions. It was so simple, thank you again. (:

---

