---
title: "Webcam not working on new Starling3"
date: 2010-11-04
forum: System76 Support
---

### Post by Dan Lucier on 2010-11-04
I have been trying to get my webcam working since,I got this computer yesterday. When I open Cheese, I get a message saying no device found. Sometimes, Cheese freezes. Any ideas?

System76 Starling3
Ubuntu 10.04 Netbook Remix

I'm still new to Ubuntu

Thanks

---

### Post by Dave_L on 2010-11-05
Before launching Cheese, did you enable the webcam with Fn + F10?

---

### Post by HotShotDJ on 2010-11-05
> **Dan Lucier said:**
> Sometimes, Cheese freezes. Any ideas?
Dan --

Cheese has been a problem for at least a year for many people across several distributions.  I've found several active bug reports against Cheese that describe your problem (and mine on my Panp5 and my friend's Star1). EDIT: Perhaps you mean something else regarding Cheese freezing since your webcam isn't detected (perhaps the "freezing" that you are reporting is related to Cheese being unable to detect the camera)... in any case, the rest of this message may, eventually, still apply. :)

Fortunately there is a solution: Once you resolve the problem with your webcam not being detected, remove Cheese (sudo apt-get autoremove cheese) and install GUVCViewer (sudo apt-get install guvcview).  GUVCViewer works quite well on both the systems that mention above without the freezing.  However, it isn't as intuitive as Cheese.  Also, it only works with webcams supported by the UVC driver.  Again, after you have resolved the problem with your webcam not being detected, you can check if it is supported by the UVC driver by running the following in a terminal:```
dmesg | grep uvc
```You should get something like "Found UVC 1.00 device..."  If so, you're good to go with GUVCViewer.

Also, when you first run GUVCViewer, it is important to open the Audio tab and set the input device to "pulse," otherwise, your video & audio may be out of sync when you do an AV capture.  Beyond that, the default settings seem reasonable and work well.

If you have any trouble with GUVCViewer, let me know and I'll be happy to help you out as best I can.

---

### Post by Dan Lucier on 2010-11-05
> **Dave_L said:**
> Before launching Cheese, did you enable the webcam with Fn + F10?

Oh, thank you. That worked. I didn't realize I had to do anything to enable it. How do I know when it is enabled or not? Is there any reason to disable it when I'm not using it (i.e. conserve battery)?

---

### Post by Dan Lucier on 2010-11-05
Thanks for the advice regarding GUVCViewer. I'll check it out. I probably won't even use Cheese; I just opened it to check the hardware on my new machine.

---

### Post by isantop on 2010-11-08
> **Dan Lucier said:**
> Oh, thank you. That worked. I didn't realize I had to do anything to enable it. How do I know when it is enabled or not? Is there any reason to disable it when I'm not using it (i.e. conserve battery)?

Apart from launching cheese (or another app), I'm not aware of any way to monitor that. It should be persistent across reboots, though, and it doesn't drain much, if any, power, so I think it should be okay to just leave it on.

---

### Post by carrie.kandira on 2011-10-16
What if it doesn't find The device? It says failed.

---

### Post by chriscross93 on 2011-10-17
> **isantop said:**
> Apart from launching cheese (or another app), I'm not aware of any way to monitor that. It should be persistent across reboots, though, and it doesn't drain much, if any, power, so I think it should be okay to just leave it on.

Yeah, the feature is only really useful if you are security paranoid.  (Like me...)

---

### Post by isantop on 2011-10-18
Actually, there is a good way to monitor the state of the webcam in 11.10. If you click on the Device Menu (Rightmost icon in the top right corner), there is a section called "Attached devices". In here, you should see an item for Printers, and if the webcam is on, you'll see one for the webcam as well.

---

