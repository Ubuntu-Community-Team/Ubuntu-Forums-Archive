---
title: "WhyLinuxCommunity is not making DEB files to easeHardwareInstallation?(scanner,webcam"
date: 2006-03-26
forum: The Cafe
---

### Post by patrick295767 on 2006-03-26
WhyLinuxCommunity is not making DEB files to easeHardwareInstallation?(scanner,webcam, usb microphones, ... other usb devices ... modem ) 
    
a single : dpkg -i 
would significantly ease linux users.
 
in order to ease the life of users and make them adopting Linux 

'cos pinguins are too difficult for most users coming from easy going Windows OS...
  
Greetz

---

### Post by endersshadow on 2006-03-26
[QUOTE=patrick295767]WhyLinuxCommunity is not making DEB files to easeHardwareInstallation?(scanner,webcam, usb microphones, ... other usb devices ... modem ) 
    
a single : dpkg -i 
would significantly ease linux users.
 
in order to ease the life of users and make them adopting Linux 

'cos pinguins are too difficult for most users coming from easy going Windows OS...
  
Greetz[/QUOTE]

Many drivers (especially in Ubuntu) already have .deb files...I suppose I'm very confused as to what your question is :-|

---

### Post by bernardfrancois on 2006-03-26
[QUOTE=endersshadow]Many drivers (especially in Ubuntu) already have .deb files...I suppose I'm very confused as to what your question is :-|[/QUOTE]

Drivers are mostly built-in in the Linux kernel. Some are not, those can be loaded with the **modprobe** command.

.deb packages are files that contain programs which are already compiled. Some of those programs can function as a driver to support some of your hardware. Mostly they won't just make your hardware work after installing the program (using dpkg -i ...), you will often need to do some more configuration.

The most user-friendly way to have your hardware working is when it's detected automatically I guess. The second way is when the manufacturer of your hardware gives you a cd with an installer to install your hardware (unfortunately, this is rarely the case). A third way is to load the proper module (if available, you'll need to find out which one you need to load). And a fourth way is by installing some program that gives support for your hardware (which may come in a .deb package).

Note that rather than installing .deb pacakges, you should use synaptic if possible.

To make a scanner work, you have to use 'sane'. This is installed with ubuntu by default.
To make your webcam work, you also already have a driver for that as well. You can read more [here](http://ubuntuforums.org/showthread.php?t=119596) about it.

Mostly the [wiki](http://www.wiki.ubuntu.com) is a good starting point for troubleshooting on hardware (use the search option).

---

