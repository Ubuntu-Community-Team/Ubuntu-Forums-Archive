---
title: "Ubuntu no go with VirtusalBox"
date: 2012-12-11
forum: Virtualisation
---

### Post by DrRus on 2012-12-11
Hi guys,

Decided to add Ubuntu to VB, but this is all I get when I start it (see attached photo). I have tried everything, including reinstalling and all I get is this background and that's it. I think I'm missing something very simple, but don't know what.

Any help?

---

### Post by LiamOS on 2012-12-11
Are the graphics settings are reasonably good on the virtual machine?

Try ctrl+alt+t to get a terminal open if it works.

Alternatively try doing alt+f2/3/... to get to a command line, which would be good for diagnosing what's wrong.

---

### Post by TheFu on 2012-12-11
Did you install the vbox guest additions successfully into the guestOS?

---

### Post by papibe on 2012-12-11
Hi DrRus. Welcome to the forums ):P

12Mb for video RAM is too little.

Later versions of Ubuntu (running Unity) require more video RAM (read [here]("https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements")). Try increasing it to 128Mb.

Let us know how it goes.
Regards.

---

### Post by DrRus on 2012-12-11
> **LiamOS said:**
> Are the graphics settings are reasonably good on the virtual machine?

Try ctrl+alt+t to get a terminal open if it works.

Alternatively try doing alt+f2/3/... to get to a command line, which would be good for diagnosing what's wrong.

Got the terminal open, but don't know what to do from there :) first time outside windows here, hehe...

> 12Mb for video RAM is too little.

Later versions of Ubuntu (running Unity) require more video RAM (read [here]("https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements")). Try increasing it to 128Mb.Done, but no difference.

> Did you install the vbox guest additions successfully into the guestOS?     I believe I did. To be 100% certain I think I will reinstall the whole thing once more :)

---

### Post by DrRus on 2012-12-11
Well,

I reinstalled Ubuntu and the same thing happened - just the background image and nothing else. The I began to install the guest additions and I got an error message "The application Compiz has closed unexpectedly". I tried to relaunch it a couple of times just to get the same error, so I ignored and continued with the guest additions. After restart - still nothing...

I can get the terminal open and even opened some text editor (?) by using "gedit" command. But other than terminal - nothing else. Not a fan right now :) Shame, considering Vista installed with no issues...

---

### Post by QIII on 2012-12-11
Did you check the md5sum on your downloaded image?  Did you check the media for errors?

---

### Post by TheFu on 2012-12-11
Don't login using the Unity interface. You can control that at the login OR by disabling the 2D and 3D GPU accel in the VM settings.  I always give desktop VMs 128MB of video RAM.  While not for Ubuntu VM Hosts, I've written up how to make the settings optimal for an Ubuntu VM Guest system running under a Windows HostOS here: [http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

To load the vbox guest extention dependencies, check this [http://blog.jdpfu.com/2012/07/05/virtualbox-guest-extension-dependencies](http://blog.jdpfu.com/2012/07/05/virtualbox-guest-extension-dependencies)

Sorry I don't have direct experience. I use KVM for Linux hosts, not VirtualBox. KVM is better for non-desktop OSes, IMHO.

---

### Post by andrew.46 on 2012-12-12
Have you had a look at the 3d settings in VirtualBox? I attach a screenshot to show the section of VB to look in...

---

### Post by DrRus on 2012-12-12
> **QIII said:**
> Did you check the md5sum on your downloaded image?  Did you check the media for errors?

I deleted everything and re-downloaded the iso. Then installed it, installed the guest additions - still nothing.

> Have you had a look at the 3d settings in VirtualBox? I attach a screenshot to show the section of VB to look in...

Enabling 3d made no difference.

---

### Post by TheFu on 2012-12-12
> **DrRus said:**
> Enabling 3d made no difference.

Actually, you want to disable 3D and not use Unity. To avoid Unity, before you login, click on the little circle and choose some other desktop - sorry, I don't recall which are available immediately after install.

Exactly which version of Ubuntu are you trying to install into the VM?  I'd recommend staying with an LTS release like 12.04. Newer is not always better.

---

