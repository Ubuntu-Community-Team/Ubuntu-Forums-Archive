---
title: "Panp5 - Webcam quit working"
date: 2009-09-08
forum: System76 Support
---

### Post by samalex on 2009-09-08
Hi.

I don't use my webcam much, but this evening I fired up Cheese to play with it and saw the message that no webcam was found.  I then opened Skype which has worked with the webcam before and it said the same thing.

Any suggestions on what to try and check out to see what's going on?  I'm running Ubuntu 9.04, which was preloaded, and all updates to date.

Thanks in advance...

Sam

---

### Post by samalex on 2009-09-09
In an earlier post someone asked about the webcam not working, and it was suggested to reinstall the drivers using the System76 Driver app because sometimes kernel updates can remove the drivers.  I've done this and rebooted, but there's still no webcam listed on any apps (Skype, Cheese, or Ekiga).  

Here's output from lsusb
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

and shouldn't the webcam appear here if it's working and installed?  Also dmesg doesn't show any reference to video0 or video4linux.  

Any other suggestions?

Thanks --

Sam

---

### Post by samalex on 2009-09-09
One more quick update... I don't know if the webcam works with the stock version of Ubuntu, but I booted from the live version of 9.04 from CD and lsusb didn't show the webcam either.  Ubuntu outta the box has no webcam software from what I saw, but i hoped to see some reference to it from terminal if it was working correctly.

At this point I'm at a loss on what to try next.  

Update: I didn't want to keep adding stuff to the thread, but I just noticed there's no /dev/video0.  Is this auto created or should it already be there for the driver to work?  Also if it was once there what would cause it to be deleted?  Just checking.  I'll try to add it and reboot then see if the webcam works.

Thanks --

Sam

---

### Post by samalex on 2009-09-09
Yet another update. 

I created /dev/video0 but no dice... rebooting just removed it.  In reading through other posts I stumbled on gstreamer-properties which I ran as root.  The Multimedia Systems Selector came up, and under Video the "Plugin" selected for "Default Input" is "Video for Linux 2 (v4l2)".  When I click Test it says "Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'".

Is there a way to manually reinstall the driver or check to verify it's installed and running?  I'm not sure what type of webcam came with the laptop so I'm not sure what to look-up.

Thanks again for any suggestions... Take care,

Sam

---

### Post by thomasaaron on 2009-09-09
Hi, Samalex.

You have to press Fn-F10 to turn the webcam on.

---

### Post by samalex on 2009-09-09
[QUOTE="thomasaaron"]You have to press Fn-F10 to turn the webcam on. [/QUOTE]

No.... Well crap.  Nevermind then, that did it.  

I've never had to do that before to get the webcam going, so is this new?  At least I learned a few new things about my system in this endeavour :)

As always thanks for your help ...

Sam

---

### Post by thomasaaron on 2009-09-09
It's not new (at least not intentionally new). I've seen this on a few other computers. Something seems to change the default status of the webcam.

---

### Post by miniyak on 2009-09-09
I have had the same issue, fn-f10 seem to do something but cheese and skype still fails to recognise. Cheese seems to be thinking when fn-f10 on, if i press f10 again it says camera not found 

f10 and 12 really should be labeled like all the other F keys it would save tom a few support questions and the customers the headache of thinking their unit is broke.

---

### Post by samalex on 2009-09-10
[QUOTE="miniyak"]I have had the same issue, fn-f10 seem to do something but cheese and skype still fails to recognise. Cheese seems to be thinking when fn-f10 on, if i press f10 again it says camera not found

f10 and 12 really should be labeled like all the other F keys it would save tom a few support questions and the customers the headache of thinking their unit is broke.[/QUOTE]

After I start-up and hit Fn-F10 it looks like Cheese and Skype both worked fine... I didn't try opening them first then hitting Fn-F10 but it looks like until the driver is active /dev/video0 isn't there for the applications to tie to.

I agree about the key label, but as long as I know what to press it doesn't matter to me either way.  I just wonder why it didn't do this to me outta the box... it just now started requiring me to use Fn-F10 to enable the webcam but used to be enabled on startup.  Oh well, as long as it works.

Take care --

Sam

---

### Post by miniyak on 2009-09-11
I tried using fn-f10 to get the cam to work with cheese, before starting cheese, while cheese was running and after a restart.

like previously stated it seems to be working in some way but there is no picture in cheese (just the hourglass wheel) and skype seems to look for something but finds nothing, ekiga recognizes a usb 2.0 camera where as it found a "bison webcam" while it was working when i first got the panp5. May be i just need to reinstall the drivers or something?

---

