---
title: "VMware Tools for server"
date: 2012-07-18
forum: Server Platforms
---

### Post by geohei on 2012-07-18
Hi.

Is it worth/useful/possible to install VMware Tools to an Ubuntu 12.04 guest being hosted by VMware 7.1.2 Workstation?

Thanks,

---

### Post by LHammonds on 2012-07-18
I have only used ESXi/VMware/vSphere but I do install the tools which is supposed to provide better performance...but I have not measured the difference.
 
Check my sig for a link on setting up an Ubuntu Server which has steps for installing/removing the tools. Not sure how similar it will be for VMware Workstation but I would venture to guess it will be similar (mount CDROM, install software)
 
**EDIT:** My google-fu is strong today. [VMware Workstation docs]("http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html")
 
[Same question posed on another site]("http://communities.vmware.com/thread/50571").
 
An article about the [benefits of VMware tools]("http://www.petri.co.il/virtual_install_vmware_tools_in_linux.htm").
 
[What does VMware tools do]("http://reformedmusings.wordpress.com/2008/08/15/what-does-vmware-tools-do/")?
 
LHammonds

---

### Post by sandyd on 2012-07-18
> **geohei said:**
> Hi.

Is it worth/useful/possible to install VMware Tools to an Ubuntu 12.04 guest being hosted by VMware 7.1.2 Workstation?

Thanks,
Have you tried open-vm-tools?
[http://packages.ubuntu.com/search?keywords=open-vm-tools](http://packages.ubuntu.com/search?keywords=open-vm-tools)

Just install the package, this is an Vmware-compatible open-source version of the modules.

---

### Post by geohei on 2012-07-19
Ok. Thanks for the links.
Going to test all this extensively during weekend.

My intention was to connect USB devices of the guest by command inside the host. Is this possible using VMware Tools?

---

### Post by geohei on 2012-07-20
> **sandyd said:**
> Have you tried open-vm-tools?
[http://packages.ubuntu.com/search?keywords=open-vm-tools](http://packages.ubuntu.com/search?keywords=open-vm-tools)

Just install the package, this is an Vmware-compatible open-source version of the modules.
When I try this, I get:
```
root@vm-90:~# apt-get install open-vm-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  cvs debhelper defoma diffstat ethtool fontconfig fontconfig-config gettext hicolor-icon-theme html2text intel-gpu-tools intltool-debian libatk1.0-0
  libatk1.0-data libavahi-client3 libavahi-common-data libavahi-common3 libcairo2 libcairomm-1.0-1 libcroco3 libcups2 libdatrie1 libdirectfb-1.2-0
  libfontconfig1 libfontenc1 libgl1-mesa-dri libglibmm-2.4-1c2a libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkmm-2.4-1c2a libice6 libicu42 libjasper1
  libjpeg62 libmail-sendmail-perl libpango1.0-0 libpango1.0-common libpangomm-1.4-1 libpciaccess0 libpixman-1-0 libsm6 libsys-hostname-long-perl libsysfs2
  libthai-data libthai0 libtiff4 libts-0.0-0 liburiparser1 libxaw7 libxcb-render-util0 libxcb-render0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3
  libxfont1 libxft2 libxi6 libxinerama1 libxkbfile1 libxmu6 libxpm4 libxrandr2 libxrender1 libxss1 libxt6 libxtst6 libxv1 libxvmc1 module-assistant
  open-vm-source open-vm-toolbox po-debconf quilt shared-mime-info tsconf ttf-dejavu-core x-ttcidfont-conf x11-common x11-xkb-utils xfonts-base
  xfonts-encodings xfonts-utils xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-vmmouse
  xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo zerofree
Suggested packages:
  dh-make defoma-doc psfontmgr dfontmgr libfont-freetype-perl gettext-doc cups-common libglide3 librsvg2-common gvfs libjasper-runtime ttf-japanese-gothic
  ttf-japanese-mincho ttf-thryomanes ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp ttf-arphic-bkai00mp xdg-utils libmail-box-perl
  procmail graphviz xfs xserver xfonts-100dpi xfonts-75dpi xfonts-scalable firmware-linux
Recommended packages:
  xserver-xorg-video-cyrix xserver-xorg-video-nsc
The following NEW packages will be installed:
  cvs debhelper defoma diffstat ethtool fontconfig fontconfig-config gettext hicolor-icon-theme html2text intel-gpu-tools intltool-debian libatk1.0-0
  libatk1.0-data libavahi-client3 libavahi-common-data libavahi-common3 libcairo2 libcairomm-1.0-1 libcroco3 libcups2 libdatrie1 libdirectfb-1.2-0
  libfontconfig1 libfontenc1 libgl1-mesa-dri libglibmm-2.4-1c2a libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkmm-2.4-1c2a libice6 libicu42 libjasper1
  libjpeg62 libmail-sendmail-perl libpango1.0-0 libpango1.0-common libpangomm-1.4-1 libpciaccess0 libpixman-1-0 libsm6 libsys-hostname-long-perl libsysfs2
  libthai-data libthai0 libtiff4 libts-0.0-0 liburiparser1 libxaw7 libxcb-render-util0 libxcb-render0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3
  libxfont1 libxft2 libxi6 libxinerama1 libxkbfile1 libxmu6 libxpm4 libxrandr2 libxrender1 libxss1 libxt6 libxtst6 libxv1 libxvmc1 module-assistant
  open-vm-source open-vm-toolbox open-vm-tools po-debconf quilt shared-mime-info tsconf ttf-dejavu-core x-ttcidfont-conf x11-common x11-xkb-utils xfonts-base
  xfonts-encodings xfonts-utils xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-vmmouse
  xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo zerofree
0 upgraded, 125 newly installed, 0 to remove and 5 not upgraded.
Need to get 43.6MB of archives.
After this operation, 163MB of additional disk space will be used.
Do you want to continue [Y/n]?
```
I didn't install it (yet)!
This is basically all X stuff which I don't need on the server.

I also read through the articles/links provided by LHammonds. Interesting, but also lots (not only) X related.

Since the purpose of all this is to end up connected USB devices to the guest, I'd like to know before I install 163 MB that this really works.

Thanks,

---

### Post by LHammonds on 2012-07-20
> **geohei said:**
> 
Since the purpose of all this is to end up connected USB devices to the guest, I'd like to know before I install 163 MB that this really works.
It's a VM.  Why don't you take a snapshot, install what is necessary and test it out...if it does not work, revert the snapshot to remove the changes you made.  If it works, commit the snapshot and keep the changes.

TIP: Always make a snapshot when the server is powered down to ensure there will be no problems if you need to revert to a prior snapshot.  Even though they can quiesce the running processes/memory, it is faster and less troublesome to snapshot a down'd system.

LHammonds

---

### Post by geohei on 2012-07-23
Yes, will do this.

But before, I try that one here:
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1648](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1648)

Looks promising. It's not exactly what my initial intention was (connect USB device from guest), but it connects the USB device when starting up guest.

---

### Post by geohei on 2012-07-24
> **geohei said:**
> 
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1648](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1648)

Looks promising. It's not exactly what my initial intention was (connect USB device from guest), but it connects the USB device when starting up guest.
I finally tested that one. I used the path parameter option.

I works like charm!

The path information was taken from the vmware.log.
I had to comment out the existing 'usb.autoConnect.device0 = ""' in the .vmx file first.
When I startup the guest now, the USB devices get connected properly.

Thanks.

---

