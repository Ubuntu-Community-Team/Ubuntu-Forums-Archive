---
title: "Stuck at boot with raid (non boot) in fstab = useless."
date: 2010-11-01
forum: Server Platforms
---

### Post by trendle on 2010-11-01
Forgive the terseness.  I'm frazzled with this issue, perhaps I should have asked earlier.  Every weekend for the past 2 months has been an endless cycle of 'repair broken system' off the install disk.

Installed from Ubuntu server 10.04LTS x86_64, + xfce-desktop

Here is uname -a
Linux ournas 2.6.32-25-server #45-Ubuntu SMP Sat Oct 16 20:06:58 UTC 2010 x86_64 GNU/Linux

If I add my raid + lvm to the fstab file, the boot stalls, (no error it, just hangs waiting, forever).  So that's a not very user friendly to start with.

I've tried the suggestions about UUID in fstab tried using LABEL instead, or even /dev/xxx. Every time it hangs.

I've googled this endlessly and not found a solution.

So don't ask why... since I seem to have tried every odd suggestion to fix this, I've lost track. There seems to be some consensus that whoever gave us plymouth laid an egg.  Forgive me if I'm wrong, but did we need a better graphical boot if it breaks everything else?

So I tried to reinstall plymouth. That's a bust !!!.  Something seriously wrong there if you can't successfully reinstall a piece of software.....
and no useful error messages.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages will be REINSTALLED:
  plymouth 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/123kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 188832 files and directories currently installed.)
