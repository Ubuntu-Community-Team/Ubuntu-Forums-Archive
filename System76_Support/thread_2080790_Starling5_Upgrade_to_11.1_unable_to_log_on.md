---
title: "Starling5 Upgrade to 11.1 unable to log on"
date: 2012-11-05
forum: System76 Support
---

### Post by chownoir on 2012-11-05
Hi,

I ran the upgrade based on screen instructions to do so. Downloaded everything and installed fine seemingly. Restart sends me to a screen saying Low Graphics mode. None of the keyboard commands seem to work to activate the OK.

I looked up the problem on the forum here but the solution doesn't work. I can't get the command line to recognize anything.

Please advise, thanks.

---

### Post by chownoir on 2012-11-05
Anyone? I can get to the Grub screen and the command line. But don't know what to do next.

---

### Post by isantop on 2012-11-06
> **chownoir said:**
> Anyone? I can get to the Grub screen and the command line. But don't know what to do next.

It sounds to me like the upgrade was corrupted while in progress. I would recommend doing an upgrade to 12.10 via a USB drive.

---

### Post by chownoir on 2012-11-06
Hi,

Can you point me to how I can do that? I know nothing about how to do an install. Where do I download the right version? After that, what do I do when I plug in the USB?

---

### Post by isantop on 2012-11-07
> **chownoir said:**
> Hi,

Can you point me to how I can do that? I know nothing about how to do an install. Where do I download the right version? After that, what do I do when I plug in the USB?

You can download the latest version from [http://www.ubuntu.com](http://www.ubuntu.com)

Once you have the LiveUSB made, you will leave it in the machine and restart. When you see the System76 Logo page, press F1 repeatedly to open up the boot menu. From there, choose your USB drive, then wait and follow any instructions on screen.

---

### Post by chownoir on 2012-11-07
Hi,

No love. I get the boot menu. I select the USB option,I get
JMicron JMC26x fast Ethernet controller version 1.0.0.25

Pxe-E61: media test failure, check cable
Pxe-m0f: exiting PXE rom
Operating system not found

I'm not sure why I'm getting that as its the second option on the boot menu but I'm not selecting that.

What should I try next?

---

### Post by isantop on 2012-11-08
> **chownoir said:**
> Hi,

No love. I get the boot menu. I select the USB option,I get
JMicron JMC26x fast Ethernet controller version 1.0.0.25

Pxe-E61: media test failure, check cable
Pxe-m0f: exiting PXE rom
Operating system not found

I'm not sure why I'm getting that as its the second option on the boot menu but I'm not selecting that.

What should I try next?

What is the USB drive listed as in the boot menu? Also, did you copy Ubuntu to the USB drive using the "Startup Disk Creator" app?

---

### Post by chownoir on 2012-11-08
Hi,

Followed all the instructions on the site to set up a bootable stick and I got the laptop up and running.

However, even though I selected the upgrade and not replace option, it looks like I wiped out my entire system! :(. 

I don't have any of documents, photos, etc. Any idea if there's even the vaguest of a chance that it's possible to recover. I double checked each selection to make sure I would keep all and not replace.

---

### Post by isantop on 2012-11-09
> **chownoir said:**
> Hi,

Followed all the instructions on the site to set up a bootable stick and I got the laptop up and running.

However, even though I selected the upgrade and not replace option, it looks like I wiped out my entire system! :(. 

I don't have any of documents, photos, etc. Any idea if there's even the vaguest of a chance that it's possible to recover. I double checked each selection to make sure I would keep all and not replace.

Go ahead and open the File Browser (Home Folder icon in the launcher on the left). Once it's open, press Ctrl+l, then type this in:

```
/home
```

followed by enter. Tell me if there are any folders listed there.

---

### Post by chownoir on 2012-11-12
I saw two home folders. Opened up the older one and all my files were in there! Awesome, thanks so much!

I created two profiles then? Is the best way just to copy the files in the old profile into the new one I'm logging into now?

Thanks for all the patience, I'm slowly learning here and not afraid to poke as you can see, I just need to know where to look for directions so I can figure it out.

---

### Post by isantop on 2012-11-13
> **chownoir said:**
> I saw two home folders. Opened up the older one and all my files were in there! Awesome, thanks so much!

I created two profiles then? Is the best way just to copy the files in the old profile into the new one I'm logging into now?

Thanks for all the patience, I'm slowly learning here and not afraid to poke as you can see, I just need to know where to look for directions so I can figure it out.

That's how I would do it.

---

### Post by chownoir on 2012-11-13
Thanks again for all the help. Is there anything I can do to help contribute. Write a quick document for another newbie like me detailing what steps I did? Is that of any value?

---

