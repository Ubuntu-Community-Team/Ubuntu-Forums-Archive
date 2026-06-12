---
title: "VLC: Error when record audio-stream, can't find audio encoder?"
date: 2009-03-02
forum: Server Platforms
---

### Post by gobbledigook on 2009-03-02
Hi!

Firstly apologies for posting this over here, i have had this post on the vlc forum for *ages* and not one reply!

Currently i'm trying this on the desktop edition as its easier to mess about with and see whats going on... but eventually i want it on my headless server:)

i'm running Ubuntu 8.10 with the medibuntu repo added and i am trying to record an audio-webstream from the CLI. my command is:
```
 vlc --http-caching 1500 http://icecast.commedia.org.uk:8000/phonic.mp3 --sout='#transcode{acodec=mp3,ab=128,channels=2}:duplicate{dst=display,dst=std{access=file,mux=raw,dst=/home/dan/Desktop/phonic.mp3}}'
```

when i run the command everything looks good, but then an error box pops up to say: 
```
Streaming / Transcoding failed:
VLC could not find encoder "MPEG Audio layer 1/2/3".
```

further the output from vlc in the terminal is:
```
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000421] mux_dummy mux: Open
[00000424] access_http access: Raw-audio server found, mp3 demuxer selected
TagLib: Could not open file icecast.commedia.org.uk:8000/phonic.mp3
[00000465] avcodec encoder error: cannot find encoder MPEG Audio layer 1/2/3
[00000410] stream_out_transcode stream out error: cannot find audio encoder (module:any fourcc:mp3 )
[00000410] stream_out_transcode stream out error: cannot create audio chain
[00000463] main packetizer error: cannot create packetizer output (mpga)
```

