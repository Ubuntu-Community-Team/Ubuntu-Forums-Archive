---
title: "No ncftp?"
date: 2006-08-04
forum: Server Platforms
---

### Post by JSchwage on 2006-08-04
I've been going through a tutorial on how to set up a web server and whatnot over at howtoforge.com. I've just had one problem so far. It seems the ncftp package is missing from the repository. Whenever I try installing it I get an error which says it can't find the package ncftp.

Any help is greatly appreciated!

---

### Post by croak77 on 2006-08-04
It's in universe. Double check your /etc/apt/sources.list.

---

### Post by JSchwage on 2006-08-04
Ah, thanks. I actually uncommented the universe repository but forgot to do an apt-get update. I'm having a problem with Apache2 also though. Since I entered jared-server as the domain name for the computer Apache goes all wild on me and says it's setting the ServerName as 192.168.2.89 instead, which is the address of the machine.

---

