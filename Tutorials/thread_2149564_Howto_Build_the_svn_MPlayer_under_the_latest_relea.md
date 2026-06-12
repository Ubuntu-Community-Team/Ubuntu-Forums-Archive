---
title: "Howto: Build the svn MPlayer under the latest release version of Ubuntu"
date: 2013-05-29
forum: Tutorials
---

### Post by andrew.46 on 2013-05-29
This guide details how to install the development version of MPlayer on the latest release version of Ubuntu Linux. It will be periodically updated to cover the latest Ubuntu version in a 'rolling release' fashion. I hope you enjoy this guide and profit by it, feel free to post any problems or discussion in the thread that follows.

[SIZE=4][COLOR=#B22222]**Preparation: 14.04 LTS (Trusty Tahr)...**[/COLOR][/SIZE]

To start with some basic tools are required, and we will also setup our build directory:

```

sudo apt-get -y install build-essential subversion checkinstall yasm \
git docbook-xml docbook-xsl xsltproc libxml2-utils && \
mkdir -pv $HOME/mplayer_build

```

Next a considerable volume of *interlinked* development files are required, the following is a *single* command:

```

sudo apt-get -y install libaa1-dev libasound2-dev libcaca-dev libcdparanoia-dev libdca-dev \
libdirectfb-dev libenca-dev libesd0-dev libfontconfig1-dev libfreetype6-dev \
libfribidi-dev libgif-dev libgl1-mesa-dev libjack-jackd2-dev libopenal-dev libpulse-dev \
libsdl1.2-dev libsvga1-dev libvdpau-dev libxinerama-dev libxv-dev libxvmc-dev libxxf86dga-dev \
libxxf86vm-dev librtmp-dev libsctp-dev libass-dev libfaac-dev libsmbclient-dev libtheora-dev \
libogg-dev libxvidcore-dev libspeex-dev libvpx-dev libschroedinger-dev libdirac-dev libdv4-dev \
libopencore-amrnb-dev libopencore-amrwb-dev libmp3lame-dev libtwolame-dev \
libmad0-dev libgsm1-dev libbs2b-dev liblzo2-dev ladspa-sdk libopenjpeg-dev libfaad-dev \
libmpg123-dev libopus-dev libbluray-dev libaacs-dev libgtk2.0-dev

```

Be a little wary of omitting any of these files as often a single file given here pulls in several more that are essential to a good MPlayer  installation but feel free to add a few if required. With the basics done now we download some files *external* to the Ubuntu repositories:

**Codecs...**

MPlayer benefits from the use of some external codecs and these can be downloaded directly from the MPlayer website. The following is a single command:

```

cd $HOME/mplayer_build && \
sudo mkdir -pv /usr/local/lib/codecs && \
if [ "$(uname -m)" = "x86_64" ]; then
 wget http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-amd64-20071007.tar.bz2
 tar xjvf essential-amd64-20071007.tar.bz2
 sudo cp -v essential-amd64-20071007/* /usr/local/lib/codecs
else
 wget http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20110131.tar.bz2
 tar xjvf all-20110131.tar.bz2
 sudo cp -v all-20110131/* /usr/local/lib/codecs
fi

```

Bear in mind that codecs for 64 bit users are pretty minimal, the real benefits here are for the 32 bit users. There is a continuing drive to bring access to these file formats under the libavcodec umbrella so hopefully one day these codecs will no longer be necessary.

[SIZE=4][COLOR=#B22222]**DVD Playback...**[/COLOR][/SIZE]

The various libraries involved in DVD playback have all moved beyond repository versions and the newest  libdvdcss requires newer libdvdread at least, I will throw in the newest libdvdnav for free :). First remove all of the older libraries:

```

sudo apt-get remove libdvdcss2 libdvdnav-dev libdvdnav4 libdvdread-dev libdvdread4

```

and now install the newer libraries:

**libdvdcss...**

Install the latest libdvdcss with the following single command: 

```

cd $HOME/mplayer_build && \
wget http://download.videolan.org/pub/libdvdcss/1.3.0/libdvdcss-1.3.0.tar.bz2 && \
tar xvf libdvdcss-1.3.0.tar.bz2 && \
cd libdvdcss-1.3.0 && \
./configure --disable-doc \
            --docdir=/usr/share/doc/libdvdcss && make && \
mkdir -vp doc-pak && cp -v AUTHORS ChangeLog COPYING INSTALL NEWS README doc-pak && \
sudo checkinstall --pakdir "$HOME/mplayer_build" --backup=no --deldoc=yes \
                  --pkgname libdvdcss2 --pkgversion "1.3.0" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

**libdvdread...**

Install the latest libdvdread with the following single command:

```

cd $HOME/mplayer_build && \
wget http://www.videolan.org/pub/videolan/libdvdread/5.0.0/libdvdread-5.0.0.tar.bz2 && \
tar xvf libdvdread-5.0.0.tar.bz2 && \
cd libdvdread-5.0.0 && \
./configure && make && \
mkdir -vp doc-pak && cp -v AUTHORS ChangeLog COPYING NEWS README doc-pak && \
sudo checkinstall --pakdir "$HOME/mplayer_build" --backup=no --deldoc=yes \
                  --pkgname libdvdread --pkgversion "5.0.0" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

**libdvdnav...**


Install the latest libdvdnav with the following single command:

```

cd $HOME/mplayer_build && \
wget http://www.videolan.org/pub/videolan/libdvdnav/5.0.1/libdvdnav-5.0.1.tar.bz2 && \
tar xvf libdvdnav-5.0.1.tar.bz2 && \
cd libdvdnav-5.0.1 && \
./configure  && make && \
mkdir -vp doc-pak && cp -v AUTHORS ChangeLog COPYING README TODO doc-pak && \
sudo checkinstall --pakdir "$HOME/mplayer_build" --backup=no --deldoc=yes \
                  --pkgname libdvdnav --pkgversion "5.0.1" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

And now to compile the MPlayer code:

[SIZE=4][COLOR=#B22222]**Compiling MPlayer...**[/COLOR][/SIZE]

Now to finally download and compile the svn MPlayer, bear in mind that you will be asked to also download the FFmpeg git source during this process which you should allow by pressing 'enter' when directed. The following is a single command:

```

cd $HOME/mplayer_build && \
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer && cd mplayer && \
./configure --disable-mencoder --codecsdir=/usr/local/lib/codecs && \
make -j 2 && make html-chunked && \
mkdir -vp doc-pak && \
cp -v DOCS/HTML/*/* AUTHORS Changelog LICENSE README doc-pak && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)" && \
make distclean && sudo ldconfig

```

And this is enough to get you a working copy of the great MPlayer! But it is a good idea to return from time to time and update your installation:

**Updating MPlayer...**

When you wish to update the svn MPlayer, as you definitely should do from time to time, the following single command will suffice:

```

cd $HOME/mplayer_build/mplayer && svn up && \
./configure --disable-mencoder --codecsdir=/usr/local/lib/codecs && \
make -j 2 && make html-chunked && \
mkdir -vp doc-pak && \
cp -v DOCS/HTML/*/* AUTHORS Changelog LICENSE README doc-pak && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)" && \
make distclean && sudo ldconfig

