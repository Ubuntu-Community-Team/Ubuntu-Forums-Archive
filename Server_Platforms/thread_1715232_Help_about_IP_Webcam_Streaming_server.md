---
title: "Help about IP Webcam Streaming server????"
date: 2011-03-26
forum: Server Platforms
---

### Post by Xelmep on 2011-03-26
Dear all,
 I have Foscam IP Camera, and i like to stream live video from camera with Ubuntu VPS server. How is this possible, which application support video streaming from IP camera, and how to configure it.
   Thank you.

---

### Post by rubylaser on 2011-03-26
You could use Zoneminder ([http://www.zoneminder.com/]("http://www.zoneminder.com/")), but most decent network cameras have a built in web server that you can just connect directly to to view the live stream.  Also, they typically allow you to upload the time lapse photos to an FTP server.

Here are directions from their wiki to setup up Zoneminder on Ubuntu Server. [http://www.zoneminder.com/wiki/index.php/Ubuntu_10.04_Server_64-bit_(with_ffmpeg,_etc.)]("http://www.zoneminder.com/wiki/index.php/Ubuntu_10.04_Server_64-bit_(with_ffmpeg,_etc.)")

---

### Post by HermanAB on 2011-03-27
LibAV (a.k.a. ffmpeg), ffserve specifically.

---

### Post by R.Bucky on 2011-03-27
I use webcam and webcam-server for pushing static and streaming video - tutorial here: [http://nwlinux.com/put-your-webcam-online-through-your-web-server/]("http://nwlinux.com/put-your-webcam-online-through-your-web-server/")

---

### Post by Xelmep on 2011-03-30
Thanks a lot to all, i will try to make experiments. :) I will report about my job.
  Thank you again.

---

### Post by Xelmep on 2011-03-30
> **R.Bucky said:**
> I use webcam and webcam-server for pushing static and streaming video - tutorial here: [http://nwlinux.com/put-your-webcam-online-through-your-web-server/]("http://nwlinux.com/put-your-webcam-online-through-your-web-server/")

apt-get install:
         Unable to locate webcam-server 
 why ?

---

### Post by R.Bucky on 2011-04-11
It might be possible that webcam-server is no longer in the repos after 10.04. I host a mirror at [http://nwlinux.us](http://nwlinux.us), which the webcam-server package still exists. Just a hunch. What version are you operating?

---

### Post by HermanAB on 2011-04-12
Wahl, laaik ah sed:
libav (aka ffmpeg): ffserve.

Go to the libav web site and read the manual.

---

### Post by andrew.46 on 2011-04-12
> **HermanAB said:**
> libav (aka ffmpeg)

A little sideways of this thread: there are now *two* diverging applications, there is FFmpeg itself [here]("http://www.ffmpeg.org/") and the fork libav [here]("http://libav.org/"). Unless the developers rend each other even further :(.

---

### Post by HermanAB on 2011-04-12
Yeah, I compiled LibAV from source and it all works, so the fork seems to be the way to go.  I'm trying to make some specialized video filters - rather difficult stuff.

---

### Post by Xelmep on 2011-04-16
> **R.Bucky said:**
> It might be possible that webcam-server is no longer in the repos after 10.04. I host a mirror at [http://nwlinux.us](http://nwlinux.us), which the webcam-server package still exists. Just a hunch. What version are you operating?
 
 
 I use UBUNTU 10.10 Server edition

---

