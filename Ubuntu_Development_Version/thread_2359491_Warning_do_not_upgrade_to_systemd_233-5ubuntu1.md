---
title: "Warning: do not upgrade to systemd 233-5ubuntu1"
date: 2017-04-24
forum: Ubuntu Development Version
---

### Post by harry332 on 2017-04-24
After upgrading to the newest systemd 233-5ubuntu1 (in artful proposed) I got no network.
**This is very likely a DNS issue.**
As a workaround downgrading back to systemd 232-21ubuntu3 the network and DNS work fine.

**~$ systemd-resolve --status**
Failed to get global data: Unit dbus-org.freedesktop.resolve1.service not found.

---

### Post by ventrical on 2017-04-24
> **harry332 said:**
> After upgrading to the newest systemd 233-5ubuntu1 (in artful proposed) I got no network.
**This is very likely a DNS issue.**
As a workaround downgrading back to systemd 232-21ubuntu3 the network and DNS work fine.

**~$ systemd-resolve --status**
Failed to get global data: Unit dbus-org.freedesktop.resolve1.service not found.

Thanks for the heads up.

Regards..

---

### Post by #&amp;thj^% on 2017-04-24
> **harry332 said:**
> After upgrading to the newest systemd 233-5ubuntu1 (in artful proposed) I got no network.
**This is very likely a DNS issue.**
As a workaround downgrading back to systemd 232-21ubuntu3 the network and DNS work fine.

**~$ systemd-resolve --status**
Failed to get global data: Unit dbus-org.freedesktop.resolve1.service not found.

Sorry to hear this but all is good here:
```
$ apt policy systemd
systemd:
  Installed: 233-5ubuntu1
  Candidate: 233-5ubuntu1
  Version table:
 *** 233-5ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu artful-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     232-21ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu artful/main amd64 Packages


```
AND:
```
$ systemd-resolve --status
Global
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

Link 2 (enp0s3)
      Current Scopes: DNS LLMNR/IPv4 LLMNR/IPv6
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: allow-downgrade
    DNSSEC supported: yes
         DNS Servers: 75.75.76.76
                      75.75.75.75




```

network card:
```
 inxi -N
Network:   Card: Intel 82540EM Gigabit Ethernet Controller driver: e1000


```

---

### Post by jbicha on 2017-04-24
Harry, did you file a bug?

---

### Post by ventrical on 2017-04-24
> **1fallen said:**
> Sorry to hear this but all is good here:
```
$ apt policy systemd
systemd:
  Installed: 233-5ubuntu1
  Candidate: 233-5ubuntu1
  Version table:
 *** 233-5ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu artful-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     232-21ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu artful/main amd64 Packages


```
AND:
```
$ systemd-resolve --status
Global
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

Link 2 (enp0s3)
      Current Scopes: DNS LLMNR/IPv4 LLMNR/IPv6
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: allow-downgrade
    DNSSEC supported: yes
         DNS Servers: 75.75.76.76
                      75.75.75.75




```

network card:
```
 inxi -N
Network:   Card: Intel 82540EM Gigabit Ethernet Controller driver: e1000


```


I did an upgrade on a non-production machine . Turned on proposed then upgraded. It ripped the ubuntu-desktop right out along with all the kernels. It is a dual install so when I run :
```

sudo update-grub

```

it shows me that artful is installed with linux kernels there but it won't come up to grub from /sda6

Also .. before I rebooted, it shut down the network as harry described. I'll try to get it back up somehow.

---

### Post by #&amp;thj^% on 2017-04-24
> **ventrical said:**
> I did an upgrade on a non-production machine . Turned on proposed then upgraded. It ripped the ubuntu-desktop right out along with all the kernels. It is a dual install so when I run :
```

sudo update-grub

```

it shows me that artful is installed with linux kernels there but it won't come up to grub from /sda6

Also .. before I rebooted, it shut down the network as harry described. I'll try to get it back up somehow.

