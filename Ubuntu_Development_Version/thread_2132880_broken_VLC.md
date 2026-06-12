---
title: "broken VLC"
date: 2013-04-06
forum: Ubuntu Development Version
---

### Post by Mr.Carramba on 2013-04-06
After the latest updates the VLC is broken. VLC does not start at all with gui.
in terminal 
```

->vlc -vv
VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
[0x1ee3008] main libvlc debug: VLC media player - 2.0.5 Twoflower
[0x1ee3008] main libvlc debug: Copyright © 1996-2012 VLC authors and VideoLAN
[0x1ee3008] main libvlc debug: revision 2.0.5-0-g1661b7d
[0x1ee3008] main libvlc debug: configured with ./configure  '--enable-static' '--build=x86_64-linux-gnu' 'CFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'CPPFLAGS=-D_FORTIFY_SOURCE=2' 'CXXFLAGS=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' '--config-cache' '--disable-maintainer-mode' '--disable-silent-rules' '--disable-update-check' '--enable-fast-install' '--prefix=/usr' '--docdir=/usr/share/doc/vlc-nox' '--sysconfdir=/etc' '--with-binary-version=2' '--enable-a52' '--enable-aa' '--enable-bluray' '--enable-bonjour' '--enable-caca' '--enable-dbus' '--enable-dca' '--enable-dirac' '--enable-directfb' '--enable-dvbpsi' '--enable-dvdnav' '--enable-faad' '--enable-flac' '--enable-fluidsynth' '--enable-freetype' '--enable-fribidi' '--enable-gnutls' '--enable-jack' '--enable-kate' '--enable-libass' '--enable-libmpeg2' '--enable-libproxy' '--enable-libxml2' '--enable-lirc' '--enable-live555' '--enable-mad' '--enable-mkv' '--enable-mod' '--enable-mpc' '--enable-mtp' '--enable-mux_ogg' '--enable-ncurses' '--enable-notify' '--enable-ogg' '--enable-opus' '--enable-oss' '--enable-pulse' '--enable-qt4' '--enable-realrtsp' '--enable-samplerate' '--enable-schroedinger' '--enable-sdl' '--enable-sftp' '--enable-shout' '--enable-skins2' '--enable-smb' '--enable-speex' '--enable-svg' '--enable-taglib' '--enable-theora' '--enable-twolame' '--enable-upnp' '--enable-vcd' '--enable-vcdx' '--enable-vorbis' '--enable-x264' '--enable-zvbi' '--with-kde-solid=/usr/share/kde4/apps/solid/actions/' '--disable-dxva2' '--disable-gnomevfs' '--disable-goom' '--disable-portaudio' '--disable-projectm' '--disable-sqlite' '--disable-telx' '--enable-alsa' '--enable-atmo' '--enable-dc1394' '--enable-dv' '--enable-fbosd' '--enable-libva' '--enable-linsys' '--enable-omxil' '--enable-pvr' '--enable-udev' '--enable-v4l2' '--enable-crystalhd' '--enable-mmx' '--enable-sse' '--disable-neon' '--disable-altivec' 'build_alias=x86_64-linux-gnu'
[0x1ee3008] main libvlc debug: searching plug-in modules
[0x1ee3008] main libvlc debug: loading plugins cache file /usr/lib/vlc/plugins/plugins.dat
[0x1ee3008] main libvlc debug: recursively browsing `/usr/lib/vlc/plugins'
[0x1ee3008] main libvlc warning: cannot load module `/usr/lib/vlc/plugins/gui/libqt4_plugin.so' (/usr/lib/vlc/plugins/gui/libqt4_plugin.so: undefined symbol: _ZN12QApplication10commitDataER15QSessionManager)
[0x1ee3008] main libvlc debug: saving plugins cache /usr/lib/vlc/plugins/plugins.dat
[0x1ee3008] main libvlc debug: plug-ins loaded: 419 modules
[0x1ee3008] main libvlc debug: opening config file (/home/carra/.config/vlc/vlcrc)
[0x1ee3008] main libvlc debug: translation test: code is "C"
[0x1ee3008] main libvlc debug: CPU has capabilities MMX MMXEXT SSE SSE2 SSE3 SSSE3 SSE4.1 SSE4.2 FPU 
[0x1ee3008] main libvlc debug: looking for memcpy module: 4 candidates
[0x1ee3008] main libvlc debug: using memcpy module "memcpymmxext"
[0x1ef8ca8] main input debug: Creating an input for 'Media Library'
[0x1ef8ca8] main input debug: Input is a meta file: disabling unneeded options
[0x1ef8ca8] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x1ef8ca8] main input debug: `file/xspf-open:///home/carra/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/carra/.local/share/vlc/ml.xspf'
[0x1ef8ca8] main input debug: creating demux: access='file' demux='xspf-open' location='/home/carra/.local/share/vlc/ml.xspf' file='/home/carra/.local/share/vlc/ml.xspf'
[0x1faebe8] main demux debug: looking for access_demux module: 3 candidates
[0x1faebe8] main demux debug: no access_demux module matching "file" could be loaded
[0x1faebe8] main demux debug: TIMER module_need() : 1.491 ms - Total 1.491 ms / 1 intvls (Avg 1.491 ms)
[0x1ef8ca8] main input debug: creating access 'file' location='/home/carra/.local/share/vlc/ml.xspf', path='/home/carra/.local/share/vlc/ml.xspf'
[0x1fafbe8] main access debug: looking for access module: 2 candidates
[0x1fafbe8] filesystem access debug: opening file `/home/carra/.local/share/vlc/ml.xspf'
[0x1fafbe8] main access debug: using access module "filesystem"
[0x1fafbe8] main access debug: TIMER module_need() : 0.546 ms - Total 0.546 ms / 1 intvls (Avg 0.546 ms)
[0x1fb08e8] main stream debug: Using stream method for AStream*
[0x1fb08e8] main stream debug: starting pre-buffering
[0x1fb08e8] main stream debug: received first data after 0 ms
[0x1fb08e8] main stream debug: pre-buffering done 296 bytes in 0s - 5781 KiB/s
[0x1fb0b48] main stream debug: looking for stream_filter module: 7 candidates
[0x1fb0b48] main stream debug: no stream_filter module matching "any" could be loaded
[0x1fb0b48] main stream debug: TIMER module_need() : 1.608 ms - Total 1.608 ms / 1 intvls (Avg 1.608 ms)
[0x1fb0b48] main stream debug: looking for stream_filter module: 1 candidate
[0x1fb0b48] main stream debug: using stream_filter module "stream_filter_record"
[0x1fb0b48] main stream debug: TIMER module_need() : 0.393 ms - Total 0.393 ms / 1 intvls (Avg 0.393 ms)
[0x1ef8ca8] main input debug: creating demux: access='file' demux='xspf-open' location='/home/carra/.local/share/vlc/ml.xspf' file='/home/carra/.local/share/vlc/ml.xspf'
[0x1fb3888] main demux debug: looking for demux module: 1 candidate
[0x1fb3888] playlist demux debug: using XSPF playlist reader
[0x1fb3888] main demux debug: using demux module "playlist"
[0x1fb3888] main demux debug: TIMER module_need() : 0.812 ms - Total 0.812 ms / 1 intvls (Avg 0.812 ms)
[0x1fb4198] main demux meta debug: looking for meta reader module: 2 candidates
[0x1fb4198] lua demux meta debug: Trying Lua scripts in /home/carra/.local/share/vlc/lua/meta/reader
[0x1fb4198] lua demux meta debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
[0x1fb4198] lua demux meta debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
[0x1fb4198] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x1fb4198] main demux meta debug: no meta reader module matching "any" could be loaded
[0x1fb4198] main demux meta debug: TIMER module_need() : 3.721 ms - Total 3.721 ms / 1 intvls (Avg 3.721 ms)
[0x1ef8ca8] main input debug: `file/xspf-open:///home/carra/.local/share/vlc/ml.xspf' successfully opened
[0x1f171c8] main xml reader debug: looking for xml reader module: 1 candidate
[0x1f171c8] main xml reader debug: using xml reader module "xml"
[0x1f171c8] main xml reader debug: TIMER module_need() : 1.355 ms - Total 1.355 ms / 1 intvls (Avg 1.355 ms)
[0x1fb3888] playlist demux debug: parsed 0 tracks successfully
[0x1ef8ca8] main input debug: EOF reached
[0x1fb3888] main demux debug: removing module "playlist"
[0x1fb0b48] main stream debug: removing module "stream_filter_record"
[0x1fafbe8] main access debug: removing module "filesystem"
[0x1ef8ca8] main input debug: TIMER input launching for 'Media Library' : 9.684 ms - Total 9.684 ms / 1 intvls (Avg 9.684 ms)
[0x1fae6f8] main interface debug: looking for interface module: 1 candidate
[0x1fae6f8] main interface debug: using interface module "hotkeys"
[0x1fae6f8] main interface debug: TIMER module_need() : 0.475 ms - Total 0.475 ms / 1 intvls (Avg 0.475 ms)
[0x1faedc8] main interface debug: looking for interface module: 1 candidate
[0x1ef6928] main playlist debug: playlist threads correctly activated
[0x1faedc8] main interface debug: using interface module "inhibit"
[0x1faedc8] main interface debug: TIMER module_need() : 3.926 ms - Total 3.926 ms / 1 intvls (Avg 3.926 ms)
[0x1ef6928] main playlist debug: rebuilding array of current - root Playlist
[0x1ef6928] main playlist debug: rebuild done - 0 items, index -1
[0x1f11c58] main interface debug: looking for interface module: 1 candidate
[0x1f11c58] main interface debug: using interface module "globalhotkeys"
[0x1f11c58] main interface debug: TIMER module_need() : 1.246 ms - Total 1.246 ms / 1 intvls (Avg 1.246 ms)
[0x1ee3008] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x1f13c58] main interface debug: looking for interface module: 5 candidates
[0x1f13c58] skins2 interface debug: EWMH: supported 1
[0x1f13c58] skins2 interface debug: _NET_WM_STATE support: yes
[0x1f13c58] skins2 interface debug: _NET_WM_STATE_FULLSCREEN support: yes
[0x1f13c58] skins2 interface debug: _NET_WM_STATE_STAYS_ON_TOP support: no
[0x1f13c58] skins2 interface debug: _NET_WM_STATE_ABOVE support: yes
[0x1f13c58] skins2 interface debug: _NET_WM_WINDOW_OPACITY support: yes
[0x1f13c58] skins2 interface debug: _NET_WM_PID support: no
[0x1f13c58] main interface error: option qt-volume-complete does not exist
[0x1f13c58] skins2 interface debug: cannot open directory /home/carra/.local/share/vlc/skins2
[0x1f13c58] skins2 interface debug: cannot open directory share/skins2
[0x1f13c58] skins2 interface debug: found skin /usr/share/vlc/skins2/default.vlt
[0x1f13c58] skins2 interface debug: requested skins /usr/share/vlc/skins2/default.vlt is  accessible
[0x7fd1a8024818] main generic debug: looking for dialogs provider module: 0 candidates
[0x7fd1a8024818] main generic debug: no dialogs provider module matched "any"
[0x7fd1a8024818] main generic debug: TIMER module_need() : 0.534 ms - Total 0.534 ms / 1 intvls (Avg 0.534 ms)
[0x1f13c58] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x1f13c58] skins2 interface error: cannot instantiate qt4 dialogs provider
[0x1f13c58] [cli] lua interface debug: Found lua interface script: /usr/lib/vlc/lua/intf/cli.luac
[0x1f13c58] [cli] main interface debug: using interface module "lua"
[0x1f13c58] [cli] main interface debug: TIMER module_need() : 56.520 ms - Total 56.520 ms / 1 intvls (Avg 56.520 ms)
[0x1f13c58] [cli] lua interface: Listening on host "*console".

