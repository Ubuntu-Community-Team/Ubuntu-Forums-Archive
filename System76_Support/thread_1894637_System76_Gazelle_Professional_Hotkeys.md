---
title: "System76 Gazelle Professional Hotkeys"
date: 2011-12-13
forum: System76 Support
---

### Post by dodo3773 on 2011-12-13
I am under the impression that system76 uses special drivers for hotkeys and special keys on the laptop. I am also under the impression that these drivers are setup for Ubuntu as Ubuntu is the only officially supported distro. My question is: 

Is there any way to get these drivers in another distro? I like everything I have heard and seen about system76 and I will be using them. But, I would like to be able to configure my laptop for Arch or Gentoo or any other distro. So, are these drivers available somewhere to download? Is there a generic run package available anywhere? Or even a tarball I can get?

On that same note: Are the drivers open source?

---

### Post by isantop on 2011-12-13
No, the drivers are only distributed as a .deb package, and will only run on Ubuntu. The drivers are open source, and written in python.

As a note, as of Ubuntu 11.10, no additional drivers are required for the Gazelle. Everything works and is provided by Ubuntu.

---

### Post by dodo3773 on 2011-12-13
> **isantop said:**
> No, the drivers are only distributed as a .deb package, and will only run on Ubuntu. The drivers are open source, and written in python.

As a note, as of Ubuntu 11.10, no additional drivers are required for the Gazelle. Everything works and is provided by Ubuntu.

So, is this the latest driver / package for all systems? 

[http://planet76.com/repositories/system76-driver-2.7.1.deb](http://planet76.com/repositories/system76-driver-2.7.1.deb)

---

### Post by isantop on 2011-12-13
Yep, that's the latest one. It will work on any of our computers and any supported version of Ubuntu (for a given computer).

---

### Post by dodo3773 on 2011-12-14
> **isantop said:**
> Yep, that's the latest one. It will work on any of our computers and any supported version of Ubuntu (for a given computer).

O.K. Got it thanks. Marking thread as solved. I did have one more question though:

From what I have seen in the driver package the only things that I can think of that may need to be done is the xmodmap stuff and maybe the ricoh card reader stuff (not sure on that one with an up-to-date kernel though). 

So all I would really need to focus on is making sure that the media keys are mapped correctly based on the config files in the driver package right (panv3_xmodmap.conf)?

---

### Post by isantop on 2011-12-14
I think I talked to you on the phone. 

The driver functions for each device are controlled through a central control program, driverscontrol.py. This program is essentially all of the fixes required for each system for each supported version of Ubuntu per system.

---

### Post by dodo3773 on 2011-12-14
> **isantop said:**
> I think I talked to you on the phone. 

The driver functions for each device are controlled through a central control program, driverscontrol.py. This program is essentially all of the fixes required for each system for each supported version of Ubuntu per system.

I did talk to you. Thanks for the response. I am looking forward to doing business with you guys isantop. Take care.

---

