---
title: "How to install ubuntu server without display"
date: 2020-03-05
forum: Server Platforms
---

### Post by liups233 on 2020-03-05
I have an E3 server. But the display port on it doesn't work. I have tried to plug the hard drive to another computer to install, but it won't boot. When I try to install ubuntu on it through netboot. But I can even not get into BIOS settings because I have no display. So I wonder if there's an image that when I flash it into the hard drive on my server, it can finish the installation by itself. If that image doesn't exist, can I install ubuntu through ssh?

---

### Post by CelticWarrior on 2020-03-05
If you can't access the firmware, BIOS or UEFI, to set the boot device, etc. then I'm afraid there's no way unless it is already set to boot from that drive, which is unlikely.

---

### Post by slickymaster on 2020-03-05
Thread moved to **Server Platforms** for a better fit

---

### Post by TheFu on 2020-03-05
If there isn't any GUI connected, you'll need to configure grub that way before boot so it uses only serial output.  Basically, edit the storage on a different system before.
[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

I've only used pre-built images to do this for industrial systems.

---

