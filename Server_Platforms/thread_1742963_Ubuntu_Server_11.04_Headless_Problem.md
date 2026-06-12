---
title: "Ubuntu Server 11.04 Headless Problem"
date: 2011-04-29
forum: Server Platforms
---

### Post by schallb on 2011-04-29
Hello everybody,

I'm new to ubuntu and i wanted to setup a headless server
(Asus Hummingbird, 2GB RAM, Ubuntu Server 11.04)

The installation was sucessful BUT:

After i tried starting my server without any connected monitor, the server did not start -> i run into a kernel panic (if i connect the monitor after a while i can see the messages on the screen, Keyboard lights flash...)
What do i have to do to get the machine running without any monitor?

My second problem is, that the Network is allways powered down on system power down -> no WOL is possible. Is there an easy way of enabling the WOL function?
I tried serveral things from different tutorials but nothing worked...

Thanks a lot and have a nice day!

---

### Post by stlsaint on 2011-04-29
> **schallb said:**
> Hello everybody,

I'm new to ubuntu and i wanted to setup a headless server
(Asus Hummingbird, 2GB RAM, Ubuntu Server 11.04)

The installation was sucessful BUT:

After i tried starting my server without any connected monitor, the server did not start -> i run into a kernel panic (if i connect the monitor after a while i can see the messages on the screen, Keyboard lights flash...)
What do i have to do to get the machine running without any monitor?

My second problem is, that the Network is allways powered down on system power down -> no WOL is possible. Is there an easy way of enabling the WOL function?
I tried serveral things from different tutorials but nothing worked...

Thanks a lot and have a nice day!

1st Question: Im probably wrong but you may need to kill xorg-server from starting.

2nd Question: WOL has nothing to do with operating system. It is a hardware issue with your MOBO and NIC. Maybe this can help a bit: [http://linuxappfinder.com/package/wakeonlan](http://linuxappfinder.com/package/wakeonlan)

---

### Post by schallb on 2011-04-29
there is a xorg server @ the server installation?

---

### Post by bobmct on 2011-04-29
It sounds like you either didn't install the server version or you selected to install the GUI desktop feature(s).

You must have used a monitor and kbd to do the install so you may have to do it again.

I've been running multiple small Ubuntu servers for quite a number of years now.  All headless.  But I DO have a KVM to access all of them but they are all character consoles.

But, when you do get things installed so you can gain console access I'd recommend you install webmin as it makes a wonderful, although generic, systems management tool.  Using it you will be able to access your system from any other suitably networked computer with a browser.  You will have full configuration ability and the best thing is you do not have to learn any of the various sub-system configuration techniques or methods.  It all looks the same in webmin.

Back to the basic installation process,  somewhere during the install you will be offered the opportunity to select what features you want/don't want which will tailor the initial install.  You will also be able to define your network parameters during that time and when complete and rebooted download and install webmin.

Good luck.

---

