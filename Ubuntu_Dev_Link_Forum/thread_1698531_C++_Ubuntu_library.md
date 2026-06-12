---
title: "C++ Ubuntu library"
date: 2011-03-02
forum: Ubuntu Dev Link Forum
---

### Post by nearlymagicman on 2011-03-02
Is there any library like "windows.h" for Ubuntu? If so is there a API as well? 
I want to write a C++ program which automatically recognize when hardware is plugged in, so it can take action (like copying certain files or unmounting it), but to do so I need some functions which give me data like all plugged in hardware.

Thanks for your help

---

### Post by johnl on 2011-03-02
Hi,

For something that you are interested in, you have a couple choices:

1. HAL (Hardware Abstraction Layer) is the older way to do this.  It provides dbus notifications when devices are attached or removed to the system.  If you google for HAL/Dbus you should find some results for this.

2. udev is the newer way; in C/C++ this is provided by libudev.  Check [this page](http://www.signal11.us/oss/udev/) for some great info; at the bottom it shows how to monitor udev events for device added, removed.

There is no "one" header or library for Linux development, unlike windows.  most of the similar functionality is exposed in the POSIX headers (like <sys/stat.h>, <unistd.h>, etc.) or linux-specific or library-specific headers.

---

### Post by stchman on 2011-03-03
> **nearlymagicman said:**
> Is there any library like "windows.h" for Ubuntu? If so is there a API as well? 
I want to write a C++ program which automatically recognize when hardware is plugged in, so it can take action (like copying certain files or unmounting it), but to do so I need some functions which give me data like all plugged in hardware.

Thanks for your help

So you are wanting to develop win32 apps under Ubuntu?  I don't know if Ubuntu has the win32 API in its repositories.

My suggestion is to run Windows in a Virtualbox environment  and install Visual Studio.

---

