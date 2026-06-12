---
title: "Assistance with Lamp setup"
date: 2016-03-11
forum: Server Platforms
---

### Post by Shane_MacNeill on 2016-03-11
Hello, 

I have successfully setup a server running apache and mysql... however there is always something that causes it to fail, and I end up reinstalling. The latest seup was installing ispconfig as a gui to add websites and databases. it worked ok until I clicked a firewall link, and now it's unaccessable. so I am reinstalling Ubuntu 15.10 a third time. 

All I need is to be able to add a website, ftp the files up to the directory and add a database. 
I figure I can use the mysql workbench on my machine to connect to the DB on the server, but what I really need is a way to add a site and ftp user with folder access. So far I have tried vsftp, but I haven't been able to get it to add users with folder access to the folders that they need to. I followed a couple different sites instructions on setting it up.... but neither work, and I am unable to connect. If I leave it as it's installed I can connect fine, but not to the folders that I need to be connected to. Also adding a site with the console, editing a few files seems rather time consuming, and frustrating. I have 30+ sites to add and need a good solution. 

Is there any gui's that I can use to add sites and FTP accounts? I havn't found a single thing. 

Please any assistance would be appreciated otherwise I guess i'll spend all weekend trying to add the sites... and no idea how to get the files to the server. 

Thanks

---

### Post by Andy_Richardson on 2016-03-12
I'm assuming you're accessing your server using ssh? If so, why don't you use sshfs rather than ftp?

Use the following command to mount sshfs in ubuntu:
```
sshfs -o allow_other user@host:/path/to/folder /mount/point
```

---

### Post by SeijiSensei on 2016-03-13
> **Shane_MacNeill said:**
> I figure I can use the mysql workbench on my machine to connect to the DB on the server

I prefer Microsoft Access with the MySQL ODBC driver.  LibreOffice Base is a workable solution as well.

> Also adding a site with the console, editing a few files seems rather time consuming, and frustrating. I have 30+ sites to add and need a good solution.

There really aren't many alternatives for this task.  You'll need a separate file in /etc/apache2/sites-available/ for each virtual host. Use SSH and sudo.  If the sites are reasonably simple, you can clone a basic template in just a minute or two.

The sites need not reside under /var/www.  I have all my sites in directories under a common username as /home/user/sites/sitename.  This works well if you're the only one who will be administering the content.  If each site needs to be managed by a different user, I recommend creating accounts for each of them and placing the site in a directory under that account. Just point the DocumentRoot directive in Apache to the appropriate location and make sure the directories and files below them are world-readable.  

FTP is not a secure protocol.  I suggest using SCP or SFTP with clients like Filezilla or WinSCP.  If all the clients have Linux, then sshfs is a good alternative.  On KDE systems like mine, I can connect to remote directories using a "fish" URL.  That's how I transfer files to my sites with the Dolphin file manager.  I believe it's possible to use Nautilus in a similar manner.

---

