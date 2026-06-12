---
title: "Authenticate Windows Clients on Linux Network"
date: 2013-05-13
forum: Server Platforms
---

### Post by dwpsco on 2013-05-13
Okay am I headed in the wrong direction?
I want to ditch all my Windows servers and replace them with Ubuntu Servers.  I want to have several Ubuntu servers handle all the authentication for my network consisting of Ubuntu and windows clients.  I google “Authenticate Windows Clients on Linux Network” and get allot of information for going the other way (Authenticate Linux Clients on Windows Network) but nothing helpful on how I want to do it.
Yes I’m new to Ubuntu, but love a new challenge.

Can anyone throw me a bone or starting place?

---

### Post by tripp98 on 2013-05-13
Start with samba 4.  

[http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4)

Should be a good start

---

### Post by dwpsco on 2013-05-13
Am I wrong or does samba connect to a domain?  Isn't there a way to skip windows domains completely?

---

### Post by d4m1r on 2013-05-13
Some topics for your consideration.......This is the age old question of, "Can I have a 100% linux back-end but support Windows clients as well?"

[http://www.cyberciti.biz/tips/linux-active-directory-server.html](http://www.cyberciti.biz/tips/linux-active-directory-server.html)

[https://wiki.archlinux.org/index.php/Active_Directory_Integration](https://wiki.archlinux.org/index.php/Active_Directory_Integration)

[http://serverfault.com/questions/13419/what-are-some-good-open-source-alternatives-to-active-directory](http://serverfault.com/questions/13419/what-are-some-good-open-source-alternatives-to-active-directory)

[http://community.spiceworks.com/topic/272530-samba4-a-viable-alternative-to-active-directory](http://community.spiceworks.com/topic/272530-samba4-a-viable-alternative-to-active-directory)

[http://www.infoworld.com/d/networking/samba-4-review-no-substitute-active-directory-yet-211318](http://www.infoworld.com/d/networking/samba-4-review-no-substitute-active-directory-yet-211318)

[http://www.zdnet.com/samba-4-released-brings-free-alternative-to-active-directory-7000008654/](http://www.zdnet.com/samba-4-released-brings-free-alternative-to-active-directory-7000008654/)

---

### Post by dwpsco on 2013-05-13
d4m1r, thanks for the links good reading all, then it led me to "The Ripple Effect of Windows 8&#8221; [http://www.datamation.com/applications/the-ripple-effect-of-windows-8-1.html](http://www.datamation.com/applications/the-ripple-effect-of-windows-8-1.html) which is exactly what and why I have been thinking it&#8217;s time to move on from microsoft.  Hence the conversion.
 
tripp98, looks like you were right Samba 4 is where I need to start the process.
I will do my best to update this thread on my progress.  Looks like a fun time.

---

### Post by tripp98 on 2013-05-15
Glad i could point you in the right direction.  Feel free to ask any questions.  One of many projects right now is to use samba to replace our Active directory.  Havent started yet.

---

