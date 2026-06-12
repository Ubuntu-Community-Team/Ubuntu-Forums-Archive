---
title: "apt upgrade failing"
date: 2012-03-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ratcheer on 2012-03-16
This morning's safe-upgrade is failing for my system. I have tried to rerun it, but no luck.

```
sudo aptitude safe-upgrade
Resolving dependencies...                
The following NEW packages will be installed:
  libarchive12{a} libgmime-2.6-0{a} libnettle4{a} 
The following packages will be upgraded:
  apparmor apt apt-transport-https apt-utils console-setup debconf debconf-i18n dh-apparmor gdb gir1.2-rb-3.0 gir1.2-totem-plparser-1.0 gnome-settings-daemon gwibber gwibber-service 
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter indicator-appmenu keyboard-configuration language-selector-common language-selector-gnome libapt-inst1.4 libgdata-common 
  libgdata13 libgwibber-gtk2 libgwibber2 libpackagekit-glib2-14 librhythmbox-core5 libtotem-plparser17 os-prober python-packagekit python3 python3-minimal rhythmbox rhythmbox-data 
  rhythmbox-plugin-cdrecorder rhythmbox-plugins unity-greeter xserver-xorg-input-evdev xserver-xorg-input-synaptics 
The following partially installed packages will be configured:
  libapt-pkg4.12 python 
The following packages are RECOMMENDED but will NOT be installed:
  rhythmbox-mozilla rhythmbox-plugin-zeitgeist 
40 packages upgraded, 3 newly installed, 0 to remove and 4 not upgraded.
Need to get 0 B/10.1 MB of archives. After unpacking 1,364 kB will be used.
Do you want to continue? [Y/n/?] 
[COLOR=Red]E: Internal Error, No file name for libapt-pkg4.12[/COLOR]

```

Showing the package libapt-pkg4.12 shows a state of "unpacked". It appears that it has unpacked the package but now cannot find it, or something like that.

Any idea how to get around this?

Tim

---

### Post by dino99 on 2012-03-16
the "unpacked" issue have been fixed with the latest "apt"

apt (0.8.16~exp12ubuntu6) precise; urgency=low

  * cherry pick from
    [http://bzr.debian.org/bzr/bzr/apt/apt/debian-experimental2/:](http://bzr.debian.org/bzr/bzr/apt/apt/debian-experimental2/:)
    * apt-pkg/packagemanager.cc:
      - fix bug in predepends handling - ensure that packages that needs
        unpackaging are unpacked before they are configured (LP: #927993)

so better to update/upgrade via apt-get

---

### Post by ratcheer on 2012-03-16
Thanks, @dino99.

Tim

---

### Post by ratcheer on 2012-03-16
I am sorry, I do not understand how to use that file. I ran ./configure, then when I tried "make", it gave: "configure: error: failed: I need CURL due https support"

I had hoped it would just expand to a .deb file that I could install. :confused:

I'm getting too old for this.

Tim

re: apt_0.8.16~exp12ubuntu6.tar.gz

---

### Post by ratcheer on 2012-03-16
Ok, I am out of the ditch, now. I found this via Google search, installed it, and was able to complete my daily upgrade.

[http://www.ubuntuupdates.org/package/core/precise/main/base/libapt-pkg4.12](http://www.ubuntuupdates.org/package/core/precise/main/base/libapt-pkg4.12)

Thanks for pointing me in the right direction.

Tim

---