```

[SIZE=4][COLOR=#B22222]**Using a gui...**[/COLOR][/SIZE]

Many will want a gui to use with MPlayer and still the best is SMPlayer, although there is competition around these days! I conquer my usual misgivings about PPAs and give the directions for RVM's PPA:

```

sudo add-apt-repository ppa:rvm/smplayer && \
sudo apt-get update && \
sudo apt-get install smplayer smtube smplayer-themes smplayer-skins 

```

This completes the setup for this guide and I wish you all the best with your continued exploration of this great media player!

[SIZE=4][COLOR=#B22222]**And in conclusion...**[/COLOR][/SIZE]

**Guide updates:**

*** Dec 02:** Added compile instructions for DVD libraries to sort out some incompatibilites.
*** Dec 01:** Added the required libraries (libdvdread & libdvdnav) to allow dvd reading post MPlayer source changes.
*** Oct 11: ** Update for Trusty Tahr, removed MEncoder and GMPlayer, added SMPlayer.

---

### Post by andrew.46 on 2013-05-29
This guide has returned to the Forums, feels good to be back again! I have placed a 301 redirect from its temporary home on my website so there will be no duplication...

---

### Post by andrew.46 on 2013-06-04
This guide no longer includes instructions for SMPlayer but if you are interested perhaps use the developer's PPA:

```

sudo add-apt-repository ppa:rvm/smplayer
sudo apt-get update
sudo apt-get install smplayer smtube smplayer-themes smplayer-skins

```

Most recent MPlayer successful compile:

```

andrew@ithaca:~$ mplayer | head -n 1
MPlayer SVN-r36298-4.7 (C) 2000-2013 MPlayer Team

```

---

### Post by andrew.46 on 2013-06-08
I have added an optional section for the (now) open source speech codec iLBC. I have also placed a sample file:

```

wget http://www.andrews-corner.org/samples/luckynight.lbc

```

I have to thank a certain bat for the inspiration for this one :). MPlayer cannot find the shared library at the moment so this section remains a little broken until I can sort this out...

---

### Post by mc4man on 2013-06-08
> **andrew.46 said:**
> I have added an optional section for the (now) open source speech codec iLBC. I have also placed a sample file:

```

wget http://www.andrews-corner.org/samples/luckynight.lbc

```

I have to thank a certain bat for the inspiration for this one :). MPlayer cannot find the shared library at the moment so this section remains a little broken until I can sort this out...

Where iLBC installs it's libs & what it defines in it's .pc aren't the same, maybe try adjusting one or the other

mplayer would play if started with an env but's that's no 'solution'
ex.
```
:~$ env LD_LIBRARY_PATH=/usr/local/lib/x86_64-linux-gnu   mplayer  /home/doug/luckynight.lbc
Creating config file: /home/doug/.mplayer/config
MPlayer SVN-r36305-4.7 (C) 2000-2013 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/doug/luckynight.lbc.
libavformat version 55.8.102 (internal)
libavformat file format detected.
[ilbc @ 0x7f7e59624c60]max_analyze_duration 5000000 reached at 5000000 microseconds
[ilbc @ 0x7f7e59624c60]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: audio (libilbc), -aid 0
Load subtitles in /home/doug/
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 55.15.100 (internal)
AUDIO: 8000 Hz, 1 ch, s16le, 15.2 kbit/11.87% (ratio: 1900->16000)
Selected audio codec: [libilbc] afm: ffmpeg (FFmpeg libilbc)
...ect.


```
A symlink shows -

```
 
$ ldd /usr/local/bin/mplayer |grep ilbc
	libilbc.so.1 => not found
$ sudo ln -s /usr/local/lib/x86_64-linux-gnu/libilbc.so.1.1.1   /usr/local/lib/libilbc.so.1
$ sudo ldconfig
$ ldd /usr/local/bin/mplayer |grep ilbc
	libilbc.so.1 => /usr/local/lib/libilbc.so.1 (0x00007f4196fc0000)
