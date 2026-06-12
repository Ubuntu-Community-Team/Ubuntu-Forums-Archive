---
title: "Server Unpingable Randomly"
date: 2009-06-17
forum: Server Platforms
---

### Post by dustovich on 2009-06-17
Hello, 
I am having an issue with my Ubuntu Server 8.10. It is a headless/keyboardless/mouseless system that runs:mt-daapd, mediatomb, apache2, rtorrent, samba, icecast, etc. It works fine most of the time, but once in a while (every day or two) it will disconnect from network or sleep? no ping/no nothing, but all I have to do is press the power button (since no keyboard/mouse, only form of input) once for it to reappear on the network and start working within about 10 seconds or less. The system is not rebooting or doing anything other then pretty well just waking up, there is nothing in the dmesg output out of the ordinary.  I have looked around the internet and have not been able to find anything about this odd problem. Just wondering if anybody has any ideas or needs more information.
Thanks
Dustovich

---

### Post by ghen on 2009-06-18
Check the BIOS for any power settings. I don't know if linux has output for sleep modes, but no messages in the OS leads me to believe its one level lower.

---

