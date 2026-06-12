---
title: "Headless 8.10 server - remote printer browseable, but can't print"
date: 2009-01-09
forum: Server Platforms
---

### Post by 655 on 2009-01-09
I've seen variants of this question posted, and I've tried to cull the information into something that will work for me, but I'm still stuck.

I have a headless 8.10 server box on a local LAN.  It has a Samsung ML-1630N attached to it via usb.  I want to print from other ubuntu-based machines (8.04) to the printer.

After modifying cupsd.conf to make the printer browseable from a remote client, it shows up in the System > Administration > Printing dialog (see attached image).  

However, options for printing a test page, etc., are grayed out, as if I don't have sufficient admin privileges or something.  Similarly, trying to print to the remote printer from a document or web page also shows the ML-1630 as among my list of printers, but the option to print is grayed out.

I assume this is just a question of fixing up the cupsd.conf file on the server.  I read elsewhere that adding the lines Allow all/Allow localhost/Allow @LOCAL to the Location blocks would help, but this seems to have done nothing.  I have indicated for cups to listen on port 631 for two distinct addresses on the network.

As an afterthought, the remote machine was previously running the desktop version of 8.04, and I was able to share printers seamlessly.  Since switching to the server version, it's been a no-go.  NFS sharing etc. works fine.

Also attached is the cupsd.conf -- could anyone point out what I'm missing?

---

### Post by Rocket2DMn on 2009-01-15
Moved to Server Platforms.  Consider this a bump!

---

