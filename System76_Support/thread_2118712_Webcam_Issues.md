---
title: "Webcam Issues"
date: 2013-02-22
forum: System76 Support
---

### Post by jedsled on 2013-02-22
After a recent ubuntu update, I no longer had webcam functionality. I reinstalled 12.10 via a live disk and tested the webcam with cheese--it worked fine. It only stops working after fully updating.

The restore settings feature via the System76 driver did not fix the problem.
Resetting things to "Optimized Defaults" in the bios didn't help either.

This could be a number of things (gstreamer?, kernel patch?). I will look at the packages installed in the update

Model: Lemu4, Ubuntu 12.10

UPDATE: Device is still listed under ls /dev/video* as video0
lsusb still displays the device
In the preferences menu of cheese the device is still recognized but no image is displayed.
Testing the pipeline in gstreamer-properties yields no display of output, only says "testing pipeline"
kamerka doesn’t display anything either.

I think the problem is coming from linux-headers-generic 3.5.0.25.31

UPDATE 2: Running the System Testing program's camera test shows that it doesn't work.
Results for picture test: Image viewer opened and said "Could not load image 'camera_test_lm810p.jpg'. Error interpreting JPEG image file (Improper call to JPEG library in state 200)"
Nothing showed up at all during the video test.

UPDATE 3: Forced linux-image-generic and linux-headers-generic to earlier version with Synaptic - Still no success.
Reset cheese's config with dconf editor - Unsuccessful

I'm running out of ideas :S

Update 4: Similar to cashat, guvcview works and skype does not. I also filed a system76 support case and have yet to receive a reply.

Update 5: Forgot to mention earlier that fn+f10 does turns the camera on or off but image/video is still not displayed.

Could these certain programs have incompatibilities with kernel updates rather than this being a kernel fault? Perhaps an ffmpeg library or something to do with gstreamer prevents these programs from working correctly with a new kernel? I know cheese is fairly unreliable but the null result from gstreamer-properties is suspicious.

---

### Post by cashat on 2013-02-23
I have the same problem. Tried to restore, reboot, install, reboor the system76 driver. Still cheese recognize my camera, but no picture. 
PC:lemur4
Ubuntu 12.10 
Camera:  BisonCam, nb Pro
linux-image-3.5.0-20-generic (3.5.0-25.38)

Hope there will be a solution to this!

EDIT1: Installed guvcview and i can view picture from the camere, but still, not working with cheese, skype

EDIT2:System test 
/dev/video0: OK     name   : BisonCam, NB Pro     driver : uvcvideo     version: 3.5.7     flags  : 0x4000001 [ CAPTURE STREAMING ]     Format: YUYV (YUV 4:2:2 (YUYV)) Resolutions:  640x480,352x288,320x240,160x120,176x144,1600x1200,1280x1024,1280x720,640x480  Format: MJPG (MJPEG) Resolutions:  640x480,352x288,320x240,160x120,176x144,1600x1200,1280x1024,1280x720,640x480   
But fails to capture an image

EDIT3:Changed grub so i can choose kernel. Used the old kernel and [COLOR=Red]camera works[/COLOR]. Must be the updated kernel.

---

### Post by betorr on 2013-02-24
Hello, its my first time posting here.
I am having the exact same problem since last Friday night, which correlates with a recent update.
I am running ubuntu 12.04 on a lemur ultra
camera: Chicony Electronics 2.0
Cheese, VlC, player and Camorama, all open but display nothing. The device is listed on  /dev/video0. At first the system76 driver would not open to do a system restore, it would crash and generate an error report. A subsequently did a clean install of Ubuntu 12.04, where I noticed the the camera functioned perfectly on Camorama when booted in the installation USB. So the camera itself is not broken.  After installation system-76 driver works and can do a system restore, but cheese, vlc, camorama still display no image. All so did a gstreamer-properties video test with same negative results. I have opened a support note on system76 website have not heard a  reply as of yet.

---

### Post by FreedomOverdose on 2013-02-24
Same here. I think the problem first appeared after one of the latest kernel updates. If I boot with an older version of the kernel the camera works fine...

---

### Post by spazzeri on 2013-02-25
Similar problem on panp9 running 12.10 ubuntu.

The integrated webcam is listed in Cheese's preferences but its screen area remains black.

On live USB 12.04 and 12.10, Cheese does work.

---

### Post by mfraser on 2013-02-25
I'm running Kubuntu 13.04 with kernel 3.8.0-5 and I can't get the BisonCam, NB Pro to work either.

---

### Post by jedsled on 2013-02-25
Output of some commands:

jedidiah@jedidiah-Lemur-Ultra:~$ sudo modprobe uvcvideo
[sudo] password for jedidiah: 
jedidiah@jedidiah-Lemur-Ultra:~$ dmesg | grep BisonCam
[    2.762663] usb 3-4: Product: BisonCam, NB Pro
[   12.537878] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0401)
[   12.542772] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input5
[   92.105695] usb 3-4: Product: BisonCam, NB Pro
[   92.108852] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0401)
[   92.113966] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input11
jedidiah@jedidiah-Lemur-Ultra:~$ dmesg | grep uvcvideo
[   12.537878] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0401)
[   12.542938] usbcore: registered new interface driver uvcvideo
[   92.108852] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0401)

