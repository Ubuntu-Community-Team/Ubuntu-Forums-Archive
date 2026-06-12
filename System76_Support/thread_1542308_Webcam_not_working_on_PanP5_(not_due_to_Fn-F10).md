---
title: "Webcam not working on PanP5 (not due to Fn-F10)"
date: 2010-07-30
forum: System76 Support
---

### Post by samalex on 2010-07-30
Hi, 

About a month or more ago I installed Ubuntu Desktop 10.04 from scratch on my PanP5 system plus the drivers from System76, and thus far things have been rockin' along.  I tested the webcam through Flash using uStream.tv, which worked, but that's the only webcam test I've made since installing.

Today I tried Skype and found the webcam wouldn't work, and having ran into the Fn-F10 ordeal before I've ruled that out.  Below is the results of lsusb, which shows the webcam is there:
> Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0402:5606 ALi Corp. USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


And if I hit Fn-F10 it's gone then Fn-F10 again its' back, so I know that part is working.

This is in /etc/messages after startup if that matters:
> Jul 30 09:54:01 TritonOne kernel: [   49.682246] uvcvideo: UVC non compliance - GET_MIN/MAX(PROBE) incorrectly supported. Enabling workaround.
Jul 30 09:54:01 TritonOne kernel: [   49.784810] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.

And after hitting Fn-F10 twice (once to disable then once to enable) here's what it adds to /etc/messages also if that helps:
> Jul 30 09:59:27 TritonOne kernel: [  375.381358] usb 2-6: USB disconnect, address 3
Jul 30 09:59:28 TritonOne kernel: [  376.820286] usb 2-6: new high speed USB device using ehci_hcd and address 4
Jul 30 09:59:29 TritonOne kernel: [  377.214016] usb 2-6: configuration #1 chosen from 1 choice
Jul 30 09:59:29 TritonOne kernel: [  377.223240] uvcvideo: Found UVC 1.00 device USB2.0 Camera (0402:5606)
Jul 30 09:59:29 TritonOne kernel: [  377.239607] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input1

In Cheese the screen is just black, and the preferences shows it's using Device USB2.0 Camera (/dev/video0).

In Skype it shows it's using USB2.0 Camera (/dev/video0) also but clicking Test also just shows a black screen.

Going back to uStream.tv it shows it's using USB2.0 Camera (V4L2) but no video ever shows, nor does it on the few webcam Flash test sites I visit.

So any suggestions?  I went into the Syste76 Driver Installer in the Administration menu, then under Install Drivers ran the Install there plus rebooted, just incase, but that had no effect.  I didn't want to run the Restore System part though because I wasn't sure what that would effect...

Thanks for any advice you guys have.  Take care -

Sam

---

### Post by samalex on 2010-07-30
I went ahead and ran the Restore on the System76 driver section, but no effect either.  Hmm, not sure what to try next.

I did notice when I start Cheese this drops into /var/log/messages:
> Jul 30 10:11:34 TritonOne kernel: [  172.614517] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.

I did some research on this, but most reports where this appeared were with the camera working but just with some weirdness... none reported just nothing as I'm getting.

Also if it helps I'm attaching the results from running [lsusb -v -d 0402:5606] which gives more info on the camera.  I'm not sure if that'll help either, but I figure the more info the better for anyone familiar with this.

Thanks --

Sam

---

### Post by samalex on 2010-07-30
More info... i found this post with others reporting the same problem, one of which is someone with a Panp5, possibly due to the kernel update?
[http://ubuntuforums.org/showthread.php?p=9042380](http://ubuntuforums.org/showthread.php?p=9042380)

There has been at least one kernel update since I installed Ubuntu 10.04, and I'm currently on 2.6.32-24-generic.  

Using the info from the post I linked to above I ran a similar test with xawtv and got similar results:
> 
samalex@TritonOne:~$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.32-24-generic)
looking for available devices
port 310-341
    type : Xvideo, image scaler
    name : NV17 Video Texture

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : USB2.0 Camera
    flags:  capture  

> 
samalex@TritonOne:~$ xawtv -c /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.32-24-generic)
xinerama 0: 1680x1050+0+0
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x202f990 [PAL_I,PAL_K,PAL_M,PAL_60,NTSC_M,NTSC_M_JP,?,?,SECAM_D,(null)]): Invalid argument
ioctl: VIDIOC_S_CTRL(id=9963778;value=2): Input/output error
ioctl: VIDIOC_S_CTRL(id=9963776;value=49): Input/output error
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
v4l2: oops: select timeout
Killed

It hung and I had to kill the process.

Thanks -- 

Sam

---

### Post by isantop on 2010-07-30
In that other thread, a user said uninstalling camserv fixed their problem. Con you try this?

---

