---
title: "Server GUI?"
date: 2006-03-21
forum: Server Platforms
---

### Post by kc0rtg on 2006-03-21
I want to set my linux comoputer up as a HTTP and FTP server so some friends and myself can share files and mess around with PHP and MySQL.  I read about VSFTPD and i installed it from the terminal.  My question is, is there a GUI for this or any other free FTP server for linux?  I do not enjoy searching through configuration files in the terminal to set things the way i want.  Also, is there an HTTP server with a GUI in linux?  I downloaded abyss web server and unzipped it.  When i double click the abyssws icon that is supposed to start the server i dont see anything happening.  When that computer still had Windows 98 on it i had Abyss Web Server and zFTPServer Suite.  I really liked the way zFTPServer Suite was configured and Abyss was nice too.  If you have any suggestions or comments i am looking forward to your reply!

---

### Post by localzuk on 2006-03-21
Linux generally does not have 'click to run' applications, instead you have to set up shortcuts that run the necessary commands, or run the command from the terminal.

When running a webserver or ftp server I would say that you must configure it by hand else you will end up with an insecure computer. It is a learning experience and teaches you about the software that you are running.

I do not know of a reason to have a GUI configuration for either of the server application types you mention as this would not really be a bonus to a systems admin.

For now I would recommend installing apache and vsftpd and also webmin (this needs you to select which modules for it you wish to use).

Webmin is a web based gui config tool for linux based software. It is based on being modular so can be configured to work with pretty much anything if you want to.

---

