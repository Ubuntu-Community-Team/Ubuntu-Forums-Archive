---
title: "Netboot preseed minimal server VM install is not minimal"
date: 2012-05-08
forum: Server Platforms
---

### Post by MTBikerTim on 2012-05-08
Hey Everyone

I am having lots of fun with preseed files. But I have run into an issue that I can not work out a solution too. 

The issue is that if I do a minimal Ubuntu server VM install off the ubuntu-12.04-server-amd64.iso, I end up with a nice minimal Ubuntu server VM.

When I do a netboot install using the same preseed file choosing the same options as the iso install, I end up with a very different set of packages.

So my question is what do I need to do to make the netboot install the same or at least similar to iso install? I am using Virtual Box and I have a feeling the extra packages are dependencies of the vbox-additions. Is there a way to stop vbox-additions from being installed?

For example below is a package count and a diff of the two package lists with u1204t1 being the netboot install:
```
$ wc -l *.pkg
  380 u1204t1.pkg
  229 u1204t2.pkg
``````
$ diff u1204t1.pkg u1204t2.pkg
1d0
< accountsservice                    install
3d1
< apparmor                    install
5d2
< apt-transport-https                install
9d5
< at                        install
13,16d8
< bash-completion                    install
< bind9-host                    install
< binutils                    install
< bsdmainutils                    install
19d10
< busybox-static                    install
22,23d12
< command-not-found                install
< command-not-found-data                install
27,28d15
< cpp                        install
< cpp-4.6                        install
32d18
< dbus                        install
37,39d22
< discover                    install
< discover-data                    install
< dkms                        install
42,43d24
< dnsutils                    install
< dosfstools                    install
47d27
< ed                        install
49d28
< fakeroot                    install
52,56d30
< friendly-recovery                install
< ftp                        install
< fuse                        install
< gcc                        install
< gcc-4.6                        install
58d31
< geoip-database                    install
60d32
< gir1.2-glib-2.0                    install
64d35
< groff-base                    install
71d41
< hdparm                        install
74d43
< info                        install
79d47
< install-info                    install
82d49
< iptables                    install
84,85d50
< iputils-tracepath                install
< irqbalance                    install
95,97d59
< language-pack-gnome-en                install
< language-pack-gnome-en-base            install
< language-selector-common            install
100d61
< libaccountsservice0                install
104d64
< libasn1-8-heimdal                install
106d65
< libbind9-80                    install
112d70
< libc-dev-bin                    install
114,115d71
< libc6-dev                    install
< libcap-ng0                    install
119d74
< libcurl3-gnutls                    install
123d77
< libdbus-glib-1-2                install
125,126d78
< libdiscover2                    install
< libdns81                    install
136d87
< libfontenc1                    install
141d91
< libgcrypt11                    install
143,145d92
< libgeoip1                    install
< libgirepository-1.0-1                install
< libgl1-mesa-dri                    install
147,150d93
< libgmp10                    install
< libgnutls26                    install
< libgomp1                    install
< libgpg-error0                    install
152,157d94
< libgssapi3-heimdal                install
< libhcrypto4-heimdal                install
< libheimbase1-heimdal                install
< libheimntlm0-heimdal                install
< libhx509-5-heimdal                install
< libice6                        install
160,162d96
< libisc83                    install
< libisccc80                    install
< libisccfg82                    install
166d99
< libkrb5-26-heimdal                install
169,170d101
< libldap-2.4-2                    install
< libllvm3.0                    install
174d104
< liblwres80                    install
178,179d107
< libmpc2                        install
< libmpfr4                    install
183d110
< libnfnetlink0                    install
188d114
< libp11-kit0                    install
194,195d119
< libparted0debian1                install
< libpcap0.8                    install
199,200d122
< libpipeline1                    install
< libpixman-1-0                    install
203d124
< libpolkit-gobject-1-0                install
205d125
< libquadmath0                    install
207,210d126
< libroken18-heimdal                install
< librtmp0                    install
< libsasl2-2                    install
< libsasl2-modules                install
214d129
< libsm6                        install
221d135
< libtasn1-3                    install
231d144
< libwind0-heimdal                install
237d149
< libxaw7                        install
239,240d150
< libxcomposite1                    install
< libxdamage1                    install
243,247d152
< libxfixes3                    install
< libxfont1                    install
< libxkbfile1                    install
< libxml2                        install
< libxmu6                        install
249,252d153
< libxpm4                        install
< libxrandr2                    install
< libxrender1                    install
< libxt6                        install
254,260c155,157
< linux-generic                    install
< linux-headers-3.2.0-24                install
< linux-headers-3.2.0-24-generic            install
< linux-headers-generic                install
< linux-image-3.2.0-24-generic            install
< linux-image-generic                install
< linux-libc-dev                    install
---
> linux-image-3.2.0-23-virtual            install
> linux-image-virtual                install
> linux-virtual                    install
267,270d163
< lshw                        install
< lsof                        install
< ltrace                        install
< make                        install
272,274d164
< man-db                        install
< manpages                    install
< manpages-dev                    install
276d165
< memtest86+                    install
278d166
< mlocate                        install
282d169
< mtr-tiny                    install
284d170
< nano                        install
290d175
< ntfs-3g                        install
296d180
< parted                        install
298d181
< patch                        install
304,309d186
< plymouth-theme-ubuntu-text            install
< popularity-contest                install
< powermgmt-base                    install
< ppp                        install
< pppconfig                    install
< pppoeconf                    install
311d187
< psmisc                        install
316,317d191
< python-dbus                    install
< python-dbus-dev                    install
319,321d192
< python-gdbm                    install
< python-gi                    install
< python-gnupginterface                install
328d198
< rsync                        install
332d201
< sgml-base                    install
334d202
< strace                        install
342,344d209
< tcpdump                        install
< telnet                        install
< time                        install
348d212
< ubuntu-standard                    install
351d214
< ufw                        install
353d215
< update-manager-core                install
358d219
< uuid-runtime                    install
361,364d221
< virtualbox-guest-dkms                install
< virtualbox-guest-utils                install
< virtualbox-guest-x11                install
< virtualbox-ose-guest-x11            install
368,369d224
< x11-common                    install
< x11-xkb-utils                    install
371,373d225
< xfonts-base                    install
< xfonts-encodings                install
< xfonts-utils                    install
375,377d226
< xml-core                    install
< xserver-common                    install
< xserver-xorg-core                install
```preseed.cfg from the cd used for both installs
```
# Always install the virtual kernel, with no headers.
d-i     base-installer/kernel/override-image    string linux-virtual
d-i     base-installer/kernel/headers   boolean false
# Don't even install the standard task.
tasksel tasksel/skip-tasks      string standard
# Only install basic language packs. Let tasksel ask about tasks.
d-i     pkgsel/language-pack-patterns   string
# No language support packages.
d-i     pkgsel/install-language-support boolean false
# Only ask the UTC question if there are other operating systems installed.
d-i     clock-setup/utc-auto    boolean true
# Verbose output and no boot splash screen.
d-i     debian-installer/quiet  boolean false
d-i     debian-installer/splash boolean false
# Install the debconf oem-config frontend (if in OEM mode).
d-i     oem-config-udeb/frontend        string debconf
# Wait for two seconds in grub
d-i     grub-installer/timeout  string 2
# Add the network and tasks oem-config steps by default.
oem-config      oem-config/steps        multiselect language, timezone, keyboard, user, network, tasks

```