```

---

### Post by andrew.46 on 2013-06-09
Thanks again mc4man for looking at this! I have carved a little piece of the CMakeLists.txt away which I did not particularly like anyway:

```

cd $HOME/mplayer_build && git clone git://github.com/dekkers/libilbc.git --depth 1 && \
cd $HOME/mplayer_build/libilbc && mkdir build && cd build && \
**[COLOR="#FF0000"]sed -i_bak 's#/${CMAKE_LIBRARY_ARCHITECTURE}##g' ../CMakeLists.txt [/COLOR]**&& \
cmake -DCMAKE_INSTALL_PREFIX=/usr/local .. && make && \
mkdir -vp doc-pak && cp -v ../README doc-pak && \
sudo checkinstall --pakdir "$HOME/mplayer_build" --backup=no --deldoc=yes \
                  --pkgname libilbc --pkgversion "1.1.1-git-$(date +%Y%m%d)" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
sudo ldconfig && cd .. && rm -rf $HOME/mplayer_build/libilbc/build && \
**[COLOR="#FF0000"]mv CMakeLists.txt_bak CMakeLists.txt[/COLOR]**

```

and restored it at the end for the sake of completion. It may not be the most elegant solution but it works well enough on this 32bit VM and I hope also on a 64bit system (I do not have a 64bit VM for MPlayer atm). I will probably revisit this over the next week and neaten things up a little. This is not the greatest CMakeLists.txt file, gave a few issues with 64bit/multilib slackware as well, but it could be that I am not the greatest user of cmake in the Linux world :).

Thanks again for taking the trouble...

---

### Post by mc4man on 2013-06-09
I don't think the .pc matters much, at least with mplayer.  More likely is mplayer doesn't link/search to /usr/local/lib/x86_64-linux-gnu or /usr/local/lib/i386-linux-gnu  because it's not in the default ld search path

So if using cmake if you could just install to /usr then mplayer should find the .so 

ie. - cmake -DCMAKE_INSTALL_PREFIX=/usr

ldd for mplayer
libilbc.so.1 => /usr/lib/x86_64-linux-gnu/libilbc.so.1

Or add  /usr/local/lib/x86_64-linux-gnu or /usr/local/lib/i386-linux-gnu to ld (/etc/ld.so.conf.d/*.conf
The file to add to would depend on arch - ex. on amd64 shown in screen

 ldd for mplayer
	libilbc.so.1 => /usr/local/lib/x86_64-linux-gnu/libilbc.so.1

I guess if wishing to keep with the newer install paths for multiarch then I'd say for guide just use /usr as install prefix


( the .pc could be corrected with this if it mattered in the CMakeLists.txt
set(libdir "\${exec_prefix}/lib/${CMAKE_LIBRARY_ARCHITECTURE}")


The source can also be built from a 'normal' ./configure (autoreconf -fiv then  ./configure), that installs to /lib but oddly names the .so as libilbc.so.0.0.1

---

### Post by andrew.46 on 2013-06-09
Mind you how widespread is the use of multi-arch naming conventions in Ubuntu? The fact that these directories are not searched* by default* seems to me to be a sign that it is very much early days for this.

---

### Post by mc4man on 2013-06-09
> **andrew.46 said:**
> Mind you how widespread is the use of multi-arch naming conventions in Ubuntu? The fact that these directories are not searched* by default* seems to me to be a sign that it is very much early days for this.
It's actually quite common - take a look in /usr/lib/x86_64-linux-gnu or /usr/lib/i386-linux-gnu

So /usr/lib/*-linux-gnu is now default enabled but /usr/local/lib/*-linux-gnu is not (from the distro standpoint no  reason to do so

Most sources/apps that need to do so will find/link to /usr/lib/*-linux-gnu, there was a recent ex. of where one didn't (python-nautilus), that was a case where it was using /usr/lib for i386 & /usr/lib64 for amd64, neither of which were correct. I wrote a couple of patches to fix that, applied to saucy, for 13.04 [a ppa]("https://launchpad.net/~mc3man/+archive/n-p-testfix")

Anyway mplayer links to /usr/lib/*-linux-gnu just fine, can't to /usr/local/lib/*-linux-gnu because it's not 'enabled'

---

### Post by mc4man on 2013-06-09
Did libopenal1 need the -dev? (libopenal-dev

---

### Post by andrew.46 on 2013-06-10
> **mc4man said:**
> Anyway mplayer links to /usr/lib/*-linux-gnu just fine, can't to /usr/local/lib/*-linux-gnu because it's not 'enabled'

Times like this I long for the simplicity and completeness of slackware..... On 3rd thoughts I will remain with the hacked installation that places all of the libs in /usr/local/lib. This works with miminal futzing with Ubuntu's incomplete /etc/ld.so.conf.d/, works with both 32 and 64bit installations and FWIW leaves a technically correct .pc file.

---

### Post by andrew.46 on 2013-06-10
> **mc4man said:**
> Did libopenal1 need the -dev? (libopenal-dev

Does not seem right so I have changed this but not tested, MPlayer compile seems broken at the moment and work calls. I will come back and test...

**Edit: **A vdpau problem, running *--disable-vdpau* is a temporary workaround...

---

### Post by andrew.46 on 2013-06-11
Compile has been fixed with r36330:

[http://lists.mplayerhq.hu/pipermail/mplayer-users/2013-June/086312.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2013-June/086312.html)

---

### Post by mc4man on 2013-06-12
Not sure when started but at least here in all recent **svn** mplayer builds mplayer & mencoder, if built, are seen as - 
shared library (application/x-sharedlib) ( ELF 64-bit LSB shared object
screen 1, in this case used yesterdays export to d. check

Doesn't seem to affect use but seems bothersome. 

on the other hand releases show as normal - 
executable (application/x-executable) (ELF 64-bit LSB executable
screen 2, using recent 1.1.1 release as source

edit; see the same with fedora rpm's, release versions are executable, svn are shared object, so seems par for course though curious

---

### Post by andrew.46 on 2013-06-12
Same for Ubuntu and Slackware here. Seen on Ubuntu:

```

