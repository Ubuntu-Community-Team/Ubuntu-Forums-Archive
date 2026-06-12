---
title: "Setting up a file server"
date: 2008-08-15
forum: Server Platforms
---

### Post by MarlonDean on 2008-08-15
Hi everyone.

I recently started using ubuntu. At work I have about 16 windows clients and i want to experiment with an ubuntu server. Now i am totally new to linux so i need someone to point me in the right direction:

I need to setup a file server that will allow windows clients to log in. but the thing is that when user 'A' logs into the windows client, I want his 'My documents' folder to point to a spesific folder on the server. If user 'B' logs in, again it will point his my Documents to an unique folder on the ubuntu server. I am not afraid to google, but like i said, i am very green at linux, and dont even know what this is called

Thanks for your advice!!

---

### Post by MarlonDean on 2008-08-15
Hi everyone.

I recently started using ubuntu. At work I have about 16 windows clients and i want to experiment with an ubuntu server. Now i am totally new to linux so i need someone to point me in the right direction:

I need to setup a file server that will allow windows clients to log in. but the thing is that when user 'A' logs into the windows client, I want his 'My documents' folder to point to a spesific folder on the server. If user 'B' logs in, again it will point his my Documents to an unique folder on the ubuntu server. I am not afraid to google, but like i said, i am very green at linux, and dont even know what this is called

Thanks for your advice!

---

### Post by eddVRS on 2008-08-15
Hi,

I share files with friends and the band, so I set up an ftp server so they could access from over the internet, or within the local network.

If this sounds like what you need then have a look into **proftpd**, or **gproftpd** if you want graphical administration.

Have a read of this [http://www.linuxhelp.net/guides/proftpd/(although](http://www.linuxhelp.net/guides/proftpd/(although) not the How-to I used) and PM me if you have problems.

Ted

---

### Post by windependence on 2008-08-15
You don't have to do anything special on the server. If you install SAMBA, you would then create their directories on the server, and on each of their Windows destops, set the folder location of MyDocuments to the appropriate folder on the Linux box by right clicking on their My Documents folder and on the target tab click on move, navigate to the folder, and finish. Windows will think your Linux box is just another Windows server. It's easy.

Note that the users must exist on the Linux box with the same user name and password.

-Tim

---

### Post by Sef on 2008-08-15
Moved to Server Platforms.

[Setting Up Samba]("http://help.ubuntu.com/community/SettingUpSamba")

---

### Post by windependence on 2008-08-15
This is actually a cross post. I answered you [here.]("http://ubuntuforums.org/showthread.php?t=890538")

-Tim

---

### Post by windependence on 2008-08-15
> **eddVRS said:**
> Hi,

I share files with friends and the band, so I set up an ftp server so they could access from over the internet, or within the local network.

If this sounds like what you need then have a look into **proftpd**, or **gproftpd** if you want graphical administration.

Have a read of this [http://www.linuxhelp.net/guides/proftpd/(although](http://www.linuxhelp.net/guides/proftpd/(although) not the How-to I used) and PM me if you have problems.

Ted

This isn't really what he wants to do. He is looking to use a remotely mounted My Documents folder. SAMBA is best for that.

-Tim

---

### Post by Rocket2DMn on 2008-08-15
Threads merged - please do not create multiple threads for the same question, even in different areas of the forums.  It isn't fair to those helping you and doesn't really help get more or better responses.
Thank you.

---

