---
title: "LTSP VMware Installation ?"
date: 2006-01-19
forum: Server Platforms
---

### Post by andymelton on 2006-01-19
I have Ubuntu 5.10 installed on a virtual machine, using VMware (on Windows). I am trying to set up LTSP. I know this is not a viable option for day to day usage, however I would really like to learn how to do it and VMware is my only option at the moment..anyways...

I have followed a couple of tutorials on how to install LTSP and even used the guide at LTSP. I don't have any issues installing LTSP. The main problem that I am having is with the DHCP server...I think.

When I get to the point in the installations where DHCP is stopping & restarting, it says "FAIL" on each of them.

I added a virtual NIC to the virtual machine. Configured it to be on another virtual network. 

I can currently use the Linux Terminal Server Client and login to the virtual server. On the virtual machine window I can tell that traffic is going to and from the second NIC that I added.

I set up another virtual machine to boot into the virtual machine using the network boot option. Once the machine is powered on, it begins looking for a DHCP server, then, it appears to start loading...but it never brings me to a graphical login. 

SO, I don't know if its the DHCP server, or what. Any help would be GREATLY appreciated. I am trying to learn this so I can have something to add to my resume and something I can make a video about for my website.

---

