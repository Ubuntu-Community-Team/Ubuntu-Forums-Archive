---
title: "Printer and Printer Server"
date: 2013-01-30
forum: Server Platforms
---

### Post by chrisguk on 2013-01-30
Hi,

I am running Ubuntu Server 12.04 LTS on a Proliant DL380 G3 server.  

I wanted to create a printer server solution so that the client PCs could make print requests across the LAN. I install CUPS and it installed as desired, I was also able to use the web interface with no problems.

I have an Epson SX230 printer, when I plugged it in I keep receiving the following messages:

```


hub 1-0:1.0: unable to enumerate USB device on port 4

then 

usb 1-4: device descriptor read/64, error -62


```

I have searched for a resolution but the only I can find is to disable ehci_hcd which to me is not a great idea as I have USB attached storage that requires USB 2.

Does anyone have any ideas how to fix this and install the printer?

---

### Post by tgalati4 on 2013-01-31
Does the epson printer work on a laptop with CUPS installed?  Or does it work in Windows using Epson's Windows driver?  That error message happens when a USB port is not working properly.  Either the epson's USB port is having problems or the server's USB port is having issues.  Have you tried other USB ports on the server?  Perhaps put a USB-4port dongle and see if that will communicate with the epson.  It's a strange problem.  Also try a few different cables.

---