Well for goodness sake??? I've been running with proposed since day one here and no bad or show stoppers as of yet.
Here is everything that has come from the Proposed repos:
```
$ awk '$1 == "Package:" { if (a[$2]++ == 0) print $2; }' /var/lib/apt/lists/*proposed*Packages
acl
advancecomp
bind9
bind9-doc
bind9-host
bind9utils
ceph
ceph-base
ceph-common
ceph-mon
ceph-osd
conntrack
cpp-6
cpp-6-doc
crmsh
crmsh-doc
cron
dctrl-tools
dnsutils
firefox
firefox-dbg
firefox-dev
firefox-locale-af
firefox-locale-an
firefox-locale-ar
firefox-locale-as
firefox-locale-ast
firefox-locale-az
firefox-locale-be
firefox-locale-bg
firefox-locale-bn
firefox-locale-br
firefox-locale-bs
firefox-locale-ca
firefox-locale-cak
firefox-locale-cs
firefox-locale-csb
firefox-locale-cy
firefox-locale-da
firefox-locale-de
firefox-locale-el
firefox-locale-en
firefox-locale-eo
firefox-locale-es
firefox-locale-et
firefox-locale-eu
firefox-locale-fa
firefox-locale-fi
firefox-locale-fr
firefox-locale-fy
firefox-locale-ga
firefox-locale-gd
firefox-locale-gl
firefox-locale-gn
firefox-locale-gu
firefox-locale-he
firefox-locale-hi
firefox-locale-hr
firefox-locale-hsb
firefox-locale-hu
firefox-locale-hy
firefox-locale-id
firefox-locale-is
firefox-locale-it
firefox-locale-ja
firefox-locale-ka
firefox-locale-kab
firefox-locale-kk
firefox-locale-km
firefox-locale-kn
firefox-locale-ko
firefox-locale-ku
firefox-locale-lg
firefox-locale-lt
firefox-locale-lv
firefox-locale-mai
firefox-locale-mk
firefox-locale-ml
firefox-locale-mn
firefox-locale-mr
firefox-locale-ms
firefox-locale-nb
firefox-locale-nl
firefox-locale-nn
firefox-locale-nso
firefox-locale-oc
firefox-locale-or
firefox-locale-pa
firefox-locale-pl
firefox-locale-pt
firefox-locale-ro
firefox-locale-ru
firefox-locale-si
firefox-locale-sk
firefox-locale-sl
firefox-locale-sq
firefox-locale-sr
firefox-locale-sv
firefox-locale-sw
firefox-locale-ta
firefox-locale-te
firefox-locale-th
firefox-locale-tr
firefox-locale-uk
firefox-locale-ur
firefox-locale-uz
firefox-locale-vi
firefox-locale-xh
firefox-locale-zh-hans
firefox-locale-zh-hant
firefox-locale-zu
g++-6
g++-6-multilib
gcc-6
gcc-6-base
gcc-6-doc
gcc-6-multilib
gcc-6-plugin-dev
gccgo-6-doc
gcj-6-jre-lib
gfortran-6
gfortran-6-doc
gfortran-6-multilib
gir1.2-ubuntu-app-launch-3
gnome-calendar
kpartx
kpartx-boot
krb5-doc
krb5-locales
krb5-multidev
lib32asan3
lib32asan3-dbg
lib32atomic1
lib32atomic1-dbg
lib32cilkrts5
lib32cilkrts5-dbg
lib32gcc-6-dev
lib32gcc1
lib32gcc1-dbg
lib32gfortran-6-dev
lib32gfortran3
lib32gfortran3-dbg
lib32gomp1
lib32gomp1-dbg
lib32gphobos-6-dev
lib32gphobos68
lib32gphobos68-dbg
lib32itm1
lib32itm1-dbg
lib32lsan0
lib32lsan0-dbg
lib32mpx2
lib32mpx2-dbg
lib32objc-6-dev
lib32objc4
lib32objc4-dbg
lib32quadmath0
lib32quadmath0-dbg
lib32stdc++-6-dev
lib32stdc++6
lib32stdc++6-6-dbg
lib32ubsan0
lib32ubsan0-dbg
libacl1
libacl1-dev
libasan3
libasan3-dbg
libasm-dev
libasm1
libatomic1
libatomic1-dbg
libbind-dev
libbind-export-dev
libbind9-140
libcc1-0
libcephfs-dev
libcephfs1
libcilkrts5
libcilkrts5-dbg
libdns-export162
libdns162
libdw-dev
libdw1
libelf-dev
libelf1
libgcc-6-dev
libgcc1
libgcc1-dbg
libgccjit-6-dev
libgccjit-6-doc
libgccjit0
libgccjit0-dbg
libgcj-doc
libgcj17
libgcj17-awt
libgcj17-dbg
libgcj17-dev
libgfortran-6-dev
libgfortran3
libgfortran3-dbg
libgomp1
libgomp1-dbg
libgphobos-6-dev
libgphobos68
libgphobos68-dbg
libgssapi-krb5-2
libgssrpc4
libirs-export141
libirs141
libisc-export160
libisc160
libisccc-export140
libisccc140
libisccfg-export140
libisccfg140
libitm1
libitm1-dbg
libk5crypto3
libkadm5clnt-mit11
libkadm5srv-mit11
libkdb5-8
libkrad-dev
libkrad0
libkrb5-3
libkrb5-dbg
libkrb5-dev
libkrb5support0
liblsan0
liblsan0-dbg
liblwres141
libmetacity-dev
libmetacity1
libmpx2
libmpx2-dbg
libnss-myhostname
libnss-resolve
libobjc-6-dev
libobjc4
libobjc4-dbg
libpam-cracklib
libpam-doc
libpam-modules
libpam-modules-bin
libpam-runtime
libpam-systemd
libpam0g
libpam0g-dev
libpci-dev
libpci3
libquadmath0
libquadmath0-dbg
librados-dev
librados2
libradosstriper-dev
libradosstriper1
librbd-dev
librbd1
librgw-dev
librgw2
libstdc++-6-dev
libstdc++-6-doc
libstdc++6
libstdc++6-6-dbg
libsystemd-dev
libsystemd0
libtsan0
libtsan0-dbg
libubsan0
libubsan0-dbg
libubuntu-app-launch3-dev
libubuntu-app-launch4
libubuntugestures5
libubuntugestures5-dev
libubuntugestures5-private-dev
libubuntumetrics5
libubuntumetrics5-dev
libubuntumetrics5-private-dev
libubuntutoolkit5
libubuntutoolkit5-dev
libubuntutoolkit5-private-dev
libudev-dev
libudev1
libx32asan3
libx32asan3-dbg
libx32atomic1
libx32atomic1-dbg
libx32cilkrts5
libx32cilkrts5-dbg
libx32gcc-6-dev
libx32gcc1
libx32gcc1-dbg
libx32gfortran-6-dev
libx32gfortran3
libx32gfortran3-dbg
libx32gomp1
libx32gomp1-dbg
libx32gphobos-6-dev
libx32gphobos68
libx32gphobos68-dbg
libx32itm1
libx32itm1-dbg
libx32lsan0
libx32lsan0-dbg
libx32objc-6-dev
libx32objc4
libx32objc4-dbg
libx32quadmath0
libx32quadmath0-dbg
libx32stdc++-6-dev
libx32stdc++6
libx32stdc++6-6-dbg
libx32ubsan0
libx32ubsan0-dbg
metacity
metacity-common
multipath-tools
multipath-tools-boot
open-vm-tools
open-vm-tools-dev
openssh-client
openssh-server
openssh-sftp-server
pciutils
pkg-config
python-aodhclient
python-aodhclient-doc
python-automaton
python-automaton-doc
python-castellan
python-castellan-doc
python-ceph
python-cephfs
python-cinderclient
python-cliff
python-cliff-doc
python-debtcollector
python-debtcollector-doc
python-futurist
python-futurist-doc
python-heatclient
python-keystoneauth1
python-keystoneauth1-doc
python-keystonemiddleware
python-keystonemiddleware-doc
python-openstackclient
python-openstackclient-doc
python-os-win
python-os-win-doc
python-osc-lib
python-osc-lib-doc
python-oslo-serialization-doc
python-oslo-vmware-doc
python-oslo.cache
python-oslo.cache-doc
python-oslo.concurrency
python-oslo.concurrency-doc
python-oslo.config
python-oslo.config-doc
python-oslo.context
python-oslo.context-doc
python-oslo.db
python-oslo.db-doc
python-oslo.i18n
python-oslo.i18n-doc
python-oslo.log
python-oslo.log-doc
python-oslo.middleware
python-oslo.middleware-doc
python-oslo.policy
python-oslo.policy-doc
python-oslo.privsep
python-oslo.privsep-doc
python-oslo.reports
python-oslo.reports-doc
python-oslo.rootwrap
python-oslo.serialization
python-oslo.serialization-doc
python-oslo.service
python-oslo.service-doc
python-oslo.utils
python-oslo.utils-doc
python-oslo.vmware
python-oslo.vmware-doc
python-pbr
python-pbr-doc
python-rados
python-rbd
python-requests
python-stevedore
python-stevedore-doc
python-urllib3
python-webob
python-webob-doc
python3-cliff
python3-pbr
python3-requests
python3-stevedore
python3-urllib3
python3-webob
qml-module-ubuntu-components
qml-module-ubuntu-components-labs
qml-module-ubuntu-layouts
qml-module-ubuntu-performancemetrics
qml-module-ubuntu-test
qtdeclarative5-ubuntu-ui-toolkit-plugin
radosgw
ssh
strace
systemd
systemd-sysv
systemd-tests
ubuntu-app-launch
ubuntu-ui-toolkit-doc
ubuntu-ui-toolkit-theme
udev
unattended-upgrades
lib64asan3
lib64asan3-dbg
lib64atomic1
lib64atomic1-dbg
lib64cilkrts5
lib64cilkrts5-dbg
lib64gcc-6-dev
lib64gcc1
lib64gcc1-dbg
lib64gfortran-6-dev
lib64gfortran3
lib64gfortran3-dbg
lib64gomp1
lib64gomp1-dbg
lib64gphobos-6-dev
lib64gphobos68
lib64gphobos68-dbg
lib64itm1
lib64itm1-dbg
lib64mpx2
lib64mpx2-dbg
lib64objc-6-dev
lib64objc4
lib64objc4-dbg
lib64quadmath0
lib64quadmath0-dbg
lib64stdc++-6-dev
lib64stdc++6
lib64stdc++6-6-dbg
lib64ubsan0
lib64ubsan0-dbg
imgtex
libmyth-0.28-0
libmyth-dev
libmyth-python
libmythtv-perl
mytharchive
mythbrowser
mythgallery
mythgame
mythmusic
mythnetvision
mythnews
mythplugins
mythtv
mythtv-backend
mythtv-backend-master
mythtv-common
mythtv-database
mythtv-dbg
mythtv-doc
mythtv-frontend
mythtv-theme-mythbuntu
mythtv-transcode-utils
mythweather
mythweb
mythzoneminder
nvidia-persistenced
php-mythtv
account-plugin-ubuntuone
acl2
acl2-books
acl2-books-certs
acl2-books-source
acl2-doc
acl2-emacs
acl2-infix
acl2-infix-source
acl2-source
aegisub
aegisub-dbg
aegisub-l10n
asdftool
autopilot-desktop
autopilot-touch
bareos
bareos-bat
bareos-bconsole
bareos-client
bareos-common
bareos-database-common
bareos-database-mysql
bareos-database-postgresql
bareos-database-sqlite3
bareos-database-tools
bareos-dbg
bareos-devel
bareos-director
bareos-director-python-plugin
bareos-filedaemon
bareos-filedaemon-ceph-plugin
bareos-filedaemon-glusterfs-plugin
bareos-filedaemon-ldap-python-plugin
bareos-filedaemon-python-plugin
bareos-storage
bareos-storage-ceph
bareos-storage-fifo
bareos-storage-glusterfs
bareos-storage-python-plugin
bareos-storage-tape
bareos-tools
bareos-traymonitor
bcron
bcron-run
bino
breathe-doc
cacti
cadvisor
ceph-fs-common
ceph-fuse
ceph-mds
ceph-resource-agents
ceph-test
cgpt
cgroup-lite
cl-pgloader
clang-3.8
clang-3.8-doc
clang-3.8-examples
clang-5.0
clang-5.0-doc
clang-5.0-examples
clang-format-3.8
clang-format-5.0
clang-tidy-3.8
clang-tidy-5.0
clisp
clisp-dev
clisp-doc
clisp-module-berkeley-db
clisp-module-bindings-glibc
clisp-module-clx
clisp-module-dbus
clisp-module-gdbm
clisp-module-pcre
clisp-module-postgresql
clisp-module-rawsock
clisp-module-wildcard
clisp-module-zlib
clsync
conntrackd
crack
crack-common
crack-md5
ddcci-dkms
discount
elasticsearch-curator
elfutils
ffmpeg
ffmpeg-doc
firefox-globalmenu
firefox-mozsymbols
firefox-testsuite
fiu-utils
fixincludes
frama-c
frama-c-base
freedombox-setup
freedroidrpg
freedroidrpg-data
fsprotect
gcc-6-hppa64-linux-gnu
gcc-6-locales
gcc-6-source
gcc-6-test-results
gccgo-6
gccgo-6-multilib
gcj-6
gcj-6-jdk
gcj-6-jre
gcj-6-jre-headless
gcj-6-source
gdc-6
gdc-6-multilib
gir1.2-gst-plugins-bad-1.0
gir1.2-ostree-1.0
gist
gnat-6
gnat-6-doc
gnat-6-sjlj
gobjc++-6
gobjc++-6-multilib
gobjc-6
gobjc-6-multilib
golang-docker-credential-helpers
golang-github-docker-docker-credential-helpers-dev
golang-github-google-cadvisor-dev
golang-github-syncthing-syncthing-dev
gpaw
gstreamer1.0-plugins-bad
gstreamer1.0-plugins-bad-dbg
gstreamer1.0-plugins-bad-doc
gstreamer1.0-plugins-bad-faad
gstreamer1.0-plugins-bad-videoparsers
gyoto
gyoto-bin
gyoto-dbg
gyoto-doc
handbrake
handbrake-cli
host
ike-scan
krb5-admin-server
krb5-gss-samples
krb5-k5tls
krb5-kdc
krb5-kdc-ldap
krb5-kpropd
krb5-otp
krb5-pkinit
krb5-user
lava
lava-dev
lava-dispatcher
lava-server
lava-server-doc
lib32go9
lib32go9-dbg
libalog-doc
libalog0.5.2
libalog2-dev
libapache2-mod-gnutls
libapache2-mod-php7.1
libass-dev
libass9
libav-tools
libavcodec-dev
libavcodec-extra
libavcodec-extra57
libavcodec57
libavdevice-dev
libavdevice57
libavfilter-dev
libavfilter-extra
libavfilter-extra6
libavfilter6
libavformat-dev
libavformat57
libavresample-dev
libavresample3
libavutil-dev
libavutil55
libbde-dbg
libbde-dev
libbde-utils
libbde1
libblitz-doc
libblitz0-dev
libblitz0v5
libcephfs-java
libcephfs-jni
libclang-3.8-dev
libclang-5.0-dev
libclang-common-3.8-dev
libclang-common-5.0-dev
libclang1-3.8
libclang1-3.8-dbg
libclang1-5.0
libclang1-5.0-dbg
libclsync-dev
libclsync0
libcore-extended-ocaml
libcore-extended-ocaml-dev
libcore-ocaml
libcore-ocaml-dev
libdist-zilla-perl
libextutils-parsexs-perl
libfiu-dev
libfiu0
libfuzzer-3.8-dev
libfuzzer-5.0-dev
libgnat-6
libgnat-6-dbg
libgnatprj6
libgnatprj6-dbg
libgnatprj6-dev
libgnatvsn6
libgnatvsn6-dbg
libgnatvsn6-dev
libgo9
libgo9-dbg
libgstreamer-plugins-bad1.0-0
libgstreamer-plugins-bad1.0-dev
libgyoto6
libgyoto6-dev
liblld-5.0
liblld-5.0-dbg
liblld-5.0-dev
liblldb-3.8
liblldb-3.8-dbg
liblldb-3.8-dev
liblldb-5.0
liblldb-5.0-dbg
liblldb-5.0-dev
libllvm-3.8-ocaml-dev
libllvm-5.0-ocaml-dev
libllvm3.8
libllvm3.8-dbg
libllvm5.0
libllvm5.0-dbg
libmarkdown2
libmarkdown2-dev
libmpv-dev
libmpv1
libncursesada-doc
libncursesada4
libncursesada4-dev
libnss-mymachines
libnss-systemd
libostree-1-1
libostree-dev
libostree-doc
libphonon-dev
libphonon4
libphonon4qt5-4
libphonon4qt5-dev
libphonon4qt5experimental-dev
libphonon4qt5experimental4
libphononexperimental-dev
libphononexperimental4
libphp7.1-embed
libpostproc-dev
libpostproc54
libre2-ocaml
libre2-ocaml-dev
librecon-1.11
librecon-1.11-dev
libresiprocate-1.11
libresiprocate-1.11-dev
libresiprocate-turn-client-1.11
libresiprocate-turn-client-1.11-dev
libretro-bsnes-mercury-accuracy
libretro-bsnes-mercury-balanced
libretro-bsnes-mercury-performance
libservice-wrapper-doc
libservice-wrapper-java
libservice-wrapper-jni
libstdc++-6-pic
libswresample-dev
libswresample2
libswscale-dev
libswscale4
libtest-most-perl
libtextutils-ocaml
libtextutils-ocaml-dev
libubuntuoneauth-2.0-0
libubuntuoneauth-2.0-dev
liburweb-cgi0
liburweb-fastcgi0
liburweb-http0
liburweb-static0
liburweb0
libv8-3.14-dbg
libv8-3.14-dev
libv8-3.14.5
libv8-dev
libvlc-bin
libvlc-dev
libvlc5
libvlccore-dev
libvlccore8
libwhy-coq
libx32go9
libx32go9-dbg
libyara-dev
libyara3
libyaz5
libyaz5-dev
liferea
liferea-data
live-config
live-config-doc
live-config-systemd
live-config-sysvinit
live-image-cinnamon-desktop
live-image-gnome-desktop
live-image-kde-desktop
live-image-lxde-desktop
live-image-mate-desktop
live-image-standard
live-image-xfce-desktop
live-images
live-task-base
live-task-cinnamon
live-task-extra
live-task-gnome
live-task-kde
live-task-localisation
live-task-localisation-desktop
live-task-lxde
live-task-mate
live-task-recommended
live-task-xfce
lld-5.0
lldb-3.8
lldb-3.8-dev
lldb-5.0
llvm-3.7-doc
llvm-3.7-examples
llvm-3.8
llvm-3.8-dev
llvm-3.8-doc
llvm-3.8-examples
llvm-3.8-runtime
llvm-3.8-tools
llvm-5.0
llvm-5.0-dev
llvm-5.0-doc
llvm-5.0-examples
llvm-5.0-runtime
llvm-5.0-tools
lwresd
mencoder
mercurial
mercurial-common
mongodb
mongodb-clients
mongodb-server
mplayer
mplayer-doc
mplayer-gui
mplayer2
mpv
nfct
node-resumer
nodejs
nodejs-dbg
nodejs-dev
nodejs-legacy
open-vm-tools-desktop
open-vm-tools-dkms
openssh-client-ssh1
osslsigncode
ostree
ostree-tests
pgloader
phonon
phonon-backend-null
phonon-backend-vlc
phonon4qt5
phonon4qt5-backend-null
phonon4qt5-backend-vlc
php7.1
php7.1-bcmath
php7.1-bz2
php7.1-cgi
php7.1-cli
php7.1-common
php7.1-curl
php7.1-dba
php7.1-dev
php7.1-enchant
php7.1-fpm
php7.1-gd
php7.1-gmp
php7.1-imap
php7.1-interbase
php7.1-intl
php7.1-json
php7.1-ldap
php7.1-mbstring
php7.1-mcrypt
php7.1-mysql
php7.1-odbc
php7.1-opcache
php7.1-pgsql
php7.1-phpdbg
php7.1-pspell
php7.1-readline
php7.1-recode
php7.1-snmp
php7.1-soap
php7.1-sqlite3
php7.1-sybase
php7.1-tidy
php7.1-xml
php7.1-xmlrpc
php7.1-xsl
php7.1-zip
profanity
python-asdf
python-asdf-doc
python-boto
python-breathe
python-clang-3.8
python-clang-5.0
python-cxx-dev
python-dmidecode
python-dmidecode-dbg
python-elasticsearch-curator
python-elasticsearch-curator-doc
python-fiu
python-guessit
python-gyoto
python-healpy
python-healpy-data
python-ironic-lib
python-libbde
python-lldb-3.8
python-lldb-5.0
python-oslo-serialization
python-oslo-vmware
python-oslotest
python-oslotest-doc
python-pywt
python-pywt-doc
python-schooltool
python-schooltool.cando
python-schooltool.gradebook
python-schooltool.intervention
python-schooltool.ldap
python-schooltool.lyceum.journal
python-toolz-doc
python-z3c.rml
python-zodb
python3-aodhclient
python3-asdf
python3-automaton
python3-autopilot
python3-autopilot-tests
python3-autopilot-trace
python3-autopilot-vis
python3-boto
python3-breathe
python3-castellan
python3-cinderclient
python3-cxx-dev
python3-debtcollector
python3-elasticsearch-curator
python3-fiu
python3-futurist
python3-guessit
python3-gyoto
python3-healpy
python3-heatclient
python3-ironic-lib
python3-keystoneauth1
python3-keystonemiddleware
python3-libbde
python3-openstackclient
python3-os-win
python3-osc-lib
python3-oslo-serialization
python3-oslo.cache
python3-oslo.concurrency
python3-oslo.config
python3-oslo.context
python3-oslo.db
python3-oslo.i18n
python3-oslo.log
python3-oslo.middleware
python3-oslo.policy
python3-oslo.privsep
python3-oslo.reports
python3-oslo.rootwrap
python3-oslo.serialization
python3-oslo.service
python3-oslo.utils
python3-oslo.vmware
python3-oslotest
python3-pywt
python3-toolz
qml-module-ubuntu-metrics
qml-module-ubuntuone
qtdeclarative5-qtmir-plugin
qtmir-android
qtmir-desktop
qtmir-tests
rbd-fuse
rbd-mirror
rbd-nbd
redis-sentinel
redis-server
redis-tools
repro
resiprocate-turn-server
resiprocate-turn-server-psql
rpmlint
ruby-json-schema
ruby-kaminari
ruby-pathname2
s3ql
s3ql-dbg
schooltool
service-wrapper
signon-plugin-ubuntuone
sipdialer
sitesummary
sitesummary-client
sooperlooper
ssh-askpass-gnome
ssh-krb5
sslsplit
steghide
steghide-doc
syncthing
syncthing-discosrv
syncthing-relaysrv
systemd-container
systemd-coredump
systemd-journal-remote
telepathy-resiprocate
ubuntu-app-launch-profiler
ubuntu-app-launch-tools
ubuntu-app-test
ubuntu-core-libs
ubuntu-core-libs-dev
ubuntu-ui-toolkit-autopilot
ubuntu-ui-toolkit-examples
ubuntu-ui-toolkit-tools
ubuntuone-credentials-autopilot
ubuntuone-credentials-common
urweb
urweb-doc
urweb-mode
vboot-kernel-utils
vboot-utils
vlc
vlc-bin
vlc-data
vlc-l10n
vlc-plugin-access-extra
vlc-plugin-base
vlc-plugin-fluidsynth
vlc-plugin-jack
vlc-plugin-notify
vlc-plugin-qt
vlc-plugin-samba
vlc-plugin-sdl
vlc-plugin-skins2
vlc-plugin-svg
vlc-plugin-video-output
vlc-plugin-video-splitter
vlc-plugin-visualization
vlc-plugin-zvbi
why
wireguard-dkms
wireguard-tools
yara
yara-doc
yaz
yaz-doc
yaz-icu
yaz-illclient
yorick-gyoto
gstreamer1.0-hybris
lib64go9
lib64go9-dbg
strace64


```
I guess i've just been lucky so far....but this is testing at it's funnist...:) Breakage...Yee haw.

