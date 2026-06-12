---
title: "Windows 2008 IIS Fast CGI PHP or Windows 2008 with Ubuntu guest w/LAMP stack?"
date: 2011-01-18
forum: Virtualisation
---

### Post by Syirrus on 2011-01-18
I have a server that I have co-located in a datacenter. It is a Quad Xeon (5130) with 8GB of RAM.  I have a few usb and serial port devices (peripherals) attached to it which require Windows to run.  

I would like to add web hosting a (production) website onto this server's workload.  The website is runs on a LAMP stack.  After much reading, it seems that hypervisors and VM installs don't seem to work with peripherals (physical serial ports etc). Please correct me if I'm wrong.  I would rather Ubuntu as the HOST and windows as the guest

So I was thinking about running Windows 2008 server x64bit and installing Vbox 4.0 (Ubuntu guest )on it to handle the production LAMP stack.  I was also thinking about running the LAMP stack on IIS 7.0 w/FASTCGI.  Which option do you think is better?  Are there other options that I'm not considering?

Syirrus

---

### Post by mdshann on 2011-01-18
I used to use my minidisc player from sony on my ubuntu machine using a windows XP virtual machine to read the USB port it plugged in to. I had to use the non-free cersion of vitualbox if I remember correctly to get it to see the USB devices as the open source version did not have USB drivers for the client OS. So I guess what I am trying to say is that it is possible with USB but I have no idea if it works the same way with serial although I imagine it would.

---

