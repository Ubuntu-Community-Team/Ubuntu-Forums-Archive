---
title: "Webcam stopped working in Pangolin Performance."
date: 2008-12-24
forum: System76 Support
---

### Post by Guille Damke on 2008-12-24
Hello People,

My webcam stopped working in a Pangolin Performance (panp4n) running 8.10 64-bits.
It was working yesterday. I have tried many things, I will list them in order:

1.- I know that it is enabled, it is still detected doing 'lsusb', the camera is 'Bus 008 Device 002: ID 0402:5606 ALi Corp. ', and obviously it is activated/deactivated if I hit Fn+F10. (not detected if deactivated).

2.- I followed another thread/guide from the system76 Ubuntu forums to do it to work in Ekiga, but when I finally try to see images, Ekiga freezes (its window went gray, I waited for a loooong time but it did not recover).

3.- I know that it was working in amsn and skype yesterday. Now in amsn (in account > preferences > others > Edit_audio_and_video_settings) I get an error message (instead of working as before): 'Unable to capture from device' (it tries to read /dev/video0 and the device is 'v4l2: USB2.0 Camera' (the only one available) and the channel is 'Camera 1' (also the only one)). Skype does not give error messages, but it doesn't show images either.

4.- Since I just reinstalled 8.10 64 a few days ago to change the "/" partition space (and the webcam was working before and after that using the same kernel 2.6.27-9-generic), I reinstalled again 8.10 following EXACTLY the same steps I did before, but I had the same behavior in Ekiga, amsn and skype.

5.- I tried the Live CD plus Ekiga, still the same problem. I installed amsn under the liveCD session and I got the same error message.

6.- I reinstalled the system again (2nd time during the night), but I did not installed the updates from update manager this time (tried Ekiga and amsn in this point with no success) then I installed the nVidia driver and the system76 driver, but I had the same problem with the webcam. After, I installed the system updates using the update manager (obviously rebooted as usual), but I still have the same problem in amsn, Ekiga and skype (Ekiga still freezes and amsn/skipe do not work). Finally, I installed the extra codecs (I followed the guide to install Skype in system76 website) and even rerun the system76 drive and rebooted, but no one of the 3 programs can put the webcam to work.

Can the camera be (physically) broken/burnt?, but the system detects it doing lsusb. It would be nice to have it working asap, since I want to use skype to talk to my family for Christmas. I'll be online the whole day to follow any suggestion you have, especially from system76 support, since I do not know what else I can do.

Thanks in advance.
Guille.

---

### Post by Lee_Machine on 2008-12-24
go to command line and type sudo gstreamer-properties 

then in the Video tab for plugin make sure V4L2 is selected along with UVC camera in device. About that also make sure for output is X11 and NV17 is selected. Otherwise the output video will be all choppy.

Do the same thing with out running as sudo to make sure they both match each other.

gstreamer-properties is also where you would select the system wide sound.

hope this helps.

I had a similar issue and had to recompile uvcvideo in the kernel. Not hard.

[http://linuxtv.org/hg/~pinchartl/uvcvideo/](http://linuxtv.org/hg/~pinchartl/uvcvideo/)

---

### Post by Guille Damke on 2008-12-26
Thank you for your idea Lee_Machine, but it did not work. My camera is listed as "USB2.0 Camera" in gstreamer-properties and I followed your suggestion. I know that my camera should be fully supported by uvcvideo (its device ID is 0402:5606 by ALi Corp., and it is listed here [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)). 
Now I am in 8.04 64-bit, which was the original system in my Pangolin and supported my webcam also. I had already reinstalled this version once and my camera worked straightforward, but now it has the same behavior as in 8.10. Probably it is a real hardware issue more than software issue. 
Now I am going to install 8.10 again, and try to put it to work there, but I confirmed that the camera is also recognized but does not work in 8.04 either.

I'll be waiting for any other suggestion that you or others may have.
Thank you.
Guille.

---

### Post by Guille Damke on 2008-12-26
Hi guys,
I just reinstalled 8.10 (for 3rd time in 2 days) after confirming that my webcam is not working in 8.04 either (which I also installed). I have to say that following the system76 procedure again it did not worked, but it used to work straightforward. The webcam is still recognized but not working under any program. For details about what I have already tried see my first post in this thread. I hope I have some advice from you guys or from system76 support, but I am suspicious that the webcam can be broken.
Guille.

---

### Post by thomasaaron on 2008-12-26
Please shoot me an email on Monday (support@system76.com) and I'll walk you through some stuff. But it does sound like it could be hardware related.

Also, did you run the System76 driver and reboot before testing? This was necessary in 8.04.

---

### Post by Guille Damke on 2008-12-26
HI Thomas,

I will send you an email on Monday.
And yes, I always install/run the system76 driver (either in 8.04 or 8.10) and reboot while doing a clean install.
Thanks for answering.
Guillermo.

---