---

### Post by ventrical on 2017-04-24
> **1fallen said:**
> Well for goodness sake??? I've been running with proposed since day one here and no bad or show stoppers as of yet.
Here is everything that has come from the Proposed repos:
```
$ awk '$1 == "Package:" { if (a[$2]++ == 0) print $2; }' /var/lib/apt/lists/*proposed*Packages
acl
advancecomp
bind9
bind9-doc
bind9-host
bind9utils
ceph
ceph-base
ceph-common
ceph-mon
ceph-osd
conntrack
cpp-6
cpp-6-doc
crmsh
crmsh-doc
cron
dctrl-tools
dnsutils
firefox
firefox-dbg
firefox-dev
firefox-locale-af
firefox-locale-an
firefox-locale-ar
firefox-locale-as
firefox-locale-ast
firefox-locale-az
firefox-locale-be
firefox-locale-bg
firefox-locale-bn
firefox-locale-br
firefox-locale-bs
firefox-locale-ca
firefox-locale-cak
firefox-locale-cs
firefox-locale-csb
firefox-locale-cy
firefox-locale-da
firefox-locale-de
firefox-locale-el
firefox-locale-en
firefox-locale-eo
firefox-locale-es
firefox-locale-et
firefox-locale-eu
firefox-locale-fa
firefox-locale-fi
firefox-locale-fr
firefox-locale-fy
firefox-locale-ga
firefox-locale-gd
firefox-locale-gl
firefox-locale-gn
firefox-locale-gu
firefox-locale-he
firefox-locale-hi
firefox-locale-hr
firefox-locale-hsb
firefox-locale-hu
firefox-locale-hy
firefox-locale-id
firefox-locale-is
firefox-locale-it
firefox-locale-ja
firefox-locale-ka
firefox-locale-kab
firefox-locale-kk
firefox-locale-km
firefox-locale-kn
firefox-locale-ko
firefox-locale-ku
firefox-locale-lg
firefox-locale-lt
firefox-locale-lv
firefox-locale-mai
firefox-locale-mk
firefox-locale-ml
firefox-locale-mn
firefox-locale-mr
firefox-locale-ms
firefox-locale-nb
firefox-locale-nl
firefox-locale-nn
firefox-locale-nso
firefox-locale-oc
firefox-locale-or
firefox-locale-pa
firefox-locale-pl
firefox-locale-pt
firefox-locale-ro
firefox-locale-ru
firefox-locale-si
firefox-locale-sk
firefox-locale-sl
firefox-locale-sq
firefox-locale-sr
firefox-locale-sv
firefox-locale-sw
firefox-locale-ta
firefox-locale-te
firefox-locale-th
firefox-locale-tr
firefox-locale-uk
firefox-locale-ur
firefox-locale-uz
firefox-locale-vi
firefox-locale-xh
firefox-locale-zh-hans
firefox-locale-zh-hant
firefox-locale-zu
g++-6
g++-6-multilib
gcc-6
gcc-6-base
gcc-6-doc
gcc-6-multilib
gcc-6-plugin-dev
gccgo-6-doc
gcj-6-jre-lib
gfortran-6
gfortran-6-doc
gfortran-6-multilib
gir1.2-ubuntu-app-launch-3
gnome-calendar
kpartx
kpartx-boot
krb5-doc
krb5-locales
krb5-multidev
lib32asan3
lib32asan3-dbg
lib32atomic1
lib32atomic1-dbg
lib32cilkrts5
lib32cilkrts5-dbg
lib32gcc-6-dev
lib32gcc1
lib32gcc1-dbg
lib32gfortran-6-dev
lib32gfortran3
lib32gfortran3-dbg
lib32gomp1
lib32gomp1-dbg
lib32gphobos-6-dev
lib32gphobos68
lib32gphobos68-dbg
lib32itm1
lib32itm1-dbg
lib32lsan0
lib32lsan0-dbg
lib32mpx2
lib32mpx2-dbg
lib32objc-6-dev
lib32objc4
lib32objc4-dbg
lib32quadmath0
lib32quadmath0-dbg
lib32stdc++-6-dev
lib32stdc++6
lib32stdc++6-6-dbg
lib32ubsan0
lib32ubsan0-dbg
libacl1
libacl1-dev
libasan3
libasan3-dbg
libasm-dev
libasm1
libatomic1
libatomic1-dbg
libbind-dev
libbind-export-dev
libbind9-140
libcc1-0
libcephfs-dev
libcephfs1
libcilkrts5
libcilkrts5-dbg
libdns-export162
libdns162
libdw-dev
libdw1
libelf-dev
libelf1
libgcc-6-dev
libgcc1
libgcc1-dbg
libgccjit-6-dev
libgccjit-6-doc
libgccjit0
libgccjit0-dbg
libgcj-doc
libgcj17
libgcj17-awt
libgcj17-dbg
libgcj17-dev
libgfortran-6-dev
libgfortran3
libgfortran3-dbg
libgomp1
libgomp1-dbg
libgphobos-6-dev
libgphobos68
libgphobos68-dbg
libgssapi-krb5-2
libgssrpc4
libirs-export141
libirs141
libisc-export160
libisc160
libisccc-export140
libisccc140
libisccfg-export140
libisccfg140
libitm1
libitm1-dbg
libk5crypto3
libkadm5clnt-mit11
libkadm5srv-mit11
libkdb5-8
libkrad-dev
libkrad0
libkrb5-3
libkrb5-dbg
libkrb5-dev
libkrb5support0
liblsan0
liblsan0-dbg
liblwres141
libmetacity-dev
libmetacity1
libmpx2
libmpx2-dbg
libnss-myhostname
libnss-resolve
libobjc-6-dev
libobjc4
libobjc4-dbg
libpam-cracklib
libpam-doc
libpam-modules
libpam-modules-bin
libpam-runtime
libpam-systemd
libpam0g
libpam0g-dev
libpci-dev
libpci3
libquadmath0
libquadmath0-dbg
librados-dev
librados2
libradosstriper-dev
libradosstriper1
librbd-dev
librbd1
librgw-dev
librgw2
libstdc++-6-dev
libstdc++-6-doc
libstdc++6
libstdc++6-6-dbg
libsystemd-dev
libsystemd0
libtsan0
libtsan0-dbg
libubsan0
libubsan0-dbg
libubuntu-app-launch3-dev
libubuntu-app-launch4
libubuntugestures5
libubuntugestures5-dev
libubuntugestures5-private-dev
libubuntumetrics5
libubuntumetrics5-dev
libubuntumetrics5-private-dev
libubuntutoolkit5
libubuntutoolkit5-dev
libubuntutoolkit5-private-dev
libudev-dev
libudev1
libx32asan3
libx32asan3-dbg
libx32atomic1
libx32atomic1-dbg
libx32cilkrts5
libx32cilkrts5-dbg
libx32gcc-6-dev
libx32gcc1
libx32gcc1-dbg
libx32gfortran-6-dev
libx32gfortran3
libx32gfortran3-dbg
libx32gomp1
libx32gomp1-dbg
libx32gphobos-6-dev
libx32gphobos68
libx32gphobos68-dbg
libx32itm1
libx32itm1-dbg
libx32lsan0
libx32lsan0-dbg
libx32objc-6-dev
libx32objc4
libx32objc4-dbg
libx32quadmath0
libx32quadmath0-dbg
libx32stdc++-6-dev
libx32stdc++6
libx32stdc++6-6-dbg
libx32ubsan0
libx32ubsan0-dbg
metacity
metacity-common
multipath-tools
multipath-tools-boot
open-vm-tools
open-vm-tools-dev
openssh-client
openssh-server
openssh-sftp-server
pciutils
pkg-config
python-aodhclient
python-aodhclient-doc
python-automaton
python-automaton-doc
python-castellan
python-castellan-doc
python-ceph
python-cephfs
python-cinderclient
python-cliff
python-cliff-doc
python-debtcollector
python-debtcollector-doc
python-futurist
python-futurist-doc
python-heatclient
python-keystoneauth1
python-keystoneauth1-doc
python-keystonemiddleware
python-keystonemiddleware-doc
python-openstackclient
python-openstackclient-doc
python-os-win
python-os-win-doc
python-osc-lib
python-osc-lib-doc
python-oslo-serialization-doc
python-oslo-vmware-doc
python-oslo.cache
python-oslo.cache-doc
python-oslo.concurrency
python-oslo.concurrency-doc
python-oslo.config
python-oslo.config-doc
python-oslo.context
python-oslo.context-doc
python-oslo.db
python-oslo.db-doc
python-oslo.i18n
python-oslo.i18n-doc
python-oslo.log
python-oslo.log-doc
python-oslo.middleware
python-oslo.middleware-doc
python-oslo.policy
python-oslo.policy-doc
python-oslo.privsep
python-oslo.privsep-doc
python-oslo.reports
python-oslo.reports-doc
python-oslo.rootwrap
python-oslo.serialization
python-oslo.serialization-doc
python-oslo.service
python-oslo.service-doc
python-oslo.utils
python-oslo.utils-doc
python-oslo.vmware
python-oslo.vmware-doc
python-pbr
python-pbr-doc
python-rados
python-rbd
python-requests
python-stevedore
python-stevedore-doc
python-urllib3
python-webob
python-webob-doc
python3-cliff
python3-pbr
python3-requests
python3-stevedore
python3-urllib3
python3-webob
qml-module-ubuntu-components
qml-module-ubuntu-components-labs
qml-module-ubuntu-layouts
qml-module-ubuntu-performancemetrics
qml-module-ubuntu-test
qtdeclarative5-ubuntu-ui-toolkit-plugin
radosgw
ssh
strace
systemd
systemd-sysv
systemd-tests
ubuntu-app-launch
ubuntu-ui-toolkit-doc
ubuntu-ui-toolkit-theme
udev
unattended-upgrades
lib64asan3
lib64asan3-dbg
lib64atomic1
lib64atomic1-dbg
lib64cilkrts5
lib64cilkrts5-dbg
lib64gcc-6-dev
lib64gcc1
lib64gcc1-dbg
lib64gfortran-6-dev
lib64gfortran3
lib64gfortran3-dbg
lib64gomp1
lib64gomp1-dbg
lib64gphobos-6-dev
lib64gphobos68
lib64gphobos68-dbg
lib64itm1
lib64itm1-dbg
lib64mpx2
lib64mpx2-dbg
lib64objc-6-dev
lib64objc4
lib64objc4-dbg
lib64quadmath0
lib64quadmath0-dbg
lib64stdc++-6-dev
lib64stdc++6
lib64stdc++6-6-dbg
lib64ubsan0
lib64ubsan0-dbg
imgtex
libmyth-0.28-0
libmyth-dev
libmyth-python
libmythtv-perl
mytharchive
mythbrowser
mythgallery
mythgame
mythmusic
mythnetvision
mythnews
mythplugins
mythtv
mythtv-backend
mythtv-backend-master
mythtv-common
mythtv-database
mythtv-dbg
mythtv-doc
mythtv-frontend
mythtv-theme-mythbuntu
mythtv-transcode-utils
mythweather
mythweb
mythzoneminder
nvidia-persistenced
php-mythtv
account-plugin-ubuntuone
acl2
acl2-books
acl2-books-certs
acl2-books-source
acl2-doc
acl2-emacs
acl2-infix
acl2-infix-source
acl2-source
aegisub
aegisub-dbg
aegisub-l10n
asdftool
autopilot-desktop
autopilot-touch
bareos
bareos-bat
bareos-bconsole
bareos-client
bareos-common
bareos-database-common
bareos-database-mysql
bareos-database-postgresql
bareos-database-sqlite3
bareos-database-tools
bareos-dbg
bareos-devel
bareos-director
bareos-director-python-plugin
bareos-filedaemon
bareos-filedaemon-ceph-plugin
bareos-filedaemon-glusterfs-plugin
bareos-filedaemon-ldap-python-plugin
bareos-filedaemon-python-plugin
bareos-storage
bareos-storage-ceph
bareos-storage-fifo
bareos-storage-glusterfs
bareos-storage-python-plugin
bareos-storage-tape
bareos-tools
bareos-traymonitor
bcron
bcron-run
bino
breathe-doc
cacti
cadvisor
ceph-fs-common
ceph-fuse
ceph-mds
ceph-resource-agents
ceph-test
cgpt
cgroup-lite
cl-pgloader
clang-3.8
clang-3.8-doc
clang-3.8-examples
clang-5.0
clang-5.0-doc
clang-5.0-examples
clang-format-3.8
clang-format-5.0
clang-tidy-3.8
clang-tidy-5.0
clisp
clisp-dev
clisp-doc
clisp-module-berkeley-db
clisp-module-bindings-glibc
clisp-module-clx
clisp-module-dbus
clisp-module-gdbm
clisp-module-pcre
clisp-module-postgresql
clisp-module-rawsock
clisp-module-wildcard
clisp-module-zlib
clsync
conntrackd
crack
crack-common
crack-md5
ddcci-dkms
discount
elasticsearch-curator
elfutils
ffmpeg
ffmpeg-doc
firefox-globalmenu
firefox-mozsymbols
firefox-testsuite
fiu-utils
fixincludes
frama-c
frama-c-base
freedombox-setup
freedroidrpg
freedroidrpg-data
fsprotect
gcc-6-hppa64-linux-gnu
gcc-6-locales
gcc-6-source
gcc-6-test-results
gccgo-6
gccgo-6-multilib
gcj-6
gcj-6-jdk
gcj-6-jre
gcj-6-jre-headless
gcj-6-source
gdc-6
gdc-6-multilib
gir1.2-gst-plugins-bad-1.0
gir1.2-ostree-1.0
gist
gnat-6
gnat-6-doc
gnat-6-sjlj
gobjc++-6
gobjc++-6-multilib
gobjc-6
gobjc-6-multilib
golang-docker-credential-helpers
golang-github-docker-docker-credential-helpers-dev
golang-github-google-cadvisor-dev
golang-github-syncthing-syncthing-dev
gpaw
gstreamer1.0-plugins-bad
gstreamer1.0-plugins-bad-dbg
gstreamer1.0-plugins-bad-doc
gstreamer1.0-plugins-bad-faad
gstreamer1.0-plugins-bad-videoparsers
gyoto
gyoto-bin
gyoto-dbg
gyoto-doc
handbrake
handbrake-cli
host
ike-scan
krb5-admin-server
krb5-gss-samples
krb5-k5tls
krb5-kdc
krb5-kdc-ldap
krb5-kpropd
krb5-otp
krb5-pkinit
krb5-user
lava
lava-dev
lava-dispatcher
lava-server
lava-server-doc
lib32go9
lib32go9-dbg
libalog-doc
libalog0.5.2
libalog2-dev
libapache2-mod-gnutls
libapache2-mod-php7.1
libass-dev
libass9
libav-tools
libavcodec-dev
libavcodec-extra
libavcodec-extra57
libavcodec57
libavdevice-dev
libavdevice57
libavfilter-dev
libavfilter-extra
libavfilter-extra6
libavfilter6
libavformat-dev
libavformat57
libavresample-dev
libavresample3
libavutil-dev
libavutil55
libbde-dbg
libbde-dev
libbde-utils
libbde1
libblitz-doc
libblitz0-dev
libblitz0v5
libcephfs-java
libcephfs-jni
libclang-3.8-dev
libclang-5.0-dev
libclang-common-3.8-dev
libclang-common-5.0-dev
libclang1-3.8
libclang1-3.8-dbg
libclang1-5.0
libclang1-5.0-dbg
libclsync-dev
libclsync0
libcore-extended-ocaml
libcore-extended-ocaml-dev
libcore-ocaml
libcore-ocaml-dev
libdist-zilla-perl
libextutils-parsexs-perl
libfiu-dev
libfiu0
libfuzzer-3.8-dev
libfuzzer-5.0-dev
libgnat-6
libgnat-6-dbg
libgnatprj6
libgnatprj6-dbg
libgnatprj6-dev
libgnatvsn6
libgnatvsn6-dbg
libgnatvsn6-dev
libgo9
libgo9-dbg
libgstreamer-plugins-bad1.0-0
libgstreamer-plugins-bad1.0-dev
libgyoto6
libgyoto6-dev
liblld-5.0
liblld-5.0-dbg
liblld-5.0-dev
liblldb-3.8
liblldb-3.8-dbg
liblldb-3.8-dev
liblldb-5.0
liblldb-5.0-dbg
liblldb-5.0-dev
libllvm-3.8-ocaml-dev
libllvm-5.0-ocaml-dev
libllvm3.8
libllvm3.8-dbg
libllvm5.0
libllvm5.0-dbg
libmarkdown2
libmarkdown2-dev
libmpv-dev
libmpv1
libncursesada-doc
libncursesada4
libncursesada4-dev
libnss-mymachines
libnss-systemd
libostree-1-1
libostree-dev
libostree-doc
libphonon-dev
libphonon4
libphonon4qt5-4
libphonon4qt5-dev
libphonon4qt5experimental-dev
libphonon4qt5experimental4
libphononexperimental-dev
libphononexperimental4
libphp7.1-embed
libpostproc-dev
libpostproc54
libre2-ocaml
libre2-ocaml-dev
librecon-1.11
librecon-1.11-dev
libresiprocate-1.11
libresiprocate-1.11-dev
libresiprocate-turn-client-1.11
libresiprocate-turn-client-1.11-dev
libretro-bsnes-mercury-accuracy
libretro-bsnes-mercury-balanced
libretro-bsnes-mercury-performance
libservice-wrapper-doc
libservice-wrapper-java
libservice-wrapper-jni
libstdc++-6-pic
libswresample-dev
libswresample2
libswscale-dev
libswscale4
libtest-most-perl
libtextutils-ocaml
libtextutils-ocaml-dev
libubuntuoneauth-2.0-0
libubuntuoneauth-2.0-dev
liburweb-cgi0
liburweb-fastcgi0
liburweb-http0
liburweb-static0
liburweb0
libv8-3.14-dbg
libv8-3.14-dev
libv8-3.14.5
libv8-dev
libvlc-bin
libvlc-dev
libvlc5
libvlccore-dev
libvlccore8
libwhy-coq
libx32go9
libx32go9-dbg
libyara-dev
libyara3
libyaz5
libyaz5-dev
liferea
liferea-data
live-config
live-config-doc
live-config-systemd
live-config-sysvinit
live-image-cinnamon-desktop
live-image-gnome-desktop
live-image-kde-desktop
live-image-lxde-desktop
live-image-mate-desktop
live-image-standard
live-image-xfce-desktop
live-images
live-task-base
live-task-cinnamon
live-task-extra
live-task-gnome
live-task-kde
live-task-localisation
live-task-localisation-desktop
live-task-lxde
live-task-mate
live-task-recommended
live-task-xfce
lld-5.0
lldb-3.8
lldb-3.8-dev
lldb-5.0
llvm-3.7-doc
llvm-3.7-examples
llvm-3.8
llvm-3.8-dev
llvm-3.8-doc
llvm-3.8-examples
llvm-3.8-runtime
llvm-3.8-tools
llvm-5.0
llvm-5.0-dev
llvm-5.0-doc
llvm-5.0-examples
llvm-5.0-runtime
llvm-5.0-tools
lwresd
mencoder
mercurial
mercurial-common
mongodb
mongodb-clients
mongodb-server
mplayer
mplayer-doc
mplayer-gui
mplayer2
mpv
nfct
node-resumer
nodejs
nodejs-dbg
nodejs-dev
nodejs-legacy
open-vm-tools-desktop
open-vm-tools-dkms
openssh-client-ssh1
osslsigncode
ostree
ostree-tests
pgloader
phonon
phonon-backend-null
phonon-backend-vlc
phonon4qt5
phonon4qt5-backend-null
phonon4qt5-backend-vlc
php7.1
php7.1-bcmath
php7.1-bz2
php7.1-cgi
php7.1-cli
php7.1-common
php7.1-curl
php7.1-dba
php7.1-dev
php7.1-enchant
php7.1-fpm
php7.1-gd
php7.1-gmp
php7.1-imap
php7.1-interbase
php7.1-intl
php7.1-json
php7.1-ldap
php7.1-mbstring
php7.1-mcrypt
php7.1-mysql
php7.1-odbc
php7.1-opcache
php7.1-pgsql
php7.1-phpdbg
php7.1-pspell
php7.1-readline
php7.1-recode
php7.1-snmp
php7.1-soap
php7.1-sqlite3
php7.1-sybase
php7.1-tidy
php7.1-xml
php7.1-xmlrpc
php7.1-xsl
php7.1-zip
profanity
python-asdf
python-asdf-doc
python-boto
python-breathe
python-clang-3.8
python-clang-5.0
python-cxx-dev
python-dmidecode
python-dmidecode-dbg
python-elasticsearch-curator
python-elasticsearch-curator-doc
python-fiu
python-guessit
python-gyoto
python-healpy
python-healpy-data
python-ironic-lib
python-libbde
python-lldb-3.8
python-lldb-5.0
python-oslo-serialization
python-oslo-vmware
python-oslotest
python-oslotest-doc
python-pywt
python-pywt-doc
python-schooltool
python-schooltool.cando
python-schooltool.gradebook
python-schooltool.intervention
python-schooltool.ldap
python-schooltool.lyceum.journal
python-toolz-doc
python-z3c.rml
python-zodb
python3-aodhclient
python3-asdf
python3-automaton
python3-autopilot
python3-autopilot-tests
python3-autopilot-trace
python3-autopilot-vis
python3-boto
python3-breathe
python3-castellan
python3-cinderclient
python3-cxx-dev
python3-debtcollector
python3-elasticsearch-curator
python3-fiu
python3-futurist
python3-guessit
python3-gyoto
python3-healpy
python3-heatclient
python3-ironic-lib
python3-keystoneauth1
python3-keystonemiddleware
python3-libbde
python3-openstackclient
python3-os-win
python3-osc-lib
python3-oslo-serialization
python3-oslo.cache
python3-oslo.concurrency
python3-oslo.config
python3-oslo.context
python3-oslo.db
python3-oslo.i18n
python3-oslo.log
python3-oslo.middleware
python3-oslo.policy
python3-oslo.privsep
python3-oslo.reports
python3-oslo.rootwrap
python3-oslo.serialization
python3-oslo.service
python3-oslo.utils
python3-oslo.vmware
python3-oslotest
python3-pywt
python3-toolz
qml-module-ubuntu-metrics
qml-module-ubuntuone
qtdeclarative5-qtmir-plugin
qtmir-android
qtmir-desktop
qtmir-tests
rbd-fuse
rbd-mirror
rbd-nbd
redis-sentinel
redis-server
redis-tools
repro
resiprocate-turn-server
resiprocate-turn-server-psql
rpmlint
ruby-json-schema
ruby-kaminari
ruby-pathname2
s3ql
s3ql-dbg
schooltool
service-wrapper
signon-plugin-ubuntuone
sipdialer
sitesummary
sitesummary-client
sooperlooper
ssh-askpass-gnome
ssh-krb5
sslsplit
steghide
steghide-doc
syncthing
syncthing-discosrv
syncthing-relaysrv
systemd-container
systemd-coredump
systemd-journal-remote
telepathy-resiprocate
ubuntu-app-launch-profiler
ubuntu-app-launch-tools
ubuntu-app-test
ubuntu-core-libs
ubuntu-core-libs-dev
ubuntu-ui-toolkit-autopilot
ubuntu-ui-toolkit-examples
ubuntu-ui-toolkit-tools
ubuntuone-credentials-autopilot
ubuntuone-credentials-common
urweb
urweb-doc
urweb-mode
vboot-kernel-utils
vboot-utils
vlc
vlc-bin
vlc-data
vlc-l10n
vlc-plugin-access-extra
vlc-plugin-base
vlc-plugin-fluidsynth
vlc-plugin-jack
vlc-plugin-notify
vlc-plugin-qt
vlc-plugin-samba
vlc-plugin-sdl
vlc-plugin-skins2
vlc-plugin-svg
vlc-plugin-video-output
vlc-plugin-video-splitter
vlc-plugin-visualization
vlc-plugin-zvbi
why
wireguard-dkms
wireguard-tools
yara
yara-doc
yaz
yaz-doc
yaz-icu
yaz-illclient
yorick-gyoto
gstreamer1.0-hybris
lib64go9
lib64go9-dbg
strace64


```
I guess i've just been lucky so far....but this is testing at it's funnist...:) Breakage...Yee haw.


