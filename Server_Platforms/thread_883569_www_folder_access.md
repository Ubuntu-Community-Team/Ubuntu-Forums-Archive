---
title: "www folder access"
date: 2008-08-08
forum: Server Platforms
---

### Post by maxidrom11 on 2008-08-08
How do I set up a www folder so that particular user can have access to it for uploading their web-pages + files with FTP client via my server IP address? :confused:

I have Apache 2 installed

---

### Post by ChumleyEX on 2008-08-08
install an ftp server

> sudo apt-get install proftp

---

### Post by windependence on 2008-08-08
[http://news.softpedia.com/news/How-to-Install-Vsftpd-in-Ubuntu-45753.shtml](http://news.softpedia.com/news/How-to-Install-Vsftpd-in-Ubuntu-45753.shtml)

As said above, proftp is good as well.

-Tim

---

### Post by maxidrom11 on 2008-08-15
is this a good guide to setup FTP server for users for **ubuntu server 8.04**???
[http://www.howtoforge.com/vsftpd_mysql_debian_etch](http://www.howtoforge.com/vsftpd_mysql_debian_etch)

---

### Post by windependence on 2008-08-15
Looks like it should work to me.

-Tim

---

### Post by Kolipoki on 2008-08-15
I personally have been using [**[COLOR="RoyalBlue"]WinSCP[/COLOR]**]("http://winscp.net/eng/index.php") on a Windows box. IMHO it's quite a good secure alternative to FTP. You can transfer files just as any FTP. I do beleive they did a great job with that solution.

Some similar clients are available for Linux/Ubuntu's desktops, but I can't remember their names.

Would be nice to know some of the pros and cons for each solution, meaning FTP vs these SFTP/SCP clients.

K.

---

### Post by windependence on 2008-08-15
Certainly WinSCP would have been my first choice but he specifically wanted ftp. In Linux you can just use SCP from the terminal OR in a graphical environment sftp using drag and drop in Konqueror or Nautilus. It works great.

-Tim

---

### Post by polecat409 on 2008-08-16
> **Kolipoki said:**
> I personally have been using [**[COLOR="RoyalBlue"]WinSCP[/COLOR]**]("http://winscp.net/eng/index.php") on a Windows box. IMHO it's quite a good secure alternative to FTP. You can transfer files just as any FTP. I do beleive they did a great job with that solution.

Some similar clients are available for Linux/Ubuntu's desktops, but I can't remember their names.

Would be nice to know some of the pros and cons for each solution, meaning FTP vs these SFTP/SCP clients.

K.

gFTP is a great Linux alternative to WinSCP.

Install OpenSSH on your server, then you can use gFTP to do secure file transfers.

FileZilla is also available for Windows and Linux and supports FTP, SFTP and FTPS, but no SSH support :(

---

### Post by sergie on 2008-09-30
> **windependence said:**
> Certainly WinSCP would have been my first choice but he specifically wanted ftp. In Linux you can just use SCP from the terminal OR in a graphical environment sftp using drag and drop in Konqueror or Nautilus. It works great.

-Tim

I thought of getting rid of Windows software last month, I would definitly suggest vsftpd [very secure!]

__________________
[**PharmacyRX**]("http://www.pharmacyrx.org/")

---

### Post by Kolipoki on 2008-09-30
> **polecat409 said:**
> ...

FileZilla is also available for Windows and Linux and supports FTP, SFTP and FTPS, but no SSH support :(

Actually Filezilla has come a long way. I got curious after reading your post, cuz I noticed recently that Filezilla is using port 22. So went to the site and... tah daaah... it IS supporting SSH in last version: [http://filezilla-project.org/client_features.php]("http://filezilla-project.org/client_features.php")

Way to go! Thumbs up...

---

