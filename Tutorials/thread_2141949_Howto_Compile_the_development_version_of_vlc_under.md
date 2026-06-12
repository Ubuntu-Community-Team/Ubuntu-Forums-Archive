---
title: "Howto: Compile the development version of vlc under the latest Ubuntu release"
date: 2013-05-04
forum: Tutorials
---

### Post by andrew.46 on 2013-05-04
This guide details how to install the development version of vlc using both 32 bit and 64 bit versions of the latest Ubuntu release, it owes a huge debt to [the vlc Slackbuild]("http://www.slackware.com/~alien/slackbuilds/vlc/build/vlc.SlackBuild") of Eric Hameleers, otherwise known as alienBOB. This guide will be periodically updated for each new *stable* Ubuntu version.

I emphasise at the outset that this *development* version of vlc will be broken at times and should only ever be installed by those willing to experiment a little, people who are used to running alpha or beta version software. The preferred method to build and test vlc-git is from within a Virtual Machine dedicated to this purpose alone, this is my own model in writing and testing this guide and I *strongly* recommend this method to all who follow the guide.

[SIZE=4]**[COLOR=#008000]Preparation: Trusty Tahr..[/COLOR]**[/SIZE]

As a first step it is a good idea to remove all previous vlc packages using either the Terminal, Synaptic or the Software Centre. Then some basic tools are required for compiling and we will also create the build location, the following is a single command which can simply be copied from here and pasted into a Terminal window: 

```

sudo apt-get -y install build-essential git-core checkinstall \
automake yasm cmake cmake-curses-gui && mkdir -pv $HOME/vlc_build

```

A considerable volume of 'development' files is also required, the following is a single command: 

```

sudo apt-get -y install liba52-0.7.4-dev libaa1-dev libasound2-dev libass-dev \
libavahi-client-dev libcaca-dev libcairo2-dev libcddb2-dev libcdio-dev libdca-dev \
libdirac-dev libdvbpsi-dev libdvdnav-dev libdvdread-dev libebml-dev libfaad-dev \
libflac-dev libfreetype6-dev libfribidi-dev libgcrypt11-dev libgl1-mesa-dev \
libglib2.0-0 libgnutls28-dev libid3tag0-dev libjack-jackd2-dev libkate-dev \
liblircclient-dev liblua5.1-0-dev libmad0-dev libmatroska-dev libmodplug-dev \
libmpcdec-dev libmpeg2-4-dev libmtp-dev libncursesw5-dev libnotify-dev libogg-dev \
liboggkate-dev libpango1.0-dev libpng12-dev libprojectm-dev libprojectm-qt-dev \
libproxy-dev libpulse-dev libqt4-dev libraw1394-dev librsvg2-dev libschroedinger-dev \
libsdl-image1.2-dev libsdl1.2-dev libshout3-dev libsmbclient-dev libspeex-dev \
libsqlite3-dev libsvga1-dev libsysfs-dev libtag1-dev libtar-dev libgme-dev \
libtheora-dev libtool libtwolame-dev libudev-dev libupnp-dev libv4l-dev libvcdinfo-dev \
libvorbis-dev libva-dev libvpx-dev libx11-dev libx11-xcb-dev libxcb-composite0-dev \
libxcb-keysyms1-dev libxcb-randr0-dev libxcb-shm0-dev libxcb-xv0-dev libxcb-xvmc0-dev \
libxcb1-dev libxext-dev libxml2-dev libxpm-dev libxt-dev libxv-dev libzvbi-dev \
lua5.1 qt4-qtconfig libspeexdsp-dev libsamplerate0-dev libvdpau-dev libxpm-dev \
libxinerama-dev libtar-dev libgtk2.0-dev libdc1394-22-dev libopus-dev

```

Feel free to experiment a little with these development files to match your needs but the ones given here will outfit you with a reasonably well equipped vlc. Now to add the libraries for fdk-aac which vlc will use (via FFmpeg) for aac encoding:

[COLOR=#008000][SIZE=2]**libfdk-aac...**[/SIZE][/COLOR]

libfdk-aac is in the Ubuntu Repositories but only version 1.2 and since 1.3 has some substantial fixes in place we will be compiling the newer version:

**Installing libfdk-aac:**

```

if [ "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="--with-pic"
 else
  ARCHOPTS=""
fi && \
cd $HOME/vlc_build && wget https://github.com/mstorsjo/fdk-aac/archive/v0.1.3.tar.gz && \
tar xvf v0.1.3.tar.gz && cd fdk-aac-0.1.3 && \
autoreconf -fiv && \
./configure --prefix=$HOME/vlc_build/vlcdeps/usr \
            $ARCHOPTS \
            --disable-shared \
            --enable-static && \
make && make install && make distclean

```

**Removing libfdk-aac:**

To remove all traces of libfdk-aac, including the installed libraries, the expanded source and the downloaded source archive use the following:

```

rm -rfv $HOME/vlc_build/vlcdeps/usr/include/fdk-aac && \
rm -v $HOME/vlc_build/vlcdeps/usr/lib/libfdk-aac* && \
rm -v $HOME/vlc_build/vlcdeps/usr/lib/pkgconfig/fdk-aac.pc && \
rm -rfv $HOME/vlc_build/fdk-aac-0.1.3 && rm $HOME/vlc_build/v0.1.3.tar.gz

```

Now by default vlc-git will use libfdk-aac (via FFmpeg) to produce all aac audio, producing very reasonable results according to my ears.

[COLOR=#008000][SIZE=2]**Shine...**[/SIZE][/COLOR]

Shine is a very interesting mp3 encoder that is super fast on machines with an FPU and also fast on machines *without* an FPU. The repository version is too old for vlc-git (version 3.0.0 and above is required) so again we break out the compiler:

```

cd $HOME/vlc_build && \
sudo apt-get -y remove shineenc libshine-dev libshine2 && \
wget https://github.com/savonet/shine/releases/download/3.1.0/shine-3.1.0.tar.gz && \
tar xvf shine-3.1.0.tar.gz && \
cd shine-3.1.0 && ./configure && \
mkdir -vp doc-pak && cp -v ChangeLog COPYING doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes \
                  --pkgname protobuf --pkgversion "2.6.0" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

It is worthwhile spending a little time with the commandline encoder *shineenc*, it is blindingly fast!

[COLOR=#008000][SIZE=2]**Chromecast Dependency: protobuf...**[/SIZE][/COLOR]

A Chromecast plugin is available for vlc-git and an updated version of protobuf is needed. First the repository version should be removed and then the new versions installed:

**Compiling and installing protobuf:**

```

cd $HOME/vlc_build && \
sudo apt-get -y remove protobuf-c-compiler libprotobuf-dev libprotobuf-c0 \
libprotobuf-c0-dev libprotobuf-c0 libprotoc-dev libprotoc8 && \
wget https://protobuf.googlecode.com/svn/rc/protobuf-2.6.0.tar.gz && \
tar xvf protobuf-2.6.0.tar.gz && \
cd protobuf-2.6.0 && \
./configure && \
mkdir -vp doc-pak && cp -v CHANGES.txt CONTRIBUTORS.txt COPYING.txt doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes \
                  --pkgname protobuf --pkgversion "2.6.0" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

Now you should probably go out and buy one of those Chromecast dongles!

[COLOR=#008000][SIZE=2]**x265...**[/SIZE][/COLOR]

Things have matured a little with x265 and vlc so instructions for building x265 and achieving hevc conversions return to this guide! I am using a 'release' version that will periodically be updated in this guide:

**Installing x265:**

```

cd $HOME/vlc_build && \
wget https://bitbucket.org/multicoreware/x265/get/1.4.tar.bz2 -O \
x265-1.4.tar.bz2 && tar xvf x265-1.4.tar.bz2 && \
cd multicoreware-x265-5e604833c5aa && \
mkdir -v build1 && cd build1 && \
cmake ../source && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes \
                  --pkgname x265 --pkgversion "1.4" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
sudo ldconfig && \
rm -rfv $HOME/vlc_build/multicoreware-x265-*/build1

```

**hevc (x265) conversions using cvlc:**

I have had very patchy results from the gui with conversions using x265 but the cli works nicely, just modify file names from this example to suit:

```

cvlc -vv input.mp4 --sout \
         "#transcode{vcodec=hevc,vb=1024,scale=Auto,acodec=mp4a,ab=128,channels=2,samplerate=44100}:\
         std{access=file{no-overwrite},mux=mkv,dst='output.mkv'}" \
         vlc://quit

```

vlc seems to ignore the *vb=1024* setting at the moment, I will continue to investigate this....

[COLOR=#008000][SIZE=2]**daala...**[/SIZE][/COLOR]

Yet another video format in its very early stages of development, this one aiming to be the next generation video codec after hevc and VP9. As far as I can tell vlc-git is one of the only applications at the moment with support for encoding and decoding using daala. Yet another good time to remind those following this guide of the importance of *not* using their production machine for this guide, use a Virtual Machine so breakage is not a big issue!

**Install daala:**

```

sudo apt-get -y install check && \
cd $HOME/vlc_build && \
git clone https://git.xiph.org/daala.git && \
cd daala && ./autogen.sh && \
./configure --disable-player --disable-tools --disable-doc \
            --docdir=/usr/share/doc/daala && make && \
mkdir -vp doc-pak && cp -v AUTHORS COPYING README doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname daala \
                  --pkgversion "1.0-git~$(git rev-parse --short HEAD)" \
                  --fstrans=no --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

**Update daala:**

It is a good idea to update your daala installation every week or so and the following allows this:

```

cd $HOME/vlc_build/daala && git pull && ./autogen.sh && \
./configure --disable-player --disable-tools --disable-doc \
            --docdir=/usr/share/doc/daala && make && \
mkdir -vp doc-pak && cp -v AUTHORS COPYING README doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname daala \
                  --pkgversion "1.0-git~$(git rev-parse --short HEAD)" \
                  --fstrans=no --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

Now with the appropriate ./configure option passed to vlc (*--enable-daala*) you can encode and decode daala video. Below is a sample commandline to get you started:

**daala conversions using cvlc:**

```

cvlc -vv input.mp4 --sout \
         "#transcode{vcodec=daala,vb=1024,scale=Auto,acodec=vorbis,ab=128,channels=2,samplerate=44100}:\
         std{access=file{no-overwrite},mux=ogg,dst='output.ogv'}" \
         vlc://quit

```

Encoding with daala is very, very, very slow at the moment but it is early days yet...

[COLOR=#008000][SIZE=2]**FFmpeg...**[/SIZE][/COLOR]

Next to install a *local* snapshot of the latest release version of FFmpeg which will avoid disturbing system settings of either avconv or FFmpeg..

**Installing FFmpeg:**

```

sudo apt-get -y install libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev zlib1g-dev && \
cd $HOME/vlc_build && \
wget http://ffmpeg.org/releases/ffmpeg-2.5.tar.bz2 && \
tar xvf ffmpeg-2.5.tar.bz2 && cd ffmpeg-2.5 && \
if [ "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="--enable-pic"
 else
  ARCHOPTS=""
fi && \
CPPFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include" \
LDFLAGS="-L$HOME/vlc_build/vlcdeps/usr/lib" \
PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" \
./configure --prefix=$HOME/vlc_build/vlcdeps/usr \
            $ARCHOPTS \
            --enable-gpl \
            --enable-version3 \
            --enable-nonfree \
            --enable-libmp3lame \
            --enable-libopencore-amrnb \
            --enable-libopencore-amrwb \
            --enable-libvpx \
            --enable-libfdk-aac \
            --enable-libx265 \
            --disable-programs \
            --disable-doc \
            --disable-filters \
            --disable-avdevice \
            --disable-devices \
            --disable-avfilter \
            --disable-avresample && \
make -j 2 && make install-libs install-headers && make distclean

```

**Removing FFmpeg:**

To remove the installed libraries, the expanded source and the original archived source use the following:

```

rm -rfv $HOME/vlc_build/vlcdeps/usr/include/{libav*,libpostproc,libsw*} && \
rm -v $HOME/vlc_build/vlcdeps/usr/lib/{libav*.a,libpostproc.a,libsw*.a} && \
rm -v $HOME/vlc_build/vlcdeps/usr/lib/pkgconfig/{libav*.pc,libpostproc.pc,libsw*.pc} && \
rm -rfv $HOME/vlc_build/ffmpeg-*

```

[COLOR=#008000][SIZE=2]**x264...**[/SIZE][/COLOR]

Now for x264, we will a install a *local* copy of the latest x264 which vlc will use for directly transcoding to h.264 (it does not use FFmpeg for this). The use of a local copy is to avoid the mire of dependencies and conflicting version requirements involved with a system installation under Ubuntu.

**Installing x264:**

```

if [ "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="--enable-pic"
 else
  ARCHOPTS=""
fi && \
cd $HOME/vlc_build && \
git clone git://git.videolan.org/x264.git --depth 1 && \
cd x264 && \
./configure --prefix=$HOME/vlc_build/vlcdeps/usr \
            --enable-static \
            --disable-cli \
            $ARCHOPTS && \
make && make install

```

**Removing x264:**

Removing the installed files is reasonably straightforward and the following syntax should be enough:

```

rm -v $HOME/vlc_build/vlcdeps/usr/include/x264* && \
rm -v $HOME/vlc_build/vlcdeps/usr/lib/libx264.a && \
rm -v $HOME/vlc_build/vlcdeps/usr/lib/pkgconfig/x264.pc

```

**Updating x264:**

x264 is updated fairly regularly so I would suggest returning here from time to time and updating the libraries as follows:

```

if [ "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="--enable-pic"
 else
  ARCHOPTS=""
fi && \
cd $HOME/vlc_build/x264 && git pull && \
./configure --prefix=$HOME/vlc_build/vlcdeps/usr \
            --enable-static \
            --disable-cli \
            $ARCHOPTS && \
make && make install

```

Note that these instructions do not actually create an x264 executable, ask in the thread below if you wish to actually do this as well.

[COLOR=#008000][SIZE=2]**libdvdcss...**[/SIZE][/COLOR]

Medibuntu is gone, thanks for the years of work and dedication!! Rather than add a PPA (perhaps I am a troglodyte but I really don't like PPAs!) we will compile our own copy of libdvdcss so that DVD playback is possible. If laws in your country do not allow you to install libdvdcss omit the following single command: 

```

cd $HOME/vlc_build && \
sudo apt-get remove libdvdcss2 && \
wget http://download.videolan.org/pub/libdvdcss/1.3.0/libdvdcss-1.3.0.tar.bz2 && \
tar xvf libdvdcss-1.3.0.tar.bz2 && \
cd libdvdcss-1.3.0 && \
./configure --disable-doc \
            --docdir=/usr/share/doc/libdvdcss && make && \
mkdir -vp doc-pak && cp -v AUTHORS ChangeLog COPYING INSTALL NEWS README doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes \
                  --pkgname libdvdcss2 --pkgversion "1.3.0" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

Now to install the live555 libraries: 

[COLOR=#008000][SIZE=2]**live555...**[/SIZE][/COLOR]

vlc uses live555 for reading some streams and the following single command sets up a local copy following alienBOB's (and the vlc contrib rules.mak) syntax very closely, this copy of live555 courtesy of the videolan servers.

**Installing live555:**

```

cd $HOME/vlc_build && sudo apt-get -y remove liblivemedia-dev && \
wget http://download.videolan.org/pub/contrib/live555/live.2014.07.25.tar.gz && \
tar xvf live.2014.07.25.tar.gz && chmod -R u+w live && cd live && \
if [ "$(uname -m)" = "x86_64" ]; then
  ./genMakefiles linux-64bit && make
else 
  ./genMakefiles linux && make
 fi && \
cp -v \
groupsock/libgroupsock.a liveMedia/libliveMedia.a UsageEnvironment/libUsageEnvironment.a \
BasicUsageEnvironment/libBasicUsageEnvironment.a $HOME/vlc_build/vlcdeps/usr/lib/ && \
cp -v \
groupsock/include/*.hh groupsock/include/*.h liveMedia/include/*.hh UsageEnvironment/include/*.hh \
BasicUsageEnvironment/include/*.hh $HOME/vlc_build/vlcdeps/usr/include/

```

**Removing live555:**

The following removes the installed live555 libraries, the expanded source and the original archived source:

```

rm -v $HOME/vlc_build/vlcdeps/usr/include/{*.hh,NetCommon.h} && \
rm -v $HOME/vlc_build/vlcdeps/usr/lib/{libgroupsock.a,libliveMedia.a,\
libUsageEnvironment.a,libBasicUsageEnvironment.a} && \
rm -rfv $HOME/vlc_build/live && \
rm -v $HOME/vlc_build/live.*.tar.gz

```


[SIZE=4]**[COLOR=#008000]Building vlc-git..[/COLOR]**[/SIZE]

Finally we download the vlc-git source code and build it:

**Install vlc-git:**

```

cd $HOME/vlc_build && git clone git://git.videolan.org/vlc.git --depth 1 && \
cd $HOME/vlc_build/vlc && ./bootstrap && \
CPPFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include" \
LDFLAGS="-L$HOME/vlc_build/vlcdeps/usr/lib" \
PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" \
./configure --prefix=/usr/local --enable-daala && \
make -j 2 && \
mkdir -vp doc-pak && cp -v AUTHORS COPYING INSTALL NEWS README THANKS doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname vlc \
                  --pkgversion "3.0.0-git~$(git rev-parse --short HEAD)" \
                  --fstrans=no --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

And this should give you a working copy of vlc-git! 

**Updating vlc-git...**

You should return from time to time to update your copy of vlc-git, the following single command will accomplish this: 

```

cd $HOME/vlc_build/vlc && git pull && ./bootstrap && \
CPPFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include" \
LDFLAGS="-L$HOME/vlc_build/vlcdeps/usr/lib" \
PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" \
./configure --prefix=/usr/local --enable-daala && \
make -j 2 && \
mkdir -vp doc-pak && cp -v AUTHORS COPYING INSTALL NEWS README THANKS doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname vlc \
                  --pkgversion "3.0.0-git~$(git rev-parse --short HEAD)" \
                  --fstrans=no --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

This completes the setup of vlc-git for this guide and I wish you all the best with your continued exploration of the development version of this great media player! Please use the thread attached to this guide to make any suggestions or ask any questions...

[COLOR=#008000]**[SIZE=4]And in conclusion...[/SIZE]**[/COLOR]

**Recent Guide Updates:**

[LIST]

[*]**Dec 13**: Added in libmpg123-dev to catch the new decoder.
[*]**Dec 07**: Updated FFmpeg to 2.5, updated the website mirror.
[*]**Dec 04**:Created [a website mirror]("http://www.andrews-corner.org/ubuntu/vlc.html") for the guide to hopefully increase usage...
[*]**Nov 28**:Update x265 to 1.4, FFmpeg to 2.4.3
[*]**Oct 17**:A busy pre-weekend update courtesy of me being sidelined with the flu:
    [LIST=1]
[*] Updated FFmpeg to 2.4.2
[*] Added shine for mp3 encoding, thanks to mc4man for pointing this one out. vlc insists on 3.0.0 or greater...
[*] Removed repository protoc/protobuf -dev files and compiled protobuf 2.6.0
[*] Re-enabled chromecast plugin, thanks to mc4man for testing the installation out
[*] Scattered a few more Virtual Machine warnings, this guide *really* should be used in a VM!
    [/LIST]
[/LIST]

---

### Post by andrew.46 on 2013-05-04
It is good to have this guide back in 'Tutorials' again, I look forward to supporting this guide comprehensively as I did in the old days!! A very interesting vlc-git development that I bumped into when I edited this guide for Raring is [the loss of access to the Windows codecs]("http://git.videolan.org/?p=vlc.git;a=blobdiff;f=NEWS;h=9f1a21f9bb057f3f85158e92b9c59610408ef76f;hp=14ac28655abb38e2b642dd1b59f732ebe2644b4a;hb=30b5874ffd7927f1386e06793991edd5b7e156f6;hpb=7e19e888527139a17047cfe451b179190068878a") that was formerly made possible with the* --enable-loader* option:

```

+ * Removed DLL loader for non-Windows Operating Systems

```

A great pity but I guess the Windows codecs were becoming less useful, similar situation with MPlayer. Latest successful compile with this guide:

```

andrew@corinth:~$**[COLOR="#FF0000"] vlc --version | head -n 3[/COLOR]**
VLC media player 2.1.0-pre1 Rincewind (revision 64a5b8a)
VLC version 2.1.0-pre1 Rincewind (64a5b8a)
Compiled by andrew on corinth (May  4 2013 20:18:23)
Compiler: gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1)

```

---

### Post by andrew.46 on 2013-05-04
Looks like I have some substantial catching up to do :). I have added the appropriate dev files to support some of vlc's new abilities:

[LIST=1]
[*]Support for OPUS via libopus.
[*]Support for VDPAU hardware video decoding acceleration on Linux
[*]
[/LIST]

The vdpau support is a pretty big thing, should make the upcoming release very popular. Now to hunt down the following:

```

configure: WARNING: Skins2 interface disabled due to missing dependencies.

```

**Edit:** Looks like libxpm-dev libxinerama-dev libtar-dev solved that one...

---

### Post by mc4man on 2013-05-04
was going to say that the skins2 wasn't an issue here but see you caught the dep.
Decided to let the build go on as per how-to go thru, built fine but during install  see - 
> /usr/bin/ld: /usr/local/lib/libx264.a(common.o): relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC

Likely will be because of a still installed x264 package from typical FFmpeg build. Am currently rebuilding vlc with it removed to d. check.
If so this isn't first occurrence a static build being used when it shouldn't
(when I build aud plugins to /opt againt a shared, decoder only, FFmpeg that's built  to /opt I  have to first remove the FFmpeg build in /usr/local even  with proper exports, ect.  
(options would include - 
removing x264* before build (if users only do a static x264 for a FFmpeg build then no use keeping installed
If one has a current or so FFmpeg build with x264 package still installed  then possibly? the x264 build could use --enable-pic & be usable with vlc also
find a more 'absolute' way to export the pkgconfig/includes
or
fix something here?

edit: 2nd build's install fails now on -
> /usr/bin/ld: /usr/local/lib/libvpx.a(vpx_codec.c.o): relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC

Also from FFmpeg build - will give some thought ..

Those are the only 2 here that cause an issue with as is vlc & ffmpeg  guide builds,  i'll probably just do all static builds out of path & inc., link ,ect as needed, could also move binaries or just run from install dir
( /opt/<whatever or $HOME/<whatever> , a one time set up there.

---

### Post by andrew.46 on 2013-05-05
I have perhaps not tested adequately here in that I have a VM dedicated solely to compiling vlc for this guide and thus I have no extra applications or duplicated applications installed.

---

### Post by mc4man on 2013-05-05
Well your guide is fine & the ffmpeg  guide is fine, just thinking is there a way for both to co-exist. (on 64 bit), with both guides 'as is'

Seems to be 4 sources/packages involved, ffmpeg; libopus; libvpx; (lib)x264
 
libopus - a static build to /usr/local causes _build _failure on 'relocation..."
libvpx  - a static build to /usr/local causes _install/linking_ error on 'relocation ...'
x264 -  a static build to /usr/local causes  _install/linking_ error on 'relocation ...'
ffmpeg -  a static build to /usr/local causes  _install/linking_ error on 'relocation ...'

In the 3 cases of install/linking error, removing those packages just prior to install & all is well (ie. they're not used during the build

Edit: out of the many solutions to using both guides decided for here to - 
keep the vlc one  as is

for ffmpeg went with the guide as is except for a couple of small changes,
All sources use a --prefix=/opt/ffmpeg-current
For the ffmpeg build added  --bindir= /--mandir= /--datadir= options  to install those files to appropriate places in /usr/local/ & all is well, both stay out of each others way, ect.

(the only thing that drove me crazy for a bit was getting ffmpeg to find the other source builds in /opt/ffmpeg-current.  
LD_LIBRARY_PATH & PKG_CONFIG_PATH exports are useless, went with this which worked fine

export C_INCLUDE_PATH=/opt/ffmpeg-current/include

---

### Post by FakeOutdoorsman on 2013-05-06
It is nice to see the return of this guide.

---

### Post by andrew.46 on 2013-05-06
> **FakeOutdoorsman said:**
> It is nice to see the return of this guide.

It is good to be back :).

---

### Post by andrew.46 on 2013-05-06
> **mc4man said:**
> 

Edit: out of the many solutions to using both guides decided for here to - 
keep the vlc one  as is

for ffmpeg went with the guide as is except for a couple of small changes.....

And now all is well?

---

### Post by mc4man on 2013-05-06
> **andrew.46 said:**
> And now all is well?
Yeah, if the static git versions of the mentioned sources have their includes & libs 'out of path' then when vlc is installed the linker doesn't use them.
So the various source, .h, .pc, .a & .la files are in /opt/ffmpeg-current/*, ffmpeg binaries go to /usr/local/bin, the man, data files to /ust/local/share*, ect.
If I was using x264 directly it could also go to /usr/local/bin. 

This is just one way to address, one could do any of several other approaches, from this guide only perspective I guess either just warn about to  remove conflicting before the vlc install, (64 bit), or find a way to prevent when they do exist (I don't quite understand the install process, just can see what happens & what causes

So just as an ex. of my 'new' ffmpeg configure -  (for FO's guide
```

export C_INCLUDE_PATH=/opt/ffmpeg-current/include
export LIBRARY_PATH=/opt/ffmpeg-current/lib
export CPLUS_INCLUDE_PATH=/opt/ffmpeg-current/include 
export PKG_CONFIG_PATH=/opt/ffmpeg-current/lib/pkgconfig

./configure --prefix=/opt/ffmpeg-current --bindir=/usr/local/bin --mandir=/usr/local/share/man \
--datadir=/usr/local/share/ffmpeg  --enable-gpl --enable-libass --enable-libfaac \
--enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libspeex \
--enable-librtmp --enable-libtheora   --enable-libvorbis  --enable-x11grab --enable-libx264 \
--enable-nonfree --enable-version3 --enable-libvpx --enable-libopus --enable-libfdk-aac
```

edit; initially I also used this prior to ffmpeg configure but I don't think it mattered
export LIBRARY_PATH=/opt/ffmpeg-current/lib

---

### Post by andrew.46 on 2013-05-06
I would even consider mentioning that building the development version of vlc would be better done in a virtual machine, in a clean installation of Raring (this is my own model). Problem being for most is that building / compiling vlc uses a lot of resources and all people do not have this available. Interesting to hear the motivations and methods of those who have followed this guide in the past as well as those who are new...

For myself, I have purpose built a computer so I can experiment with multiple VMs and allocate resources extravagantly. My own motivation for building vlc on onr og these sprawling VMs is the joy gained from building and exploring fine software as well as sharing this exploration with others. For bread and butter media playback I do not use the git version of vlc, I usually use Audacious for audio playback, the svn MPlayer for other files and the release vlc when I am feeling lazy...

---

### Post by mc4man on 2013-05-06
I guess any one person's reasons for building  some of these sources will vary - here it's mainly that FFmpeg is more 'active' than Libav & that some sources are 'better' when built off of FFmpeg vs. Libav
(again 'better' may be subjective.

I also use audacious & because it bases off of FFmpeg have taken to building it rather than accept the Debian/Ubuntu version which at times doesn't even include the ffaudio plugin, let alone slightly poorer decoding support when it does have the plugin. 
(11.10 never got ffaudio.so, 13.04 didn't till the last moment, (took me being a bit of a pita to get a small patch applied), 13.10 should be ok as it will use Libav9

As far as here I think just a note that if on 64 bit & using FO's guide or similar there could be issues during the install phase. The downside of one compete vlc config, build, install command is that with the exception of libopus the error(s) will only occur during install, the build itself is actually fine.
(for purpose of testing I broke your command after the make. So simply removing the offending packages, re-running the install (checkinstall) sufficed, then any removed could be re-installed

As far as my suggested concerning a static FFmpeg build - 
Certainly not my place to do so & likely not in this thread but I do think it's better to keep the includes & static libs somewhere else, they're only needed for the target build(s) & can be linked when building from their 'non-standard' location.
(the same as you're doing with FFmpeg & x264 in this guide by installing to $HOME/

---

### Post by matt_symes on 2013-05-06
Guide bookmarked again.

Thanks for posting this andrew.46 :D

---

### Post by andrew.46 on 2013-05-06
> **mc4man said:**
> As far as here I think just a note that if on 64 bit & using FO's guide or similar there could be issues during the install phase. The downside of one compete vlc config, build, install command is that with the exception of libopus the error(s) will only occur during install, the build itself is actually fine.
(for purpose of testing I broke your command after the make. So simply removing the offending packages, re-running the install (checkinstall) sufficed, then any removed could be re-installed

I have a 64bit Raring iso so when I have a quiet moment between studies, work and family I shall install FFmpeg from FakeOutdoorsman's guide and then run the vlc guide and see if there can be an easy resolution. Good to see that you hace done most of the work already :)

---

### Post by andrew.46 on 2013-05-06
> **matt_symes said:**
> Guide bookmarked again.

Thanks for posting this andrew.46 :D

Good to see have the guide active again :)

---

### Post by andrew.46 on 2013-05-06
> **mc4man said:**
> 

Seems to be 4 sources/packages involved, ffmpeg; libopus; libvpx; (lib)x264
 
libopus - a static build to /usr/local causes _build _failure on 'relocation..."
libvpx  - a static build to /usr/local causes _install/linking_ error on 'relocation ...'
x264 -  a static build to /usr/local causes  _install/linking_ error on 'relocation ...'
ffmpeg -  a static build to /usr/local causes  _install/linking_ error on 'relocation ...'

In the 3 cases of install/linking error, removing those packages just prior to install & all is well (ie. they're not used during the build



I have not as yet created my 64bit VM but a few thoughts have come to me. The FFmpeg guide is not specifically written for Raring and instead tries to cover a few Ubuntu versions with *one* guide. But for Raring at least half decent versions of libopus (1.0.1) and libvpx (1.1.0) are available in the Raring Repository, libopus development for one is not that frenetic so should easily be suitable,[ libvpx looks a little busier]("http://code.google.com/p/webm/source/list?repo=libvpx") and a more recent snapshot or release + repository version would be nice. Using Repository versions for these may eliminate 2 errors and I would be curious to then see if manually enabling pic for x264 and FFmpeg in FakeOutdoorsman's guide made the vlc install a little happier. I would have thought that by default the compiler under 64bit ubuntu would do this but I am completely uncertain about this. Certainly under Slackware this must be done manually by adding compiler flags... Would be nice if vlc would ignore these libraries of course.

Sidenote: You will see as well that the Raring yasm has now caught up with recent developments and now ships with 1.2.0 so this may save the compiler a few runs on FakeOutdoorsman's guide :)

---

### Post by FakeOutdoorsman on 2013-05-06
Thanks for the reminder--I forgot about the next Ubuntu release. I'll try to work on the guide this week. 

> **andrew.46 said:**
> ...and instead tries to cover a few Ubuntu versions with *one* guide.

That is the result of trying to be efficient/lazy. Looks like it is time to prune the old versions into their own page...or maybe a "latest Ubuntu" type method is in order. However, my ultimate goal is to ditch the system installation and avoid package management and just provide instructions for a local type install. I haven't tested this in a long time. If anyone wants to add this to the [FFmpeg guide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) then please go ahead.

---

### Post by andrew.46 on 2013-05-06
> **FakeOutdoorsman said:**
> Thanks for the reminder--I forgot about the next Ubuntu release. I'll try to work on the guide this week. 

I thought you might be listening in :)

---

### Post by mc4man on 2013-05-06
There are lots of ways around, the ffmpeg build could supply all for the vlc build that's not available in the repo as long as static builds use -fPIC & in many cases the current Ubuntu repo packages are good & neither guide really needs.

But from another perspective that semi-ties one guide to the other & presumes that the current git FFmpeg is good to go on any day with vlc
Also that presumes a user building vlc has also built FFmpeg.

What would happen if vlc builds off of the FFmpeg source in vlc_deps but then links at install to the FFmpeg git build in /usr/local is unknown.(to me

I still think the cleanest way for both is to install static libs & includes elsewhere & only install binaries, man's, ect. to /usr/local/*
(putting aside all the other sources, I believe that if a static ffmpeg is 'fully' installed' to /urs/local then that 's what will be used when vlc is installed, the same may be true for x264

---

### Post by andrew.46 on 2013-05-06
> **mc4man said:**
> I still think the cleanest way for both is to install static libs & includes elsewhere & only install binaries, man's, ect. to /usr/local/*
(putting aside all the other sources, I believe that if a static ffmpeg is 'fully' installed' to /urs/local then that 's what will be used when vlc is installed, the same may be true for x264

I suspect that as usual you are right :). I have stepped sideways a little from the issue by recommending that the vlc guide be used in a *dedicated *VM rather than as part of a standard Ubuntu installation. I have thought about this for a while and it hinges around the release model of FFmpeg, MPlayer and vlc.

[LIST=1]
[*] Both FFmpeg and MPlayer a meant by the developers to be compiled, installed and used from the 'development' tree. Thus it is a worthwhile exercise to attempt to incorporate these into a standard Ubuntu installation and use both for day to day purposes. Hence FakeOutdoorsman's FFmpeg guides and [that MPlayer guide]("http://www.andrews-corner.org/mplayer.html").
[*] vlc however is intended by the developers to be installed and used from release versions, the development version is intended to be used by developers, the curious and those who love to tinker with fine software to discover and explore new features. Potential for breakage is great and there will be some complication fitting vlc-git into a standard Raring installation.
[/LIST]

(I could add that bug reports, suggested additions etc to the development version of vlc can meet a hostile response from some of the vlc developers, unlike MPlayer and FFmpeg developers, but that is perhaps another issue!) So I have added a suggestion to use a dedicated VM for this guide fully expecting that most will ignore this, therefore I am most grateful that you have found a solution to running both guides on a standard Raring installation...

---

### Post by andrew.46 on 2013-05-07
I see that the vlc developers have upped their[ flac version to 1.3.0-pre4]("http://git.videolan.org/?p=vlc.git;a=commit;h=3ae38645902bf8850ae042dcc2b150c57f80c193") as flac slowly moves [towards a new release]("https://git.xiph.org/?p=flac.git;a%3Dsummary"). After a bit more vlc guide housekeeping this guide might very well follow suit. For those who wish to get in ahead of me here is a link:

[http://downloads.xiph.org/releases/flac/beta/flac-1.3.0pre4.tar.xz](http://downloads.xiph.org/releases/flac/beta/flac-1.3.0pre4.tar.xz)

Looks like it is just about [ready for release...]("http://lists.xiph.org/pipermail/flac-dev/2013-April/004056.html")

---

### Post by mc4man on 2013-05-08
Just to throw out for heck of, attaching slightly modified ffmpeg install com set.

The 4 exports seem to work out, ffmpeg seems a bit picky, may be 'improved'?
The datadir & mandir paths are only best guess ..., mans work which is all I care about

Sole purpose is to build current git binaries for ffmpeg & x264

---

### Post by andrew.46 on 2013-05-10
I have updated the version of FFmpeg used in the guide to 1.2.1 "Magic", latest successful compile was 5 minutes ago:

```

andrew@corinth:~$[COLOR="#FF0000"]** cvlc --version | head -n 3**[/COLOR]
VLC media player 2.1.0-pre1 Rincewind (revision 335457e)
VLC version 2.1.0-pre1 Rincewind (335457e)
Compiled by andrew on corinth (May 11 2013 07:55:30)
Compiler: gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1)
andrew@corinth:~$ 

```

64bit Raring VM now in place and it looks like both 32bit and 64bit versions of this guide are running very nicely. (I have temporarily shelved the flac upgrade as it looks like flac has a very tangled dependency structure under Ubuntu so I will wait for the release version and look again.) Now to have a look at a few of those libraries that the vlc ./configure is missing and see if they are worth chasing up...

---

### Post by mc4man on 2013-05-10
> **andrew.46 said:**
> I have updated the version of FFmpeg used in the guide to 1.2.1 "Magic", latest successful compile was 5 minutes ago:


64bit Raring VM now in place and it looks like both 32bit and 64bit versions of this guide are running very nicely. (I have temporarily shelved the flac upgrade as it looks like flac has a very tangled dependency structure under Ubuntu so I will wait for the release version and look again.) Now to have a look at a few of those libraries that the vlc ./configure is missing and see if they are worth chasing up...
Gave it on quick try on a minimal static of flac, (only built flac & libsndfile),  built/installed fine but the libflac.so was borked on an ogg symbol. Didn't do an ogg rebuild as that gets a bit "tangled".
( though as far as playback really didn't 'seem' to matter as vlc used avcodec instead.

So just went with a shared flac build & all seems well - tested both normal & 24bit flac in various players no issue. No chance yet to try an encoder but should be fine.

> ldd '/usr/local/lib/vlc/plugins/codec/libflac_plugin.so' 
	linux-vdso.so.1 =>  (0x00007fff6f7b1000)
	libvlccore.so.5 => /usr/local/lib/libvlccore.so.5 (0x00007f0b740a3000)
	libFLAC.so.8 => /usr/local/lib/libFLAC.so.8 (0x00007f0b73e52000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f0b73a89000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f0b73881000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f0b73664000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f0b7345f000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f0b7315a000)
	libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007f0b72f16000)
	libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007f0b72d0e000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f0b745aa000)

> main decoder debug: looking for decoder module matching "any": 38 candidates
[0x7f631cc04d98] main decoder debug: using decoder module "flac"

13.04 will never get a new flac, 13.10 should but that doesn't mean it will. (would be surprised if it isn't, not much work to do on it at all

(git-clone can be just git, at some point git-clone will be dropped entirely.

---

### Post by andrew.46 on 2013-05-11
> **mc4man said:**
> Gave it on quick try on a minimal static of flac, (only built flac & libsndfile),  built/installed fine but the libflac.so was borked on an ogg symbol. 

Hmm... was this something like:

```
/usr/lib/libogg.so: could not read symbols: File in wrong format
```

This was an issue that I ran into with Slackware and eventually solved [here]("http://www.linuxquestions.org/questions/slackware-14/cannot-compile-prerelease-flac-on-current-4175461498/"). But this was a multilib problem and possibly Slackware specific, the compile process was finding the wrong libogg on a system with both 32bit and 64bit copies.

> ( though as far as playback really didn't 'seem' to matter as vlc used avcodec instead.

Exactly, I am *assuming *that vlc uses flac directly to transcode but I have not tested this yet.

> 13.04 will never get a new flac, 13.10 should but that doesn't mean it will. (would be surprised if it isn't, not much work to do on it at all

For this guide I may very well wait, 13.10 is just around the corner after all :)

> 
(git-clone can be just git, at some point git-clone will be dropped entirely.

Now I am a little intrigued by that, I am not the greatest git-master in the world and I had not heard that the commands were changing.

Now off to test out the newest flac:

```
andrew@skamandros~$ flac --version
flac 1.3.0pre4
```

:)

---

### Post by mc4man on 2013-05-11
re: git-clone, meant git-core the package, didn't catch what I was typing..

The error in the plugin off of static build was quite specific, an ogg function (undefined), meant to copy out but didn't.

But easy to retrieve - 
> cannot load module `/usr/local/lib/vlc/plugins/codec/libflac_plugin.so' (/usr/local/lib/vlc/plugins/codec/libflac_plugin.so: undefined symbol: ogg_stream_reset)

---

### Post by andrew.46 on 2013-05-11
As a sort of weekend bonus I have added details of how to download and setup a rather large pack of skins for vlc. I am not so keen but perhaps others are? I attach a screenshot of a slightly scary Windows MediaPlayer skin...

---

### Post by andrew.46 on 2013-05-14
I have added in the required gtk library to build the notify plugin for vlc. Seems a little twitchy on my system with a few vlc crashes but it builds and works for the most part. Screenshot attached...

---

### Post by andrew.46 on 2013-05-16
Goom has arrived back again and a big thanks to alienBOB for much of the work massaging the old source code into some shape. I have sourced a newer patch which appears to get around some of the trouble with 32bit vlc and seg faults however I have discovered that 2 visualisations at leat (goom and ProjectM) crash vlc when switching tracks in a playlist, only on 32bit vlc as far as I can see. I would be interested to hear if anybody can duplicate this and even better give a fix :).

As always a screenshot attached, hope the Forums software does not convert this to a jpg again!

---

### Post by andrew.46 on 2013-05-17
I have added in instruction to compile libdvdcss as Medibuntu has gone at least for the moment. Could not get 1.2.13 to compile but I will have another look later unless somebody can solve the issue earlier!

---

### Post by mc4man on 2013-05-17
> **andrew.46 said:**
> I have added in instruction to compile libdvdcss as Medibuntu has gone at least for the moment. Could not get 1.2.13 to compile but I will have another look later unless somebody can solve the issue earlier!
1.2.13 'release' shouldn't be an issue to build & use, the current  git should build but may have some issues with symbols.

Are you sure it didn't build the .so?, the .13 build is quite short
> libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.13 for DVD access


Not too sure there is any advantage to .13 or that much practical difference in the last couple of years of releases...

edit
As a standalone build & install may be necessary to run an ldconfig

---

### Post by andrew.46 on 2013-05-17
Thanks for looking at that mc4man! I will not admit to the stupid thing I was doing but of course 1.2.13 builds and installs just fine. So now this guide is well insulated from whatever becomes of Medibuntu.

Next step is to tidy up the docs from each of the compiled packages and then phase 1 of the return to the Forums is done :).

---

### Post by FakeOutdoorsman on 2013-05-17
"--enable-postproc --enable-pthreads" should be default (at least in recent from git), so they aren't needed but won't hurt if you leave them.

---

### Post by andrew.46 on 2013-05-18
Thanks for that, I shall alter the guide. It has been a decent while since I have looked at the FFmpeg configure options properly and I should also add in *--disable-ffprobe* for completeness as well. **Edit: **Or *--disable-programs* rather...

As a sidenote this looked interesting for my own copy of FFmpeg (rather than this guide):

```

--enable-hardcoded-tables use hardcoded tables instead of runtime generation

```

Still reading up on this one though...

---

### Post by andrew.46 on 2013-05-19
I have been experimenting a little with vovoid's vsxu which works well enough with the git vlc, although it is a little twitchy in VM. I still have some work to do for the installation but early adopters might like to try the following:

```

sudo apt-get install libglew-dev libglfw-dev libftgl-dev libjpeg-dev libxrandr-dev cmake


cd $HOME/vlc_build && \
git clone git://github.com/vovoid/vsxu.git --depth 1 && \
cd $HOME/vlc_build/vsxu && mkdir build && cd build &&  \
cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DOPTIMIZATION_FLAGS=1 .. && make && \
mkdir -vp doc-pak && cp -v ../COPYING ../INSTALL ../README.md doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes \
                  --pkgname vsxu --pkgversion "0.4.0-git-$(date +%Y%m%d)" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
sudo ldconfig && rm -rf $HOME/vlc_build/vsxu/build

```

**Edit:** I have updated the install instructions a little, close to final version now...

---

### Post by andrew.46 on 2013-05-20
I have vsxu running on Slackware (which was not easy btw) so I can now see the visualisations running properly (VM with 3D acceleration does not do it justice). I have thus had a chance to have a closer look at the build system so definitely a little work to do on the syntax above, maybe next weekend I will add the altered syntax onto the main guide, I also need to find where to add the [extra visualisations]("http://data2.vsxu.com/0.3.1/visuals/vovoid-vsxu-visuals.zip") need to go, so more work ahead. A quick screenshot as a teaser added...

**Edit: **Looks like the extra visualisations will live in with all of the other  *.vsx files

---

### Post by andrew.46 on 2013-05-24
Vovoid's vsxu visualisations now in place and I have added in a soundfont suitable for vlc + libfluidsynth, midi playback possible with this. I attach a screenshot showing the section in preferences to put the midi details...

---

### Post by andrew.46 on 2013-05-25
In a bit more weekend work I have installed a newer version of chromaprint:

```

cd $HOME/vlc_build && sudo apt-get remove libchromaprint-dev && \
wget https://bitbucket.org/acoustid/chromaprint/downloads/chromaprint-0.7.tar.gz && \
tar xvf chromaprint-0.7.tar.gz && cd chromaprint-0.7 && \
mkdir build && cd build && \
cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DFFMPEG_ROOT=$HOME/vlc_build/vlcdeps/usr .. && \
make && \
mkdir -vp doc-pak && cp -v ../COPYING.txt ../NEWS.txt ../README.txt doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes \
                  --pkgname libchromaprint --pkgversion "0.7" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
sudo ldconfig && rm -rf $HOME/vlc_build/chromaprint-0.7/build

```

(Both chromaprint and vlc are happier btw if *--enable-shared* is added to the FFmpeg ./configure string.) vlc builds fine against this but I could not find the appropriate window to get this going, I believe there should be [an option off the 'Media Info' window]("http://mailman.videolan.org/pipermail/vlc-devel/2012-November/090875.html"). Anybody have some ideas on this one?

---

### Post by andrew.46 on 2013-05-29
Latest successful compile for this guide:

```

andrew@corinth:~$**[COLOR="#FF0000"] cvlc --version | head -n 3[/COLOR]**
VLC media player 2.1.0-pre1 Rincewind (revision 6c316cc)
VLC version 2.1.0-pre1 Rincewind (6c316cc)
Compiled by andrew on corinth (May 30 2013 11:04:06)
Compiler: gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1)

```

I have given up on acoustic fingerprinting for the moment,[ vlc forums query ]("http://forum.videolan.org/viewtopic.php?f=13&t=111093&sid=602a29a6773a5ea81bbacebafa19237f")was not terribly useful.

---

### Post by andrew.46 on 2013-05-30
> **andrew.46 said:**
> I see that the vlc developers have upped their[ flac version to 1.3.0-pre4]("http://git.videolan.org/?p=vlc.git;a=commit;h=3ae38645902bf8850ae042dcc2b150c57f80c193") as flac slowly moves [towards a new release]("https://git.xiph.org/?p=flac.git;a%3Dsummary").

With a minimum of fanfare the new flac release is out:

[http://downloads.xiph.org/releases/flac/flac-1.3.0.tar.xz](http://downloads.xiph.org/releases/flac/flac-1.3.0.tar.xz)

Low key announcement [here]("http://lists.xiph.org/pipermail/flac-dev/2013-May/004191.html") :). A big day for the audio world...

---

### Post by FakeOutdoorsman on 2013-05-30
Looking forward to FLAC 1.4.0 in 2018.

---

### Post by andrew.46 on 2013-05-30
Don't be too hasty :)

---

### Post by andrew.46 on 2013-06-07
I have added in* libdc1394-22-dev *which is used by firewire digital cameras with vlc. Now if I only had a Firewire camera.... 
[B]
Latest successful build:[/B]

```

andrew@corinth:~$ cvlc --version | head -n 3
VLC media player 2.1.0-pre1 Rincewind (revision 01b0eaf)
VLC version 2.1.0-pre1 Rincewind (01b0eaf)
Compiled by andrew on corinth (Jun  7 2013 16:31:00)
Compiler: gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1)

```

---

### Post by andrew.46 on 2013-06-15
**Latest successful build:**

```

andrew@corinth:~/Desktop$ **[COLOR="#FF0000"]cvlc --version | head -n 3[/COLOR]**
VLC media player 2.1.0-pre1 Rincewind (revision cda1e9b)
VLC version 2.1.0-pre1 Rincewind (cda1e9b)
Compiled by andrew on corinth (Jun 15 2013 14:30:32)
Compiler: gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1)

```

---

### Post by andrew.46 on 2013-07-03
I have altered the version numbers for vlc to reflect recent changes. A big welcome to Weatherwax:

```

andrew@corinth:~$ **[COLOR="#FF0000"]cvlc --version | head -n 3[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision 7ee04e3)
VLC version 2.2.0-git Weatherwax (7ee04e3)
Compiled by andrew on corinth (Jul  4 2013 11:08:41)
Compiler: gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1)

```

---

### Post by fatalkill3r on 2013-08-05
Hi there,

Thank you for this useful tutorial.
I have question. How can i enable vaapi support for my intel NUC. It is having intel HD4000 graphics. XBMC is running good with hardware acceleration. But i need vlc with H/W acceleration.

---

### Post by poul2 on 2013-09-13
Hello,

Thank you for great tutorial. But i got same error, like in official links... [https://help.ubuntu.com/community/CompileVLC](https://help.ubuntu.com/community/CompileVLC) and [https://wiki.videolan.org/UnixCompile/](https://wiki.videolan.org/UnixCompile/)
Tryed and here [http://motorscript.com/compiling-vlc-for-root-users/](http://motorscript.com/compiling-vlc-for-root-users/) And of course i tryed by this tutorial.
Somebody can help me fix it?

I got this error on 2th server.
I used 12.04.03 LTS and now new version 13.04 but still getting same error.

Full log when do installation from dpkg package - [http://pastebin.com/V2P6HNuu](http://pastebin.com/V2P6HNuu)
Error - 
make[2]: Leaving directory `/root/vlc_build/vlc/modules/altivec'
Making distclean in sse2
make[2]: Entering directory `/root/vlc_build/vlc/modules/sse2'
Makefile:1156: ../video_chroma/.deps/libi420_rgb_sse2_plugin_la-i420_rgb.Plo: No such file or directory
Makefile:1157: ../video_chroma/.deps/libi420_rgb_sse2_plugin_la-i420_rgb16.Plo: No such file or directory
Makefile:1158: ../video_chroma/.deps/libi420_yuy2_sse2_plugin_la-i420_yuy2.Plo: No such file or directory
Makefile:1159: ../video_chroma/.deps/libi422_yuy2_sse2_plugin_la-i422_yuy2.Plo: No such file or directory
make[2]: *** No rule to make target `../video_chroma/.deps/libi422_yuy2_sse2_plugin_la-i422_yuy2.Plo'.  Stop.
make[2]: Leaving directory `/root/vlc_build/vlc/modules/sse2'
make[1]: *** [distclean-recursive] Error 1
make[1]: Leaving directory `/root/vlc_build/vlc/modules'
make: *** [distclean-recursive] Error 1

It's looks problem with "--disable-altivec". When i do this in configure, everyting was okey. Just problem now with sound. When using aac, sound have some interference, sharp sound... 

Thank you for your time.

---

### Post by monkeybrain20122 on 2013-11-20
Hi.

I am following the guide to compile vlc but I got a bit confused by Mc4man's comments #6 and #10. How do I check whether vlc is using the local build of ffmpeg or the system one? I am asking because I tried to compile vlc with vdpau support using this guide and got the ./configure error that vdpau required libavcodecs >= 54.36.0. I followed the guide but use git for ffmpeg instead, so libavcodecs should be the latest.
[http://ubuntuforums.org/showthread.php?t=2188965](http://ubuntuforums.org/showthread.php?t=2188965)

---

### Post by monkeybrain20122 on 2013-11-22
Hii anyone?

---

### Post by andrew.46 on 2014-01-09
Restarted work on this guide, hopefully a Saucy version out over the next few days...

---

### Post by brooklynfunk on 2014-01-10
Great! Lets keep this guide alive !

---

### Post by andrew.46 on 2014-01-10
The vlc guide has returned after a substantial time away for me where life buffeted me more than a little. Updates have been:

[LIST=1]
[*]Updated to Saucy Salamander. I have rebuilt the guide running on a fresh Virtual Machine dedicated to building the development version of vlc solely. Some may rememeber that this is the recommended approach for this guide :). This VM has 8gigs RAM allocated from my 16gigs, 30gigs of HDD from my 2TB and 6 cores of my 8 core machine, I run the vlc compile at -j 12 and it screams along! Only testing the 64bit Ubuntu at the moment, hopefully if there are any specifically 32bit problems somebody in this thread will post...
[*]Updated FFmpeg installation to 2.1.1 "Fourier" which was released on 2013-11-20. Most will realise that a decent and up to date version of FFmpeg is essential for a solid build of vlc.
[*]Live555 libraries are no longer hosted on my website as I have shut this down and come from the VideoLan website. I have not had a good look to see if this newer version is working well or not, this will be a job for the next couple of weeks...
[*]I will continue to give instructions for compiling libdvdcss rather than use a PPA which I seem to be on my own for cordially disliking. Left a quick note about Medibuntu's demise.
[*]Updated to the latest versions of libbluray and libaacs for those like myself with bluray drives. I have added in a few line and a code snippet to allow people to easily place KEYDB.cfg in the correct location for decrypting bluray disks.
[*]I have removed the instructions for building goom and the vsxu visualisations with the aim of simplifying the guide a little and concentrating on the core idea of tracking vlc development rather than playing with eye candy.
[*]Took out the thumbnails at the base of the guide as this seemed again to be simply eye candy that the guide could do without.

[/LIST]
So hopefully the guide will attract some interest. I am aware that it is a little far from standard fare for Ubuntu users and will never attract a huge following but I am sure it has a place in these Forums and it certainly gives me a fascinating hobby :). For reference the latest successful build on my machine is:

```

andrew@corinth:~$[COLOR="#FF0000"] vlc --version | head -n 2[/COLOR]
VLC media player 2.2.0-git Weatherwax (revision 6d07bbb)
VLC version 2.2.0-git Weatherwax (6d07bbb)
Compiled by andrew on corinth (Jan 10 2014 14:39:51)

```

Happy compiling and troubleshooting :)

---

### Post by MountainX on 2014-01-16
Thank you for the guide! I'm going to try it with Kubuntu 12.04 64 bit. Is there anything I should know about differences with 12.04 before I get started?

Maybe you should also post this over on AskUbuntu. (I looked there first.)

---

### Post by mc4man on 2014-01-17
> **MountainX said:**
> Thank you for the guide! I'm going to try it with Kubuntu 12.04 64 bit. Is there anything I should know about differences with 12.04 before I get started?

Maybe you should also post this over on AskUbuntu. (I looked there first.)
You may run into a couple of issues with some outdated or unavailable packages in 12.04.
Currently I'm on the road for a while with only a portable 4g hotspot device for internet access so not in a position to test 12.04.
 I'll list some possible ones &  means to resolve

yasm - it's almost definite  12.04's yasm is too old, if so you can build a newer version or get from a ppa
libopus/libopus-dev - not in 12.04, again build or get from ppa
The 2 above I have in an mplayer ppa, if desired add/upgrade  from here - 
[https://launchpad.net/~mc3man/+archive/mplayer-test](https://launchpad.net/~mc3man/+archive/mplayer-test)

Looking at the videolan master ppa, they added 3 additional  packages for 12.04 builds, whether you need them you'll need to see. Again, if so then either build newer versions or in these cases just get from the ppa
chromaprint _ you may not need
dbus - may not hurt to use the updated ppa packages..
gnutls28 - not sure about as the guide uses a lesser version - libgnutls-dev which is libgnutls26 & available in 12.04

So in the 3 above maybe only the dbus packages are of value?, you could try without & if needed add from ppa
[https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)

In any event you should be able to get this squared away pretty quickly, post any problems or build issues if they arise..

---

### Post by andrew.46 on 2014-01-17
> **MountainX said:**
> Thank you for the guide! I'm going to try it with Kubuntu 12.04 64 bit. Is there anything I should know about differences with 12.04 before I get started?

You could very well run into a few package name issues with the so-called 'dev' files which have changed a little since 12.04 times. With all other files, that for the most part are external to the Ubuntu Repositories, there should be no trouble. Don't forget too the little note at the beginning of this guide that the development version of vlc is best built in a dedicated VM rather than your main installation...

> Maybe you should also post this over on AskUbuntu. (I looked there first.)

I am a 'part time' Ubuntu-ite and my activities in the community are mostly confined to these Forums, I confess I have never really even looked at AskUbuntu. Perhaps I will check it out on the weekend.

---

### Post by FakeOutdoorsman on 2014-01-17
askubuntu seems fairly limited in terms of interesting topics for us multimediaers, but I'll try to provide an answer now and then.

Unfortunately, the interaction often seems to be lacking. You can create a nice answer and you get no indication from the question asker if it even worked for them (usually new or one-time users I guess).

---

### Post by andrew.46 on 2014-01-17
I have just started to have a closer look at the finer details of the guide and I notice that the Opus encoder is failing:

```

checking for OPUS... no
configure: WARNING: Library ogg opus >= 1.0.3 needed for opus was not found

```

and in fact Saucy's version is too old:

```

andrew@corinth:~$ **[COLOR="#FF0000"]apt-cache policy libopus-dev[/COLOR]**
libopus-dev:
  Installed: 1.0.1-0ubuntu2
  Candidate: 1.0.1-0ubuntu2
  Version table:
 *** 1.0.1-0ubuntu2 0
        500 http://au.archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages
        100 /var/lib/dpkg/status

```

According to [the Opus website]("http://www.opus-codec.org/") version 1.1 was released on December 5th 2013 (possibly as a 53rd birthday present for myself?) so I have added in suitable instructions to compile the newest version in the 'Optional extras...' section. Note that this does not include the installation of the opus-tools source which includes the commandline encoder, decoder and info applications. Interestingly enough I cannot see the opus encoder in the vlc options so I would be interested to hear if anybody can ferret out the required menu?

In a job for next weekend I see that the development version of vlc now supports x265 decoding and encoding so this will be a fascinating area to delve into for sure :)

---

### Post by MountainX on 2014-01-17
> **andrew.46 said:**
> Don't forget too the little note at the beginning of this guide that the development version of vlc is best built in a dedicated VM rather than your main installation...


Yes,  I guess you can never remind people too often! I admit that I probably would have skipped that advice if you hadn't repeated it here. I'll start by setting up a VM now :-)

And thanks again for the great guide!

---

### Post by andrew.46 on 2014-01-17
> **MountainX said:**
> Yes,  I guess you can never remind people too often! I admit that I probably would have skipped that advice if you hadn't repeated it here. I'll start by setting up a VM now :-) 

It is a suggestion that is a little conservative in nature as the guide is relatively safe but it still deals with development software and thus would be better suited to the more *insulated* environment of a VM. I actually purpose built a computer to run VMs smoothly and this makes a big difference.

> And thanks again for the great guide!

I hope that is the same sentiment when you have installed vlc from this guide :). I have some plans for over the next week or so:

[LIST]
[*]Set up the acoustic ID settings of vlc using libchromaprint, should be working [now]("https://forum.videolan.org/viewtopic.php?f=13&t=111093"). Looks like the repository version should be ok.
[*]See what is involved in getting VP9 encoding organised through vlc.
[*]Set up h265 encoding through vlc, this arrived [a few months back]("http://git.videolan.org/?p=vlc.git;a=commit;h=f1d6824164a1b33c3befc8ad7e16aa94f866ee04").
[*]
[/LIST]

Some [interesting politics]("http://news.cnet.com/8301-11386_3-57612525-76/vlc-steps-into-next-gen-video-wars-with-vp9-hevc-support/") with 2 of these atm. I will be probably only adding these sections in each weekend but it should be a lot of fun...

---

### Post by andrew.46 on 2014-01-18
I had a small spare moment hiding inside from the 40° Celsius heatwave and I have updated the FFmpeg installation to 2.1.3. Also added in a little snippet to completely remove the older FFmpeg files, not really a mandatory thing but it is a little bit of housekeeping that some might like. The syntax is reasonably conservative in case people have added other libraries etc.

Latest successful build:

```

andrew@corinth:~$ **[COLOR="#FF0000"]cvlc --version | head -n 2[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision cdbe3ee)
VLC version 2.2.0-git Weatherwax (cdbe3ee)
Compiled by andrew on corinth (Jan 18 2014 19:58:55)

```

Which reminds me, I must fix up the package naming for vlc which looks a little amateurish...

---

### Post by andrew.46 on 2014-01-19
Having investigated a little further I can see that Opus encoding is not available from the gui as at the very least it is not yet included in the encoding profiles located in* /modules/gui/qt4/components/sout/profiles.hpp*. Have to wait a little I guess, good to see that [an h265 profile]("http://git.videolan.org/?p=vlc.git;a=commit;h=37502dd2d20a6c7669e81a24cccdaaea47c09f83") has been added today though...

---

### Post by andrew.46 on 2014-01-21
I have worked fairly hard to get x265 neatly packaged and to tell the truth there is still a little way to go and although x265 (or rather h.265 encoding) shows as a menu in vlc it does not function for me yet. Nevertheless below is the prospective section of the guide as it will appear when a few more bugs have been ironed out, you will need to have cmake and mercurial installed of course:

-----------------------------------------------------------
**h265 Encoding...**

It is very, very early days for the x265 encoder and it is very exciting to be able to sample vlc's early adoption! Use the snippet below to install:

**Install:**

```

cd $HOME/vlc_build && \
hg clone https://bitbucket.org/multicoreware/x265 && \
mkdir -v x265/build1 && cd x265/build1 && \
cmake ../source && make -j 2 && \
mkdir -vp doc-pak && cp -v ../COPYING ../build/README.txt doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --pkgname x265 \
        --pkgversion "$(cmake . | grep "x265 version" | cut -d ' ' -f4 | tr - '~')" \
        --backup=no --fstrans=no --deldoc=yes --deldesc=yes --delspec=yes --default && \
sudo ldconfig && rm -rf $HOME/vlc_build/x265/build1

```

And when it is time to update, and I would suggest that this should be reasonable often since development is moving along pretty quickly, simply use the following:

**Update:**

```

cd $HOME/vlc_build/x265 && hg pull && hg update && \
mkdir build1 && cd build1 && \
cmake ../source && make -j 2 && \
mkdir -vp doc-pak && cp -v ../COPYING ../build/README.txt doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --pkgname x265 \
        --pkgversion "$(cmake . | grep "x265 version" | cut -d ' ' -f4 | tr - '~')" \
        --backup=no --fstrans=no --deldoc=yes --deldesc=yes --delspec=yes --default && \
sudo ldconfig && rm -rf $HOME/vlc_build/x265/build1

```

I hope that like me you enjoy seeing the new encoder mature :)

-----------------------------------------------------------

Hopefully somebody will succeed where I have failed so far and get the encoder working within vlc... and remember to go and make a cup of tea while x265 is compiling or patch yasm as suggested.

---

### Post by andrew.46 on 2014-01-23
Weekend updates are now in place:

[LIST]
[*]Cleaned out the ./configure options for vlc. I have left this empty as vlc seems to have a reasonable amount of autodetection or sensible defaults in place.
[*]Added in instructions for x265 installation and appropriate syntax for updating. Still does not work well for me with vlc, there is an odd FFmpeg error message and the native encoder does not kick in. Early days yet I guess...
[*]Temporarily abandoned Acoustic ID as libchromaprint wants a shared FFmpeg, libchromaprint-dev wants to install libav extras and it was all getting a little too complicated for the small gain of *playing* with Acoustic ID...
[*]A little code snippet added in to cleanly remove the local FFmpeg, I will add similar for live555 and x264 by next weekend.
[*]
[/LIST]

Which means that the guide is now firmly up to date and may sail through the rest of the life of Saucy with minimal major changes. Trust Tahr is out in April so I guess this not saying too much :)

Latest compile:

```

andrew@corinth:~$ **[COLOR="#FF0000"]cvlc --version | head -n 2[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision 379eb76)
VLC version 2.2.0-git Weatherwax (379eb76)
Compiled by andrew on corinth (Jan 24 2014 11:46:35)

```

---

### Post by andrew.46 on 2014-02-03
Latest weekend updates now in place, a little late but things have been busy here In Real Life&#8482;. 3 simple changes:

[LIST=1]
[*]Disabled a few more options with FFmpeg. This idea mostly drawn from the syntax used by the vlc developers in their 'contrib' directory and this source of syntax rules is a rich vein I will be mining over the next little while.
[*]Updated the live555 libraries and I have also added in a little code snippet to manually rid the installation of older live555 libraries Not completely necessary but nice to have in place.
[*]I have added in cmake-curses-gui after I finally realised that this the Ubuntu package name for ccmake :). I am no cmake wizard and I have found that ccmake makes sorting out the options a lot easier...
[*]
[/LIST]

I have spent more time than I would care to admit trying to make vlc happy with libchromaprint with a succession of sometimes quite spectacular failures (although I like the sed magic I created). If only alienBob would package this and solve all of the problems for me! My 'work in progress version' is below in case somebody cleverer than me can get the whole thing working:

**[COLOR="#0000CD"]===================================[/COLOR]**

**Acoustic ID....**

Acoustic ID sampling identification is a fascinating idea and it is available with vlc and libchromaprint. We will use the latest version that will be compiled against our local copy of FFmpeg:

```

cd $HOME/vlc_build && sudo apt-get remove libchromaprint-dev && \
if [ "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="-DCMAKE_CXX_FLAGS:STRING=-fPIC -DCMAKE_C_FLAGS:STRING=-fPIC"
 else
  ARCHOPTS=""
fi && \
wget https://bitbucket.org/acoustid/chromaprint/downloads/chromaprint-1.1.tar.gz && \
tar xvf chromaprint-1.1.tar.gz && cd chromaprint-1.1 && \
sed -i_bak '/^Libs:/ s/$/ -lavcodec -lavutil/' libchromaprint.pc.cmake && \
mkdir build && cd build && \
cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DFFMPEG_ROOT=$HOME/vlc_build/vlcdeps/usr \
      -DBUILD_SHARED_LIBS:BOOL=OFF $ARCHOPTS .. && \
make && \
mkdir -vp doc-pak && cp -v ../COPYING.txt ../NEWS.txt ../README.txt doc-pak && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes \
                  --pkgname libchromaprint --pkgversion "1.1" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
sudo ldconfig && rm -rf $HOME/vlc_build/chromaprint-1.1/build

```

The little piece of sed magic duplicates part of a vlc patch, not sure if I have ever mentioned my love of sed :). Unfortunately fingerprinting currently segfaults in my installation of vlc and remains something that I need to work on further. Any wisdom from those reading will be listened to with great attention...

**[COLOR="#0000CD"]===================================[/COLOR]**

I am back at my ashram for a couple of weeks soon so updates may be a bit sparse but I am still enjoying myself immensely plugging away at vlc-git so the updates will continue :). First job will be to change x265 to a local installation and and then perhaps have another go at libchromaprint... Latest successful compile:

```

andrew@corinth:~$ **[COLOR="#FF0000"]cvlc --version | head -n 2[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision a24c2e7)
VLC version 2.2.0-git Weatherwax (a24c2e7)
Compiled by andrew on corinth (Feb  3 2014 21:02:20)

```

---

### Post by mc4man on 2014-02-05
Haven't been using vlc much lately (other than thru an interesting FF add-on) so have no clue as to how to 'use' chromaprint..?

Have you tried using the repo version ? (it should not require any libav dev files
Edit: - sorry, see now your issue is with libchromaprint0 which deps on libav*...

---

### Post by andrew.46 on 2014-02-05
> **mc4man said:**
> Edit: - sorry, see now your issue is with libchromaprint0 which deps on libav*...

Indeed, and I have followed pretty closely the vlc method of building libchromaprint. Also tried building against FFTW3 which unfortunately also had a few issues under 64bit Ubuntu. Looks like I am not alone though:

[https://forum.videolan.org/viewtopic.php?f=13&t=113054](https://forum.videolan.org/viewtopic.php?f=13&t=113054)

although the vlc developers are an irascible lot sometimes.... At the worst I will simply wait a little and hope for the code to develope further or hear from others with the same problem and hopefully a solution, Acoustic ID is not exactly a vital addition to testing the development version. I have it working on a Windows installation and so far it has not successfully identified any tracks :)

---

### Post by andrew.46 on 2014-02-09
A few very small updates to the guide this weekend as I prepare for a fortnight at the ashram:

[LIST=1]
[*]Placed removal and update instructions for x264.
[*]Started a larger project of improving the syntax of the guide with different sized headings and detailed installation, removal and updating instructions for each section
[*]
[/LIST]

I have a few small projects when I come back from my retreat:

[LIST=1]
[*]Convert the x265 section to a local installation (as with x264) and no longer build and install the x265 executable. This will avoid future snarl ups with version requirements with x265 although I doubt that x265 will make it into the upcoming Trusty release.
[*]Remove the faac option from FFmpeg and install fdkaac instead which vlc can encode with directly, faac is *way* past its time now.
[*]Finish tidying up the syntax of the guide.....
[*]
[/LIST]

 **Note**: at the moment *--disable-vdpau* is a quick work around to enable build...

Latest successful build:

```

ndrew@corinth:~$ **[COLOR="#FF0000"]cvlc --version | head -n 2[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision c3f638a)
VLC version 2.2.0-git Weatherwax (c3f638a)
Compiled by andrew on corinth (Feb  9 2014 13:49:43)

```

---

### Post by andrew.46 on 2014-02-25
Back on deck with a couple of updates for the guide:

[LIST=1]
[*] Added instructions to build the release version 2.1.3 for those who wish to have a look at it.
[*] Tested the cli syntax for producing opus files and included this in the 'opus' section.
[*] Changed x265 syntax to build the 'release' version .7 and shifted to a local install without the cli binary. Newer versions are breaking the vlc compile and x265 has yet to produce a workable file for me from within vlc anyway :).
[*]
[/LIST]

The *--disable-vdpau* is still in place but courtesy of alienBOB I may have found the problem with this and hopefully will have this fixed in the next set of updates. For the next update as well I hope to remove faac and use fdk-aac for aac encoding with vlc. Latest successful compile:

```

andrew@corinth:~$**[COLOR="#FF0000"] cvlc --version | head -n 2[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision ee6b5ce)
VLC version 2.2.0-git Weatherwax (ee6b5ce)
Compiled by andrew on corinth (Feb 26 2014 09:28:18)

```

---

### Post by monkeybrain20122 on 2014-02-25
I have no problem building with vdpau enabled, is it because you are using a developmental version of ffmpeg? I just build against ffmpeg 2.1.3  (vlc also 2.1.3)

Is there any clean way to handle phonon-backend-vlc? Just wondering.

---

### Post by andrew.46 on 2014-02-25
> **monkeybrain20122 said:**
> I have no problem building with vdpau enabled, is it because you are using a developmental version of ffmpeg? I just build against ffmpeg 2.1.3  (vlc also 2.1.3)

I actually use the release version of FFmpeg but certainly the development version of vlc. In vlc-git there is an issue with a 64bit installation statically linking against libvdpau which I notice that alienBOB has fixed by adding an extra strip command against the libraries. I have not investigated any further than this and certainly this is a problem for vlc-git and not vlc 2.1.3. It would be nice to see where this issue crept into the source tree...

> Is there any clean way to handle phonon-backend-vlc? Just wondering.

Hmmm... I am not familiar with this except to know it is a multimedia 'back-end' to kde. What uses this?

---

### Post by monkeybrain20122 on 2014-02-25
> **andrew.46 said:**
> 

Hmmm... I am not familiar with this except to know it is a multimedia 'back-end' to kde. What uses this?

Minitube. The alternative is phonon-backend-gstreamer but it has been broken for quite a while.

---

### Post by mc4man on 2014-02-25
> **monkeybrain20122 said:**
> 

Is there any clean way to handle phonon-backend-vlc? Just wondering.
Other than equivs probably not.
Unless something has changed in checkinstall it will only do one 'provides' & in this case 3 are needed

---

### Post by andrew.46 on 2014-02-25
Can't sort the vdpau error so I have thrown myself to the lions:

[https://forum.videolan.org/viewtopic.php?f=13&t=117726](https://forum.videolan.org/viewtopic.php?f=13&t=117726)

:)

---

### Post by mc4man on 2014-02-26
So vlc has jumped on the libav bandwagon?? (or is it a slow boat to china
See no issue using FFmpeg in a recent compile (amd64

---

### Post by andrew.46 on 2014-02-27
And the libav / FFmpeg split rumbles along :(. Did your successful compile of vlc-git involve FFmpeg 2.1.3 or FFmpeg from git?

---

### Post by FakeOutdoorsman on 2014-02-27
I don't think all VLC devs are on the bandwagon, but I haven't been following it much.

---

### Post by andrew.46 on 2014-02-27
> **FakeOutdoorsman said:**
> I don't think all VLC devs are on the bandwagon, but I haven't been following it much.

I could easily tire of the whole business I will admit as my only interest here is to build the latest vlc, check out the newest features etc etc. Sigh..... Anyway for the moment I have borrowed the FFmpeg snapshot idea from the FFmpeg wiki and that has everything running well enough. It is not ideal as I would like a specific version of FFmpeg to compile against and when the FFmpeg developers produce a new release from the master I will jump to this. On the website there is talk of such a release every 3 months which should mean a new version very soon.

Latest successful compile:

```

andrew@corinth:~$ **[COLOR="#FF0000"]cvlc --version | head -n 2[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision 6ae117d)
VLC version 2.2.0-git Weatherwax (6ae117d)
Compiled by andrew on corinth (Feb 28 2014 07:05:07)

```

---

### Post by mc4man on 2014-02-27
> **andrew.46 said:**
> And the libav / FFmpeg split rumbles along :(. Did your successful compile of vlc-git involve FFmpeg 2.1.3 or FFmpeg from git?
I did it with git but there is a 2.1.4 release that I'd imagine would be ok..

---

### Post by andrew.46 on 2014-02-27
> **mc4man said:**
> I did it with git but there is a 2.1.4 release that I'd imagine would be ok..

I am working on [a scheme ]("http://ubuntuforums.org/showthread.php?t=786095&p=12942284&viewfull=1#post12942284")to use a set git snapshot, as always unsuccessfully trying to keep the complexity level of this guide down a little :(. 2.1.4 was giving some trouble but vlc-git compiles fine with this snapshot so after a bit more testing I will probably use this. I will be back at work in a few days so it will be good to have this final bit of work on the guide complete.

---

### Post by mc4man on 2014-02-27
I'm sure you'll find a solid way.
In regards to that orig. error - 

I tried with FFmpeg 2.1.4 & got same error using the same vlc git as the other day.
In that source /modules/hw/vdpau/avcodec.c had this at point of error - 

#if (LIBAVCODEC_VERSION_INT >= AV_VERSION_INT(55, 26, 0))
    sys->context = av_vdpau_alloc_context();
#else
    sys->context = calloc(1, sizeof (*sys->context));

It's possible that if 26 had been changed to higher that whatever libavcodec was in 2.1.3 or is in .4 the build would have succeeded.
(I gather libav & FFmpeg at are different states with similar XX,XX,X

The vlc git from today has removed the if & else so now it's just 
sys->context = av_vdpau_alloc_context();
which I guess doesn't work with 2.1.3 or 2.1.4

---

### Post by andrew.46 on 2014-02-28
Thanks for looking at this mc4man, I am greatly relieved that I am not alone with that error :).  Looks like I will go ahead with the snapshot from FFmpeg gitweb as this gives a great amount of flexibility as well as a standardised FFmpeg source. The release versions will always stay frozen in time with point upgrades for 3-4 months and, as in this case, this can be more than a little frustrating and maintaining a cloned git repository for FFmpeg is something I would prefer to avoid.

I will say up front that this is yet another idea I have taken from [alienBOB's vlc build]("http://www.slackware.com/~alien/slackbuilds/vlc/build/vlc.SlackBuild"), that man is truly a genius with a script. That particular slackbuild is quite complex and a similar level of complexity can be seen in his [libreoffice]("http://www.slackware.com/~alien/slackbuilds/libreoffice/build/libreoffice.SlackBuild") build. Always something to learn from alienBOB...

---

### Post by ron998 on 2014-03-01
Hi
> ron@Xubuntu:~$ cvlc --version | head -n 2
VLC media player 2.2.0-git Weatherwax (revision 8da1697)
VLC version 2.2.0-git Weatherwax (8da1697)
Compiled by ron on Xubuntu (Mar  1 2014 04:19:07)

**"From time to time the live555 libraries will be updated..."**

Tweaked the live555 procedure... ;)

```
cd $HOME/vlc_build; sudo apt-get -y remove liblivemedia-dev; \
curl live555.com/liveMedia/public/live555-latest.tar.gz | tar -xz; chmod -R u+w live; cd live; \
if [ "$(uname -m)" = "x86_64" ]; then
  ./genMakefiles linux-64bit; make
else 
  ./genMakefiles linux; make
 fi
......
```

---

### Post by andrew.46 on 2014-03-01
Ron I am starting to suspect that you have been spending too much time at the commandline :)

---

### Post by andrew.46 on 2014-03-01
Weekend updates now in place and I am glad to have made some substantial progress as I am not only back to work in a day but I have another 12 months of hard study ahead!! Changes have been:

[LIST=1]
[*]FFmpeg moved to gitweb snapshot and environment variables added. I have selected a gitweb snapshot at about the time that 2.2 is being released but this strategy will pay off in the long term I am sure as I will be able to 'surgically' select an FFmpeg snapshot and capture new features when required. The environment variables will enable FFmpeg to pick up locally installed libraries such as fdk-aac and this is another investment in the future of this guide.
[*]libfaac-dev removed and fdk-aac instructions added plus a cli example for aac encoding. Faac has been dead technology for a while now and I have found much better sounding aac encoding with fdk-aac through vlc. I am almost 100% sure that fdk-aac is doing the encoding via FFmpeg, the vlc commandline does not give a lot away and the 'encoded by' tag is a vlc one... I have added an example of such encoding from the cli.
[*]x265 instructions moved to the 'Optional' section. My next weekend project is to sort out the x265 issues. As the guide sits at the moment x265 encoding does not work although just 5 minutes ago I compiled current FFmpeg against current x265 and produced a workable hevc file in an mkv container. I suspect I need a newer x265 compiled against a newer FFmpeg (with --enable-libx265) and see if that will make vlc happier.Next week.
[*]Removal instructions for 'local', compiled applications standardised throughout the guide. This makes my work on the guide a little easier and perhaps will make those unhappy with *not *using checkinstall a little happier.
[*]cli instructions for resetting preferences to default. Added this near the 'Skins' section as I have found several of the skins will make vlc crash and burn!
[/LIST]

So I suspect the sequence will be: fix x265 definitively and then have a look at Trusty. A more nebulous project is to gather a few commandline examples in one section for those who are keen on this, there is not a lot of decent information on cli usage with vlc.

---

### Post by ron998 on 2014-03-01
> **andrew.46 said:**
> ... I am almost 100% sure that fdk-aac is doing the encoding via FFmpeg...

Yes, I think so too. :)

With **--enable-libfdkaac**...

mediainfo outfile1.m4a shows **LC**
mediainfo outfile2.m4a shows **HE-AAC / LC**
mediainfo outfile3.m4a shows [B]HE-AACv2 / HE-AAC / LC
[/B]
```
cvlc -vv --sout \
     "#transcode{acodec=mp4a,ab=128,channels=2,samplerate=44100}:\
     std{access=file,mux=mp4,dst=outfile1.m4a}" \
     infile.wav vlc://quit
```

```
cvlc -vv --sout-avcodec-aac-profile hev1 --sout \
     "#transcode{acodec=mp4a,ab=64,channels=2,samplerate=44100}:\
     std{access=file,mux=mp4,dst=outfile2.m4a}" \
     infile.wav vlc://quit
```

```
cvlc -vv --sout-avcodec-aac-profile hev2 --sout \
     "#transcode{acodec=mp4a,ab=32,channels=2,samplerate=44100}:\
     std{access=file,mux=mp4,dst=outfile3.m4a}" \
     infile.wav vlc://quit
```

> ron@Xubuntu:~$ cvlc --version | head -n 2
VLC media player 2.2.0-git Weatherwax (revision 54536c5)
VLC version 2.2.0-git Weatherwax (54536c5)
Compiled by ron on Xubuntu (Mar  1 2014 12:30:50)


---

### Post by andrew.46 on 2014-03-01
Thanks Ron for confirming that, I was not aware of the *--sout-avcodec-aac-profile* option but that demonstrates it nicely :). One day I should delve a little deeper into the cli options for vlc.....

I see it clearly enough now:

```

      --sout-avcodec-aac-profile <string>
                                 Specify AAC audio profile to use
          Specify the AAC audio profile to use for encoding the audio
          bitstream. It takes the following options: main, low, ssr (not
          supported),ltp, hev1, hev2 (default: low). hev1 and hev2 are
          currently supported only with libfdk-aac enabled libavcodec

```

Much buried treasure in cvlc -H !

**Edit:** On digging a little deeper it looks like in this build FFmpeg only has 2 aac encoders: aac and libfdk_aac and these can be specified on the commandline:

```

cvlc -vv --sout-avcodec-aac-profile hev2 **[COLOR="#FF0000"]--sout-avcodec-codec libfdk_aac[/COLOR]** --sout \
     "#transcode{acodec=mp4a,ab=32,channels=2,samplerate=44100}:\
     std{access=file,mux=mp4,dst=outfile.m44}" \
     luckynight.wav vlc://quit

```

Using *aac *of course fails, this is FFmpeg's own native encoder, and there is an error message suggesting* libfdk_aac*. It is always a good day when you learn something new...

---

### Post by mc4man on 2014-03-03
Just a note - 
don't know how many want https support in vlc (I find handy) but the current git & recent releases  seem to require  higher version than before 
> configure: error: Requested 'gnutls >= 3.0.20' but version of GnuTLS is 2.12.23

Satisfied with  -  libgnutls28-dev

---

### Post by ron998 on 2014-03-03
> **mc4man said:**
> Satisfied with  -  libgnutls28-dev

Pangolin-12.04LTS libgnutls28-dev is only 3.0.11. :(
"Requested 'gnutls >= 3.0.20' but version of GnuTLS is 3.0.11"

Trusty-14.04LTS libgnutls28-dev is 3.2.3
Will have to manage without gnutls till April. :)

---

### Post by mc4man on 2014-03-04
> **ron998 said:**
> Pangolin-12.04LTS libgnutls28-dev is only 3.0.11. :(
"Requested 'gnutls >= 3.0.20' but version of GnuTLS is 3.0.11"

Trusty-14.04LTS libgnutls28-dev is 3.2.3
Will have to manage without gnutls till April. :)

14.04 should be much improved, currently has a few issues, mainly around unity-window-decorator, compiz & lim.

A small side 'issue' of  libgnutls28-dev  is then librtmp-dev is removed.  Doesn't much matter unless one wanted for a mplayer build, then it & libgnutls-dev would need to be returned for the build.
(I did put up a test build of rtmpdump off of libgnutls28 for trusty to see, seems fine.

---

### Post by andrew.46 on 2014-03-04
Thanks mc4man and ron, I have added in the required gnutls dev package. Also taken out the x265 material as it is getting a little too hard. Perhaps I will add back in after Trusty has arrived...

---

### Post by ron998 on 2014-03-05
Hi
There are some rtsp streams that VLC can't play unless it's configured with **--enable-realrtsp**.
(Just sayin') ;)

```
ron@Xubuntu:~$ cvlc --list | grep real
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
  [COLOR=#ff0000]real[/COLOR]                   Real demuxer
  access_[COLOR=#ff0000]real[/COLOR]rtsp        Real RTSP
```
Examples from **rai.it**:-
```
rtsp://live.media.rai.it/broadcast/radiouno.rm
rtsp://live.media.rai.it/broadcast/radiodue.rm
rtsp://live.media.rai.it/broadcast/radiotre.rm
```
VLC handles these badly though. :(
Seems like the realrtsp plugin is broken, or maybe it's not compatible with modern libavcodec/libavformat.
Probably it won't get fixed because these rm streams are dying out.
But MPlayer plays them OK. :p

There are also well-behaved rtsp streams that VLC can play without the plugin.

Examples from **wnyc.org**:-
```
rtsp://wnyc-3gp.streamguys.com/wnycfm/wnycfm.sdp
rtsp://wnyc-3gp.streamguys.com/wqxr/wqxr.sdp
rtsp://wnyc-wowza.streamguys.com/js-stream/js-stream.stream
```

---

### Post by andrew.46 on 2014-03-05
Thanks for that ron998, I have added *--enable-realrtsp* into the vlc-git section. I will double check the release version section on the weekend:

```

andrew@corinth:~$**[COLOR="#FF0000"] cvlc --list | grep real[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision 37efc23)
  real                   Real demuxer
  access_realrtsp        Real RTSP

```

I continue to wrestle with x265 offline with no great success. The revised syntax for a local copy of x265, without the cli encoder is now:

```

cd $HOME/vlc_build && \
wget https://bitbucket.org/multicoreware/x265/get/0.8.tar.bz2 -O \
x265-0.8.tar.bz2 && tar xvf x265-0.8.tar.bz2 && \
cd multicoreware-x265-527d03c56d68 && \
mkdir -v build1 && cd build1 && \
cmake -DCMAKE_INSTALL_PREFIX:PATH=$HOME/vlc_build/vlcdeps/usr \
-DENABLE_CLI:BOOL=OFF -DENABLE_SHARED:BOOL=OFF ../source \
&& make -j 2 && make install && \
rm -rfv $HOME/vlc_build/multicoreware-x265-527d03c56d68/build1

```

with a neat removal:

```

rm -v $HOME/vlc_build/vlcdeps/usr/include/x265* && \
rm -v $HOME/vlc_build/vlcdeps/usr/lib/libx265.a && \
rm -v $HOME/vlc_build/vlcdeps/usr/lib/pkgconfig/x265.pc && \
rm -rfv $HOME/vlc_build/multicoreware-x265-527d03c56d68 && \
rm -v $HOME/vlc_build/x265-0.8.tar.bz2

```

Still breaks vlc compile though, I should be more patient :)

---

### Post by FakeOutdoorsman on 2014-03-05
> **andrew.46 said:**
> Still breaks vlc compile though, I should be more patient :)

Same with FFmpeg. More upstream API changes I guess, and the libx265 wrapper in FFmpeg hasn't caught up...not that I think x265 is really worth using yet.

---

### Post by andrew.46 on 2014-03-06
> **FakeOutdoorsman said:**
> ...not that I think x265 is really worth using yet.

It perhaps is worth a look at from the x265 commandline itself, I will admit that I am a little caught in the excitement of watching x265 slowly grow :). And I would like to get it working with vlc...

---

### Post by andrew.46 on 2014-03-06
> **FakeOutdoorsman said:**
> [...] More upstream API changes I guess, and the libx265 wrapper in FFmpeg hasn't caught up...

Looks like FFmpeg has [caught up ]("http://git.videolan.org/?p=ffmpeg.git;a=commit;h=69ead9af7519796eebbc452fbbdb43af8d846173")and all compiles nicely now. The vlc developers not quite so swift...

---

### Post by andrew.46 on 2014-03-07
There is nothing like the sweet taste of victory:

```

andrew@corinth:~/Desktop$ mediainfo test.mp4 
General
Complete name                            : test.mp4
Format                                   : MPEG-4
Format profile                           : Base Media
Codec ID                                 : isom
File size                                : 6.58 MiB
Duration                                 : 3mn 33s
Overall bit rate mode                    : Variable
Overall bit rate                         : 259 Kbps
Encoded date                             : UTC 2014-03-08 02:20:53
Tagged date                              : UTC 2014-03-08 02:20:53
**[COLOR="#FF0000"]Writing application                      : vlc 2.2.0-git stream output[/COLOR]**
Comment                                  : QuickTime 6.0 or greater

Video
ID                                       : 2
**[COLOR="#FF0000"]Format                                   : HEVC[/COLOR]**
Format/Info                              : High Efficiency Video Coding
Format profile                           : Main@L6.0
Codec ID                                 : hvc1
Codec ID/Info                            : High Efficiency Video Coding
Duration                                 : 3mn 32s
Source duration                          : 3mn 32s
Bit rate                                 : 124 Kbps
Width                                    : 320 pixels
Height                                   : 258 pixels
Original height                          : 240 pixels
Display aspect ratio                     : 5:4
Frame rate mode                          : Constant
Frame rate                               : 30.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Bits/(Pixel*Frame)                       : 0.050
Stream size                              : 3.15 MiB (48%)
Source stream size                       : 3.15 MiB (48%)
Language                                 : English
Encoded date                             : UTC 2014-03-08 02:20:53
Tagged date                              : UTC 2014-03-08 02:20:53
mdhd_Duration                            : 212931

Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 3mn 33s
Source duration                          : 3mn 33s
Bit rate mode                            : Variable
Bit rate                                 : 128 Kbps
Maximum bit rate                         : 2 906 Kbps
Channel count                            : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 3.25 MiB (49%)
Source stream size                       : 3.25 MiB (49%)
Language                                 : English
Encoded date                             : UTC 2014-03-08 02:20:53
Tagged date                              : UTC 2014-03-08 02:20:53
mdhd_Duration                            : 213115

```

It will take a little time to write it all up but hevc encoding from the vlc-git is successful :). Mind you vlc does not even like playing the mp4 container it produces, a little happier with an mkv container. So still early days.... All plays back perfectly with MPlayer.

---

### Post by andrew.46 on 2014-03-08
Weekend updates all in:

[LIST=1]
[*]Upgraded the vlc release version to 2.1.4 and added in *--enable-realrtsp*.  No big dramas with this change which runs well enough, I note that Trusty is still running with an older version and I presume will update before release?
[*]Added mercurial back to the build tools, needed to download x265. I confess that I am no hg-master but I am learning...
[*]*System* installation of a specific snapshot of x265. This one was a challenge and stubbornly refused all attempts at a* local* installation which could be used by FFmpeg and vlc. FFmpeg would not link with static libs and and vlc was only happy with shared, system libs. I have left the cli encoder installed for the moment but I suspect that it will go with the next weekend updates. Some debate online about the advisability of using 'date' with an hg update so I will be interested to see how that all pans out.
[*]Updated snapshot for FFmpeg, tailored to the x265 version. I have chosen a very recent version that has had some major hevc updates just added and so far all is well.
[*]Commandline example added for *basic* hevc encoding. Interesting that vlc does not have an mkv muxer! Took a while to find the neatest syntax for guiding the muxer to FFmpeg although without this vlc will *eventually *use the correct muxer. I have found that the best way to extract a commandline is to start vlc with* vlc -vvv*, perform an encoding from the gui and then closely examine the terminal output. Cross-reference with *vlc -H* and then endlessly experiment :).
[*]
[/LIST]

Very exciting to have finally cracked hevc encoding with vlc! Very interesting as well that vlc will not play back its own hevc encoded files in mp4 container, there is an error message in both vlc terminal and MPlayer and I would be interested if others could have a look and see what the issue is. I would like to assemble a decent bug report and take it to vlc forums but the response from there is not always friendly and receptive :). Latest successful compile:

```

andrew@corinth:~$ **[COLOR="#FF0000"]cvlc --version | head -n 2[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision e770901)
VLC version 2.2.0-git Weatherwax (e770901)
Compiled by andrew on corinth (Mar  9 2014 09:03:17)


```

And for the first time I do not have any particular goals for next weekend's updates, so things are looking pretty sorted out at the moment....

---

### Post by ron998 on 2014-03-09
Hi
VLC ./configure couldn't find TIGER.
It's easy enough to compile libtiger-0.3.4 from here ---> [https://code.google.com/p/libtiger/downloads/list](https://code.google.com/p/libtiger/downloads/list)
Then VLC finds it OK. ;)

But is there something in the Ubuntu repos that will do the job instead?

Was libtiger intentionally left out of the Howto, or would it have been pulled in if I had used the big "sudo apt-get -y install ..." command?

---

### Post by andrew.46 on 2014-03-10
> **ron998 said:**
> Was libtiger intentionally left out of the Howto, or would it have been pulled in if I had used the big "sudo apt-get -y install ..." command?

It has been left out as I plaintively try to avoid too much compiling and I though libtiger would not be one that many would want or use. Perhaps it might come in when Trusty is out, the compile instructions will go for libopus as the Trusty version is up to date and this will leave a gap. Looks like fdk-aac compile instructions will remain as the older version remains in Trusty...

**Edit: **Interesting note in #videolan:

```

18:22 -!- 255 nicks totaly - 0 opers, 0 voices and 0 normal
18:22 -!- Home page for #videolan: http://www.videolan.org/
18:22 -!- Join to #videolan was synced in 2 secs
18:22 -!- Topic for #videolan: VideoLAN, VLC and more... | **[COLOR="#FF0000"]44+3bugs to go for 2.2.0[/COLOR]** | David 
          still leads... | www.videolan.org
18:22 -!- Topic set by j-b Fri Mar  7 01:28:33 2014

```

So release not too far away perhaps? BTW I am often on #ubuntuforums if anybody following this thread wants a chat, remember there is no support in this channel...

---

### Post by ron998 on 2014-03-10
Hi
VLC ./configure couldn't find MINIZIP.
This seems to be a compression system that VLC can use if the library's available at build time.

There's some build instructions here ---> [http://slackbuilds.org/slackbuilds/13.37/libraries/libminizip/libminizip.SlackBuild](http://slackbuilds.org/slackbuilds/13.37/libraries/libminizip/libminizip.SlackBuild)

I tweaked them. ;)

But this method looks clumsy:-
```
libtoolize; aclocal; autoconf; automake --add-missing
```

Perhaps it's the way they do things in the alternative universe that is Slackware. :P

> configure:24748: checking for MINIZIP
configure:24755: $PKG_CONFIG --exists --print-errors "minizip "
configure:24758: $? = 0
configure:24772: $PKG_CONFIG --exists --print-errors "minizip "
configure:24775: $? = 0
configure:24877: result: yes

> ron@Xubuntu:~$ cvlc --version
VLC media player 2.1.5 Rincewind (revision ae9e0fd)
VLC version 2.1.5 Rincewind (ae9e0fd)
Compiled by ron on Xubuntu (Mar 11 2014 02:36:38)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-16ubuntu6)

```
# Compile local libminizip.

cd $HOME/vlc_build

curl -L sourceforge.net/projects/libpng/files/zlib/1.2.8/zlib-1.2.8.tar.xz | \
tar -xJ; cd zlib-*/contrib/minizip

libtoolize; aclocal; autoconf; automake --add-missing

CPPFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include" \
LDFLAGS="-L$HOME/vlc_build/vlcdeps/usr/lib" \
PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" \
./configure --prefix=$HOME/vlc_build/vlcdeps/usr --disable-shared

make; make install; cd ../../..

git clone --depth 1 git://git.videolan.org/vlc..........
```

---

### Post by andrew.46 on 2014-03-11
It looks interesting, does vlc use minizip to read media files in zip archives? I am at work at the moment and cannot test this out, I would be particularly interested to see if the vlc build as it is can read such files or whether the addition of minizip would be an enhancement...

---

### Post by ron998 on 2014-03-11
> **andrew.46 said:**
> ... interesting...

Hi
I'm locked out of my Xubuntu now. :oops:
Changed resolution settings and now after login just a blank screen with pointer. :confused:
Booted into different system till I get it fixed..:-k

---

### Post by andrew.46 on 2014-03-11
Mind you I tested a media file in a zip archive and vlc played it fine *without *minizip so I might hold off just for the moment...

---

### Post by qyot27 on 2014-03-11
> **andrew.46 said:**
> [*]*System* installation of a specific snapshot of x265. This one was a challenge and stubbornly refused all attempts at a* local* installation which could be used by FFmpeg and vlc. FFmpeg would not link with static libs and and vlc was only happy with shared, system libs.
FFmpeg's problem with static libs for x265 was something I ran into when doing an extremely minimal build with only a few external libraries.  I never ran into it when linking in all the rest of the external libraries I normally use (when cross-compiling, but this is a moot point).

The reason is that pkg-config isn't being told to use the --static flag, which is something I *did* use with the huge list of external libraries (SDL, libschrödinger, librtmp, and one or two others require it in order to link statically).  libx265 seems to be yet another that needs it.  So at least in the FFmpeg step, getting libx265.a to link in would require:
--pkg-config="pkg-config --static"

Although libav seems to be close to adding a --pkg-config-flags option if the mailing list is any indication, so if FFmpeg pulls that particular change in, it'd probably be --pkg-config-flags="--static" rather than needing to specify it through the option meant for pointing at the binary itself.

---

### Post by andrew.46 on 2014-03-12
Thanks for that qyot, certainly this allows FFmpeg to compile against the static, local, libraries which is the first part of the puzzle! vlc finds and compiles against x265 but will not encode:

```

[00007f84640011c8] **[COLOR="#FF0000"]avcodec encoder error: cannot open hevc video encoder[/COLOR]**
[00007f84640011c8] core encoder error: Streaming / Transcoding failed
[00007f84640011c8] core encoder error: VLC could not open the hevc video encoder.

```

Which is something I hope to battle with on my days off....

---

### Post by andrew.46 on 2014-03-14
Having had a good look at Trusty Tahr it looks like this guide will remain as it is until just after the release on or about April 17th. Looks like a great release coming and one that will be very kind to those of us who enjoy compiling the latest vlc :)

---

### Post by ron998 on 2014-03-15
Hi
minizip gives error:-
```
main libvlc warning: cannot load module `/usr/local/lib/vlc/plugins/access/libzip_plugin.so' (/usr/local/lib/vlc/plugins/access/libzip_plugin.so: undefined symbol: inflate)
```
Maybe it's best to keep this "feature" out of the Howto guide after all.

Also I need to investigate this error now:-
```
main libvlc warning: cannot load module `/usr/local/lib/vlc/plugins/access/liblive555_plugin.so' (/usr/local/lib/vlc/plugins/access/liblive555_plugin.so: undefined symbol: _ZTI10RTSPClient)
```

Tested with xubuntu-14.04-beta1-desktop-i386.

```
@Xubuntu:~$ cvlc --version
VLC media player 2.2.0-git Weatherwax (revision 00f76ba)
VLC version 2.2.0-git Weatherwax (00f76ba)
Compiled by ron on Xubuntu (Mar 16 2014 02:36:49)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-16ubuntu6)
```

---

### Post by andrew.46 on 2014-03-16
Hey Ron!

Were you using live.2014.01.21.tar.gz (sourced from videolan) or the latest version live.2014.03.16.tar.gz (sourced from live555 download page)? I am at work at the moment but I will check my own installation when I get home...

---

### Post by ron998 on 2014-03-16
> **andrew.46 said:**
> ... Were you using live.2014.01.21.tar.gz... 
Hi
I used 2014.03.16.tar.gz from live555.com with ffmpeg-git.
Now rebuilt with 2014.01.21.tar.gz from videolan.com and ffmpeg-61ff043 but the error message still shows. :(

---

### Post by ron998 on 2014-03-16
> **ron998 said:**
> Also I need to investigate this error now:-
```
main libvlc warning: cannot load module `/usr/local/lib/vlc/plugins/access/liblive555_plugin.so' (/usr/local/lib/vlc/plugins/access/liblive555_plugin.so: undefined symbol: _ZTI10RTSPClient)
```
Hi
To help VLC find live555 I had used extra flags...
LIVE555_LIBS="-L$HOME/vlc_build/vlcdeps/usr/lib"
LIVE555_CFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include"

This found live555 OK but failed to register "version 1324598400 or later", so plugin was not compiled correctly. :(
Removed these extra flags and error message has disappeared (using 2014.03.16.tar.gz). :)
My own fault for trying to be too clever. A little knowledge is dangerous. :cool:

By the way, the "**--enable-realrtsp**" option is badly broken.
Google says it can't/won't be fixed.
Probably that's why it's disabled by default.
Maybe best to airbrush this "feature" from the Howto guide.
```
@Xubuntu:~$ cvlc --version
VLC media player 2.2.0-git Weatherwax (revision f952f16)
VLC version 2.2.0-git Weatherwax (f952f16)
Compiled by ron on Xubuntu (Mar 16 2014 21:03:26)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-16ubuntu6)
```

---

### Post by andrew.46 on 2014-03-17
> **ron998 said:**
> Removed these extra flags and error message has disappeared (using 2014.03.16.tar.gz). :)
My own fault for trying to be too clever. A little knowledge is dangerous. :cool:

Good to hear the issue is resolved :). I will probably stay with the older version for the moment simply because the live555 guys remove the archive as soon as it is superceded, and the newer version is not always guaranteed to work with vlc. My own web site is no more and thus I don't have easy access to secure storage either to host my own copy...

> By the way, the "**--enable-realrtsp**" option is badly broken.
Google says it can't/won't be fixed.
Probably that's why it's disabled by default.
Maybe best to airbrush this "feature" from the Howto guide.

My Google powers are no so good and I could not find discussion of this, do you have a link?

---

### Post by ron998 on 2014-03-17
> **andrew.46 said:**
> ... the live555 guys remove the archive as soon as it is superceded...
Some old versions are here ---> [http://download.videolan.org/contrib/live555/](http://download.videolan.org/contrib/live555/)

> **andrew.46 said:**
> ...do you have a link?
It was in trac, but I can't find it now. :mad:

---

### Post by andrew.46 on 2014-03-17
> **ron998 said:**
> Some old versions are here ---> [http://download.videolan.org/contrib/live555/](http://download.videolan.org/contrib/live555/)

Indeed, that is the area used in this guide :)


> It was in trac, but I can't find it now. :mad:

Never mind I will leave the option as it is for the moment and treat it with caution...

---

### Post by andrew103 on 2014-03-17
got some erros at the begining, but after i looked again i mistyped some codes. silly me. great explanation also.

---

### Post by andrew.46 on 2014-03-17
> **andrew103 said:**
> got some erros at the begining, but after i looked again i mistyped some codes. silly me. great explanation also.

Good to hear it all worked out :). Mind you the guide is designed so that if you like a simple set of Copy and Paste commands should see the whole thing working, no typing or mistyping then required!

---

### Post by andrew.46 on 2014-03-18
In a very minor update I have added in some details of how to automagically let mercurial / hg perform a cert check when downloading from multicoreware's x265 repository. Otherwise I will let the guide slumber until Trusty Tahr is release. (Unless something breaks...) Latest successful compile:

```

andrew@corinth:~$ **[COLOR="#FF0000"]cvlc --version | head -n 2[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision 44db86c)
VLC version 2.2.0-git Weatherwax (44db86c)
Compiled by andrew on corinth (Mar 18 2014 18:15:48)

```

---

### Post by andrew.46 on 2014-04-08
Development of the Trusty Tahr version is stalled at the moment with the following consistent error:

```

  GEN      ../modules/plugins.dat
/bin/bash: line 4: 26442 Segmentation fault      (core dumped) ./vlc-cache-gen ../modules
make[2]: *** [../modules/plugins.dat] Error 139

```

Frustrating.....

---

### Post by andrew.46 on 2014-04-08
I have spoken too soon as an Arch post suggested a fix which I have put in place. The guide has been updated and tested for Trusty and all is well. Most outstanding feature is that the guide has lost a* lot* of weight :). Details below:

[LIST=1]
[*]Updated the 'Development' files to suit Trusty. Some work remains here which I will undertake next weekend. A few version names for Trusty and a few files have been dropped.
[*]Removed the fdk-aac commandline examples in the interest of simplifying the guide. I am not convinced that vlc is the best encoder in the world and I suspect there are few that will use the vlc cli. Examples will be given and discussed in the threads leading from the guide for those who are interested.
[*]Again removed x265 compile examples. x265 is working beautifully with FFmpeg at the moment and also as a standalone executable but was eating up too much of my time with vlc so this time it is exiled until some stability with the uneasy partnership of FFmpeg / x265 / vlc has arrived.
[*]Changed FFmpeg to latest release version. In the cause of simplifying the guide.
[*]Removed bluray material, this does not work in Virtual Machine anyway. As far as I am aware bluray does not work under VM and this guide *should *be undertaken under VM so the bluray instructions have gone. I have the syntax backed up if anybody is keen to use it anyway.
[*]Compile instructions for libopus removed as Trusty version is sufficient now. Pretty clear?
[*]Removed skins instructions to keep focus on more central issues of this guide. I dislike skins and this has influenced my decision to remove this section. Some of the skins freeze vlc pretty badly anyway and I for one am not going to sort through them all looking for the good ones :).
[*]No longer compile release version as well, focus is on the development version. In the interest of minimising time spent away from the central business of this guide: building and experimenting with the development version.
[*]Removed libfluidsynth instructions, this may be causing compile segfault. Removing this allowed compile to succeed on my system so out it goes. Not sure how many people seriously need this for midi playback and that sound font was ridiculously big!
[*]
[/LIST]

Latest successful compile:

```

andrew@hellas:~$**[COLOR="#FF0000"] cvlc --version | head -n 2[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision 017fa48)
VLC version 2.2.0-git Weatherwax (017fa48)
Compiled by andrew on hellas (Apr  8 2014 18:08:13)

```

New days for Trusty and this iteration of this guide could do with some testing so feel free to point out any errors or shortcomings :).

---

### Post by andrew.46 on 2014-04-12
Only a quick update this weekend: upgraded the FFmpeg version to 2.2.1. Latest successful compile:

```

andrew@hellas:~$**[COLOR="#FF0000"] cvlc --version | head -n 3[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision 25d5ddb)
VLC version 2.2.0-git Weatherwax (25d5ddb)
Compiled by andrew on hellas (Apr 12 2014 20:21:40)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1)

```

---

### Post by andrew.46 on 2014-04-16
I have temporarily retired my 8 core machine and will be surviving on an old Latitude D520 laptop, good news is that it runs Lubuntu Trusty very nicely on VM. And even better news is that this guide needs no modification at all to run on Lubuntu. Latest successful compile:

```

andrew@hellas:~$ cvlc --version | head -n 3
VLC media player 2.2.0-git Weatherwax (revision 6ceee19)
VLC version 2.2.0-git Weatherwax (6ceee19)
Compiled by andrew on hellas (Apr 16 2014 11:08:41)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1)

```

Mind you compiling vlc on effectively a single core can be a little painful so perhaps this guide will slumber for a while...

---

### Post by deepblue232 on 2014-04-17
Compiled version does not open blu rays for me.
Output in terminal:
[00000000013fa338] core interface error: option bluray-menu does not exist
[00007fabbc003908] core input error: open of `bluray:///dev/sr1' failed

Any ideas?

//Edit: This also happens if i try to open DVDs without menu (with menu it works)
[00007fabbc003908] core input error: open of `dvdsimple:///dev/sr0' failed

---

### Post by andrew.46 on 2014-04-17
Indeed I removed the bluray instructions which require libbluray, libaacs and a keydb.cfg file in the right location. I believe that the repository version of libbluray and libaacs should be sufficient (the -dev files) and the keydb.cfg file is [here]("http://vlc-bluray.whoknowsmy.name/").

I removed the bluray material as this guide is best completed under a virtual machine and I believe that blurays will not run under VM. I could be wrong of course...

---

### Post by deepblue232 on 2014-04-18
It works after just installing libbluray (I use makemkv for aacs). Thank you for this excellent guide! One question left: does the compiled vlc rely on any of the files in the vlc_build folder? If I understand it correctly, vlc uses the local libraries from this folder, so i haven't to compile vlc again e.g. if I updated the x264 libraries - or are they all compiled into the .deb package?

---

### Post by andrew.46 on 2014-04-18
I am away from my Ubuntu installation at the moment but if you run:

```

sudo ldd /usr/local/vlc

```

you should see no linkage to the*local* libraries. (I am not sure, as I don't have access to my Ubuntu build at the moment, if that is actually */usr/local[COLOR="#FF0000"]/bin[/COLOR]/vlc*). Mind you the definitive test would be to rename* $HOME/vlc_build* and see if vlc complains :). Downside is that if you update either FFmpeg or x264 you will have to recompile to use the updated libraries. I am not sure how many people use vlc for transcoding to h.264, I admit that use FFmpeg directly.

Glad the guide has been useful to you, I have a few computer access problems at the moment which will make updating a little difficult for a while but hopefully things will be running again soon. The old laptop I am reduced to at the moment is significantly less than ideal for the job of compiling vlc, on my nice 8 core machine it only takes 10 minutes or so...

---

### Post by andrew.46 on 2014-04-24
Finally have the 8 core beast up and running again, there is a story there for one day :). Anyway just for the record ldd shows a nice slender story:

```

andrew@hellas:~$ **[COLOR="#FF0000"]sudo ldd /usr/local/bin/vlc[/COLOR]**
	linux-vdso.so.1 =>  (0x00007fffeac00000)
	libvlc.so.5 => /usr/local/lib/libvlc.so.5 (0x00007fbe76468000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fbe76248000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fbe76040000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fbe75c78000)
	libvlccore.so.7 => /usr/local/lib/libvlccore.so.7 (0x00007fbe75988000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fbe766a8000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fbe75780000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fbe75478000)
	libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007fbe75230000)


```
Nice and neat, try running that on MPlayer and you will get a screen or three! Anyway not much happening at the vlc head so just the latest successful compile to give an elegant 'bump' to this thread:

```

andrew@hellas:~$ **[COLOR="#FF0000"]cvlc --version | head -n 3[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision 82552e5)
VLC version 2.2.0-git Weatherwax (82552e5)
Compiled by andrew on hellas (Apr 24 2014 19:48:26)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1)
andrew@hellas:~$ 

```

I must say the current version of this guide is looking remakably robust and for the first time I am quite happy with it as it is. Mind you I would like a bit more turbulence at the git end of things to make compiling a bit more challenging :)

---

### Post by monkeybrain20122 on 2014-06-09
Hi,

I have a question about syntax

I am trying to build vlc 2.2-git but encountered the warning "configure: WARNING: Library dvdread > 4.9.0 needed for dvdread was not found"
The highest version available in Ubuntu and Debian is 4.2 So I downloaded the tarball for libdvdread-4.9.9 from videolan and build with 
```
./configure --prefix=$HOME/vlc_build/vlcdeps/usr
```
in keeping with the structure of the build directories in the tutorial.

I then build vlc with
```

CPPFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include"
LDFLAGS="-L$HOME/vlc_build/vlcdeps/usr/lib"  
PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig"

```

But still get the same complaint of not finding dvdread, but if I do instead
```
export CPPFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include" 
export LDFLAGS="-L$HOME/vlc_build/vlcdeps/usr/lib" 
export PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig"

```

Then it found libdvdread. 

It appears that without "export" the build process is not actually using the dependencies in $HOME/vlc_build/vlcdeps 
but the system libraries. Does it make any sense?

I have another question. So in this case it seems that I would need to keep the build directory with libdvdread-4.9.9. I could have installed libdvdread-4.9.9  with checkinstall to replace 4.2, but then since there is no separate libdvdread-4.9.9-dev package the build process would not be able to find it. Is there a more elegant way to handle this? 

Thanks.

---

### Post by mc4man on 2014-06-09
> **monkeybrain20122 said:**
> Hi,

I have another question. So in this case it seems that I would need to keep the build directory with libdvdread-4.9.9. I could have installed libdvdread-4.9.9  with checkinstall to replace 4.2, but then since there is no separate libdvdread-4.9.9-dev package the build process would not be able to find it. Is there a more elegant way to handle this? 

Thanks.

first off it's a warning so it's possible vlc git doesn't absolutely require 4.9?? 
(the latest daily master ppa builds still uses 4.2

If you wanted to use 4.9 (via checkinstall) then headers & includes will be installed
Though in that case consider if there is any reason to re-build dvdnav against the 4.9 dvdread (libdvdnav-dev deps on libdvdread-dev in Debian/Ubuntu

(-  I did a quick test of packaging though haven't outright tested other than a quick play of a dvd with vlc (2.1.5 built off of 4.2) to see if newer lib  breaks read or dvdnav, it doesn't appear to.
What advantage to 4.9 I don't know..

If you want a copy of the 4.9 source with a debian folder let me know

---

### Post by monkeybrain20122 on 2014-06-10
> **mc4man said:**
> first off it's a warning so it's possible vlc git doesn't absolutely require 4.9?? 


It is not necessary, it will build, just that it would complain that dvdread is missing.

> If you wanted to use 4.9 (via checkinstall) then headers & includes will be installed

I have installed libdvdread 4.9  via checkinstall and removed -dev packages. You are right that I don't need the -dev package.  I also rebuided libdvdnav4 from Debain source package [https://packages.debian.org/source/sid/libdvdnav](https://packages.debian.org/source/sid/libdvdnav). Rebuild vlc, now it no longer complains about not finding dvdread. I have just tested with a random dvd and it works. 

Thanks for the pointer.

Doing it this way building vlc is somewhat less tedious. Since I already have ffmpeg-2.2.3 installed in /opt/ffmpeg so I just need to have CPPFLAGS, LDFLAGS and PKG_CONFIG_PATH pointing there instead of some local folder where I install libdvdread ( say $HOME/vlc_build/vlcdeps in Andrew's template) and then have to build ffmpeg there again (well may be I don't have to, but I don't know how otherwise as I don't want to use the system's libav)

> What advantage to 4.9 I don't know.. 

Probably no advantage, it is just that I am not sure if I have full dvd support if I compile vlc 2.2 without dvdread and it requires 4.9.  I had vlc 2.14 and it segfaulted ever so often with VAAPI enabled and some videos appear pixiated, vlc 2.2 seems to fix all these problems

> If you want a copy of the 4.9 source with a debian folder let me know       

Thanks for the kind offer, it is working out very nicely now.

P.S. Where do you get vlc 2.1.5? The latest release I can find is 2.1.4 [http://download.videolan.org/pub/videolan/vlc/](http://download.videolan.org/pub/videolan/vlc/)

---

### Post by mc4man on 2014-06-10
"P.S. Where do you get vlc 2.1.5? The latest release I can find is 2.1.4"
2.1.5 is 2.1.4 + git commits to maintenance (stable
If I find any commits of value then I  take the current source from the stable ppa & upload to the media ppa 
(basically waiting till 2.2 goes stable

Edit: 
It appears that without "export" the build process is not actually using the dependencies in $HOME/vlc_build/vlcdeps
but the system libraries. Does it make any sense?

Vlc (& maybe others?) can do that, that was one of the reasons for adjusting the FFmpeg build method to install includes & headers to somewhere not in normal  paths. ( the guide of choice now uses $HOME/ffmpeg_build

---

### Post by monkeybrain20122 on 2014-06-10
> **mc4man said:**
> 

Vlc (& maybe others?) can do that, that was one of the reasons for adjusting the FFmpeg build method to install includes & headers to somewhere not in normal  paths. ( the guide of choice now uses $HOME/ffmpeg_build

Hi,

This is not what I found. In my first attempt I installed libdvdread-4.9.9 in $HOME/vlc_build/vlcdeps/usr and then build vlc. Without "export" in front of CPPFLAGS, LDFLAGS and PKG-CONFIG-PATH it did not find libdvdread, but with 'export' added it did. So it made a difference. Now since in the guide a local version ffmpeg is installed in the same place and the environment variables are set in the same way but without 'export' I am wondering maybe vlc is actually compiled with system libav instead of the local version of ffmpeg (I remember having an issue compiling vlc 2.1.2 back in Ubuntu 13.04 o get vdpau support, it complained that libavcodecs was not up to date even though I built a local ffmpeg from git following much the same the build structure here, it only worked when I added 'export')

I have since built vlc in a different way (as explained above, export CPPFLAGS etc to /opt/ffmpeg/. to use libav libraries with ffmpeg-2.2.3. and use system libs for libdvdread and everything else) I don't have the old config log to see which version of libav was actually used without 'export' in my first attempt.

---

### Post by qyot27 on 2014-06-11
Based on what it *sounds* like you're saying, the reason 'export' is needed is because setting environment variables as separate steps *before* ever running configure is not supported; configure will rewrite them (and thus you lose their values) unless they've been exported.  The way to get around that is to specify the variables *with* configure, as a single command.

Frankly, it makes little sense to me to try setting [CPP|C|CXX|LD|etc.]FLAGS as 'regular' environment variables, and it doesn't surprise me at all that they don't work that way; they were never intended to work that way.  Those flags are generally specific to the current project in question and should not spill over between multiple projects.  Trying to set them as exported variables is nothing else *except* spillage.  The guide itself issues these as a single command like I just described (it's what those \ are for), not separate ones, and thus configure inherits the FLAGS values in the variables.  *That's* why it doesn't have to use 'export'.

Being paranoid about whether something uses the headers/libs in one directory vs. another is where path order comes in.  PKG_CONFIG_PATH (and PKG_CONFIG_LIBDIR as well, probably - LIBDIR being more strict about where it loads things from, at the risk of breaking other library detection) will load the first occurrence of a project's dev files that appears in their path:
```
PKG_CONFIG_PATH=/opt/ffmpeg/lib/pkgconfig:/usr/local/lib/pkgconfig
```
will use the FFmpeg in /opt rather than the one in /usr/local, in this case.

---

### Post by monkeybrain20122 on 2014-06-11
> **qyot27 said:**
> Based on what it *sounds* like you're saying, the reason 'export' is needed is because setting environment variables as separate steps *before* ever running configure is not supported; configure will rewrite them (and thus you lose their values) unless they've been exported.  The way to get around that is to specify the variables *with* configure, as a single command...

.

I see, this makes sense. But I don't get the part about spillage. There is no spillage with 'export' because it only affects the current terminal session as I understand, close the terminal and they are reset. If you put that in .profile (or .bashrc?) then yes.

Well I suppose some people would use the same terminal session from one project to the next unrelated one, but I always start a new terminal session.

---

### Post by andrew.46 on 2014-06-13
Thanks qyot27 for that great exlanation about the use of environment variables. I have been away but at least temporarily back and I have added in a simple update: moving to the latest release version of Fmpeg. Latest successful compile:

```

andrew@hellas:~$**[COLOR="#FF0000"] cvlc --version | head -n 3[/COLOR]**
VLC media player 2.2.0-git Weatherwax (revision bb9e60e)
VLC version 2.2.0-git Weatherwax (bb9e60e)
Compiled by andrew on hellas (Jun 13 2014 16:04:05)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1)


```

Perhaps with the next FFmpeg version cut from git I will revisit x265 in this guide, x265 is looking pretty solid from the commandline these days...

---

### Post by qyot27 on 2014-06-13
> **monkeybrain20122 said:**
> Well I suppose some people would use the same terminal session from one project to the next unrelated one, but I always start a new terminal session.
This is precisely the scenario I meant by 'spillage'.  Not closing the Terminal session between building each project is common enough (or even the typical approach; restarting the Terminal or constantly opening new tabs after each project would get *really* annoying for something like [this](https://github.com/qyot27/mpv/tree/extra-new/DOCS/crosscompile-mingw-tedious.txt)) that guides and rules of thumb need to account for it.

---

### Post by andrew.46 on 2014-06-14
> **qyot27 said:**
> [...] restarting the Terminal or constantly opening new tabs after each project would get *really* annoying for something like [this](https://github.com/qyot27/mpv/tree/extra-new/DOCS/crosscompile-mingw-tedious.txt)) [...]

And people tell me that* I *make complex guides :)

---

### Post by andrew.46 on 2014-06-15
Last update for a little while. I have updated the live555 libraries and also corrected a mistake I made in the live555 removal instructions. Changed the pkgversion to 3.0.0 now that Vetinari is with us.

```

andrew@hellas:~$ **[COLOR="#FF0000"]cvlc --version | head -n 3[/COLOR]**
VLC media player 3.0.0-git Vetinari (revision 2.2.0-git-4-g5d11e66)
VLC version 3.0.0-git Vetinari (2.2.0-git-4-g5d11e66)
Compiled by andrew on hellas (Jun 15 2014 21:28:19)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1)

```

I am still having fun building the git vlc, I hope others are too :).

---

### Post by qyot27 on 2014-06-15
> **andrew.46 said:**
> And people tell me that* I *make complex guides :)
It actually didn't start out complex; it originally only had the main components and some useful optional dependencies.  But then I decided to challenge myself with getting all those disparate external libraries and whatnot built so that both FFmpeg and mpv could be as fully-featured as possible, and it just metastasized.  The only reason I had to give instructions for each little piece is that there is no reliably uniform repository system on Windows to pull in this stuff, and I did this in a vacuum apart from setups like MXE, winbuilds, or on Windows itself, the appearance of MSys2 (which uses a Windows port of pacman to handle packages).

On the upside, though, it provides a point-of-reference for static toolchains and dependency chains for FFmpeg and mpv, and IMO that element of it is more centrally important than whether it's technically possible to accomplish the same thing with less tedium by using the package management tools others have set up.  64-bit is a sore spot because I don't have any Win64 setups to test on, but it's probably only a matter of time before I get around to doing that too.

---

### Post by monkeybrain20122 on 2014-06-23
Hi,

I have some audio files that I can play with vlc 2.1.x but not with 2.2 or 3.0.0 (latest git). The codecs of these are FFAAC and FFFLAC, I wonder if anyone has an idea about it.
Here are two samples, perhaps someone can have a look. They are a bit big so I can't upload them here. I am sorry for the captcha. Thanks
[http://filecloud.io/m9s1kj3r](http://filecloud.io/m9s1kj3r)

---

### Post by mc4man on 2014-06-23
> **monkeybrain20122 said:**
> Hi,

I have some audio files that I can play with vlc 2.1.x but not with 2.2 or 3.0.0 (latest git). The codecs of these are FFAAC and FFFLAC, I wonder if anyone has an idea about it.
Here are two samples, perhaps someone can have a look. They are a bit big so I can't upload them here. I am sorry for the captcha. Thanks
[http://filecloud.io/m9s1kj3r](http://filecloud.io/m9s1kj3r)
The first one is a Dash audio & it seems vlc > 2.1.x can no longer handle. The other, flac in ogg,  same deal. You could file vlc bugs on Videolan's bug thing or post query's in it's [support forum.]("https://forum.videolan.org/viewtopic.php?f=13&t=120113")

(using ffmpeg with -c:a copy to .m4a or .flac respectively will 'fix' vlc playback

---

### Post by andrew.46 on 2014-06-23
As always MPlayer plays these files flawlessly......

---

### Post by monkeybrain20122 on 2014-06-24
> **mc4man said:**
> The first one is a Dash audio & it seems vlc > 2.1.x can no longer handle. The other, flac in ogg,  same deal. You could file vlc bugs on Videolan's bug thing or post query's in it's [support forum.]("https://forum.videolan.org/viewtopic.php?f=13&t=120113")

(using ffmpeg with -c:a copy to .m4a or .flac respectively will 'fix' vlc playback

Hi, Thanks for looking at it. Will file a bug report there soon.. Have been struggling with the compiz corners again since I posted this so haven't got the time yet. :(

---

### Post by mc4man on 2014-06-24
> **monkeybrain20122 said:**
> Hi, Thanks for looking at it. Will file a bug report there soon.. Have been struggling with the compiz corners again since I posted this so haven't got the time yet. :(

I did post a question re Dash audio  on the videolan forum, no response as of yet

As far as your continuing issues with bindings there could be 3 possible solutions
1. try rotate instead of wall
2. try the latest compiz in a 14.04 install (I have in my personal ppa with a few add. changes or I'll pm you a link to the 'train' ppa - use with discretion..
3. Alter the default(s) to what you want, then if compiz/unity set back it's to what you want.

---

### Post by andrew.46 on 2014-06-27
In a very small update I have bumped the FFmpeg version to 2.2.4, changelog does not show a lot but FFmpeg is the core of vlc so..... Latest successful compile:

```

andrew@hellas:~$ **[COLOR="#FF0000"]cvlc --version | head -n 2[/COLOR]**
VLC media player 3.0.0-git Vetinari (revision 2.2.0-git-101-g8a9ac87)
VLC version 3.0.0-git Vetinari (2.2.0-git-101-g8a9ac87)
Compiled by andrew on hellas (Jun 27 2014 18:15:37)

```

A *very* interesting addition to the vlc-git code base is a patch to add a GStreamer decoder module:

 [PATCH]v4 codec: Add GStreamer based decoder module
[https://mailman.videolan.org/pipermail/vlc-devel/2014-May/097921.html](https://mailman.videolan.org/pipermail/vlc-devel/2014-May/097921.html)

This is something I am definitely going to have a look at, at the very least to see which GStreamer plugins need to be installed. So far the decoding is a little limited:

> 
Codecs currently supported are h264, mpeg4, vp8, mpeg2,
flashvideo, wmv1/2/3, vc1.


but looks like more may be added in the future. Interesting?

---

### Post by andrew.46 on 2014-06-30
In an even smaller update I have renamed *fdk-aac* to *libfdk-aac* where appropriate to avoid confusion with the command line encoder *fdkaac*. I mean how could these 3 names ever be confused!?  :)

---

### Post by neil.renaud on 2014-08-22
Hi,

I tried to use this guide as the current version of vlc won't transcode to AAC audio on my system. Got it all compiled but still doesn't seem to work very well on my system not producing the ts files I'm expecting. As such I'm now trying to do it against one of the vlc stable branches rather than the master. 

However when I do that I get the follwoing error:

checking for AVCODEC... no
configure: error: No package 'libavcodec' found
No package 'libavutil' found. Pass --disable-avcodec to ignore this error.

[FONT=Verdana]I'm pretty sure that package was part of my problem with the vlc from the 14.04 repository. Do I really need this? Also not sure why I didn't get the same error when compiling from master...

Any help much appreciated.[/FONT]

---

### Post by neil.renaud on 2014-08-22
Interestingly - running the ./configure in the vlc master on it's own fails as above but running as a block of commands with the && in seems to work so will try the same for vlc-2.2.

---

### Post by neil.renaud on 2014-08-22
Running the command as a batch works. Tried both master and 2.2 and neither work for my streaming DVB to HLS via a transcode. However 2.1 branch works. Thanks for the guide!

---

### Post by andrew.46 on 2014-08-23
> **neil.renaud said:**
>  Thanks for the guide!

Good to hear that it is still useful, I confess that my Ubuntu work has suffered lately due to other commitments. Looks like a version bump for FFmpeg is due (2.3.3) and I will work on this over the next day or so. Nothing much else leaps out at me from the vlc changelog at the moment anyway...

---

### Post by andrew.46 on 2014-08-30
It has been a while between updates but all builds well in a brand new vm with an updated FFmpeg (2.3.3). Latest successful build is:

```

andrew@corinth:~$[COLOR=#ff0000]** cvlc --version | head -n 2**[/COLOR]
VLC media player 3.0.0-git Vetinari (revision ee78942)
VLC version 3.0.0-git Vetinari (ee78942)
Compiled by andrew on corinth (Aug 30 2014 18:22:15)

```

Work, family and study are keeping me busy but I hope to keep this guide (perhaps my most favoured guide in my long history on these Forums) puttering along.....

---

### Post by andrew.46 on 2014-09-02
And speaking of puttering along: I have updated the Live555 libraries to 2014.07.25. All compiles well here:

```

andrew@corinth:~$[COLOR=#ff0000]** cvlc --version | head -n 2**[/COLOR]
VLC media player 3.0.0-git Vetinari (revision 407756f)
VLC version 3.0.0-git Vetinari (407756f)
Compiled by andrew on corinth (Sep  2 2014 17:58:02)


```

---

### Post by mc4man on 2014-09-04
Have noticed that vlc > 2.1.X now has issues playing http/https files that are h.264 (.mp4 or .mov), wmv seems ok.
A simple test would be to try any generic youtube url (not vevo or any url that get a 403 or has feature=player in url

---

### Post by andrew.46 on 2014-09-05
I have to admit that I no longer report such problems to videolan forums as the response can often be more than a little terse :(.

---

### Post by andrew.46 on 2014-09-06
Looks like x265 works a little more reliably with vlc-git so I have again included instructions to build a 'release' version:

```

andrew@corinth:~$ [COLOR=#ff0000]**x265 --version**[/COLOR]
x265 [info]: HEVC encoder version 1.3
x265 [info]: build info [Linux][GCC 4.8.2][64 bit] 8bpp
x265 [info]: using cpu capabilities: MMX2 SSE2Fast SSSE3 SlowCTZ

```

There is now a gui option available for hevc encoding but this was unreliable for reasons I could not track down but a fairly primitive commandline worked 100% reliably:

```

cvlc -vv input.mp4 --sout \
         "#transcode{vcodec=hevc,vb=1024,scale=Auto,acodec=mp4a,ab=128,channels=2,samplerate=44100}:\
         std{access=file{no-overwrite},mux=mkv,dst='output.mkv'}" \
         vlc://quit

```

although the syntax given here could be tightened up considerably (vcodec for example can be either x265 or hevc, not sure which is most correct...). It would be great if anybody could improve on this and test my build for h.264 encoding with vlc. If following in my steps remember to *recompile* FFmpeg with the required option to enable x265 encoding (--enable-libx265) and test your copy of vlc as follows:

```

andrew@corinth:~$ [COLOR=#ff0000]**cvlc --list | grep -i x265**[/COLOR]
VLC media player 3.0.0-git Vetinari (revision 08c15c3)
  x265                   H.265/HEVC encoder (x265)

```

Latest successful compile is as follows:

```

andrew@corinth:~$[COLOR=#ff0000]** cvlc --version | head -n 3**[/COLOR]
VLC media player 3.0.0-git Vetinari (revision 08c15c3)
VLC version 3.0.0-git Vetinari (08c15c3)
Compiled by andrew on corinth (Sep  6 2014 15:42:55)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1)

```

And remember to 'Have fun!!'...

---

### Post by andrew.46 on 2014-09-13
In a very simple weekend update I have bumped the libdvdcss version to 1.3.0. Latest successful compile:

```

andrew@corinth:~$ [COLOR=#ff0000]**cvlc --version | head -n 3**[/COLOR]
VLC media player 3.0.0-git Vetinari (revision 87466e4)
VLC version 3.0.0-git Vetinari (87466e4)
Compiled by andrew on corinth (Sep 13 2014 16:41:25)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1)

```

Spent a bit of time with the x265 / vlc commandline syntax with no great joy so I shall leave it as is for the moment, simply happy that it is all working nicely as as :).

---

### Post by andrew.46 on 2014-09-22
A slightly late weekend update with an FFmpeg upgrade to 2.4.1. Latest successful compile:

```

andrew@corinth:~$ [COLOR=#ff0000]**cvlc --version | head -n 3**[/COLOR]
VLC media player 3.0.0-git Vetinari (revision e23945f)
VLC version 3.0.0-git Vetinari (e23945f)
Compiled by andrew on corinth (Sep 22 2014 18:29:38)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1)

```

Next weekend I will tighten up the x265 compile and install instructions......

---

### Post by andrew.46 on 2014-09-26
In a big bonus for those who build the development version of vlc I have added instructions to build [the newest video compression technology: daala]("http://xiph.org/daala/") as well as cvlc instructions to produce a working example. I believe that vlc is right at the cutting edge being one of the few, possible the only, application that can encode and playback daala files. Check your copy after compiling with:

```

andrew@corinth:~$ [COLOR=#ff0000]**cvlc -l | grep daala**[/COLOR]
VLC media player 3.0.0-git Vetinari (revision de7040d)
  daala                  Daala video decoder
  daala                  Daala video encoder
  daala                  Daala video packetizer
andrew@corinth:~$ 

```

Latest successful compile:

```

andrew@corinth:~$ [COLOR=#ff0000]**cvlc --version | head -n 2**[/COLOR]
VLC media player 3.0.0-git Vetinari (revision de7040d)
VLC version 3.0.0-git Vetinari (de7040d)
Compiled by andrew on corinth (Sep 26 2014 14:27:03)

```

I get the feeling sometimes that I am alone with this guide but that does not matter, I am still having a great time building and testing the bleeding edge vlc :).

---

### Post by qyot27 on 2014-09-26
I'd been following Daala development casually and doing occasional builds since a year or two ago; I didn't know anybody was considering actually exposing the codec yet in a legit media player because I thought the API was still unstable.  But I just checked on VLC's mailing list, and it appears it was one of the Daala devs who submitted it, with an explanation of why they felt it was relatively safe to do.  So yay, I guess.

Still would have preferred finding a branch for libavcodec/format, so I could test it in mpv, but something is better than nothing.  And this should be a lot more comfortable than the example player in the Daala source is.

---

### Post by andrew.46 on 2014-09-27
I have to confess that I had not heard of daala until I saw it on the vlc.git shortlog :). It will certainly give a reason, (for those who need a reason!!) to build the latest vlc from git...

---

### Post by andrew.46 on 2014-10-03
This weekend update some added instructions for updating the daala source from git, compiling and installing. daala version now 0.0-681-g773c90c. Next project will be to update the guide to the soon-to-be released Utopic Unicorn and I suspect this will actually involve very few changes. Most recent successful compile:

```

andrew@corinth:~/Desktop$ **[COLOR="#FF0000"]cvlc --version | head -n 2[/COLOR]**
VLC media player 3.0.0-git Vetinari (revision a9ac943)
VLC version 3.0.0-git Vetinari (a9ac943)
Compiled by andrew on corinth (Oct  3 2014 13:55:21)

```

I will produce a daala sample file, generated by vlc, soon but I need to set vlc-git on my main partition, it is a little too painful via VM...

---

### Post by andrew.46 on 2014-10-09
Well, the plan *was* to update the guide to Utopic Unicorn this weekend but Utopic does not load in a VM with a display problem that looks like it has been around for a little while. Not all that promising with the release just around the corner; I shall try again at release time and stick with the LTS for the moment....

**Edit: **Looks like VMPlayer gets it running though, not sure why VirtualBox is having such trouble.....

---

### Post by mc4man on 2014-10-10
> **andrew.46 said:**
> Well, the plan *was* to update the guide to Utopic Unicorn this weekend but Utopic does not load in a VM with a display problem that looks like it has been around for a little while. Not all that promising with the release just around the corner; I shall try again at release time and stick with the LTS for the moment....

**Edit: **Looks like VMPlayer gets it running though, not sure why VirtualBox is having such trouble.....
You might consider keeping a post here with 14.04 instructs (if it varies from 14.10/14.10+, personally don't see the point of *using* 14.10
Or possibly I'll copy out & replace my 1st. post here, ect.

---

### Post by andrew.46 on 2014-10-10
> **mc4man said:**
> You might consider keeping a post here with 14.04 instructs (if it varies from 14.10/14.10+, personally don't see the point of *using* 14.10

I will have to think about it. The difficulty getting Utopic running in a VM worried me a little and the short time of official support as well...

---

### Post by andrew.46 on 2014-10-11
@mc4man: As a sidenote I think I read another post where you spoke about *not* running the Utopic Unicorn release and I was curious about your reasons? The only real deal breaker for me and this guide is that I advocate the use of a VM and if Utopic Unicorn won't run in a VirtualBox VM.....

---

### Post by mc4man on 2014-10-11
> **andrew.46 said:**
> @mc4man: As a sidenote I think I read another post where you spoke about *not* running the Utopic Unicorn release and I was curious about your reasons? The only real deal breaker for me and this guide is that I advocate the use of a VM and if Utopic Unicorn won't run in a VirtualBox VM.....
Atm I can't see where ubuntu on the Desktop is heading. There was supposed to be something usable to see in 14.04, never materialized. Now there is an ubuntu next image for 14.10 - currently worthless, can't get past the login screen.

So atm 14.04 with unity7, compiz, ect. is known & at least here provides a very useful Desktop install. 14.10+ isn't & may not be great on the Desktop or may be, currently I've no clue.
Because the interim releases are only 9 months I'm sticking with 14.04 until there is something better to replace with.
14.10 itself provides little improvement over 14.04 in an ubuntu session & most of those improvements can be ported to 14.04
(either targeted [individually]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-prop") or for a [greater audience]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") (or not [so great..]("https://launchpad.net/~mc3man/+archive/ubuntu/testing6")

Anyway - 
on current vlc have noticed this chromecast plugin though it doesn't appear ready for linux? Or if now possible it's something many linux users would like
(my son has it, thinks it's great.

---

### Post by andrew.46 on 2014-10-11
> **mc4man said:**
> Atm I can't see where ubuntu on the Desktop is heading. There was supposed to be something usable to see in 14.04, never materialized. Now there is an ubuntu next image for 14.10 - currently worthless, can't get past the login screen.

This is a worry so close to the release date.

> So atm 14.04 with unity7, compiz, ect. is known & at least here provides a very useful Desktop install. 14.10+ isn't & may not be great on the Desktop or may be, currently I've no clue.
Because the interim releases are only 9 months I'm sticking with 14.04 until there is something better to replace with.

I confess that I do not use Ubuntu for my day to day needs :(. But certainly my experience in VM has shown the LTS to be a pretty reasonable release...

> 14.10 itself provides little improvement over 14.04 in an ubuntu session & most of those improvements can be ported to 14.04
(either targeted [individually]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-prop") or for a [greater audience]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") (or not [so great..]("https://launchpad.net/~mc3man/+archive/ubuntu/testing6")

Your PPAs are proving quite popular I have seen!

> 
on current vlc have noticed this chromecast plugin though it doesn't appear ready for linux? Or if now possible it's something many linux users would like
(my son has it, thinks it's great.

Interesting. I have added in what seem to be the required *-dev *files although I note that the vlc developers have version bumped them beyond Trusty's repositories:

```

sudo apt-get install libprotobuf-dev libprotoc-dev protobuf-compiler protobuf-c-compiler

```

However compilation breaks with this so I have at least temporarily disabled this in the vlc ./configure options until I can see what is going on:

```

protoc --cpp_out=. -I. chromecast/cast_channel.proto
make[4]: *** No rule to make target `chromecast/cast_channel.pb.h', needed by `all'.  Stop.

```

Can you see something I have missed?

---

### Post by mc4man on 2014-10-12
> Can you see something I have missed? 
Not really - I just stumbled on it's potential existence from a failed configure
(- in this case the source would try to enable even if not enabled in the config, so to proceed explicitly disabled it. The fail was on the absence of protoc (protobuf-compiler), so no idea about suitability of 14.04 version

Also haven't seen anything anywhere saying  it's working in linux yet..
I guess one could try protobuf-2.6.x, to that end uploaded a build for trusty, may try tomorrow.

---

### Post by andrew.46 on 2014-10-12
> **mc4man said:**
> Also haven't seen anything anywhere saying  it's working in linux yet.

Not much about daala encoding and vlc either, takes a while for the word to get out I suspect and probably for many it will all be news when there is a release version... I left a message about the makefile error on #videolan just to see if this is any more productive than leaving a message on the vlc Forums....

---

### Post by mc4man on 2014-10-12
I guess it was the protoc version, with
doug@doug-Y510P:~$ protoc --version
libprotoc 2.6.0
the plugin does compile
Maybe sometime next week I'll ck. out if it works in some manner

---

### Post by andrew.46 on 2014-10-12
Thanks for looking at that :). Looks like I will have to write up some compiling instructions for this as even Utopic Unicorn still has 2.5. Another job for next weekend which may slip a little beyond that as I am in the process of wresting control back of my domain name so some website work to do...

---

### Post by mc4man on 2014-10-12
There's also this shine thing (libshine3) though I believe it's generally for tablets/phones ect.

---

### Post by andrew.46 on 2014-10-12
> **mc4man said:**
> There's also this shine thing (libshine3) though I believe it's generally for tablets/phones ect.

That does look interesting and I believe there is a suitable *-dev* library in the Trusty Repository which should make an easy addition on the weekend.

---

### Post by andrew.46 on 2014-10-14
And it looks like the guide will start getting a little more bulky as I note that shine has just had an 'Important rewrite and optimization' for version 3.1.0 which does not appear in Trusty but does in Utopic. A quick and dirty encoding test certainly shows that shine is fast on a device *with *an FPU:
[B]
Shine:
[/B]
```

andrew@ilium~/media/luckynight$**[COLOR="#FF0000"] time shineenc -b 128 luckynight.wav luckynight_a.mp3[/COLOR]**
shineenc (Liquidsoap version)
WAVE PCM Data, stereo 44100Hz 16bit, duration: 00:01:00
MPEG-I layer III, stereo  Psychoacoustic Model: Shine
Bitrate: 128 kbps  De-emphasis: none   Original 
Encoding "luckynight.wav" to "luckynight_a.mp3"
Finished in 00:00:01 (60.0x realtime)

**[COLOR="#FF0000"]real	0m1.056s[/COLOR]**
user	0m1.048s
sys	0m0.007s

```

**Lame:**

```
andrew@ilium~/media/luckynight$ **[COLOR="#FF0000"]time lame -b 128 luckynight.wav luckynight_b.mp3[/COLOR]**
LAME 3.99.5 64bits (http://lame.sf.net)
Using polyphase lowpass filter, transition band: 16538 Hz - 17071 Hz
Encoding luckynight.wav to luckynight_b.mp3
Encoding as 44.1 kHz j-stereo MPEG-1 Layer III (11x) 128 kbps qval=3
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
  2317/2317  (100%)|    0:01/    0:01|    0:01/    0:01|   34.986x|    0:00 
------------------------------------------------------------------------------------------------------------------------
   kbps        LR    MS  %     long switch short %
  128.0        4.3  95.7        97.3   1.5   1.1
Writing LAME Tag...done
ReplayGain: -3.7dB

**[COLOR="#FF0000"]real	0m1.741s[/COLOR]**
user	0m1.737s
sys	0m0.004s
andrew@ilium~/media/luckynight$ 

```

But I do not have the hardware to test on devices *without *an FPU where  gather shine really *shines*!!! Anyway this weekend I will add in details to compile and install the latest....

---

### Post by andrew.46 on 2014-10-17
As I have been sick with the flu this weekends updates are a little early and reasonably comprehensive:

 [LIST=1]
[*] Updated FFmpeg to 2.4.2: A reasonably standard update that caused no problems.
[*] Added shine for mp3 encoding, thanks to mc4man for pointing this one out. vlc insists on 3.0.0 or greater... Trusy has a rather old copy of shine in the reposiories which vlc-git politely rejected so out came the compiler again :). Test your own build with:* cvlc -l | grep shine*
[*] Removed repository protoc/protobuf -dev files and compiled protobuf 2.6.0. Chromecast will only compile with the newer libraries. Usually as the Ubuntu release starts getting older there will be more version problems like this with vlc-git.
[*] Re-enabled chromecast plugin, thanks to mc4man for testing the installation out, works on my system as well, I just need some enterprising person with the appropriate Chromecast dongle to test it all out!
[*] Scattered a few more Virtual Machine warnings, this guide *really* should be used in a VM! This guide is becoming increasingly complex and really, really needs to be followed in a VM dedicated to vlc experimentation alone...
 [/LIST]

Latest successful compile:

```

andrew@corinth:~$**[COLOR="#FF0000"] cvlc --version | head -n 3[/COLOR]**
VLC media player 3.0.0-git Vetinari (revision 32705a0)
VLC version 3.0.0-git Vetinari (32705a0)
Compiled by andrew on corinth (Oct 17 2014 16:36:49)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1)
andrew@corinth:~$ 

```

---

### Post by andrew.46 on 2014-10-20
Tried again to run a daily build of Utopic Unicorn and it failed to install in VM, seems a little odd this close to release. So looks like this guide stays with Trusty Tahr for the moment although I will make a token try with the release version which I believe comes out in a couple of days. I cannot be the only person having this trouble surely..... and I run multiple VMs of Ubuntu, Windows and others with no issues....

**Edit:** The solution for me was to use an odd work-around: when the install fails move to TTY1 (with VirtualBox, Right-Ctrl+F1), then move back to TTY7 (with VirtualBox, Right-Ctrl+F7). Very odd.....

---

### Post by andrew.46 on 2014-11-05
Weekend updates to this guide: x265 updated to 1.4 and FFmpeg updated to 2.4.3. Built a new VM and tested the guide from scratch and all works very, very well :). Latest successful compile:

```

andrew@corinth:~/Desktop$ **[COLOR="#FF0000"]cvlc --version | head -n 3[/COLOR]**
VLC media player 3.0.0-git Vetinari (revision 0005a10)
VLC version 3.0.0-git Vetinari (0005a10)
Compiled by andrew on corinth (Nov  6 2014 09:13:58)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1)
andrew@corinth:~/Desktop$ 

```

Officially giving Utopic a miss with this guide so here goes Trusty for a while longer....

---

### Post by monkeybrain20122 on 2014-11-07
Just compiled vlc-3.0.0 on Ubuntu 14.04, the tray icon has moved to the upper left (I use the upper left as a hot corner for compiz, that doesn't work when vlc's tray icon sits there) Same with vlc-2.0.0-rc1 from nightly build (moreover 2 copies of vlc is open everytime I open the video for the 2.0.0 builds) Something seems to be messed up

---

### Post by andrew.46 on 2014-11-07
Something is indeed wrong with your installation. On my setup the tray icon sits in the top right, not sure what is going on your system I'm afraid... Screenshot attached showing the state of play on my Trusty VM, hopefully you are using a VM as well?

---

### Post by monkeybrain20122 on 2014-11-07
Hi this is my screenshot

---

### Post by andrew.46 on 2014-11-07
Hmmmmm..... I suspect that I will be of no help here. This looks like an issue with your window manager rather than vlc-git itself and my knowledge of such things is pretty poor. Hopefully somebody with more knowledge will comment in this thread.

As a cosmetic workaround the system tray feature can be disabled in the vlc settings: 

Tools --> Preferences --> Interface --> Show Systray Icon

Perhaps this will be enough...

---

### Post by monkeybrain20122 on 2014-11-07
It is strange. I just erased my / partition and restored an image from 2 days ago, did the routine upgrades and then recompiled vlc, it is normal again. There were only two changes in the system in the last two days that I haven't done this time 1) install qt-creator which pulled in a bunch of qt5 libraries 2) update my graphic driver.  One of these may be the culprit, will do more tests after I have cloned the current / partition.

---

### Post by andrew.46 on 2014-11-07
Good to hear vlc is behaving again :).

---

### Post by mc4man on 2014-11-07
Just to note:
On default current Ubuntu it's not a systray icon, it's an indicator provided by/thru sni-qt 
(-and a rather crappy indicator compared to the 'real' systray icon

The real one can be used but sni-qt doesn't support a blacklist so it needs to be removed & for unity the systray needs to be enabled..

---

### Post by monkeybrain20122 on 2014-11-07
I have figured it out. The anomalies are indeed caused by the qt-5 libs (this include vlc 2.2 opening two instances when playing a video) Thanks to Andrew for showing me it is not a vlc problem.

---

### Post by andrew.46 on 2014-11-07
> **monkeybrain20122 said:**
> I have figured it out. The anomalies are indeed caused by the qt-5 libs (this include vlc 2.2 opening two instances when playing a video)

I believe that vlc-git should compile against qt5 although I have not tested this. Might be worth a go though? On my version of Trusty Tahr:

```

andrew@corinth:~$ **[COLOR="#FF0000"]qmake -v[/COLOR]**
QMake version 2.01a[B][COLOR="#FF0000"]
Using Qt version 4.8.6 in /usr/lib/x86_64-linux-gnu[/COLOR][/B]

```

---

### Post by qyot27 on 2014-11-08
> **andrew.46 said:**
> Tried again to run a daily build of Utopic Unicorn and it failed to install in VM, seems a little odd this close to release. So looks like this guide stays with Trusty Tahr for the moment although I will make a token try with the release version which I believe comes out in a couple of days. I cannot be the only person having this trouble surely..... and I run multiple VMs of Ubuntu, Windows and others with no issues....

**Edit:** The solution for me was to use an odd work-around: when the install fails move to TTY1 (with VirtualBox, Right-Ctrl+F1), then move back to TTY7 (with VirtualBox, Right-Ctrl+F7). Very odd.....
Even though the post in question is a couple weeks old, the theme is still being brought up in newer posts, so I'll comment anyway.

It wasn't in a VM, but I had issues installing 14.10 on my actual hardware back when it was released.  The solution I ultimately resorted to was that I let it wait on the time zone page until the hard drive was no longer working (thus all the file copying was probably finished), then finished up the user configuration, and once that was done and the slideshow began, *do not let it cycle all the way through*.  I kept turning it back to the first page whenever it popped over to the second.  Then it installed fine.  This was on 32-bit, 13-year-old hardware, but I used the same tactic to successfully install the 64-bit version to an Athlon64 setup, and the 32-bit to a Virtualbox VM (in which I didn't have a good gauge to when the file copying finished, so I think I let it sit on the time zone page for about 5-10 minutes and just hoped that was enough).  All went fine after that.  I remember having to do this on one or two previous versions in recent memory as well, so I'm certain it's a bug in the installer, but I'm not sure exactly *where* in the installer.

I'd tried falling back to text-mode when it failed and froze up during install the first time, and even though I could restart and have it eject the disc, the installation was corrupted and I had to start over.  So I went with the most paranoid solution possible for the standard desktop images, and it worked that way.

---

### Post by andrew.46 on 2014-11-08
Glad in a way that I am not the only one who experienced a few issues with Utopic :). I have no burning need to run Utopic and I spent too much time with installation issues so for the moment I have deleted all of my Utopic isos... My production work (study, email, web site, media conversions etc) is done on a non-Ubuntu distro anyway so my need for a new Ubuntu distro is never great. Still it was a little frustrating that installation was so difficult on a release version...

---

### Post by andrew.46 on 2014-11-27
Updated x265 to 1.4 and FFmpeg to 2.4.3. Latest successful compile:

```

andrew@corinth:~$ cvlc --version | head -n 2
VLC media player 3.0.0-git Vetinari (revision 90c479c)
VLC version 3.0.0-git Vetinari (90c479c)
Compiled by andrew on corinth (Nov 28 2014 07:54:07)
andrew@corinth:~$ 

```

---

### Post by mc4man on 2014-11-27
> **andrew.46 said:**
> Glad in a way that I am not the only one who experienced a few issues with Utopic :). I have no burning need to run Utopic and I spent too much time with installation issues so for the moment I have deleted all of my Utopic isos... My production work (study, email, web site, media conversions etc) is done on a non-Ubuntu distro anyway so my need for a new Ubuntu distro is never great. Still it was a little frustrating that installation was so difficult on a release version...
It's likely that 15.04 will be more useful/usable. Though again the 9 month life is a bit of an issue (to me
While I'm probably incorrect I view 14.10 less as a 'release' & more as a point in time with a little last min. work on the Desktop..

---

### Post by andrew.46 on 2014-11-27
> **mc4man said:**
> While I'm probably incorrect I view 14.10 less as a 'release' & more as a point in time with a little last min. work on the Desktop..

I certainly share this view. It is a shift in thinking for me because in more ancient days each 6 month Ubuntu release was a genuine release.

---

### Post by andrew.46 on 2014-12-06
Weekend update: upgraded FFmpeg to 2.5 & updated the website mirror. Latest successful compile:

```

andrew@corinth:~$ **[COLOR="#FF0000"]cvlc --version | head -n 3[/COLOR]**
VLC media player 3.0.0-git Vetinari (revision 67066bf)
VLC version 3.0.0-git Vetinari (67066bf)
Compiled by andrew on corinth (Dec  7 2014 10:42:06)
Compiler: gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1)
andrew@corinth:~$ 

```

---

### Post by andrew.46 on 2014-12-13
For this weekend guide I have added in libmpg123-dev to experiment with [the new decoder]("http://git.videolan.org/?p=vlc.git;a=blobdiff;f=modules/MODULES_LIST;h=4916d164d624872b05bc55ef1d303384e964c6c7;hp=bcf837dd83889e6418f1a21373038645d67df161;hb=61f7f3dc630f5cb3573cb648413e1c52d5c81ec2;hpb=575a20f3c2f5ae886a63b27a7e2c9bce7e997075"). Test it is available by running:

```

andrew@corinth:~$ **[COLOR="#FF0000"]vlc -l | grep mpg123 [/COLOR]**
VLC media player 3.0.0-git Vetinari (revision 05c4336)
  mpg123                 MPEG audio decoder using mpg123

```

So it is definitely built but I am still searching in the commandline and gui options to find a place to manually specify this decoder :). The usual suspect *--aout mpg123* seems not to work...

---

### Post by mc4man on 2014-12-13
Been quite some time since I used vlc from cli, how about --codec, maybe --codec mpg123

---

### Post by andrew.46 on 2014-12-13
That would do it :). Finally found it here:

```

 Decoders
 This option can be used to alter the way VLC selects its codecs (decompression methods). 
Only advanced users should alter this option as it can break playback of all your streams.
      --codec <string>           Preferred decoders list
          List of codecs that VLC will use in priority. For instance, 'dummy,a52' will try
          the dummy and a52 codecs before trying the other ones. Only advanced users should
          alter this option as it can break playback of all your streams.

```

---

### Post by mc4man on 2014-12-13
> **andrew.46 said:**
> That would do it :). Finally found it here:

```

 Decoders
 This option can be used to alter the way VLC selects its codecs (decompression methods). 
Only advanced users should alter this option as it can break playback of all your streams.
      --codec <string>           Preferred decoders list
          List of codecs that VLC will use in priority. For instance, 'dummy,a52' will try
          the dummy and a52 codecs before trying the other ones. Only advanced users should
          alter this option as it can break playback of all your streams.

```
Which reminds me that it seemed the limitation was only 1 per stream/file, specifying a codec for either audio or video but not one for each
(- likely rare to want to do that

---

### Post by andrew.46 on 2014-12-13
> **mc4man said:**
> Which reminds me that it seemed the limitation was only 1 per stream/file, specifying a codec for either audio or video but not one for each

It looks a little shotgun style but there is an option in the gui tools, not nearly as intuitive or as useful as MPlayer or FFmpeg. Screenshot attached...

---

### Post by mc4man on 2014-12-13
> **andrew.46 said:**
> It looks a little shotgun style but there is an option in the gui tools, not nearly as intuitive or as useful as MPlayer or FFmpeg. Screenshot attached...
Maybe that's something new?, don't see here in my current vlc 2.2.0~rc1, at least in that section..
(-need to ck. whether 2.2 has progressed, seems to be quite delayed in a release

---

### Post by andrew.46 on 2014-12-13
> **mc4man said:**
> Maybe that's something new?, don't see here in my current vlc 2.2.0~rc1, at least in that section.

Now that is very odd. On Slackware I am running vlc 2.1.5 and the preferred decoder  / encoder option is in there...

**Edit: **Mind you probably easier to edit the $HOME/.config/vlc/vlcrc file where I see:

```

# Preferred decoders list (string)
#codec=

# Preferred encoders list (string)
#encoder=

```

---

### Post by mc4man on 2014-12-13
> **andrew.46 said:**
> Now that is very odd. On Slackware I am running vlc 2.1.5 and the preferred decoder  / encoder option is in there...

**Edit: **Mind you probably easier to edit the $HOME/.config/vlc/vlcrc file where I see:

```

# Preferred decoders list (string)
#codec=

# Preferred encoders list (string)
#encoder=

```

As best I can see the options were removed in 2.2 then returned recently to 3.0
(- i see 2.2 is now up to rc2, maybe 3.0 will Release first.

edit ot - 
I see audacious (think you use?) has pushed out 3.6-alpha1
One notable is it'll be either qt5 or gtk2. Atm they'll offer a gtk3 source for those that really want
(- I'd suspect ubuntu may end up with the gtk3 though really more up to Debian.

---

### Post by andrew.46 on 2014-12-13
> **mc4man said:**
> I see audacious (think you use?) has pushed out 3.6-alpha1
One notable is it'll be either qt5 or gtk2. Atm they'll offer a gtk3 source for those that really want
(- I'd suspect ubuntu may end up with the gtk3 though really more up to Debian.

Indeed I am a keen audacious user :). I read the big thumbs down to gtk 3:

> 
We have switched back to using GTK+ version 2.x by default. It has now been over three years since the release of GTK+ 3.0, and yet the &#8220;legacy&#8221; version of the toolkit provides more features relevant to Audacious, better cross-platform support, a more stable API, and lower memory usage. Audacious can still be built with GTK3 if desired, but we recommend the GTK2 variant for any desktop environment other than GNOME 3.


Interesting times indeed. Slackware -current (which will become Slackware 14.2 or 15.0 in the new year) is still stuck on qt 4.8.6 although I see [a buildscript for qt 5]("http://slackbuilds.org/repository/14.1/libraries/qt5/") which might be worth a spin on the release version 14.1 which I am running...

---

### Post by mc4man on 2014-12-13
I mis-stated that
currently by default builds with gtk2 (looks fine here) & qt interface can be added. Or one could just enable qt & disable gtk2 but qt isn't really ready so better to do the former.

edit: fooling around with both the qt & gtk2 interfaces gtk2 is *currently* much better on ubuntu

---

### Post by andrew.46 on 2014-12-14
> **mc4man said:**
> edit: fooling around with both the qt & gtk2 interfaces gtk2 is *currently* much better on ubuntu

Mind you my daily desktop is Fluxbox so gtk or qt tends to look equally ugly :). As a further sidenote I see that MKVtoolnix is moving to qt over the next few versions...

---

### Post by mc4man on 2014-12-28
I think as time goes on this guide will have good value, even with the return of ffmpeg to some degree.
It seems that vlc has chosen to base off of libav so there will certainly times when even if ffmpeg-shared is available builds will fail, users would need to use an ffmpeg git statically linked (once vlc inspired commits to libav are merged in FFmpeg.
So in that regard this is a means to that end.

(- current example would be some vlc vdpau changes where the code will vary depending on libavcodec minor version. So while currently libav11 or so and ffmpeg 2.5.x or so are @ 56 the minor version is way different.  
ex.  - 
libavcodec    56.  1. 0  vs  56. 13.100

Seems to me that at some point Debian needs to pick one or the other..

---

### Post by andrew.46 on 2014-12-29
> **mc4man said:**
> I think as time goes on this guide will have good value, even with the return of ffmpeg to some degree.

I worry a little about this guide on these Forums, it seems a little out of step with what most people are after. Hence my placing of the guide [on my website]("http://www.andrews-corner.org/ubuntu/vlc.html") where I am testing if there is more interest from the wider Ubuntu community.

Certainly server logs show about half the number of page views for the vlc guide as opposed to the MPlayer guide but the site has only just been fully reindexed by google and ranking is pretty low, numbers should mature over the next 6 months or so. Some very polite emails thanking me for showing how to build MEncoder which is interesting and I will have to continue this, some have MEncoder in scripts that work well for them and they do not wish to change to FFmpeg.

Greatest ranking, indexing, page views from my abcde page which is also interesting, but not changed since I last had the site online...

---

### Post by poul2 on 2015-02-06
Hello,

I will try bump this thread. 
This VLC developer version working on ubuntu version 14.04 server?

Thanks in advance for time and tutorial.

Tested:

Like always have some problems from first time... No erros shows, but getting "kils"[ATTACH=CONFIG]259752[/ATTACH]

Found and erros -[ATTACH=CONFIG]259753[/ATTACH]

[000000000061ee48] core interface error: no suitable interface module
[0000000000605118] core libvlc error: interface "globalhotkeys,none" initialization failed
[000000000061ee48] core interface debug: looking for interface module matching "dbus,none": 18 candidates
[000000000061ee48] dbus interface error: Failed to connect to the D-Bus session daemon: Unable to autolaunch a dbus-daemon without a $DISPLAY for X11
[000000000061ee48] core interface debug: no interface modules matched
[000000000061ee48] core interface error: no suitable interface module
[0000000000605118] core libvlc error: interface "dbus,none" initialization failed

---

### Post by monkeybrain20122 on 2015-02-06
Don't think it build on 14.0.4. Tried it around Xmas, vlc 3.0.0 requires newer libs (can't remember which ones) than provided by stock Ubuntu. So I build the vlc2.2.0 nightly  instead.

---

### Post by andrew.46 on 2015-11-12
This guide has slowly slipped into a deep sleep but some might be interested to see that work continues in the world away from these forums:

Compile vlc-git under the latest Ubuntu release...
[http://www.andrews-corner.org/ubuntu/vlc.html](http://www.andrews-corner.org/ubuntu/vlc.html)

It has been updated for the Wily Werewolf, I see that this has a scarily modern gcc btw :)

---

### Post by matt_symes on 2015-11-12
> **andrew.46 said:**
> This guide has slowly slipped into a deep sleep but some might be interested to see that work continues in the world away from these forums:

Compile vlc-git under the latest Ubuntu release...
[http://www.andrews-corner.org/ubuntu/vlc.html](http://www.andrews-corner.org/ubuntu/vlc.html)

It has been updated for the Wily Werewolf, I see that this has a scarily modern gcc btw :)

Bookmarked andrew.46 and thank you.

---

### Post by Zekeriya_Akgl on 2016-01-01
when i trying the install vlc-git i get the following errors:
cc1: some warnings being treated as errors
make[4]: *** [codec/libdaala_plugin_la-daala.lo] Error 1
make[4]: *** Waiting for unfinished jobs....
make[4]: Leaving directory `/home/zekeriya/vlc_build/vlc/modules'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/zekeriya/vlc_build/vlc/modules'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/zekeriya/vlc_build/vlc/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/zekeriya/vlc_build/vlc'
make: *** [all] Error 2

---

### Post by andrew.46 on 2016-01-01
This guide has not been worked on for a loooooooooooong time and perhaps should be closed I think. But for the moment simply omit the following from the ./configure string:

```

--enable-daala 

```

The newer version of this guide, which I host on my website, has given up on daala which is just a little too early in its development cycle for my taste :).

---

### Post by andrew.46 on 2016-10-07
The latest git vlc seems to be stuck with an FFmpeg error:

October 3rd, 2016: Unable to compile vlc-git
[https://forum.videolan.org/viewtopic.php?f=13&t=135840](https://forum.videolan.org/viewtopic.php?f=13&t=135840)

This is based on the work here:

Compile vlc-git under the latest Ubuntu release...
[http://www.andrews-corner.org/linux/ubuntu/vlc.html](http://www.andrews-corner.org/linux/ubuntu/vlc.html)

This one has me stumped completely and I would be very interested to hear if anybody has got around this one. Compile still fails for me October 8th. Pastebin output [here...]("http://pastebin.com/1q9H6DGS")

On a side note I am considering bringing the guide back to these forums as a mirror of the website. Just a matter of scripting it to make it a simple enough process...

---

### Post by mc4man on 2016-10-08
Possibly this thread can give you some ground to explore?
[http://stackoverflow.com/questions/38995044/errors-of-vagetdisplay-and-vagetdisplaydrm](http://stackoverflow.com/questions/38995044/errors-of-vagetdisplay-and-vagetdisplaydrm)

(- actually came to this sub-forum to see if anyone had seen value in ffmpeg for nvenc, did you get a chance to checkout?

---

### Post by andrew.46 on 2016-10-08
> **mc4man said:**
> Possibly this thread can give you some ground to explore?
[http://stackoverflow.com/questions/38995044/errors-of-vagetdisplay-and-vagetdisplaydrm](http://stackoverflow.com/questions/38995044/errors-of-vagetdisplay-and-vagetdisplaydrm)

Thanks mc4man I will have a go with this, and in fact the addition of the following to the guide looks quite promising:

```

sed -i_bak 's/Libs: -L${libdir}  -lavutil -lm/\
Libs: -L${libdir}  -lavutil -lm  -lX11 -lm  -lvdpau -lva -lva-drm -lva-x11/' \
~/vlc_build/vlcdeps/usr/lib/pkgconfig/libavutil.pc

```

But I need to test things a little further before publishing...

> (- actually came to this sub-forum to see if anyone had seen value in ffmpeg for nvenc, did you get a chance to checkout?

Not yet but soon. Work etc.... But it is very exciting to have nvenc suddenly arrive in my copy of FFmpeg with no effort on my part :)

---

