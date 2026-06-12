---
title: "What is the maximum video file size that a 128MB video card can handle?"
date: 2011-05-22
forum: The Cafe
---

### Post by brawnypandora0 on 2011-05-22
Whenever I watch a video that is 1GB or larger, the  video becomes very laggy with streaks across the monitor. Is this  always the case for video cards my size?

---

### Post by leviathan8 on 2011-05-22
Do you have an IGP? 
It happened to me once, that while I was browsing on some forums, a malevolent person posted a huge image (10000x10000 pixels in size) that crashed my laptop, which had 2 GB RAM and an Intel Graphics HD IGP, which I can't really guess how much VRAM has, but I think it's close to yours. I've asked other people regarding this issue, and the most clear answer was that I didn't had enough VRAM, so I guess your case is the same, yet you're playing a video.

---

### Post by Paqman on 2011-05-22
It's probably not down to the file size as such, but rather the resolution of the video. If it's a big file size is probably encoded for some kind of HD output (eg: 720p or 1080p). You can see the resolution if you right click on the file and go to "properties" and click on the last tab.

If your card can't handle output at that resolution you'll have to re-encode it to a lower one. [Arista Transcoder]("apt:arista") is a nice easy way to do this, it's in the repos. Re-encoding can take ages, especially if it's a big file and/or you're running 32-bit.

---

### Post by brawnypandora0 on 2011-05-22
> **Paqman said:**
> It's probably not down to the file size as such, but rather the resolution of the video. If it's a big file size is probably encoded for some kind of HD output (eg: 720p or 1080p). You can see the resolution if you right click on the file and go to "properties" and click on the last tab.

If your card can't handle output at that resolution you'll have to re-encode it to a lower one. [Arista Transcoder]("apt:arista") is a nice easy way to do this, it's in the repos. Re-encoding can take ages, especially if it's a big file and/or you're running 32-bit.

I'm a 32 bit. The file I have is 2GB. How long do you think I'd take?

---

### Post by Paqman on 2011-05-22
> **brawnypandora0 said:**
> I'm a 32 bit. The file I have is 2GB. How long do you think I'd take?

Quite a while (random unscientific guess: over an hour). Exactly how long depends on how fast your processor is, what the input and output formats are, and what codec is in use.

Install Arista and feed it the file, it'll tell you how long it expects to take.

---

