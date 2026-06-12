---
title: "[SOLVED] Please explaine"
date: 2008-11-07
forum: Server Platforms
---

### Post by theozzlives on 2008-11-07
I have yet to discover the differance BTW the desktop and server software (besides the lack of a GUI). Am I missing something???

---

### Post by wirelessmonkey on 2008-11-07
> **theozzlives said:**
> I have yet to discover the differance BTW the desktop and server software (besides the lack of a GUI). Am I missing something???

I believe that is the major difference, though PAE memory support for 4GB memory on x86 systems is also enabled on the server distro.
There are several small differences in default applications, and installed modules.

---

### Post by ad_267 on 2008-11-07
I believe the server also has things like Apache, MySQL, OpenSSH and other software installed by default.

---

### Post by Thirtysixway on 2008-11-07
The server kernel is a little different than that of the desktop kernel.  Server doesn't come with ssh/lamp installed by default but does present you with the options during installation.

If you're looking at running a server, don't bother with using desktop version.  You'll be wasting system resources and hd space with the desktop and default applications like openoffice.

---

### Post by windependence on 2008-11-07
Look here:

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

There are MAJOR differences.

-Tim

---

### Post by theozzlives on 2008-11-08
> **windependence said:**
> Look here:

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

There are MAJOR differences.

-Tim

thanks for the info, but I'm running 32bit server for Apache, a 32 bit Desktop as a print server, and a 64 bit laptop. I still keep asking myself Why the server???

---

### Post by blackened on 2008-11-08
Most of the differences are during installation. The desktop version has one main install type (though the details can vary), whereas the server version installs a fairly barebones system onto which you can add.

The benefit of using the server version would be if you wanted to start with a basic system and only install those packages that you specifically need/want. Not to mention that it allows you to add some server-specific packages during installation.

---

### Post by windependence on 2008-11-08
> **theozzlives said:**
> thanks for the info, but I'm running 32bit server for Apache, a 32 bit Desktop as a print server, and a 64 bit laptop. I still keep asking myself Why the server???

The differences are mostly under the hood as the link that I posted describes. A lot of n00bs think the only difference is the lack of GUI or the package selection. The truth is you can do pretty much with the desktop what you can with server, however, server will do it better and with more stability and scalability. We're talking true servers here not just your little file server or torrent server, but real, enterprise applications.

-Tim

---

