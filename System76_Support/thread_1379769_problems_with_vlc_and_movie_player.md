---
title: "problems with vlc and movie player"
date: 2010-01-12
forum: System76 Support
---

### Post by porlaizquierda on 2010-01-12
i try to open vlc and it says that it's opening, but then nothing happens. then when i try to play a dvd with movie player, nothing opens. can anyone lead me in the right direction?

---

### Post by samh785 on 2010-01-12
> **porlaizquierda said:**
> i try to open vlc and it says that it's opening, but then nothing happens. then when i try to play a dvd with movie player, nothing opens. can anyone lead me in the right direction?
run 
```
vlc
```in the terminal and post the output on here.

---

### Post by porlaizquierda on 2010-01-12
right here:

VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
LibVLC fatal error locking mutex in thread 3081086672 at misc/objects.c:395: 130
 Error message: Owner died at:
/usr/lib/libvlccore.so.0(vlc_pthread_fatal+0xb5)[0xb7f53235]
Aborted

---

### Post by thomasaaron on 2010-01-13
> **porlaizquierda said:**
> right here:

VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
LibVLC fatal error locking mutex in thread 3081086672 at misc/objects.c:395: 130
 Error message: Owner died at:
/usr/lib/libvlccore.so.0(vlc_pthread_fatal+0xb5)[0xb7f53235]
Aborted

Are you running from the account you created when you first set up the machine -- or from a subsequently created account?

What version of Ubuntu are you using?

Did you recently upgrade to that version? Or did you do a fresh install of it?

---

### Post by porlaizquierda on 2010-01-13
i'm using a starling netbook and using version 9.04 of ubuntu. i'm running from the account i created when i first set up my computer. i didn't have any problems with vlc or movie player until i did a partial upgrade a couple weeks ago. and i just noticed last night that the dvds were not playing.

---

### Post by porlaizquierda on 2010-01-13
also, on update manager it shows rhythmbox, vlc, and vlc-nox (without X support) but it will not let me click on them. does that have anything to do with my problems playing dvds?

---

### Post by revlimiter on 2010-01-13
Have you tried playing a DVD with totem-xine? This is the only player I've had repeat success with. The totem that comes with Ubuntu (totem-gstreamer?) gives me problems as does VLC.

Totem-xine might be old, but it works on my Karmic system here at work just fine.

---

### Post by thomasaaron on 2010-01-13
OK, the partial upgrade issue most likely is the cause.

Try running these commands...

sudo apt-get install -f
sudo apt-get upgrade
sudo apt-get --assume-yes dist-upgrade
sudo reboot -h now

Did that fix it?

If not, open Synaptic Package Manager and click on Edit > Fix Broken Packages. Take a screenshot of what you see.

EDIT: When you say "partial upgrade" do you mean a partial upDATE? Or do you mean you tried to go to 9.10 and it failed?

---