andrew@ithaca:/usr/local/bin$ file --mime-type -b mplayer 
application/x-sharedlib

```

and Slackware:

```

andrew@skamandros/usr/bin$ file --mime-type -b mplayer
application/x-sharedlib

```

whereas of course it should be:

```

andrew@skamandros/usr/bin$ file --mime-type -b slrn
application/x-executable

```

In absence of any *deliberate* change that I can see in the MPlayer svn log I suspect the problem can be at least bypassed with the[ autoprops setting of svn]("http://www.mediawiki.org/wiki/Subversion/auto-props"), but I have no experience with this so some tinkering might be in order. Something odd has happened at the svn repository though...

**Edit:** My brain is a little full after this:

[http://svnbook.red-bean.com/nightly/en/svn.advanced.props.html#svn.advanced.props.auto](http://svnbook.red-bean.com/nightly/en/svn.advanced.props.html#svn.advanced.props.auto)

---

### Post by mc4man on 2013-06-13
Ultimately don't know if this mimetype business matters as mplayer works fine... & while there aren't that many packages using svn mplayer sources to look in did see the same in fedora which appears to use svn for some builds (fusion
(fedora 17 & 18 svns are as expected, 19-dev shows what we see, the motu dailies stopped some time ago so nothing there, ect.

Does though seem to not be  'our', (client?) issue though a test of that isn't quite straightforward.

Did manage without wasting much time to _checkout_  an older svn -r & supply with an ffmpeg version that it could build from, when done it had the mplayer binary as  - 
> ~/mplayer$ file ./mplayer
./mplayer: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24

(r35000 with ffmpeg-0.11 source files inserted in mplayer folder

---

### Post by andrew.46 on 2013-06-13
Very odd, I tried a fresh svn pull with the appropriate autoprops set in $HOME/subversion/config and this made no difference. Puzzling.....

---

### Post by mc4man on 2013-06-17
You may want to check about whether live555 is enabled in 13.04 using the repo package(s). 
( In 13.04 it's now built as shared so 5 or 6 packages.

Here on amd64 it shows in config.log - 
> /tmp/cc4qyfOc.o: In function `main':
tmp.cpp:(.text.startup+0x25): undefined reference to `RTSPClient::createNew(UsageEnvironment&, int, char const*, unsigned short)'
/usr/lib/x86_64-linux-gnu/libBasicUsageEnvironment.so: undefined reference to `operator delete(void*)'
/usr/lib/x86_64-linux-gnu/libBasicUsageEnvironment.so: undefined reference to `operator new[](unsigned long)'
/usr/lib/x86_64-linux-gnu/libBasicUsageEnvironment.so: undefined reference to `__cxa_pure_virtual'
/usr/lib/x86_64-linux-gnu/libBasicUsageEnvironment.so: undefined reference to `operator delete[](void*)'
/usr/lib/x86_64-linux-gnu/libBasicUsageEnvironment.so: undefined reference to `__gxx_personality_v0'
/usr/lib/x86_64-linux-gnu/libBasicUsageEnvironment.so: undefined reference to `vtable for __cxxabiv1::__si_class_type_info'
/usr/lib/x86_64-linux-gnu/libBasicUsageEnvironment.so: undefined reference to `operator new(unsigned long)'
/usr/lib/x86_64-linux-gnu/libBasicUsageEnvironment.so: undefined reference to `vtable for __cxxabiv1::__class_type_info'
collect2: error: ld returned 1 exit status

---

### Post by andrew.46 on 2013-06-17
Getting towards time that live555 was dropped from this guide I am thinking...

---

### Post by mc4man on 2013-06-20
Happened to notice that support isn't enabled & likely not for some time now.
Maybe not needed ? otherwise figure this would have been fixed..(no longer dts.h

---

### Post by andrew.46 on 2013-06-21
So liblivemedia-dev has gone for the time being, I will experiment a little.

The winds have changed a little on these Forums, both this guide and my vlc guide have been very, very quiet which does not match with the large amount of work I have put into them. I am starting to wonder if perhaps such guides are in fact a relic of the days when the media needs of Ubuntu were not particularly well met and in the present day they only really cater for the needs of a small handful of enthusiasts. Hmmmm.....

---

### Post by SeijiSensei on 2013-06-21
Speaking personally, I haven't needed to compile mplayer in about a year now.  The repository version uses mplayer2 which resolves my issues with the original mplayer when it comes to things like Matroska ordered chapters and good support for A** subs.

---

### Post by andrew.46 on 2013-06-21
Indeed..... I have a 2 week break coming up where I will be weighing this and a few other things up...

---

### Post by mc4man on 2013-06-22
> **andrew.46 said:**
> 
The winds have changed a little on these Forums, both this guide and my vlc guide have been very, very quiet which does not match with the large amount of work I have put into them. I am starting to wonder if perhaps such guides are in fact a relic of the days when the media needs of Ubuntu were not particularly well met and in the present day they only really cater for the needs of a small handful of enthusiasts. Hmmmm.....
You know I've felt that for some time now, things progress, get old, whatever.

Here though don't think I'd be using ubuntu without some newer, altered, or repaired packages, so will continue in that regard, at least for a while.
Recently have decided to let LP take care of appropriate sources, do the building, achieving, keeping track ect. Actually is quite convenient. (and certainly more orderly

---

### Post by andrew.46 on 2013-06-22
I have just finished a BA majoring in English Literature so this all reminds me of:

```

