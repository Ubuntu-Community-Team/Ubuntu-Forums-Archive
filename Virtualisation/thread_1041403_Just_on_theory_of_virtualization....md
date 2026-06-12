---
title: "Just on theory of virtualization..."
date: 2009-01-16
forum: Virtualisation
---

### Post by qhimq on 2009-01-16
It all started when I couldn't get a printer working on ubuntu.  I checked openprinting and it said it was a paperweight.  I started investigating virtual machines not to specifically solve that problem but hopefully to get around to it.

Firstly, if ubuntu is host and I have windows as the guest would the printer be able to function?  My guess is no.  I tried vmware and could not for the life of me get it to work.

Secondly, I looked into a lot of other virtual machines and it raised some questions.  Is it possible (or done already) to create a layer between the host OS and the hardware where the layer would allow the hardware to be compatible with the common operating systems of today?  If this is possible then shouldn't a group of people come together, make standards, and then we would never have to worry about new devices ever being incompatible with the common operating systems with the low level layer installed.

I took a system programming class last semester so I know a bit of terminology.  I am interested in pursuing my understanding of this field.

Thanks.

---

### Post by PilotJLR on 2009-01-16
The hypervisor itself is basically the layer you are talking about, but that's for bare metal products, and it's certainly not industry standardized... it would be nice if it was, but standardization is really hard to pull off in this industry.

Is the printer USB attached? If so, all you need is to attach it to the guest with VMware Workstation or VirtualBox, and then it will work in the windows guest.

---

### Post by HotShotDJ on 2009-01-16
> **qhimq said:**
> Firstly, if ubuntu is host and I have windows as the guest would the printer be able to function?Using VirtualBox, this should work -- you'll at least be able to print to your USB printer from the the guest OS.  It will still be a paperweight in the host OS. See: [http://ubuntuforums.org/showthread.php?t=1015763](http://ubuntuforums.org/showthread.php?t=1015763) on how to install the proper version of VirtualBox and enable USB support.

> **qhimq said:**
> Is it possible (or done already) to create a layer between the host OS and the hardware where the layer would allow the hardware to be compatible with the common operating systems of today? There has been some work on getting Windows drivers to work in Linux using some sort of universal wrapper (similar to what has been done for certain wireless cards using [NDISwrapper]("http://en.wikipedia.org/wiki/NdisWrapper")).  However, there are hardware manufacturers that are downright hostile toward having their hardware supported outside of the Windows environment.  The better solution is for the specifications to be released (either publicly or via a non-disclosure agreement) so that Linux kernel developers can support the hardware directly.  But, again, while some hardware vendors have been cooperative, others have simply refused to participate.  There really is little that the Linux developers can do about the relatively few hardware vendors that are actively obstructing the development of drivers for their hardware.

---

