---
title: "[SOLVED] Darter Ultra videocam stopped working in Ekiga and Cheese"
date: 2008-11-30
forum: System76 Support
---

### Post by dzrtmn on 2008-11-30
Ekiga gives the attached error, and the Ekiga Preferences are as attached. The first Synaptic Package Manager attachment shows the installed version of v4l2.

The attached Cheese screen shot shows a test screen, and when I take a photo or video I get the test screen. The second Synaptic screen attached shows the installed version of gstreamer plugins.

The changes made since the UVC videocam last worked have been regular Synaptic updates.

WHat next steps should I take to troubleshoot?

Thanks

Dzrtmn

---

### Post by thomasaaron on 2008-12-01
Press your P2 button. That is how you turn the camera on with the DarU2.

---

### Post by dzrtmn on 2008-12-01
Pressing the F10 key (which I assume is the "P2" key), makes no difference to Cheese. Ekiga gives a new error "Your driver doesn't seem to support any of the color formats supported by Ekiga. Please chack your kernel driver documentation in order to determine which Palette is supported.".

What should I try next?

Thanks

dzrtmn

---

### Post by jdb on 2008-12-01
> **dzrtmn said:**
> Pressing the F10 key (which I assume is the "P2" key), makes no difference to Cheese. Ekiga gives a new error "Your driver doesn't seem to support any of the color formats supported by Ekiga. Please chack your kernel driver documentation in order to determine which Palette is supported.".

What should I try next?

Thanks

dzrtmn

On a Daru2 the P2 key is the round button at the top of the keyboard with P2 written on it.

jdb

---

### Post by dzrtmn on 2008-12-02
Thank you for the suggestion jdb, but the 3 keys to the left of the power buton are: Email, Web and Silent Mode.

---

### Post by gaussian on 2008-12-02
> **dzrtmn said:**
> Thank you for the suggestion jdb, but the 3 keys to the left of the power buton are: Email, Web and Silent Mode.

What version of Darter you have? Just start System 76 driver and it will tell you your model name (mine says daru2).

---

### Post by thomasaaron on 2008-12-03
dzrtmn, you have a DarU3.
Fn-F10 turns the cam on and off.

Your settings in Ekiga are incorrect.

They should be...
Video Plugin: V4L2
Input Device: BisonCam
Format: PAL(Europe)
Channel: 0
Image: None

---

### Post by dzrtmn on 2008-12-03
Thomas, the Input Device is not a free-text field, it is based on the detected videocam device(s). In my case, the only available choice is 'UVC Camera...'. Attached are the properties of the only videocam device listed in the Device Manager. 

Why do you think the device should be Bisoncam? And what would have caused the identity of the device to change?

I look forward to your continued help...

Thanks

---

### Post by thomasaaron on 2008-12-04
> Why do you think the device should be Bisoncam?

That's what it says on our shop DarU3.

```
what would have caused the identity of the device to change?
```

Did you do anything at all to activate the webcam apart from running the System76 driver and pushing the P2 button?

---

### Post by dzrtmn on 2008-12-04
> **thomasaaron said:**
> 

Did you do anything at all to activate the webcam apart from running the System76 driver and pushing the P2 button?

I have not installed any additional hardware drivers, as you can see in the attached Hardware Driver screen shot. 

The System76 driver is as shown in the attached screen shot.

As part of my troubleshooting I did initiate the Ubuntu Hardware Testing found in the System>Administration menu, and this froze when it got to the video section; I had to force a reboot.

I have used Totem Movie player (version info shown in the attached screen shot), but I don't believe this would be activating the webcam.

