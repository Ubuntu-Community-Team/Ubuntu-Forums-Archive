---
title: "Ubuntu Server 7.04 Assistance"
date: 2007-06-16
forum: Server Platforms
---

### Post by Shadow Jolteon on 2007-06-16
I installed Ubuntu server edition earlier, and I am a bit lost with it.. I was expecting more of a GUI, but I think I can learn the commands.. I just need a bit of help with them..

I managed to get Apache, MySQL, and PHP installed, but after that I get a bit lost. I read through the [Ubuntu Server Guide](https://help.ubuntu.com/7.04/server/C/) to figure out that stuff, but the rest is a bit confusing. Basically, I need to know how to set the domain name, the e-mail, and a bit of information as to how I can create HTML files, and somehow get image files onto it.

Also, is there any way that I could import HTML and image files from a CD or USB flash drive?

Thanks!

---

### Post by carcioni on 2007-06-18
There is a utility that is part of the 'yp-tools' package, that can set your domainname for you. The entire package is a bit of overkill if all you need is to register your domainname on startup but it will work.

You may want to look at Xmail for a mail server, assuming this is what you want to do. There are several good places to refer to for setting up a mail server under Ubuntu. Give 'Ubuntu Xmail' a go on you favourite search engine.

Editting HTML from a command line, on the  server can be a bit ugly. I'd recommend using your favourite HTML editor under Gnome or those other guys (Micro something or another) :-) and just deploy them to the htdocs directory under the Apache install.

You should ba able to use a USB drive asuuming the 'hotplug' utility is loaded, which is usually is. The USB drive will show up under your /media directory with a new folder, where your files will be located. Don't forget to suo 'umount /media/<usb folder name>' before removing the device.

All that said, you have a lot of things to learn to get all of these pieces working well and securely together but the process can be very educational and there is usually lots of help here on the forum and elsewhere.

Cheers
D

---

