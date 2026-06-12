---
title: "Asus ProArt P16"
date: 2024-10-15
forum: Ubuntu, Linux and OS Chat
---

### Post by paulycalvin on 2024-10-15
Well I just bought this computer and I thought I would share my experience. I would be happy to answer any questions. I looked around quite a bit before I installed Ubuntu and there wasn't a lot of information. I think the most important thing is that Ubuntu 24.10 with the latest kernel 6.11 or later is what you must have with this computer. So this computer would have been a real headache last month but is working really great at the moment. Let me post the specs.

# System Details Report
---

## Report details
- **Date generated:**                              2024-10-15 17:47:53

## Hardware Information:
- **Hardware Model:**                              ASUSTeK COMPUTER INC. ProArt P16 H7606WV_H7606WV
- **Memory:**                                      32.0 GiB
- **Processor:**                                   AMD Ryzen&#8482; AI 9 HX 370 w/ Radeon&#8482; 890M × 24
- **Graphics:**                                    NVIDIA GeForce RTX&#8482; 4060 Laptop GPU
- **Graphics 1:**                                  NVIDIA GeForce RTX&#8482; 4060 Laptop GPU
- **Disk Capacity:**                               (null)

## Software Information:
- **Firmware Version:**                            H7606WV.308
- **OS Name:**                                     Ubuntu 24.10
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               47
- **Windowing System:**                            X11
- **Kernel Version:**                              Linux 6.11.0-8-generic

The install kind of sucked because it kept hanging at select your keyboard. I googled it and I read that it had something to do with networking so I went into the UEFI/Bios settings and I turned off networking and began the install again. Then it hung up at time zone selection but this could have been not realizing that you have to press inside the time zone drop down. I think I was expecting it to auto populate as the old installer used to do. It may not have found the time zone as networking was turned off. I waited so long I got a message about NVIDIA graphics timeout so I retried again in safe graphics mode. Then the install completed. After that I had to reboot and go back into the bios to turn networking back on. So the install works but has a few hang ups.

But this computer is working great now. Let me now if you have any questions.

"working great" apply's to me and what works for me. there are a few more issues but it's something I am okay with until newer kernels arrive in the future and some of these items get fixed. I will add a list here below.

The backlight pulsates but is working.
Volume level cannot be controlled. If you adjust the slider you get sound at one level or you can slide it off. I don't think the tweeters are working so it's only the sub woofers. Sounds fine but taking advantage of the speakers not really at this point.
Bluetooth is not working.
Wayland works but is buggy so i would recommend selecting Xorg session before logging in.
I will come back and edit if I find anything else.

You can follow along at the following link for progress of issues and fixes.

[https://gitlab.com/asus-linux/asusctl/-/issues/555](https://gitlab.com/asus-linux/asusctl/-/issues/555)

---

### Post by sigxcpu on 2024-10-16
I've had a similar model (H7606WI, BIOS 307) 2 weeks ago and it was bad:
- I don't want to use NVIDIA as a display driver, just keep it headless. Didn't work. There is simply no video output on internal monitor if NVIDIA is disabled. AMDGPU boots just fine, but it requires an external monitor that will also trigger output on internal. Then it works until the next reboot. Maybe some video mux stuff that needs to be sorted out.

How does the suspend/resume work for you? To my amazement, the laptop goes to sleep but after some time (tens of minutes, hours, I don't know) it resumes. Found it with 10% battery, don't know when and why it resumed because it was stuck.
I've also used the latest linux-firmware and kernel 6.12-rc2 at the moment, but still no go.

This machine is the next best thing I've touched after a Mac in terms of feeling and build quality.

---

### Post by paulycalvin on 2024-10-18
Sorry i didn't see you reply.

I turned off suspend because the screen went black after the system tried to resume. 

Definitely the 4K display is the best I have ever seen with Ubuntu and I love this build quality.

Bleutooth isn't working and volume control is either muted or max. You can't set the volume level but I have been reading that Kernel 6.12 will solve these issues. So that shouldn't be long. I also read that the open driver for Nvidia is better than proprietary so I set that with the additional drivers and that does seem better. I am not using Wayland for nwo.

---

### Post by paulycalvin on 2024-10-18
I created and gnome shell theme that I really love with this computer.

[https://www.opendesktop.org/s/Gnome/p/2216288](https://www.opendesktop.org/s/Gnome/p/2216288)

---

### Post by stonetoken on 2024-10-22
Hello! Do your media keys work? (brightness +-, volume +-, etc.)
Have you been able to control keyboard backlight? (for me it does pulsate constantly due to active OOBE mode)

---

### Post by paulycalvin on 2024-10-24
No the media keys don't work. I can control the screen brightness from the quick settings menu. Volume level can't be set either. It's only on or off because only the sub woofers are putting out volume and bluetooth doesn't work either. it's a fairly new computer so i expect most of this stuff will get fixed in later kernel versions.

---

### Post by paulycalvin on 2024-10-24
What is OOBE mode?

Oh I guess you are saying the keyboard backlight is pulsating. Yeah mine is doing that as well but it hasn't been bothering me.

---