Function key toggles the existence of /dev/video0

---

### Post by jamesmcq24 on 2013-02-25
Reporting this issue as well. guvcview does display video, but cheese, vlc, and google hangouts do not. 

fn+f10 does control /dev/video0 but does not seem to get the camera working

---

### Post by jedsled on 2013-02-25
From System76 support case

"Thank you for your  email.  We're believing there is a software bug as a result of a recent  update that's affected the camera.  The camera itself seems to work,  just does not provide any on-screen feedback, although taking pictures  with the camera seems to work as it should.  

"We do have an internal bug that we're tracking and I'm adding you to it so we may provide periodic updates on the issue."

Do the problems persist only  on 12.10 or also 12.04? I might try 12.04 and see if this regression is only in 12.10's update channel.

---

### Post by dfarthur on 2013-02-26
> **jamesmcq24 said:**
> Reporting this issue as well. guvcview does display video, but cheese, vlc, and google hangouts do not. 

fn+f10 does control /dev/video0 but does not seem to get the camera working

Exactly the same on my machine.

---

### Post by FreedomOverdose on 2013-02-26
> **jamesmcq24 said:**
> Reporting this issue as well. guvcview does display video, but cheese, vlc, and google hangouts do not. 

fn+f10 does control /dev/video0 but does not seem to get the camera working

Yes,  I can also confirm that the webcam works on guvcview, but not on skype/google hangouts/cheese webcam booth...

---

### Post by cashat on 2013-02-27
Updated to kernel 3.5.0-26 and now the camera works again

EDIT1: Updated via software updater.

---

### Post by FreedomOverdose on 2013-02-27
> **cashat said:**
> Updated to kernel 3.5.0-26 and now the camera works again

Did that update show up in the Software Updater?

---

### Post by Flopy on 2013-02-27
It shows up once you enable the `quantal-proposed` repository.

---

### Post by isantop on 2013-02-28
We're looking into the updated kernel in quantal-proposed. For now, we recommend against upgrading your system yet, as updates in proposed can have adverse, unwanted side effects. If we can find that it's a workable solution, we'll update all support tickets on our website with instructions.

In the meantime, we encourage all users experiencing this issue to open support tickets on the website if you haven't yet. This will allow us to best track your issue and get the solution out to you as quickly as possbile.

---

### Post by Mugatu on 2013-03-06
I've run into this same problem on my Lenovo laptop.  I've documented some instructions as well as a bug report here:

[http://askubuntu.com/a/264461/18665](http://askubuntu.com/a/264461/18665)

Please contribute to the bug report so we can get more attention from developers and hopefully get this issue fixed soon.  Thanks!

---

### Post by lodoc on 2013-03-07
With my old computer using 12.04 the camera worked fine.  When I recently purchased a Pan with 12.10 installed no camera app will bring a picture up.

---

### Post by mörgæs on 2013-03-07
It seems like one or more regressions are in play.
Would be good if people could test 13.04 and see if the problem is solved. 

If 13.04 is also buggy: A bug report against this one will receive more attention than 12.04 / 12.10.

---

### Post by hamrick on 2013-03-08
I am having the same issue on my lemu4 system.  All works with a live disk, but fails with the latest updates. Hope it is resolved with further updates.

---

### Post by Mugatu on 2013-03-08
> **hamrick said:**
> I am having the same issue on my lemu4 system.  All works with a live disk, but fails with the latest updates. Hope it is resolved with further updates.

It sounds like this could be related to the issue I found.  It only takes a few minutes to try out the fix and contribute to the bug report.  If we hope to get this fixed, we need to get more attention for it:

[http://askubuntu.com/a/264461/18665](http://askubuntu.com/a/264461/18665)

---

### Post by Mugatu on 2013-03-08
> **mörgæs said:**
> It seems like one or more regressions are in play.
Would be good if people could test 13.04 and see if the problem is solved. 

If 13.04 is also buggy: A bug report against this one will receive more attention than 12.04 / 12.10.

I'm probably staying away from 13.04.  At least 12.04 will be supported for 5 years.  13.04 might not even get the normal 18 months of support:

[Ubuntu 13.04 Still On Course for April Release?]("http://www.omgubuntu.co.uk/2013/03/ubuntu-13-04-still-on-course-for-april-release")

Of course if anyone does test this against 13.04 it could easily be added to the existing bug report.

---

### Post by isantop on 2013-03-08
**As a quick note to any System76 customer experiencing this issue:**

We do have a workaround available until an updated kernel is released. Please open a support ticket, and we'll be able to get you the workaround, and let you know when the updated kernel is available.

> **Mugatu said:**
> I'm probably staying away from 13.04.  At least 12.04 will be supported for 5 years.  13.04 might not even get the normal 18 months of support:

[Ubuntu 13.04 Still On Course for April Release?]("http://www.omgubuntu.co.uk/2013/03/ubuntu-13-04-still-on-course-for-april-release")

Of course if anyone does test this against 13.04 it could easily be added to the existing bug report.

Those thoughts were actually overruled by Mark Shuttleworth yesterday. 13.04 is still on for release with the full 18-month support: [http://www.markshuttleworth.com/archives/1228](http://www.markshuttleworth.com/archives/1228)

---

