---
title: "Ubuntu Server - Change Web Player?"
date: 2011-02-03
forum: Server Platforms
---

### Post by MtnDew on 2011-02-03
Hello,

I finally got the server running. All seems OKAY, however I want to change the default player on my server. As of now, when I upload a file, it plays but has no "play/pause/stop/mute/fullscreen" buttons. How do I get those? I've tried installing FFMPEG, MPlayer and a few others to no avail. Please suggest a tried&true method of allowing for this. I need it to be able to at least play audio(mp3) and video(mp4,wmv,avi,flv)

Ubuntu 64 Bit
Apache 2.0
PHP5


Any commands &| articles would be great. I'm not a Linux genius, please don't speak to me as if I am :P

-MtnDew

---

### Post by WinstonChurchill on 2011-02-03
> **MtnDew said:**
> Hello,

I finally got the server running. All seems OKAY, however I want to change the default player on my server. As of now, when I upload a file, it plays but has no "play/pause/stop/mute/fullscreen" buttons. How do I get those? I've tried installing FFMPEG, MPlayer and a few others to no avail. Please suggest a tried&true method of allowing for this. I need it to be able to at least play audio(mp3) and video(mp4,wmv,avi,flv)

Ubuntu 64 Bit
Apache 2.0
PHP5


Any commands &| articles would be great. I'm not a Linux genius, please don't speak to me as if I am :P

-MtnDew
Can you be a little clearer about exactly what you're trying to do here? It sounds like you have a server hooked up to a sound system and you're trying to get it to play music/videos, but that doesn't really make sense since a server install of Ubuntu doesn't have any GUI components... are you accessing files on the server with another computer? Like through a web browser or something? If so, it's that computer that isn't doing what you want, not the server.

---

### Post by Thirtysixway on 2011-02-03
Did you install ubuntu-desktop and you're trying touse something like vlc?

---

### Post by MtnDew on 2011-02-03
Sorry for being unclear.

I have an Ubuntu Server 10.10. I am currently on my other computer on my network. All access the internet. I am going to push my full website over to this server (this has worked well so far with the port forwarding,etc). Now, when I upload a video to my web server via FTP (server has no GUI) I get the video, but with no options for pausing, stoping, muting, full screens, etc. 

Screenshot: [http://i269.photobucket.com/albums/jj79/swordsmen666/Capture-32.png](http://i269.photobucket.com/albums/jj79/swordsmen666/Capture-32.png)

I have a feeling it's a video codec, or lack of one rather.

-MtnDew

---

### Post by MtnDew on 2011-02-03
> **WinstonChurchill said:**
>  If so, it's that computer that isn't doing what you want, not the server.

Thank you. I had tried this on the other 3 computers and had my friend try it out on his and it still wouldn't play, this led me to believe it was something missing on my server. I installed Divx (with all addons) and it works fine now.

Thanks!

---

