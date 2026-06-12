---
title: "Programs  Starting to be Removed:"
date: 2011-11-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-11-16
Just did most recent update in synaptic. It  called to remove (which I allowed it) several programs including the "shutter" program with is a screenshot program -(can't figure that one out).

---

### Post by effenberg0x0 on 2011-11-16
Weird, I updated this morning, there was nothing in central repo (US) for me. And now all I got is a bunch of perl stuff held back and it is just upgrading stuff (no removal).

```
The following packages have been kept back:
  libalgorithm-diff-xs-perl libapt-pkg-perl libcairo-perl libfolks25 libglib-perl libgtk2-perl
  libhtml-parser-perl libio-pty-perl libjson-xs-perl liblocale-gettext-perl libnet-dns-perl
  libnet-ssleay-perl libpango-perl libsnmp15 libsocket6-perl libsub-name-perl
  libtext-charwidth-perl libtext-iconv-perl libuuid-perl libxml-parser-perl libyaml-syck-perl perl
  perl-base perl-modules perlmagick sessioninstaller
The following packages will be upgraded:
  aisleriot apparmor dh-translations firefox firefox-globalmenu firefox-gnome-support
  firefox-locale-en firefox-locale-es firefox-locale-pt firefox-locale-zh-hans gir1.2-totem-1.0
  gir1.2-vte-2.90 gnome-accessibility-themes gnome-icon-theme gnome-icon-theme-full
  gnome-settings-daemon gnome-themes-standard imagemagick initscripts libldap-2.4-2
  liblightdm-gobject-1-0 libmagick++3 libmagickcore3 libmagickcore3-extra libmagickwand3
  libpurple-bin libsnmp-base libsyncdaemon-1.0-1 libtotem0 libvte-2.90-9 libvte-common libvte9
  libxmmsclient6 libzbar0 lightdm lightdm-gtk-greeter locales python-ubuntuone-client python-vte
  sysv-rc sysvinit-utils totem-common ubuntuone-client vim-common vim-tiny xul-ext-ubufox
46 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
Need to get 40.2 MB of archives.

```

---

### Post by ronacc on 2011-11-16
I just now started an update with synaptic , 1 removed 1 installed and 67 upgrades , the removed was libperl 5.12 the installed was libperl 5.14 .

---

### Post by BillyBoa on 2011-11-16
If you go to Ubuntu Software Center there is a tab HISTORY. Click it to see what happened.

---

### Post by ronacc on 2011-11-16
synaptic also has a history , file>history .

---

### Post by dino99 on 2011-11-16
that removed gtkorphan on my end, due to libperl5.12
but can be installed back again now

---

### Post by castrojo on 2011-11-16
> **ventrical said:**
> Just did most recent update in synaptic. It  called to remove (which I allowed it) several programs including the "shutter" program with is a screenshot program -(can't figure that one out).

There's a Perl transition in progress right now so everything requiring perl needs to be rebuilt: 

[https://lists.ubuntu.com/archives/ubuntu-devel/2011-November/034441.html](https://lists.ubuntu.com/archives/ubuntu-devel/2011-November/034441.html)

---

### Post by ventrical on 2011-11-16
> **BillyBoa said:**
> If you go to Ubuntu Software Center there is a tab HISTORY. Click it to see what happened.


OK.. but why would it remove the *shutter* screenshot program?

---

### Post by ventrical on 2011-11-16
> **castrojo said:**
> There's a Perl transition in progress right now so everything requiring perl needs to be rebuilt: 

[https://lists.ubuntu.com/archives/ubuntu-devel/2011-November/034441.html](https://lists.ubuntu.com/archives/ubuntu-devel/2011-November/034441.html)

Thanks castrojo. I am just wondering if these removals and transitions will lead to possible breakages.

thanks.

Ok .. the dev  more or less says that there will not be too much disruption. Hmmmm ? :)

---

### Post by castrojo on 2011-11-16
For me all the packages are held back (which is what is supposed to happen). 

If something is wanting to be removed it's because you're trying to do a partial upgrade, probably a setting with synaptic or something (I'm not familiar with it).

---

### Post by philinux on 2011-11-16
> **castrojo said:**
> For me all the packages are held back (which is what is supposed to happen). 

If something is wanting to be removed it's because you're trying to do a partial upgrade, probably a setting with synaptic or something (I'm not familiar with it).

Yep exactly same here as expected.
```
The following packages have been kept back:
  evolution-data-server libcairo-perl libcamel-1.2-29 libedataserverui-3.0-1 libglib-perl libgtk2-perl liblocale-gettext-perl
  libpango-perl libpurple0 libsnmp15 libsub-name-perl libtext-charwidth-perl libtext-iconv-perl libuuid-perl perl perl-base
  perl-modules sessioninstaller xchat xchat-common
0 upgraded, 0 newly installed, 0 to remove and 20 not upgrade
```

---

### Post by ventrical on 2011-11-16
> **castrojo said:**
> For me all the packages are held back (which is what is supposed to happen). 

If something is wanting to be removed it's because you're trying to do a partial upgrade, probably a setting with synaptic or something (I'm not familiar with it).


Haven't touched a thing in synaptic.  Updates were  going great , unimpeded until today.

---

### Post by effenberg0x0 on 2011-11-16
It's holding some packages here every two days or so, but nothing out of the ordinary. Also important to mention: I gave up update-manager, update-notifier, synaptic, apt-get, Ubuntu Software Center, and am relying only on aptitude. As much as I know that all these tools are supposed to output the same results, recent events proved me aptitude is a bit smarter. What triggered it was the last wonderful advice I got from update-manager (to remove libc6).

---

### Post by ventrical on 2011-11-16
> **effenberg0x0 said:**
> It's holding some packages here every two days or so, but nothing out of the ordinary. Also important to mention: I gave up update-manager, update-notifier, synaptic, apt-get, Ubuntu Software Center, and am relying only on aptitude. As much as I know that all these tools are supposed to output the same results, recent events proved me aptitude is a bit smarter. What triggered it was the last wonderful advice I got from update-manager (to remove libc6).


  I used aptitude a while back .. worked good when I had that busted precise system back a while ago.

---

### Post by philinux on 2011-11-16
> **effenberg0x0 said:**
> It's holding some packages here every two days or so, but nothing out of the ordinary. Also important to mention: I gave up update-manager, update-notifier, synaptic, apt-get, Ubuntu Software Center, and am relying only on aptitude. As much as I know that all these tools are supposed to output the same results, recent events proved me aptitude is a bit smarter. What triggered it was the last wonderful advice I got from update-manager (to remove libc6).

+1. I only use aptitude on a development release. Never let me down. Plus I nearly always update via chroot from the stable release so I have no gui. :p

```
aptitude update && aptitude safe-upgrade
and
aptitude update && aptitude full-upgrade
```
The full upgrade wants to do this but I'll wait a few more hours.
```
The following NEW packages will be installed:
  libperl5.14{a} 
The following packages will be upgraded:
  libcairo-perl libglib-perl libgtk2-perl liblocale-gettext-perl libpango-perl libpurple0 libsnmp15 libsub-name-perl 
  libtext-charwidth-perl libtext-iconv-perl libuuid-perl perl perl-base perl-modules sessioninstaller{b} xchat xchat-common 
17 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.5 MB of archives. After unpacking 10.8 MB will be freed.
The following packages have unmet dependencies:
  sessioninstaller: Conflicts: gnome-codec-install but 0.4.7+nmu1ubuntu2 is installed.
  libperl5.12: Depends: perl-base (= 5.12.4-6) but 5.14.2-3build1 is to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     gnome-codec-install         
2)     libperl5.12
```

---

### Post by dino99 on 2011-11-16
> **castrojo said:**
> For me all the packages are held back (which is what is supposed to happen). 

If something is wanting to be removed it's because you're trying to do a partial upgrade, probably a setting with synaptic or something (I'm not familiar with it).

All the *perl packages have been installed without trouble if you first purge libperl 5.12, then after the *perl installation you can install back the removed package(s). No more package held back here on i386.

---

### Post by ventrical on 2011-11-16
> **philinux said:**
> +1. I only use aptitude on a development release. Never let me down. Plus I nearly always update via chroot from the stable release so I have no gui. :p

```
aptitude update && aptitude safe-upgrade
and
aptitude update && aptitude full-upgrade
```The full upgrade wants to do this but I'll wait a few more hours.
```
The following NEW packages will be installed:
  libperl5.14{a} 
The following packages will be upgraded:
  libcairo-perl libglib-perl libgtk2-perl liblocale-gettext-perl libpango-perl libpurple0 libsnmp15 libsub-name-perl 
  libtext-charwidth-perl libtext-iconv-perl libuuid-perl perl perl-base perl-modules sessioninstaller{b} xchat xchat-common 
17 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.5 MB of archives. After unpacking 10.8 MB will be freed.
The following packages have unmet dependencies:
  sessioninstaller: Conflicts: gnome-codec-install but 0.4.7+nmu1ubuntu2 is installed.
  libperl5.12: Depends: perl-base (= 5.12.4-6) but 5.14.2-3build1 is to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     gnome-codec-install         
2)     libperl5.12
```


Thanks for that confirmation - re: <gnome-codec-install>    .. so it's not  just me.

---

### Post by Bowmore on 2011-11-16
These packages was removed in my case:
- libperl5.12
- gnome-codec-install

libperl5.12 is obvious due to the upgrade from 5.12 to 5.14.
gnome-codec-install is removed because sessioninstaller replaces it acc to its dependencies.

---

### Post by PaulW2U on 2011-11-16
> **castrojo said:**
> There's a Perl transition in progress right now so everything requiring perl needs to be rebuilt: 

[https://lists.ubuntu.com/archives/ubuntu-devel/2011-November/034441.html](https://lists.ubuntu.com/archives/ubuntu-devel/2011-November/034441.html)

Thanks for the link, I guessed that was what was happening.

As a Kubuntu user, I've only lost kvirc in order to install the Perl updates. I'll just use konversation until I get kvirc back. :neutral:

[COLOR="Maroon"]**Edit**: New kvirc build just installed.[/COLOR] :D

---

### Post by IanW on 2011-11-16
> **ventrical said:**
> OK.. but why would it remove the *shutter* screenshot program?

Synaptic says that Shutter depends on Perl.

---

### Post by effenberg0x0 on 2011-11-16
> **IanW said:**
> Synaptic says that Shutter depends on Perl.

It does, in fact.

```
$ [sudo] password for ahsl: 
shutter
  Depends: libgtk2-perl
  Depends: libglib-perl
  Depends: libgnome2-perl
  Depends: libgnome2-vfs-perl
  Depends: libgnome2-wnck-perl
  Depends: libgnome2-gconf-perl
  Depends: liblocale-gettext-perl
  Depends: libxml-simple-perl
  Depends: libwww-mechanize-perl
  Depends: libwww-perl
  Depends: perlmagick
    graphicsmagick-libmagick-dev-compat
  Depends: libx11-protocol-perl
  Depends: librsvg2-common
  Depends: libfile-desktopentry-perl
  Depends: libfile-basedir-perl
  Depends: libfile-copy-recursive-perl
  Depends: libfile-mimeinfo-perl
  Depends: libproc-simple-perl
  Depends: libfile-homedir-perl
  Depends: libfile-which-perl
  Depends: libsort-naturally-perl
  Depends: libgtk2-imageview-perl
  Depends: libnet-dbus-perl
  Depends: libgnome2-canvas-perl
  Depends: imagemagick
    graphicsmagick-imagemagick-compat
  Depends: libproc-processtable-perl
  Depends: libgtk2-unique-perl
  Suggests: nautilus-sendto
  Suggests: libnet-dbus-glib-perl
  Recommends: gnome-web-photo
  Recommends: libgoo-canvas-perl
```

---

### Post by castrojo on 2011-11-17
> **effenberg0x0 said:**
> As much as I know that all these tools are supposed to output the same results, recent events proved me aptitude is a bit smarter.

They don't offer the same results, aptitude's upgrade resolver isn't really tested (which is why it was moved to universe), see this bug: 

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/592336/comments/19](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/592336/comments/19)

---

### Post by effenberg0x0 on 2011-11-17
> **castrojo said:**
> They don't offer the same results, aptitude's upgrade resolver isn't really tested (which is why it was moved to universe), see this bug: 

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/592336/comments/19](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/592336/comments/19)

I was completely unaware of aptitude not being in the "official" set of tools and had never paid attention to which repo it was on when installing. Anyway, it's good to know I'm not crazy - the thing indeed works differently with deps. Good info.

Whenever I see relevant differences in what apt-get and aptitude propose, I'll remember to post a bug reply then. Since both have a simulation mode, I will consider scripting something to auto diff their suggestions.

Thanks castrojo

---

