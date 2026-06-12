---
title: "Portable Desktop"
date: 2010-05-23
forum: Virtualisation
---

### Post by mpg33 on 2010-05-23
Any body know of a portable virtualization software that can be run off a usb that would work on either a  linux machine and a windows machine....can it even be done?......i heard of Portable Virtual box but it runs only on windows machines.  OR is my best choice just to get rid of linux at home and install windows?

---

### Post by TheFu on 2010-05-24
I may not understand your question, but it sounds like you have a Windows machine and a Linux machine. You'd like to have 1 desktop that is shared between them.  Wikipedia on Desktop Virtualization [http://en.wikipedia.org/wiki/Desktop_virtualization](http://en.wikipedia.org/wiki/Desktop_virtualization)

Usually when you want complete virtualization, you need to boot into a hypervisor. Since the API provided by Windows and Linux are different, the hypervisors that work on each are different. 

You do have some options.

a) Place the complete OS and desktop onto a flash USB drive. Reboot both physical machines when ever you want to use it. I'd use Linux since it isn't tied to the hardware as closely as Windows is. Windows requires a reinstall if you change the motherboard and Linux almost always does not.

b) Find a cross platform, JAVA, desktop environment and use it. Java is cross platform for 10+ different operating systems. You'll be limited to only the applications that run under that JVM - java applications. I doubt you'll be happy.

c) Find and use a web-based desktop. There are a number of these running "in the cloud" and use a web browser as the interface. You'll be limited to the applications provide by the web-desktop, but those could be enough for you.

d) If you need more space than option "a" provides, use an external USB disk drive or an SSD drive for 16GB to 2TB disks. Sadly, USB performance isn't very good, but it may be good enough for your needs.

e) Use a remote access protocol and simply remote into the machine you want to use. Normally work firewalls will prevent the free solutions, but GotoMyPC.com usually gets around them. If you work at a big company then doing remote access without approval may get you fired.  On Linux, there are a number of remote access methods. VNC, rdesktop, ssh, ssh -X for X/Windows forwarding ... and you can run remote access or VPN software on your home Linux box to allow remote access securely. I can't recommend VNC or RDP without an encrypted tunnel/VPN.

If you stated the specific things you'd like to accomplish, perhaps some more folks here will be able to recommend better solutions?

---

### Post by Perkins on 2010-05-24
Depending on precisely what you're trying to do, it might work to take say a 16GB flash drive and install Puppy Linux (or similar, tiny distro) and the linux version of Virtual Box...  Then you can take your Windows guest with you anywhere and start it up on almost anything...  Is that what you had in mind?

Any virtualization software will pretty well be platform-specific, and will require at least some level of administrative access on the target machine.  The Windows and Linux versions of VirtualBox can each be run from a flash drive with a few adjustments, but only if you have the appropriate permissions.

---

