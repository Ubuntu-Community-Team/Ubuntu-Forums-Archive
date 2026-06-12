---
title: "I broke my gf's webcam while trying to fix hulu"
date: 2010-06-26
forum: System76 Support
---

### Post by ubunchu on 2010-06-26
So the title pretty much sums it up. She is running a pangolin performance which came with lucid while I am running a pangolin performance which came with karmic and i upgraded to lucid (bought before her). For some reason hulu always worked for me, so I was trying to fix it on her computer too, but somehow one of the commands I told her to run made her computer not be able to recognize that her built in webcam exists anymore.

The reason that this is so hard is that I don't remember which commands I told her to run, but one of them was the instructions from post #5 on this page: [http://ubuntuforums.org/showthread.php?t=1146708](http://ubuntuforums.org/showthread.php?t=1146708) . But I don't know how messing with flash stuff could have possibly screwed up her computer detecting her webcam. Another clue I have found is that the command ```
locate uvcvideo
``` does not give back what it is supposed to on her computer, but I don't know how to fix that either or if that would affect her computer being able to tell that an internal webcam existed.

---

### Post by tech newbie on 2010-06-26
Try :
```
gstreamer-properties
```

Then go to video tab, under defualt input try changing the device and/or plug-in and hit test.

---

### Post by ubunchu on 2010-06-26
> **tech newbie said:**
> Try :
```
gstreamer-properties
```Then go to video tab, under defualt input try changing the device and/or plug-in and hit test.

She says that the device option is grayed out so that she can't even hit the drop down menu. What I am going to do is get her to manually install v4l-dvb and see how that goes since uvcvideo doesn't seem to exist anymore on her system.

---

### Post by ubunchu on 2010-06-27
I found the problem: the computer had glitched and turned off the webcam  in the bios, so i reenabled it with the fn+f10 button.

---

### Post by jbelmonte on 2010-06-27
Cound the webcam have gotten turned off? I believe there is a function key combo for toggling the webcam. You may want to try toggling it to see if that makes a difference.

---

### Post by silvertuna on 2010-07-01
Similar problem here. Built-in webcam no longer works. Cheeze and Skype cant find it anymore. Didnt see any setting in BIOS to reactivate it. Fn+F10 has no effect (my F10 key is blank, has no label). How do i reactivate the webcam? How do i figure out what turned it off?

Tried

sudo rmmod uvcvideo
sudo modprobe uvcvideo

Didnt work.

PanP4 Karmic

---

### Post by isantop on 2010-07-02
Please open a terminal (Applications > Accessories > Terminal) and run:```
lsusb
```once before pressing Fn+F10 and again after. Post the output here, and I'll make sure the computer is recognizing the webcam.

---

### Post by silvertuna on 2010-07-04
Here's the output. Before Fn+F10 and after.

```
silvertuna@silvertuna-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0402:5606 ALi Corp. USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
silvertuna@silvertuna-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
silvertuna@silvertuna-laptop:~$ 
```

---

### Post by silvertuna on 2010-07-08
When i run Cheese i get this and NO video. 

```
silvertuna@silvertuna-laptop:~$ cheese -v
Cheese 2.28.1 
Probing devices with HAL...
Found device 0402:5606, getting capabilities...
Detected v4l2 device: USB2.0 Camera
Driver: uvcvideo, version: 256
Capabilities: 0x04000001

Probing supported video formats...

```

---

### Post by silvertuna on 2010-07-08
And when i run gestreamer-properties, i get this - 

```
silvertuna@silvertuna-laptop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

```

---

### Post by silvertuna on 2010-07-08
And this dmesg output - 

```
silvertuna@silvertuna-laptop:~$ dmesg | grep -i video
[    4.580130] pci 0000:01:00.0: Boot video device
[    6.596169] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/device:04/input/input6
[    6.596204] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   26.025303] Linux video capture interface: v2.00
[   26.027448] uvcvideo: Found UVC 1.00 device USB2.0 Camera (0402:5606)
[   26.048943] usbcore: registered new interface driver uvcvideo
[   26.048946] USB Video Class driver (v0.1.0)
[  459.754454] uvcvideo: Found UVC 1.00 device USB2.0 Camera (0402:5606)
[  553.204118] uvcvideo: UVC non compliance - GET_MIN/MAX(PROBE) incorrectly supported. Enabling workaround.
[  553.307650] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[  654.859769] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[  783.716532] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[  805.746397] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[ 1430.857237] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
silvertuna@silvertuna-laptop:~$ 

```

---

### Post by thomasaaron on 2010-07-08
Make sure Cheese and Skype are completely turned off. That means, you will have to right-click the Skype icon in the upper toolbar and select quit.

Please press Fn-F10 and run lsusb until you see this line...

Bus 002 Device 003: ID 0402:5606 ALi Corp. USB 2.0 Camera

That means your camera is on. Now, open Cheese. What happens?

---

### Post by silvertuna on 2010-07-08
I get the multicolor test pattern and fuzzy gray and black box in lower right.

---

### Post by thomasaaron on 2010-07-09
OK, it does sound to me like a bad web cam, but if you could run one more test, I think we can confirm it.

Please boot from a live 10.04 / 64-bit CD. Once there, establish an Internet connection and open a terminal. Run this command...

sudo apt-get install cheese

Then, run lsusb and see if your camera is on. If it's not, press Fn-F10 and verify that it is on in lsusb.

Then open cheese.

What happened? (This should help us eliminate the possibility of a configuration issue.)

---

### Post by silvertuna on 2010-07-13
Live CD launched.  Fn+F10, checked lsusb.  Webcam on. Result no image, black screen only. In Preferences/Webcam/Device "USB 2.0 Camera (dev/videoO)" appears but is grayed-out.

;(

---

### Post by thomasaaron on 2010-07-13
silvertuna, one last thing...

Please go to System > Admin > System76 Driver and click the Install Drivers tab and the Install button. When the driver finishes, reboot.

Did that make a diff?

---

### Post by silvertuna on 2010-07-13
No difference, no image in Cheese.  What are my options now? Should i email you directly?

---

### Post by thomasaaron on 2010-07-14
Yes, lets move this to email... 

support...at...system76...dot...com

---