Now obviously i realise this is an issue with .mp3 encoder? but i cannot find the solution! 
I have tried through apt-get: 
1. Remove and purge vlc and ffmpeg
2. Add the medibuntu's repositories
3. Install ffmpeg
4. Install vlc
as per this thread: [http://forum.videolan.org/viewtopic.php?f=13&t=39801&p=125909&hilit=mp3+encoder#p125909](http://forum.videolan.org/viewtopic.php?f=13&t=39801&p=125909&hilit=mp3+encoder#p125909)

i have tried manually installing an mpeg audio encoder from the synaptic package manager, firstly unticking all other repo's except the medibuntu and reloading so i only see medibuntu packages, and doing a search for mpeg encoders, i have already installed:
[list]twolame
libtwolame0
ffmpeg
libaac0
libmjpegtools
mjpegtools
mencoder
libmp3lame0
librte1
libflac8
gogo
libavcodec51[/list]

i have also run my command with the -vvv for full debug output, sorry for the long post, as it is a lot!!

```
dan@ubuntu:~$ vlc -vvv --http-caching 1500 http://icecast.commedia.org.uk:8000/phonic.mp3 --sout='#transcode{acodec=mp3,ab=192,channels=2}:duplicate{dst=display,dst=std{access=file,mux=raw,dst=/home/dan/Desktop/"phonic.wma"}}'
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc debug: checking builtin modules
[00000001] main libvlc debug: checking plugin modules
[00000001] main libvlc debug: loading plugins cache file /home/dan/.cache/vlc/plugins-04041e.dat
[00000001] main libvlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main libvlc debug: module bank initialized, found 271 modules
[00000001] main libvlc debug: opening config file (/home/dan/.config/vlc/vlcrc)
[00000001] main libvlc debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT SSE SSE2 FPU 
[00000001] main libvlc debug: looking for memcpy module: 4 candidates
[00000001] main libvlc debug: using memcpy module "memcpymmxext"
[00000369] main interaction debug: thread 3082369936 (Interaction control) created at priority 0 (interface/interaction.c:382)
[00000369] main interaction debug: thread started
[00000371] main input debug: Creating an input for 'Media Library'
[00000371] main input debug: Input is a meta file: disabling unneeded options
[00000371] main input debug: `file/xspf-open:///home/dan/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/dan/.local/share/vlc/ml.xspf'
[00000371] main input debug: creating access 'file' path='/home/dan/.local/share/vlc/ml.xspf'
[00000372] main access debug: looking for access module: 3 candidates
[00000372] access_mmap access debug: opening file /home/dan/.local/share/vlc/ml.xspf
[00000372] main access debug: using access module "access_mmap"
[00000372] main access debug: TIMER module_Need() : 1.050 ms - Total 1.050 ms / 1 intvls (Avg 1.050 ms)
[00000376] main stream debug: Using AStream*Block
[00000376] main stream debug: pre buffering
[00000376] main stream debug: received first data for our buffer
[00000372] access_mmap access debug: at end of memory mapped file
[00000371] main input debug: creating demux: access='file' demux='xspf-open' path='/home/dan/.local/share/vlc/ml.xspf'
[00000377] main demux debug: looking for demux module: 1 candidate
[00000377] playlist demux debug: using XSPF playlist reader
[00000377] main demux debug: using demux module "playlist"
[00000377] main demux debug: TIMER module_Need() : 0.749 ms - Total 0.749 ms / 1 intvls (Avg 0.749 ms)
[00000371] main input debug: `file/xspf-open:///home/dan/.local/share/vlc/ml.xspf' successfully opened
[00000392] main xml debug: looking for xml module: 2 candidates
[00000392] main xml debug: using xml module "xml"
[00000392] main xml debug: TIMER module_Need() : 1.383 ms - Total 1.383 ms / 1 intvls (Avg 1.383 ms)
[00000372] access_mmap access debug: at end of memory mapped file
[00000377] playlist demux warning: invalid <playlist> attribute:"xmlns:vlc"
[00000377] playlist demux debug: parsed 0 tracks successfully
[00000392] main xml debug: removing module "xml"
[00000371] main input debug: EOF reached
[00000371] main input debug: control type=1
[00000377] main demux debug: removing module "playlist"
[00000372] main access debug: removing module "access_mmap"
[00000371] main input debug: TIMER input launching for 'Media Library' : 6.259 ms - Total 6.259 ms / 1 intvls (Avg 6.259 ms)
[00000394] main preparser debug: thread started
[00000394] main preparser debug: waiting for thread initialization
[00000394] main preparser debug: thread 3072416656 (preparser) created at priority 0 (playlist/thread.c:79)
[00000395] main fetcher debug: thread started
[00000395] main fetcher debug: waiting for thread initialization
[00000395] main fetcher debug: thread 3064023952 (fetcher) created at priority 0 (playlist/thread.c:108)
[00000370] main playlist debug: thread started
[00000370] main playlist debug: waiting for thread initialization
[00000370] main playlist debug: rebuilding array of current - root Playlist
[00000370] main playlist debug: rebuild done - 0 items, index -1
[00000370] main playlist debug: thread 3055631248 (playlist) created at priority 0 (playlist/thread.c:117)
[00000396] main interface debug: looking for interface module: 1 candidate
[00000396] main interface debug: using interface module "hotkeys"
[00000396] main interface debug: TIMER module_Need() : 0.562 ms - Total 0.562 ms / 1 intvls (Avg 0.562 ms)
[00000396] main interface debug: thread started
[00000396] main interface debug: thread 3047238544 (interface) created at priority 0 (interface/interface.c:168)
[00000398] main interface debug: looking for interface module: 1 candidate
[00000398] main interface debug: using interface module "inhibit"
[00000398] main interface debug: TIMER module_Need() : 5.405 ms - Total 5.405 ms / 1 intvls (Avg 5.405 ms)
[00000398] main interface debug: thread started
[00000398] main interface debug: thread 3038845840 (interface) created at priority 0 (interface/interface.c:168)
[00000400] main interface debug: looking for interface module: 1 candidate
[00000400] main interface debug: using interface module "screensaver"
[00000400] main interface debug: TIMER module_Need() : 0.793 ms - Total 0.793 ms / 1 intvls (Avg 0.793 ms)
[00000400] main interface debug: thread started
[00000400] main interface debug: thread 3030453136 (interface) created at priority 0 (interface/interface.c:168)
[00000370] main playlist debug: adding item `http://icecast.commedia.org.uk:8000/phonic.mp3' ( http://icecast.commedia.org.uk:8000/phonic.mp3 )
[00000402] main interface debug: looking for interface module: 22 candidates
[00000402] main interface debug: using interface module "signals"
[00000402] main interface debug: TIMER module_Need() : 0.646 ms - Total 0.646 ms / 1 intvls (Avg 0.646 ms)
[00000402] main interface debug: thread started
[00000402] main interface debug: thread 3013667728 (interface) created at priority 0 (interface/interface.c:168)
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000404] main interface debug: looking for interface module: 4 candidates
[00000404] main interface debug: using interface module "qt4"
[00000404] main interface debug: TIMER module_Need() : 89.429 ms - Total 89.429 ms / 1 intvls (Avg 89.429 ms)
[00000404] main interface debug: thread 2986912656 (interface) created at priority 0 (interface/interface.c:168)
[00000370] main playlist debug: rebuilding array of current - root Playlist
[00000370] main playlist debug: rebuild done - 1 items, index -1
[00000370] main playlist debug: starting new item
[00000370] main playlist debug: processing request item null node Playlist skip 0
[00000370] main playlist debug: creating new input thread
[00000408] main input debug: Creating an input for 'http://icecast.commedia.org.uk:8000/phonic.mp3'
[00000404] main interface debug: thread started
[00000408] main input debug: waiting for thread initialization
[00000408] main input debug: thread started
[00000408] main input debug: thread 2976906128 (input) created at priority 10 (input/input.c:370)
[00000409] main stream output debug: stream=`transcode'
[00000410] main stream out debug: looking for sout stream module: 1 candidate
[00000409] main stream output debug: stream=`duplicate'
[00000413] main stream out debug: looking for sout stream module: 1 candidate
[00000413] stream_out_duplicate stream out debug: creating 'duplicate'
[00000413] stream_out_duplicate stream out debug:  * adding `display'
[00000409] main stream output debug: stream=`display'
[00000415] main stream out debug: looking for sout stream module: 1 candidate
[00000415] main stream out debug: using sout stream module "stream_out_display"
[00000415] main stream out debug: TIMER module_Need() : 1.549 ms - Total 1.549 ms / 1 intvls (Avg 1.549 ms)
[00000413] stream_out_duplicate stream out debug:  * adding `std{access=file,mux=raw,dst=/home/dan/Desktop/"phonic.wma"}'
[00000409] main stream output debug: stream=`std'
[00000417] main stream out debug: looking for sout stream module: 1 candidate
[00000417] main stream out debug: set config option: sout-standard-access to file
[00000417] main stream out debug: set config option: sout-standard-mux to raw
[00000417] main stream out debug: set config option: sout-standard-dst to /home/dan/Desktop/"phonic.wma"
[00000417] stream_out_standard stream out debug: creating `file/raw:///home/dan/Desktop/"phonic.wma"'
[00000417] stream_out_standard stream out debug: extension is wma"
[00000417] stream_out_standard stream out debug: extension -> mux=(null)
[00000417] stream_out_standard stream out debug: using `file/raw:///home/dan/Desktop/"phonic.wma"'
[00000419] main access out debug: looking for sout access module: 1 candidate
[00000419] access_output_file access out debug: file access output opened (/home/dan/Desktop/"phonic.wma")
[00000419] main access out debug: using sout access module "access_output_file"
[00000419] main access out debug: TIMER module_Need() : 1.308 ms - Total 1.308 ms / 1 intvls (Avg 1.308 ms)
[00000417] stream_out_standard stream out debug: access opened
[00000421] main mux debug: looking for sout mux module: 1 candidate
[00000421] mux_dummy mux debug: Dummy/Raw muxer opened
[00000421] mux_dummy mux: Open
[00000421] main mux debug: using sout mux module "mux_dummy"
[00000421] main mux debug: TIMER module_Need() : 0.604 ms - Total 0.604 ms / 1 intvls (Avg 0.604 ms)
[00000409] main stream output debug: muxer support adding stream at any time
[00000417] stream_out_standard stream out debug: mux opened
[00000417] main stream out debug: using sout stream module "stream_out_standard"
[00000417] main stream out debug: TIMER module_Need() : 7.420 ms - Total 7.420 ms / 1 intvls (Avg 7.420 ms)
[00000413] main stream out debug: using sout stream module "stream_out_duplicate"
[00000413] main stream out debug: TIMER module_Need() : 9.634 ms - Total 9.634 ms / 1 intvls (Avg 9.634 ms)
[00000410] main stream out debug: set config option: sout-transcode-acodec to mp3
[00000410] main stream out debug: set config option: sout-transcode-ab to 192
[00000410] main stream out debug: set config option: sout-transcode-channels to 2
[00000410] stream_out_transcode stream out debug: codec audio=mp3  0Hz 2 channels 192Kb/s
[00000410] main stream out debug: using sout stream module "stream_out_transcode"
[00000410] main stream out debug: TIMER module_Need() : 19.271 ms - Total 19.271 ms / 1 intvls (Avg 19.271 ms)
[00000408] main input debug: `http://icecast.commedia.org.uk:8000/phonic.mp3' gives access `http' demux `' path `icecast.commedia.org.uk:8000/phonic.mp3'
[00000408] main input debug: creating demux: access='http' demux='' path='icecast.commedia.org.uk:8000/phonic.mp3'
[00000423] main demux debug: looking for access_demux module: 0 candidates
[00000423] main demux warning: no access_demux module matched "http"
[00000423] main demux debug: TIMER module_Need() : 0.185 ms - Total 0.185 ms / 1 intvls (Avg 0.185 ms)
[00000408] main input debug: creating access 'http' path='icecast.commedia.org.uk:8000/phonic.mp3'
[00000424] main access debug: looking for access module: 2 candidates
[00000424] access_http access debug: http: server='icecast.commedia.org.uk' port=8000 file='/phonic.mp3
[00000424] main access debug: net: connecting to icecast.commedia.org.uk port 8000
[00000424] main access debug: connection: Operation now in progress
[00000424] main access debug: connection succeeded (socket = 13)
[00000424] access_http access debug: protocol 'HTTP' answer code 200
[00000424] access_http access debug: Content-Type: audio/mpeg
[00000424] access_http access debug: Meta-Info: icy-br: 64
[00000424] access_http access debug: Meta-Info: ice-audio-info: ice-samplerate=44100;ice-bitrate=64;ice-channels=2
[00000424] access_http access debug: Meta-Info: icy-br: 64
[00000424] access_http access debug: Meta-Info: icy-description: 106.8FM in Exeter, UK
[00000424] access_http access debug: Icy-Genre: Phonic
[00000424] access_http access debug: Icy-Name: Phonic.FM
[00000424] access_http access debug: Meta-Info: icy-private: 0
[00000424] access_http access debug: Meta-Info: icy-pub: 1
[00000424] access_http access debug: Meta-Info: icy-url: http://www.phonic.fm
[00000424] access_http access debug: Server: Icecast trunk
[00000424] access_http access debug: Icy-MetaInt: 16000
[00000424] access_http access warning: ICY metaint=16000
[00000424] access_http access: Raw-audio server found, mp3 demuxer selected
[00000424] access_http access debug: auto re-connect enabled
[00000424] main access debug: using access module "access_http"
[00000424] main access debug: TIMER module_Need() : 520.309 ms - Total 520.309 ms / 1 intvls (Avg 520.309 ms)
[00000426] main stream debug: Using AStream*Stream
[00000426] main stream debug: pre-buffering...
[00000404] qt4 interface debug: Error while initializing qt-specific localization
[00000404] qt4 interface debug: Updating the stream status: 3
[00000426] main stream debug: received first data for our buffer
[00000426] main stream debug: pre-buffering done 15400 bytes in 0s - 27 kbytes/s
[00000408] main input debug: creating demux: access='http' demux='mp3' path='icecast.commedia.org.uk:8000/phonic.mp3'
[00000427] main demux debug: looking for demux module: 1 candidate
[00000429] main packetizer debug: looking for packetizer module: 18 candidates
[00000429] main packetizer debug: using packetizer module "mpeg_audio"
[00000429] main packetizer debug: TIMER module_Need() : 6.895 ms - Total 6.895 ms / 1 intvls (Avg 6.895 ms)
[00000427] main demux debug: using demux module "mpga"
[00000427] main demux debug: TIMER module_Need() : 7.971 ms - Total 7.971 ms / 1 intvls (Avg 7.971 ms)
[00000408] main input debug: starting in async mode
[00000427] main demux debug: looking for meta reader module: 2 candidates
TagLib: Could not open file icecast.commedia.org.uk:8000/phonic.mp3
[00000427] id3tag demux debug: checking for ID3v1/2 and APEv1/2 tags
[00000427] main demux debug: TIMER module_Need() : 5.311 ms - Total 5.311 ms / 1 intvls (Avg 5.311 ms)
[00000408] main input debug: `http://icecast.commedia.org.uk:8000/phonic.mp3' successfully opened
[00000429] mpeg_audio packetizer debug: free bitrate mode
[00000427] mpga demux debug: did not sync on first block
[00000408] main input debug: control type=1
[00000429] mpeg_audio packetizer debug: frame too big 2091 > 2090 (emulated startcode ?)
[00000429] mpeg_audio packetizer debug: emulated startcode
[00000429] mpeg_audio packetizer debug: MPGA channels:2 samplerate:44100 bitrate:64
[00000408] main input debug: selecting program id=0
[00000463] main packetizer debug: looking for packetizer module: 18 candidates
[00000463] main packetizer debug: using packetizer module "mpeg_audio"
[00000463] main packetizer debug: TIMER module_Need() : 0.755 ms - Total 0.755 ms / 1 intvls (Avg 0.755 ms)
[00000408] main input debug: stream out mode -> no decoder thread
[00000463] mpeg_audio packetizer debug: MPGA channels:2 samplerate:44100 bitrate:64
[00000409] main stream output debug: adding a new sout input (sout_input:0x944bef0)
[00000410] stream_out_transcode stream out debug: creating audio transcoding from fcc=`mpga' to fcc=`mp3 '
[00000464] main decoder debug: looking for decoder module: 30 candidates
[00000464] main decoder debug: using decoder module "mpeg_audio"
[00000464] main decoder debug: TIMER module_Need() : 12.499 ms - Total 12.499 ms / 1 intvls (Avg 12.499 ms)
[00000465] main encoder debug: looking for encoder module: 10 candidates
[00000465] avcodec encoder debug: libavcodec initialized (interface 3355136 )
[00000465] avcodec encoder error: cannot find encoder MPEG Audio layer 1/2/3
[00000465] main encoder debug: TIMER module_Need() : 26.950 ms - Total 26.950 ms / 1 intvls (Avg 26.950 ms)
[00000410] stream_out_transcode stream out error: cannot find audio encoder (module:any fourcc:mp3 )
[00000464] main decoder debug: removing module "mpeg_audio"
[00000410] stream_out_transcode stream out error: cannot create audio chain
[00000463] main packetizer error: cannot create packetizer output (mpga)
[00000424] access_http access debug: New Title=
[00000404] qt4 interface debug: New Event: type 1103
[00000404] qt4 interface debug: Updating the stream status: 3
[00000404] qt4 interface debug: New Event: type 1108
[00000404] qt4 interface debug: Initialization of Capture device panel
^C[00000402] signals interface error: Caught Interrupt signal, exiting...
[00000402] main interface debug: thread ended
[00000001] main libvlc debug: removing all interfaces
[00000370] main playlist debug: incoming request - stopping current input
[00000424] main access debug: waitpipe: object killed
[00000404] qt4 interface debug: Quitting the Qt4 Interface
[00000404] qt4 interface debug: Destroying the main interface
[00000424] main access debug: socket 13 polling interrupted
[00000370] main playlist debug: dying input
[00000404] qt4 interface debug: Destroying the Dialog Provider
[00000404] main interface debug: thread ended
[00000404] main interface debug: thread 2986912656 joined (interface/interface.c:188)
[00000404] main interface debug: removing module "qt4"
[00000402] main interface debug: thread 3013667728 joined (interface/interface.c:188)
[00000402] main interface debug: removing module "signals"
[00000400] main interface debug: thread ended
[00000400] main interface debug: thread 3030453136 joined (interface/interface.c:188)
[00000400] main interface debug: removing module "screensaver"
[00000398] main interface debug: thread ended
[00000398] main interface debug: thread 3038845840 joined (interface/interface.c:188)
[00000398] main interface debug: removing module "inhibit"
[00000396] main interface debug: thread ended
[00000396] main interface debug: thread 3047238544 joined (interface/interface.c:188)
[00000396] main interface debug: removing module "hotkeys"
[00000001] main libvlc debug: removing all services discovery tasks
[00000001] main libvlc debug: removing playlist
[00000408] main input debug: control type=0
[00000408] main input debug: control: stopping input
[00000429] main packetizer debug: removing module "mpeg_audio"
[00000427] main demux debug: removing module "mpga"
[00000424] main access debug: removing module "access_http"
[00000463] main packetizer debug: removing module "mpeg_audio"
[00000463] main packetizer debug: killing decoder fourcc `mpga', 0 PES in FIFO
[00000408] main input debug: thread ended
[00000370] main playlist debug: dead input
[00000408] main input debug: thread 2976906128 joined (playlist/engine.c:244)
[00000408] main input debug: TIMER input launching for 'http://icecast.commedia.org.uk:8000/phonic.mp3' : 1127.662 ms - Total 1127.662 ms / 1 intvls (Avg 1127.662 ms)
[00000410] main stream out debug: destroying chain... (name=transcode)
[00000413] main stream out debug: destroying chain... (name=duplicate)
[00000413] stream_out_duplicate stream out debug: closing a duplication
[00000415] main stream out debug: destroying chain... (name=display)
[00000415] main stream out debug: removing module "stream_out_display"
[00000415] main stream out debug: destroying chain done
[00000417] main stream out debug: destroying chain... (name=std)
[00000421] mux_dummy mux debug: Dummy/Raw muxer closed
[00000421] main mux debug: removing module "mux_dummy"
[00000419] access_output_file access out debug: file access output closed
[00000419] main access out debug: removing module "access_output_file"
[00000417] main stream out debug: removing module "stream_out_standard"
[00000417] main stream out debug: destroying chain done
[00000413] main stream out debug: removing module "stream_out_duplicate"
[00000413] main stream out debug: destroying chain done
[00000410] main stream out debug: removing module "stream_out_transcode"
[00000410] main stream out debug: destroying chain done
[00000370] main playlist debug: saving Media Library to file /home/dan/.local/share/vlc/ml.xspf
[00000370] main playlist debug: looking for playlist export module: 1 candidate
[00000370] main playlist debug: using playlist export module "export"
[00000370] main playlist debug: TIMER module_Need() : 0.810 ms - Total 0.810 ms / 1 intvls (Avg 0.810 ms)
[00000370] main playlist debug: removing module "export"
[00000394] main preparser debug: thread ended
[00000394] main preparser debug: thread 3072416656 joined (playlist/engine.c:521)
[00000395] main fetcher debug: thread ended
[00000395] main fetcher debug: thread 3064023952 joined (playlist/engine.c:523)
[00000370] main playlist debug: thread ended
[00000370] main playlist debug: thread 3055631248 joined (libvlc.c:992)
[00000394] main preparser debug: Destroyed
[00000395] main fetcher debug: Destroyed
[00000370] main playlist debug: Destroyed
[00000001] main libvlc debug: removing interaction
[00000369] main interaction debug: thread ended
[00000369] main interaction debug: thread 3082369936 joined (interface/interaction.c:400)
[00000001] main libvlc debug: removing all video outputs
[00000001] main libvlc debug: TIMER ML Load : Total 8.430 ms / 1 intvls (Avg 8.430 ms)
[00000001] main libvlc debug: TIMER Items array build : Total 0.186 ms / 2 intvls (Avg 0.093 ms)
[00000001] main libvlc debug: TIMER ML Dump : Total 1.129 ms / 1 intvls (Avg 1.129 ms)
[00000001] main libvlc debug: removing stats
[00000001] main libvlc debug: removing module "memcpymmxext"
[00000001] main libvlc debug: opening config file (/home/dan/.config/vlc/vlcrc)
[00000001] main libvlc debug: opening config file (/home/dan/.config/vlc/vlcrc)
[00000001] main libvlc debug: writing plugins cache /home/dan/.cache/vlc/plugins-04041e.dat
```

