---
title: "Installing a wireless card. HELP!"
date: 2010-06-27
forum: Wine
---

### Post by ElRonHubbard on 2010-06-27
SO I bought a Zonet ZEW1605 pci wireless card with a RealTek Chipset and installed it into my dell. I am using wine for the driver software but am runing into issues during installation. I got around the dll file sissues I was having but now it is telling me:
 "storage share mode is not implemented" and this is the beginning of the issues. The installation seems to finish desitethe error messages i am receiving such as:
 "INSTPATH.EXE encountered a serious problem" and my terminal tell me:
 "call from 0x7b836572 to unimplemented function setupapi.dll.SetupQuerySourceListA, aborting"

Why did the card work once and the comuter booted fine and now i can't get it to work at all. 

Any help would be appreciated.

-Lucas

---

### Post by ajgreeny on 2010-06-27
You might do better with ndisgtk for using the windows driver; in fact, I've never heard of using wine for the wireless driver.  Are you certain wine is what you really meant?

---

### Post by cogadh on 2010-06-27
Windows drivers do not and never will work in Wine. Wine utilizes the existing Linux drivers to access the hardware. From the [Wine FAQ]("http://wiki.winehq.org/FAQ"):
> **[SIZE="3"]3.6. Can I use Wine to install drivers for my hardware?[/SIZE]**

No. With the possible future exception of some printer drivers, Wine requires your hardware to already be working on your operating system. The technical reason for this is that Wine, like most applications, runs in user mode and not kernel mode.

---

