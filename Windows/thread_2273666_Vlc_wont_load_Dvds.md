---
title: "Vlc wont load Dvds"
date: 2015-04-14
forum: Windows
---

### Post by josh127 on 2015-04-14
When i load up dvds with vlc it attempts load but then stops and doesnt end up loading the dvd. this is what the debug looks like 

```


core debug: adding item `dvd:///D:/' ( dvd:///D:/ )
core debug: processing request item: dvd:///D:/, node: null, skip: 0
core debug: rebuilding array of current - root Playlist
core debug: rebuild done - 5 items, index 4
core debug: starting playback of the new playlist item
core debug: resyncing on dvd:///D:/
core debug: dvd:///D:/ is at 4
core debug: creating new input thread
core debug: Creating an input for 'dvd:///D:/'
core debug: requesting art for dvd:///D:/
core debug: meta ok for (null), need to fetch art
core debug: using timeshift granularity of 50 MiB, in path 'C:\Users\PROJEC~1\AppData\Local\Temp'
core debug: `dvd:///D:/' gives access `dvd' demux `' path `/D:/'
core debug: specified demux `any'
core debug: creating demux: access='dvd' demux='any' location='/D:/' file='D:\'
core debug: looking for meta fetcher module matching "any": 1 candidates
core debug: looking for access_demux module matching "dvd": 12 candidates
lua debug: Trying Lua scripts in C:\Users\ProjectEvo\AppData\Roaming\vlc\lua\meta\fetcher
core debug: looking for meta fetcher module matching "any": 1 candidates
lua debug: Trying Lua scripts in C:\Program Files (x86)\VideoLAN\VLC\lua\meta\fetcher
lua debug: Trying Lua playlist script C:\Program Files (x86)\VideoLAN\VLC\lua\meta\fetcher\tvrage.luac
lua debug: Trying Lua scripts in C:\Users\ProjectEvo\AppData\Roaming\vlc\lua\meta\fetcher
lua debug: Trying Lua scripts in C:\Program Files (x86)\VideoLAN\VLC\lua\meta\fetcher
lua debug: Trying Lua playlist script C:\Program Files (x86)\VideoLAN\VLC\lua\meta\fetcher\tvrage.luac
lua debug: skipping script (unmatched scope) C:\Program Files (x86)\VideoLAN\VLC\lua\meta\fetcher\tvrage.luac
core debug: no meta fetcher modules matched
core debug: searching art for dvd:///D:/
core debug: looking for art finder module matching "any": 2 candidates
lua debug: skipping script (unmatched scope) C:\Program Files (x86)\VideoLAN\VLC\lua\meta\fetcher\tvrage.luac
core debug: no meta fetcher modules matched
core debug: searching art for dvd:///D:/
core debug: looking for art finder module matching "any": 2 candidates
lua debug: Trying Lua scripts in C:\Users\ProjectEvo\AppData\Roaming\vlc\lua\meta\art
lua debug: Trying Lua scripts in C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art
lua debug: Trying Lua playlist script C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\00_musicbrainz.luac
lua debug: Trying Lua scripts in C:\Users\ProjectEvo\AppData\Roaming\vlc\lua\meta\art
lua debug: Trying Lua scripts in C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art
lua debug: Trying Lua playlist script C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\00_musicbrainz.luac
lua debug: skipping script (unmatched scope) C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\00_musicbrainz.luac
lua debug: Trying Lua playlist script C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\01_googleimage.luac
lua debug: skipping script (unmatched scope) C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\00_musicbrainz.luac
lua debug: Trying Lua playlist script C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\01_googleimage.luac
lua debug: skipping script (unmatched scope) C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\01_googleimage.luac
lua debug: Trying Lua playlist script C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\02_frenchtv.luac
lua debug: skipping script (unmatched scope) C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\01_googleimage.luac
lua debug: Trying Lua playlist script C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\02_frenchtv.luac
lua debug: skipping script (unmatched scope) C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\02_frenchtv.luac
lua debug: Trying Lua playlist script C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\03_lastfm.luac
lua debug: skipping script (unmatched scope) C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\02_frenchtv.luac
lua debug: Trying Lua playlist script C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\03_lastfm.luac
lua debug: skipping script (unmatched scope) C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\03_lastfm.luac
core debug: no art finder modules matched
core debug: art not found for dvd:///D:/
lua debug: skipping script (unmatched scope) C:\Program Files (x86)\VideoLAN\VLC\lua\meta\art\03_lastfm.luac
core debug: no art finder modules matched
core debug: art not found for dvd:///D:/
qt4 debug: IM: Setting an input
dvdnav debug: trying to go to dvd menu
core debug: using access_demux module "dvdnav"
core debug: looking for meta reader module matching "any": 2 candidates
lua debug: Trying Lua scripts in C:\Users\ProjectEvo\AppData\Roaming\vlc\lua\meta\reader
lua debug: Trying Lua scripts in C:\Program Files (x86)\VideoLAN\VLC\lua\meta\reader
lua debug: Trying Lua playlist script C:\Program Files (x86)\VideoLAN\VLC\lua\meta\reader\filename.luac
core debug: no meta reader modules matched
core debug: `dvd:///D:/' successfully opened
dvdnav debug: DVDNAV_HOP_CHANNEL
core error: ES_OUT_RESET_PCR called
dvdnav debug: DVDNAV_VTS_CHANGE
dvdnav debug: - vtsN=1
dvdnav debug: - domain=8
core error: ES_OUT_RESET_PCR called
dvdnav debug: DVDNAV_CELL_CHANGE
dvdnav debug: - cellN=1
dvdnav debug: - pgN=1
dvdnav debug: - cell_length=668
dvdnav debug: - pg_length=668
dvdnav debug: - pgc_length=4053600
dvdnav debug: - cell_start=0
dvdnav debug: - pg_start=0
dvdnav debug: DVDNAV_SPU_CLUT_CHANGE
dvdnav debug: DVDNAV_SPU_STREAM_CHANGE
dvdnav debug: - physical_wide=0
dvdnav debug: - physical_letterbox=0
dvdnav debug: - physical_pan_scan=1
dvdnav debug: buttonUpdate not done b=1 t=0
core debug: selecting program id=0
core debug: looking for decoder module matching "any": 43 candidates
core debug: using decoder module "spudec"
spudec debug: invalid starting packet (size 
spudec debug: spu size: 0, i_pts: 0 i_buffer: 128
dvdnav debug: DVDNAV_AUDIO_STREAM_CHANGE
dvdnav debug: - physical=0
core debug: Buffering 0%
dvdnav debug: buttonUpdate 1
core debug: Buffering 0%
core debug: looking for decoder module matching "any": 43 candidates
avcodec debug: CPU flags: 0x01035fdb
avcodec debug: trying to use direct rendering
avcodec debug: allowing 4 thread(s) for decoding
avcodec warning: threaded frame decoding is not compatible with DXVA2, disabled
avcodec debug: avcodec codec (MPEG-1/2 Video) started
core debug: using decoder module "avcodec"
core debug: looking for packetizer module matching "any": 23 candidates
core debug: using packetizer module "packetizer_mpegvideo"
dvdnav debug: buttonUpdate 1
dvdnav warning: cannot get next block (Error reading from DVD.)
dvdnav debug: jumping to first title
dvdnav debug: DVDNAV_HOP_CHANNEL
core error: ES_OUT_RESET_PCR called
spudec debug: invalid starting packet (size 
spudec debug: spu size: 0, i_pts: 0 i_buffer: 128
packetizer_mpegvideo debug: size 720x576 fps=25.000
dvdnav debug: DVDNAV_VTS_CHANGE
dvdnav debug: - vtsN=1
dvdnav debug: - domain=2
core error: ES_OUT_RESET_PCR called
spudec debug: invalid starting packet (size 
spudec debug: spu size: 0, i_pts: 0 i_buffer: 128
core debug: removing module "avcodec"
avcodec debug: ffmpeg codec (MPEG-1/2 Video) stopped
core debug: killing decoder fourcc `mpgv', 0 PES in FIFO
core debug: removing module "packetizer_mpegvideo"
core debug: removing module "spudec"
core debug: killing decoder fourcc `spu ', 0 PES in FIFO
core debug: Program doesn't contain anymore ES
dvdnav debug: DVDNAV_CELL_CHANGE
dvdnav debug: - cellN=1
dvdnav debug: - pgN=1
dvdnav debug: - cell_length=177869
dvdnav debug: - pg_length=177869
dvdnav debug: - pgc_length=379753200
dvdnav debug: - cell_start=0
dvdnav debug: - pg_start=0
dvdnav debug: DVDNAV_SPU_CLUT_CHANGE
dvdnav debug: DVDNAV_SPU_STREAM_CHANGE
dvdnav debug: - physical_wide=128
dvdnav debug: - physical_letterbox=128
dvdnav debug: - physical_pan_scan=128
dvdnav debug: buttonUpdate not done b=1 t=1
dvdnav debug: DVDNAV_AUDIO_STREAM_CHANGE
dvdnav debug: - physical=0
core debug: Buffering 0%
dvdnav debug: buttonUpdate not done b=1 t=1
core debug: Buffering 0%
core debug: looking for decoder module matching "any": 43 candidates
avcodec debug: CPU flags: 0x01035fdb
avcodec debug: trying to use direct rendering
avcodec debug: allowing 4 thread(s) for decoding
avcodec warning: threaded frame decoding is not compatible with DXVA2, disabled
avcodec debug: avcodec codec (MPEG-1/2 Video) started
core debug: using decoder module "avcodec"
core debug: looking for packetizer module matching "any": 23 candidates
core debug: using packetizer module "packetizer_mpegvideo"
dvdnav debug: buttonUpdate not done b=1 t=1
packetizer_mpegvideo debug: size 720x576 fps=25.000
dvdnav warning: cannot get next block (Error reading from DVD.)
core debug: finished input
core debug: finished input
core debug: removing module "avcodec"
avcodec debug: ffmpeg codec (MPEG-1/2 Video) stopped
core debug: killing decoder fourcc `mpgv', 0 PES in FIFO
core debug: removing module "packetizer_mpegvideo"
core debug: removing module "dvdnav"
core debug: Program doesn't contain anymore ES
core debug: dead input
core debug: changing item without a request (current 4/5)
core debug: nothing to play
qt4 debug: IM: Deleting the input
```

I am new to doing this sort of stuff.

---

### Post by mc4man on 2015-04-14
You may want to explain what the connection to Ubuntu is here. What you've posted concerns a Windows version of vlc.

---

### Post by josh127 on 2015-04-14
Oh, i thought i could seek for help, because i saw anther person seek for help here with a close problem to mine.

---

### Post by howefield on 2015-04-14
Code tags added to the OP and thread moved to the "*Windows*" forum.

---

