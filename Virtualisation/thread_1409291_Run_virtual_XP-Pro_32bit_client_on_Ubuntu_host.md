---
title: "Run virtual XP-Pro 32bit client on Ubuntu host"
date: 2010-02-17
forum: Virtualisation
---

### Post by allbread on 2010-02-17
Can an XP-Pro 32-bit client be run virtually on an Ubuntu X86-64bit host? 

I have a machine that I've been slowly collecting parts for; the majority of which have been leftovers from other disassembled workstations and/or hardware clearance sales. The specs of the box, if it's ever completed (still need drives) will admittedly be overkill from a hardware perspective (8 core 32GB DDR2 with a GeForce 260 GTX G-card... and these are the parts I already have). I strongly prefer to run Linux as opposed to (what would likely be a much simpler install of) Windows7 for security purposes; it is my desire to install 10.04 once it is released this coming year and the box will primarily serve as a central file repository / media center for my family. My goal on the media side is to run a virtual XP client primarily for streaming Netflix movies over IE and possibly installing the Pandora client. 

As I understand it, XP is prefeable over Windows7 as the former is less system intensive... or does this not matter when running a virtual client?

If this can be done, what are my options for virtualization software... and which, if any, is best suited for my purposes?

---

### Post by pirateghost on 2010-02-17
in answer to your question, yes any 32bit OS can be virtualized in a 64bit host.

my recommendation would be VirtualBox for your needs.


doesnt boxee support netflix now?

---

### Post by Objekt on 2010-02-18
Yes, you can.  I use a Windows XP 32-bit virtual machine, running in Virtualbox 3.1.4 PUEL on my Ubuntu 9.10 64-bit host machine, to do stuff all the time.  I have not tried Netflix streaming video, but streaming audio from radio station websites works fine.  

DVD playback works also on the virtual Win XP.  

Windows XP vs. 7 is a close race in resource requirements.  I once ran Windows 7 RC on a netbook that also had Windows XP, and my desktop machine (which runs Ubuntu 9.10) also has both Windows XP and Windows 7 RC installed.  7 and XP seem to perform about the same on the same hardware.  Such is also true for virtual machines.

There are some improvements in Windows 7 - programs allowed to crash without locking up the system, somewhat better security through UAC, etc. - that make it better than XP.  However, I doubt it matters much for a virtual machine, if you're only using it to watch Netflix streaming video.

---

### Post by allbread on 2010-02-18
[http://tech.slashdot.org/story/10/02/18/0429258/86-of-Windows-7-PCs-Maxing-Out-Memory](http://tech.slashdot.org/story/10/02/18/0429258/86-of-Windows-7-PCs-Maxing-Out-Memory)

Is there any kind of DirectX support when using a virtual Windows XP or 7 client under VirtualBox?

---

### Post by jpl888 on 2010-02-18
Yes but it is experimental so YMMV.

I also don't think it supports Windows 7.

---

### Post by allbread on 2010-02-19
[http://www.vmware.com/support/ws65/doc/releasenotes_ws65.html](http://www.vmware.com/support/ws65/doc/releasenotes_ws65.html)

According to this, as of v6.5, VMWare Workstation supports DirectX9 - however their latest releast v7.01 doesn't make any mention of extending this to DirectX10.

How does VMware support of DirectX compare against that of VirtualBox?

---

### Post by jpl888 on 2010-02-19
I only used the Directx support once on a Windows XP virtual machine in VirtualBox. It appeared to work ok but I don't really play games so didn't test it fully.

---

