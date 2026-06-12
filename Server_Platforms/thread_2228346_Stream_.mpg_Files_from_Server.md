---
title: "Stream .mpg Files from Server"
date: 2014-06-06
forum: Server Platforms
---

### Post by palmerito0 on 2014-06-06
Hello, I'm currently looking for a way to stream video files from my server in a youtube-ish (i guess?) method. The files are Mpeg-5, and I'm running Ubuntu server 12.04
There should also be a way to automagically get the mounted and streaming. Also, the files streamed will be a few hours long, so it needs to be able to handle large files.

I've heard about the .flv with flash method, but I'm not sure about it because of decreasing support for flash on mobile devices. I've also heard about the Darwin quicktime server, so that might be an option.

Thanks in advance. :)

---

### Post by Lars Noodén on 2014-06-06
If you are going to stream mpeg files, you might look at [Iceast2](http://www.icecast.org/faq.php) or [VLC](http://www.videolan.org/doc/streaming-howto/en/).  I've read about Darwin, but it is not in the repository and the other two are.  Flash should be avoided for security and compatibility reasons, and it is just a wrapper anyway.

---

### Post by fatmann66 on 2014-06-06
are you streaming to one device or to multiple devices at once? on LAN or WAN / internet?  did you look into PLEX or PlayOn?

---

### Post by Gyokuro on 2014-06-08
You can stream with nginx: [http://nginx.org/en/docs/http/ngx_http_mp4_module.html](http://nginx.org/en/docs/http/ngx_http_mp4_module.html) but this depends what you want to do. For streaming at home apps like minidlna or ps3media server or the already mentioned vlc, Icecast2 are better suited.

---

### Post by palmerito0 on 2014-06-08
Thank you for all the replies, the streaming would be over the internet accessible from anywhere and stream in-browser. There probably would be only one viewer at a time.

---

### Post by palmerito0 on 2014-06-08
Thank you for all the replies! I'll be checking each of the methods you suggested. I'm sorry if I was unclear, but you should be able to play the stream_* in browser.*_

> **fatmann66 said:**
> are you streaming to one device or to multiple devices at once? on LAN or WAN / internet? did you look into PLEX or PlayOn?

It would stream to one device at a time. I would prefer the videos to play in browser and not be on a 3rd party cloud for security reasons, ruling out PLEX and PlayON.

> **Lars Noodén said:**
> If you are going to stream mpeg files, you might look at [Iceast2]("http://www.icecast.org/faq.php") or [VLC]("http://www.videolan.org/doc/streaming-howto/en/"). I've read about Darwin, but it is not in the repository and the other two are. Flash should be avoided for security and compatibility reasons, and it is just a wrapper anyway.

Can IceCast stream video? The website says it only streams audio.

> **Lars Noodén said:**
> If you are going to stream mpeg files, you might look at [Iceast2]("http://www.icecast.org/faq.php") or [VLC]("http://www.videolan.org/doc/streaming-howto/en/"). I've read about Darwin, but it is not in the repository and the other two are. Flash should be avoided for security and compatibility reasons, and it is just a wrapper anyway.

Can't Icecast only stream audio? Also, does the VLC method have to be played in the VLC player?

> **Gyokuro said:**
> You can stream with nginx: [http://nginx.org/en/docs/http/ngx_http_mp4_module.html](http://nginx.org/en/docs/http/ngx_http_mp4_module.html) but this depends what you want to do. For streaming at home apps like minidlna or ps3media server or the already mentioned vlc, Icecast2 are better suited.

So, with nginx all the client needs is a flash player like Adobe Flash? I'm sorry if it sounds stupid but I'm a noob. If so, I think I'll go with nginx.

---

### Post by palmerito0 on 2014-06-13
Found my answer: [Video.js]("http://www.videojs.com/"). Just what I was looking for!

---

