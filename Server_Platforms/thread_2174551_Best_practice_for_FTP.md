---
title: "Best practice for FTP"
date: 2013-09-15
forum: Server Platforms
---

### Post by PiVoKoZeL on 2013-09-15
Hi.
I have few questions about setting and using FTP server.
At first, I want to know what is the best solution for FTP server with about hundreds or thousands users. Is best choice to create system accounts and restrict it only to FTP or create virtual accounts or to use SQL database?
At second, How to manage access to folders? Example - I have user "A" , "B" and "C". Both "A" and "B" wants to see their own folder but also want to see folder of user "C". User "C" wants to see only his own folder. What is the best practice to configure it? Use ACL or mount folder from one user to another or something else?

And last question. Is it possible to configure upload, download or space quota limit per user on VSFTPD?

Thanks for your help.
Kumar

---

### Post by nerdtron on 2013-09-15
Wow that is a lot of work. And how to do the users access the ftp server? via filezilla, terminal only or webpage?
You might want to look on setting up owncloud. If you are familiar with dropbox and its shared folders, you'll see similar features.
[http://linuxg.net/how-to-install-owncloud-5-on-ubuntu-13-04-and-linux-mint-14/](http://linuxg.net/how-to-install-owncloud-5-on-ubuntu-13-04-and-linux-mint-14/)

---