The lights begin to twinkle from the rocks:
The long day wanes: the slow moon climbs: the deep
Moans round with many voices. Come, my friends,
'Tis not too late to seek a newer world.
Push off, and sitting well in order smite
The sounding furrows; for my purpose holds
To sail beyond the sunset, and the baths
Of all the western stars.....

```

where the aged Ulysses strikes out one last time :)

---

### Post by randy7 on 2013-11-28
> **andrew.46 said:**
> I have just finished a BA majoring in English Literature so this all reminds me of:

 :)

Hi Andrew,

Just wanted to say, obsolete or not, I just used your guide to install the latest MPlayer from SVN.  Happy to say that everything worked just right.  

Congrats on your BA!

R

---

### Post by gillza on 2013-12-04
Andrew,

Thank you very much for the wonderful guide. I am installing mplayer onto a fresh Mint 16 as I type! 

Thank you!

---

### Post by andrew.46 on 2013-12-07
Thanks for the two posts above :)

---

### Post by digitall.h on 2014-03-02
Hi andrew.46, thank you for your effort in making it easier to have mplayer/mencoder updated.

I'm and old newcomer (I lost my previous account...). Linux Mint KDE 13 installed, Precise Pangolin inside, 64bit.
I know your tuto uses a more recent Ubuntu version. But I tried to use it, and could not compile.
When I execute in terminal:
```
make -j 2
```
I get the following error:
```
libvo/vo_dfbmga.c: In function 'control':
libvo/vo_dfbmga.c:1412:11: error: 'VOCTRL_GUI_NOWINDOW' undeclared (first use in this function)
libvo/vo_dfbmga.c:1412:11: note: each undeclared identifier is reported only once for each function it appears in
libvo/vo_fbdev.c: In function 'vt_set_textarea':
libvo/vo_fbdev.c:760:14: warning: ignoring return value of 'write', declared with attribute warn_unused_result [-Wunused-result]
make: *** [libvo/vo_dfbmga.o] Error 1
```
and exits.
Is this related to an old Ubuntu version?. Can I solve it?
:p

---

### Post by SeijiSensei on 2014-03-02
Is there some reason the stock mplayer binary in the repositories doesn't meet your needs?  It uses the mplayer2 fork and does everything I could ask of it including support for Matroska ordered chapters.  I haven't compiled an mplayer binary in at least a year now, and I use to do so quite regularly after the code fork.

So, what precisely do you need that the current binary release does not contain?

---

### Post by digitall.h on 2014-03-02
(duplicated post)

---

### Post by digitall.h on 2014-03-02
Thank you for your answer SeijiSensei.

My mplayer/mencoder version, from motumedia ppa (now outdated) is 2:1.0 SVN 34707.

Never had a problem, but I'm trying to make a back-up of a Blu-ray (VC-1 format) and I'm trying to apply some light filtering with mencoder and 'frameserve' it to x264.
With this Blu-ray, playback in VLC is O.K. but in mplayer and mencoder it shows strange artefacts.

To my knowledge this may be solved with a more recent version.
That's the reason I would like to update mplayer without having to update/re-install my hole system.

---

### Post by SeijiSensei on 2014-03-02
From what I understand, mencoder has pretty much been deprecated in favor of ffmpeg for most conversion tasks.  Mencoder was originally designed to encode into AVI; we're a long way past that now.  Mencoder is no longer included with the source code in the mplayer2 fork; those guys just gave up on it.

Maybe you should see if ffmpeg is a better long-term solution for you.

---

### Post by digitall.h on 2014-03-02
Probably there was something broken in previous SVN version. Today I managed to successfully update mplayer/mencoder to SVN-r36970-4.6.

Sadly this did not solve my problem. Will try with ffmpeg.

Thank you for your help
:)

---

### Post by andrew.46 on 2014-03-03
> **digitall.h said:**
> Hi andrew.46, thank you for your effort in making it easier to have mplayer/mencoder updated.

I have to admit that I have let this guide slumber for quite some time and there is still a decent chance I may not develop it any longer. I still believe that running the svn MPlayer is the best possible way to get great media playback and continue to update every couple of days but in previous times I spread myself a little too far and I have pulled back a little...

> Is this related to an old Ubuntu version?. Can I solve it?:p

No this is related to a mistake made by one of the MPlayer developers and has been corrected in r36963 :). So just run svn up and resompile, all should be well.

---

### Post by estrella-ed on 2014-07-20
Hello! ;)
Thanks for this tutorial. 
I have a problema when trying to compile mplayer:

Checking for GTK+ version ... GTK+ 2 devel packages were not found, trying GTK+ 1.2 
Checking for GTK+ version ... 
Error: The GUI requires GTK+ devel packages (which were not found).

Check "config.log" if you do not understand why it failed.

Apparently i need gtk+2 dev , but i cannot find anywhere in repository, im on Linux mint 17 qiana kde 64 bits.

Unfortunately the official repository installer generates errors when you install mplayer skins, its a well know error but was not yet resolved.

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510)

So, this force me to have to compile from source mplayer to work correctly.

¿can you please help me?

:(

---

### Post by mc4man on 2014-07-22
> **estrella-ed said:**
> Hello! ;)
Thanks for this tutorial. 
I have a problema when trying to compile mplayer:

Checking for GTK+ version ... GTK+ 2 devel packages were not found, trying GTK+ 1.2 
Checking for GTK+ version ... 
Error: The GUI requires GTK+ devel packages (which were not found).

Check "config.log" if you do not understand why it failed.

Apparently i need gtk+2 dev , but i cannot find anywhere in repository, im on Linux mint 17 qiana kde 64 bits.

Unfortunately the official repository installer generates errors when you install mplayer skins, its a well know error but was not yet resolved.

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510)

So, this force me to have to compile from source mplayer to work correctly.

¿can you please help me?

:(
The package is  libgtk2.0-dev

---

### Post by estrella-ed on 2014-07-28
> **mc4man said:**
> The package is  libgtk2.0-dev

Ok the problem is about 




   unsatisfied dependencies.

sudo apt-get install libgtk2.0-dev




             libgtk2.0-dev : Dep: libpango1.0-dev (>= 1.20) but it will not be installed                                                                   
                                  Dep: libcairo2-dev (>= 1.6.4-6.1) but it will not be installed


*linux mint qiana*

---

### Post by SeijiSensei on 2014-07-28
Did you run "sudo apt-get update" before running "sudo apt-get install"?

---

### Post by mc4man on 2014-07-28
> **estrella-ed said:**
> 

Unfortunately the official repository installer generates errors when you install mplayer skins, its a well know error but was not yet resolved.

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1218510)

So, this force me to have to compile from source mplayer to work correctly.

:(
The bug report does contain some workarounds though in the end a newer mplayer will serve you better.  The odds of that bug being fixed are slim to none as I *believe* Debian is dropping mplayer altogether

---

### Post by monkeybrain20122 on 2014-07-28
> **mc4man said:**
>   The odds of that bug being fixed are slim to none as I *believe* Debian is dropping mplayer altogether

Really?? What do they have to replace it if they drop mplayer? It is one of the best Linux media players.

---

### Post by andrew.46 on 2014-07-29
I come out of retirement to post the grisly details here:

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=732159#112](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=732159#112)

Beyond sad to see this when you think what MPlayer has meant to Linux over the years.....

---

### Post by FakeOutdoorsman on 2014-07-29
Andreas Cadhalpun is working on getting FFmpeg back into Debian. When, or if, he is successful then MPlayer returning would probably be likely I'm guessing.

---

### Post by mc4man on 2014-07-31
> **FakeOutdoorsman said:**
> Andreas Cadhalpun is working on getting FFmpeg back into Debian. When, or if, he is successful then MPlayer returning would probably be likely I'm guessing.
I noticed that the latest vlc build via Debian sid now allows either libav or ffmpeg. I'd assume ffmpeg will be configured to use a suffix, like  libavcodecXX-ffmpeg,  ect. That way, with a little care,  both sets of libs could coexist.

So if that all works out it would seem logical mplayer could be returned though not a given.

---

### Post by CyborgAlpha on 2014-08-16
I've been talking to him on the Debian mailing list {729203@bugs.debian.org}. He, I, and several others are working on making FFmpeg & MPlayer interoperable on Ubuntu. I'm stuck on building a test bench for the project.

I don't think there needs to be a separation from Debian/Ubuntu (creating yet another flavor of linux) , but we do need a group of people willing to resolve differences and keep Debian/Ubuntu open!

---

### Post by mc4man on 2014-10-10
Well I see FFmpeg has made it back into Debian (sid) so that may allow the return of mplayer
(- the ffmpeg build seems to have a lot enabled but appears woefully incomplete regarding aac encoding.

---

### Post by andrew.46 on 2014-10-11
I still shake my head at the mindset that would drop an application like MPlayer....

---

### Post by andrew.46 on 2014-10-11
Perhaps some reason still to compile MPlayer under Ubuntu: I have made a few edits and tested an update for Trusty Tahr. The guide will need more than a little fine tuning but seems solid enough for the moment..... Latest successful compile:

```

