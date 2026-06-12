---
title: "Compiling a webserver"
date: 2008-06-18
forum: Server Platforms
---

### Post by Butcher on 2008-06-18
Hello,

I am looking to put together a complete webserver system to a .iso file that I can burn and then deploy on any machine anywhere, using the following:
- Ubuntu Server Edition
- LAMPP (everything in the [Xampp for Linux](http://www.apachefriends.org/en/xampp-linux.html) package **as well** as the default options in the LAMP package for Ubuntu)
- Webmin
- Security tools etc.

The problem is, I have no idea how you put together the CD. I managed to install Webmin through command line, but how do I go about putting all the packages I want/need into the CD (before burning it) and then get the install screens (the language, keyboard etc) to let me select which packages I want to install?

---

### Post by Butcher on 2008-06-19
Am I perhaps asking in the wrong forum?

---

### Post by NateMan on 2008-06-19
You really need to check out the ubuntu perfect server guide to manually install your lamp server. They have a list of needed packages, just as you install them copy and paste what packages are needed for everything, that way you can burn them onto your cd. Two cds (one for os, one for packages) would probably be best (or a dvd). Once you have that guide down, I'm sure that with a script it could be easily automated for easy deployment. I highly don't recommend any automated installs. Doing it yourself a few times will give you the abilities to write a simple to execute script to do everything for you.

---

### Post by Butcher on 2008-06-19
Yeah, read through some of that guide - great stuff, but, are there any freeware scripts for unpacking the .iso, putting in whatever packages I wanted, make a script for installing it (basic selection like Ubuntu currently has) and then reassemble the .iso for burning? I've never done any scripting other than web related.

Doesn't need to be a automated script, maybe a tutorial or hint to what coding language we are talking about. I really do like the "setup" that the install on the current Ubuntu Server has, where you select language, keyboard, packages to install (very useful to have them available at that stage, if the server will not be connected to the internet, but maybe a LAN intranet).

---

### Post by mbeach on 2008-06-22
haven't tried this out but it might be what you are after:
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

or for a live cd type thing perhaps:
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

I agree through, writing a script to install exactly what you are after post base Ubuntu install would be how I'd approach it (because I've never taken the time to fully attempt the help.ubuntu.com post above).

---

### Post by cariboo on 2008-06-23
Have a look here:

[http://256.com/gray/docs/redhat_boot/](http://256.com/gray/docs/redhat_boot/)

The kickstart script can be modified to do what you want, or you could look here:

[http://linuxmafia.com/faq/Debian/kickstart.html](http://linuxmafia.com/faq/Debian/kickstart.html)

This has a lot of different ways to do what you want.

It looks like a big project.

Jim

---