:)

```

ventrical@ventrical-System-Product-Name:~$ sudo update-grub
[sudo] password for ventrical: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-30-generic
Found initrd image: /boot/initrd.img-4.8.0-30-generic
Found linux image: /boot/vmlinuz-4.8.0-28-generic
Found initrd image: /boot/initrd.img-4.8.0-28-generic
Found linux image: /boot/vmlinuz-4.8.0-27-generic
Found initrd image: /boot/initrd.img-4.8.0-27-generic
Found linux image: /boot/vmlinuz-4.8.0-26-generic
Found initrd image: /boot/initrd.img-4.8.0-26-generic
Found linux image: /boot/vmlinuz-4.8.0-22-generic
Found initrd image: /boot/initrd.img-4.8.0-22-generic
Found linux image: /boot/vmlinuz-4.8.0-21-generic
Found initrd image: /boot/initrd.img-4.8.0-21-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu Artful Aardvark (development branch) (17.10) on /dev/sda6
done
ventrical@ventrical-System-Product-Name:~$ 

```

yep.. I really busted it :)

---

### Post by #&amp;thj^% on 2017-04-24
> **ventrical said:**
> :)

```

ventrical@ventrical-System-Product-Name:~$ sudo update-grub
[sudo] password for ventrical: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.8.0-39-generic
Found initrd image: /boot/initrd.img-4.8.0-39-generic
Found linux image: /boot/vmlinuz-4.8.0-30-generic
Found initrd image: /boot/initrd.img-4.8.0-30-generic
Found linux image: /boot/vmlinuz-4.8.0-28-generic
Found initrd image: /boot/initrd.img-4.8.0-28-generic
Found linux image: /boot/vmlinuz-4.8.0-27-generic
Found initrd image: /boot/initrd.img-4.8.0-27-generic
Found linux image: /boot/vmlinuz-4.8.0-26-generic
Found initrd image: /boot/initrd.img-4.8.0-26-generic
Found linux image: /boot/vmlinuz-4.8.0-22-generic
Found initrd image: /boot/initrd.img-4.8.0-22-generic
Found linux image: /boot/vmlinuz-4.8.0-21-generic
Found initrd image: /boot/initrd.img-4.8.0-21-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu Artful Aardvark (development branch) (17.10) on /dev/sda6
done
ventrical@ventrical-System-Product-Name:~$ 

```

