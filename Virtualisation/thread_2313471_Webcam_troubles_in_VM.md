---
title: "Webcam troubles in VM"
date: 2016-02-12
forum: Virtualisation
---

### Post by apple_man on 2016-02-12
Hello community,

First of, I hope that this is in the proper section.

Alright guys, this is driving me insane! My webcam in Virtual Box won't work.

I am running** Ubuntu 14.04.3 LTS in Virtual Box 5.0.6, on a Windows 10 host.** I need a webcam for a computer vision project in OpenCV. 

I specifically bought the Trust SpotLight Webcam Pro since it was supposed to work as per [this]("http://www.ideasonboard.org/uvc/") list. When I run the video.py test I just get a black screen. 

When I run lsusb it gives me this (seems like the webcam is recognised):

```

Bus 001 Device 002: ID 0c45:6340 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Cheese also gives me a black screen, and returns this in the terminal:

```
libGL error: pci id for fd 10: 80ee:beef, driver (null)
libGL error: core dri or dri2 extension not found
libGL error: failed to load driver: vboxvideo

```

I added the USB device filter in the VirtualBox settings (3D acceleration is off), however when I hover over the filter I see that the state is *not* supported. 

Can this be fixed, or should I return my webcam and get a new one? If so, how would I know which one will work since the list obviously contains errors.

Thank you.

[B]EDIT: Tested with Logitech C270 an C310, same result........

EDIT 2: Solved it by using the integrated web cam
[/B]I don't know if this has anything to do with it, but this is how I solved it. In Virtual Box I went to the USB filter of the webcam, and removed everything except the VendorID and ProductID (I found that [here]("https://forums.virtualbox.org/viewtopic.php?f=6&t=59303&start=15")). But then when I clicked OK, Virtual Box didn't respond, so I had to reboot my PC.  When I opened up the VM, my integrated web cam appeared under the Devices menu. I still get the same errors, but it works! I think those errors have something to do with 3D acceleration?

---

### Post by MAFoElffen on 2016-02-13
So is it recognized in Ubuntu 14.04? (the host). The doc's you posted has it's ID as 0c45:62c0... I do not see that specific address in your output. Are you saying it is showing up as 0c45:6240? That is showing uought that with Macrodia, someone cam up with a drier, but you had to compile and add yourself manually...

Found info on that [here]("http://www.64bitjungle.com/tech/microdia-webcam-0c54-experimental-drivers-installation-and-testing-part-1/")

---

### Post by apple_man on 2016-02-13
> **MAFoElffen said:**
> So is it recognized in Ubuntu 14.04? (the host). **The doc's you posted has it's ID as 0c45:62c0... I do not see that specific address in your output. Are you saying it is showing up as 0c45:6240**? That is showing uought that with Macrodia, someone cam up with a drier, but you had to compile and add yourself manually...

Found info on that [here]("http://www.64bitjungle.com/tech/microdia-webcam-0c54-experimental-drivers-installation-and-testing-part-1/")

Oh man, you are right, I totally missed that! It does not show up as** 0c45:6240**, it shows up as[B] 0c45:6340.

 [/B]But that is so odd since I do have the samel model, but it has another ID. Hmmm... 

The link you gave does not work? (error establishing a database connection)

---

### Post by MAFoElffen on 2016-02-13
That link works for me, but may be regional IP filters. I am USA.

Google: "Microdia WebCam (0c45:xxxx) experimental drivers &#8211; installation and testing Part 1" That was the blog entry of that.

---

