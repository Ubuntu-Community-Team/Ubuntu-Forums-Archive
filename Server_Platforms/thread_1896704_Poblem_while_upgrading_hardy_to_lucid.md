---
title: "Poblem while upgrading hardy to lucid"
date: 2011-12-17
forum: Server Platforms
---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-12-17
Hello everyone

i have an old version of hardy 8.04.4 LTS ubuntu-server and i wanted to upgrade it to lucid 10.04 

here what i got 

```
uname -a
```
[PHP]Linux <xxxxxxx> 2.6.32.2-xxxx-std-ipv4-32 #1 SMP Tue Dec 29 14:40:32 UTC 2009 i686 GNU/Linux[/PHP]

```
lsb_release -a
```
[PHP]
Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.4 LTS
Release:    8.04
Codename:    hardy
[/PHP]

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)
i did exactly as in "Upgrade from 8.04 LTS to 10.04 LTS" 

after ```
 sudo do-release-upgrade 
```
then i got this


[PHP]Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 8, in <module>
    from UpdateManager.Core.DistUpgradeFetcherCore import DistUpgradeFetcherCore
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 34, in <module>
    import GnuPGInterface
ImportError: No module named GnuPGInterface
[/PHP]

i tried to do 
```
apt-get upgrade
```
then i got this
[PHP]Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies.
  compiz-gnome: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  evolution: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  gdm: Depends: libcanberra-gtk0 (>= 0.4) but it is not installed
       Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed
       Depends: upstart-job
  gnome-applets: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  gnome-control-center: Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
                        Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  gnome-screensaver: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  gnome-session-bin: Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed
  gnome-settings-daemon: Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
                         Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  initramfs-tools: Depends: util-linux (> 2.15~rc1) but 2.13.1-5ubuntu3.1 is installed
  irssi: Depends: libperl5.10 (>= 5.10.1) but it is not installed
  language-support-writing-en: Depends: myspell-en-us but it is not installed
  libappindicator0: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libapt-pkg-perl: Depends: perlapi-5.8.8 but it is not installable
  libauthen-pam-perl: Depends: perlapi-5.8.7 but it is not installable
  libcupsimage2: Depends: libcups2 (>= 1.4.0) but it is not installed
  libdbusmenu-gtk1: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed
  libedataserverui1.2-8: Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed
  libevdocument2: Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed
  libevview2: Depends: libgtk2.0-0 (>= 2.20.0) but 2.12.9-3ubuntu5 is installed
  libgnome-desktop-2-17: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libgnome-window-settings1: Depends: libgtk2.0-0 (>= 2.15.0) but 2.12.9-3ubuntu5 is installed
  libgnome2-canvas-perl: Depends: perlapi-5.8.8 but it is not installable
  libgnome2-perl: Depends: perlapi-5.8.7 but it is not installable
  libgnomekbd4: Depends: libgtk2.0-0 (>= 2.20.0) but 2.12.9-3ubuntu5 is installed
  libgtk2-perl: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libgtkhtml-editor0: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libgtkhtml3.14-19: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libgucharmap7: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed
  libindicator0: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed
  libmetacity-private0: Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
  libnet-ssleay-perl: Depends: perlapi-5.8.7 but it is not installable
  libpurple0: Depends: libperl5.10 (>= 5.10.1) but it is not installed
  librsvg2-2: Depends: libgtk2.0-0 (>= 2.16) but 2.12.9-3ubuntu5 is installed
  librsvg2-common: Depends: libgtk2.0-0 (>= 2.16) but 2.12.9-3ubuntu5 is installed
  libsnmp15: Depends: libperl5.8 (>= 5.8.8) but it is not installable
  libsvn-perl: Depends: perlapi-5.8.8 but it is not installable
  libtext-iconv-perl: Depends: perlapi-5.8.7 but it is not installable
  libxml-parser-perl: Depends: perlapi-5.8.8 but it is not installable
  metacity: Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
            Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  openoffice.org-base-core: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-calc: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-draw: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
                      Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-style-galaxy: Depends: openoffice.org-core (>= 1:3.2.0~beta) but it is not installed
  openoffice.org-style-human: Depends: openoffice.org-common (= 1:2.4.1-1ubuntu2.5) but 1:3.2.0-7ubuntu4.2 is installed
  openoffice.org-thesaurus-de: Depends: openoffice.org-core (>= 1.9) but it is not installed
  openoffice.org-thesaurus-de-ch: Depends: openoffice.org-core (>= 1.9) but it is not installed
  openoffice.org-thesaurus-pl: Depends: openoffice.org-core (>= 1.9) but it is not installed
  openoffice.org-writer: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  pidgin: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  policykit-1-gnome: Depends: libgtk2.0-0 (>= 2.17.1) but 2.12.9-3ubuntu5 is installed
  python: Depends: python-minimal (= 2.5.2-0ubuntu1) but 2.6.5-0ubuntu1 is installed
  python-cairo: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-evince: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-evolution: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gconf: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-glade2: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
                 Depends: libgtk2.0-0 (>= 2.19.0) but 2.12.9-3ubuntu5 is installed
  python-gnome2: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomeapplet: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomecanvas: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomedesktop: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomekeyring: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomeprint: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gobject: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gtk2: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
               Depends: libgtk2.0-0 (>= 2.19.1) but 2.12.9-3ubuntu5 is installed
  python-gtop: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-mediaprofiles: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-metacity: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-pyorbit: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-rsvg: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-totem-plparser: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-uno: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2.5) but it is not installed
  python-wnck: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  slapd: Depends: libperl5.10 (>= 5.10.1) but it is not installed
  udev: Depends: upstart-job
        Depends: util-linux (> 2.15~rc2) but 2.13.1-5ubuntu3.1 is installed
  ufw: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
       Depends: upstart-job
  util-linux-locales: Depends: util-linux (>= 2.17.2-0) but 2.13.1-5ubuntu3.1 is installed
  x11-common: Depends: upstart-job
  xchat: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
         Depends: libperl5.10 (>= 5.10.1) but it is not installed
  xchat-gnome: Depends: libcanberra-gtk0 (>= 0.3) but it is not installed
               Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
               Depends: libperl5.10 (>= 5.10.0) but it is not installed
E: Unmet dependencies. Try using -f.
[/PHP]


then i tried
```
apt-get -f install
```

and i got this
[PHP]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
  compiz-gnome: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  evolution: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  gdm: Depends: libcanberra-gtk0 (>= 0.4) but it is not installed
       Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed
       Depends: upstart-job
  gnome-applets: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  gnome-control-center: Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
                        Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  gnome-screensaver: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  gnome-session-bin: Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed
  gnome-settings-daemon: Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
                         Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  initramfs-tools: Depends: util-linux (> 2.15~rc1) but 2.13.1-5ubuntu3.1 is installed
  irssi: Depends: libperl5.10 (>= 5.10.1) but it is not installed
  language-support-writing-en: Depends: myspell-en-us but it is not installed
  libappindicator0: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libapt-pkg-perl: Depends: perlapi-5.8.8 but it is not installable
  libauthen-pam-perl: Depends: perlapi-5.8.7 but it is not installable
  libcupsimage2: Depends: libcups2 (>= 1.4.0) but it is not installed
  libdbusmenu-gtk1: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed
  libedataserverui1.2-8: Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed
  libevdocument2: Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed
  libevview2: Depends: libgtk2.0-0 (>= 2.20.0) but 2.12.9-3ubuntu5 is installed
  libgnome-desktop-2-17: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libgnome-window-settings1: Depends: libgtk2.0-0 (>= 2.15.0) but 2.12.9-3ubuntu5 is installed
  libgnome2-canvas-perl: Depends: perlapi-5.8.8 but it is not installable
  libgnome2-perl: Depends: perlapi-5.8.7 but it is not installable
  libgnomekbd4: Depends: libgtk2.0-0 (>= 2.20.0) but 2.12.9-3ubuntu5 is installed
  libgtk2-perl: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libgtkhtml-editor0: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libgtkhtml3.14-19: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libgucharmap7: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed
  libindicator0: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed
  libmetacity-private0: Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
  libnet-ssleay-perl: Depends: perlapi-5.8.7 but it is not installable
  libpurple0: Depends: libperl5.10 (>= 5.10.1) but it is not installed
  librsvg2-2: Depends: libgtk2.0-0 (>= 2.16) but 2.12.9-3ubuntu5 is installed
  librsvg2-common: Depends: libgtk2.0-0 (>= 2.16) but 2.12.9-3ubuntu5 is installed
  libsnmp15: Depends: libperl5.8 (>= 5.8.8) but it is not installable
  libsvn-perl: Depends: perlapi-5.8.8 but it is not installable
  libtext-iconv-perl: Depends: perlapi-5.8.7 but it is not installable
  libxml-parser-perl: Depends: perlapi-5.8.8 but it is not installable
  metacity: Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
            Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  openoffice.org-base-core: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-calc: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-draw: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
                      Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-style-galaxy: Depends: openoffice.org-core (>= 1:3.2.0~beta) but it is not installed
  openoffice.org-style-human: Depends: openoffice.org-common (= 1:2.4.1-1ubuntu2.5) but 1:3.2.0-7ubuntu4.2 is installed
  openoffice.org-thesaurus-de: Depends: openoffice.org-core (>= 1.9) but it is not installed
  openoffice.org-thesaurus-de-ch: Depends: openoffice.org-core (>= 1.9) but it is not installed
  openoffice.org-thesaurus-pl: Depends: openoffice.org-core (>= 1.9) but it is not installed
  openoffice.org-writer: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  pidgin: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  policykit-1-gnome: Depends: libgtk2.0-0 (>= 2.17.1) but 2.12.9-3ubuntu5 is installed
  python: Depends: python-minimal (= 2.5.2-0ubuntu1) but 2.6.5-0ubuntu1 is installed
  python-cairo: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-evince: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-evolution: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gconf: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-glade2: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
                 Depends: libgtk2.0-0 (>= 2.19.0) but 2.12.9-3ubuntu5 is installed
  python-gnome2: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomeapplet: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomecanvas: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomedesktop: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomekeyring: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomeprint: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gobject: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gtk2: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
               Depends: libgtk2.0-0 (>= 2.19.1) but 2.12.9-3ubuntu5 is installed
  python-gtop: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-mediaprofiles: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-metacity: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-pyorbit: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-rsvg: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-totem-plparser: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-uno: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2.5) but it is not installed
  python-wnck: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  slapd: Depends: libperl5.10 (>= 5.10.1) but it is not installed
  udev: Depends: upstart-job
        Depends: util-linux (> 2.15~rc2) but 2.13.1-5ubuntu3.1 is installed
  ufw: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
       Depends: upstart-job
  util-linux-locales: Depends: util-linux (>= 2.17.2-0) but 2.13.1-5ubuntu3.1 is installed
  x11-common: Depends: upstart-job
  xchat: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
         Depends: libperl5.10 (>= 5.10.1) but it is not installed
  xchat-gnome: Depends: libcanberra-gtk0 (>= 0.3) but it is not installed
               Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
               Depends: libperl5.10 (>= 5.10.0) but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
[/PHP]

i tried that also 

```
dpkg --configure -a
```

