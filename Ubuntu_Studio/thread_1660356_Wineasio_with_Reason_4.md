---
title: "Wineasio with Reason 4"
date: 2011-01-05
forum: Ubuntu Studio
---

### Post by Peter7K on 2011-01-05
I've installed the wineasio-beta package from the falkTX ppa (0.9.0~beta0-1).  In winecfg I've enabled both ALSA and JACK audio.  I start up JACK and then open Reason 4.  After getting an error saying the sound device cannot be found, I go to the preferences and change it to "ASIO Wine Driver", and it gets a nice little green check mark next to it afterwards.  However, I hear zero sound.  Am I doing something wrong?  Thanks.

---

### Post by Totalchaos on 2011-01-05
> **Peter7K said:**
> I've installed the wineasio-beta package from the falkTX ppa (0.9.0~beta0-1).  In winecfg I've enabled both ALSA and JACK audio.  I start up JACK and then open Reason 4.  After getting an error saying the sound device cannot be found, I go to the preferences and change it to "ASIO ASIO4ALL V2", and it gets a nice little green check mark next to it afterwards.  However, I hear zero sound.  Am I doing something wrong?  Thanks.

Yes you are. Asio4all is a Windows only lowlatency driver.
Wineasio makes possible to connect windows apps (like Reaper, FlStudio etc..)as JACK clients. I can recommend you instead of using wineasio-beta try Wineasio0.7.5, i am still using it and it never let's me down.
For stable work of windows apps on linux, and wineasio, it's recommended to use 32bit OS instead of 64bit OS. (it's not a law, just recommendation) 

cheers Biser ):P

---

### Post by Peter7K on 2011-01-05
Oh and I forgot to mention, I *did* do "regsvr32 wineasio.dll" to register the dll.

Right now I get the following error with Reason4:
Sound driver problem, the sound driver used in the previous session could not be opened.

I hit okay, and it loads.

Now I go to preferences and Audio to select the audio device (note Reason at extremely low latency but runs okay using just ALSA)... 

I select ASIO Wine ASIO Driver (not ASIO4All)

I go to play a few notes and the volume goes up as it should naturally but no sound is heard.  I've included a screenshot of Reason, the Audio Preferences, Jack connections and Jack open.

---

### Post by Peter7K on 2011-01-06
UPDATE: Installed Reason 5 today, working equally well with ALSA as reason 4 did (92 latency).

However, in Reason 5, I enabled WINEASIO and I could actually hear notes!  However it soon crashed..

```
19:51:24.761 Patchbay deactivated.
19:51:24.778 Statistics reset.
19:51:24.832 JACK is starting...
19:51:24.833 /usr/bin/jackd -u -dalsa -dhw:0 -r44100 -p1024 -n2 -m -H
19:51:24.839 ALSA connection graph change.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2702019
no message buffer overruns
JACK compiled with System V SHM support.
19:51:24.868 JACK was started with PID=2411.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|hwmon|swmeter|-|32bit
control device hw:0
19:51:25.035 ALSA connection change.
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
19:51:27.049 Server configuration saved to "/home/peter/.jackdrc".
19:51:27.053 Statistics reset.
19:51:27.098 Client activated.
19:51:27.099 JACK connection change.
19:51:27.101 JACK connection graph change.
19:51:32.933 JACK connection graph change.
19:51:33.107 JACK connection change.
19:52:10.035 JACK connection graph change.
19:52:10.150 JACK connection change.
subgraph starting at wine_jack_out_8 timed out (subgraph_wait_fd=48, status = 0, state = Finished, pollret = 0 revents = 0x0)
19:53:00.984 JACK connection graph change.
**** alsa_pcm: xrun of at least 1.755 msecs
19:53:01.023 XRUN callback (1).
19:53:01.037 JACK connection change.
subgraph starting at wine_jack_out_9 timed out (subgraph_wait_fd=45, status = 0, state = Triggered, pollret = 0 revents = 0x0)
19:54:22.098 XRUN callback (2).
19:54:22.099 JACK connection graph change.
**** alsa_pcm: xrun of at least 1.605 msecs
subgraph starting at wine_jack_out_9 lost client
bad status (-2) for client wine_jack_out_9 handling event (type = 8)
cannot send event to client [wine_jack_out_7] (Broken pipe)
bad status (1) for client wine_jack_out_7 handling event (type = 8)
cannot send event to client [wine_jack_out_5] (Broken pipe)
bad status (1) for client wine_jack_out_5 handling event (type = 8)
cannot send event to client [wine_jack_out_3] (Broken pipe)
bad status (1) for client wine_jack_out_3 handling event (type = 8)
cannot send event to client [wine_jack_out_1] (Broken pipe)
bad status (1) for client wine_jack_out_1 handling event (type = 8)
cannot send event to client [wine_jack_out_2] (Broken pipe)
bad status (1) for client wine_jack_out_2 handling event (type = 8)
cannot send event to client [wine_jack_out_4] (Broken pipe)
bad status (1) for client wine_jack_out_4 handling event (type = 8)
cannot send event to client [wine_jack_out_6] (Broken pipe)
19:54:22.103 JACK connection change.
bad status (1) for client wine_jack_out_6 handling event (type = 8)
cannot send event to client [wine_jack_out_8] (Broken pipe)
bad status (1) for client wine_jack_out_8 handling event (type = 8)
**** alsa_pcm: xrun of at least 52.753 msecs
19:54:23.506 XRUN callback (1 skipped).
```