yep.. I really busted it :)

Well just shooting from the hip here...but have you tried re-installing Grub to "/dev/sda6"
Using A Live Install medium.
Or even perhaps running "** fdisk -l**"
Still got my thinking cap on though :lolflag:
Yep I can hear those rusty gears just churning away....LOL

---

### Post by ventrical on 2017-04-24
> **1fallen said:**
> Well just shooting from the hip here...but have you tried re-installing Grub to "/dev/sda6"
Using A Live Install medium.
Or even perhaps running "** fdisk -l**"
Still got my thinking cap on though :lolflag:
Yep I can hear those rusty gears just churning away....LOL


I was just thinking the same thing. I'm so rusty I put the tin man to shame:)

---

### Post by ventrical on 2017-04-24
Not sure how that partition became extended.

```

ventrical@ventrical-System-Product-Name:~$ fdisk -l

Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 1.4 TiB, 1500301910016 bytes, 2930277168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0afaa35a

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048  491533991  491531944 234.4G 83 Linux
/dev/sda2        491534334 2930276351 2438742018   1.1T  5 Extended
/dev/sda5       2923988992 2930276351    6287360     3G 82 Linux swap / Solaris
/dev/sda6        491534336 2923988991 2432454656   1.1T 83 Linux

Partition 2 does not start on physical sector boundary.
Partition table entries are not in disk order.


ventrical@ventrical-System-Product-Name:~$ 

```