[PHP]dpkg: dependency problems prevent configuration of libgnomekbd4:
 libgnomekbd4 depends on libgtk2.0-0 (>= 2.20.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing libgnomekbd4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on libcanberra-gtk0 (>= 0.4); however:
  Package libcanberra-gtk0 is not installed.
 gdm depends on libgtk2.0-0 (>= 2.16.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
 gdm depends on upstart-job; however:
  Package upstart-job is not installed.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on util-linux (>> 2.15~rc1); however:
  Version of util-linux on system is 2.13.1-5ubuntu3.1.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xchat-gnome:
 xchat-gnome depends on libcanberra-gtk0 (>= 0.3); however:
  Package libcanberra-gtk0 is not installed.
 xchat-gnome depends on libgtk2.0-0 (>= 2.18.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
 xchat-gnome depends on libperl5.10 (>= 5.10.0); however:
  Package libperl5.10 is not installed.
dpkg: error processing xchat-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-wnck:
 python-wnck depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-wnck (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on libcanberra-gtk0 (>= 0.2); however:
  Package libcanberra-gtk0 is not installed.
 gnome-settings-daemon depends on libgnomekbd4 (>= 2.29.5); however:
  Package libgnomekbd4 is not configured yet.
 gnome-settings-daemon depends on libgtk2.0-0 (>= 2.18.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:3.2.0-7ubuntu4.2); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of metacity:
 metacity depends on libcanberra-gtk0 (>= 0.2); however:
  Package libcanberra-gtk0 is not installed.
 metacity depends on libgtk2.0-0 (>= 2.18.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing metacity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-desktop-2-17:
 libgnome-desktop-2-17 depends on libgtk2.0-0 (>= 2.18.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing libgnome-desktop-2-17 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnomeapplet:
 python-gnomeapplet depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-gnomeapplet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-mediaprofiles:
 python-mediaprofiles depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-mediaprofiles (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:3.2.0-7ubuntu4.2); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-window-settings1:
 libgnome-window-settings1 depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
 libgnome-window-settings1 depends on libgtk2.0-0 (>= 2.15.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing libgnome-window-settings1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpurple0:
 libpurple0 depends on libperl5.10 (>= 5.10.1); however:
  Package libperl5.10 is not installed.
dpkg: error processing libpurple0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-galaxy:
 openoffice.org-style-galaxy depends on openoffice.org-core (>= 1:3.2.0~beta); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-style-galaxy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-evince:
 python-evince depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnomecanvas:
 python-gnomecanvas depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-gnomecanvas (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdeskbar-tracker:
 libdeskbar-tracker depends on python-gnome2; however:
  Package python-gnome2 is not configured yet.
dpkg: error processing libdeskbar-tracker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit-1-gnome:
 policykit-1-gnome depends on libgtk2.0-0 (>= 2.17.1); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing policykit-1-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-totem-plparser:
 python-totem-plparser depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-totem-plparser (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on python-evince (>= 2.30.0-0ubuntu1.1); however:
  Package python-evince is not configured yet.
 python-gnome2-desktop depends on python-gnomeapplet (>= 2.30.0-0ubuntu1.1); however:
  Package python-gnomeapplet is not configured yet.
 python-gnome2-desktop depends on python-mediaprofiles (>= 2.30.0-0ubuntu1.1); however:
  Package python-mediaprofiles is not configured yet.
 python-gnome2-desktop depends on python-totem-plparser (>= 2.30.0-0ubuntu1.1); however:
  Package python-totem-plparser is not configured yet.
 python-gnome2-desktop depends on python-wnck (>= 2.30.0-0ubuntu1.1); however:
  Package python-wnck is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libappindicator0:
 libappindicator0 depends on libgtk2.0-0 (>= 2.18.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing libappindicator0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libevdocument2:
 libevdocument2 depends on libgtk2.0-0 (>= 2.14.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing libevdocument2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-cairo:
 python-cairo depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-cairo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libappindicator0 (>= 0.0.19); however:
  Package libappindicator0 is not configured yet.
 gnome-control-center depends on libcanberra-gtk0 (>= 0.2); however:
  Package libcanberra-gtk0 is not installed.
 gnome-control-center depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
 gnome-control-center depends on libgnome-window-settings1 (= 1:2.30.1-0ubuntu2); however:
  Package libgnome-window-settings1 is not configured yet.
 gnome-control-center depends on libgnomekbd4 (>= 2.29.5); however:
  Package libgnomekbd4 is not configured yet.
 gnome-control-center depends on libgtk2.0-0 (>= 2.18.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
 gnome-control-center depends on gnome-settings-daemon (>= 2.26); however:
  Package gnome-settings-daemon is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libevview2:
 libevview2 depends on libevdocument2 (>= 2.29.5); however:
  Package libevdocument2 is not configured yet.
 libevview2 depends on libgtk2.0-0 (>= 2.20.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing libevview2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-evolution:
 python-evolution depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-pyorbit:
 python-pyorbit depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-pyorbit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:3.2.0-7ubuntu4.2); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gtop:
 python-gtop depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-gtop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of irssi:
 irssi depends on libperl5.10 (>= 5.10.1); however:
  Package libperl5.10 is not installed.
dpkg: error processing irssi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:3.2.0-7ubuntu4.2); however:
  Package openoffice.org-core is not installed.
 openoffice.org-gtk depends on libgtk2.0-0 (>= 2.14.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnomeprint:
 python-gnomeprint depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-gnomeprint (--configure):
 dependency problems - leaving unconfigured
Setting up dictionaries-common (1.4.0ubuntu2) ...
Can't load '/usr/lib/perl5/auto/Text/Iconv/Iconv.so' for module Text::Iconv: /usr/lib/perl5/auto/Text/Iconv/Iconv.so: undefined symbol: Perl_Tcurpad_ptr at /usr/lib/perl/5.10/DynaLoader.pm line 193.
 at /usr/share/perl5/Debian/DictionariesCommon.pm line 6
Compilation failed in require at /usr/share/perl5/Debian/DictionariesCommon.pm line 6.
BEGIN failed--compilation aborted at /usr/share/perl5/Debian/DictionariesCommon.pm line 6.
Compilation failed in require at /usr/sbin/update-default-ispell line 3.
BEGIN failed--compilation aborted at /usr/sbin/update-default-ispell line 3.
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on gnome-settings-daemon (>= 2.26); however:
  Package gnome-settings-daemon is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml-editor0:
 libgtkhtml-editor0 depends on libgtk2.0-0 (>= 2.18.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing libgtkhtml-editor0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librsvg2-2:
 librsvg2-2 depends on libgtk2.0-0 (>= 2.16); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing librsvg2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserverui1.2-8:
 libedataserverui1.2-8 depends on libgtk2.0-0 (>= 2.14.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing libedataserverui1.2-8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtk2-perl:
 libgtk2-perl depends on libgtk2.0-0 (>= 2.18.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing libgtk2-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnomedesktop:
 python-gnomedesktop depends on libgnome-desktop-2-17 (>= 1:2.29.92); however:
  Package libgnome-desktop-2-17 is not configured yet.
 python-gnomedesktop depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-gnomedesktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of x11-common:
 x11-common depends on upstart-job; however:
  Package upstart-job is not installed.
dpkg: error processing x11-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-glade2:
 python-glade2 depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
 python-glade2 depends on libgtk2.0-0 (>= 2.19.0); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
dpkg: error processing python-glade2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of myspell-en-za:
 myspell-en-za depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing myspell-en-za (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.17.2-0); however:
  Version of util-linux on system is 2.13.1-5ubuntu3.1.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on libedataserverui1.2-8 (>= 2.28.3); however:
  Package libedataserverui1.2-8 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnomekeyring:
 python-gnomekeyring depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-gnomekeyring (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librsvg2-common:
 librsvg2-common depends on libgtk2.0-0 (>= 2.16); however:
  Version of libgtk2.0-0 on system is 2.12.9-3ubuntu5.
 librsvg2-common depends on librsvg2-2 (= 2.26.3-0ubuntu1.1); however:
  Package librsvg2-2 is not configured yet.
dpkg: error processing librsvg2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ufw:
 ufw depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
 ufw depends on upstart-job; however:
  Package upstart-job is not installed.
dpkg: error processing ufw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-rsvg:
 python-rsvg depends on librsvg2-2 (>= 2.26.0); however:
  Package librsvg2-2 is not configured yet.
 python-rsvg depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
 python-rsvg depends on librsvg2-common; however:
  Package librsvg2-common is not configured yet.
dpkg: error processing python-rsvg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-metacity:
 python-metacity depends on python (>= 2.6); however:
  Version of python on system is 2.5.2-0ubuntu1.
dpkg: error processing python-metacity (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 libgnomekbd4
 python-gnome2
 gdm
 initramfs-tools
 xchat-gnome
 python-wnck
 gnome-settings-daemon
 openoffice.org-gnome
 metacity
 libgnome-desktop-2-17
 python-gnomeapplet
 python-mediaprofiles
 openoffice.org-impress
 libgnome-window-settings1
 libpurple0
 openoffice.org-style-galaxy
 python-evince
 python-gnomecanvas
 libdeskbar-tracker
 policykit-1-gnome
 python-totem-plparser
 python-gnome2-desktop
 libappindicator0
 libevdocument2
 python-cairo
 gnome-control-center
 libevview2
 python-evolution
 python-pyorbit
 openoffice.org-draw
 python-gtop
 irssi
 openoffice.org-gtk
 python-gnomeprint
 dictionaries-common
 gnome-session
 libgtkhtml-editor0
 librsvg2-2
 libedataserverui1.2-8
 libgtk2-perl
 python-gnomedesktop
 x11-common
 python-glade2
 myspell-en-za
 util-linux-locales
 evolution-exchange
 python-gnomekeyring
 librsvg2-common
 ufw
 python-rsvg
 python-metacity
Processing was halted because there were too many errors.
[/PHP]


what should i do to fix this !!! please help me 

thanks in advance

---

### Post by konsole on 2011-12-17
> **&#1581 said:**
> [PHP]Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 8, in <module>
    from UpdateManager.Core.DistUpgradeFetcherCore import DistUpgradeFetcherCore
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 34, in <module>
    import GnuPGInterface
ImportError: No module named GnuPGInterface
[/PHP]

This is complaining that the python interface to gnupg is missing.

Install python-gnupginterface and retry the upgrade.

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-12-18
> **konsole said:**
> This is complaining that the python interface to gnupg is missing.

Install python-gnupginterface and retry the upgrade.

Thank you Mr. konsole 


i tried this
```
sudo aptitude reinstall python-gnupginterface
```then i got this :

[PHP]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  compiz-gnome evolution gdm gnome-applets gnome-control-center 
  gnome-screensaver gnome-session-bin gnome-settings-daemon initramfs-tools 
  irssi language-support-writing-en libappindicator0 libapt-pkg-perl 
  libauthen-pam-perl libcupsimage2 libdbusmenu-gtk1 libedataserverui1.2-8 
  libevdocument2 libevview2 libgnome-desktop-2-17 libgnome-window-settings1 
  libgnome2-canvas-perl libgnome2-perl libgnomekbd4 libgtk2-perl 
  libgtkhtml-editor0 libgtkhtml3.14-19 libgucharmap7 libindicator0 
  libmetacity-private0 libnet-ssleay-perl libpurple0 librsvg2-2 
  librsvg2-common libsnmp15 libsvn-perl libtext-iconv-perl 
  libxml-parser-perl metacity openoffice.org-base-core openoffice.org-calc 
  openoffice.org-draw openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-style-galaxy 
  openoffice.org-style-human openoffice.org-thesaurus-de 
  openoffice.org-thesaurus-de-ch openoffice.org-thesaurus-pl 
  openoffice.org-writer pidgin policykit-1-gnome python python-cairo 
  python-evince python-evolution python-gconf python-glade2 python-gnome2 
  python-gnomeapplet python-gnomecanvas python-gnomedesktop 
  python-gnomekeyring python-gnomeprint python-gobject python-gtk2 
  python-gtop python-mediaprofiles python-metacity python-pyorbit 
  python-rsvg python-totem-plparser python-uno python-wnck slapd udev ufw 
  util-linux-locales x11-common xchat xchat-gnome 
The following packages are unused and will be REMOVED:
  libdb4.2 libusplash0 xserver-xorg-video-psb xserver-xorg-video-via 
The following packages have been automatically kept back:
  ant ant-optional apt-show-versions aspell-de aspell-de-alt aspell-es 
  aspell-it aspell-nl aspell-pl aspell-pt-br aspell-pt-pt binfmt-support 
  binutils-static bogofilter-bdb bogofilter-common brazilian-conjugate 
  ca-certificates ca-certificates-java comerr-dev cupsddk cupsys 
  cupsys-client cupsys-common dbconfig-common dbus defoma devscripts 
  dupload eclipse-jdt eclipse-pde eclipse-platform eclipse-rcp expect 
  fakeroot fastjar filezilla-common finger firefox-branding 
  foomatic-filters fortunes-min freeglut3 gawk ghostscript gimp-help-de 
  gimp-help-es gimp-help-fr gimp-help-it gimp-help-nl gromit gsfonts hpijs 
  hplip hplip-data idutch ifrench-gut ingerman iogerman ipolish iportuguese 
  ispanish iswiss java-common javahelp2 jsvc junit junit4 
  language-pack-de-base language-pack-es-base language-pack-fr-base 
  language-pack-gnome-de-base language-pack-gnome-es-base 
  language-pack-gnome-fr-base language-pack-gnome-it-base 
  language-pack-gnome-nl-base language-pack-gnome-pl-base 
  language-pack-gnome-pt-base language-pack-it-base language-pack-nl-base 
  language-pack-pl-base language-pack-pt-base language-support-writing-de 
  language-support-writing-es language-support-writing-fr 
  language-support-writing-it language-support-writing-nl 
  language-support-writing-pl language-support-writing-pt liba52-0.7.4 
  libapm1 libappframework-java libarchive1 libaudio2 libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1 
  libbcel-java libbeansbinding-java libck-connector0 
  libcommons-beanutils-java libcommons-collections-java 
  libcommons-collections3-java libcommons-daemon-java libcommons-dbcp-java 
  libcommons-digester-java libcommons-el-java libcommons-launcher-java 
  libcommons-logging-java libcommons-modeler-java libcommons-pool-java 
  libconvert-binhex-perl libdaemon0 libdvdnav4 libecj-java libexif12 
  libfaac0 libfontenc1 libfreebob0 libfreemarker-java libfreetype6 libfs6 
  libgcj-bc libgcj-common libgeoip1 libgif4 libgl1-mesa-glx libglu1-mesa 
  libgomp1 libgphoto2-2 libgphoto2-port0 libgs8 libgsl0ldbl libgsm1 
  libgtkhtml3.16-cil libhal1 libice6 libid3tag0 libieee1284-3 libini4j-java 
  libio-stringy-perl libjack0 libjaxp1.3-java libjline-java libjpeg62 
  libjsch-java libjtidy-java libkrb5-dev liblaunchpad-integration1 
  liblog4j1.2-java liblucene2-java libmad0 libmailtools-perl libmatroska0 
  libmcrypt4 libmime-perl libmime-tools-perl libmodplug0c2 libmpcdec3 
  libmpeg2-4 libmx4j-java libnb-apisupport1-java libnb-javaparser-java 
  libnb-svnclientadapter-java libnet-daemon-perl libnxcl1 libpaper-utils 
  libpaper1 libplrpc-perl libquicktime1 librecode0 libregexp-java libsane 
  libsdl-image1.2 libsensors3 libservlet2.3-java libservlet2.4-java libslp1 
  libsm6 libsvn1 libswing-layout-java libswingworker-java libtar libtiff4 
  libvcdinfo0 libwxbase2.6-0 libwxbase2.8-0 libwxgtk2.6-0 libwxgtk2.8-0 
  libx11-data libx86-1 libxau6 libxaw7 libxcomp3 libxcompshad3 libxcursor1 
  libxdamage1 libxdmcp6 libxerces2-java libxext6 libxfce4util4 
  libxfcegui4-4 libxfixes3 libxfont1 libxft2 libxinerama1 libxkbfile1 
  libxml-commons-resolver1.1-java libxmlrpc-c3 libxmu6 libxmuu1 libxosd2 
  libxplc0.3.13 libxpm4 libxrender1 libxt6 libxtst6 libxv1 libxvidcore4 
  libxxf86dga1 libxxf86misc1 libxxf86vm1 m4 mbr mono-gmcs mono-xsp2-base 
  mscompress myspell-fr-gut myspell-it myspell-nl myspell-pl myspell-pt 
  myspell-pt-br myspell-pt-pt nethack-common odbcinst1debian1 openjdk-6-jdk 
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib 
  openoffice.org-hyphenation-de openoffice.org-hyphenation-it 
  openoffice.org-hyphenation-pl openoffice.org-l10n-de 
  openoffice.org-l10n-es openoffice.org-l10n-fr openoffice.org-l10n-it 
  openoffice.org-l10n-nl openoffice.org-l10n-pl openoffice.org-l10n-pt 
  openoffice.org-l10n-pt-br openoffice.org-thesaurus-it openssh-server 
  php-auth php-mail-mime php-net-smtp php-net-socket php-pear php5-cli 
  php5-mcrypt poppler-utils powermgmt-base python-gdata python-imaging 
  radeontool roundcube-core roundcube-mysql samba-common sqlite sqlite3 
  ssl-cert svn-buildpackage tcl8.4 thunderbird-locale-de 
  thunderbird-locale-es-ar thunderbird-locale-es-es thunderbird-locale-fr 
  thunderbird-locale-it thunderbird-locale-nl thunderbird-locale-pl 
  thunderbird-locale-pt-br thunderbird-locale-pt-pt tinymce 
  totem-plugins-extra ttf-dejavu ttf-dejavu-core ttf-dejavu-extra unixodbc 
  unp uuid-runtime vbetool vim-runtime wbrazilian wdutch wfrench winbind 
  wngerman wogerman wpolish wportuguese wspanish wswiss x11-apps 
  x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils 
  xauth xbitmaps xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings 
  xfonts-scalable xfonts-utils xinit xutils xutils-dev 
The following packages have been kept back:
  acl adduser adobe-flashplugin alacarte alsa-base alsa-utils anacron 
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common apmd 
  app-install-data app-install-data-commercial apparmor apparmor-utils 
  apport apport-gtk apt apt-utils aptitude apturl aspell aspell-en at 
  at-spi autoconf automake1.9 autotools-dev avahi-autoipd avahi-daemon 
  awstats bash bc bind9 bind9-host binutils bluez-cups bluez-utils 
  bogofilter brasero brltty brltty-x11 bsdmainutils bsdutils bug-buddy 
  build-essential bzip2 cdparanoia cdrdao cli-common command-not-found 
  command-not-found-data compiz compizconfig-backend-gconf console-setup 
  console-terminus console-tools coreutils cpio cpp cron cups-pdf 
  cupsys-bsd cupsys-driver-gutenprint curl dash dbus-x11 dc dcraw debconf 
  debconf-i18n deskbar-applet desktop-file-utils dhcp3-client dhcp3-common 
  dialog diff dmidecode dnsutils docbook-xml dosfstools dovecot-common 
  dovecot-imapd dovecot-pop3d dpkg-dev dvd+rw-tools e2fslibs e2fsprogs 
  eclipse ed eject ekiga eog esound-common espeak espeak-data ethtool 
  evince evolution-plugins evolution-webcal example-content f-spot fdutils 
  file file-roller filezilla firefox firefox-3.0 firefox-3.0-gnome-support 
  firefox-gnome-support fontconfig foo2zjs foomatic-db foomatic-db-engine 
  fortune-mod friendly-recovery ftp fuse-utils g++ gamin gcalctool gcc 
  gconf-editor gdb gdebi gdebi-core gedit gedit-common genisoimage 
  gettext-base ghostscript-x gimp gimp-data gimp-help-common gimp-help-en 
  gksu gmountiso gnome-about gnome-accessibility-themes gnome-app-install 
  gnome-desktop-data gnome-doc-utils gnome-games gnome-keyring gnome-mag 
  gnome-media gnome-media-common gnome-menus gnome-netstatus-applet 
  gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot 
  gnome-pilot-conduits gnome-power-manager gnome-system-monitor 
  gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes 
  gnome-user-guide gnome-utils gnupg gpgv grep groff-base 
  gstreamer0.10-alsa gstreamer0.10-ffmpeg gstreamer0.10-gnomevfs 
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base-apps 
  gstreamer0.10-tools gstreamer0.10-x gtk2-engines gtk2-engines-murrine 
  gtk2-engines-pixbuf gucharmap guile-1.6-libs gvfs gvfs-backends gzip hal 
  hal-cups-utils hal-info hdparm hicolor-icon-theme hostname 
  human-icon-theme human-theme hwtest hwtest-gtk iamerican ibritish 
  ifupdown im-switch info initscripts inputattach iproute iptables 
  iputils-arping iputils-ping iputils-tracepath iso-codes ispell klogd 
  landscape-client language-pack-de language-pack-en language-pack-en-base 
  language-pack-es language-pack-fr language-pack-gnome-de 
  language-pack-gnome-en language-pack-gnome-en-base language-pack-gnome-es 
  language-pack-gnome-fr language-pack-gnome-it language-pack-gnome-nl 
  language-pack-gnome-pl language-pack-gnome-pt language-pack-it 
  language-pack-nl language-pack-pl language-pack-pt language-selector 
  language-selector-common language-support-de language-support-en 
  language-support-es language-support-fr language-support-it 
  language-support-nl language-support-pl language-support-pt laptop-detect 
  launchpad-integration less lftp libaa1 libacl1 libalut0 libao2 
  libapache2-mod-php5 libapache2-mod-scgi libapr1 libaprutil1 libart-2.0-2 
  libart2.0-cil libaspell15 libatm1 libatspi1.0-0 libattr1 libaudiofile0 
  libavahi-glib1 libavahi-ui0 libavc1394-0 libbeagle1 libbonoboui2-0 
  libbonoboui2-common libbrlapi0.5 libbz2-1.0 libcairomm-1.0-1 
  libcdio-cdda0 libcdio-paranoia0 libcomerr2 libconsole 
  libconvert-asn1-perl libcurl3 libcurl3-gnutls libcurl4-openssl-dev 
  libcwidget3 libdb4.6 libdecoration0 libdevmapper1.02.1 libdmx1 libdv4 
  libedit2 libelfg0 libesd-alsa0 libespeak1 libexempi3 libexpat1 libflac8 
  libfribidi0 libfuse2 libgail-common libgail-gnome-module libgail18 
  libgamin0 libgc1c2 libgcc1 libgconf2.0-cil libgd2-noxpm libgdbm3 libggz2 
  libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libgl1-mesa-dri libglade2-0 
  libglade2.0-cil libglew1.5 libglib2.0-cil libglibmm-2.4-1c2a 
  libgnome-keyring0 libgnome-mag2 libgnome-media0 libgnome-pilot2 
  libgnome-speech7 libgnome-vfs2.0-cil libgnome2-0 libgnome2-common 
  libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-bin 
  libgpgme11 libgpod-common libgraphviz4 libgtk-vnc-1.0-0 libgtk2.0-0 
  libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgtkhtml2-0 
  libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 
  libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 
  libgtop2-common libguile-ltdl-1 libgutenprint2 libgvfscommon0 
  libhal-storage1 libhesiod0 libidl0 libjasper1 libkeyutils1 liblcms1 
  liblircclient0 liblpint-bonobo0 liblzo2-2 libmagic1 libmeanwhile1 libmng1 
  libmono-addins-gui0.2-cil libmono-addins0.2-cil libmono-cairo1.0-cil 
  libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil 
  libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-security1.0-cil 
  libmono-security2.0-cil libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil 
  libmono-sqlite2.0-cil libmono-system-data1.0-cil 
  libmono-system-data2.0-cil libmono-system-web1.0-cil 
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil 
  libmono0 libmono1.0-cil libmono2.0-cil libmusicbrainz4c2a 
  libnautilus-burn4 libnautilus-extension1 libncurses5 libncursesw5 
  libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libnet-ldap-perl 
  libnewt0.52 libnl1 libnspr4-0d libnss-mdns libnss3-1d libnxcl-bin libogg0 
  liboil0.3 liboobs-1-4 libopenobex1 liborbit2 libotr2 libpam-gnome-keyring 
  libpam-runtime libpam-smbpass libpanel-applet2-0 libpcap0.8 libpisock9 
  libpisync1 libpolkit-dbus2 libpolkit-gnome0 libpolkit-grant2 libpolkit2 
  libportaudio0 libpq5 libpt-1.10.10 libpt-1.10.10-plugins-alsa 
  libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpth20 
  libpulse-browse0 libqthreads-12 librarian0 libreadline5 librpc-xml-perl 
  libsamplerate0 libsasl2-2 libsasl2-modules libscim8c2a libsdl1.2debian 
  libsdl1.2debian-alsa libsexy2 libshout3 libsigc++-2.0-0c2a 
  libsigc++-2.0-dev libsigc++-2.0-doc libslang2 libsmbclient libsqlite0 
  libss2 libsysfs2 libtext-wrapi18n-perl libtimedate-perl libtool 
  libtracker-gtk0 libtrackerclient0 libusb-0.1-4 libvisual-0.4-0 
  libvorbis0a libvorbisenc2 libvorbisfile3 libvte-common libvte9 
  libwavpack1 libwmf0.2-7 libwnck-common libwnck22 libwpd8c2a libwpg-0.1-1 
  libwps-0.1-1 libwrap0 libx11-xcb1 libxcomposite1 libxml-twig-perl 
  libxml2-utils libxp6 libxres1 libxslt1.1 libxss1 lilo 
  linux-headers-generic linux-sound-base login logrotate lsb-release lshw 
  lsof ltrace lynx lzma make makedev man-db manpages mawk mcpp mdetect 
  mesa-utils migrationtools mii-diag mime-support min12xxw mktemp mlocate 
  module-init-tools mono-gac mono-runtime mono-xsp2 mount mousetweaks mtr 
  mutt mysql-server nano nautilus nautilus-cd-burner nautilus-data 
  nautilus-sendto ncurses-base net-tools netbase netbeans netcat 
  netcat-traditional nethack-x11 notification-daemon ntfs-3g ntpdate 
  nxproxy obex-data-server onboard openoffice.org-hyphenation 
  openoffice.org-hyphenation-en-us openoffice.org-l10n-en-gb 
  openoffice.org-l10n-en-za openoffice.org-thesaurus-en-au 
  openoffice.org-thesaurus-en-us openprinting-ppds openssh-blacklist 
  openssh-client openssl openssl-blacklist openssl-doc p7zip parted patch 
  pciutils pcmciautils perl-doc-html php5 php5-common php5-mysql 
  php5-xmlrpc phpmyadmin pidgin-otr pkg-config pm-utils pnm2ppa policykit 
  policykit-gnome popularity-contest postfix powernowd ppp pppconfig 
  pppoeconf procmail procps psmisc pulseaudio pulseaudio-esound-compat 
  pulseaudio-module-gconf pulseaudio-utils pxljr python-apport python-apt 
  python-brlapi python-cups python-dbus python-gdbm python-gmenu 
  python-gst0.10 python-gtksourceview2 python-launchpad-integration 
  python-libxml2 python-notify python-numeric python-problem-report 
  python-pyatspi python-scgi python-sexy python-software-properties 
  python-virtkey python-vte python-xdg rar rdesktop readahead 
  readline-common reiserfsprogs rhythmbox roundcube rss-glx rsync scim 
  scim-bridge-agent scim-bridge-client-gtk scim-gtk2-immodule 
  scim-modules-socket scim-modules-table scim-tables-additional screen 
  scrollkeeper seahorse sgml-data shared-mime-info smbclient smbfs smbnetfs 
  software-properties-gtk sound-juicer splix ssh-askpass-gnome strace 
  subversion sudo synaptic sysklogd system-config-printer-common 
  system-config-printer-gnome system-tools-backends sysv-rc sysvutils 
  tangerine-icon-theme tar tasksel tasksel-data tcpd tcpdump telnet 
  thunderbird-locale-en-gb time tomboy totem totem-common totem-gstreamer 
  totem-mozilla totem-plugins traceroute tracker tracker-search-tool 
  transmission-common transmission-gtk tree tsclient ttf-arabeyes 
  ttf-arphic-uming ttf-freefont ttf-indic-fonts-core ttf-kochi-gothic 
  ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-opensymbol ttf-thai-tlwg 
  ttf-unfonts-core ubufox ubuntu-artwork ubuntu-docs ubuntu-keyring 
  ubuntu-sounds ubuntu-wallpapers ucf unattended-upgrades unrar unrar-free 
  unzip update-inetd update-manager update-manager-core update-notifier 
  update-notifier-common upstart usbutils util-linux vim vim-common 
  vim-tiny vinagre vino vlc vlc-nox vlc-plugin-pulse vnc4server w3m 
  wamerican wbritish webalizer wget whiptail whois wine wodim wpasupplicant 
  wvdial x-ttcidfont-conf xbase-clients xcursor-themes xdg-user-dirs 
  xdg-user-dirs-gtk xdg-utils xfce4-appfinder xinetd xml-core 
  xml-rpc-api2cpp xorg xsane xsane-common xscreensaver-data xscreensaver-gl 
  xsltproc xterm xulrunner-1.9 yelp zenity zip 
The following packages will be REINSTALLED:
  python-gnupginterface 
The following partially installed packages will be configured:
  busybox-initramfs capplets-data compiz-core compiz-fusion-plugins-extra 
  compiz-fusion-plugins-main compiz-plugins consolekit dictionaries-common 
  doc-base evolution-common evolution-data-server evolution-exchange 
  fontconfig-config gconf2 gnome-applets-data gnome-icon-theme 
  gnome-session gstreamer0.10-nice gstreamer0.10-plugins-base 
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio hunspell-de-at 
  hunspell-de-ch hunspell-de-de ldap-utils libatk1.0-0 libbonobo2-0 
  libc6-i686 libcaca0 libcairo-perl libcairo2 libcamel1.2-14 libcanberra0 
  libcdparanoia0 libcompizconfig0 libcroco3 libcucul0 libdatrie1 
  libdbd-mysql-perl libdbi-perl libdbus-glib-1-2 libdbusmenu-glib1 
  libdeskbar-tracker libdevkit-power-gobject1 libdirectfb-1.2-0 
  libdrm-intel1 libebackend1.2-0 libebook1.2-9 libecal1.2-7 
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libeggdbus-1-0 
  libegroupwise1.2-13 libenchant1c2a libexchange-storage1.2-3 
  libfile-temp-perl libfontconfig1 libgconf2-4 libgdata-google1.2-1 
  libgdata1.2-1 libglib-perl libglib2.0-0 libgmime-2.4-2 libgnome-menu2 
  libgnome2-vfs-perl libgnomekbd-common libgnomevfs2-0 libgnomevfs2-common 
  libgnomevfs2-extra libgnutls26 libgsf-1-114 libgssapi-krb5-2 
  libgssdp-1.0-2 libgstfarsight0.10-0 libgstreamer-plugins-base0.10-0 
  libgstreamer0.10-0 libgudev-1.0-0 libgupnp-1.0-3 libgupnp-igd-1.0-2 
  libgweather-common libgweather1 libhtml-parser-perl libhtml-tagset-perl 
  libicu42 libio-pty-perl libjson-glib-1.0-0 libkrb5-3 libldap-2.4-2 
  libldap2-dev libmldbm-perl libnet-dbus-perl libnice0 libnih-dbus1 libnih1 
  libnotify1 libpango-perl libpango1.0-0 libpciaccess0 libpcre3 
  libpixman-1-0 libplymouth2 libpng12-0 libpolkit-agent-1-0 
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpulse-mainloop-glib0 
  libpulse0 libsoup-gnome2.4-1 libsoup2.4-1 libssl-dev 
  libstartup-notification0 libstlport4.6ldbl libtag1c2a libtemplate-perl 
  libterm-readkey-perl libthai0 libtotem-plparser17 libts-0.0-0 
  libunique-1.0-0 liburi-perl libuuid-perl libwww-perl libx11-6 libxi6 
  libxklavier16 libxrandr2 libxvmc1 libzephyr4 lp-solve metacity-common 
  myspell-en-gb myspell-en-za myspell-es openoffice.org-common 
  openoffice.org-help-de openoffice.org-help-it openoffice.org-help-nl 
  openoffice.org-help-pl openoffice.org-help-pt perl perl-doc perl-modules 
  policykit-1 python-bugbuddy python-central python-gnome2-desktop tsconf 
  ubuntu-system-service uno-libs3 ure xchat-common xchat-gnome-common 
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all 
  xserver-xorg-input-evdev xserver-xorg-input-mouse 
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse 
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm 
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips 
  xserver-xorg-video-cirrus xserver-xorg-video-dummy 
  xserver-xorg-video-fbdev xserver-xorg-video-geode 
  xserver-xorg-video-glint xserver-xorg-video-i128 xserver-xorg-video-i740 
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga 
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau 
  xserver-xorg-video-nv xserver-xorg-video-openchrome 
  xserver-xorg-video-r128 xserver-xorg-video-radeon 
  xserver-xorg-video-rendition xserver-xorg-video-s3 
  xserver-xorg-video-s3virge xserver-xorg-video-savage 
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis 
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx 
  xserver-xorg-video-trident xserver-xorg-video-tseng 
  xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware 
  xserver-xorg-video-voodoo zlib1g-dev 
0 packages upgraded, 0 newly installed, 1 reinstalled, 4 to remove and 1049 not upgraded.
Need to get 0B of archives. After unpacking 1655kB will be freed.
The following packages have unmet dependencies:
  policykit-1-gnome: Depends: libgtk2.0-0 (>= 2.17.1) but 2.12.9-3ubuntu5 is installed and it is kept back.
  libgnomekbd4: Depends: libgtk2.0-0 (>= 2.20.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  libpurple0: Depends: libperl5.10 (>= 5.10.1) but it is not installable
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installable
  openoffice.org-writer: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installable
  python-gnome2: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  metacity: Depends: libcanberra-gtk0 (>= 0.2) but it is not installable
            Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  openoffice.org-impress: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installable
  libindicator0: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  libsnmp15: Depends: libperl5.8 (>= 5.8.8) which is a virtual package.
  gnome-settings-daemon: Depends: libcanberra-gtk0 (>= 0.2) but it is not installable
                         Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  language-support-writing-en: Depends: myspell-en-us but it is not installable
  openoffice.org-draw: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installable
  python-evince: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  python-gnomecanvas: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  libnet-ssleay-perl: Depends: perlapi-5.8.7 which is a virtual package.
  evolution: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installable
                      Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  slapd: Depends: libperl5.10 (>= 5.10.1) but it is not installable
  xchat: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
         Depends: libperl5.10 (>= 5.10.1) but it is not installable
  gnome-screensaver: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  libevview2: Depends: libgtk2.0-0 (>= 2.20.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  gnome-control-center: Depends: libcanberra-gtk0 (>= 0.2) but it is not installable
                        Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  libgnome2-perl: Depends: perlapi-5.8.7 which is a virtual package.
  libgtkhtml-editor0: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  python-pyorbit: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  python-gconf: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  libapt-pkg-perl: Depends: perlapi-5.8.8 which is a virtual package.
  openoffice.org-style-human: Depends: openoffice.org-common (= 1:2.4.1-1ubuntu2.5) but 1:3.2.0-7ubuntu4.2 is installed.
  libxml-parser-perl: Depends: perlapi-5.8.8 which is a virtual package.
  util-linux-locales: Depends: util-linux (>= 2.17.2-0) but 2.13.1-5ubuntu3.1 is installed and it is kept back.
  initramfs-tools: Depends: util-linux (> 2.15~rc1) but 2.13.1-5ubuntu3.1 is installed and it is kept back.
  python-gnomedesktop: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  openoffice.org-style-galaxy: Depends: openoffice.org-core (>= 1:3.2.0~beta) but it is not installable
  udev: Depends: upstart-job which is a virtual package.
        Depends: util-linux (> 2.15~rc2) but 2.13.1-5ubuntu3.1 is installed and it is kept back.
  libauthen-pam-perl: Depends: perlapi-5.8.7 which is a virtual package.
  gdm: Depends: libcanberra-gtk0 (>= 0.4) but it is not installable
       Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
       Depends: upstart-job which is a virtual package.
  python-gnomeprint: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  python-glade2: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
                 Depends: libgtk2.0-0 (>= 2.19.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  python-uno: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2.5) but it is not installable
  python: Depends: python-minimal (= 2.5.2-0ubuntu1) but 2.6.5-0ubuntu1 is installed.
  libdbusmenu-gtk1: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  libgtk2-perl: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  gnome-session-bin: Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  python-metacity: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  openoffice.org-base-core: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installable
  libevdocument2: Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  python-rsvg: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  python-gnomeapplet: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  python-mediaprofiles: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  libedataserverui1.2-8: Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  libtext-iconv-perl: Depends: perlapi-5.8.7 which is a virtual package.
  libgnome-window-settings1: Depends: libgtk2.0-0 (>= 2.15.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  xchat-gnome: Depends: libcanberra-gtk0 (>= 0.3) but it is not installable
               Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
               Depends: libperl5.10 (>= 5.10.0) but it is not installable
  python-gnomekeyring: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  ufw: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
       Depends: upstart-job which is a virtual package.
  libappindicator0: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  python-totem-plparser: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  libcupsimage2: Depends: libcups2 (>= 1.4.0) but it is not installable
  python-evolution: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  librsvg2-2: Depends: libgtk2.0-0 (>= 2.16) but 2.12.9-3ubuntu5 is installed and it is kept back.
  openoffice.org-thesaurus-de-ch: Depends: openoffice.org-core (>= 1.9) but it is not installable
  x11-common: Depends: upstart-job which is a virtual package.
  pidgin: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  libgucharmap7: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  gnome-applets: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  irssi: Depends: libperl5.10 (>= 5.10.1) but it is not installable
  python-wnck: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  libgnome-desktop-2-17: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  openoffice.org-thesaurus-de: Depends: openoffice.org-core (>= 1.9) but it is not installable
  openoffice.org-calc: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installable
  libsvn-perl: Depends: perlapi-5.8.8 which is a virtual package.
  openoffice.org-thesaurus-pl: Depends: openoffice.org-core (>= 1.9) but it is not installable
  librsvg2-common: Depends: libgtk2.0-0 (>= 2.16) but 2.12.9-3ubuntu5 is installed and it is kept back.
  python-gtk2: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
               Depends: libgtk2.0-0 (>= 2.19.1) but 2.12.9-3ubuntu5 is installed and it is kept back.
  python-cairo: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  libgnome2-canvas-perl: Depends: perlapi-5.8.8 which is a virtual package.
  libgtkhtml3.14-19: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  compiz-gnome: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed and it is kept back.
  python-gtop: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  python-gobject: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed and it is kept back.
  libmetacity-private0: Depends: libcanberra-gtk0 (>= 0.2) but it is not installable

[/PHP][PHP]Resolving dependencies...
open: 5292; closed: 4947; defer: 0; conflict: 11                               oNo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 10732; closed: 9958; defer: 0; conflict: 12                              .No solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 16132; closed: 14941; defer: 0; conflict: 12                             ONo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 21491; closed: 19897; defer: 0; conflict: 12                             .No solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 26956; closed: 24930; defer: 0; conflict: 12                             .No solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 32359; closed: 29936; defer: 0; conflict: 12                             oNo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 37792; closed: 34952; defer: 0; conflict: 12                             oNo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 43182; closed: 39946; defer: 0; conflict: 12                             ONo solution found within the allotted time.  Try harder? [Y/n]

No solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 48565; closed: 44952; defer: 0; conflict: 12                             oNo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 53970; closed: 49989; defer: 0; conflict: 12                             ONo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 59337; closed: 54983; defer: 0; conflict: 12                             ONo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 64659; closed: 59951; defer: 0; conflict: 12                             oNo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 69992; closed: 64931; defer: 0; conflict: 12                             ONo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 75330; closed: 69905; defer: 0; conflict: 12                             ONo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 80697; closed: 74933; defer: 0; conflict: 12                             .No solution found within the allotted time.  Try harder? [Y/n]

No solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 85974; closed: 79872; defer: 0; conflict: 12                             oNo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 91453; closed: 84924; defer: 0; conflict: 14                             oNo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 98473; closed: 89925; defer: 0; conflict: 14                             oNo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 105764; closed: 94934; defer: 0; conflict: 14                                                  oNo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 112937; closed: 99898; defer: 0; conflict: 14                                                  ONo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 120306; closed: 104976; defer: 0; conflict: 14                                                 ONo solution found within the allotted time.  Try harder? [Y/n]

................................

open: 173710; closed: 141878; defer: 0; conflict: 29                                                 oE: I wasn't able to locate file for the myspell-fr-gut package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Remove the following packages:
apport
apport-gtk
aptitude
apturl
bluez-cups
cups-pdf
cupsddk-drivers
cupsys
cupsys-bsd
cupsys-driver-gutenprint
displayconfig-gtk
firefox-3.0-gnome-support
firefox-gnome-support
foomatic-db-hpijs
gimp
gimp-data
gimp-gnomevfs
gimp-python
gnome-app-install
guidance-backends
hal-cups-utils
hpijs
hplip
language-selector
libcupsys2
libgimp2.0
openoffice.org-base-core
openoffice.org-calc
openoffice.org-common
openoffice.org-draw
openoffice.org-gnome
openoffice.org-gtk
openoffice.org-impress
openoffice.org-style-galaxy
openoffice.org-style-human
openoffice.org-writer
python-apport
python-gtkhtml2
python-uno
software-properties-gtk
splix
startup-tasks
synaptic
system-config-printer-common
system-config-printer-gnome
system-services
tasksel
tasksel-data
ubufox
update-manager
update-manager-core
update-notifier
upstart-compat-sysv
upstart-logd
xsane
xsane-common

Install the following packages:
apache2.2-bin [2.2.14-5ubuntu8.7 (lucid-updates, lucid-security, lucid-updates)]
cups-client [1.4.3-1ubuntu1.5 (lucid-updates, lucid-security, lucid-updates)]
cups-common [1.4.3-1ubuntu1.5 (lucid-updates, lucid-security, lucid-updates)]
cups-ppdc [1.4.3-1ubuntu1.5 (lucid-updates, lucid-security, lucid-updates)]
enscript [1.6.5-1 (lucid, lucid)]
fancontrol [1:3.1.2-2 (lucid, lucid)]
libaprutil1-dbd-sqlite3 [1.3.9+dfsg-3ubuntu0.10.04.1 (lucid-updates, lucid-security, lucid-updates)]
libaprutil1-ldap [1.3.9+dfsg-3ubuntu0.10.04.1 (lucid-updates, lucid-security, lucid-updates)]
libcanberra-gtk-module [0.22-1ubuntu2 (lucid, lucid)]
libcanberra-gtk0 [0.22-1ubuntu2 (lucid, lucid)]
libcap2 [1:2.17-2ubuntu1 (lucid, lucid)]
libcups2 [1.4.3-1ubuntu1.5 (lucid-updates, lucid-security, lucid-updates)]
libcupsppdc1 [1.4.3-1ubuntu1.5 (lucid-updates, lucid-security, lucid-updates)]
libneon27-gnutls [0.29.0-1 (lucid, lucid)]
libperl5.10 [5.10.1-8ubuntu2.1 (lucid-updates, lucid-security, lucid-updates)]
libsensors4 [1:3.1.2-2 (lucid, lucid)]
lm-sensors [1:3.1.2-2 (lucid, lucid)]
mountall [2.14 (lucid, lucid)]
myspell-en-us [1:3.2.0-3ubuntu3.1 (lucid-updates, lucid-updates)]
plymouth [0.8.2-2ubuntu2 (lucid, lucid)]
plymouth-theme-ubuntu-text [0.8.2-2ubuntu2.2 (lucid-updates, lucid-updates)]

Upgrade the following packages:
apache2-mpm-prefork [2.2.8-1ubuntu0.22 (now) -> 2.2.14-5ubuntu8.7 (lucid-updates, lucid-security,
lucid-updates)]
apache2.2-common [2.2.8-1ubuntu0.22 (now) -> 2.2.14-5ubuntu8.7 (lucid-updates, lucid-security,
lucid-updates)]
apt [0.7.9ubuntu17.4 (now) -> 0.7.25.3ubuntu9.9 (lucid-updates, lucid-security, lucid-updates)]
apt-utils [0.7.9ubuntu17.4 (now) -> 0.7.25.3ubuntu9.9 (lucid-updates, lucid-security, lucid-updates)]
coreutils [6.10-3ubuntu2 (now) -> 7.4-2ubuntu3 (lucid-updates, lucid-updates)]
cupsddk [1.2.0-0ubuntu1 (now) -> 1.4.3-1ubuntu1.5 (lucid-updates, lucid-security, lucid-updates)]
cupsys-client [1.3.7-1ubuntu3.13 (now) -> 1.4.3-1ubuntu1.5 (lucid-updates, lucid-security,
lucid-updates)]
cupsys-common [1.3.7-1ubuntu3.13 (now) -> 1.4.3-1ubuntu1.5 (lucid-updates, lucid-security,
lucid-updates)]
deskbar-applet [2.22.3.1-0ubuntu1 (now) -> 2.30.0-0ubuntu1 (lucid, lucid)]
firefox [3.6.17+build3+nobinonly-0ubuntu0.8.04.1 (now) -> 3.6.24+build2+nobinonly-0ubuntu0.10.04.1
(lucid-updates, lucid-security, lucid-updates)]
firefox-branding [3.6.17+build3+nobinonly-0ubuntu0.8.04.1 (now) ->
3.6.24+build2+nobinonly-0ubuntu0.10.04.1 (lucid-updates, lucid-security, lucid-updates)]
gnome-menus [2.22.2-0ubuntu1 (now) -> 2.30.0-0ubuntu4 (lucid, lucid)]
gtk2-engines-pixbuf [2.12.9-3ubuntu5 (now) -> 2.20.1-0ubuntu2.1 (lucid-updates, lucid-updates)]
hplip-data [2.8.2-0ubuntu8.2 (now) -> 3.10.2-2ubuntu2.2 (lucid-updates, lucid-security,
lucid-updates)]
ifupdown [0.6.8ubuntu8 (now) -> 0.6.8ubuntu29.2 (lucid-updates, lucid-security, lucid-updates)]
libapr1 [1.2.11-1ubuntu0.2 (now) -> 1.3.8-1ubuntu0.3 (lucid-updates, lucid-security, lucid-updates)]
libaprutil1 [1.2.12+dfsg-3ubuntu0.3 (now) -> 1.3.9+dfsg-3ubuntu0.10.04.1 (lucid-updates,
lucid-security, lucid-updates)]
libapt-pkg-perl [0.1.21build3 (now) -> 0.1.24 (lucid, lucid)]
libauthen-pam-perl [0.16-1 (now) -> 0.16-2 (lucid, lucid)]
libgnome2-canvas-perl [1.002-1+b1ubuntu1 (now) -> 1.002-2build1 (lucid, lucid)]
libgnome2-perl [1.040-1 (now) -> 1.042-2build1 (lucid, lucid)]
libgnomecups1.0-1 [0.2.3-1ubuntu1 (now) -> 0.2.3-3build2 (lucid, lucid)]
libgnomeprint2.2-0 [2.18.4-1 (now) -> 2.18.6-1build2 (lucid, lucid)]
libgnomeprint2.2-data [2.18.4-1 (now) -> 2.18.6-1build2 (lucid, lucid)]
libgs8 [8.61.dfsg.1-1ubuntu3.3 (now) -> 8.71.dfsg.1-0ubuntu5.3 (lucid-updates, lucid-updates)]
libgtk2.0-0 [2.12.9-3ubuntu5 (now) -> 2.20.1-0ubuntu2.1 (lucid-updates, lucid-updates)]
libgtksourceview2.0-0 [2.2.2-0ubuntu1 (now) -> 2.10.4-0ubuntu1 (lucid-updates, lucid-updates)]
libgtksourceview2.0-common [2.2.2-0ubuntu1 (now) -> 2.10.4-0ubuntu1 (lucid-updates, lucid-updates)]
libnet-ssleay-perl [1.30-1 (now) -> 1.35-2ubuntu1 (lucid, lucid)]
libsnmp15 [5.4.1~dfsg-4ubuntu4.3 (now) -> 5.4.2.1~dfsg0ubuntu1-0ubuntu2.1 (lucid-updates,
lucid-security, lucid-updates)]
libsvn-perl [1.4.6dfsg1-2ubuntu1.3 (now) -> 1.6.6dfsg-2ubuntu1.3 (lucid-updates, lucid-security,
lucid-updates)]
libsvn1 [1.4.6dfsg1-2ubuntu1.3 (now) -> 1.6.6dfsg-2ubuntu1.3 (lucid-updates, lucid-security,
lucid-updates)]
libtext-iconv-perl [1.4-3 (now) -> 1.7-2 (lucid, lucid)]
libvte9 [1:0.16.13-1ubuntu1 (now) -> 1:0.23.5-0ubuntu1.1 (lucid-updates, lucid-security,
lucid-updates)]
libxml-parser-perl [2.34-4.3 (now) -> 2.36-1.1build3 (lucid, lucid)]
min12xxw [0.0.9-1build1 (now) -> 0.0.9-3ubuntu2 (lucid, lucid)]
netbase [4.30ubuntu1 (now) -> 4.35ubuntu3 (lucid, lucid)]
openoffice.org-hyphenation-pl [20070207-1 (now) -> 1:3.0a-3 (lucid, lucid)]
openoffice.org-thesaurus-de [20070408-3 (now) -> 20080808-3ubuntu1 (lucid, lucid)]
openoffice.org-thesaurus-de-ch [20070408-3 (now) -> 20080808-3ubuntu1 (lucid, lucid)]
openoffice.org-thesaurus-pl [1.4-1 (now) -> 1.5-3ubuntu1 (lucid, lucid)]
python [2.5.2-0ubuntu1 (now) -> 2.6.5-0ubuntu1 (lucid, lucid)]
python-apt [0.7.4ubuntu7.7 (now) -> 0.7.94.2ubuntu6.4 (lucid-updates, lucid-updates)]
python-brlapi [3.9-6ubuntu1 (now) -> 4.1-2ubuntu6 (lucid, lucid)]
python-cups [1.9.34-0ubuntu1 (now) -> 1.9.49-0ubuntu1 (lucid, lucid)]
python-dbus [0.82.4-1ubuntu1 (now) -> 0.83.0-1ubuntu3 (lucid, lucid)]
python-gdbm [2.5.2-0ubuntu2 (now) -> 2.6.5-0ubuntu2 (lucid, lucid)]
python-gmenu [2.22.2-0ubuntu1 (now) -> 2.30.0-0ubuntu4 (lucid, lucid)]
python-gst0.10 [0.10.11-1 (now) -> 0.10.18-1 (lucid, lucid)]
python-gtksourceview2 [2.2.0-0ubuntu2 (now) -> 2.10.1-0ubuntu1 (lucid-updates, lucid-updates)]
python-imaging [1.1.6-1ubuntu5 (now) -> 1.1.7-1ubuntu0.1 (lucid-updates, lucid-updates)]
python-launchpad-integration [0.1.19 (now) -> 0.1.35 (lucid, lucid)]
python-libxml2 [2.6.31.dfsg-2ubuntu1.6 (now) -> 2.7.6.dfsg-1ubuntu1.2 (lucid-updates, lucid-security,
lucid-updates)]
python-notify [0.1.1-2 (now) -> 0.1.1-2build3 (lucid, lucid)]
python-numeric [24.2-8ubuntu2 (now) -> 24.2-9ubuntu1 (lucid, lucid)]
python-problem-report [0.108.4 (now) -> 1.13.3-0ubuntu2.1 (lucid-updates, lucid-updates)]
python-scgi [1.12-0.2 (now) -> 1.13-1 (lucid, lucid)]
python-sexy [0.1.9-1ubuntu1 (now) -> 0.1.9-1ubuntu3 (lucid, lucid)]
python-virtkey [0.50ubuntu0.1 (now) -> 0.50ubuntu3 (lucid, lucid)]
python-vte [1:0.16.13-1ubuntu1 (now) -> 1:0.23.5-0ubuntu1.1 (lucid-updates, lucid-security,
lucid-updates)]
python-xdg [0.15-1.1ubuntu3 (now) -> 0.18-1ubuntu2 (lucid, lucid)]
subversion [1.4.6dfsg1-2ubuntu1.3 (now) -> 1.6.6dfsg-2ubuntu1.3 (lucid-updates, lucid-security,
lucid-updates)]
upstart [0.3.9-2 (now) -> 0.6.5-6 (lucid, lucid)]
util-linux [2.13.1-5ubuntu3.1 (now) -> 2.17.2-0ubuntu1.10.04.2 (lucid-updates, lucid-updates)]

Downgrade the following packages:
libplymouth2 [0.8.2-2ubuntu2.2 (lucid-updates, lucid-updates, now) -> 0.8.2-2ubuntu2 (lucid, lucid)]


[/PHP][PHP]
Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
firefox recommends ubufox
nautilus recommends gnome-app-install
Score is 4839

Accept this solution? [Y/n/q/?] Y

The following packages are unused and will be REMOVED:
  cupsddk hplip-data libdb4.2 libieee1284-3 libsane libsensors3 libsnmp-base libsnmp15 
  libusplash0 python-imaging xserver-xorg-video-psb xserver-xorg-video-via 
The following packages have been automatically kept back:
  ant ant-optional apt-show-versions aspell-de aspell-de-alt aspell-es aspell-it aspell-nl 
  aspell-pl aspell-pt-br aspell-pt-pt binfmt-support binutils-static bogofilter-bdb 
  bogofilter-common brazilian-conjugate ca-certificates ca-certificates-java comerr-dev 
  dbconfig-common dbus defoma devscripts dupload eclipse-jdt eclipse-pde eclipse-platform 
  eclipse-rcp expect fakeroot fastjar filezilla-common finger foomatic-filters fortunes-min 
  freeglut3 gawk ghostscript gimp-help-de gimp-help-es gimp-help-fr gimp-help-it gimp-help-nl 
  gromit gsfonts idutch ifrench-gut ingerman iogerman ipolish iportuguese ispanish iswiss 
  java-common javahelp2 jsvc junit junit4 language-pack-de-base language-pack-es-base 
  language-pack-fr-base language-pack-gnome-de-base language-pack-gnome-es-base 
  language-pack-gnome-fr-base language-pack-gnome-it-base language-pack-gnome-nl-base 
  language-pack-gnome-pl-base language-pack-gnome-pt-base language-pack-it-base 
  language-pack-nl-base language-pack-pl-base language-pack-pt-base language-support-writing-de 
  language-support-writing-es language-support-writing-fr language-support-writing-it 
  language-support-writing-nl language-support-writing-pl language-support-writing-pt 
  liba52-0.7.4 libapm1 libappframework-java libarchive1 libaudio2 libavahi-client3 
  libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1 libbcel-java 
  libbeansbinding-java libck-connector0 libcommons-beanutils-java libcommons-collections-java 
  libcommons-collections3-java libcommons-daemon-java libcommons-dbcp-java 
  libcommons-digester-java libcommons-el-java libcommons-launcher-java libcommons-logging-java 
  libcommons-modeler-java libcommons-pool-java libconvert-binhex-perl libdaemon0 libdvdnav4 
  libecj-java libexif12 libfaac0 libfontenc1 libfreebob0 libfreemarker-java libfreetype6 libfs6 
  libgcj-bc libgcj-common libgeoip1 libgif4 libgl1-mesa-glx libglu1-mesa libgomp1 libgphoto2-2 
  libgphoto2-port0 libgsl0ldbl libgsm1 libgtkhtml3.16-cil libhal1 libice6 libid3tag0 
  libini4j-java libio-stringy-perl libjack0 libjaxp1.3-java libjline-java libjpeg62 libjsch-java 
  libjtidy-java libkrb5-dev liblaunchpad-integration1 liblog4j1.2-java liblucene2-java libmad0 
  libmailtools-perl libmatroska0 libmcrypt4 libmime-perl libmime-tools-perl libmodplug0c2 
  libmpcdec3 libmpeg2-4 libmx4j-java libnb-apisupport1-java libnb-javaparser-java 
  libnb-svnclientadapter-java libnet-daemon-perl libnxcl1 libpaper-utils libpaper1 libplrpc-perl 
  libquicktime1 librecode0 libregexp-java libsdl-image1.2 libservlet2.3-java libservlet2.4-java 
  libslp1 libsm6 libswing-layout-java libswingworker-java libtar libtiff4 libvcdinfo0 
  libwxbase2.6-0 libwxbase2.8-0 libwxgtk2.6-0 libwxgtk2.8-0 libx11-data libx86-1 libxau6 libxaw7 
  libxcomp3 libxcompshad3 libxcursor1 libxdamage1 libxdmcp6 libxerces2-java libxext6 
  libxfce4util4 libxfcegui4-4 libxfixes3 libxfont1 libxft2 libxinerama1 libxkbfile1 
  libxml-commons-resolver1.1-java libxmlrpc-c3 libxmu6 libxmuu1 libxosd2 libxplc0.3.13 libxpm4 
  libxrender1 libxt6 libxtst6 libxv1 libxvidcore4 libxxf86dga1 libxxf86misc1 libxxf86vm1 m4 mbr 
  mono-gmcs mono-xsp2-base mscompress myspell-fr-gut myspell-it myspell-nl myspell-pl myspell-pt 
  myspell-pt-br myspell-pt-pt nethack-common odbcinst1debian1 openjdk-6-jdk openjdk-6-jre 
  openjdk-6-jre-headless openjdk-6-jre-lib openoffice.org-hyphenation-de 
  openoffice.org-hyphenation-it openoffice.org-l10n-de openoffice.org-l10n-es 
  openoffice.org-l10n-fr openoffice.org-l10n-it openoffice.org-l10n-nl openoffice.org-l10n-pl 
  openoffice.org-l10n-pt openoffice.org-l10n-pt-br openoffice.org-thesaurus-it openssh-server 
  php-auth php-mail-mime php-net-smtp php-net-socket php-pear php5-cli php5-mcrypt poppler-utils 
  powermgmt-base python-gdata radeontool roundcube-core roundcube-mysql samba-common sqlite 
  sqlite3 ssl-cert svn-buildpackage tcl8.4 thunderbird-locale-de thunderbird-locale-es-ar 
  thunderbird-locale-es-es thunderbird-locale-fr thunderbird-locale-it thunderbird-locale-nl 
  thunderbird-locale-pl thunderbird-locale-pt-br thunderbird-locale-pt-pt tinymce 
  totem-plugins-extra ttf-dejavu ttf-dejavu-core ttf-dejavu-extra unixodbc unp uuid-runtime 
  vbetool vim-runtime wbrazilian wdutch wfrench winbind wngerman wogerman wpolish wportuguese 
  wspanish wswiss x11-apps x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils 
  x11-xserver-utils xauth xbitmaps xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings 
  xfonts-scalable xfonts-utils xinit xutils xutils-dev 
The following NEW packages will be automatically installed:
  apache2.2-bin cups-client cups-common enscript libaprutil1-dbd-sqlite3 libaprutil1-ldap 
  libcanberra-gtk-module libcanberra-gtk0 libcap2 libcups2 libneon27-gnutls libperl5.10 mountall 
  myspell-en-us plymouth plymouth-theme-ubuntu-text 
The following packages will be automatically REMOVED:
  apport apport-gtk aptitude apturl bluez-cups cups-pdf cupsddk-drivers cupsys cupsys-bsd 
  cupsys-driver-gutenprint displayconfig-gtk firefox-3.0-gnome-support firefox-gnome-support 
  foomatic-db-hpijs gimp gimp-data gimp-gnomevfs gimp-python gnome-app-install guidance-backends 
  hal-cups-utils hpijs hplip language-selector libcupsys2 libgimp2.0 openoffice.org-base-core 
  openoffice.org-calc openoffice.org-common openoffice.org-draw openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-style-galaxy 
  openoffice.org-style-human openoffice.org-writer python-apport python-gtkhtml2 python-uno 
  software-properties-gtk splix startup-tasks synaptic system-config-printer-common 
  system-config-printer-gnome system-services tasksel tasksel-data ubufox update-manager 
  update-manager-core update-notifier upstart-compat-sysv upstart-logd xsane xsane-common 
The following packages will be DOWNGRADED:
  libplymouth2 
The following packages have been kept back:
  acl adduser adobe-flashplugin alacarte alsa-base alsa-utils anacron apache2 apache2-utils apmd 
  app-install-data app-install-data-commercial apparmor apparmor-utils aspell aspell-en at at-spi 
  autoconf automake1.9 autotools-dev avahi-autoipd avahi-daemon awstats bash bc bind9 bind9-host 
  binutils bluez-utils bogofilter brasero brltty brltty-x11 bsdmainutils bsdutils bug-buddy 
  build-essential bzip2 cdparanoia cdrdao cli-common command-not-found command-not-found-data 
  compiz compizconfig-backend-gconf console-setup console-terminus console-tools cpio cpp cron 
  curl dash dbus-x11 dc dcraw debconf debconf-i18n desktop-file-utils dhcp3-client dhcp3-common 
  dialog diff dmidecode dnsutils docbook-xml dosfstools dovecot-common dovecot-imapd 
  dovecot-pop3d dpkg-dev dvd+rw-tools e2fslibs e2fsprogs eclipse ed eject ekiga eog esound-common 
  espeak espeak-data ethtool evince evolution-plugins evolution-webcal example-content f-spot 
  fdutils file file-roller filezilla firefox-3.0 fontconfig foo2zjs foomatic-db 
  foomatic-db-engine fortune-mod friendly-recovery ftp fuse-utils g++ gamin gcalctool gcc 
  gconf-editor gdb gdebi gdebi-core gedit gedit-common genisoimage gettext-base ghostscript-x 
  gimp-help-common gimp-help-en gksu gmountiso gnome-about gnome-accessibility-themes 
  gnome-desktop-data gnome-doc-utils gnome-games gnome-keyring gnome-mag gnome-media 
  gnome-media-common gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data 
  gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-system-monitor gnome-system-tools 
  gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnupg gpgv grep 
  groff-base gstreamer0.10-alsa gstreamer0.10-ffmpeg gstreamer0.10-gnomevfs 
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base-apps gstreamer0.10-tools 
  gstreamer0.10-x gtk2-engines gtk2-engines-murrine gucharmap guile-1.6-libs gvfs gvfs-backends 
  gzip hal hal-info hdparm hicolor-icon-theme hostname human-icon-theme human-theme hwtest 
  hwtest-gtk iamerican ibritish im-switch info initscripts inputattach iproute iptables 
  iputils-arping iputils-ping iputils-tracepath iso-codes ispell klogd landscape-client 
  language-pack-de language-pack-en language-pack-en-base language-pack-es language-pack-fr 
  language-pack-gnome-de language-pack-gnome-en language-pack-gnome-en-base 
  language-pack-gnome-es language-pack-gnome-fr language-pack-gnome-it language-pack-gnome-nl 
  language-pack-gnome-pl language-pack-gnome-pt language-pack-it language-pack-nl 
  language-pack-pl language-pack-pt language-selector-common language-support-de 
  language-support-en language-support-es language-support-fr language-support-it 
  language-support-nl language-support-pl language-support-pt language-support-writing-en 
  laptop-detect launchpad-integration less lftp libaa1 libacl1 libalut0 libao2 
  libapache2-mod-php5 libapache2-mod-scgi libart-2.0-2 libart2.0-cil libaspell15 libatm1 
  libatspi1.0-0 libattr1 libaudiofile0 libavahi-glib1 libavahi-ui0 libavc1394-0 libbeagle1 
  libbonoboui2-0 libbonoboui2-common libbrlapi0.5 libbz2-1.0 libcairomm-1.0-1 libcdio-cdda0 
  libcdio-paranoia0 libcomerr2 libconsole libconvert-asn1-perl libcurl3 libcurl3-gnutls 
  libcurl4-openssl-dev libcwidget3 libdb4.6 libdecoration0 libdevmapper1.02.1 libdmx1 libdv4 
  libedit2 libelfg0 libesd-alsa0 libespeak1 libexempi3 libexpat1 libflac8 libfribidi0 libfuse2 
  libgail-common libgail-gnome-module libgail18 libgamin0 libgc1c2 libgcc1 libgconf2.0-cil 
  libgd2-noxpm libgdbm3 libggz2 libggzcore9 libggzmod4 libgksu2-0 libgl1-mesa-dri libglade2-0 
  libglade2.0-cil libglew1.5 libglib2.0-cil libglibmm-2.4-1c2a libgnome-keyring0 libgnome-mag2 
  libgnome-media0 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.0-cil libgnome2-0 
  libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common libgnomeprintui2.2-0 
  libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-bin libgpgme11 
  libgpod-common libgraphviz4 libgtk-vnc-1.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common 
  libgtkhtml2-0 libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 
  libgtop2-7 libgtop2-common libguile-ltdl-1 libgutenprint2 libgvfscommon0 libhal-storage1 
  libhesiod0 libidl0 libjasper1 libkeyutils1 liblcms1 liblircclient0 liblpint-bonobo0 liblzo2-2 
  libmagic1 libmeanwhile1 libmng1 libmono-addins-gui0.2-cil libmono-addins0.2-cil 
  libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil 
  libmono-data-tds1.0-cil libmono-data-tds2.0-cil libmono-security1.0-cil libmono-security2.0-cil 
  libmono-sharpzip0.84-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil 
  libmono-system-data1.0-cil libmono-system-data2.0-cil libmono-system-web1.0-cil 
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono1.0-cil 
  libmono2.0-cil libmusicbrainz4c2a libnautilus-burn4 libnautilus-extension1 libncurses5 
  libncursesw5 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27 libnet-ldap-perl 
  libnewt0.52 libnl1 libnspr4-0d libnss-mdns libnss3-1d libnxcl-bin libogg0 liboil0.3 liboobs-1-4 
  libopenobex1 liborbit2 libotr2 libpam-gnome-keyring libpam-runtime libpam-smbpass 
  libpanel-applet2-0 libpcap0.8 libpisock9 libpisync1 libpolkit-dbus2 libpolkit-gnome0 
  libpolkit-grant2 libpolkit2 libportaudio0 libpq5 libpt-1.10.10 libpt-1.10.10-plugins-alsa 
  libpt-1.10.10-plugins-v4l libpt-1.10.10-plugins-v4l2 libpth20 libpulse-browse0 libqthreads-12 
  librarian0 libreadline5 librpc-xml-perl libsamplerate0 libsasl2-2 libsasl2-modules libscim8c2a 
  libsdl1.2debian libsdl1.2debian-alsa libsexy2 libshout3 libsigc++-2.0-0c2a libsigc++-2.0-dev 
  libsigc++-2.0-doc libslang2 libsmbclient libsqlite0 libss2 libsysfs2 libtext-wrapi18n-perl 
  libtimedate-perl libtool libtracker-gtk0 libtrackerclient0 libusb-0.1-4 libvisual-0.4-0 
  libvorbis0a libvorbisenc2 libvorbisfile3 libvte-common libwavpack1 libwmf0.2-7 libwnck-common 
  libwnck22 libwpd8c2a libwpg-0.1-1 libwps-0.1-1 libwrap0 libx11-xcb1 libxcomposite1 
  libxml-twig-perl libxml2-utils libxp6 libxres1 libxslt1.1 libxss1 lilo linux-headers-generic 
  linux-sound-base login logrotate lsb-release lshw lsof ltrace lynx lzma make makedev man-db 
  manpages mawk mcpp mdetect mesa-utils migrationtools mii-diag mime-support mktemp mlocate 
  module-init-tools mono-gac mono-runtime mono-xsp2 mount mousetweaks mtr mutt mysql-server nano 
  nautilus nautilus-cd-burner nautilus-data nautilus-sendto ncurses-base net-tools netbeans 
  netcat netcat-traditional nethack-x11 notification-daemon ntfs-3g ntpdate nxproxy 
  obex-data-server onboard openoffice.org-hyphenation openoffice.org-hyphenation-en-us 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-thesaurus-en-au 
  openoffice.org-thesaurus-en-us openprinting-ppds openssh-blacklist openssh-client openssl 
  openssl-blacklist openssl-doc p7zip parted patch pciutils pcmciautils perl-doc-html php5 
  php5-common php5-mysql php5-xmlrpc phpmyadmin pidgin-otr pkg-config pm-utils pnm2ppa policykit 
  policykit-gnome popularity-contest postfix powernowd ppp pppconfig pppoeconf procmail procps 
  psmisc pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-utils pxljr 
  python-pyatspi python-software-properties rar rdesktop readahead readline-common reiserfsprogs 
  rhythmbox roundcube rss-glx rsync scim scim-bridge-agent scim-bridge-client-gtk 
  scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional screen 
  scrollkeeper seahorse sgml-data shared-mime-info smbclient smbfs smbnetfs sound-juicer 
  ssh-askpass-gnome strace sudo sysklogd system-tools-backends sysv-rc sysvutils 
  tangerine-icon-theme tar tcpd tcpdump telnet thunderbird-locale-en-gb time tomboy totem 
  totem-common totem-gstreamer totem-mozilla totem-plugins traceroute tracker tracker-search-tool 
  transmission-common transmission-gtk tree tsclient ttf-arabeyes ttf-arphic-uming ttf-freefont 
  ttf-indic-fonts-core ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts 
  ttf-opensymbol ttf-thai-tlwg ttf-unfonts-core ubuntu-artwork ubuntu-docs ubuntu-keyring 
  ubuntu-sounds ubuntu-wallpapers ucf unattended-upgrades unrar unrar-free unzip update-inetd 
  update-notifier-common usbutils vim vim-common vim-tiny vinagre vino vlc vlc-nox 
  vlc-plugin-pulse vnc4server w3m wamerican wbritish webalizer wget whiptail whois wine wodim 
  wpasupplicant wvdial x-ttcidfont-conf xbase-clients xcursor-themes xdg-user-dirs 
  xdg-user-dirs-gtk xdg-utils xfce4-appfinder xinetd xml-core xml-rpc-api2cpp xorg 
  xscreensaver-data xscreensaver-gl xsltproc xterm xulrunner-1.9 yelp zenity zip 
The following packages will be REINSTALLED:
  python-gnupginterface 
The following NEW packages will be installed:
  apache2.2-bin cups-client cups-common enscript libaprutil1-dbd-sqlite3 libaprutil1-ldap 
  libcanberra-gtk-module libcanberra-gtk0 libcap2 libcups2 libneon27-gnutls libperl5.10 mountall 
  myspell-en-us plymouth plymouth-theme-ubuntu-text 
The following packages will be REMOVED:
  apport apport-gtk aptitude apturl bluez-cups cups-pdf cupsddk-drivers cupsys cupsys-bsd 
  cupsys-driver-gutenprint displayconfig-gtk firefox-3.0-gnome-support firefox-gnome-support 
  foomatic-db-hpijs gimp gimp-data gimp-gnomevfs gimp-python gnome-app-install guidance-backends 
  hal-cups-utils hpijs hplip language-selector libcupsys2 libgimp2.0 openoffice.org-base-core 
  openoffice.org-calc openoffice.org-common openoffice.org-draw openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-style-galaxy 
  openoffice.org-style-human openoffice.org-writer python-apport python-gtkhtml2 python-uno 
  software-properties-gtk splix startup-tasks synaptic system-config-printer-common 
  system-config-printer-gnome system-services tasksel tasksel-data ubufox update-manager 
  update-manager-core update-notifier upstart-compat-sysv upstart-logd xsane xsane-common 
The following packages will be upgraded:
  apache2-mpm-prefork apache2.2-common apt apt-utils coreutils cupsys-client cupsys-common 
  deskbar-applet firefox firefox-branding gnome-menus gtk2-engines-pixbuf ifupdown libapr1 
  libaprutil1 libapt-pkg-perl libauthen-pam-perl libgnome2-canvas-perl libgnome2-perl 
  libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgs8 libgtk2.0-0 
  libgtksourceview2.0-0 libgtksourceview2.0-common libnet-ssleay-perl libsvn-perl libsvn1 
  libtext-iconv-perl libvte9 libxml-parser-perl min12xxw netbase openoffice.org-hyphenation-pl 
  openoffice.org-thesaurus-de openoffice.org-thesaurus-de-ch openoffice.org-thesaurus-pl python 
  python-apt python-brlapi python-cups python-dbus python-gdbm python-gmenu python-gst0.10 
  python-gtksourceview2 python-launchpad-integration python-libxml2 python-notify python-numeric 
  python-problem-report python-scgi python-sexy python-virtkey python-vte python-xdg subversion 
  upstart util-linux 
The following partially installed packages will be configured:
  busybox-initramfs capplets-data compiz-core compiz-fusion-plugins-extra 
  compiz-fusion-plugins-main compiz-gnome compiz-plugins consolekit dictionaries-common doc-base 
  evolution evolution-common evolution-data-server evolution-exchange fontconfig-config gconf2 
  gdm gnome-applets gnome-applets-data gnome-control-center gnome-icon-theme gnome-screensaver 
  gnome-session gnome-session-bin gnome-settings-daemon gstreamer0.10-nice 
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-pulseaudio hunspell-de-at 
  hunspell-de-ch hunspell-de-de initramfs-tools irssi ldap-utils libappindicator0 libatk1.0-0 
  libbonobo2-0 libc6-i686 libcaca0 libcairo-perl libcairo2 libcamel1.2-14 libcanberra0 
  libcdparanoia0 libcompizconfig0 libcroco3 libcucul0 libcupsimage2 libdatrie1 libdbd-mysql-perl 
  libdbi-perl libdbus-glib-1-2 libdbusmenu-glib1 libdbusmenu-gtk1 libdeskbar-tracker 
  libdevkit-power-gobject1 libdirectfb-1.2-0 libdrm-intel1 libebackend1.2-0 libebook1.2-9 
  libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 
  libeggdbus-1-0 libegroupwise1.2-13 libenchant1c2a libevdocument2 libevview2 
  libexchange-storage1.2-3 libfile-temp-perl libfontconfig1 libgconf2-4 libgdata-google1.2-1 
  libgdata1.2-1 libglib-perl libglib2.0-0 libgmime-2.4-2 libgnome-desktop-2-17 libgnome-menu2 
  libgnome-window-settings1 libgnome2-vfs-perl libgnomekbd-common libgnomekbd4 libgnomevfs2-0 
  libgnomevfs2-common libgnomevfs2-extra libgnutls26 libgsf-1-114 libgssapi-krb5-2 libgssdp-1.0-2 
  libgstfarsight0.10-0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk2-perl 
  libgtkhtml-editor0 libgtkhtml3.14-19 libgucharmap7 libgudev-1.0-0 libgupnp-1.0-3 
  libgupnp-igd-1.0-2 libgweather-common libgweather1 libhtml-parser-perl libhtml-tagset-perl 
  libicu42 libindicator0 libio-pty-perl libjson-glib-1.0-0 libkrb5-3 libldap-2.4-2 libldap2-dev 
  libmetacity-private0 libmldbm-perl libnet-dbus-perl libnice0 libnih-dbus1 libnih1 libnotify1 
  libpango-perl libpango1.0-0 libpciaccess0 libpcre3 libpixman-1-0 libpng12-0 libpolkit-agent-1-0 
  libpolkit-backend-1-0 libpolkit-gobject-1-0 libpulse-mainloop-glib0 libpulse0 libpurple0 
  librsvg2-2 librsvg2-common libsoup-gnome2.4-1 libsoup2.4-1 libssl-dev libstartup-notification0 
  libstlport4.6ldbl libtag1c2a libtemplate-perl libterm-readkey-perl libthai0 libtotem-plparser17 
  libts-0.0-0 libunique-1.0-0 liburi-perl libuuid-perl libwww-perl libx11-6 libxi6 libxklavier16 
  libxrandr2 libxvmc1 libzephyr4 lp-solve metacity metacity-common myspell-en-gb myspell-en-za 
  myspell-es openoffice.org-help-de openoffice.org-help-it openoffice.org-help-nl 
  openoffice.org-help-pl openoffice.org-help-pt perl perl-doc perl-modules pidgin policykit-1 
  policykit-1-gnome python-bugbuddy python-cairo python-central python-evince python-evolution 
  python-gconf python-glade2 python-gnome2 python-gnome2-desktop python-gnomeapplet 
  python-gnomecanvas python-gnomedesktop python-gnomekeyring python-gnomeprint python-gobject 
  python-gtk2 python-gtop python-mediaprofiles python-metacity python-pyorbit python-rsvg 
  python-totem-plparser python-wnck slapd tsconf ubuntu-system-service udev ufw uno-libs3 ure 
  util-linux-locales x11-common xchat xchat-common xchat-gnome xchat-gnome-common xserver-common 
  xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev 
  xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse 
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark 
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus 
  xserver-xorg-video-dummy xserver-xorg-video-fbdev xserver-xorg-video-geode 
  xserver-xorg-video-glint xserver-xorg-video-i128 xserver-xorg-video-i740 
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga 
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv 
  xserver-xorg-video-openchrome xserver-xorg-video-r128 xserver-xorg-video-radeon 
  xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-s3virge 
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis 
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident 
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa 
  xserver-xorg-video-vmware xserver-xorg-video-voodoo zlib1g-dev 
60 packages upgraded, 16 newly installed, 1 reinstalled, 1 downgraded, 68 to remove and 947 not upgraded.
Need to get 17.9MB of archives. After unpacking 217MB will be freed.
Do you want to continue? [Y/n/?]Y


Need to get 17.9MB of archives. After unpacking 217MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Error!
E: I wasn't able to locate file for the myspell-fr-gut package. This might mean you need to manually fix this package.

[/PHP]

what i should do then !

thank you

---

### Post by Lars Noodén on 2011-12-18
Have you run [font=Courier New]apt-get dist-upgrade[/font] yet?

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-12-18
> **Lars Noodén said:**
> Have you run [FONT=Courier New]apt-get dist-upgrade[/FONT] yet?

yes i did it many times and always i got the same problem

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-12-18
i got this now which corresponding score should i choose


[PHP]Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
firefox recommends ubufox
nautilus recommends gnome-app-install
Score is 4839

Accept this solution? [Y/n/q/?] n

Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
firefox recommends ubufox
xsane-common recommends xsane
nautilus recommends gnome-app-install
Score is 4640

Accept this solution? [Y/n/q/?] n

Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
xsane-common recommends xsane
firefox recommends ubufox
nautilus recommends gnome-app-install
Score is 4600

Accept this solution? [Y/n/q/?] n

Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
firefox recommends ubufox
xsane-common recommends xsane
nautilus recommends gnome-app-install
Score is 4570

Accept this solution? [Y/n/q/?] n

Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
firefox recommends ubufox
nautilus recommends gnome-app-install
Score is 4799

Accept this solution? [Y/n/q/?] n

Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
firefox recommends ubufox
xsane-common recommends xsane
nautilus recommends gnome-app-install
Score is 4600

Accept this solution? [Y/n/q/?] n

Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
xsane-common recommends xsane
firefox recommends ubufox
nautilus recommends gnome-app-install
Score is 4560

Accept this solution? [Y/n/q/?] n

Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
firefox recommends ubufox
xsane-common recommends xsane
nautilus recommends gnome-app-install
Score is 4530

Accept this solution? [Y/n/q/?] n

Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
firefox recommends ubufox
nautilus recommends gnome-app-install
hplip-data recommends hplip
Score is 4629

Accept this solution? [Y/n/q/?] n

Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
firefox recommends ubufox
xsane-common recommends xsane
nautilus recommends gnome-app-install
hplip-data recommends hplip
Score is 4430

Accept this solution? [Y/n/q/?] n

Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
xsane-common recommends xsane
firefox recommends ubufox
nautilus recommends gnome-app-install
hplip-data recommends hplip
Score is 4390

Accept this solution? [Y/n/q/?] n

Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
firefox recommends ubufox
xsane-common recommends xsane
nautilus recommends gnome-app-install
hplip-data recommends hplip
Score is 4360

Accept this solution? [Y/n/q/?] n

Leave the following dependencies unresolved:
openoffice.org-hyphenation-pl recommends openoffice.org (>= 1.0.3) | openoffice.org-writer
firefox recommends ubufox
nautilus recommends gnome-app-install
Score is 4538

Accept this solution? [Y/n/q/?] n

[/PHP]

---

### Post by brighty22 on 2011-12-18
Try apt-get -f install. If still no luck, I had a package problem recently and aptitude seemed to be better than apt-get at resolving unmet dependencies.

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-12-18
> **brighty22 said:**
> Try apt-get -f install. If still no luck, I had a package problem recently and aptitude seemed to be better than apt-get at resolving unmet dependencies.

always same output

```
apt-get -f install
```[PHP]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
  compiz-gnome: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  evolution: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  gdm: Depends: libcanberra-gtk0 (>= 0.4) but it is not installed
       Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed
       Depends: upstart-job
  gnome-applets: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  gnome-control-center: Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
                        Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  gnome-screensaver: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  gnome-session-bin: Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed
  gnome-settings-daemon: Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
                         Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  initramfs-tools: Depends: util-linux (> 2.15~rc1) but 2.13.1-5ubuntu3.1 is installed
  irssi: Depends: libperl5.10 (>= 5.10.1) but it is not installed
  language-support-writing-en: Depends: myspell-en-us but it is not installed
  libappindicator0: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libapt-pkg-perl: Depends: perlapi-5.8.8 but it is not installable
  libauthen-pam-perl: Depends: perlapi-5.8.7 but it is not installable
  libcupsimage2: Depends: libcups2 (>= 1.4.0) but it is not installed
  libdbusmenu-gtk1: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed
  libedataserverui1.2-8: Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed
  libevdocument2: Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed
  libevview2: Depends: libgtk2.0-0 (>= 2.20.0) but 2.12.9-3ubuntu5 is installed
  libgnome-desktop-2-17: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libgnome-window-settings1: Depends: libgtk2.0-0 (>= 2.15.0) but 2.12.9-3ubuntu5 is installed
  libgnome2-canvas-perl: Depends: perlapi-5.8.8 but it is not installable
  libgnome2-perl: Depends: perlapi-5.8.7 but it is not installable
  libgnomekbd4: Depends: libgtk2.0-0 (>= 2.20.0) but 2.12.9-3ubuntu5 is installed
  libgtk2-perl: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libgtkhtml-editor0: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libgtkhtml3.14-19: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  libgucharmap7: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed
  libindicator0: Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is installed
  libmetacity-private0: Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
  libnet-ssleay-perl: Depends: perlapi-5.8.7 but it is not installable
  libpurple0: Depends: libperl5.10 (>= 5.10.1) but it is not installed
  librsvg2-2: Depends: libgtk2.0-0 (>= 2.16) but 2.12.9-3ubuntu5 is installed
  librsvg2-common: Depends: libgtk2.0-0 (>= 2.16) but 2.12.9-3ubuntu5 is installed
  libsnmp15: Depends: libperl5.8 (>= 5.8.8) but it is not installable
  libsvn-perl: Depends: perlapi-5.8.8 but it is not installable
  libtext-iconv-perl: Depends: perlapi-5.8.7 but it is not installable
  libxml-parser-perl: Depends: perlapi-5.8.8 but it is not installable
  metacity: Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
            Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  openoffice.org-base-core: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-calc: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-draw: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
                      Depends: libgtk2.0-0 (>= 2.14.0) but 2.12.9-3ubuntu5 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  openoffice.org-style-galaxy: Depends: openoffice.org-core (>= 1:3.2.0~beta) but it is not installed
  openoffice.org-style-human: Depends: openoffice.org-common (= 1:2.4.1-1ubuntu2.5) but 1:3.2.0-7ubuntu4.2 is installed
  openoffice.org-thesaurus-de: Depends: openoffice.org-core (>= 1.9) but it is not installed
  openoffice.org-thesaurus-de-ch: Depends: openoffice.org-core (>= 1.9) but it is not installed
  openoffice.org-thesaurus-pl: Depends: openoffice.org-core (>= 1.9) but it is not installed
  openoffice.org-writer: Depends: openoffice.org-core (= 1:3.2.0-7ubuntu4.2) but it is not installed
  pidgin: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
  policykit-1-gnome: Depends: libgtk2.0-0 (>= 2.17.1) but 2.12.9-3ubuntu5 is installed
  python: Depends: python-minimal (= 2.5.2-0ubuntu1) but 2.6.5-0ubuntu1 is installed
  python-cairo: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-evince: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-evolution: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gconf: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-glade2: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
                 Depends: libgtk2.0-0 (>= 2.19.0) but 2.12.9-3ubuntu5 is installed
  python-gnome2: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomeapplet: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomecanvas: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomedesktop: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomekeyring: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gnomeprint: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gobject: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-gtk2: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
               Depends: libgtk2.0-0 (>= 2.19.1) but 2.12.9-3ubuntu5 is installed
  python-gtop: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-mediaprofiles: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-metacity: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-pyorbit: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-rsvg: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-totem-plparser: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  python-uno: Depends: openoffice.org-core (= 1:2.4.1-1ubuntu2.5) but it is not installed
  python-wnck: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
  slapd: Depends: libperl5.10 (>= 5.10.1) but it is not installed
  udev: Depends: upstart-job
        Depends: util-linux (> 2.15~rc2) but 2.13.1-5ubuntu3.1 is installed
  ufw: Depends: python (>= 2.6) but 2.5.2-0ubuntu1 is installed
       Depends: upstart-job
  util-linux-locales: Depends: util-linux (>= 2.17.2-0) but 2.13.1-5ubuntu3.1 is installed
  x11-common: Depends: upstart-job
  xchat: Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
         Depends: libperl5.10 (>= 5.10.1) but it is not installed
  xchat-gnome: Depends: libcanberra-gtk0 (>= 0.3) but it is not installed
               Depends: libgtk2.0-0 (>= 2.18.0) but 2.12.9-3ubuntu5 is installed
               Depends: libperl5.10 (>= 5.10.0) but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
[/PHP]
please i am waiting for any suggestion !

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-12-22
pleaase give me a solution i still waiting:frown:

---

### Post by Lars Noodén on 2011-12-23
I haven't made the exact same upgrade as you are trying but have done others.  What has worked for me is to update /etc/apt/sources.list to the new distro, then:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

reboot

sudo apt-get upgrade
sudo apt-get dist-upgrade

reboot

```

---

