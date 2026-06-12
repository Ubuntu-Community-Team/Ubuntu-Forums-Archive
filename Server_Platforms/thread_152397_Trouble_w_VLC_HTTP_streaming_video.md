---
title: "Trouble w/ VLC HTTP streaming video"
date: 2006-03-29
forum: Server Platforms
---

### Post by echo $USER on 2006-03-29
This is what I get:

*******@ubuntu:~$ vlc -vvv /var/www/media/Strange.mpg --sout '#standard{access=http,mux=ogg,url=localhost:8080}'
VLC media player 0.8.4-svn20040920 Janus
[00000001] main vlc debug: opening config file /home/media/.vlc/vlcrc
[00000001] main vlc debug: checking builtin modules
[00000001] main vlc debug: checking plugin modules
[00000001] main vlc debug: loading plugins cache file /home/media/.vlc/cache/plugins-04041e.dat
[00000001] main vlc debug: recursively browsing `modules'
[00000001] main vlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main vlc debug: recursively browsing `plugins'
[00000001] main vlc debug: module bank initialized, found 206 modules
[00000001] main vlc debug: opening config file /home/media/.vlc/vlcrc
[00000000] main root debug: VLC media player - version 0.8.4-svn20040920 Janus - (c) 1996-2005 the VideoLAN team
[00000000] main root debug: libvlc was configured with ./configure --mandir=/share/man --infodir=/share/info --enable-release --prefix=/usr --disable-gnome --disable-gtk --disable-familiar --disable-fb --enable-ggi --enable-sdl --enable-esd --disable-qt --enable-mad --enable-arts --enable-alsa --enable-lirc --enable-a52 --enable-aa --enable-dvbpsi --enable-xosd --enable-mozilla --disable-kde --enable-mp4 --enable-dvb --enable-dv --disable-satellite --enable-ogg --enable-vorbis --enable-wxwidgets --with-wx-config=wxgtk-2.4-config --disable-slp --enable-flac --disable-skins --disable-basic-skins --enable-skins2 --enable-freetype --disable-mkv --enable-v4l --enable-pvr --disable-speex --enable-caca --enable-livedotcom --enable-libmpeg2 --enable-dts --enable-fribidi --enable-cdio --enable-mod --enable-theora --enable-modplug --enable-dvdnav --enable-gnutls --enable-ncurses --enable-smb --disable-gnomevfs --enable-faad --with-faad-tree=extras/faad2 --enable-ffmpeg --with-ffmpeg-tree=extras/ffmpeg --enable-x264 --with-x264-tree=extras/x264 --enable-glide --enable-svgalib --enable-dvd
[00000001] main vlc debug: translation test: code is "C"
[00000001] main vlc debug: opening config file /home/media/.vlc/vlcrc
[00000001] main vlc debug: checking builtin modules
[00000001] main vlc debug: checking plugin modules
[00000001] main vlc debug: loading plugins cache file /home/media/.vlc/cache/plugins-04041e.dat
[00000001] main vlc debug: recursively browsing `modules'
[00000001] main vlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main vlc debug: recursively browsing `plugins'
[00000001] main vlc debug: module bank initialized, found 206 modules
[00000001] main vlc debug: opening config file /home/media/.vlc/vlcrc
[00000001] main vlc debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT FPU
[00000001] main vlc debug: looking for memcpy module: 4 candidates
[00000010] main module debug: using memcpy module "memcpymmxext"
[00000260] main playlist debug: waiting for thread completion
[00000260] main playlist debug: thread 3081497520 (playlist) created at priority 0 (src/playlist/playlist.c:183)
[00000261] main private debug: waiting for thread completion
[00000261] main private debug: thread 3073104816 (preparser) created at priority 0 (src/playlist/playlist.c:205)
[00000262] main interface debug: looking for interface module: 1 candidate
[00000137] main module debug: using interface module "hotkeys"
[00000262] main interface debug: interface initialized
[00000262] main interface debug: thread 3064691632 (interface) created at priority 0 (src/interface/interface.c:211)
[00000264] main interface debug: looking for interface module: 6 candidates
[00000182] main module debug: using interface module "screensaver"
[00000264] main interface debug: interface initialized
[00000264] main interface debug: thread 3056290736 (interface) created at priority 0 (src/interface/interface.c:211)
[00000260] main playlist debug: adding playlist item `/var/www/media/Strange.mpg' ( /var/www/media/Strange.mpg )
[00000266] main interface debug: looking for interface module: 5 candidates
[00000044] main module debug: using interface module "wxwidgets"
[00000266] main interface debug: interface initialized
[00000266] main interface debug: thread 3039144880 (manager) created at priority 0 (src/interface/interface.c:196)
[00000266] wxwidgets interface debug: Using last windows config '(-1,0,0,1024,768)(0,225,87,401,107)'
[00000266] wxwidgets interface debug: id=0 p=(225,87) s=(401,107)
[00000260] main playlist debug: nothing requested, starting
[00000260] main playlist debug: creating new input thread
[00000269] main input debug: waiting for thread completion
[00000269] main input debug: thread 3030535088 (input) created at priority 0 (src/input/input.c:230)
[00000270] main stream output debug: stream=`standard'
[00000271] main private debug: looking for sout stream module: 1 candidate
[00000271] main private debug: set sout option: sout-standard-access to http
[00000271] main private debug: set sout option: sout-standard-mux to ogg
[00000271] main private debug: set sout option: sout-standard-url to 192.168.0.3:8080
[00000271] stream_out_standard private debug: creating `http/ogg://192.168.0.3:8080'
[00000271] stream_out_standard private debug: extention is 3:8080
[00000271] stream_out_standard private debug: extention -> mux=(null)
[00000271] stream_out_standard private debug: using `http/ogg://192.168.0.3:8080'
[00000273] main private debug: looking for sout access module: 1 candidate
[00000273] main private: creating httpd
[00000273] main private debug: net: listening to 192.168.0.3 port 8080
[00000276] main private debug: thread 3022126000 (httpd host thread) created at priority 0 (src/misc/httpd.c:1182)
[00000241] main module debug: using sout access module "access_output_http"
[00000271] stream_out_standard private debug: access opened
[00000277] main private debug: looking for sout mux module: 1 candidate
[00000277] mux_ogg private: Open
[00000057] main module debug: using sout mux module "mux_ogg"
[00000270] main stream output debug: muxer support adding stream at any time
[00000270] main stream output debug: muxer prefers waiting for all ES before starting muxing
[00000271] stream_out_standard private debug: mux opened
[00000249] main module debug: using sout stream module "stream_out_standard"
[00000269] main input debug: `/var/www/media/Strange.mpg' gives access `' demux `' path `/var/www/media/Strange.mpg'
[00000269] main input debug: creating demux: access='' demux='' path='/var/www/media/Strange.mpg'
[00000279] main demuxer debug: looking for access_demux module: 2 candidates
[00000269] main input debug: creating access '' path='/var/www/media/Strange.mpg'
[00000282] main access debug: looking for access2 module: 4 candidates
[00000282] vcd access debug: trying .cue file: /var/www/media/Strange.cue
[00000282] access_file access debug: opening file `/var/www/media/Strange.mpg'
[00000028] main module debug: using access2 module "access_file"
[00000287] main private debug: pre buffering
[00000287] main private debug: received first data for our buffer
[00000287] main private debug: prebuffering done 1408981 bytes in 0s - 10221 kbytes/s
[00000269] main input debug: creating demux: access='' demux='' path='/var/www/media/Strange.mpg'
[00000288] main demuxer debug: looking for demux2 module: 39 candidates
[00000170] main module debug: using demux2 module "ps"


[00000269] main input debug: looking for a subtitle file in /var/www/media/
[00000269] main input debug: starting in synch mode
[00000269] main input debug: `/var/www/media/Strange.mpg' successfully opened
[00000269] main input debug: selecting program id=0
[00000269] main input debug: audio is disabled, not selecting ES 0x0
[00000269] main input debug: video is disabled, not selecting ES 0x1

Then the video is played on the local player with no video or sound; then after it finishes playing I get this:

[00000260] main playlist: nothing to play

---

