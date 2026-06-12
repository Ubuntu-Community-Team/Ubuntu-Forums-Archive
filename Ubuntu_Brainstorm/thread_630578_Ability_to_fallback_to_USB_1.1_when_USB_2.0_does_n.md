---
title: "Ability to fallback to USB 1.1 when USB 2.0 does not work"
date: 2007-12-03
forum: Ubuntu Brainstorm
---

### Post by loa on 2007-12-03
Hello, I have a suggestion that would ease things a bit for some users. The proposal is that if a USB device gets plugged in, and Linux isn't able to initialize it properly at usb 2.0, it should try initializing it with usb 1.1 instead.

The problem for me is that the cabling to my front usb-ports are not so good, and they work only at usb 1.1 speeds. If I plug in lower speed devices, such as my keyboard, it works perfectly from the front ports. But when i connect higher speed devices, such as usb-sticks, or my digital camera, it won't work. It just fails silently. However, if I remove the usb 2.0 support from the kernel (unloading that module, ie sudo rmmod ehci-hcd), and then insert the usb-stick after that, it works, but at only at usb 1.1 speeds of course.

So I think it would be quite nice if Ubuntu could do this:
When a usb device 2.0 device gets connected on a 2.0 capable port (ie one that is connected to a ehci controller), it should of course first try to init it with usb 2.0 (ehci). If that doesn't work, try with usb 1.1 (uhci/ohci), and preferably put up some message that device is not working at full speed. (This is what win xp does.) I think that a lot of users gets confused when their devices just silently fails at some ports of their computer. And if initializing it with uhci/ohci doesn't work either, then pop up some error message then also of course.

I don't know if this is hard to implement, I'm no kernel hacker. If there is anyone here who knows if this is in the works, or just has some other opinion or information about it, I would be grateful.

/Regards

---

### Post by smartboyathome on 2007-12-03
I don't know if it would be hard to impliment, but the fact that it requires superuser privilages could be a little troublesome for some users.

---

### Post by loa on 2007-12-03
Well, I suppose this would have to be implemented at kernel level if it were to work properly. So in that case the user would not require any superuser privileges. He would in fact require no extra privilege over what he needs to use the device in the first place (even if usb 2.0 was working properly). So my case where I did rmmod ehci-hcd was just to test that it works at usb 1.1. The real implementation would not unload that module, as that would probably make existing usb 2.0 devices freak out. It would implement this fallback with the module still loade, but in some elegant way automatically in the kernel. Maybe it could be with udev and some user space daemon involved also, I don't know about how it would be implemented. Or correct me if I'm wrong on how the kernel works in Linux system.

---

