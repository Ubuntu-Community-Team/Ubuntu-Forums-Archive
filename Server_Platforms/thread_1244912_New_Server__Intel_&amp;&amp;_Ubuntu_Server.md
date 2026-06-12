---
title: "New Server | Intel &amp;&amp; Ubuntu Server"
date: 2009-08-20
forum: Server Platforms
---

### Post by antseo on 2009-08-20
Hello, my (nick)name is Ant. I'm new to Ubuntu and to this forum. This is my first post.
 
Over the next 2 weeks I'm having a new server custom built with..
 
Intel motherboard (utilizing built in Intel video card, nothing more)
2 Intel 64 bit Quad core xeon processors.
RAID 1+0 (4 - 1T hot plug SATA drives)
Hardware RAID controller
Dual power supply
1GB ethernet nic+1
8GB of Kingston RAM (system will have up to 32GB capacity)
DVD/RW Disk Drive.
 
This 2U rack server will serve up cfm (coldfusion) and php web pages and will sit in a nicely cooled co-location facility. I will set up webmin on it.
 
The company putting it together is not familiar with Linux. They, for many years now, have pieced together servers and desktops designed for Microsoft software. They infact are an Microsoft OEM provider.
 
The question they have asked me and that I'm asking this community is whether or not there are Ubuntu drivers out there built for Intel motherboard and hardware RAID controller. If so, please advise or send a url to download. Do you need to know the specs of the intel motherboard?
 
How much RAM does Ubuntu utilize? Should I scale it back to 4GB and add more as needed or should I stick with 8GB?
 
Is having 2 Quad core XEON processors overkill? Am I ok with just 1 processor. Yes, Windows would leverage both processors, but Linux? Is 1 Quad core Intel processor sufficient enough?
 
Which version of Ubuntu should I choose? I see the latest server version is 9.04 but I also hear about version 8.x which is supported until 2013. What does that mean really? Which is more stable to act as a web server (which is the sole intent of what I'm doing - hosting web pages in production use)?
 
Would I need a video card beyond the one that comes on the intel motherboard? Again, I'm hosting web pages, not gaming.
 
I've decided to go with Ubuntu because the Microsoft licensing and requirements are too much for me so here I am. Any help is greatly appreciated.

---

### Post by SoftwareExplorer on 2009-08-20
Well, I can tell you it will do just fine utilizing both processors. Linux is run on most of the worlds super computers after all. To use the most of the processors, I would use 64 bit with a server kernel. (which would be default if you use the ubuntu server image)

---

### Post by SoftwareExplorer on 2009-08-20
By the way, welcome to the ubuntu forums. As far as more stable, the 8.04 version is a Long Term Support release which means its more stable, or at least in theory.

---

### Post by antseo on 2009-08-20
Thanks SoftwareExplorer for your replies.  Yes, I'll download the 64 bit, that's a good plan of action.  So it shounds as though I'm well off using both processors.  However, how do I know Ubuntu has drivers that will support the Intel motherboard?
 
Yes, I need a stable OS since I'm using this system to serve up web pages for production use. Which version of Ubuntu do you use and do you like it?
 
One of the main concerns is how well Ubuntu works with Intel chipset.  Do you know?

---

### Post by SoftwareExplorer on 2009-08-20
Think it should do pretty good with it. Intel has made opensource drivers for their wireless chipsets and their graphics chipsets, so they have a pretty good record of supporting Linux. The main thing I don't know about is raid, because I've never set something like that up. You could always ask the company you buy the hardware from if it supports linux.
Edit:As far as what version, I use 9.04, but I'm a desktop user with apache running just to see how hard it is to set up and to mess around with html.

---

### Post by antseo on 2009-08-20
Ok, thanks again SoftwareExplorer.  I found this link to help me out with finding Intel drivers.. 
 
[http://downloadcenter.intel.com/default.aspx?iid=subhdr+downloads](http://downloadcenter.intel.com/default.aspx?iid=subhdr+downloads)

---