I'm thinking remove extended partition?

---

### Post by #&amp;thj^% on 2017-04-24
> **ventrical said:**
> Not sure how that partition became extended.

```

ventrical@ventrical-System-Product-Name:~$ fdisk -l

Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 1.4 TiB, 1500301910016 bytes, 2930277168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0afaa35a

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048  491533991  491531944 234.4G 83 Linux
/dev/sda2        491534334 2930276351 2438742018   1.1T  5 Extended
/dev/sda5       2923988992 2930276351    6287360     3G 82 Linux swap / Solaris
/dev/sda6        491534336 2923988991 2432454656   1.1T 83 Linux

Partition 2 does not start on physical sector boundary.
Partition table entries are not in disk order.


ventrical@ventrical-System-Product-Name:~$ 

```

I'm thinking remove extended partition?

 Did you say this was a EFI/UEFI machine/bios
And can you try with legacy enabled in the bios...before removing that partition.

---

### Post by ventrical on 2017-04-24
> **1fallen said:**
> Did you say this was a EFI/UEFI machine/bios
And can you try with legacy enabled in the bios...before removing that partition.

I am in legacy BIOS machine but I tried CD grub rescue in newer device. Grub rescue or super grub will not work in either machine on this hdd. I am currently in BIOS mode. It was installed in BIOS mode. This particular machine does not have UEFI. Grub said there was a fastboot warning so I disabled fastboot.