### Post by samalex on 2010-07-30
> **isantop said:**
> In that other thread, a user said uninstalling camserv fixed their problem. Con you try this?

I just saw the reply, but I don't have Camserv installed... Any other suggestions?

Thanks --

Sam

---

### Post by samalex on 2010-07-30
Sorry to have so many posts in here .... When I originally installed 10.04 I did it from a USB Thumbdrive, so I just booted from it to the desktop (just as if I booted from a Live CD) and the webcam was picked-up but is having the same problem.  So I wonder if it's gone out.  That sucks if so.  

Any tests I can run or possibly other distros I can boot with to test?  Thanks --

Sam

---

### Post by HotShotDJ on 2010-07-30
Hi, Sam --

Open a terminal and run:```
gstreamer-properties
```and take a look at the "Video" tab -> Default Input.  The webcam on my PanP5 is working just fine.  I've attached a screenshot of what my gstreamer-properties video tab looks like as a point of reference for you.  Hopefully it helps you get things sorted.

---

### Post by samalex on 2010-07-31
> **HotShotDJ said:**
> Hi, Sam --

Open a terminal and run:```
gstreamer-properties
```and take a look at the "Video" tab -> Default Input.  The webcam on my PanP5 is working just fine.  I've attached a screenshot of what my gstreamer-properties video tab looks like as a point of reference for you.  Hopefully it helps you get things sorted.

Neat, I didn't know this was out there.  The only difference between yours and mine was in Video under Default Input section the Device was just 'Default'.  The only other option is 'USB2.0 Camera' which I just set, and clicking Test it just says Testing with the bar going back and forth.  I can click Ok to get out, but I wasn't sure if this should've brought up anything.

After changing it though, I'm getting the same results with Cheese and other video apps.  My fear is the camera is hosed for some reason since even booting from the Live CD (via my thumb drive that is) it does the same thing... but htis is without using the Syste76 drivers which may be needed.  Not sure.

I do remember seeing references to BisonCam before, but now it's just "USB2.0 Camera".  Could something not be seeing the camera correctly?

Sam

---

### Post by HotShotDJ on 2010-07-31
> **samalex said:**
> Neat, I didn't know this was out there.  The only difference between yours and mine was in Video under Default Input section the Device was just 'Default'.  The only other option is 'USB2.0 Camera' which I just set, and clicking Test it just says Testing with the bar going back and forth.  I can click Ok to get out, but I wasn't sure if this should've brought up anything.
Hi, Sam --

Testing the camera should have brought up a window with your bright and shining face as recorded by the webcam.  Also, it definitely should be showing the detected camera as a BisonCam.

Although I'm pretty sure you've ruled out the normal "Fn+F10" fix, would you mind trying something?  First, open a terminal, then press "Fn+F10" and then run "dmesg" -- then repeat the "Fn_F10" and run dmesg again.  This should (hopefully) give us a clue as to what is going on.

Assuming that the webcam is "turned on," the first time you do that, you should see a line like this:```
[ 8242.551841] usb 2-6: USB disconnect, address 5
```
And the second time, something like this:```
[ 8292.892671] usb 2-6: new high speed USB device using ehci_hcd and address 6
[ 8293.385442] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0300)
[ 8293.401647] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input14
```
If you would post the results, that could help with debugging this.

---

### Post by samalex on 2010-08-01
Here's the tail end of dmesg after hitting Fn-F10:

> [ 4011.861607] usb 2-6: USB disconnect, address 3

And after hitting it again here's the results:
> [ 4071.990159] usb 2-6: new high speed USB device using ehci_hcd and address 4
[ 4072.383591] usb 2-6: configuration #1 chosen from 1 choice
[ 4072.399520] uvcvideo: Found UVC 1.00 device USB2.0 Camera (0402:5606)
[ 4072.415445] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input11

Oddly enough today I went into VirtualBox to setup my TomTom GPS (can only get the software to work in Windows -- but different story), and when adding USB Filters, given I had this Guest OS setup on my old 9.04 system it still had "BisonCam, NB Pro [0004]" on there ... but from the new install now that I'm running 10.04 it added "USB2.0 Camera [0100]" instead.  

So what could be causing either my system or Linux to pick-up the camera as the wrong device?  I've reran the driver installs from System76 both after installing 10.04 and again on Friday.

Thanks again for the help ...

Sam

---

### Post by HotShotDJ on 2010-08-01
The driver for the PanP5 web cam is not provided by the System76 driver, it is part of the Kernel, so running the System76 driver will have no effect. I'm now suspecting a hardware issue.  I would email System76.

---

### Post by thomasaaron on 2010-08-03
This one is now being worked on via email. Advised Sam to try from live CD.

---

### Post by isantop on 2010-08-03
[edited]

---