```
 I have tryed to pure/autoremore and reinstall both VLS and qt, as well as removing .config/vlc, and the rest of suggestions online. Dunno if it is regresion bug which is visible in conenction to 11.04.

As the error sugests
```

x1ee3008] main libvlc warning: cannot load module `/usr/lib/vlc/plugins/gui/libqt4_plugin.so' (/usr/lib/vlc/plugins/gui/libqt4_plugin.so: undefined symbol: _ZN12QApplication10commitDataER15QSessionManager)

```

my system is up to date.

any suggestions for fixing?

---

### Post by LordAshrum on 2013-04-06
I know this sounds simple, but did you redownload it?

---

### Post by mc4man on 2013-04-06
what do these show?
```
ldconfig -p |grep libQtG
```
```
 ldconfig -p |grep libQtC 
```
```
ldd -r /usr/lib/vlc/plugins/gui/libqt4_plugin.so
```

Are you using any ppa's or google earth, maya, or some other third party app  that put qt4 files in /lib or /usr/local ?

---

### Post by Cheesemill on 2013-04-06
Which version of Ubuntu are you running?

---

### Post by Mr.Carramba on 2013-05-17
Sorry for late reply, somehow notification slipped my eyes.

The problem stil exists, I am runing Ubuntu 13.04. I have tryed multiple times to remove and reinstall vlc. I have removed all third party apps and no luck, stil same error and vlc wount start. Really frustrating.

