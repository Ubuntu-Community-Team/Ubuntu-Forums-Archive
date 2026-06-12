---
title: "Trying to get Gutsy to work"
date: 2007-10-27
forum: Repositories &amp; Backports
---

### Post by CheshireMac on 2007-10-27
Okay, so I'm trying to get my new installation of Gutsy to playback video of any kind, but for the time being, it seems unable to do so. I was given a tutorial on how to install the proper codecs and plugins, but it seems that this failed, although everything seemed to go through fine in terminal. Here's the commands I put in:
```
cd Desktop 
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2

sudo mkdir -v /usr/local/lib/codecs
sudo tar xjvf all-20071007.tar.bz2 -C /usr/local/lib/codecs

sudo apt-get install avifile-divx-plugin avifile-xvid-plugin gawk \
libxcursor-dev ladspa-sdk liba52-0.7.4 liba52-0.7.4-dev libaa1-dev libartsc0 \
libartsc0-dev libasound2-dev libatk1.0-dev libaudiofile-dev libavcodec1d libavcodec-dev \
libavformat1d libavformat-dev libavifile-0.7c2 libavifile-0.7-dev libavutil1d \
libavutil-dev libcaca-dev libcairo2-dev libcdparanoia0-dev libcucul-dev libdv4-dev \
libdirectfb-dev libdirectfb-extra libdbus-1-dev libdbus-glib-1-dev libdc1394-13 \
libdc1394-13-dev libdfb++-0.9-25 libdfb++-dev libdts-dev libdvdnav4 libdvdnav-dev \
libdvdread3 libdvdread-dev libebml0 libebml-dev libenca0 libenca-dev libesd0-dev \
libexpat1-dev libfaac0 libfaac-dev libfaad2-0 libfaad2-dev libfame-0.9 libfame-dev \
libflac++6 libflac-dev libflac++-dev libfontconfig1-dev libfontenc-dev libfreetype6-dev \
libfribidi-dev libgdk-pixbuf2 libgdk-pixbuf-dev libgii1 libgii1-dev libgii1-target-x \
libgl1-mesa-dev libglib1.2 libglib1.2-dev libglib2.0-dev libglu1-mesa-dev \
libglu1-xorg-dev libgsm1 libgsm1-dev libgtk1.2 libgtk1.2-common libgtk1.2-dev \
libgtk2.0-dev libice-dev libggi2 libggi2-dev libggimisc2 libggimisc2-dev libggiwmh0 \
libggiwmh0-dev libjpeg62-dev liblame0 liblame-dev liblivemedia-dev liblzo1 liblzo-dev \
liblzo2-2 liblzo2-dev libmad0 libmad0-dev libmatroska0 libmatroska-dev libmikmod2 \
libmikmod2-dev libmp4v2-0 libmp4v2-dev libmpcdec3 libmpcdec-dev libncurses5-dev \
libogg-dev libpango1.0-dev libpng12-dev libpopt-dev libpostproc1d libpostproc-dev \
libraw1394-dev libsdl1.2-dev libslang2-dev libsmbclient-dev libsm-dev libspeex-dev \
libsvga1 libsvga1-dev libsysfs-dev libtheora-dev libungif4-dev libungif4g \
libvorbis-dev libx11-dev libx264-54 libx264-dev libxau-dev libxcomposite-dev \
libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxfont-dev libxft-dev \
libxi-dev libxinerama-dev libxrandr-dev libxrender-dev libxsharp-dev libxv-dev \
libxvidcore4 libxvidcore4-dev libxvmc1 libxvmc-dev libxxf86dga-dev libxxf86vm-dev \
mesa-common-dev pnet-interpreter sharutils toolame ttf-bitstream-vera \
x11proto-composite-dev x11proto-core-dev x11proto-damage-dev \
x11proto-fixes-dev x11proto-fonts-dev x11proto-input-dev x11proto-kb-dev \
x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev \
xlibs-static-dev xtrans-dev zlib1g-dev    

cd $HOME/Desktop/mplayer
./configure \
--prefix=/usr/local \
--enable-largefiles \
--enable-gui \
--codecsdir=/usr/local/lib/codecs
make 
sudo make install

cd $HOME
mkdir -pv .mplayer/skins/default
ln -sv /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf ~/.mplayer/subfont.ttf

cd Desktop
wget http://www.mplayerhq.hu/MPlayer/skins/Blue-1.7.tar.bz2
tar xjvf Blue-1.7.tar.bz2 
cp -Rv $HOME/Desktop/Blue/* $HOME/.mplayer/skins/default
```

I'm at a loss, since I'm new to the Gutsy experience, and I've never had this much trouble trying to play a movie on any other previous version of Ubuntu. 
Any thoughts on what's going on?

---

### Post by zen2000 on 2007-10-27
Don't bother with terminal commands yet. Start easy. Go to //help.ubuntu.com/community/RestrictedFormats
and go down to multimedia support. just read and paste the sudo commands into your terminal. It is easy and works!

---

### Post by CheshireMac on 2007-10-27
Okay, so I walked myself through the whole thing, including a couple extras. Still nothing. I'm beginning to wonder if I'm able to support this distro. I went through the  medibuntu install process and got libdvd2 or whatever and I'm at a standstill.

---

### Post by andrew.46 on 2007-11-06
Hi,

 Saw your frustration:

> **CheshireMac said:**
> Okay, so I walked myself through the whole thing, including a couple extras. Still nothing. I'm beginning to wonder if I'm able to support this distro. I went through the  medibuntu install process and got libdvd2 or whatever and I'm at a standstill.

 That walkthrough (which I will admit that I wrote) is really not intended for somebody who simply wants access to a few media files and simple dvd playback. It is intended instead to provide a *cutting edge* version of Linux's premium media player / encoder. There is in fact a short statement to this effect at the beginning of the walkthrough.

 Can I suggest that you try simply installing the media player vlc from the ubuntu repositories:

```
sudo apt-get install vlc
```

and that way your linux experience might be a little more enjoyable. Come back to the svn mplayer at a later stage perhaps. Remember the old linux saying: "Have fun!".

              Andrew

---

