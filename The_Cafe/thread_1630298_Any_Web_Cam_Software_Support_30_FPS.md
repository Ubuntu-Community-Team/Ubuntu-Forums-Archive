---
title: "Any Web Cam Software Support 30 FPS?"
date: 2010-11-25
forum: The Cafe
---

### Post by giddyup306 on 2010-11-25
I tried doing some searching, but all I found was Cheeze, and wxcam.  Anything better than these?  Even with the lowest res setting, these are still very sluggish.

---

### Post by czr114 on 2010-11-25
Does your cam support 30 FPS?

---

### Post by giddyup306 on 2010-11-25
> **czr114 said:**
> Does your cam support 30 FPS?

Yes. It's a Logitech Orbital AF.  The built in camera in my laptop isn't any worse as far as lagging with either of the programs mentioned.

---

### Post by MaindotC on 2010-11-25
[WebCamStudio]("http://www.ws4gl.org")

---

### Post by czr114 on 2010-11-25
> **giddyup306 said:**
> Yes. It's a Logitech Orbital AF.  The built in camera in my laptop isn't any worse as far as lagging with either of the programs mentioned.

That's weird, I could swear I pulled 30 from a Pro 9000 on cheese.

What resolution are you trying to capture at? I don't believe full HD can be done at 30 due to hardware limitations.

---

### Post by giddyup306 on 2010-11-25
> **czr114 said:**
> That's weird, I could swear I pulled 30 from a Pro 9000 on cheese.

What resolution are you trying to capture at? I don't believe full HD can be done at 30 due to hardware limitations.


160X120.  I hope I don't have any hardware problems.  I have some audio problems as well.  *kicks can*

---

### Post by joepie91 on 2010-11-25
Try using the "Streaming" feature in VLC Player, and stream from the Video4Linux2 stream to a file, preferably in OGG + Flac or OGG + Vorbis. You might want to check 'Display Locally' to have it display on screen as well, but it makes things slower and more sluggish. If you find a way to encode into WMV (yes, I know, blergh) that may help as well since apparently WMV encodes a lot faster, as demonstrated by Windows Media Encoder.

And of course check if your cam supports 30FPS, but since even my $14 Exoo cam supports it (means cheap stuff from China) I think it will.

Don't try this on an IDE drive by the way... your write speed will simply be too low to get anything like stutter-free video. SSD is best, regular SATA harddisk will work OK with the above settings in most cases. Also try to unfocus your camera a bit if that doesn't matter for the video, and try to resize the video to a slightly smaller resolution in the transcoding settings of VLC. That gives more chance of a succesful recording.

EDIT: Oh, capturing WILL be slower than simply displaying on-screen. Don't ask me why, but for some reason it is.

---