andrew@corinth:~/Desktop$**[COLOR="#FF0000"] mplayer | head -n 1[/COLOR]**
MPlayer SVN-r37293-4.8 (C) 2000-2014 MPlayer Team
andrew@corinth:~/Desktop$ 

```

---

### Post by cetag on 2014-10-14
Is this the current MPlayer build instructions you are referring to [here]("http://ubuntuforums.org/showthread.php?t=2149564&p=12668354#post12668354") ? 

Unfortunately I found [this one]("https://help.ubuntu.com/community/Compiling%20MPlayer") first, which creates a problematic MPlayer on 14.04. 
 
If you can confirm that first MPlayer build sequence is somewhat current, Andrew, 
then I will attempt to clean up from the older version I used. And will try your version out.

---

### Post by mc4man on 2014-10-14
> **cetag said:**
> Is this the current MPlayer build instructions you are referring to [here]("http://ubuntuforums.org/showthread.php?t=2149564&p=12668354#post12668354") ? 

Unfortunately I found [this one]("https://help.ubuntu.com/community/Compiling%20MPlayer") first, which creates a problematic MPlayer on 14.04. 
 
If you can confirm that first MPlayer build sequence is somewhat current, Andrew, 
then I will attempt to clean up from the older version I used. And will try your version out.
The one at the top of this thread is what you'd want to use, the wiki is for 12.10 (should be updated or removed

Shouldn't be that hard to proceed, yasm should show as an update avail. (or just remove it, then start on the proper guide). The contents of your current  ~/mplayer_build folder should be deleted 1st also

---

### Post by andrew.46 on 2014-10-14
> **cetag said:**
> Is this the current MPlayer build instructions you are referring to [here]("http://ubuntuforums.org/showthread.php?t=2149564&p=12668354#post12668354") ? 

Unfortunately I found [this one]("https://help.ubuntu.com/community/Compiling%20MPlayer") first, which creates a problematic MPlayer on 14.04. 

As mc4man has pointed out *this* guide is the appropriate one for Trusty. The wiki is an aged experiment with moving the tutorials from this Forum to the Ubuntu wiki. (You will note that the wiki page was actually my work and was intended for an older version of Ubuntu.)

> If you can confirm that first MPlayer build sequence is somewhat current, Andrew, 
then I will attempt to clean up from the older version I used. And will try your version out.

Sounds good, feel free to use material from this Forum guide to update the wiki one :). This Forums guide was compiled and installed on a fresh version of Trusty only a week ago and worked fine...

---

### Post by cetag on 2014-10-15
Thanks for confirming that. Great. 
 
Yes, OK.  Will delete ~/mplayer_build folder, and other associated stuff where possible.
Then will take it from the top.


Edit:   No errors and a good result from the build. Thank you.

---

### Post by andrew.46 on 2014-10-15
Note a couple if changes from the wiki:

[LIST=1]
[*]MEncoder is not built
[*]GMPlayer is not built
[*]GMPlayer skins are not sourced
[*]
[/LIST]

A little more streamlined than the wiki pages :)

---

### Post by andrew.46 on 2014-10-16
There has been a query elsewhere on these Forums about the GMP4 codec (GeoVision Advanced MPEG-4) used in many surveillance cameras. A test file can be downloaded here:

```

