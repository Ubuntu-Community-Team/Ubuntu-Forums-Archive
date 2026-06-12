---
title: "[ubuntu_server] [10.04.2] Out of Range"
date: 2014-02-18
forum: Server Platforms
---

### Post by Wej on 2014-02-18
Hello,

I recently moved a server from an old rack to a new one. It was running headless prior to the move. It has no GUI, just a textmode console. Upon booting in its new home, it wouldn't respond after booting. I tried connecting an LCD and keyboard (rackmount KVM) to the system to troubleshoot, but it is giving me an out of range message on the LCD. The strange thing is that it seems to be booting fine. I can watch the console as it enumerates all 21 disks, does all the kernel stuff, mdadm assembles the array, etc. As soon as it's complete and it does the screen refresh where it would normally dump me to a login prompt, I instead get an out of range message on my monitor. I temporarily borrowed a monitor that could support a higher resolution and refresh rate and hooked it up before rebooting, which allowed me to see it was doing an fsck and not yet fully booted. After cancelling and disabling fsck, I can remote into the system, but locally when connected to the rack-mount LCD, I can't actually see what's displaying on the screen.

I've spent the last 4 hours trying different combinations of GFX settings in grub, but it doesn't seem like it's a grub issue. It takes quite a while to enumerate and assemble a 40TB array on every boot. I am able to watch the entire system boot until the last second before I get to a login prompt.
So far I've tried:
```

edit /etc/default/grub
uncomment GRUB_TERMINAL=console
set GRUB_GFXMODE=1024x768 (KVM does this fine on other linux systems in the same rack, also tried 800x600 and 640x480)
set GRUB_GFXPAYLOAD_LINUX=1024x768
ran update-grub
rebooted

```

Am I missing something obvious? Is there some console setting that is different than what grub passes into the kernel at boot time? I'm about ready to punch a kitten I'm so frustrated.

Thanks

---

### Post by TheFu on 2014-02-18
Consider connecting a serial console?
Tried switching the console using ALT-F2 or ALT-F3 ....?  

I've never seen a pure text console go out of bounds for any monitor.
Is there even a video card inside the server?

---

### Post by tgalati4 on 2014-02-18
Definitely check the inside of the server to make sure the VGA connector has something connected to it.  And let's leave the kitties alone.

---

### Post by Wej on 2014-02-18
There is a video card. It's an nVidia MX 400 PCI card. It works fine if I boot from any other media, so it's not a hardware failure. It only happens when it loads the OS installed on its local disk. I haven't tried a serial console, it's not server class hardware, so there is no hardware serial port on the board, I'd have to bring it out from a header, and it's not worth the trouble. It's definitely a software setting, I just don't know where or what I screwed up. This server has been in production for 3-4 years now, I just never had a need to physically access it, SSH was sufficient.

---

### Post by CharlesA on 2014-02-18
I think the console switches over to the video driver instead of "normal VGA" after it refreshes the screen and adjusts the resolution based on what the monitor and card supports.

No idea what driver it is using or how to prevent that other than blacklisting tho.

---