Preparing to replace plymouth 0.8.2-2ubuntu2 (using .../plymouth_0.8.2-2ubuntu2_amd64.deb) ...
Unpacking replacement plymouth ...
Processing triggers for ureadahead ...
Setting up plymouth (0.8.2-2ubuntu2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-25-server
.: 6: Can't open /scripts/functions
.: 5: Can't open /scripts/functions
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
----------------
And if I try and uninstall plymouth is wants to trash everything !!!!!!
Whats with that ?  It's not what I asked for.
----------------
sudo apt-get remove plymouth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono-data-tds2.0-cil liblash2 meld libsdl-ttf2.0-0 libxfce4menu-0.1-0 menu libnumber-compare-perl
  libwpd8c2a dnsmasq-base python-notify libmono-security2.0-cil python-cupshelpers libecryptfs0
  python-bluez libgnome-bluetooth7 libndesk-dbus1.0-cil gedit-common libmono-addins-gui0.2-cil xsltproc
  libsilcclient-1.1-3 libido-0.1-0 lp-solve libwxbase2.8-0 libaiksaurus-1.2-data libunique-1.0-0
  libgmime-2.4-2 libnet-ip-perl libmono-system2.0-cil squashfs-tools libpurple-bin python-numpy
  libnet-dns-perl nvidia-common libgtk-vnc-1.0-0 libmeanwhile1 libgucharmap7 libkpathsea5 libwmf0.2-7
  intel-gpu-tools libmono-sqlite2.0-cil libevdocument2 libnunit2.4-cil libdebconfclient0 remuco-base
  libavc1394-0 python-pygame discover-data zenity libdiscid0 link-grammar-dictionaries-en gadmin-dhcpd
  libotr2 libots0 desktop-file-utils libspectre1 libqtscript4-network bind9utils libbeagle1
  libmono-corlib2.0-cil dhcp3-server libsdl-mixer1.2 lzop cli-common libfile-find-rule-perl libjpeg-progs
  alacarte gnome-menus libmono-cairo2.0-cil libevview2 libndesk-dbus-glib1.0-cil libgupnp-1.0-3
  gadmin-rsync libavfilter0 nvidia-current-modaliases squid-common transcode-doc
  mobile-broadband-provider-info abiword-common libindicate-gtk2 libgdata-google1.2-1
  libmono-i18n-west2.0-cil guile-1.8-libs libwps-0.1-1 xfdesktop4-data afio libiso9660-7 libsqlite0
  libcddb2 libportmidi0 libgdict-1.0-6 python-gtksourceview2 xdg-user-dirs libavdevice52 libmysqlclient-dev
  libjs-prototype libgoffice-0.8-8-common libtag-extras1 openvpn-blacklist fortune-mod
  xfce-keyboard-shortcuts libmono-posix2.0-cil mono-runtime liblapack3gf libcanberra-gtk-module pidgin-data
  libcanberra0 libqtscript4-sql libmono-addins0.2-cil dcraw libgadu3 xorg-docs-core xresprobe discover
  libdvbpsi5 libpsiconv6 user-setup libmono-system-runtime2.0-cil toshset libglitz-glx1 liblqr-1-0
  transmission-common k3b-data libqtscript4-xml python-mmkeys libthunar-vfs-1-2 ttf-lyx libqt4-dbg
  gadmin-openvpn-server python-gmenu libindicate4 libdevkit-power-gobject1 rdate libcue1 libbabl-0.0-0
  libgegl-0.0-0 librecode0 libiec61883-0 xinput libvlc2 libgdu-gtk0 libgdata-common libgtkspell0
  libbinio1ldbl xubuntu-artwork libsdl-image1.2 finger liblink-grammar4 libclutter-gtk-0.10-0 rtkit
  xubuntu-wallpapers libt1-5 vlc-nox libpkcs11-helper1 gdb libaudclient2 libsilc-1.1-2 libjs-scriptaculous
  bogl-bterm libgraphviz4 binfmt-support amarok-utils libwv-1.2-3 python-launchpad-integration
  libmono-system-data2.0-cil libresid-builder0c2a libreadline5 libmono2.0-cil libgdome2-0 python-sexy
  libupnp3 ubiquity-ubuntu-artwork libtelepathy-glib0 mono-gac libcolamd2.7.1 libdebian-installer4
  indicator-messages xubuntu-icon-theme libmatroska0 liblensfun-data modemmanager icedax
  libaiksaurusgtk-1.2-0c2a python-smbc system-config-printer-udev libglade2.0-cil libclutter-1.0-0 buffer
  libxcb-keysyms1 libart2.0-cil libneon27-gnutls ffmpeg libglitz1 libglib2.0-cil audacity-data
  amarok-common mono-2.0-gac libdjvulibre21 libpoppler-glib4 libgtkmathview0c2a libdevmapper-event1.02.1
  liblzo2-2 libdate-calc-perl libcanberra-gtk0 localechooser-data openssl-blacklist python-appindicator
  squid-langpack libflickrnet2.2-cil libshout3 libmowgli1 libmono-sharpzip2.84-cil liblensfun0
  xfce4-power-manager-data ubiquity-casper libcarp-clan-perl thunar-data libfs6 gstreamer0.10-x libblas3gf
  libtext-glob-perl fglrx-modaliases libtotem-plparser17 nvidia-96-modaliases filezilla-common libnfsidmap2
  libgimp2.0 gnumeric-common liblircclient0 libxxf86misc1 libaudcore1 wwwconfig-common libgupnp-igd-1.0-2
  libc6-dbg libsidplay2 libboost-serialization1.40.0 gnome-desktop-data python-cups reiserfsprogs
  libnautilus-extension1 liblua5.1-0 libmono-system-web2.0-cil python-gst0.10 libdiscover2 mjpegtools
  fortunes-min libgfortran3 libgnome-keyring1.0-cil evolution-data-server-common librpcsecgss3
  libgtksourceview2.0-0 vlc-data libzephyr4 libmhash2 libwpg-0.1-1 libaiksaurus-1.2-0c2a libtar miscfiles
  libvamp-hostsdk3 python-pyicu libmcs1 libgnome-menu2 openvpn system-config-printer-common liblastfm0
  dvd+rw-tools python-libuser python-xkit libdjvulibre-text libavahi-gobject0 marble-data libnice0
  libgtk2.0-cil murrine-themes libgssglue1 gstreamer0.10-nice libloudmouth1-0 gimp-data libqtscript4-core
  libvlccore2 libvcdinfo0 mdadm libxmlrpc-core-c3 libebml0 discover1 nvidia-173-modaliases libaudid3tag2
  mscompress python-rdflib libgdata1.2-1 openbsd-inetd bcmwl-modaliases gadmin-openvpn-client
  javascript-common libdigest-hmac-perl libgssdp-1.0-2 gnome-doc-utils gnumeric-doc mindi-busybox
  libxkbfile1 libgdiplus libbit-vector-perl libgd2-noxpm libgdome2-cpp-smart0c2a libgtksourceview2.0-common
  libsmpeg0
---------------------


So where do I go now ... Windows7 ? ... god knows, if I paid myself for the time I've wasted on this it would be a bargain, but that's not why I persevere.  

So... anyone got a fix ? 
Please....

---

### Post by dtfinch on 2010-11-01
I've never had lvm on md raid work "out of the box" with 10.04. I have to add a udev rule to get it to detect the lvm groups at boot, otherwise it stalls waiting.

[http://ubuntuforums.org/showthread.php?t=1564411](http://ubuntuforums.org/showthread.php?t=1564411)

And if you haven't already, you'll also want to make sure to update your mdadm.conf with your array details (like "mdadm --examine --scan >> /etc/mdadm/mdadm.conf" then examining it manually), otherwise the autodetection might randomly steal one of the drives to make a new partial inactive "md_d0" raid, which would also cause a stall. I've forgotten this on a few systems already.

Not sure about your plymouth issues.

---

### Post by trendle on 2010-11-01
Thank,
I've tried the fix, (but still to reboot), fingers Xed.

I now get update-initramfs errors....

sudo update-initramfs -u -k `uname -r`
update-initramfs: Generating /boot/initrd.img-2.6.32-25-server
.: 6: Can't open /scripts/functions
.: 5: Can't open /scripts/functions

Seems that there's a Debian bug report about this ...
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=576641](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=576641)

(above with -v option)
Calling hook dmsetup
.: 6: Can't open /scripts/functions
.: 5: Can't open /scripts/functions

So will need to dig a bit deeper.
Will report on the results, anon.

---

### Post by trendle on 2010-11-02
So I'm now completely out of my depth here... 
But I hacked in a few comment lines in the two culprit files...
in /usr/share/initramfs-tools/scripts
they are
init-top/runbootcdmodprobe 
init-premount/runbootcdproberoot

and now the problem is exposed.... but I don't understand 
1) why are these scripts sourcing from non-existent root paths ?
2) what are they doing ?
3) how do I fix it if it really is a problem ?

sudo update-initramfs -v -u -k `uname -r`

Calling hook dmsetup
+ echo ------------------------------- runbootcdproberoot --------------------
+ . /scripts/functions
.: 1: Can't open /scripts/functions
+ set -e
+ PREREQ=
+ prereqs
+ echo 
+ exit 0
+ echo -------------------- runbootcdmodprobe -----------------------
+ . /scripts/functions
.: 1: Can't open /scripts/functions

Well,  it doesn't look like the echo is actually being executed.
If I blindly hack in the full path to functions...

Calling hook dmsetup
+ . /usr/share/initramfs-tools/scripts/functions
+ echo -- #------------------------------- runbootcdproberoot --------------------
+ PREREQ=udev
+ prereqs
+ echo udev
+ exit 0
+ . /usr/share/initramfs-tools/scripts/functions
+ echo -- #-------------------- runbootcdmodprobe -----------------------
+ PREREQ=
+ prereqs
+ echo 
+ exit 0

No message, is it fixed ?  Should I leave it ?.

---

