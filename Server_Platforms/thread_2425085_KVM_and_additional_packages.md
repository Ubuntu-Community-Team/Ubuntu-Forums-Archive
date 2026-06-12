---
title: "KVM and additional packages"
date: 2019-08-20
forum: Server Platforms
---

### Post by cosy2 on 2019-08-20
[https://help.ubuntu.com/community/KVM/Installation#Installation_of_KVM](https://help.ubuntu.com/community/KVM/Installation#Installation_of_KVM)

> For the following setup, we will assume that you are deploying KVM on a server, and therefore do not have any X server on the machine.

> sudo apt-get install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils

```
The following NEW packages will be installed:
  acl **adwaita-icon-theme** at-spi2-core bridge-utils dbus-user-session dconf-gsettings-backend dconf-service dns-root-data dnsmasq-base ebtables fontconfig fontconfig-config
  fonts-dejavu-core glib-networking glib-networking-common glib-networking-services gsettings-desktop-schemas gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-x
  gtk-update-icon-cache **hicolor-icon-theme humanity-icon-theme** ipxe-qemu ipxe-qemu-256k-compat-efi-roms libaa1 libasound2 libasound2-data libasyncns0 libatk-bridge2.0-0 libatk1.0-0
  libatk1.0-data libatspi2.0-0 libavahi-client3 libavahi-common-data libavahi-common3 libavc1394-0 libbluetooth3 libbrlapi0.6 libcaca0 libcacard0 libcairo-gobject2 libcairo2 libcdparanoia0
  libcolord2 libcroco3 libcups2 libdatrie1 libdconf1 libdv4 libepoxy0 libfdt1 libflac8 libfontconfig1 libgbm1 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-bin libgdk-pixbuf2.0-common libgraphite2-3
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer1.0-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgudev-1.0-0 libharfbuzz0b libiec61883-0 libiscsi7
  libjack-jackd2-0 libjbig0 libjpeg-turbo8 libjpeg8 libjson-glib-1.0-0 libjson-glib-1.0-common liblcms2-2 libmp3lame0 libmpg123-0 libogg0 libopus0 liborc-0.4-0 libpango-1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpciaccess0 libpcsclite1 libpixman-1-0 libpolkit-agent-1-0 libpolkit-backend-1-0 libproxy1v5 libpulse0 libraw1394-11 librbd1 librdmacm1
  librest-0.7-0 librsvg2-2 librsvg2-common libsamplerate0 libshout3 libsndfile1 libsoup-gnome2.4-1 libsoup2.4-1 libspeex1 libspice-server1 libtag1v5 libtag1v5-vanilla libthai-data libthai0
  libtheora0 libtiff5 libtwolame0 libusbredirparser1 libv4l-0 libv4lconvert0 libvirglrenderer0 libvirt-clients libvirt-daemon libvirt-daemon-driver-storage-rbd libvirt-daemon-system
  libvirt0 libvisual-0.4-0 libvorbis0a libvorbisenc2 libvpx5 libvte-2.91-0 libvte-2.91-common libwavpack1 libwayland-client0 libwayland-cursor0 libwayland-egl1 libwayland-server0 libwebp6
  libxcb-render0 libxcb-shm0 libxcomposite1 libxcursor1 libxdamage1 libxen-4.9 libxenstore3.0 libxfixes3 libxi6 libxinerama1 libxkbcommon0 libxml2-utils libxrandr2 libxrender1 libxtst6
  libxv1 libyajl2 policykit-1 qemu-block-extra qemu-kvm qemu-system-common qemu-system-data **qemu-system-gui** qemu-system-x86 qemu-utils seabios sharutils ubuntu-mono **x11-common**
```

do i really need all this trash?

---

### Post by TheFu on 2019-08-20
Have you run any updates on the desktop before?  Do that first.

Also, best not to have multiple hypervisors installed concurrently.  Don't have both KVM and Xen installed at the same time. Or Virtualbox.  1 at a time.

I don't install that list.

---

### Post by cosy2 on 2019-08-20
it was a clean Ubuntu server 19.04 install nothing fancy

---

### Post by TheFu on 2019-08-20
> **cosy2 said:**
> it was a clean Ubuntu server 19.04 install nothing fancy

Did you or did you not install updates?
Servers should almost always be using LTS releases. 19.04 is NOT an LTS.  Support for it ends January.

Avahi shouldn't be installed on any server, but it is installed on desktop releases.  This is part of my confusion.  There's a bunch of GUI stuff in there that makes no sense at all.  I don't have 19.04 anywhere.

Did a fresh 18.04 server install .... 
```
233 packages can be updated.
126 updates are security updates.

```
Patching now ...

---

### Post by cosy2 on 2019-08-20
> Did you or did you not install updates?
there were like 51 updates after install i dont see how is that relevant to top post


> vahi shouldn't be installed on any server, but it is installed on desktop releases. This is part of my confusion. There's a bunch of GUI stuff in there that makes no sense at all. I don't have 19.04 anywhere.

i am following the wiki

---

### Post by QIII on 2019-08-20
> **cosy2 said:**
> there were like 51 updates after install i dont see how is that relevant to top post

Updating immediately after install should be done as a rule and it is always relevant to diagnosis.

---

### Post by TheFu on 2019-08-20
So patching finished.  Then:
```
$ sudo apt install  --no-install-recommends  qemu-kvm  bridge-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  ipxe-qemu ipxe-qemu-256k-compat-efi-roms libaio1 libasound2 libasound2-data
  libasyncns0 libbluetooth3 libbrlapi0.6 libcaca0 libcacard0 libfdt1 libflac8
  libgstreamer-plugins-base1.0-0 libgstreamer1.0-0 libibverbs1 libiscsi7
  libjpeg-turbo8 libjpeg8 libnl-route-3-200 libnspr4 libnss3 libogg0 libopus0
  liborc-0.4-0 libpixman-1-0 libpulse0 librados2 librbd1 librdmacm1
  libsdl1.2debian libsndfile1 libspice-server1 libusbredirparser1 libvorbis0a
  libvorbisenc2 libxen-4.9 libxenstore3.0 libyajl2 qemu-block-extra
  qemu-system-common qemu-system-x86 seabios
Suggested packages:
  ifupdown libasound2-plugins alsa-utils libvisual-0.4-plugins
  gstreamer1.0-tools opus-tools pulseaudio samba vde2 sgabios ovmf
Recommended packages:
  gstreamer1.0-plugins-base ibverbs-providers gstreamer1.0-plugins-good
  qemu-utils
...
```

Don't let apt install *suggested* or *recommended* packages.

Dependency bugs, even with the minimal install, IMHO: [https://bugs.launchpad.net/qemu/+bugs](https://bugs.launchpad.net/qemu/+bugs)
Why would any sound or bluetooth3 be included?!!!  I have no interest in another online account (launchpad), but perhaps someone else does?  I've been hacked over bluetooth before. No thanks.

---

### Post by cruzer001 on 2019-08-20
Hello TheFu, how b ya :)

I have been following this thread with interests since I recently switched over to KVM from VirtualBox.  I also wondered about all those packages that showed up on a fresh (updated) virtual server install.  So I set up a fresh basic-server install and tried:

apt install qemu-kvm bridge-utils which equals 138pkgs/148M
--no-install-recommends = 70pkgs/100M

Quite the difference

---

### Post by cosy2 on 2019-08-20
note that for some stuff qemu-utils is needed

---

### Post by cruzer001 on 2019-08-20
> **cosy2 said:**
> note that for some stuff qemu-utils is needed
So I went ahead and finished the download.  qemu/virt-manager/libvirt-bin

Another 183pkgs/80M downloaded.

The packages could of been pulled back in, don't know, I didn't create a download file just based on what I could see in console.  It does seem to work ok.

---

### Post by TheFu on 2019-08-20
qemu-utils adds qemu-img and qemu-ndb ... which may or may not be important to you.  If you convert file-based storage to other formats or want to use QCOW2 snapshots, you'll want qemu-img.  I use LVM for my storage back end, so don't need it.  If I were doing clustered N+1 replicated storage, then I'd use sheepdog, so I don't think I'd need it then either.

Everyone has different requirements for their specific needs. Ain't nuffin' wrong with dat.

---

### Post by cosy2 on 2019-08-21
> libvirt-bin


for the record

> The package was split into two parts:

libvirt-daemon-system

libvirt-clients

In most cases you probably want both of them at the same time.

[https://askubuntu.com/questions/1089753/kvm-qemu-installation-issue-18-10/1089849#1089849](https://askubuntu.com/questions/1089753/kvm-qemu-installation-issue-18-10/1089849#1089849)

---

### Post by cruzer001 on 2019-08-22
qemu-utils - I show as installed
qemu-img and -ndb - I show as unavailable (not on my system)
libvirt-deamon-system and -clients - show installed

Edit
So it turns out on my install adding the qemu package pulls in qemu-utils and libvirt-bin pulls in daemon and clients.  All seems good and with no sign of bluetooth :)

QCOW2 also appears as working.  I think no-recommends can be used effectly on my install.

---

