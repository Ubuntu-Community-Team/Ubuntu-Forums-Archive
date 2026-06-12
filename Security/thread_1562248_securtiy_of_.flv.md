---
title: "securtiy of .flv"
date: 2010-08-27
forum: Security
---

### Post by kiridude on 2010-08-27
I'm wondering if saved .flv files on my drive are a security hazard. I know that flash has various security holes, but what about the many videos I have saved from various sites? should i delete them all?

---

### Post by linux18 on 2010-08-27
videos on your hard drive should be perfectly safe if they wern't malicious from the start, but if you wan't, you could just convert them to mp4 using handbrake or ffmpeg

---

### Post by kiridude on 2010-08-27
Thanks for your reply.

If some, or one, was malicious from the start, and I converted it to mp4, would that neutralize the threat?

---

### Post by linux18 on 2010-08-27
yes, because mp4 doesn't use the buggy insecure flash player

---

### Post by styxcoverbnd on 2010-08-27
> **linux18 said:**
> yes, because mp4 doesn't use the buggy insecure flash player

I'm not sure about that, but your still missing the part before that, ie a malicious file was already downloaded to a system which would infect it

---

### Post by cdenley on 2010-08-27
> **linux18 said:**
> yes, because mp4 doesn't use the buggy insecure flash player

I believe both mp4 and flv video files residing on the local filesystem play with the totem media player by default. Either format can potentially exploit a vulnerability in the gstreamer decoder, but this is very unlikely. Playing streaming video in your browser using the flash plugin might not be very secure, but I don't believe there is anything inherently insecure about the flv file format. It all depends on the media player you use to play it, and the decoders used.

---

### Post by Linuxforall on 2010-08-27
Play them with mplayer in that case, its way more secure as it doesnt' use gstreamer.

---

### Post by kiridude on 2010-08-29
> **cdenley said:**
> I believe both mp4 and flv video files residing on the local filesystem play with the totem media player by default. Either format can potentially exploit a vulnerability in the gstreamer decoder, but this is very unlikely. Playing streaming video in your browser using the flash plugin might not be very secure, but I don't believe there is anything inherently insecure about the flv file format. It all depends on the media player you use to play it, and the decoders used.

Yes, I've never had any problems with viruses or malware (that I am aware of). I use vlc as it seems to play all videos. What decoders and what player do you suggest?

> Linuxforall  	
Re: securtiy of .flv
Play them with mplayer in that case, its way more secure as it doesnt' use gstreamer. 

Mplayer seems to not play some videos. Not sure why...?

---

