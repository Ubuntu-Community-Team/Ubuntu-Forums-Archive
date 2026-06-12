---
title: "Beginner needs help with configuring Ubuntu Server 9.10"
date: 2010-03-10
forum: Server Platforms
---

### Post by woodsytime on 2010-03-10
Hi guys,

I realise this may be a problem with the VirtualBox software I'm using rather than the Ubuntu server, but I figure some people on this forum must have a similar setup to mine so here goes.....

I'm looking to setup a virtual server on my laptop so I can test out Server Side Scripting.

My OS is Windows Vista SP2 and I've installed Ubuntu Server 9.10 (32bit version).

I seem to have got the server running via VirtualBox (vers 3.1.4).

I'm now looking to edit the xml configuration file for my virtual machine (which is called 'webdev_ubuntu'), so I can access it from the host system. 

I've accessed my xml at this location (users/keith/.VirtualBox/Machines/WebDev_Ubuntu/WebDev_Ubuntu.xml.

The tutotial I'm following has told me to add some extra attributes/nodes (whatever they're called in xml??!! - still learning!) to the xml file.  After I do this, this is what happens:

- I save the xml file
- I start up the virtual machine
- open my browser (Firefox 3.5) and type in 'http://localhost:8888/' to connect to the default Apache page.  However, Firefox states its unable to connect.
- I then open up my xml config file again and the extra attributes/nodes I've added have been removed????

This tutorial is the [tutotial]("http://www.sitepoint.com/blogs/2009/10/27/build-your-own-dev-server-with-virtualbox/") I'm following if it helps.  [SIZE=2]I've got to the section headed...
[/SIZE]**[SIZE=2]'Accessing the Virtual Server from the Host System'[/SIZE]**

...where I'm now stuck!  Any help greatly appreciated!

---

### Post by terazen on 2010-03-10
I've never tried the setup you are using, but for windows boxes I've always just used microsoft virtual server or vmware.  Sorry can't help with the guide since I haven't setup anything that way, so free bump if nothing else. :-)

---