EDIT: Drat it looks like I got over-excited.. it seems that Reason 5 is incredibly unstable when running in wineasio:
Here's what happens when I run Reason in the terminal with jack:
```
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/libX11.so.6.3.0
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
cannot use real-time scheduling (FIFO at priority 5) [for thread 2093923184, from thread 2093923184] (1: Operation not permitted)
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/winejack.drv.so
unlocking /usr/lib/wine/winejack.drv.so
unlocking /usr/lib/wine/winejack.drv.so
unlocking /usr/lib/wine/winejack.drv.so
unlocking /usr/lib/wine/msacm32.drv.so
unlocking /usr/lib/wine/msacm32.drv.so
unlocking /usr/lib/wine/msacm32.drv.so
unlocking /usr/lib/wine/msacm32.drv.so
unlocking /usr/lib/libwine.so.1.0
unlocking /usr/lib/wine/psapi.dll.so
unlocking /usr/lib/wine/psapi.dll.so
unlocking /usr/lib/wine/psapi.dll.so
unlocking /usr/lib/wine/psapi.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/libX11.so.6.3.0
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
cannot use real-time scheduling (FIFO at priority 5) [for thread 2091064176, from thread 2091064176] (1: Operation not permitted)
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/winejack.drv.so
unlocking /usr/lib/wine/winejack.drv.so
unlocking /usr/lib/wine/winejack.drv.so
unlocking /usr/lib/wine/winejack.drv.so
unlocking /usr/lib/wine/msacm32.drv.so
unlocking /usr/lib/wine/msacm32.drv.so
unlocking /usr/lib/wine/msacm32.drv.so
unlocking /usr/lib/wine/msacm32.drv.so
unlocking /usr/lib/libwine.so.1.0
unlocking /usr/lib/wine/psapi.dll.so
unlocking /usr/lib/wine/psapi.dll.so
unlocking /usr/lib/wine/psapi.dll.so
unlocking /usr/lib/wine/psapi.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/libX11.so.6.3.0
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
cannot use real-time scheduling (FIFO at priority 5) [for thread 2088205168, from thread 2088205168] (1: Operation not permitted)
fixme:process:GetLogicalProcessorInformation (0x3228d20,0x22388a4): stub
fixme:uxtheme:BufferedPaintInit Stub ()
fixme:uxtheme:BeginBufferedPaint Stub (0x658 0x223ca68 0 (nil) 0x223ca98)
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:process:GetLogicalProcessorInformation (0x647c538,0x223d31c): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x798ea20): stub
fixme:process:GetLogicalProcessorInformation (0x6490d08,0x2238038): stub
fixme:process:GetLogicalProcessorInformation (0x64910e8,0x2238038): stub
fixme:avrt:AvRevertMmThreadCharacteristics (0x12345678): stub
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/dsound.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/msacm32.dll.so
unlocking /usr/lib/wine/winejack.drv.so
unlocking /usr/lib/wine/winejack.drv.so
unlocking /usr/lib/wine/winejack.drv.so
unlocking /usr/lib/wine/winejack.drv.so
unlocking /usr/lib/wine/msacm32.drv.so
unlocking /usr/lib/wine/msacm32.drv.so
unlocking /usr/lib/wine/msacm32.drv.so
unlocking /usr/lib/wine/msacm32.drv.so
unlocking /usr/lib/libwine.so.1.0
unlocking /usr/lib/wine/psapi.dll.so
unlocking /usr/lib/wine/psapi.dll.so
unlocking /usr/lib/wine/psapi.dll.so
unlocking /usr/lib/wine/psapi.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/winmm.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/user32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/comctl32.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/shlwapi.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/uxtheme.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/rpcrt4.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/shell32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/ole32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/imm32.dll.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winspool.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/wine/winex11.drv.so
unlocking /usr/lib/libX11.so.6.3.0
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/localspl.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/spoolss.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/midimap.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/advapi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/gdi32.dll.so
unlocking /usr/lib/wine/wineasio.dll.so
unlocking /usr/lib/wine/wineasio.dll.so
unlocking /usr/lib/wine/wineasio.dll.so
unlocking /usr/lib/wine/wineasio.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/comdlg32.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/version.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/msimg32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/kernel32.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
unlocking /usr/lib/wine/ntdll.dll.so
cannot use real-time scheduling (FIFO at priority 5) [for thread 63372144, from thread 63372144] (1: Operation not permitted)
fixme:process:GetLogicalProcessorInformation (0x65007b0,0x223d270): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x7d6e9e8): stub
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:uxtheme:BufferedPaintInit Stub ()
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0xee0e9e8): stub
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:uxtheme:BufferedPaintUnInit Stub ()
fixme:uxtheme:BufferedPaintInit Stub ()
fixme:uxtheme:BufferedPaintInit Stub ()
fixme:uxtheme:BufferedPaintUnInit Stub ()
jack_client_thread zombified - exiting from JACK

```