And I have tried using Cheese. When searching for references to 'UVC camera (5986:0303)', I came across this reference to a Clevo laptop and Cheese...[http://lists.berlios.de/pipermail/linux-uvc-devel/2008-July/003921.html](http://lists.berlios.de/pipermail/linux-uvc-devel/2008-July/003921.html)

Thanks for your continued assistance...

---

### Post by dzrtmn on 2008-12-04
> **thomasaaron said:**
> That's what it says on our shop DarU3.



Thomas, the very last entry at [http://blognux.free.fr/Liste.txt](http://blognux.free.fr/Liste.txt), has the following entry as part of the 'UVC' section of the list:

ID 5986:0303 Clevo M570TU - Bison Electronics 	

So perhaps a UVC 5986:0303 is synonymous with BisonCam?

---

### Post by thomasaaron on 2008-12-05
I'm pretty sure Cheese is still broken. So, let's keep working with Ekiga.
Try turning off your desktop effects (System > Preferences > Appearance > Visual Effects > None.

Does Ekiga work now?  (Make sure you're using the settings I outlined above... other than the Bisoncam part).

---

### Post by dzrtmn on 2008-12-06
> **thomasaaron said:**
> I'm pretty sure Cheese is still broken. 

[http://platonic.techfiz.info/2008/12/03/uvcvideo-and-cheese-on-ubuntu-810/](http://platonic.techfiz.info/2008/12/03/uvcvideo-and-cheese-on-ubuntu-810/) said a new version of UVCvideo fixed Cheese in 8.10. Do you think 8.04 needs a new version of uvcvideo?

With respect to Ekiga I followed your advice, but still get the error that the driver doesn't support the color format. I tried NTSC, SEACAM, and Auto and got the same error. Attached is a screen shot of the Video Streamer Interface properties. I don't see a version number for uvcvideo. How do I determine what version I have? What version do you have on your working Daru3?

Thanks

---

### Post by perez2000 on 2008-12-06
If you regularly keep your system up-to-date and have upgraded to the latest kernel, you may need to rebuild your kernel modules. I'm on the 2.6-24-22-generic kernel. 

1) Go to System -> Administration -> System76 Driver. Select "Install Drivers" tab and click install. Verify that /lib/modules/2.6.24-22-generic/ubuntu/media/usbvideo/uvcvideo.ko is updated to current date/time.

2) open terminal and enter:

```
sudo rmmod uvcvideo
sudo modprobe uvcvideo
```

(alternatively you can reboot to reload the modules)

3) Make sure the cam is turned on, enable/disable is is Fn-F10 on the keyboard.

Anyway, this worked for me after I upgraded the kernel and Cheese stopped working with the built-in BisonCam NB Pro. I'm on a System76 Bonobo Pro laptop.

---

### Post by dzrtmn on 2008-12-07
THANK YOU, Perez, the process you described fixed the issue. Both Ekiga and Cheese are now working again :)

---

### Post by swizman on 2008-12-07
I can confirm that Cheese works on a panp4n with Intrepid 8.10 after compiling a new camera module according this instructions:

[http://www.soccio.it/michelinux/2008/10/25/webcam-cheese-gstreamer-and-uvcvideo-problems-in-intrepid/en/](http://www.soccio.it/michelinux/2008/10/25/webcam-cheese-gstreamer-and-uvcvideo-problems-in-intrepid/en/)

The command “make” will give you this warning:

-------------------------------- WARNING ---------------------------------------
 The USB Video Class driver has moved to [http://linuxtv.org/](http://linuxtv.org/).
 Using the Berlios SVN repository is now deprecated.
 Please check [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) for download instructions.
 If you really want to compile this historical version, run 'make uvcvideo'.
--------------------------------------------------------------------------------

 So you just use “make uvcvideo” instead and it will compile.

After finishing all instructions, Cheese works after setting the video resolution:
Cheese > Edit > Preferences > Camera: UVC Camera(5986:0300) /dev/video0 	> Resolution: 1280 x 1024. 
Other resolutions do not work. 

Cheese still works after multiple rebooting and after closing/opening the lid.



Instead Cheese you can also test the camera with issuing this command into a terminal: 

gstreamer-properties

Multimedia Systems Selector > Video > Default Input > Plugin: Video for Linux 2 (v4|2) > Device: Default > Test > a window appears with the picture from the camera > Testing > OK > window closes. 

Maybe this helps on a Darter too.

---

### Post by Lee_Machine on 2008-12-08
> **swizman said:**
> I can confirm that Cheese works on a panp4n with Intrepid 8.10 after compiling a new camera module according this instructions:

[http://www.soccio.it/michelinux/2008/10/25/webcam-cheese-gstreamer-and-uvcvideo-problems-in-intrepid/en/](http://www.soccio.it/michelinux/2008/10/25/webcam-cheese-gstreamer-and-uvcvideo-problems-in-intrepid/en/)

The command “make” will give you this warning:

-------------------------------- WARNING ---------------------------------------
 The USB Video Class driver has moved to [http://linuxtv.org/](http://linuxtv.org/).
 Using the Berlios SVN repository is now deprecated.
 Please check [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) for download instructions.
 If you really want to compile this historical version, run 'make uvcvideo'.
--------------------------------------------------------------------------------

 So you just use “make uvcvideo” instead and it will compile.

After finishing all instructions, Cheese works after setting the video resolution:
Cheese > Edit > Preferences > Camera: UVC Camera(5986:0300) /dev/video0 	> Resolution: 1280 x 1024. 
Other resolutions do not work. 

Cheese still works after multiple rebooting and after closing/opening the lid.



Instead Cheese you can also test the camera with issuing this command into a terminal: 

gstreamer-properties

Multimedia Systems Selector > Video > Default Input > Plugin: Video for Linux 2 (v4|2) > Device: Default > Test > a window appears with the picture from the camera > Testing > OK > window closes. 

Maybe this helps on a Darter too.

I have a Panp4n and I couldnt get my web cam to work under cheese either. I just took Toms word that it was still broken. As it did work in skype and ekiga but not cheese.

even after compiling the new uvc camera modual it didnt work. I then say the above post about checking the gstreamer settings. For plugin v4l was chosen not V4L2. I chose that V4L2 and cheese now works on my Panp4 like it should. Thanks

---

### Post by EnderEcho on 2008-12-09
So I tried the walk through that Swizman posted. Everything went well, but Cheese still isn't working. Now Ekiga isn't work either. Can anyone help me undo what I've done. Nothing is detected my web cam now.

I'm running Ibex on DarU3

---

### Post by swizman on 2008-12-09
**EnderEcho:**

To use the old camera module, you just install the System 76 Drivers again:

System > Administration > System 76 Driver > PW > Install Drivers > Install > **Reboot !**


But before you do that, make sure that you did test the camera with gstreamer-properties (see the end of my post above) and that you did set it to "Video for Linux 2 (v4|2)".

Good luck.

---

### Post by EnderEcho on 2008-12-09
Thanks Swiz I had it set originally like that. I'm wondering if I just didn't hit fn-F10 before I opened up cheese the very first time. I'm about to reboot and I'll let you know.

---

### Post by EnderEcho on 2008-12-09
I reinstalled system76 drivers I think. All I did was go to drivers and install. I'm not sure if that does the same if I followed the walkthrough for the terminal.

After rebooting Ekiga, Cheese, and Camorama don't work. Nothing recognizes the webcam. I've tried it with fn-F10 many times.

What in the world do I do from here?

---

### Post by thomasaaron on 2008-12-10
EnderEcho, this thread is getting a bit difficult to follow. Since you came in pretty late in the game, please do the following and tell me the results, and I'll try to get you up and running...

By the way, camorama doesn't work with your cam. Let's test with Ekiga first.

1. In a terminal enter this command...
   lsusb
   ...Do you see your webcam listed (it will probably say "BISON" somewhere in there. If not press Fn-F10 and run the command. If it didn't show your webcam before, it should definitely show it now. If it does not, you probably have a hardware problem. Once your webcam is listed, you can proceed.
2. In a terminal enter this command...
   gstreamer-properties
   Under the video tab, make sure the Default Input plugin is set to V4L2.
3. Open Ekiga and go to Edit > Preferences > Devices > Video Devices. Your settings should look like this...

Video Plugin > V4l2
Input Device > Bison Web Cam or possibly UVC...
Format > Pal(Europe)
Chanel > 0
Image > None

At this point, right-click the Ekiga icon in the upper right of your LCD and select "Quit". Then re-start Ekiga and click the Webcam Icon.

Does it work?

---

### Post by EnderEcho on 2008-12-10
Yea it is a little confusing.

I don't know what was different. I didn't have to change any settings since last time, but I ran the test and it came up fullscreen working. Ekiga is working fine. Cheese still isn't working, but is there another program I can use that captures and has effects?

Thanks!

---

### Post by thomasaaron on 2008-12-10
Not that I'm aware of.

Ekiga, Skype and Cheese are the only ones I'm familiar with that support V4L2.

---

### Post by Cicer on 2008-12-21
So pleased to find this thread. Thanks perez2000 + thomasaaron!

---

### Post by doubledown11 on 2009-02-16
I seem to have the same issue.  I reinstalled system76 drivers.  After rebooting Ekiga, Cheese, and Camorama do not recognize the webcam. I too have tried it with fn-F10 many times.

This is on a new Gazelle Ultra just received on Friday.

Any help would be greatly appreciated.

---

### Post by thomasaaron on 2009-02-17
doubledown11,

Please carefully follow the tutorial here...
[http://ubuntuforums.org/showthread.php?p=6749439#post6749439](http://ubuntuforums.org/showthread.php?p=6749439#post6749439)

---

### Post by doubledown11 on 2009-02-20
I followed the tutorial to the letter with the same result.

Here are the error messages received from Ekiga and gstreamer-properties.

---

### Post by thomasaaron on 2009-02-20
That last one seems to indicate you have your screen resolution set incorrectly. What is it set at: System > Prefs > Screen Resolution

---

### Post by doubledown11 on 2009-02-20
> **thomasaaron said:**
> That last one seems to indicate you have your screen resolution set incorrectly. What is it set at: System > Prefs > Screen Resolution

1280 x 800

---

### Post by thomasaaron on 2009-02-20
doubledown, which Darter do you have please?
If you're unsure, go to System > Administration > System76 Driver. It will tell you.

---

### Post by thomasaaron on 2009-02-20
...also, could you try downloading a *current* intrepid CD and using the webcam in Ekiga to see if you get the same error. That will help me to know if we're dealing with a hardware issue or a configuration issue.

---

### Post by doubledown11 on 2009-02-20
Thanks again for the help.

Here's a shot of my system info.  This a System76 install and is less than a week old.  Not sure I understand the question about downloading the latest version of the Intrepid CD... for what?

---

### Post by jbelmonte on 2009-02-20
Hi doubledown11,

I think thomasaaron wanted you to use the latest 8.10 live CD to see if the problem existed there. If the camera worked off the current live CD, then that would indicate the problem is a configuration problem rather than a hardware problem.

---

### Post by doubledown11 on 2009-02-21
Pulled down a fresh copy of 8.10 and tried the cam from the live CD.  Same errors as before.  Here is the detail from the Terminal:

```
user@ubuntu:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
libv4l2: error setting pixformat: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 1280x1024 [v4l2src_calls.c(1289): gst_v4l2src_set_capture (): /GstPipeline:pipeline4/GstV4l2Src:v4l2src3:
Call to S_FMT failed for YU12 @ 1280x1024: Input/output error]

(gstreamer-properties:6631): GStreamer-CRITICAL **: gst_util_uint64_scale_int: assertion `denom > 0' failed
user@ubuntu:~$ 

```

---

### Post by doubledown11 on 2009-02-21
Fixed with help from System76 Support.  I was getting "No such file or directory" When I was asked to run:

```
cat /etc/modprobe.d/uvc
```

Based on this information, Support had me run the following and reboot:

```
echo options uvcvideo quirks=2 | sudo tee -a /etc/modprobe.d/uvc
```

Works perfect now... Apparently this command creates a file that tells the kernel to load the webcam driver in a specific way.

---

### Post by doubledown11 on 2009-03-20
It seems that I need to re-run this command after each restart before the webcam will work.  Not the end of the world but can anyone recommend how I can automate this at startup?

---

### Post by thomasaaron on 2009-03-20
Really? That definitely should not be necessary. That command permanently inserts the data into the file.

Please reboot your computer and then post the output of...
cat /etc/modprobe.d/uvc

I'm thinking there is something else going on?

Cheese can be a little slow. Are you waiting long enough for your image to appear?

---

