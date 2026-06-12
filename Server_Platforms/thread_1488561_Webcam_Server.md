---
title: "Webcam Server"
date: 2010-05-20
forum: Server Platforms
---

### Post by danielgroves on 2010-05-20
Hi,

I am setting up a webcam server using FFMPEG.  I have managed to get video output onto the HDD as an MPEG, but I now have another issue.  This webcam server will be online 24/7 for... well, a long time, but the file just grows and grows forever more, and this is something I need to stop from happening as I do not have the capacity for it to keep on growing.  

Can anyone help me out here?  I think what I need to do is restart my script every now and again recording straight over the top of the old data in order to stop the files getting too large.  Is their a way I can schedule this to happen on the system?  

The current command I am running is:

ffmpeg -f video4linux2 -s 640x480 -i /dev/video1 '/var/www/cam001.mpg'

This command works perfectly to record the video.  

Also, I need to embed this video I am recording into a webpage?  Any ideas how?  This footage *must* be live.  

I am the latest release of Ubuntu Server.  

Thanks,
Dan.

---

### Post by R.Bucky on 2010-05-20
Not sure about your software package, however I use webcam-server for streaming without a hitch. Here's a write-up ([http://rbucky.com/blog/put-your-webcam-online-through-your-web-server/](http://rbucky.com/blog/put-your-webcam-online-through-your-web-server/))

---

### Post by danielgroves on 2010-05-20
Thanks for the response, but I have already looked at webcam server.  I found it supports hardly any cameras, is unreliable, and more to the point IT at school won't allow it for no apparent reason.  

I need to use FFMPEG apparently.

---

### Post by nairatinu on 2010-07-11
To get it working you can use the V4L1 compatibility wrapper like this:
(check where your v4l1compat.so is located and change if necessary)

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so webcam_server

no error for me after this...

So command line is:

sudo LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so webcam-server -v -g 320x240 -p 8888 -d /dev/video0

or whatever options you're using

---

### Post by bartos on 2010-07-11
Try Motion [HTML]http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome[/HTML]

It is in the repos and has a ton of configuration.

---

### Post by YorYor on 2010-07-12
Just cron it.
```
sudo crontab -e
```
and insert
```
0 * * * * /usr/bin/killall ffmpeg; /usr/bin/ffmpeg -f video4linux2 -s 640x480 -i /dev/video1 /var/www/cam001.mpg
```

---