wget samples.mplayerhq.hu/V-codecs/GMP4/clip7.avi

```

It plays nicely on a 32bit MPlayer using the external codec *GXAMP4.dll *:

```

andrew@ilium~$ **[COLOR="#FF0000"]mplayer clip7.avi [/COLOR]**
MPlayer SVN-r37294-4.8.2 (C) 2000-2014 MPlayer Team

Playing clip7.avi.
libavformat version 56.9.100 (internal)
AVI file format detected.
[aviheader] Video stream found, -vid 0
AVI: No audio stream found -> no sound.
VIDEO:  [GMP4]  320x240  24bpp  30.000 fps  151.3 kbps (18.5 kbyte/s)
Load subtitles in ./
==========================================================================
Opening video decoder: [vfw] Win32/VfW video codecs
**[COLOR="#FF0000"]Loading codec DLL: 'GXAMP4.dll'[/COLOR]**
Loaded DLL driver GXAMP4.dll at 10000000
[PP] Using codec's postprocessing, max q = 9.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Opening video filter: [flip]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xf76d52e0]bicubic scaler, from bgr24 to yuv420p using MMXEXT
[swscaler @ 0xf76d52e0]using unscaled bgr24 -> yuv420p special converter
VO: [xv] 320x240 => 320x240 Planar YV12 
**[COLOR="#FF0000"]Selected video codec: [geomp4] vfm: vfw (GeoVision Advanced MPEG-4)[/COLOR]**
==========================================================================
Audio: no sound
Starting playback...
V:  22.7 682/682  0%  0%  0.0% 0 0 


Exiting... (End of file)

```

I attach a screenshot of the admittedly unexciting video in progress :), As a sidenote I have to admit that I tested this on a 64bit (multi-lib) Slackware installation and I saw how easy it is to install a 32bit MPlayer on a 64bit system, I am not sure if it is a bigger undertaking on a 64bit Ubuntu install....

---

### Post by lemel on 2014-10-31
Hi, I had an error while installing mplayer following the steps in the guide. I received the following error
```
//usr/lib/x86_64-linux-gnu/libvorbis.so.0: undefined reference to `__exp_finite@GLIBC_2.15'//usr/lib/x86_64-linux-gnu/libvorbis.so.0: undefined reference to `__acosf_finite@GLIBC_2.15'
/usr/lib/x86_64-linux-gnu/libpulse.so: undefined reference to `__pow_finite@GLIBC_2.15'
//usr/lib/x86_64-linux-gnu/libvorbis.so.0: undefined reference to `__log_finite@GLIBC_2.15'
/usr/lib/x86_64-linux-gnu/libpulse.so: undefined reference to `__log10_finite@GLIBC_2.15'
collect2: error: ld returned 1 exit status
make: *** [mplayer] Error 1

```

I'm not sure what's the error.
My machine is Ubuntu 14.04 64bits

[ATTACH]257651[/ATTACH]

---

### Post by andrew.46 on 2014-11-01
Seems odd, I have just built MPlayer from scratch, also on 64bit, and did not see that error. Could you confirm the version that you are working with:

```

cd $HOME/mplayer_build/mplayer/ && svn info

```

Current version should give:

```

andrew@corinth:~/mplayer_build/mplayer$ **[COLOR="#FF0000"]svn info[/COLOR]**
Path: .
Working Copy Root Path: /home/andrew/mplayer_build/mplayer
URL: svn://svn.mplayerhq.hu/mplayer/trunk
Relative URL: ^/trunk
Repository Root: svn://svn.mplayerhq.hu/mplayer
Repository UUID: b3059339-0415-0410-9bf9-f77b7e298cf2
**[COLOR="#FF0000"]Revision: 37315[/COLOR]**
Node Kind: directory
Schedule: normal
Last Changed Author: michael
Last Changed Rev: 37315
Last Changed Date: 2014-10-29 13:37:46 +1100 (Wed, 29 Oct 2014)

andrew@corinth:~/mplayer_build/mplayer$ 

```

