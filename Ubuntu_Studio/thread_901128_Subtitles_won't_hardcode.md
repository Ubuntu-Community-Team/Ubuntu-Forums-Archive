---
title: "Subtitles won't hardcode?"
date: 2008-08-26
forum: Ubuntu Studio
---

### Post by HangukMiguk on 2008-08-26
I'm getting absolutely frustrated by this.

I have downloaded (and checked) my subtitle files in VLC.  They work.  They show up onscreen, and they are in sync with the video.  However, whenever I try to pass the option in mencoder to include subtitles, and open up the video file in VLC or on my Xbox 360, it shows up with no subtitles.

here is the output from mencoder (which is showing that it detects, and extracts, subtitles):

```
mencoder 'xxxxxxxxxx.avi' -ovc copy -oac copy -sub 'xxxxxxxxxxx.srt'
Mencoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) Processor (Family: 6, Model: 4, Stepping: 2)
CPUflags: Type: 6 MMX: 1 MMx2: 1 3DNo2: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled with runtime CPU detection
success: format: 0 data: 0x0 - 0x2bb55000
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO: [XVID] 560x320 12bpp 23.976 fps 575.9 kbps (70.3 kbytes/s)
[V] filefmt:3 fourcc:0x44495658 size 560:320 fps:23.98 ftime:=0.0417
SUB: Detected subtitle file format: subviewer
SUB: Read 1300 subtitles
SUB: Adjusted 6 subtitle(s).
videocodec: framecopy (560x320 12bpp fourcc=44495658)
audiocodec: framecopy (format=55 chans=2 rate=48000 bits=0 B/s=15189 sample-0
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing index...80f (101%) 869.42fps Trem: 0min 862mb A-V:0.040 [575:121]
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 575.864 kbit/s (71983 B/s) size: 894694742 bytes 8261.595 sec 198080 frames

Audio stream: 121.510 kbit/s (15188 B/s) size: 125483376 bytes 8261.592 sec
```

I have also tried using the Subtitler filter in Avidemux, with the same result.

Help me please.

---

### Post by Irony on 2008-08-26
Paste this into a text file like gedit, save it then give the file an extension of . a s s (without the spaces, I did that because the Ubuntu filter here thinks its a rude word);

```
&#65279;[Script Info]
Title: <untitled>
Original Script: <unknown>
Script Type: v4.00+
PlayResX: 0
PlayResY: 0
PlayDepth: 0

[V4+ Styles]
Format: Name, Fontname, Fontsize, PrimaryColour, SecondaryColour, OutlineColour, BackColour, Bold, Italic, Underline, StrikeOut, ScaleX, ScaleY, Spacing, Angle, BorderStyle, Outline, Shadow, Alignment, MarginL, MarginR, MarginV, Encoding
Style: Default,Tahoma,14,&H00FFFFFF,&H00FFFFFF,&H00000000,&H00000000,-1,0,0,0,100,100,0,0.00,1,1,0,2,0,0,0,1

[Events]
Format: Layer, Start, End, Style, Actor, MarginL, MarginR, MarginV, Effect, Text
Dialogue: 0,0:00:00.00,0:00:31.21,Default,,0005,0305,0100,,Hello
Dialogue: 0,0:00:31.22,0:03:00.00,Default,,0005,0305,0100,,Hello again
Dialogue: 0,0:00:00.00,0:03:00.00,Default,,0005,0305,0090,,Is it working
Dialogue: 0,0:00:00.00,0:03:00.00,Default,,0315,0000,0100,,On the other side
```

Then in avidemux choose the subtitler option and add the file - manually edit the file with the words you want.

---

### Post by dodle on 2008-10-04
What format are you subtitles in?

---