ZOMBIED! Jack MSGS:
```
20:02:35.755 Patchbay deactivated.
20:02:35.761 Statistics reset.
20:02:35.786 JACK is starting...
20:02:35.786 /usr/bin/jackd -u -dalsa -dhw:0 -r44100 -p1024 -n2 -m -H
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    2702019
20:02:35.793 ALSA connection graph change.
20:02:35.793 JACK was started with PID=3134.
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|hwmon|swmeter|-|32bit
control device hw:0
20:02:35.988 ALSA connection change.
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
20:02:37.993 Server configuration saved to "/home/peter/.jackdrc".
20:02:37.995 Statistics reset.
20:02:38.029 Client activated.
20:02:38.030 JACK connection change.
20:02:38.031 JACK connection graph change.
20:03:00.774 JACK connection graph change.
20:03:00.844 JACK connection change.
20:03:00.846 JACK connection graph change.
20:03:01.045 JACK connection change.
20:03:01.046 JACK connection graph change.
20:03:01.248 JACK connection change.
20:03:03.388 JACK connection graph change.
20:03:03.453 JACK connection change.
subgraph starting at wine_jack_out_9 timed out (subgraph_wait_fd=48, status = 0, state = Finished, pollret = 0 revents = 0x0)
20:03:08.661 JACK connection graph change.
**** alsa_pcm: xrun of at least 1.610 msecs
20:03:08.702 XRUN callback (1).
20:03:08.859 JACK connection change.
```

---

### Post by sgx on 2011-01-08
> **Peter7K said:**
> I've installed the wineasio-beta package from the falkTX ppa (0.9.0~beta0-1).  In winecfg I've enabled both ALSA and JACK audio.  I start up JACK and then open Reason 4.  After getting an error saying the sound device cannot be found, I go to the preferences and change it to "ASIO Wine Driver", and it gets a nice little green check mark next to it afterwards.  However, I hear zero sound.  Am I doing something wrong?  Thanks.

Hi, a few things, install a2jmidid

Untick jackd in the winecfg. Tick only alsa.

reboot

start qjackctl

The icons shaped like > by the Input device and output device,
on the setup page, click these to insure you have the right soundcard selected.

run the command:

a2jmidid -j default

note the additional entries available in the qjackctl tabs
experimenting with the various connections.

start wine and reason, hope for the best, continue experiments.

Cheers

---

### Post by Peter7K on 2011-01-08
> **sgx said:**
> Hi, a few things, install a2jmidid

Untick jackd in the winecfg. Tick only alsa.

reboot

start qjackctl

The icons shaped like > by the Input device and output device,
on the setup page, click these to insure you have the right soundcard selected.

run the command:

a2jmidid -j default

note the additional entries available in the qjackctl tabs
experimenting with the various connections.

start wine and reason, hope for the best, continue experiments.

Cheers

Thanks for the assistance.  It appears that Reason 5 becomes nonresponsive pretty quickly, the same as before.

However, (I did already have a2jmidid installed) I didn't notice any additional tabs pop up when I started a2jmidid... More tabs are supposed to come up on top Settings Options Display Misc.. tabs are the only ones present whether I have a2jmidid started or not.

---

### Post by sgx on 2011-01-09
Hi, I should have said a2jmidid displays a new connection in the midi tab
of the connect panel. :oops:

---

### Post by Peter7K on 2011-01-09
It liiiives!  I just recorded audio from Reason in Ardour!  (I reduced the latency of the JACK server so it didn't crash this time)

Thanks for the help!

---

### Post by sgx on 2011-01-09
Thats great news, Reason is a bit of a parallel universe, like
the Native Instruments Reaktor. A good source of sounds for Ardour. :)

---

### Post by Peter7K on 2011-01-14
Sadly it seems that it won't run at any speed decent.. the delay will be really annoying for working with the midi keyboard but oh well it's better than nothing.

---

