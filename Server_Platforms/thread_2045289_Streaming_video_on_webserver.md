---
title: "Streaming video on webserver"
date: 2012-08-20
forum: Server Platforms
---

### Post by conradin on 2012-08-20
Hi all,
I am using lucid Lynx, desktop edition, with php5, and appache2, as a web server. I ssh into the computer, and I am trying to stream music from this server, I would like to embed a player in a web page, but I dont know how to do that yet.

I am using the command```
vlc -I dummy Firestarter.mp3  --sout '#standard{access=http,mux=ogg,dst=130.111.192.241:8080}'
```
to stream video from the server, and that plays just fine with the command ```
vlc http://130.111.192.241:8080
```

So how can I make a webpage link to the streaming content on my website?

---

### Post by bigmonmulgrew on 2012-08-21
Not an expert here but


As a start get yourself a fixed internet IP address.
There are ways round this buttt.
Then get yourself a domain name.
Forward your Domain name to your WAN IP address
Forward any ports your using in your router to the IP address of your server, looks like your using port 8080, I'd also forward 80 (HTTP) 21 (ftp) 22 (ssh)
If apache is setup just with the default site then it should accept requests as it is now with your WAN IP (I guess thats your wan IP below)

I also found this. May be useful
[http://wiki.videolan.org/Control_VLC_via_a_browser](http://wiki.videolan.org/Control_VLC_via_a_browser)
and this
[http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/](http://www.engadget.com/2005/11/29/how-to-stream-almost-anything-using-vlc/)

---

### Post by conradin on 2012-08-21
I have a static ip, and a hostname, this is a testing server so an FQDN isn't necessary, Also the stream is already running, I can access it using a media players in Linux mac and windows. The only thing I want to do now is embed the audio on the site I already have running. Maybe I can link to it... maybe this is a w3schools question.

---

### Post by cool110 on 2012-08-21
Try using HTML5 audio and video tags.
[http://www.w3schools.com/html5/html5_audio.asp](http://www.w3schools.com/html5/html5_audio.asp)
[http://www.w3schools.com/html5/html5_video.asp](http://www.w3schools.com/html5/html5_video.asp)

---

