---
title: "Software similar to manycam for Linux?"
date: 2008-03-02
forum: The Cafe
---

### Post by HumanAnarchist on 2008-03-02
Anyone know if there are some software similar to [http://www.manycam.com/](http://www.manycam.com/) for Linux?

---

### Post by yazzen on 2008-07-06
don't think there is software available like that, i'm looking for some myself. A friend tried to create a virtal cam driver to show the desktop enviroment although he could not impliment it correctly... problems linking the video stream with the virtual driver. He could stream it with VLC player though.

Would be cool to show off the ubuntu GUI capabilities in video chat applications ;P

Guess you're going to have to settle with pointing the webcam at the screen ^^

---

### Post by madjr on 2008-07-06
the closest thing is **Cheese** i think..

---

### Post by HumanAnarchist on 2008-07-06
> **yazzen said:**
> don't think there is software available like that, i'm looking for some myself. A friend tried to create a virtal cam driver to show the desktop enviroment although he could not impliment it correctly... problems linking the video stream with the virtual driver. He could stream it with VLC player though.

hey cool, do you know more about what your friend tried. I've thought about trying to make a program like that, but I'm not sure where to start and whats needs to be done. What kind of virtual driver did he use and what did he stream to VLC? What libraries did he use? 

-ha-

---

### Post by Randypinball on 2008-08-11
Im pretty frustrated, because I love Ubuntu/Linux I want to completely run Ubuntu and remove VISTA from my PC, and UBUNTU is almost perfect for me EXCEPT when I want to broadcast Video or Audio on Stickam.com, Justin.tv etc I have no way of manipulating my webcam, my audio or screen destop capture.  The only other thing I really need is for realplayers superpass to work. 

Those are the only 2 things I cant live without for broadcasting reasons.. I really really want to rid my life of Microsoft.

Any Ideas..

Thanks community :)
Randy, sherman oaks, calif

---

### Post by gabtrat on 2008-08-22
Hopefully better webcam support will come in Intrepid or Intrepid +1.  It currently has over 3500 votes on the Ubuntu brainstorm site.

---

### Post by patrickballeux on 2008-08-25
I found a solution by using flashcam, recordMyDesktop, ffmpeg and mjpegtools_yuv_to_v4l.

Here is the complete detail in french : [http://blog.patrickballeux.com/2008/08/ubuntu-et-une-webcam-virtuelle.html](http://blog.patrickballeux.com/2008/08/ubuntu-et-une-webcam-virtuelle.html)

Compile and install those software and with this script:

mkfifo stream.ogg
sudo modprobe vloopback
echo "CTRL-C to stop the capture"
sleep 5
recordmydesktop -width 320 -height 240 -fps 15 --no-sound --on-the-fly-encoding --follow-mouse --overwrite -o stream.ogg & sleep 10 & ffmpeg -i stream.ogg -an -s 320x240 -r 15 -f yuv4mpegpipe - | mjpegtools_yuv_to_v4l /dev/video2
killall recordmydesktop
rm stream.ogg

You will be able to screenscast 320x240 view of you desktop following your mouse.

As I write this, I am screencasting my entire desktop at 5 fps (1600x1070) over Stickam channel and the load is not too much...


As you just read, Yes, it works also with Flash site as a virtual webcam.

And your voice will be from your sound card as usual...

Have fun!

---

### Post by patrickballeux on 2008-10-07
Now the answer would be YES!...

See [http://webcamstudio.wiki.sourceforge.net/]("http://webcamstudio.wiki.sourceforge.net/")

It is a new project that I have created for Linux users...

Hope you enjoy it!

---

### Post by jeyaganesh on 2008-10-07
Easycam was working good for me. But not it is not working. I dont know why.

---

### Post by patrickballeux on 2008-10-07
Easycam is not like Manycam.  Manycam can provice special effects, text overlay and some nice live features..

For Linux, there is WebcamStudio for GNU/Linux that does almost the same thing.

---

### Post by HumanAnarchist on 2008-10-08
> **patrickballeux said:**
> Now the answer would be YES!...

See [http://webcamstudio.wiki.sourceforge.net/]("http://webcamstudio.wiki.sourceforge.net/")

It is a new project that I have created for Linux users...

Hope you enjoy it!

That's super sweet, **** yeah :guitar:

---

### Post by bryantrivera on 2010-08-29
I got this message: Cannot install 'openjdk-6-jre'

---

### Post by boosalisis12 on 2011-02-28
Hi all.

I heard that now there is development of a new version of [SplitCam]("http://splitcamera.com/") for Linux. So it may in the near future SplitCam you can use on Linux

---

### Post by PalqkA on 2012-05-05
> **patrickballeux said:**
> Now the answer would be YES!...

See [http://webcamstudio.wiki.sourceforge.net/](http://webcamstudio.wiki.sourceforge.net/)

It is a new project that I have created for Linux users...

Hope you enjoy it!

Thanks dude this will help me spend some useless time in the web space :)

---

### Post by Bandit on 2012-05-05
** COUGH ** Video Lan Client? Perhaps?

---

### Post by cariboo on 2012-05-06
Things have changed in the four years since this thread was created, so it really isn't relevant any more. Closed.

---

