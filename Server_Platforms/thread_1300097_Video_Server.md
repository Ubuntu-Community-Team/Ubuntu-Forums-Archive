---
title: "Video Server"
date: 2009-10-24
forum: Server Platforms
---

### Post by stretch427 on 2009-10-24
Hi all! I don't know if this is possible, but I want to create a server on which I can host my videos and stream them from any computer. Does anyone know of a way I can go about this using a linux server platform?

Stretch

---

### Post by wsims2 on 2009-10-24
We need to know a little more about your setup. 

Are you looking to run a headless ubuntu server? 

Are you looking to only stream on your LAN?

Are your remotes windows, linux, or both?

I use ubuntu sever edition as a file and web sever. Apache streams my music ouside my LAN, and i use NFS on my LAN to share files locally. 

I also use mediatomb to stream media to my ps3.

---

### Post by R.Bucky on 2009-10-24
I have positive experiences with fuppes media server. It is a UPnP server that I had configured for streaming audio and video media, in addition for publishing images for viewing on my PS3.

---

### Post by stretch427 on 2009-10-24
Yes I'd like to run it headless, and as of now I was planning on using ubuntu 9.04 server ed.  I'd like to stream over the entire "interwebs" as it were, with both windows and linux. I have a file server already, But i'm wondering about streaming  video, if that is possible. 

As of now i havent set up this server so, i just have an empty box and i want to use it to store movies and stuff that i could stream.

---

### Post by stretch427 on 2009-10-25
Would you run fuppes on a desktop edition or would you use a server platform?

---

### Post by Lars Noodén on 2009-10-26
[VLC](http://www.videolan.org/vlc/streaming.html) can be set up to stream.  

So can [ffmpeg](http://ffmpeg.org/) and [icecast](http://www.icecast.org/faq.php)

All three are available for Ubuntu and can stream video.

---

### Post by FakeOutdoorsman on 2009-10-26
I use FFmpeg to encode my videos to H.264/AAC MP4.  I then run the encoded video through *qt-faststart* (part of FFmpeg) to prepare the video so it can start playing before it is completely downloaded.  I play the videos on a web page served by Apache using a custom Flash player, but I'm in the process of moving to [JW Player](http://www.longtailvideo.com/) to save development time.  Another good Flash player is [FlowPlayer](http://flowplayer.org/). This is all on a headless server.

I recommend encoding with FFmpeg/libx264 to H.264 video and AAC audio.  You will get excellent quality and it is well supported.  If you want the best quality I recommend compiling FFmpeg yourself.  Development in FFmpeg and x264 (the H.264 encoder FFmpeg uses) is very active and the repository versions lack some important features.  Instructions and usage examples are in this thread:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Lars Noodén on 2009-10-26
> **FakeOutdoorsman said:**
> 
I recommend encoding with FFmpeg/libx264 to H.264 video and AAC audio.  You will get excellent quality and it is well supported. 

You mentioned libx264 before.  I'll have to try rolling a package with the latest.  What about theora?  I'm really anxious to pick up where things left off before the WMV scandals in the EU and push for the most open formats available.

---

### Post by FakeOutdoorsman on 2009-10-26
> **Lars Noodén said:**
> You mentioned libx264 before.  I'll have to try rolling a package with the latest.  What about theora?  I'm really anxious to pick up where things left off before the WMV scandals in the EU and push for the most open formats available.

Theora can't compete with x264 in terms of output quality per bitrate.  See for yourself: [Open source codec comparison](http://saintdevelopment.com/media/).  I also read that multi-threading encoding isn't supported by Theora unlike x264, but I don't use Theora so I can't confirm this, but if you're encoding many videos or large ones, this is another loss for Theora.  Theora is based on an old design (VP3 from On2) which probably limits the room for any major improvements.

However, if it looks good enough for you (or more importantly your viewers) then go for it.  It's nice to have a choice.

---

