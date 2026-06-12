---
title: "[Ubuntu 24.04] Failing to install xubuntu"
date: 2024-04-01
forum: Ubuntu Development Version
---

### Post by Swiftjay on 2024-04-01
I've been testing ubuntu 24.04 before it's released, originally when I installed ubuntu-server edition this worked fine, I was able to install xubuntu-desktop and no issues (this was about 2-3 weeks ago).  I downloaded a fresh new version of the daily build and for the past 2-3 daily builds I've attempted I've failed to install xubuntu desktop at all.  It flatout refuses to install it due to multiple dependencies not installable so it won't install xubuntu-desktop.  Even ubuntu-desktop won't install due to the same reason.

The only way to install ubuntu desktop is to actually download the ubuntu-desktop iso and install it.  But if I try to install xubuntu-desktop from the ubuntu-desktop it fails due to dependencies that won't install.

See error message below 

```bash
```

The following packages have unmet dependencies:
 gir1.2-javascriptcoregtk-4.1 : Depends: libjavascriptcoregtk-4.1-0 (= 2.43.3-1) but it is not installable
 gir1.2-webkit2-4.1 : Depends: libwebkit2gtk-4.1-0 (= 2.43.3-1) but it is not installable
 libasound2-plugins : Depends: libavcodec60 (>= 7:6.0)
                      Depends: libswresample4 (>= 7:6.0) but it is not installable
 pkexec : Depends: polkitd (= 124-1) but 124-1ubuntu1 is to be installed
          Depends: libpolkit-agent-1-0 (= 124-1) but 124-1ubuntu1 is to be installed
          Depends: libpolkit-gobject-1-0 (= 124-1) but 124-1ubuntu1 is to be installed
 plymouth-label : Depends: plymouth (= 24.004.60-1ubuntu3) but 24.004.60-1ubuntu6 is to be installed
 policykit-1 : Depends: polkitd (= 124-1) but 124-1ubuntu1 is to be installed
 thunar : Depends: thunar-data (= 4.18.8-1) but 4.18.8-1build2 is to be installed
          Recommends: gvfs but it is not installable
 tumbler : Depends: tumbler-common (= 4.18.1-1) but 4.18.1-1.1build3 is to be installed
 xubuntu-desktop : Depends: alsa-utils but it is not installable
                   Depends: xfdesktop4 but it is not installable
                   Recommends: atril but it is not installable
                   Recommends: blueman but it is not installable
                   Recommends: catfish but it is not installable
                   Recommends: dbus-x11 but it is not installable
                   Recommends: engrampa but it is not installable
                   Recommends: gimp but it is not installable
                   Recommends: gvfs-backends but it is not installable
                   Recommends: gvfs-fuse but it is not installable
                   Recommends: hexchat but it is not installable
                   Recommends: hplip but it is not installable
                   Recommends: libreoffice-calc but it is not installable
                   Recommends: libreoffice-gnome but it is not installable
                   Recommends: libreoffice-impress but it is not installable
                   Recommends: libreoffice-writer but it is not installable
                   Recommends: network-manager-gnome but it is not installable
                   Recommends: network-manager-pptp-gnome but it is not installable
                   Recommends: onboard but it is not installable
                   Recommends: parole but it is not installable
                   Recommends: simple-scan but it is not installable
                   Recommends: system-config-printer but it is not installable
                   Recommends: xfce4-power-manager but it is not installable
 xubuntu-desktop-minimal : Depends: alsa-utils but it is not installable
                           Depends: xfdesktop4 but it is not installable
                           Recommends: dbus-x11 but it is not installable
                           Recommends: hplip but it is not installable
                           Recommends: network-manager-gnome but it is not installable
                           Recommends: xfce4-power-manager but it is not installable
E: Unable to correct problems, you have held broken packages.
```
```

I've tried using aptitude to install the package, i've also tried tasksel but this fails to do so, am I missing something very basic in terms of enabling this that I'm failing to see?  Any advice is appreciated

My /etc/apt/sources.list.d/ubuntu.sources file looks like this

```
```
root@harness:/home/dsisys# cat /etc/apt/sources.list.d/ubuntu.sources
Types: deb
URIs: [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu)
Suites: noble noble-updates noble-backports
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg

Types: deb
URIs: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
Suites: noble-security
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
```

```

---

### Post by maglin2 on 2024-04-01
Possibly related to this.

[https://discourse.ubuntu.com/t/whats-happening-in-noble-repositories/43729/7](https://discourse.ubuntu.com/t/whats-happening-in-noble-repositories/43729/7)

Advice seems to be to leave 24.04 alone for now.

---

### Post by Swiftjay on 2024-04-01
Yeap.....that would do it, ok I guess I'll have to try and do some testing elsewhere for now, thanks for this I'll keep this thread up to date.

---

### Post by oldfred on 2024-04-01
Since 24.04 moved to Development sub-forum.

---

### Post by ajgreeny on 2024-04-01
Yes, we've all been suffering these problems now for 4 or 5 days; updating packages and installing many is also currently impossible so for the moment you orobably need to wait for a new ISO file to appear.
The last one available was dated 28-03-2024 and I am aware the devs are having problems getting new ISOs built.

Wait a few more days and hopefully  new versions will be available to test, though I will not be surprised to see a few difficulties lingering on for a while.

Fingers crossed!

---

### Post by Frogs Hair on 2024-04-01
An update two days ago almost removed my entire desktop. I got though with with fix broken install and the next update replaced many missing packages. Today, xz-utils updated, so back to normal testing on the current installation.

---

### Post by Swiftjay on 2024-04-02
Tried a fresh install, still failing for me but it is the same image from 29th but I thought an apt upgrade would work but still not working.   I guess I'll wait for a new iso image, hopefully tmrw.

---

### Post by Swiftjay on 2024-04-08
Daily build from yesterday resolved the issue, I do have some further ones but I'll deal with that in another ticket.

---

