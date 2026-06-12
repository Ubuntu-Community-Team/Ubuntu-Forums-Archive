---
title: "User Websites"
date: 2006-11-24
forum: Server Platforms
---

### Post by macuserx1 on 2006-11-24
[FONT="Comic Sans MS"]I recently installed Ubuntu LTS on an old Compaq (2.4Ghz, 512 RAM) running headless and have been trying to teach myself how to administer a server through SSH. I have used other Distros in the past (CentOS, OS X, Solaris) so I am not a completely new user. One thing that I cannot seem to grok in Ubuntu is how to let each user have a website. The only directory that has web access seems to be /var/www. So I guess I have two questions:

1:How would I go about setting up apache so that every user can have a personal website at [http://localhost/~username/?](http://localhost/~username/?)

2:How can I set up the FTP server so that each user only has access to their own home folder using vsftpd?

Ultimately I would like to set up this machine as a server to offer free shell accounts/web services to people that would like to learn about linux, and for myself as well.

Thanks in advance![/FONT]

---

### Post by elst on 2006-11-24
1. This functionality is provided by a standard Apache module. You'll need to use a2enmod to enable extra modules.

The apache2-doc package installs the HTML manual for the Apache Web server into /usr/share/doc/, which covers this and other topics, and you can also view this on-line at [http://httpd.apache.org/](http://httpd.apache.org/).

2. vsftpd includes a chroot feature for this. Personally I would only recommend using FTP if necessary - graphical SSH clients exist for Windows, and the WebDAV module for Apache enables file management over HTTP. WebDAV is now fairly mainstream - XP supports it under the name "Web Folders", and I beleive Dreamweaver can use it as an alternative to FTP for remote site management.

---

### Post by macuserx1 on 2006-11-24
Thanks for the information! I just needed to create the directory public_html in the home folder for it to work. As far as webDAV I know nothing of it but will learn soon. Is there any way for me to create the public_html directory automatically when i run adduser? 

You can be sure I'll be back with many more questions in the near future. 

Thanks again.

---

### Post by elst on 2006-11-24
IIRC, any files or directories that you create in /etc/skel/ are automatically copied to new home directories as the accounts are created - /etc/skel/ is the "template" for home directories on the system.

---

### Post by macuserx1 on 2006-11-25
Thanks again, I must say that this forum is MUCH more friendly than any other linux board or irc I've used. Generally the only responses were "RTFM" or "google is you friend". It's nice to have someone answer your questions and not be an elitist dick. :-D

---

### Post by coastdweller on 2006-12-09
> **macuserx1 said:**
> Thanks again, I must say that this forum is MUCH more friendly than any other linux board or irc I've used. Generally the only responses were "RTFM" or "google is you friend". It's nice to have someone answer your questions and not be an elitist dick. :-D

Ubuntu's Espresso stimulates endorphins in your brain, this is why everyone is so "passive" and milky.

Well at least that's my excuse.

---

