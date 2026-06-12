---
title: "Headless server ?"
date: 2006-09-08
forum: Server Platforms
---

### Post by McHenry on 2006-09-08
We are looking at converting a headless server to Ubuntu Server Edition and being new to Linux I would like to know what options are available for performing server admin tasks from a client machine.

I am familiar with using Putty from an XP box to access a Linux box however the command line does wear thin after a while, are there any easier options ?

What do most people do ?

Thanks in advance...

---

### Post by jimm on 2006-09-08
Hi,

Have a look at WebMin ([www.webmin.com)](www.webmin.com)). Its a favourite of a lot of people, myself included and it runs fine on Ubuntu.

Webmin is good because it is very compatible. Not just with the OS but also with all the server components you are likely to run. i.e. mail, web, DNS etc.

I like it because it doesnt mess up your config files at all like some other web based admin tools I have seen.

Hope that helps!

Thanks,
James

---

### Post by chrisfay on 2006-09-08
I second Webmin....It's a great tool with a nice layout. The only thing is you need to be fairly familiar with the config files for new software as Webmin will occaisionally attempt to administer the software using outdated file locations. 

Ex. The latest Webmin install will administer Apache based on Apache1 configuration locations. You have to manually change Webmin to use the new location of Apache2 folders/files.

---

### Post by fnjordy on 2006-09-09
You can login to Ubuntu remotely through X11 or VNC.

[https://help.ubuntu.com/community/HowToCygwinX](https://help.ubuntu.com/community/HowToCygwinX)
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

