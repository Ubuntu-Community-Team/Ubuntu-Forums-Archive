---
title: "[SOLVED] USB issues with VM Ware"
date: 2008-02-15
forum: Virtualisation
---

### Post by malayka on 2008-02-15
Hi,

I have just installed win xp sp2 on a VM Ware workstation on my Ubuntu 7.10 host o/s.

However, I seem to be having trouble picking up my usb devices correctly. Whenever I restart the Vitual workstation I get a message saying.

The issue I have relates to a logitech quickcam sphere MP.

I know the cam works as it works in ubuntu.

 "A USB device that was previously attached to this VM could nit be automatically reconnected. If the device is still available but resides on a different USB port, you will need to reconnect it manually"

Further when I check the device manager on the XP machine it shows logitech quick cam PTZ under Imaging devices.

 Also under VM/Removable Devices\USB Devices it shows logitech Video device.

When I try and launch the cam either with the logitech software or skype, neither can see the cam.

Can anyone tell me why?

Many thanks

Chris

---

### Post by fjgaude on 2008-02-15
I've never had such an issue but it could be that the device is connected to both OSs. Try detaching it from Ubuntu and see if it works in Windows.

---

### Post by malayka on 2008-02-15
Hi fjgaude,

Please can you advise how I would detach the cam from ubuntu?

Still a complete novice with Linux!

regards

Chris

---

### Post by fjgaude on 2008-02-15
Not knowing anything about your setup, what about unpluging, undoing it from the USB plug, the cam before you boot into the host, then after you are in vmware plug it back in.

Let us know if that works.

---

### Post by dgoodwin on 2008-02-15
This thread has the solution

[http://ubuntuforums.org/showthread.php?t=626062](http://ubuntuforums.org/showthread.php?t=626062)

---

### Post by malayka on 2008-02-17
Thanks v much for yr help.

Adding 'usbfs /proc/bus/usb usbfs auto 0 0' to the fstab file sorted the problem.

Thanks again.

Chris

---