---

### Post by dino99 on 2013-05-17
maybe try the saucy 2.0.6-1, works here on i386     [https://launchpad.net/ubuntu/+source/vlc](https://launchpad.net/ubuntu/+source/vlc)

---

### Post by Mr.Carramba on 2013-05-18
installed from ppa, but got same error

VLC media player 2.1.0-pre1 Rincewind (revision 2.1.0~~git20130518+r2715)
[0x650018] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x67e978] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x67e978] skins2 interface error: cannot instantiate qt4 dialogs provider
[0x67e978] [cli] lua interface: Listening on host "*console".
VLC media player 2.1.0-pre1 Rincewind

---

### Post by Mr.Carramba on 2013-05-18
> **mc4man said:**
> what do these show?
```
ldconfig -p |grep libQtG
```
```
 ldconfig -p |grep libQtC 
```
```
ldd -r /usr/lib/vlc/plugins/gui/libqt4_plugin.so
```

Are you using any ppa's or google earth, maya, or some other third party app  that put qt4 files in /lib or /usr/local ?

```
->ldconfig -p |grep libQtG
    libQtGui.so.4 (libc6,x86-64) => /usr/local/lib/libQtGui.so.4
    libQtGui.so.4 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libQtGui.so.4
    libQtGui.so.4 (libc6) => /usr/lib/i386-linux-gnu/libQtGui.so.4
    libQtGui.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libQtGui.so

```

