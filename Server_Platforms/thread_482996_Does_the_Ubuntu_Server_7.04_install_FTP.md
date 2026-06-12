---
title: "Does the Ubuntu Server 7.04 install FTP?"
date: 2007-06-24
forum: Server Platforms
---

### Post by petersfreeman on 2007-06-24
I recently installed Ubuntu Server 7.04 Feisty Fawn using the ISO image on a CD and I chose the LAMP option.  I want to now FTP files to the server from my laptop.  I have these questions:

* Is FTP already running on the server?
* If not, what FTP application should I install?
* Where do I get it?
* Can you point me to a tutorial that will show me how me to set up FTP user accounts?
* Where do I find this tutorial?

Thank you,

Peter Freeman

---

### Post by Wardazo on 2007-06-24
Hi

I'm pretty certain an ftp server isn't installed by default.

vsftpd is an excellent ftp server. A good tutorial can be found at:

[http://ubuntuforums.org/archive/index.php/t-91887.html](http://ubuntuforums.org/archive/index.php/t-91887.html)

However, if only **you ** are going to be transfering files, then sftp is more secure and comes with the ssh server.

sudo apt-get install ssh

All modern ftp clients handle sftp. Only use this option if it is **you **who will be using it (unless you understand all the implications)... it is a very powerful option, and can very dangerous if you let other people use it without setting it up with this in mind.  See:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server)

---

### Post by nix4me on 2007-06-24
i would recommend you not use vsftpd.  It is not a full featured ftp server.

I would recommend using sftp over ssh for sporatic use.

I would recommend proftpd for a high use ftp server.

nix4me

---