i eventually would like to run this as a script on my headless server in conjunction with cron to record certain shows.... but obviously i'm a long way from there!!

first things first, to get the stream recording!! :)

any suggestions are much appreciated, if you need any more info from me just ask:)

thanx in advance!!

Dan

---

### Post by ajgreeny on 2009-03-02
I can't help your situation with VLC, but just wonder if you have seen, or used streamripper, which I use to record mp3 radio streams without a problem.  It is in the repos and together with streamtuner as a browser/recorder they are terrific.  I know this does not specifically answer your question, but though it worth the "lateral thought" comment.

I assume you can play mp3s on your box so it is the encoding, not the decoding that is the problem, but also wonder if you have tried using soundconverter, just as a test to convert a wav to an mp3.  If that will not work, it will at least tell you that there is a system wide mp3 problem, not just a VLC one.

---

### Post by andrew.46 on 2009-03-02
Hi,

Easier with MPlayer:

```
$ mplayer -cache 2048 http://icecast.commedia.org.uk:8000/phonic.mp3 \
          -vc null -vo null -ao pcm:fast:waveheader:file=download.wav
```

and then convert the file download.wav to whatever format you wish.

Incidentally your commandline worked perfectly on my system:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]cvlc --http-caching 1500 http://icecast.commedia.org.uk:8000/phonic.mp3  --sout='#transcode{acodec=mp3,ab=128,channels=2}:duplicate{dst=display,dst=std{access=file,mux=raw,dst=phonic.mp3}}'[/COLOR]**
VLC media player 0.9.8a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.8a Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--prefix=/usr' '--libdir=/usr/lib' '--sysconfdir=/etc' '--mandir=/usr/man' '--localstatedir=/var' '--without-contrib' '--disable-rpath' '--disable-debug' '--disable-testsuite' '--disable-static' '--enable-shared' '--enable-release' '--enable-optimize-memory=no' '--enable-qt4' '--disable-arts' '--enable-esd' '--disable-gnomevfs' '--enable-pvr' '--enable-dc1394' '--with-dv-raw1394=/tmp/build/tmp-vlc/libraw1394-1.3.0' '--with-dv-avc1394=/tmp/build/tmp-vlc/libavc1394-0.5.3' '--disable-dv' '--enable-dvbpsi' '--enable-dvdnav' '--with-dvdnav-config-path=/tmp/build/tmp-vlc/vlcdeps/usr/bin' '--enable-libcdio' '--enable-cddax' '--enable-vcdx' '--enable-libcddb' '--enable-svg' '--enable-svgalib' '--enable-telx' '--disable-zvbi' '--disable-snapshot' '--enable-libass' '--enable-v4l' '--enable-caca' '--enable-aa' '--enable-galaktos' '--enable-upnp' '--enable-flac' '--enable-shout' '--enable-schroedinger' '--enable-live555' '--with-live555-tree=/tmp/build/tmp-vlc/live' '--enable-real' '--enable-realrtsp' '--enable-speex' '--with-speex-tree=/tmp/build/tmp-vlc/speex-1.2rc1' '--enable-x264' '--with-x264-tree=/tmp/build/tmp-vlc/x264-snapshot-20081210-2245' '--enable-a52' '--with-a52-tree=/tmp/build/tmp-vlc/a52dec-0.7.4' '--enable-dca' '--with-dca-tree=/tmp/build/tmp-vlc/libdca-0.0.5' '--enable-faad' '--with-faad-tree=/tmp/build/tmp-vlc/faad2' '--enable-twolame' '--with-twolame-tree=/tmp/build/tmp-vlc/twolame-0.3.12' '--enable-ogg' '--enable-vorbis' '--enable-theora' '--enable-avcodec' '--enable-avformat' '--enable-swscale' '--enable-loader' '--program-prefix=' '--program-suffix=' '--build=i486-slackware-linux' 'AVCODEC_LIBS=-lavcodec -lbz2 -lz -lamrnb -lamrwb -lmp3lame -lfaac -ldl -ltheora -lvorbisenc -lavutil -lvorbis -lm -logg' 'AVCODEC_CFLAGS=' 'build_alias=i486-slackware-linux' 'CFLAGS=-O2 -march=i486 -mtune=i686 -I/tmp/build/tmp-vlc/vlcdeps/usr/include' 'LDFLAGS= -L/tmp/build/tmp-vlc/vlcdeps/usr/lib' 'CPPFLAGS=-I/tmp/build/tmp-vlc/vlcdeps/usr/include' 'CXXFLAGS=-O2 -march=i486 -mtune=i686 -I/tmp/build/tmp-vlc/vlcdeps/usr/include' 'PKG_CONFIG_PATH=/tmp/build/tmp-vlc/vlcdeps/usr/lib/pkgconfig'
[00000001] main libvlc debug: translation test: code is "C"
[00000412] dummy interface: using the dummy interface module...
[00000434] mux_dummy mux: Open
[00000437] access_http access: Raw-audio server found, mp3 demuxer selected
TagLib: Could not open file icecast.commedia.org.uk:8000/phonic.mp3

