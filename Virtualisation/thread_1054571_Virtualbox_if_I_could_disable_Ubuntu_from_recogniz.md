---
title: "Virtualbox: if I could disable Ubuntu from recognizing my ipod touch, i bet..."
date: 2009-01-29
forum: Virtualisation
---

### Post by surelock22 on 2009-01-29
...i bet my VM Windows XP would see it and I could enable it.

Because as of now, whenever I plug in my ipod touch, it recognizes it as a camera on Ubuntu. I try to "unmount" it, and it may leave the desktop, but it's still there under "places".

And at the same time, since I'm trying to get itunes to work in XP via VirtualBox, I need VB to recognize my USB'd ipod touch, and it sees it pre-powering on Windows, but doesn't allow me to enable it, and my guess is because its being looked at by Ubuntu.

So... what's the deal? Will I ever get my ipod touch to see my ubuntu based PC's much larger library of songs , or will I constantly have to sloppily delete music off my maxed out notebook pc's harddrive and re-fill it with new stuff via MP3 CD's?

 I've got another laptop that's more powerful than the other Windows notebook, and I'm thinking I'm gonna dual boot the thing to help subside these problems.

---

### Post by HotShotDJ on 2009-01-29
Before you start your virtual machine, plug in the iPod (don't worry about Ubuntu mounting it right now... it doesn't matter yet).  Now, click to highlight your XP VM, but DON'T start it!  Click on Settings, then USB.  You'll notice a large white box below the heading "USB Device Filters."  Right click anywhere in that large white box and choose "Add filter from device."  Select your iPod.  You notice it now appears in the large white box with a checked box next to it.  Click "OK."  Now, unmount and disconnect your iPod.  Start your XP VM.  After it is booted up and ready to use, plug in your iPod.  XP should capture the device immediately.

If this doesn't solve the problem, then the issue is something other than Ubuntu taking control of the device.

---

### Post by surelock22 on 2009-01-30
> **HotShotDJ said:**
> 

If this doesn't solve the problem, then the issue is something other than Ubuntu taking control of the device.

I did everything you said in the order you said it, and when i plugged in the ipod touch in fullscreen XP VM, it STILL doesn't allow me to use it. I windowed the VM and checked Ubuntu to see if it mounted in Ubuntu, and it did automatically when I plugged it in.

The ipod shows up as an unavailable device in the device/usb menu. It's "greyed out" and I can't enable it.

Hmmmmm, I've been trying to overcome this problem for about a month now. I'm glad people still try to help me get it solved though. :) Thanks.

---

### Post by lime4x4 on 2009-01-30
did u add the line for usb devices in your fstab file?

---

### Post by HotShotDJ on 2009-01-30
> **surelock22 said:**
> The ipod shows up as an unavailable device in the device/usb menu. It's "greyed out" and I can't enable it.Ok.  Let's put the iPod aside for a moment.  Tell me about your other USB devices.  Are they working?  (USB Printer, Flash Drives, USB Hard Drives, USB Whatevers).

---

### Post by surelock22 on 2009-02-07
> **HotShotDJ said:**
> Ok.  Let's put the iPod aside for a moment.  Tell me about your other USB devices.  Are they working?  (USB Printer, Flash Drives, USB Hard Drives, USB Whatevers). i take it you're talking about in VB. well, I'm not sure if this counts, but my keyboard and mouse are both usb, and they work. they are not added as USB devices though, there's no profile set for them. BUT if I look at my USB devices once my VM is on, I can see in "greyed out" form a Logitech USB mouse and a Logitech USB keyboard, but I cannot allow or disable those devices, the same way I can't disable the ipod which shows up in the same "greyed out" form.

Thanks for checking into this and helping me overcome this...

---

### Post by surelock22 on 2009-02-07
> **lime4x4 said:**
> did u add the line for usb devices in your fstab file?

yes. I did, along with the correct user number (was it 125?.. been awhile).

If I didn't, I wouldn't have USB support from the main VB menu, right?

---

### Post by HotShotDJ on 2009-02-07
> **surelock22 said:**
> I'm not sure if this counts, but my keyboard and mouse are both usb, and they work. they are not added as USB devices though, there's no profile set for them. BUT if I look at my USB devices once my VM is on, I can see in "greyed out" form a Logitech USB mouse and a Logitech USB keyboard, but I cannot allow or disable those devices, the same way I can't disable the ipod which shows up in the same "greyed out" form.USB Keyboards and Mice are not handled by the VB USB subsystem.  I was hoping you had a flash drive or USB hard drive other than the iPod.  I'm thinking that SOMETHING (I'm not sure what) is set up incorrectly.  I'd like you to take a look at:  [http://ubuntuforums.org/showpost.php?p=6398716&postcount=1](http://ubuntuforums.org/showpost.php?p=6398716&postcount=1)

See if there is something you missed when setting things up.  Also, there are some Trouble Shooting guidelines at the end of the HowTo.  If you still have problems, post back (with the information mentioned in the Trouble Shooting guidelines).

---

### Post by surelock22 on 2009-02-07
> **HotShotDJ said:**
> USB Keyboards and Mice are not handled by the VB USB subsystem.  I was hoping you had a flash drive or USB hard drive other than the iPod.  I'm thinking that SOMETHING (I'm not sure what) is set up incorrectly.  I'd like you to take a look at:  [http://ubuntuforums.org/showpost.php?p=6398716&postcount=1](http://ubuntuforums.org/showpost.php?p=6398716&postcount=1)

See if there is something you missed when setting things up.  Also, there are some Trouble Shooting guidelines at the end of the HowTo.  If you still have problems, post back (with the information mentioned in the Trouble Shooting guidelines).

I've gone through this once before, and I'm willing to give it another go when I get off work, but in all honesty, should I just try to use a different VM intead since it seems that this problem has occured with alot of folks? Do you know of anyone that has had any success getting an ipod touch v.2 to sync with itunes via this method anyways?

Again, I've got some time to kill tonight, I'll spend it on this: AGAIN!!!

---

