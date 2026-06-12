---
title: "Old laptop for wireless print server"
date: 2009-09-10
forum: The Cafe
---

### Post by pookiebear on 2009-09-10
I have an old laptop that I want to setup as a print server. It has xubuntu on it but I can install anything really. 
What is the fastest way to set it up as a print server (non GUI linux options?). I would like the hard drive to be accessed as close to never as possible. It has to run the cisco aironet 350 wireless card. 

This was my old linux test platform and it works  pretty decent with xubuntu on it. but I want low power consumption too. So a terminal only load that will be easy to setup would be nice.
Like a memory resident power save mode that will run the wireless for IP connectivity and be a print server to an old laser printer I have.(lpt only) 

Thanks for any suggestions!

-Chris

---

### Post by marshmallow1304 on 2009-09-10
How about [Ubuntu Server Edition]("http://www.ubuntu.com/getubuntu/download-server") (with the help of the [Ubuntu Server Guide]("https://help.ubuntu.com/9.04/serverguide/C/index.html")) with a [CUPS server]("https://help.ubuntu.com/9.04/serverguide/C/cups.html")?

I've also had good experiences using the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") and building the server from the ground up.


Edit: I don't know how you'll fare with the wireless card.  For ease of setup and reliability, I'd recommended using a wired connection if possible.

---

### Post by tgalati4 on 2009-09-10
As for the hard drive use, that's a tough one.  Running the server edition means creating log files.  (What else is a Linux Administrator supposed to do?)

Also, no suspend/resume in the server install.  Laptop BIOS likes to put things to sleep automatically, so you may have some issues there as well.  

In short, it's probably better to use an old desktop with a server install than a laptop.  If you get it to work, great, but if you have problems, then they will be tougher to solve because you are running a server on hardware that wasn't really designed for server use.

---

### Post by pookiebear on 2009-09-11
Well it is working as a xubuntu install with Samba now.

The XP workstations and the mac workstation print to it just fine. 
I was hoping there was a non-samba version that was command line only that I could boot from a CD/usb that would be a boot, edit the text file config, and start the service. Guess I will make my own-ish, I thought there would be a distro that would have it built in.  but xubuntu is fine. I used the old laptop cause it had the wireless built in which is a requirement.  I close the lid and it cuts the screen off which keeps the power low. So I am ok for now. Thanks again!

---

