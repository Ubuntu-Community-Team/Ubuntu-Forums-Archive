---
title: "Webcam not working on Gazp7"
date: 2012-07-28
forum: System76 Support
---

### Post by imnotanerd on 2012-07-28
I used my webcam only once yesterday to  see if it works and the quality. I opened up Cheese, and it worked! Not today,  opened Cheese again, and it gives me a message saying "No device found." But how is that possible? I didn't do anything to it! I've looked this over already through google, and I'll output what `lsusb` gives me.

lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub

No webcam there to be found. There was also the key with the camera on it (F10), and I clicked that, and still nothing. I don't have any other operating systems to test this on. It worked once, what's wrong now?!

---

### Post by jakobcreutzfeldt on 2012-07-28
Hmmm....by any chance was there a kernel update? Just as a sanity check, try restarting the system (if you haven't already).

---

### Post by imnotanerd on 2012-07-28
You know what? I actually did update the kernel. I followed the [pinned thread atop the threads page]("http://ubuntuforums.org/showthread.php?t=2014669") last night. Webcam worked before that, now it doesn't.

---

### Post by jakobcreutzfeldt on 2012-07-28
That's a start then :)
Have you restarted the system since the kernel update? Sometimes (often, in my experience at least) USB devices like to stop working after an update until the system is rebooted. 

If that doesn't help, best to wait for a System76 rep because they'd probably know a lot better than me!

---

### Post by imnotanerd on 2012-07-28
Yep, power cycled a few times already. Let the wait begin!

---

### Post by jakobcreutzfeldt on 2012-07-29
Could you please post the command-line output of 

```
dmesg | grep BisonCam
dmesg | grep uvcvideo
```

---

### Post by jakobcreutzfeldt on 2012-07-29
Also try running this:
```
gst-launch-0.10 v4l2src ! xvimagesink
```...from a commandline. What it does is open a very basic GStreamer pipeline, using video4linux (what webcams use) as a source and dropping it into a simple Xv (X Windows video extension) sink. If it works, a window  should pop up and you should see yourself. If it doesn't then that means GStreamer isn't able to open a v4l stream for some reason.

Please post any output to the commandline produced by this command as well!

---

### Post by imnotanerd on 2012-07-29
dmesg | grep BisonCam
```
imnotanerd@sys76laptop:~$ dmesg | grep BisonCam
imnotanerd@sys76laptop:~$ 
```

dmesg | grep uvcvideo
```
imnotanerd@sys76laptop:~$ dmesg | grep uvcvideo
imnotanerd@sys76laptop:~$ 

```

gst-launch-0.10 v4l2src ! xvimagesink
```
imnotanerd@sys76laptop:~$ gst-launch-0.10 v4l2src ! xvimagesink
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /GstPipeline:pipeline0/GstV4l2Src:v4l2src0: Cannot identify device '/dev/video0'.
Additional debug info:
v4l2_calls.c(493): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
Freeing pipeline ...
imnotanerd@sys76laptop:~$ 
```

:(

---

### Post by jakobcreutzfeldt on 2012-07-29
Ok, try 
```
sudo modprobe uvcvideo
```
and then try the previous commands again. uvcvideo is the kernel module that the webcam depends on.

---

### Post by imnotanerd on 2012-07-29
```
imnotanerd@sys76laptop:~$ sudo modprobe uvcvideo
[sudo] password for imnotanerd: 
imnotanerd@sys76laptop:~$ dmesg | grep BisonCam
imnotanerd@sys76laptop:~$ dmesg | grep uvcvideo
[  207.628090] usbcore: registered new interface driver uvcvideo
imnotanerd@sys76laptop:~$ gst-launch-0.10 v4l2src ! xvimagesink
Setting pipeline to PAUSED ...
ERROR: Pipeline doesn't want to pause.
ERROR: from element /GstPipeline:pipeline0/GstV4l2Src:v4l2src0: Cannot identify device '/dev/video0'.
Additional debug info:
v4l2_calls.c(493): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src0:
system error: No such file or directory
Setting pipeline to NULL ...
Freeing pipeline ...
imnotanerd@sys76laptop:~$ 

```

---

### Post by jakobcreutzfeldt on 2012-07-30
Crap....
Well, let's wait and see what the Sys76 guys say. I can't think of anything right now.

---

### Post by isantop on 2012-07-30
Press Fn+F12 on your keyboard. My guess is that somehow the update turned off the camera, and that will toggle it back on.

---

### Post by imnotanerd on 2012-07-30
Yay, isantop!

I tried out your answer, and even with bluetooth, it wasn't working. Then I tried out Fn+F10 because it had the camera icon on it, and now it works! :D

---

### Post by jakobcreutzfeldt on 2012-07-30
I thought you already tried that before your first post...?

> **imnotanerd said:**
> There was also the key with the camera on it (F10), and I clicked that, and still nothing. I

---

### Post by isantop on 2012-07-30
> **imnotanerd said:**
> Yay, isantop!

I tried out your answer, and even with bluetooth, it wasn't working. Then I tried out Fn+F10 because it had the camera icon on it, and now it works! :D

Sorry about that, I somehow read the entire post as "Bluetooth" rather than "Camera".

---

### Post by imnotanerd on 2012-07-30
> **jakobcreutzfeldt said:**
> I thought you already tried that before your first post...?

I did. But it just happens to work now.

---

### Post by Rader on 2012-09-05
I've been looking at this problem on a lemur ultra.  The Fn+F10 key did nothing to
start with, then I loaded various suggested other tools ...  such as libwebcam0,
xawtv.  One thing I noticed was the error message from gstreamer-properties
saying that there was no /dev/video0.  

And, reading this, I tried Fn+F10 again, and now there is a /dev/video0, and
cheese works to take a picture.

I see that the Fn+F10 key toggles the existence of /dev/video0.  I like that, but it
does cause confusion in figuring out how to get {cheese, skype} to work.

---

### Post by HDave on 2013-02-23
> **isantop said:**
> Press Fn+F12 on your keyboard. My guess is that somehow the update turned off the camera, and that will toggle it back on.

DOH!  Thanks for this....

---

### Post by jedsled on 2013-02-25
I've been having similar problems on my Lemu4. The function key toggles the existence of /dev/video0 but nothing is displayed in cheese or skype.

My original post: [http://ubuntuforums.org/showthread.php?t=2118712](http://ubuntuforums.org/showthread.php?t=2118712)

---