```
->ldconfig -p |grep libQtG
    libQtGui.so.4 (libc6,x86-64) => /usr/local/lib/libQtGui.so.4
    libQtGui.so.4 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libQtGui.so.4
    libQtGui.so.4 (libc6) => /usr/lib/i386-linux-gnu/libQtGui.so.4
    libQtGui.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libQtGui.so

```

```

->ldd -r /usr/lib/vlc/plugins/gui/libqt4_plugin.so
    linux-vdso.so.1 =>  (0x00007fff837fe000)
    libvlccore.so.5 => /usr/lib/libvlccore.so.5 (0x00007f5f88d45000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f5f88b0a000)
    libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f5f887cf000)
    libQtGui.so.4 => /usr/local/lib/libQtGui.so.4 (0x00007f5f87b01000)
    libQtCore.so.4 => /usr/local/lib/libQtCore.so.4 (0x00007f5f8761b000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f5f87317000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f5f87012000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f5f86c4a000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f5f86a33000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f5f8682b000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f5f86627000)
    libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007f5f863e2000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f5f894af000)
    libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f5f861c4000)
    libgthread-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0 (0x00007f5f85fc1000)
    libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007f5f85cc5000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f5f85aae000)
    libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007f5f85810000)
    libXrender.so.1 => /usr/lib/x86_64-linux-gnu/libXrender.so.1 (0x00007f5f85606000)
    libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007f5f853cc000)
    libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f5f851b9000)
    libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f5f84fb5000)
    libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f5f84dae000)
    libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f5f84b6f000)
    libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007f5f84946000)
undefined symbol: _ZN12QApplication10commitDataER15QSessionManager    (/usr/lib/vlc/plugins/gui/libqt4_plugin.so) 
undefined symbol: _ZN12QApplication9saveStateER15QSessionManager    (/usr/lib/vlc/plugins/gui/libqt4_plugin.so)

```

