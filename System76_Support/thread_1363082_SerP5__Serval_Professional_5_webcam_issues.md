---
title: "SerP5 / Serval Professional 5 webcam issues"
date: 2009-12-23
forum: System76 Support
---

### Post by achrity on 2009-12-23
Hello all! So, earlier today I ran the auto updater - as I hadn't in a while - and immediately noticed that my webcam no longer worked. It was functioning properly right up until I rebooted (it seems that a kernel update came along with it), at which point it just stopped. I first noticed this on a Skype chat, where I could see the person I was chatting with, but Skype didn't seem to be picking up a signal from my webcam. They said it wasn't showing anything at all, and my self view showed only a gray box. Trying it in Cheese yielded only what I think is the 'no signal' image: a lot of pretty colored boxes with a small square of static in the bottom left corner.

While talking to a far more technically talented friend than I (who gave up, telling me to Google it), I ran a few commands in terminal. "ls /dev | grep video" gives me one result - video0 - which I do think is my webcam. In my mind, that implies that my computer can detect it, but is not receiving a signal from it. I'm a bit of a newb, though, so I may very well be wrong in that assumption. "dmesg | grep video" gave me the following output: ```
[    1.091391] pci 0000:01:00.0: Boot video device
[   30.462750] Linux video capture interface: v2.00
[   30.464799] uvcvideo: Found UVC 1.00 device USB2.0 Camera (0402:5606)
[   30.482735] usbcore: registered new interface driver uvcvideo
[  144.832285] uvcvideo: UVC non compliance - GET_MIN/MAX(PROBE) incorrectly supported. Enabling workaround.
[  145.031567] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[  187.526730] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[  601.410226] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[  861.606238] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[ 1263.043423] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[ 1971.147877] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[ 4006.756660] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[ 4292.178431] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[ 4605.689079] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[ 7239.345788] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
[ 8157.013287] uvcvideo: device USB2.0 Camera requested null bandwidth, defaulting to lowest.
```I've really no clue as to what's wrong here, and searching this forum as well as Google hasn't turned up many results. A few details as to my system, I suppose, might help: In case the title didn't clue you off, I have a SerP5, and am running Ubuntu 9.10 Karmic Koala 64 bit. Any help at all would be appreciated, as I'd love to get my webcam up and working again. Thanks!

~achrity

---

### Post by thomasaaron on 2009-12-26
First, run your system76 driver (System > Admin > System76 Driver > Install tab > Install button).

Second, reboot.

Did that fix it?

If please run this command from a terminal...

lsusb

Does your camera appear there?

If not, Press Fn-F10 simultaneously. Then run...

lsusb

Does your camera appear now?

---

### Post by achrity on 2009-12-26
Hmm, unfortunately, the System76 driver did not appear to help. lsusb did indeed show my camera, both before and after pressing Fn-F10, at least assuming that this is it:
```
Bus 001 Device 004: ID 0402:5606 ALi Corp. USB 2.0 Camera
```Is there something else that could be wrong? I think the computer is recognizing the device, but just not receiving an image from it. Thank you!

---

### Post by thomasaaron on 2009-12-28
Yes, that is indeed the camera.

I'd like to rule out a hardware problem before digging deeper. Could you boot into a previous kernel (press 'Esc' or 'Shift' when you see "Grub" in the upper corner of your screen to see a kernel list)? If your cam works there, we know an update hosed it. If it doesn't work there, please boot from a 9.04 / 9.10 64-bit live CD and test with Ekiga.

I'll be back in the office on Wednesday and can walk you through setting up Ekiga over the phone. It's not very intuitive.

---

