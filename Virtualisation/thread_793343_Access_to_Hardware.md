---
title: "Access to Hardware"
date: 2008-05-13
forum: Virtualisation
---

### Post by M4rotku on 2008-05-13
Hello all, 

I am using VirtualBox.
I need for my Windows XP guest to be able to access my webcam and audio input.  I have so far only figured out how to allow it to access a shared folder and my mouse.  The webcam shows up on the virtualbox application window as being a usb connection, but for some reason, it isn't detected by the guest os.  Is there any way to give the guest os full access to all of the hardware?  Or can anyone tell me just how to allow it to access my webcam and audio input?  Is there another virtualization application that manages the devices in an easier fashion?

Any advice about how to get this working would be very much appreciated.

Much thanks,
M4rotku

---

### Post by 00arthuryu on 2008-05-16
You have to enable usb support on virtualbox to use usb hardware.
But you have to install the closed source version of virtualbox first

hope this helps

---

### Post by Sleaka J on 2008-05-17
There's a small trick getting USB working in VirtualBox 1.6.

[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ)

Look under **Linux hosts**

---

### Post by M4rotku on 2008-05-17
Sorry, i wasn't specific enough.  The USB ports are accessible, but the device needs to be unmounted from the host operating system in order for the guest to be able to use it.  I guess I need to know the location of the webcam so that I can unmount it.

Does anyone know how I can unmount my webcam?

---

### Post by M4rotku on 2008-05-19
bump

---

