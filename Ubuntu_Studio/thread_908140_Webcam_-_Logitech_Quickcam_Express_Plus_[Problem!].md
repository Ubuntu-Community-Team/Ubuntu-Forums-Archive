---
title: "Webcam - Logitech Quickcam Express Plus [Problem!]"
date: 2008-09-02
forum: Ubuntu Studio
---

### Post by modjoa on 2008-09-02
hi, guys :)

Yesterday I purchase a new web cam - ID 046d:092f Logitech, Inc. QuickCam express Plus, but I have a problems when I tried to use it on Ubuntu 8.04. Before purchasing the webcam, I make a short search and according to: [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams), the camera should works without any additional drivers, but that's not true in my case :(.
I tried to install the drivers with Easycam2(the installation process finished successfully), I followed the instructions on [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html), but I had bad luck all the time. I also follow all the links listed in [http://ubuntuforums.org/showthread.php?t=907309&highlight=logitech+express](http://ubuntuforums.org/showthread.php?t=907309&highlight=logitech+express), but the webcam still doesn't work.
dmesg gives me the following errors;

[  186.305653] usb 4-1: USB disconnect, address 2
[  186.305780] gspca: disconnect complete
[  187.003649] usb 4-1: new full speed USB device using uhci_hcd and address 4
[  187.037235] usb 4-1: configuration #1 chosen from 1 choice
[  187.043401] gspca: probing 046d:092f
[  187.105089] gspca: probe ok
[  187.155085] gspca: disagrees about version of symbol video_devdata
[  187.155096] gspca: Unknown symbol video_devdata
[  187.155333] gspca: disagrees about version of symbol video_unregister_device
[  187.155335] gspca: Unknown symbol video_unregister_device
[  187.155423] gspca: disagrees about version of symbol video_device_alloc
[  187.155425] gspca: Unknown symbol video_device_alloc
[  187.155459] gspca: disagrees about version of symbol video_register_device
[  187.155461] gspca: Unknown symbol video_register_device
[  187.155631] gspca: disagrees about version of symbol video_usercopy
[  187.155633] gspca: Unknown symbol video_usercopy
[  187.155666] gspca: disagrees about version of symbol video_device_release
[  187.155668] gspca: Unknown symbol video_device_release

when I tried to use it, for example with Skype, it just crashes and gives me the following error message:

[  106.085158] gspca: usb_submit_urb [0] err -28

 Do you have any idea how to solve the problem? I suppose that there is a conflict between drivers, because previously I had got a no-name Chinese webcam, for which I compiled, installed and tried a lot of drivers.... So my question is how to remove all previously installed drivers, maybe then my Ubuntu will recognize automatically the Webcam?

---

### Post by nalmeth on 2008-09-02
I wonder if the problem is with skype and not with the webcam drivers.

I always refer people to this page: 
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Looks like you have used EasyCam2 to install drivers, which is all I needed to do for my Logitech Quickcam. Since the install completed successfully, try installing camorama, and see if it can pick up video from the cam.

Alternatively, you can use the command-line to capture some video:
[https://help.ubuntu.com/community/Webcam#Recording](https://help.ubuntu.com/community/Webcam#Recording) video

If you can capture video with any of these tools, then the driver is working fine and the problem may be with skype.

However, if all that fails, maybe this link will be of some help (although its for an older release of ubuntu):
[https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy](https://help.ubuntu.com/community/InstallingLogitechQuickcamPro5000OnEdgy)

---

### Post by kostkon on 2008-09-02
> **modjoa said:**
>  Do you have any idea how to solve the problem? I suppose that there is a conflict between drivers, because previously I had got a no-name Chinese webcam, for which I compiled, installed and tried a lot of drivers.... So my question is how to remove all previously installed drivers, maybe then my Ubuntu will recognize automatically the Webcam?
I believe, it should have been recognised by Ubuntu and work right away. I have the same camera and it works with any web camera aware application, like *Cheese*, *Skype*, *Ekiga*, and even *Flash* just fine.

Although, mine has the ID *046d:092d*, maybe yours is a newer model, a little different that does not work?

You may have created a conflict with the drivers you have compiled and installed so, yes, you could try to remove them to be sure that they don't create problems.

Could you give the source of these drives?

---

### Post by modjoa on 2008-09-03
hi, guys, in fact I have already tried ekiga, canorama, which also just crashed at start up. I have reinstall the easycam2 drivers and camorama application, but the problem still occurs.
The drivers I have previously tried for my Chenese webcam (not for Logitech) was downloaded and modified from here: [http://moinejf.free.fr/gspca_README.txt](http://moinejf.free.fr/gspca_README.txt) and [http://article.gmane.org/gmane.linux.drivers.spca50x.devel/2946](http://article.gmane.org/gmane.linux.drivers.spca50x.devel/2946)

How to make sure that all previously installed drivers doesn't affect me. How to remove them?

---

### Post by Crafty Kisses on 2008-09-05
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by modjoa on 2008-09-06
I tried what you suggest but Ekiga is not working, it gives me the following error message:
> 
Error while opening video device Camera

A moving logo will be transmitted during calls. Notice that you can always transmit a given image or the moving logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

Your driver doesn't seem to support any of the color formats supported by Ekiga.
 Please check your kernel driver documentation in order to determine which Palette is supported.

Easycam2 recognize my webcam Logitech Quickcam Express Plus as: Logitech QC  Elch2

lsusb returns the following identification of the webcam:
Bus 005 Device 002: ID 046d:092f Logitech, Inc. QuickCam express Plus

Obviously the problem comes from the drivers... but I didn't how to fix it...

---

### Post by dawhistler on 2008-12-11
Hello there and sorry if this has been answered already.

I took this from another site and it worked for me.

[https://answers.launchpad.net/ubuntu/+question/49739](https://answers.launchpad.net/ubuntu/+question/49739)

DONT forget to make the file /usr/local/bin/skype_wrapper EXECUTABLE.
(check the box to make it executable located in the properties box, permissions tab.)



mas

8.10
Logitech QuickCam Communicate STX

---

