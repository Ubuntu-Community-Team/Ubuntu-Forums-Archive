---
title: "The never ending multiarch troubles"
date: 2012-02-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Sworddragon on 2012-02-17
Maybe some of you do know the ia32-libs problem that the dependencies of it will end in i386-packages. But a lot of them are not ready now and the problem already exists a few months. Will it really be fixed if Ubuntu 12.04 os out? What if this problem is not fixed in 2 months?

But today there is a new problem. The package wine1.4 is in the repositories and it will depend on 64 bit systems on wine1.4-i386:i386. I can't install this package because it leads again in dependency problems. Has somebody else such troubles with multiarch too?

Interestingly if I enable multiarch Ubuntu tries to install 224 new packages on my system but no of them is a needed dependency of any of my installed packages. This is really mysterious.

---

### Post by clivejo on 2012-02-18
Do you think this is the problem why I cant install 32bit packages on PP, even when they have worked on previous Ubuntu installs?

I've been trying to set-up a 32bit CHROOT environment, but this wont work for me either :(

---

### Post by Sworddragon on 2012-02-18
> **clivejo said:**
> Do you think this is the problem why I cant install 32bit packages on PP, even when they have worked on previous Ubuntu installs?

ia32-libs from Oneric works on my system but it seems for Precise to be reworked with the libraries.

wine1.4 from the official repository makes now new problems. A bug report is here: [https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/934854](https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/934854)

---

### Post by philinux on 2012-02-18
I presumed that on a 64 bit system and multiarch that ia32libs was no longer needed?

Multiarch is on by default too isn't it. 

Any way I'll try installing wine on my rig and see what gives.

[edit] My oh my. Woah :P
apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 1.4~rc4-0ubuntu1