### Post by thomasaaron on 2009-09-11
Run...
```
lsusb
```
...and then press Fn-F10. And then run...
```
lsusb
```
...again.

Post the output of both runs of lsusb.

---

### Post by miniyak on 2009-09-11
```
Bus 002 Device 003: ID 0402:5606 ALi Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 147e:2016  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by thomasaaron on 2009-09-14
Thanks. This line...

Bus 002 Device 003: ID 0402:5606 ALi Corp. 

...means your camera is on. So, get that line to appear in lsusb, and then try out Ekiga Softphone (Applications > Internet > Ekiga...)

When you're in Ekiga, go to Edit > Preferences > Video > Devices. Make sure the Input Devices drop-down is set to USB Camera. It might have some other option. If you can't figure it out, let me know what you are seeing. If you don't see anything useful, click the "Detect Devices" button. Once you have it set to the camera, click the 'Close' button. 

Then click the little video camera icon.

Did that work?

---

### Post by miniyak on 2009-09-14
I had a feeling the webcam was "turning on", because ekiga, skype, and cheese all seem to recognize that there is a usb 2.0 camera (except skype seems to freeze while testing/detecting) The problem is that video will no longer come up regardless of recognizing the hardware 

ekiga does have the usb 2.0 option in video devices but i personally dont have a way of testing this as no one i know can stand to use ekiga. I tried a test and conference call but the video icon is blurred out. This may be because of those type of calls but i dont know, i assume video is not going through.

---

### Post by thomasaaron on 2009-09-14
> except skype seems to freeze while testing/detecting

Ah. Try turning off your desktop effects. I've seen that before. System > Prefs > Appearance > Visual Effects > None.

> but i personally dont have a way of testing this as no one i know can stand to use ekiga

You can test your own camera in Ekiga without having someone to call. Go to Edit > Preferences > Video > Devices. Make sure the Input Devices drop-down is set to USB Camera. Once you have it set to the camera, click the 'Close' button. Then click the little video camera icon.

---

### Post by miniyak on 2009-09-14
skype- ok maybe skype is just a cpu hog... i said skype "froze" but its more like is doesn't want to do anything when i press "test video". Everything else is still responsive.

ekiga- Sorry, my call panel was hidden so the video icon was hidden also. When the video icon is pressed, ekiga freezes and the unresponsive program window pops up asking me to wait or force quit.

*unrelated* The irony of disabling desktop effects is that i get more. I mainly use CCSM to turn things off like window decorations and animations.. though maybe i can do that a different way.. *

---

### Post by HotShotDJ on 2009-09-14
> **miniyak said:**
> *unrelated* The irony of disabling desktop effects is that i get more. I mainly use CCSM to turn things off like window decorations and animations.. though maybe i can do that a different way.. *Try installing "fusion-icon" (available through Synaptic Package Manager).  This will allow you to switch between Compiz and Metacity on-the-fly using a Notification Area icon.

---

### Post by thomasaaron on 2009-09-15
I like the Fusion Icon too. For testing purposes, though, please turn desktop effects off via System > Preferences > Appearance > Visual Effects > None.

Then try Ekiga and Skype again.

---

### Post by Guille Damke on 2009-10-04
Hi people,

I think that the problem that this user has experienced with his webcam is the same that other Pangolin users have had (including myself). It is just a hardware failure, the camera is recognized as ALi Corp., but any application that you try to run with the camera does not work at all and show the same behavior: they seem to hang just waiting to get any answer from the broken camera. 
Definitely, a hardware problem. I hope someone found a solution. Does someone has an Ali Corp. camera in a Pangolin that works? It would be good to know it.

Cheers.
Guille.

---

### Post by miniyak on 2009-10-04
guille pretty much summed it up. It seems like thats it for my cam. Tried suggested solution again, but Its doubtful compiz is interfering. With the symptoms i'm seeing at least. I have seen compiz interfere and it is normally when a program want to initialize new graphics modes or settings, like for a game something. In my case there is no indication to show the applications themselves are failing or acting sluggish for any other reason then dysfunctional camera.  

Only question now is, are there other ideas for a possible solution if this isn't hardware failure?

Or maybe i will just try and get the EyeToy i have lying around to work with it... maybe latter

---

### Post by thomasaaron on 2009-10-05
Guille Damke and miniyak,

To find out if it is a hardware problem, boot from a live CD, toggle your webcam no using the function key combination (verify it with lsusb), turn off your Desktop Effects and see if the cam will work under Ekiga.

If it doesn't, it's a hardware problem. If it does, you have a configuration issue or a software conflict going on.

If it's hardware, contact me at support...at...system76...dot...com.

---