```

although for the life of me I could not disable that taglib message :-). Can you actually encode to mp3 with your copy of vlc?

Andrew

---

### Post by gobbledigook on 2009-03-02
Hi!

thanx for your replies:)

@ ajgreeny: i looked at streamripper previously but was more difficult to configure timed recordings with.

@ andrew.46: I found a previous post by you concerning a similar issue and modified your script using mplayer to rip and lame to encode to mp3. It works perfectly so thankyou!!

```

#!/bin/sh
#-------------------------------------------------------------
# A very simple script to capture the audio stream of:
#               phonic.fm
# Requires the svn Mplayer & Lame.
#-------------------------------------------------------------

# Most of the variables:

DATE1=$(date +%d%m%Y)
DATE2=$(date +"%A %B %d, %Y.")
STREAM=http://icecast.commedia.org.uk:8000/phonic.mp3.m3u
DURATION=2h
MUSIC_DIR=/home/server/phonic_tmp

#-------------------------------------------------------------
cd $MUSIC_DIR

# Download the stream and convert it to wave format:

mplayer -cache 128 -playlist $STREAM \
        -vc null -vo null -ao pcm:fast:waveheader:file=phonic.wav &

sleep $DURATION # Length of the program being recorded as background.
kill $!         # End the most recently backgrounded job = mplayer

