---
title: "KVM Switch Suddenly Not Detecting Peripherials"
date: 2015-12-06
forum: Virtualisation
---

### Post by arsenic-creed on 2015-12-06
Hello everyone,
I have two computers at the moment (long story short: new computer is going to dual boot but I need a new Windows disk because my previous one is OEM, old computer will be a personal server once I get the new disk but I had to pay for medicine before computer stuff because adulthood) hooked up to one monitor via a cheap KVM switch ([http://www.trendnet.com/support/supportdetail.asp?prod=215_TK-207K](http://www.trendnet.com/support/supportdetail.asp?prod=215_TK-207K)) and a wireless keyboard with a tiny usb receiver and a usb connected mouse connected to it. It's been working fine for a few months now but suddenly the switch isn't detecting my mouse or keyboard on either computer. I tried swapping the keyboard, can't try swapping the mouse because I don't have a spare, but the mouse/keyboard are still working fine because I have them hooked directly to one computer right now so I can post this and it's working perfectly. The button on the switch still works switching between computers but the little light that shows which computer you're on won't stop blinking (not that surprising since it only seems to stop once the computer connects to the keyboard and mouse and it's not now).  I admit, I never had the utility the site links in because it's only available for Windows and Mac and it worked without it. Tried putting the windows ones in too and still won't connect to the peripherals even just on Windows.
I also had a pop up that said a USB utility had malfunctioned just before this but I have a bunch of USB things right now so I wasn't sure what it was and it just popped up again while I was typing this but the mouse and keyboard were still working anyway so I think maybe it's the bluetooth keyboard for my tablet that I have charging anyway.
Uh, I think I've covered all the necessary information?

---

### Post by arsenic-creed on 2015-12-17
I'm going to assume the lack of replies means the general consensus is that my cheap KVM's USB ports have broken or something and it'll just have to be replaced.

---

### Post by MAFoElffen on 2015-12-21
I believe the lack of response might be-- Questions about KVM Switches are usually asked about in the Server support section. The reason for this is that KVM switches are used in a server room to share a monitor, keyboard and mouse between many servers. No matters. Maybe a kindly Moderator will move this to that section to get some exposure. Becvuase just like me who uses a "KVM hypervisor" for visualization, a KVM Switch is hardware, an has nothing to do with visualization (this forum section).

In my server room-- I have 3 KVM Switches in my main server rack, to share my rack mounted console monitor/keyboard/touchpad shared between 14 servers. I don't know how yours let a wireless keyboard or mouse be shared(?) My console is TFT LED Monitor, PS2 Keyboard & Mouse.  One of my Switches is DVI & USB. that one O had hooked into the same console's montior, but to a USB Mouse and Keyboard.

On boot of my servers, if a GUI, then it has to see the hardware monitor when booting, then can be switched from/to. USB us PNP, by bluetooth wireless is touchy and has to be synced... so don't know how that could have been shared reliably to multiple computers, without unplugging and re-plugging in, so that it goes through a PNP cycle to reconnect.... With the physical, it's just still there. 

When I try shared Bluetooth devices between devices--I run into challenges where sometimes I have to reboot that device to get them back. Not always an elegant solution. And not something you want to have to do if you are providing services to users.

Whenever I suspect a problem with a KVM Switch, unplug it and hook it up directly and see if you still have the problem. None of my switches need a "driver". They all come up by keyboard sense codes. When a key-combination comes up, the KVM Switch pops up an appropriate KVM popup menu to switch between ports.

---