```
apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support fonts-droid fonts-horai-umefont fonts-unfonts-core gcc-4.6-base:i386 gnome-exe-thumbnailer icoutils imagemagick
  imagemagick-common libasn1-8-heimdal:i386 libasound2:i386 libc6:i386 libcdt4 libcomerr2:i386 libdb5.1:i386 libdrm-intel1:i386
  libdrm-nouveau1a:i386 libdrm-radeon1:i386 libdrm2:i386 libencode-locale-perl libexif12:i386 libexpat1:i386 libffi6:i386
  libfile-listing-perl libfont-afm-perl libfontconfig1:i386 libfreetype6:i386 libgcc1:i386 libgcrypt11:i386 libgd2-xpm:i386
  libgettextpo0 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386
  libgnutls26:i386 libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386 libgraph4 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgvc5 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhx509-5-heimdal:i386
  libice6:i386 libio-socket-inet6-perl libio-socket-ssl-perl libjpeg-turbo8:i386 libjpeg8:i386 libkrb5-26-heimdal:i386
  liblcms1:i386 libldap-2.4-2:i386 libllvm3.0:i386 liblqr-1-0 libltdl7:i386 liblwp-mediatypes-perl liblwp-protocol-https-perl
  libmagickcore4 libmagickcore4-extra libmagickwand4 libmailtools-perl libmpg123-0 libmpg123-0:i386 libnet-http-perl
  libnet-ssleay-perl libnetpbm10 libopenal1:i386 liborc-0.4-0:i386 libp11-kit0:i386 libpam-winbind libpathplan4
  libpciaccess0:i386 libpcre3:i386 libpng12-0:i386 libroken18-heimdal:i386 libsasl2-2:i386 libsasl2-modules:i386
  libselinux1:i386 libsm6:i386 libsocket6-perl libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-3:i386 libunistring0
  liburi-perl libusb-0.1-4:i386 libuuid1:i386 libwind0-heimdal:i386 libwww-perl libwww-robotrules-perl libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-glx0:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386
  libxml2:i386 libxpm4:i386 libxxf86vm1:i386 netpbm p7zip ttf-droid ttf-umefont ttf-unfonts-core winbind wine-gecko1.4
  wine-gecko1.4:i386 wine1.4 wine1.4-amd64 wine1.4-i386:i386 winetricks zlib1g:i386
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl imagemagick-doc autotrace curl enscript ffmpeg gnuplot grads hp2xx
  html2ps libwmf-bin mplayer povray radiance texlive-base-bin transfig ufraw-batch libasound2-plugins:i386
  libasound2-python:i386 glibc-doc:i386 locales:i386 rng-tools:i386 libgd-tools:i386 libglide3:i386 gnutls-bin:i386 gphoto2:i386
  gtkam:i386 libvisual-0.4-plugins:i386 gstreamer-codec-install:i386 gnome-codec-install:i386 gstreamer0.10-tools:i386
  gstreamer0.10-plugins-base:i386 libdata-dump-perl liblcms-utils:i386 libcrypt-ssleay-perl libsasl2-modules-otp:i386
  libsasl2-modules-ldap:i386 libsasl2-modules-sql:i386 libsasl2-modules-gssapi-mit:i386 libsasl2-modules-gssapi-heimdal:i386
  libauthen-ntlm-perl p7zip-full
Recommended packages:
  xml-core:i386 wine1.4:any wine1.4:any:i386 wine1.4-i386
The following NEW packages will be installed
  binfmt-support fonts-droid fonts-horai-umefont fonts-unfonts-core gcc-4.6-base:i386 gnome-exe-thumbnailer icoutils imagemagick
  imagemagick-common libasn1-8-heimdal:i386 libasound2:i386 libc6:i386 libcdt4 libcomerr2:i386 libdb5.1:i386 libdrm-intel1:i386
  libdrm-nouveau1a:i386 libdrm-radeon1:i386 libdrm2:i386 libencode-locale-perl libexif12:i386 libexpat1:i386 libffi6:i386
  libfile-listing-perl libfont-afm-perl libfontconfig1:i386 libfreetype6:i386 libgcc1:i386 libgcrypt11:i386 libgd2-xpm:i386
  libgettextpo0 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386
  libgnutls26:i386 libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386 libgraph4 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgvc5 libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386
  libheimntlm0-heimdal:i386 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhx509-5-heimdal:i386
  libice6:i386 libio-socket-inet6-perl libio-socket-ssl-perl libjpeg-turbo8:i386 libjpeg8:i386 libkrb5-26-heimdal:i386
  liblcms1:i386 libldap-2.4-2:i386 libllvm3.0:i386 liblqr-1-0 libltdl7:i386 liblwp-mediatypes-perl liblwp-protocol-https-perl
  libmagickcore4 libmagickcore4-extra libmagickwand4 libmailtools-perl libmpg123-0 libmpg123-0:i386 libnet-http-perl
  libnet-ssleay-perl libnetpbm10 libopenal1:i386 liborc-0.4-0:i386 libp11-kit0:i386 libpam-winbind libpathplan4
  libpciaccess0:i386 libpcre3:i386 libpng12-0:i386 libroken18-heimdal:i386 libsasl2-2:i386 libsasl2-modules:i386
  libselinux1:i386 libsm6:i386 libsocket6-perl libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-3:i386 libunistring0
  liburi-perl libusb-0.1-4:i386 libuuid1:i386 libwind0-heimdal:i386 libwww-perl libwww-robotrules-perl libx11-6:i386
  libx11-xcb1:i386 libxau6:i386 libxcb-glx0:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386
  libxml2:i386 libxpm4:i386 libxxf86vm1:i386 netpbm p7zip ttf-droid ttf-umefont ttf-unfonts-core winbind wine wine-gecko1.4
  wine-gecko1.4:i386 wine1.4 wine1.4-amd64 wine1.4-i386:i386 winetricks zlib1g:i386
0 upgraded, 132 newly installed, 0 to remove and 0 not upgraded.
Need to get **182 MB **of archives.
After this operation, **[COLOR="Red"]494 MB of additional disk space will be used.[/COLOR]**
```

Continue = No on this machine.

---

### Post by Ibidem on 2012-02-18
Multiarch support is a metapackage; have you let it install the packages?  They seem to be dependencies of the multiarch packages.
(I can't tell whether you went ahead or aborted install)

Try installing the packages listed as breaking wine install manually; does that work?

---

### Post by philinux on 2012-02-18
> **Ibidem said:**
> Multiarch support is a metapackage; have you let it install the packages?  They seem to be dependencies of the multiarch packages.
(I can't tell whether you went ahead or aborted install)

Try installing the packages listed as breaking wine install manually; does that work?

I was only doing a test. At the end of my post is > Continue = No on this machine.

I've no need for wine in my testin pc.

---

