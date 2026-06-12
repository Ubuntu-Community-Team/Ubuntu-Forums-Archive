---
title: "imagemagick without bloat on ubuntu? No x11 etc?"
date: 2013-06-07
forum: Server Platforms
---

### Post by Lido on 2013-06-07
I'm running a basic LAMP setup with 12.04 LTS and want/need a way for some scripts to resize images. On Gentoo we had a relatively small imagemagick installation built without x11 and other stuff we didn't need. Gentoo makes it pretty simple to build from source (which is their whole deal I think), but I'm hesitant to try it on my own with Ubuntu. Does anyone have any tips, links or advice? I've searched a bit but the only resources I've found have been on imagemagick's site and are geared to people with more experience than me. Thanks.

Here's what I'm trying to avoid, btw:

```
$ sudo apt-get install imagemagick
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libgnutls-openssl27
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cmap-adobe-japan1 fontconfig ghostscript gs-cjk-resource gsfonts imagemagick-common libavahi-client3 libavahi-common-data libavahi-common3 libcairo2
  libcdt4 libcroco3 libcups2 libcupsimage2 libdatrie1 libdjvulibre-text libdjvulibre21 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgomp1 libgraph4
  libgs9 libgs9-common libgvc5 libijs-0.35 libilmbase6 libjasper1 libjbig2dec0 liblcms1 liblcms2-2 liblqr-1-0 libmagickcore4 libmagickcore4-extra
  libmagickwand4 libnetpbm10 libopenexr6 libpango1.0-0 libpaper-utils libpaper1 libpathplan4 libpixman-1-0 librsvg2-2 libthai-data libthai0 libtiff4
  libwmf0.2-7 libxcb-render0 libxcb-shm0 libxft2 libxrender1 netpbm
Suggested packages:
  ghostscript-cups ghostscript-x hpijs fonts-ipafont-mincho fonts-ipafont-gothic ttf-arphic-ukai ttf-arphic-uming fonts-unfonts-core imagemagick-doc
  autotrace cups-bsd lpr lprng enscript ffmpeg gimp gnuplot grads hp2xx html2ps libwmf-bin mplayer povray radiance sane-utils texlive-base-bin transfig
  xdg-utils ufraw-batch cups-common libjasper-runtime liblcms-utils liblcms2-utils ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp ttf-arphic-gkai00mp
  ttf-arphic-bkai00mp librsvg2-bin libwmf0.2-7-gtk
The following NEW packages will be installed:
  cmap-adobe-japan1 fontconfig ghostscript gs-cjk-resource gsfonts imagemagick imagemagick-common libavahi-client3 libavahi-common-data libavahi-common3
  libcairo2 libcdt4 libcroco3 libcups2 libcupsimage2 libdatrie1 libdjvulibre-text libdjvulibre21 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgomp1
  libgraph4 libgs9 libgs9-common libgvc5 libijs-0.35 libilmbase6 libjasper1 libjbig2dec0 liblcms1 liblcms2-2 liblqr-1-0 libmagickcore4
  libmagickcore4-extra libmagickwand4 libnetpbm10 libopenexr6 libpango1.0-0 libpaper-utils libpaper1 libpathplan4 libpixman-1-0 librsvg2-2 libthai-data
  libthai0 libtiff4 libwmf0.2-7 libxcb-render0 libxcb-shm0 libxft2 libxrender1 netpbm
0 upgraded, 52 newly installed, 0 to remove and 7 not upgraded.
Need to get 20.4 MB of archives.
After this operation, 56.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by CharlesA on 2013-06-07
You could try installing it like this:

```
sudo apt-get install --no-install-recommends imagemagick
```

---

### Post by CharlesA on 2013-06-07
You could try installing it like this:

```
sudo apt-get install --no-install-recommends imagemagick
```

---

### Post by Lido on 2013-06-07
Thanks, I'll set up a virtualbox and give that a try. Seems to have worked. Thanks!

---

