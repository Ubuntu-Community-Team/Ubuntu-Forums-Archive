---
title: "Rootkits - How?"
date: 2006-11-09
forum: Server Platforms
---

### Post by leftcase on 2006-11-09
Hi folks,

I've been having a discussion lately with a colleague about security on Linux and Windows and the differences/occurances between them.

After discussing the fact that to install a virus on Linux requires the virus to be made executable and for the user to run it with root privleges in order for it to cause any serious damage my colleague refered to rootkits.

I know what a rootkit is, but the conversation lead me to wonder how a rootkit is introduced to a system? I wonder if anyone could give me any examples on how rootkits are installed to a linux box?

Thanks

---

### Post by Jussi Kukkonen on 2006-11-09
Three basic routes: trojan, worm and unauthorized login. Trojans rely on a user executing an unknown binary/script, worms get in through a vulnarability in a running service. Unauthorized logins are done with e.g. doing a dictionary attack on a ssh server and getting access that way.

Those approaches do not necessarily ensure root access (which is needed for many rootkit methods), but they cover the initial attack vectors.

---

### Post by leftcase on 2006-11-09
Thanks for clearing that up for me :D

---

### Post by BLTicklemonster on 2006-12-18
Here's a good read

[http://linuxhelp.blogspot.com/2006/12/various-ways-of-detecting-rootkits-in.html](http://linuxhelp.blogspot.com/2006/12/various-ways-of-detecting-rootkits-in.html)

---