```

ventrical@ventrical-System-Product-Name:~$ inxi -Fxz
System:    Host: ventrical-System-Product-Name Kernel: 4.8.0-39-generic x86_64 (64 bit gcc: 6.2.0)
           Desktop: Unity 7.5.0 (Gtk 3.20.9-1ubuntu2) Distro: Ubuntu 16.10
Machine:   Mobo: ASUSTeK model: P5B-E v: Rev 1.xx
           BIOS: American Megatrends v: 1807 date: 04/15/2009
CPU:       Dual core Intel Core2 Duo E8400 (-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 11980
           clock speeds: max: 2995 MHz 1: 2995 MHz 2: 2995 MHz
Graphics:  Card: NVIDIA GF119 [GeForce GT 610] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.89hz
           GLX Renderer: Gallium 0.4 on NVD9
           GLX Version: 3.0 Mesa 12.0.3 Direct Rendering: Yes
Audio:     Card-1 Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 NVIDIA GF119 HDMI Audio Controller
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.8.0-39-generic
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet
           driver: atl1 v: 2.1.3 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1500.3GB (2.8% used)
           ID-1: /dev/sda model: WDC_WD15EURS size: 1500.3GB
Partition: ID-1: / size: 230G used: 18G (8%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 3.22GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 34.5C mobo: 36.0C gpu: 37.0
           Fan Speeds (in rpm): cpu: 4245 psu: 0 sys-1: 0 sys-2: 0
Info:      Processes: 225 Uptime: 29 min Memory: 992.9/3007.1MB
           Init: systemd runlevel: 5 Gcc sys: 6.2.0
           Client: Shell (bash 4.3.461) inxi: 2.3.1 
ventrical@ventrical-System-Product-Name:~$ 

```

 I have access to all logs on the affected machine.  I have backup any useful archives. ubuntuforums will not allow me to upload terminal.log because it says there is a missing security token. To me it's not a big deal. I am just curious if I can bring it back up.

regards..

edit:

Just for fun .. and since it is extra huge drive I am going to install ubuntu-gnome as an along-side from the 17.04 release and see if that will bring in that artful upgrade. If that don't work I'll remove partition or use gparted to try and repair.

oh .. harry is right, I should of listened:)

---

### Post by ventrical on 2017-04-24
I tried to do an install but it warned me there were errors on the partition. uh.. ya know .. I could of fixed it .. but I just deleted the extended partition and now cannot get arful back.... whoops .. I mean artful! :)

---

### Post by mc4man on 2017-04-24
Well 4 months+  heads-up on dns issues wasn't enough in 17.04, maybe 5+ will fare better in 17.10..

---

### Post by harry332 on 2017-04-25
Oh yes Jeremy,
here is the bug report:

[https://bugs.launchpad.net/bugs/1685900](https://bugs.launchpad.net/bugs/1685900)

---

### Post by harry332 on 2017-04-25
And please all you who experience the same bug, please add a "affects me too" to the bug report:

[https://bugs.launchpad.net/bugs/1685900](https://bugs.launchpad.net/bugs/1685900)
To test this, one easy way is here:

1) download the working version of systemd (232-21ubuntu3) packages into your home directory (empty one):
   [https://launchpad.net/ubuntu/+source/systemd/232-21ubuntu3](https://launchpad.net/ubuntu/+source/systemd/232-21ubuntu3)

2) do the upgrade to v. 233-5ubuntu1

3) reboot and test if you still have a working dns

4) if not, then open the terminator and go to the directory where the downloaded 232-21ubuntu3 packages are

