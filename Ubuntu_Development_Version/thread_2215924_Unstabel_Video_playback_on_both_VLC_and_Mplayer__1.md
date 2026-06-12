---
title: "Unstabel Video playback on both VLC and Mplayer | 14.04 Beta2"
date: 2014-04-09
forum: Ubuntu Development Version
---

### Post by linuxyogi on 2014-04-09
Hi,

I cant watch any videos with both vlc and mplayer2. I tried using mplayer2 from the command line but same thing.

The nature of the problem is identical. Both VLC and mplayer2 is actcing the same way.

Here's VLC's debug

 

 ```
[COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 8 ms)

 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 1 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 1 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]auto hiding mouse cursor
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 3 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 4 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 11 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 15 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 14 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 6 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]auto hiding mouse cursor
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 13 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 4 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]adding item `Agneepath - Chikni Chameli Extended Video-MQM7CNoAsBI.mp4' ( file:///home/techy/videos/New/hindi/Agneepath%20-%20Chikni%20Chameli%20Extended%20Video-MQM7CNoAsBI.mp4 )
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]control: stopping input
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Adding a new MRL to recent ones: file:///home/techy/videos/New/hindi/Agneepath%20-%20Chikni%20Chameli%20Extended%20Video-MQM7CNoAsBI.mp4
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]incoming request - stopping current input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]control: stopping input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Creating an input for 'Agneepath - Chikni Chameli Extended Video-MQM7CNoAsBI.mp4'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 0 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no fetch required for (null) (art currently (null))
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]incoming request - stopping current input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]finished input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "avcodec"
 [COLOR=#00008b]*avcodec*[/COLOR][COLOR=#808080]* debug: *[/COLOR]ffmpeg codec (H264 - MPEG-4 AVC (part 10)) stopped
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]killing decoder fourcc `h264', 0 PES in FIFO
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]saving a free vout
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]reusing provided vout
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "a52"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]killing decoder fourcc `a52 ', 0 PES in FIFO
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "samplerate"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "a52tofloat32"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "scaletempo"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "float_mixer"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]keeping audio output
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "mkv"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Program doesn't contain anymore ES
 [COLOR=#00008b]*mkv*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Stopping the UI Hook
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "record"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "filesystem"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]incoming request - stopping current input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dead input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]processing request item: Agneepath - Chikni Chameli Extended Video-MQM7CNoAsBI.mp4, node: null, skip: 0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]rebuilding array of current - root Playlist
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]rebuild done - 2 items, index 1
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]starting playback of the new playlist item
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]resyncing on Agneepath - Chikni Chameli Extended Video-MQM7CNoAsBI.mp4
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Agneepath - Chikni Chameli Extended Video-MQM7CNoAsBI.mp4 is at 1
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating new input thread
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Creating an input for 'Agneepath - Chikni Chameli Extended Video-MQM7CNoAsBI.mp4'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using timeshift granularity of 50 MiB, in path '/tmp'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]`file:///home/techy/videos/New/hindi/Agneepath%20-%20Chikni%20Chameli%20Extended%20Video-MQM7CNoAsBI.mp4' gives access `file' demux `' path `/home/techy/videos/New/hindi/Agneepath%20-%20Chikni%20Chameli%20Extended%20Video-MQM7CNoAsBI.mp4'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating demux: access='file' demux='' location='/home/techy/videos/New/hindi/Agneepath%20-%20Chikni%20Chameli%20Extended%20Video-MQM7CNoAsBI.mp4' file='/home/techy/videos/New/hindi/Agneepath - Chikni Chameli Extended Video-MQM7CNoAsBI.mp4'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access_demux module matching "file": 20 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access_demux modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating access 'file' location='/home/techy/videos/New/hindi/Agneepath%20-%20Chikni%20Chameli%20Extended%20Video-MQM7CNoAsBI.mp4', path='/home/techy/videos/New/hindi/Agneepath - Chikni Chameli Extended Video-MQM7CNoAsBI.mp4'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access module matching "file": 25 candidates
 [COLOR=#00008b]*filesystem*[/COLOR][COLOR=#808080]* debug: *[/COLOR]opening file `/home/techy/videos/New/hindi/Agneepath - Chikni Chameli Extended Video-MQM7CNoAsBI.mp4'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using access module "filesystem"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Using stream method for AStream*
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]starting pre-buffering
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]received first data after 0 ms
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]pre-buffering done 1024 bytes in 0s - 52631 KiB/s
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for stream_filter module matching "any": 9 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no stream_filter modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for stream_filter module matching "record": 9 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using stream_filter module "record"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating demux: access='file' demux='' location='/home/techy/videos/New/hindi/Agneepath%20-%20Chikni%20Chameli%20Extended%20Video-MQM7CNoAsBI.mp4' file='/home/techy/videos/New/hindi/Agneepath - Chikni Chameli Extended Video-MQM7CNoAsBI.mp4'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for demux module matching "mp4": 63 candidates
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#008000]* warning: *[/COLOR]unknown box type btrt (incompletely loaded)
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#008000]* warning: *[/COLOR]unknown box type gsst (incompletely loaded)
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#008000]* warning: *[/COLOR]unknown box type gstd (incompletely loaded)
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#008000]* warning: *[/COLOR]unknown box type gssd (incompletely loaded)
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#008000]* warning: *[/COLOR]unknown box type gspu (incompletely loaded)
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#008000]* warning: *[/COLOR]unknown box type gspm (incompletely loaded)
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#008000]* warning: *[/COLOR]unknown box type gshh (incompletely loaded)
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dumping root Box "root"
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| + ftyp size 24
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| + moov size 113167
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | + mvhd size 108
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | + iods size 21
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | + trak size 40733
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | + tkhd size 92
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | + edts size 36
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | + elst size 28
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | + mdia size 40597
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | + mdhd size 32
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | + hdlr size 45
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | + minf size 40512
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | + vmhd size 20
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | + dinf size 36
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + dref size 28
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | | + url size 12
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | + stbl size 40448
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + stsd size 168
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | | + avc1 size 152
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | | | + avcC size 46
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | | | + btrt size 20
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + stts size 24
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + stss size 804
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + stsc size 40
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + stsz size 36360
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + stco size 3044
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | + trak size 71541
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | + tkhd size 92
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | + mdia size 71441
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | + mdhd size 32
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | + hdlr size 76
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | + minf size 71325
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | + smhd size 16
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | + dinf size 36
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + dref size 28
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | | + url size 12
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | + stbl size 71265
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + stsd size 105
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | | + mp4a size 89
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | | | + esds size 53
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + stts size 24
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + stsc size 5464
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + stsz size 62624
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | | + stco size 3040
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | + udta size 756
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | + meta size 748
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | + hdlr size 33
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | + ilst size 703
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | + gsst size 25
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | + gstd size 30
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | + gssd size 56
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | + gspu size 152
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | + gspm size 152
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| | | | | + gshh size 280
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]| + mdat size 117051720
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]unrecognized major file specification (mp42).
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]found 2 tracks
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#008000]* warning: *[/COLOR]elst box found
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- [0] duration=363380ms media time=0ms) rate=1.0
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]track[Id 0x1] read 757 chunk
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]track[Id 0x1] read 9085 samples length:363s
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]selecting program id=0
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]adding track[Id 0x1] video (enable) language undef
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]track[Id 0x2] read 756 chunk
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]track[Id 0x2] read 15651 samples length:363s
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]adding track[Id 0x2] audio (enable) language undef
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using demux module "mp4"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for a subtitle file in /home/techy/videos/New/hindi/
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for decoder module matching "any": 39 candidates
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing sink 0: alsa_output.pci-0000_00_05.0.analog-stereo (Built-in Audio Analog Stereo)
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Deleting the input
 [COLOR=#00008b]*avcodec*[/COLOR][COLOR=#808080]* debug: *[/COLOR]trying to use direct rendering
 [COLOR=#00008b]*avcodec*[/COLOR][COLOR=#808080]* debug: *[/COLOR]allowing 3 thread(s) for decoding
 [COLOR=#00008b]*avcodec*[/COLOR][COLOR=#808080]* debug: *[/COLOR]avcodec codec (H264 - MPEG-4 AVC (part 10)) started
 [COLOR=#00008b]*avcodec*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using frame thread mode with 3 threads
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using decoder module "avcodec"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for decoder module matching "any": 39 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]Failed to resize display
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Setting an input
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Deleting the input
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Setting an input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using decoder module "faad"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for meta reader module matching "any": 2 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/techy/.local/share/vlc/lua/meta/reader
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/reader
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no meta reader modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]`file:///home/techy/videos/New/hindi/Agneepath%20-%20Chikni%20Chameli%20Extended%20Video-MQM7CNoAsBI.mp4' successfully opened
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]elst (0) gives 0ms (movie)-> 0ms (track)
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]track[Id 0x1] using Sync Sample Box (stss)
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]stts gives 0 --> 0 (sample number)
 [COLOR=#00008b]*mp4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]track[Id 0x2] does not provide Sync Sample Box (stss)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Buffering 0%
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Buffering 0%
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Buffering 33%
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Buffering 66%
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Buffering 100%
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Stream buffering done (400 ms in 1 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]trying to reuse free vout
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "freetype"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for text renderer module matching "any": 2 candidates
 [COLOR=#00008b]*freetype*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Building font databases.
 [COLOR=#00008b]*freetype*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Took 1 microseconds
 [COLOR=#00008b]*faad*[/COLOR][COLOR=#008000]* warning: *[/COLOR]decoded zero sample
 [COLOR=#00008b]*freetype*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Using Serif Bold as font from file /usr/share/fonts/truetype/dejavu/DejaVuSans.ttf
 [COLOR=#00008b]*freetype*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using fontsize: 2
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using text renderer module "freetype"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "xcb_glx"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Opening vout display wrapper
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for vout display module matching "any": 12 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Reusing previous vout window
 [COLOR=#00008b]*xcb_glx*[/COLOR][COLOR=#808080]* debug: *[/COLOR]connected to X11.0 server
 [COLOR=#00008b]*xcb_glx*[/COLOR][COLOR=#808080]* debug: *[/COLOR]vendor : The X.Org Foundation
 [COLOR=#00008b]*xcb_glx*[/COLOR][COLOR=#808080]* debug: *[/COLOR]version: 11500000
 [COLOR=#00008b]*xcb_glx*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using screen 0x254
 [COLOR=#00008b]*xcb_glx*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using GLX extension version 1.4
 [COLOR=#00008b]*xcb_glx*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using X11 window 04200000
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]VoutDisplayEvent 'fullscreen' 0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]VoutDisplayEvent 'resize' 1280x544 window
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using vout display module "xcb_glx"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]original format sz 1280x720, of (0,0), vsz 1280x720, 4cc I420, sar 1:1, msk r0x0 g0x0 b0x0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]reusing provided vout
 [COLOR=#00008b]*avcodec*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using direct rendering
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]reusing audio output
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using stereo channel map
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changed buffer metrics: maxlength=4194304, tlength=42336, prebuf=0, minreq=14112
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]connected to sink alsa_output.pci-0000_00_05.0.analog-stereo
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]output 'f32l' 48000 Hz Stereo frame=1 samples/8 bytes
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]base volume: 65536
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for audio volume module matching "any": 2 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using audio volume module "float_mixer"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]input 'f32l' 44100 Hz Stereo frame=1 samples/8 bytes
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for audio filter module matching "scaletempo": 14 candidates
 [COLOR=#00008b]*scaletempo*[/COLOR][COLOR=#808080]* debug: *[/COLOR]format: 44100 rate, 2 nch, 4 bps, fl32
 [COLOR=#00008b]*scaletempo*[/COLOR][COLOR=#808080]* debug: *[/COLOR]params: 30 stride, 0.200 overlap, 14 search
 [COLOR=#00008b]*scaletempo*[/COLOR][COLOR=#808080]* debug: *[/COLOR]1.000 scale, 1323.000 stride_in, 1323 stride_out, 1059 standing, 264 overlap, 617 search, 2204 queue, fl32 mode
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using audio filter module "scaletempo"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]conversion: 'f32l'->'f32l' 44100 Hz->44100 Hz Stereo->Stereo
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]conversion pipeline complete
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]conversion: 'f32l'->'f32l' 44100 Hz->44100 Hz Stereo->Stereo
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]conversion pipeline complete
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for audio resampler module matching "any": 3 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using audio resampler module "samplerate"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]End of audio preroll
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]End of video preroll
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Received first picture
 [COLOR=#00008b]*freetype*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Breaking line
 [COLOR=#00008b]*xcb_glx*[/COLOR][COLOR=#808080]* debug: *[/COLOR]display is visible
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Decoder buffering done in 250 ms
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]cannot synchronize start
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]deferring start (30969 us)
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]deferring start (7951 us)
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]deferring start (7502 us)
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#008000]* warning: *[/COLOR]starting late (-18032 us)
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]started
 [COLOR=#00008b]*pulse*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing sink 0: alsa_output.pci-0000_00_05.0.analog-stereo (Built-in Audio Analog Stereo)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]Failed to resize display
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]VoutDisplayEvent 'resize' 1280x720 window
 [COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR]picture is too late to be displayed (missing 99 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR]picture is too late to be displayed (missing 59 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 19 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR]picture is too late to be displayed (missing 41 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 1 ms)
 [COLOR=#00008b]*xcb_glx*[/COLOR][COLOR=#808080]* debug: *[/COLOR]display is visible
 [COLOR=#00008b]*xcb_glx*[/COLOR][COLOR=#808080]* debug: *[/COLOR]display is visible
 [COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR]picture is too late to be displayed (missing 38 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 14 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 8 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR]picture is too late to be displayed (missing 34 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 3 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR]picture is too late to be displayed (missing 45 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]picture might be displayed late (missing 5 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#008000]* warning: *[/COLOR]picture is too late to be displayed (missing 38 ms)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]auto hiding mouse cursor
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]auto hiding mouse cursor
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]auto hiding mouse cursor


```

Since both the player are down I am stuck.

---

### Post by linuxyogi on 2014-04-09
Problem solved !

Installed lubuntu-desktop. I guess my system is not capable of handling Unity. 

Is it possible to safe remove the ubuntu-desktop and all its dependencies without breaking things ?

---

### Post by Roosje on 2014-04-09
That is not [SOLVED], that is sidestepping the issue :-( Here i was hoping to find a solution, although mine only crashes on .MP4 files now.

---

### Post by linuxyogi on 2014-04-09
I marked this thread as solved coz I thought the specs of my PC is the problem not Ubuntu. I am marking it unsolved. I hope someone offers a solution.

---

### Post by andrew.46 on 2014-04-09
It might be helpful to see the MPlayer commandline errors on one of the difficult files.

---

### Post by linuxyogi on 2014-04-10
> **andrew.46 said:**
> It might be helpful to see the MPlayer commandline errors on one of the difficult files.

There problem is not with some files. No matter which I try to play while in Unity I am facing this issue.

mplayer log

```
echy@techy:~/videos/New/hindi$ mplayer -v track\ f.mkv 
Reading config file /etc/mplayer/mplayer.conf
: No such file or directory
get_path('') -> '/home/techy/.mplayer/'
get_path('config') -> '/home/techy/.mplayer/config'
Reading config file /home/techy/.mplayer/config
MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 1
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (Family: 15, Model: 107, Stepping: 2)
extended cpuid-level: 24
extended cache-info: 33587520
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 1 SSSE3: 0
Compiled with runtime CPU detection.
Compiled against libavutil version 52.3.0
Compiled against libavcodec version 54.35.0
Compiled against libavformat version 54.20.3
Compiled against libswscale version 2.1.1
get_path('codecs.conf') -> '/home/techy/.mplayer/codecs.conf'
No optional codecs config file: /home/techy/.mplayer/codecs.conf
No optional codecs config file: /etc/mplayer/codecs.conf
163 audio & 363 video codecs
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-translation --extra-cflags=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -D_FORTIFY_SOURCE=2 --extra-ldflags=-Wl,-Bsymbolic-functions -Wl,-z,relro --enable-debug=3 --enable-runtime-cpudetection
CommandLine: '-v' 'track f.mkv'
get_path('fonts') -> '/home/techy/.mplayer/fonts'
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/techy/.mplayer/fonts'
[ass] Raster: FreeType 2.5.2
[ass] Shaper: FriBidi 0.19.6 (SIMPLE)
[ass] Initialized
get_path('fonts') -> '/home/techy/.mplayer/fonts'
get_path('subfont.ttf') -> '/home/techy/.mplayer/subfont.ttf'
[ass] Updating font cache
Using nanosleep() timing
get_path('input.conf') -> '/home/techy/.mplayer/input.conf'
Cannot open file '/home/techy/.mplayer/input.conf': No such file or directory
Failed to open /home/techy/.mplayer/input.conf.
Can't open input config file /home/techy/.mplayer/input.conf.
Cannot open file '/etc/mplayer/input.conf': No such file or directory
Failed to open /etc/mplayer/input.conf.
Can't open input config file /etc/mplayer/input.conf.
Falling back on default (hardcoded) input config
Setting up LIRC support...
Failed to open LIRC support. You will not be able to use your remote control.
get_path('track f.mkv.conf') -> '/home/techy/.mplayer/track f.mkv.conf'

Playing track f.mkv.
get_path('sub/') -> '/home/techy/.mplayer/sub/'
[file] File size is 118191764 bytes
STREAM: [file] track f.mkv
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: Matroska / WebM
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for REAL
Checking for SMJPEG
[mkv] Found the head...
[mkv] + a segment...
[mkv] /---- [ parsing seek head ] ---------
[mkv] |+ segment information...
[mkv] | + timecode scale: 1000000
[mkv] | + duration: 213.647s
[mkv] | + segment uid a5 f9 b3 4b 10 bd af 91 b9 e7 73 76 61 a7 54 7b
[mkv] |+ segment tracks...
[mkv] | + a track...
[mkv] |  + Track number: 1
[mkv] |  + Track type: Video
[mkv] |  + Video track
[mkv] |   + Display width: 1280
[mkv] |   + Display height: 544
[mkv] |   + Pixel width: 1280
[mkv] |   + Pixel height: 544
[mkv] |  + Codec ID: V_MPEG4/ISO/AVC
[mkv] |  + CodecPrivate, length 39
[mkv] |  + Language: und
[mkv] |  + Default duration: 33.367ms ( = 29.970 fps)
[mkv] | + a track...
[mkv] |  + Track number: 2
[mkv] |  + Track type: Audio
[mkv] |  + Audio track
[mkv] |   + Sampling frequency: 48000.000000
[mkv] |   + Channels: 6
[mkv] |  + Codec ID: A_AC3
[mkv] |  + Language: und
[mkv] |  + Default duration: 32.000ms ( = 31.250 fps)
[mkv] /---- [ parsing cues ] -----------
[mkv] \---- [ parsing cues ] -----------
[mkv] \---- [ parsing seek head ] ---------
[mkv] |+ found cluster, headers are parsed completely :)
==> Found video stream: 0
[mkv] Aspect: 2.352941
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
==> Found audio stream: 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Will play video track 1.
Detected file format: Matroska
[ass] Raster: FreeType 2.5.2
[ass] Shaper: FriBidi 0.19.6 (SIMPLE)
[ass] Initialized
get_path('fonts') -> '/home/techy/.mplayer/fonts'
get_path('subfont.ttf') -> '/home/techy/.mplayer/subfont.ttf'
[ass] Updating font cache
[V] filefmt:28  fourcc:0x31637661  size:1280x544  fps:29.970  ftime:=0.0334
Load subtitles in .
get_path('sub/') -> '/home/techy/.mplayer/sub/'
X11 opening display: :0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1920x1080 with depth 24 and 32 bpp (":0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[vdpau] Error when calling vdp_device_create_x11: 1
vo: uninit ...
X11 opening display: :0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1920x1080 with depth 24 and 32 bpp (":0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[VO_XV] Using Xv Adapter #0 (NV17 Video Texture)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 4096x4096
[vo] query(Planar YV12) -> 437
[ass] auto-open
Opening video decoder: [ffmpeg] libavcodec video codecs
Asking decoder to use 2 threads if supported.
Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [libavcodec]
Video codecs.conf entry: ffh264 (FFmpeg H.264)  vfm: ffmpeg
Opening audio decoder: [ffmpeg] libavcodec audio decoders
dec_audio: Allocating 8192 + 65536 = 73728 bytes for output buffer.
INFO: libavcodec "ac3" init OK!
(Re)initializing libavresample format conversion...
Selected audio codec: ATSC A/52A (AC-3) [libavcodec]
Audio codecs.conf entry: ffac3 (FFmpeg AC-3)  afm: ffmpeg
AUDIO: 48000 Hz, 2 ch, floatle, 448.0 kbit/14.58% (ratio: 56000->384000)
Building audio filter chain for 48000Hz/2ch/floatle -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/floatle
Audio filter chain:
  [in] 48000Hz/2ch/floatle
  [dummy] 48000Hz/2ch/floatle
  [out] 0Hz/0ch/??
[dummy] Was reinitialized: 48000Hz/2ch/floatle
Audio filter chain:
  [in] 48000Hz/2ch/floatle
  [dummy] 48000Hz/2ch/floatle
  [out] 0Hz/0ch/??
Trying every known audio driver...
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 48000Hz/2ch/floatle -> 48000Hz/2ch/floatle...
[dummy] Was reinitialized: 48000Hz/2ch/floatle
Audio filter chain:
  [in] 48000Hz/2ch/floatle
  [dummy] 48000Hz/2ch/floatle
  [out] 48000Hz/2ch/floatle
[dummy] Was reinitialized: 48000Hz/2ch/floatle
Audio filter chain:
  [in] 48000Hz/2ch/floatle
  [dummy] 48000Hz/2ch/floatle
  [out] 48000Hz/2ch/floatle
Starting playback...
[ffmpeg] aspect_ratio: 2.352941
VIDEO:  1280x544  29.970 fps    0.0 kbps ( 0.0 kB/s)
VDec: vo config request - 1280 x 544 (preferred colorspace: Planar YV12)
Trying filter chain: ass vo
VDec: using Planar YV12 as output csp (no 0)
VO Config (1280x544->1280x544,flags=0,0x32315659)
REQ: flags=0x437  req=0x0  
VO: [xv] 1280x544 => 1280x544 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 505 for hw scaling
xv_set_eq called! (bt_709, 100)
xv_get_eq called! (bt_709, 100)
*** [ass] Exporting mp_image_t, 1280x544x12bpp YUV planar, 1044480 bytes
*** [vo] Allocating mp_image_t, 1280x544x12bpp YUV planar, 1044480 bytes
Increasing filtered audio buffer size from 0 to 4096
Increasing filtered audio buffer size from 4096 to 69632
Increasing filtered audio buffer size from 69632 to 135168
Increasing filtered audio buffer size from 135168 to 200704
Increasing filtered audio buffer size from 200704 to 266240
Increasing filtered audio buffer size from 266240 to 331776
Increasing filtered audio buffer size from 331776 to 388096
A:   8.1 V:   8.1 A-V: -0.000 ct:  0.000   0/  0  9%  6%  2.4% 0 0 
Invalid command for bound key 'MOUSE_BTN0': 'dvdnav mouse'
A:  10.8 V:  10.8 A-V: -0.014 ct:  0.000   0/  0  9%  6%  2.0% 0 0 
Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: ffmpeg
Uninit video: ffmpeg
vo: uninit ...

Exiting... (Quit)


```

---

### Post by andrew.46 on 2014-04-10
Is playback better if you add the following to your commandline:

```
-ao alsa -vo xv
```

?

---

### Post by linuxyogi on 2014-04-10
> **andrew.46 said:**
> Is playback better if you add the following to your commandline:

```
-ao alsa -vo xv
```

?

No. Same playback issue.

---

