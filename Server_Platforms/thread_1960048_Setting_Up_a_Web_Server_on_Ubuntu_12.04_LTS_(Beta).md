---
title: "Setting Up a Web Server on Ubuntu 12.04 LTS (Beta)"
date: 2012-04-16
forum: Server Platforms
---

### Post by jonedney on 2012-04-16
Hello Everyone,

So I attempted to install ISPConfig 3 on an Ubuntu 10.04 LTS VPS and ISPConfig just didn't want to play nice, so since the only sites on this VPS will be mine, I'd like to get some recommendations on some good tutorials on setting up an Ubuntu server for my VPS.  Below are some specifics on what I will be doing on this server:

*Basic server hosting multiple domain names (Currently, 3)
*Apache, PHP, MySQL is a must.
*Email server, as I will be using this VPS for everything.

Just looking for some recommendations.

Thank you,
Jon Edney

---

### Post by d4m1r on 2012-04-16
1) I'd recommend against using the 12.04, unless your VPS is just a test bed. If it is a production server running important stuff, consider using 11.04 or 11.10 instead.

2) These should get you started: 

[https://help.ubuntu.com/](https://help.ubuntu.com/) > Version > Server (guides on Apache, MySQL, PHP, Email, etc)

and more VPS specific/technical:
[_entomy.com/VPS-Server-Configuration-Guide.pdf_]("http://ubuntuforums.org/entomy.com/VPS-Server-Configuration-Guide.pdf")

---

### Post by jonedney on 2012-04-17
Hello!

Thank you for your recommendations.  I'm going to try them out starting today.

Thank you,
Jon Edney

---

### Post by jonedney on 2012-04-17
Hello,

Just figured I'd add some information here for those who may be new like myself, and looking around the forums.

I was able to get Apache, PHP, MySQL and phpMyAdmin installed and running without problem in my VPS.  I opted to install everything by hand and not use a "control panel" environment to manage the sites, and used the Virtual Hosts option within Apache.

I did not install an FTP server, since I will be using SFTP with my root access (it's just my sites on the server, so no biggie here).

I ran into some hiccups with installing and configuring the mail server and I'm sure it's to do with the amount of work I've done on the server already today, so I was getting frustrated.  

Additionally, I used 10.04 LTS as the OS.  I'm excited to get this far, and I'm looking forward to finishing up, and learning more.

Thank you,
Jon Edney

---

### Post by mörgæs on 2012-04-17
Moved to the server forum.

---

