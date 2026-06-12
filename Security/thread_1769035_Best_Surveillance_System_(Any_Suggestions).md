---
title: "Best Surveillance System (Any Suggestions)"
date: 2011-05-27
forum: Security
---

### Post by Seth92 on 2011-05-27
I'm interested in creating a stable surveillance system relatively cheaply. I found an open source program called Zoneminder, which seems fairly nice. I'd like to install it on Ubuntu 10.04, seeing as I'm not a fan of 11.04 and Unity. Unfortunately, I have no idea what DVR internal cards would be compatible with both Linux and Zoneminder, providing 8 channels. If you have any good suggestions concerning software, DVR cards, cameras (and connectors, ie BNC cables?), or any other system related issues, please let me know because this field is completely new to me.

---

### Post by DodgeV83 on 2011-05-27
> **Seth92 said:**
> I'm interested in creating a stable surveillance system relatively cheaply. I found an open source program called Zoneminder, which seems fairly nice. I'd like to install it on Ubuntu 10.04, seeing as I'm not a fan of 11.04 and Unity. Unfortunately, I have no idea what DVR internal cards would be compatible with both Linux and Zoneminder, providing 8 channels. If you have any good suggestions concerning software, DVR cards, cameras (and connectors, ie BNC cables?), or any other system related issues, please let me know because this field is completely new to me.

Not knowing anything about Zoneminder or surveillance, I would still recommend going with 11.04 instead of 10.04.  I've found hardware compatibility to be much better, and it comes with the new kernel that provides better multi-tasking while cpu intensive processes are running.

If you don't like Unity, select "Ubuntu Classic" at the bottom of the screen right before you login.

Good luck!

---

### Post by gordintoronto on 2011-05-27
[http://www.zoneminder.com/wiki/index.php/Hardware_Compatibility_List](http://www.zoneminder.com/wiki/index.php/Hardware_Compatibility_List) 

I've fooled around with zoneminder with just my webcam, and it seems to be pretty cool. It doesn't seem to have any serious competitors.

---

### Post by Seth92 on 2011-05-27
Gordin, I had previously gone through that list and most of the hardware listed there was produced in 2007 and no longer exists and is antiquated with respect to frame rate and capabilities.  

Dodge, Thanks, I will definitely upgrade and use Classic as opposed to Unity.  

Although I was being hopeful with the use of Ubuntu, I may have to end up using windoze and just use the drivers and software that come with the cheapest dvr card (after of course trying it on Ubuntu).

---

### Post by bayvista on 2011-05-29
I would like to try Zoneminder but can't get past first base. I am following the Wiki. Do I need to configure an SELinux Policy? I have a ZM Console running.

I am running Lucid on an HP Pavillion Notebook with a built-in webcam.

Xawtv seems to make my webcam work. I have got my webcam settings using zmu. 

"Service httpd start" says "unrecognised service. I have installed 'mini-http' which says that I need to configure some files first. Where are the instructions for this?

Any help welcome.

---

### Post by HermanAB on 2011-05-29
Howdy,

Ubuntu doesn't use SELinux, so don't worry about that one.

AFAIK, Zoneminder needs Apache.

BTW, there is also a program called 'Motion', which may be simpler.

---

