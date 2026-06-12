---
title: "Problem playing mp3 from webpage"
date: 2008-07-19
forum: Server Platforms
---

### Post by xshagy on 2008-07-19
I am trying to run a system command in a webpage with the following code.

```

#!/usr/bin/perl

print <<END;
Content-Type: text/html\n\n
<html>
<head></head>
<body>
END

system("mplayer 'song.mp3'");

print <<END;
</body>
</html>
END

```

If this file is run in terminal it plays the song and works fine but in a browser it displays the following

[html]
MPlayer 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ (Family: 15, Model: 107, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Terminal type `unknown' is not defined.

Playing song.mp3.
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
Opening /dev/dvb/adapter0/audio0
AO: [null] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 175.0 (02:55.0) ??,?%                                        
A:   0.0 (00.0) of 175.0 (02:55.0) ??,?%                                        
A:   0.1 (00.0) of 175.0 (02:55.0) ??,?%                                        
A:   0.1 (00.1) of 175.0 (02:55.0) ??,?%                                        
A:   0.2 (00.1) of 175.0 (02:55.0)  1.2%                                        
A:   0.2 (00.1) of 175.0 (02:55.0)  1.2%                                        
A:   0.2 (00.2) of 175.0 (02:55.0)  1.2%                                        
A:   0.3 (00.2) of 175.0 (02:55.0)  1.2%                                        

A:   0.3 (00.2) of 175.0 (02:55.0)  1.2%                                        
A:   0.3 (00.3) of 175.0 (02:55.0)  1.2%                                        
A:   0.4 (00.3) of 175.0 (02:55.0)  1.2%
[/html]

Seems like all the permissions are fine or it wouldn't display anything, right? What am I doing wrong?

---

### Post by cariboo on 2008-07-20
You should be using the mplayer plugin in Firefox to play your mp3 file. I use a program called gnump3d to stream mp3's from my server to any computer on my network. It is easy to setup and requires next to no maintenance.

Gnump3d is available from the repositories.

Jim

---