---

### Post by MTBikerTim on 2012-05-17
I have come back to this issue and spent another day banging my head against a wall trying to work out a solution for this issue. I have done some grepping and diffing and made the following list of extra packages which are installed when I do a pxeboot network install compared the CD based install. This list doesn't show the automatically installed dependencies of these packages that are also installed.

```
> acpid
> apport
> apport-symptoms
> bc
> curl
> discover
> fonts-ubuntu-font-family-console
> landscape-common
> libcurl3
> libgc1c2
> libgmp10
> libgpm2
> libiw30
> libjs-jquery
> libpcsclite1
> libpython2.7
> patch
> python-apport
> python-crypto
> python-httplib2
> python-keyring
> python-launchpadlib
> python-lazr.restfulclient
> python-lazr.uri
> python-oauth
> python-openssl
> python-pam
> python-pkg-resources
> python-problem-report
> python-serial
> python-simplejson
> python-twisted-bin
> python-twisted-core
> python-wadllib
> python-zope.interface
> update-notifier-common
> vim
> vim-runtime
> virtualbox-ose-guest-x11
> w3m
> whoopsie
> wireless-tools
> wpasupplicant

```

I compiled this list so I could do an apt-get remove <above list> after the install but this is an ugly fix that I am not happy with. Is there not a better way to stop these packages being installed during the install process?

---

### Post by buckett on 2012-07-04
I'm also seeing this issue, did you get any further with resolving it?

---

