---
title: "some questions about ubuntu server"
date: 2010-04-17
forum: Server Platforms
---

### Post by lodore on 2010-04-17
Hello,
I have installed ubuntu server installed file/printer services and setup two samba shares.
I think I have edited the samba file correctly for printer sharing but need to setup cups.

I have plugged in my HP2575 printer/scanner to the server using a usb connection.
any easy guides on how to setup cups and samba for print server?

what should I use for backup up the data on the server?

thanks in advance

---

### Post by theozzlives on 2010-04-17
I just have my website copied to an external HD. For the /home, you can make a tarball. The rest is unimportant.

---

### Post by Scunizi on 2010-04-17
As for the print server, at cli try sudo tasksel .... it'll bring up a menu which may have an option to install the print server portion of ubuntu.

---

### Post by lodore on 2010-04-18
> **Scunizi said:**
> As for the print server, at cli try sudo tasksel .... it'll bring up a menu which may have an option to install the print server portion of ubuntu.

Hello Scunizi,
I installed print server when I I installed the server from cd. im just not sure how to set it up.

---

### Post by trundlenut on 2010-04-19
If I recall correctly doesn't CUPS have a web interface that should have been installed?

---

### Post by Scunizi on 2010-04-19
[http://localhost:631](http://localhost:631)

---

### Post by lodore on 2010-04-20
> **Scunizi said:**
> [http://localhost:631](http://localhost:631)
how do I allow access to the cups webinterface from another machine on the lan?
it was a nightmare to navigate using a text browser from the server itself.

---

### Post by Scunizi on 2010-04-20
Access would be through a browser using the IP address and credentials of a valid user on the cups machine.. http://<ip_address>:631

---