# Convert to mp3 format and add the date tag:

lame --quiet phonic.wav \
        --preset standard \
        -o /media/swap/phonic/phonic_$DATE1.mp3

#-------------------------------------------------------------
# Clean up:

rm phonic.wav

```

the main problem was the ```
 TagLib: Could not open file icecast.commedia.org.uk:8000/phonic.mp3 
```message, i originally wrote this script for vlc as a batch file in windoze and didn't need to append the .m3u to the end of the streams url! :lol:

once i'd figured that out it was plain sailing:)

have the script on my server now... only problem is i can't seem to get it to execute from cron :(

have modified using sudo crontab -e and adding the line:

```
# m h  dom mon dow   command
00 10 * * 3     ./home/server/phonic_fm
00 01 * * 2     ./home/server/phonic_test

```

(phonic_test is a 5 min recording)

and also added the same lines to /etc/crontab so it looks like:

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
00 10   * * 3   root    ./home/server/phonic_fm
00 01   * * 2   root    ./home/server/phonic_test

```

to no avail! its getting a bit late for me here so gonna call it a night and try again in the morning.

thanks for the help:)

Dan,

---

### Post by gobbledigook on 2009-03-03
hi!

well after a bit of searching today i think i've found my solution, i checked out [**_this _**]("http://ubuntuforums.org/showthread.php?t=1040145&highlight=crontab")thread and added my script to cron.weekly and edited /etc/crontab as follows:

```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
00 10   * * 3   root    cd / && run-parts --report /etc/cron.weekly/ 2> /dev/null
#

```

i understand that this will run every script in cron.weekly but i have run it from terminal and it doesn;t seem to create any ill effects, i tried editing my users crontab using ```
crontab -e
``` and ```
sudo crontab -e
``` to directly execute just my script but it never worked!!

i tried checking syslog but this had no info other that the date and time when i edited the various crontabs.

its not perfect but... now my friends radio show is recorded and transcoded to mp3 every weds:) 

:guitar:

---

### Post by andrew.46 on 2009-03-03
Hi gobbledigook,

> **gobbledigook said:**
> I found a previous post by you concerning a similar issue and modified your script using mplayer to rip and lame to encode to mp3. It works perfectly so thankyou!!

```

mplayer [COLOR="Red"]**-cache 128**[/COLOR] -playlist $STREAM \
        -vc null -vo null -ao pcm:fast:waveheader:file=phonic.wav &

```


I am tickled pink that you have reworked my script for your own use :-). This script works beautifully for me as well. Small error that I have highlighted above: -cache takes kilobytes so you may be better with 1024 or 2048 rather than 128.

All the best,

Andrew

---