---

### Post by mc4man on 2014-11-01
> **lemel said:**
> Hi, I had an error while installing mplayer following the steps in the guide. I received the following error
```
//usr/lib/x86_64-linux-gnu/libvorbis.so.0: undefined reference to `__exp_finite@GLIBC_2.15'//usr/lib/x86_64-linux-gnu/libvorbis.so.0: undefined reference to `__acosf_finite@GLIBC_2.15'
/usr/lib/x86_64-linux-gnu/libpulse.so: undefined reference to `__pow_finite@GLIBC_2.15'
//usr/lib/x86_64-linux-gnu/libvorbis.so.0: undefined reference to `__log_finite@GLIBC_2.15'
/usr/lib/x86_64-linux-gnu/libpulse.so: undefined reference to `__log10_finite@GLIBC_2.15'
collect2: error: ld returned 1 exit status
make: *** [mplayer] Error 1

```

I'm not sure what's the error.
My machine is Ubuntu 14.04 64bits
]

What do these return?
```
locate  libm.so
```
```
ldd  /usr/lib/x86_64-linux-gnu/libvorbis.so.0


``````

ldd  /usr/lib/x86_64-linux-gnu/libm.so
```

---

### Post by mc4man on 2014-11-10
Noticed internal libdvd* support & files has been removed. So I gather the -dev's are needed for compiling in.

---

### Post by andrew.46 on 2014-11-11
Thanks for the heads up mc4man, this is tagged onto my weekend list :)

---

### Post by andrew.46 on 2014-12-01
I have added in the required libdvdnav and libdvdread libraries to enable DVD playback post the MPlayer changes. I was *severely* tempted to compile the newer versions available at videolan as the repository versions are quite old but decided to play safe for a while. And this guide is not exactly burning these Forums down anyway so the less complexity the better in the hope of attracting users :)

Latest successful compile:

```

andrew@corinth:~$ mplayer | head -n 1
MPlayer SVN-r37329-4.8 (C) 2000-2014 MPlayer Team
andrew@corinth:~$ 

```

I ran the entire guide on a fresh VM and it all runs very, very smoothly, although some DVD problems. Might need to revisit this...

---

### Post by andrew.46 on 2014-12-11
[Website mirror ]("http://www.andrews-corner.org/ubuntu/mplayer.html")now set in place complete with the iLBC section that has been giving me some grief. Added some 301 magic to catch links to my old MPlayer page. I am not sure at the moment whether the website might be a better home for this guide and its companion vlc guide than these Forums, traffic is so slow on both... might be a bigger audience on andrews-corner perhaps...

---

### Post by codairem on 2014-12-17
Thank you for this hugely helpful guide.  It worked flawlessly.  The 14.04 distribution mplayer has a bug that has been fixed in the source but not in the package yet, so being able to install from source will be important to many people. ([URL="https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1352447Thank"]https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1352447 ) 
[/URL]

---

### Post by andrew.46 on 2014-12-17
Good to hear that is has all worked out, just as I was thinking about moving this guide to a web page only as activity has been so low!
 BTW your link 404s, perhaps this one is better:

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1352447](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/1352447)

---

### Post by the-hand on 2015-05-15
Thank you so much, Andrew, for this guide. Everything went smoothly for me with the exception of the downloads from videolan.org, which I had to do manually - a server message said the files had moved. Anyway, I now have a fully working mplayer with the SM Player front-end with which I am absolutely delighted. As a noob I would have had no chance on my own.  My ageing HTPC machine has an embedded nvidia 9400 gpu (nvidia MCP7A chipset) with a Core 2 Duo, which I am about to upgrade to a faster Core 2 Quad. According to mplayer's FAQ I will need to recompile. Should I just repeat the same procedure from an appropriate point using the existing mplayer_build directory, perhaps using updated files from videolan.org, or do I need to do anything else? Also, I may upgrade to a more recent nvidia card (the 9400 doesn't handle scaling) at some point soon. Would I need to recompile again then?  Thank you, again, for your work on this; it is very much appreciated.

---

### Post by andrew.46 on 2015-05-15
Well really I should apologise for this guide, which is a little unmaintained for a while now! Most recent work has shifted here:

Build the svn MPlayer under the latest Ubuntu release
[http://www.andrews-corner.org/ubuntu/mplayer.html](http://www.andrews-corner.org/ubuntu/mplayer.html)

which now deals with Vivid Vervet. I suspected that the Ubuntu Forums ideological policy of closing quiet threads might have claimed this guide sooner rather than later :).

Rebuilding is always a good idea when newer libraries are installed and there is a section in both the older and newer guides to accommodate this. MPlayer development has slowed dramatically of late but still a good idea to recompile from time to time.

Good news with using rvm's PPA for SMTube is that it now catches the rebuilt version, the old version no longer worked with youtube and the entire program was almost abandoned by the author.

And thanks for finding the guide and finding it useful!!

---

### Post by andrew.46 on 2016-04-04
And now because of a trickle of fan mail an update for Xenial Xerus:

Build the svn MPlayer under the latest Ubuntu release
[http://www.andrews-corner.org/ubuntu/mplayer.html](http://www.andrews-corner.org/ubuntu/mplayer.html)

:)

---

