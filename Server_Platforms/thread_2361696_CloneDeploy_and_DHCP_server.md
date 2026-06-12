---
title: "CloneDeploy and DHCP server"
date: 2017-05-19
forum: Server Platforms
---

### Post by dublea on 2017-05-19
Hello to anyone who may be able to point me in the right direction!

I'm trying to setup and configure a server with two network interfaces for a [CloneDeploy]("http://clonedeploy.org/") server.  One network interface will need to be able to obtain autodhcp and connect to our production network only for being able to access the webgui.  The second network interface needs to be able to run DHCP for connection to the tftpd via PXE booting and imaging.  I'm trying to figure out a way to be able to host the site over both interfaces while keeping the DHCP server isolated to a separate network.  Any advice would be appreciated!

---