seems that for some reason libqt4plugin have underfined symbols...

---

### Post by mc4man on 2013-05-18
> **Mr.Carramba said:**
> 
seems that for some reason libqt4plugin have underfined symbols...

What it seems is that you have qt4 libs in /usr/local/lib/ that are incompatible with vlc & being used (/usr/local will trump /usr

> ldconfig -p |grep libQtG
libQtGui.so.4 (libc6,x86-64) => /usr/[COLOR="#FF0000"]local[/COLOR]/lib/libQtGui.so.4

> ldd -r /usr/lib/vlc/plugins/gui/libqt4_plugin.so
libQtGui.so.4 => /usr/[COLOR="#FF0000"]local[/COLOR]/lib/libQtGui.so.4 (0x00007f5f87b01000)
 libQtCore.so.4 => /usr/[COLOR="#FF0000"]local[/COLOR]/lib/libQtCore.so.4 (0x00007f5f8761b000)


They didn't get there by themselves, something you installed put them there. I mentioned a few apps that would have, did you ck. that?

Until you get rid of them or maybe tell vlc not to use vlc will continue to fail to open with the qt4 (default) interface. It's as simple as that.

I'd remove them one way or the other though possibly you could run vlc with - 
```
env LD_LIBRARY_PATH=/usr/lib vlc
```

---

### Post by Mr.Carramba on 2013-05-18
> **mc4man said:**
> What it seems is that you have qt4 libs in /usr/local/lib/ that are incompatible with vlc & being used (/usr/local will trump /usr




They didn't get there by themselves, something you installed put them there. I mentioned a few apps that would have, did you ck. that?

Until you get rid of them or maybe tell vlc not to use vlc will continue to fail to open with the qt4 (default) interface. It's as simple as that.

I'd remove them one way or the other though possibly you could run vlc with - 
```
env LD_LIBRARY_PATH=/usr/lib vlc
```

your latest suggestion did not worked.

I had only spotify and chromium, and some others. Reinstallet all libqt4 packades and still get the error
```
->vlc
VLC media player 2.1.0-pre1 Rincewind (revision 2.1.0~~git20130518+r2715)
[0x128b018] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x12b96d8] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x12b96d8] skins2 interface error: cannot instantiate qt4 dialogs provider
```

---

### Post by mc4man on 2013-05-18
So I'd assume this will produce an error?
```
vlc -Iqt4
```

If so what's in /usr/local/lib
For starters - 
```
ls /usr/local/lib
```

---

### Post by Mr.Carramba on 2013-05-18
> **mc4man said:**
> So I'd assume this will produce an error?
```
vlc -Iqt4
```

If so what's in /usr/local/lib
For starters - 
```
ls /usr/local/lib
```

Thank you for taking time! 

```
->vlc -Iqt4
VLC media player 2.1.0-pre1 Rincewind (revision 2.1.0~~git20130518+r2715)
[0x1e6b838] main interface error: no suitable interface module
[0x1e3d018] main libvlc error: interface "default" initialization failed


```

```
->ls /usr/local/lib
libAntTweakBar.so.1  libQtGui.so.4      libQtWebKit.so.4       python2.7
libLeap.so           libQtNetwork.so.4  libQtXmlPatterns.so.4  python3.3
libQtCore.so.4       libQtScript.so.4   libusb-1.0.so.0        site_ruby

```

all libQt are there, how do they end up there is a mistery...

---

### Post by Mr.Carramba on 2013-05-18
oki, after too much time spend fixing this, I ound out that it was LeapMotion SDK packade. GAH! After uninstall all good now!
thank you for feedback and help.

---