5) then run:
   sudo dpkg -i *.deb

6) reboot and your network with working dns is back

---

### Post by ventrical on 2017-04-25
> **1fallen said:**
> Sorry to hear this but all is good here:
```
$ apt policy systemd
systemd:
  Installed: 233-5ubuntu1
  Candidate: 233-5ubuntu1
  Version table:
 *** 233-5ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu artful-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     232-21ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu artful/main amd64 Packages


```
AND:
```
$ systemd-resolve --status
Global
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

Link 2 (enp0s3)
      Current Scopes: DNS LLMNR/IPv4 LLMNR/IPv6
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: allow-downgrade
    DNSSEC supported: yes
         DNS Servers: 75.75.76.76
                      75.75.75.75




```

network card:
```
 inxi -N
Network:   Card: Intel 82540EM Gigabit Ethernet Controller driver: e1000


```

I was able to get the same as you .. so no problem here.

```

ventrical@ventrical-System-Product-Name:~$ apt policy systemd
systemd:
  Installed: 233-5ubuntu1
  Candidate: 233-5ubuntu1
  Version table:
 *** 233-5ubuntu1 500
        500 http://ca.archive.ubuntu.com/ubuntu artful-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     232-21ubuntu3 500
        500 http://ca.archive.ubuntu.com/ubuntu artful/main amd64 Packages
ventrical@ventrical-System-Product-Name:~$ systemd-resolve --status
Global
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

Link 2 (enp3s0)
      Current Scopes: DNS LLMNR/IPv4 LLMNR/IPv6
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: allow-downgrade
    DNSSEC supported: no
         DNS Servers: 192.168.2.1
          DNS Domain: gateway.2wire.net

```

```
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1

```

regards..

---

### Post by #&amp;thj^% on 2017-04-25
> **ventrical said:**
> I was able to get the same as you .. so no problem here.

```

ventrical@ventrical-System-Product-Name:~$ apt policy systemd
systemd:
  Installed: 233-5ubuntu1
  Candidate: 233-5ubuntu1
  Version table:
 *** 233-5ubuntu1 500
        500 http://ca.archive.ubuntu.com/ubuntu artful-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     232-21ubuntu3 500
        500 http://ca.archive.ubuntu.com/ubuntu artful/main amd64 Packages
ventrical@ventrical-System-Product-Name:~$ systemd-resolve --status
Global
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

Link 2 (enp3s0)
      Current Scopes: DNS LLMNR/IPv4 LLMNR/IPv6updates tod
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: allow-downgrade
    DNSSEC supported: no
         DNS Servers: 192.168.2.1
          DNS Domain: gateway.2wire.net

```

```
Network:   Card: Qualcomm Atheros Attansic L1 Gigabit Ethernet driver: atl1

```

regards..

Glad someone else is up also.:)
BTW I did not have any updates today that would have fixed this...but I'm guessing here this is a fresh install as of today for you then.

---

### Post by ventrical on 2017-04-25
> **1fallen said:**
> Glad someone else is up also.:)
BTW I did not have any updates today that would have fixed this...but I'm guessing here this is a fresh install as of today for you then.

Yes it is. I tried <nomodset> and busted a few more installs. Then I tried to install nvidia-current and more breakage. Ah.. I had a defective .iso so I used more current 17.04 and upgraded from there. very smooth. No more llvmpipe. The only thing I lost was the logs .. etc.. so i can't investigate as to why , while enabling proposed, it started to rip everything out during the upgrade?  Most likely my bad.

---

### Post by #&amp;thj^% on 2017-04-25
> **ventrical said:**
> Yes it is. I tried <nomodset> and busted a few more installs. Then I tried to install nvidia-current and more breakage. Ah.. I had a defective .iso so I used more current 17.04 and upgraded from there. very smooth. No more llvmpipe. The only thing I lost was the logs .. etc.. so i can't investigate as to why , while enabling proposed, it started to rip everything out during the upgrade?  Most likely my bad.

Thanks Vent....really do appreciate your efforts and time you give us here;)
Also thanks to harry 332 for posting his experience and fix for the systemd upgrade and downgrade.
Great little community....all aces.

---

### Post by ventrical on 2017-04-25
+1

and with jbicha and yourself  dropping in and contributing as much as you both do with your gnomesque insights and expertise, we will all have an influence on hammering, molding, forming and purifying the next new shiney thing ! :) just like we did with precise, trusty and xenial!

---

### Post by harry332 on 2017-04-25
OK,

So I got this solved by installing the package bind9.
I tested several times, but dnsutils with bind9-host was not enough.
So I removed those and installed bind9 instead.
Now I have a working dns.

---

### Post by ventrical on 2017-04-25
here is what I get of a fresh install/upgrade

```

ventrical@ventrical-System-Product-Name:~$ apt policy bind9
bind9:
  Installed: (none)
  Candidate: 1:9.10.3.dfsg.P4-10.1ubuntu6
  Version table:
     1:9.10.3.dfsg.P4-10.1ubuntu6 500
        500 http://ca.archive.ubuntu.com/ubuntu artful/main amd64 Packages
ventrical@ventrical-System-Product-Name:~$ 

```

```

ventrical@ventrical-System-Product-Name:~$ apt policy bind9-host
bind9-host:
  Installed: 1:9.10.3.dfsg.P4-10.1ubuntu6
  Candidate: 1:9.10.3.dfsg.P4-10.1ubuntu6
  Version table:
 *** 1:9.10.3.dfsg.P4-10.1ubuntu6 500
        500 http://ca.archive.ubuntu.com/ubuntu artful/main amd64 Packages
        100 /var/lib/dpkg/status
ventrical@ventrical-System-Product-Name:~$ 

```


network working fine.

---

### Post by harry332 on 2017-04-26
Ventrical,

Fine, you have both bind9 and bind9-host installed, and most likely dnsutils too.

It was is that I do not have any package installed that depends on bind9.
The new systemd 233-5ubuntu1 should depend on it, though.

---

### Post by harry332 on 2017-04-26
Something still wrong here.
I should not need bind9 in order to have a working dns.
This is because systemd-resolved should do this job, and now it doesn't. Bind9 is doing it.

So I did a test.
I removed the whole bind9 stuff from my setup, rebooted, just to find out dns is not working.
I have a network OK, but no dns.
Also, command
"systemd-resolve --status"
tells me it is not working.

I do get it right by manually starting it:
"sudo service systemd-resolved restart".
And now I have network and dns, without bind9.

But then again, that is not it is meant to be.

---

### Post by ventrical on 2017-04-26
> **harry332 said:**
> Ventrical,

Fine, you have both bind9 and bind9-host installed, and most likely dnsutils too.

It was is that I do not have any package installed that depends on bind9.
The new systemd 233-5ubuntu1 should depend on it, though.

Harry .. please read again... bind9 is not installed.. just mentions  candidate.

```

ventrical@ventrical-System-Product-Name:~$ apt policy bind9
bind9:
  Installed: (none)
  Candidate: 1:9.10.3.dfsg.P4-10.1ubuntu6
  Version table:
     1:9.10.3.dfsg.P4-10.1ubuntu6 500
        500 http://ca.archive.ubuntu.com/ubuntu artful/main amd64 Packages
ventrical@ventrical-System-Product-Name:~$


```

are you using an RC kernel?

---

### Post by harry332 on 2017-04-26
Ah, yes my bad. Should read more carefully ...

I am using artful proposed kernel 4.10.0-20.22.
The same which is in zesty updates.

I am using a quite minimal setup and I have removed "unnecessary" packages along the way.
I do not even remember when I installed the distro, at least 2-3 years ago.
However, I must have uninstalled too many packages.
Systemd-resolved was OK until this newest 233-5ubuntu1 version.
Now I have to manually start resolved - or downgrade to 232-21ubuntu3.

---

### Post by ventrical on 2017-04-26
@harry,

Yes.. i am using the same kernel here.

Definitely something got removed that shouldn't have. 

or maybe .. try this :

go into network connections and create a new 'connection' . It has worked several times for me in the past, especially during the xenial RC wireless bug. (you had to go into network connections and manually create a wireless connection and edit in the wep or passcode. Might apply to ethernet also.

edit , like while checking new profile see if ivp4,ivp6 are set to AUTO DNS or old profile for that matter. just checking

---

### Post by rrnbtter on 2017-04-26
Greetings,
It's broken! The bug has been reported. They will fix it. As long as you can connect long enough to update you will get the fix when it releases.  This may be a case of canonical trying to fix something that should be a personal choice, auto spoofing mac id numbers.

---

### Post by harry332 on 2017-04-30
Just to be clear and let those interested know,
my setup is working fine now with the latest systemd (in proposed now) 233-5ubuntu1.

I installed and reinstalled several packages related to systemd and the commnad
"systemd-resolve --status"
is OK now.

So this is really solved now.

---

