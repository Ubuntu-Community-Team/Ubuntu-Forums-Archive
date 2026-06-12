---
title: "capturing with MIRO DC10 hangs system"
date: 2009-03-09
forum: Ubuntu Studio
---

### Post by ypsperf on 2009-03-09
I'm trying to capture a video stream from a Miro DC10+ card using lavrec; and it hangs the whole system after 2 o 3 seconds.
I've tested the card on XP and it works ok even at full resolution, so I've discarded a hardware issue.
Any ideas ?

Thanks.
Regards.
Facundo.
Buenos Aires.
Argentina.

---

### Post by ypsperf on 2009-03-10
Some more information.
With v4l2-ctl the driver reports 192x144 capture size capability when in fact it is ( as from the manual ) "720 x 480 • 640 x 480 • 720 x 576 • 768 x 576".
Another thing is that it does not recognize the "video_bitrate" parameter.
Might it be a driver issue ?
The loaded modules as seen with modconf are those for "MIRO DC10".
Any idea will be welcome.

Regards.
Facundo.
Buenos Aires.
Argentina.

---

### Post by ypsperf on 2009-03-11
Here is what v4l2-ctl --all shows.

Driver Info:
	Driver name   : zoran
	**Card type     : DC10plus[0]**
	Bus info      : PCI:0000:04:00.0
	Driver version: 2309
	Capabilities  : 0x04000007
		Video Capture
		Video Output
		Video Overlay
		Streaming
[B]Format Video Capture:
	Width/Height  : 192/144[/B]
	Pixel Format  : YUYV
	Field         : Top
	Bytes per Line: 384
	Size Image    : 55296
	Colorspace    : Broadcast NTSC/PAL (SMPTE170M/ITU601)
Format Video Output:
	Width/Height  : 768/288
	Pixel Format  : MJPG
	Field         : Sequential Bottom-Top
	Bytes per Line: 0
	Size Image    : 524288
	Colorspace    : Broadcast NTSC/PAL (SMPTE170M/ITU601)
Format Video Overlay:
	Left/Top    : 0/0
	Width/Height: 0/0
	Field       : Top
	Chroma Key  : 0x00000000
	Global Alpha: 0x00
	Clip Count  : 0
	Clip Bitmap : No
Framebuffer Format:
	Capability    : Clipping List
	Flags         : Overlay Matches Capture/Output Size
	Width         : 0
	Height        : 0
	Pixel Format  : 
	Bytes per Line: 0
	Size image    : 0
	Colorspace    : SRGB
Crop Capability Video Output:
	Bounds      : Left 0, Top 0, Width 768, Height 576
	Default     : Left 0, Top 0, Width 32, Height 24
	Pixel Aspect: 0/0
Video input : 0 (Composite)
Video output: 0 (Autodetect)
Video Standard = 0x000000ff
	PAL-B/B1/G/H/I/D/D1/K

Regards.
Facundo.
Buenos Aires.
Argentina.

---

