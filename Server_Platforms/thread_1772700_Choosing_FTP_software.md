---
title: "Choosing FTP software"
date: 2011-05-31
forum: Server Platforms
---

### Post by Master_Taco on 2011-05-31
Does anyone have any recommendations on what software I can use so I can FTP my site's files to the /var/www directory? I tried using vsftpd, but the software was terribly difficult to configure correctly. I tried telling it to make everything that was uploaded have "704" permissions, but everything I uploaded had strange permissions on them. When I used to use professional Linux hosting, that was never a problem, so I'd like a simple FTP server software so I can easily manage my site from a remote location.

I'm not in love with FTP, so if someone has a better way of getting files to my server, let me know.

---

### Post by HermanAB on 2011-06-01
Use SSH.

FTP servers work out of the box with ZERO configuration.  People only run into trouble when they attempt to change it.  The secret to NOT changing anything is to create a FTP user account with the home directory pointing to where you want to have access to!

---

### Post by Master_Taco on 2011-06-01
I did try it without changing anything, however, when I did, it didn't allow write at all. I had to go in and change it to allow write. Once write was allowed, when I put a file on the server, it was not readable by "public", so it would throw up a 403 Forbidden error when I try accessing the file. I was not successful on getting this to work properly. If I was setting up an extremely simple site, I'd just change the permissions myself, however, if I'm bulk uploading (such as installing PHPbb) I would have to change the permissions on EVERY SINGLE FILE, which is not my idea of fun.

How do I configure/use SSH to transfer files? The main machine I work on is a Windows machine, and I manage the server with PuTTY or just walking over to the machine.

---

### Post by ikt on 2011-06-01
> **Master_Taco said:**
> Does anyone have any recommendations on what software I can use so I can FTP my site's files to the /etc/www directory

/etc/www?

I thought the default www directory was /var/www/ ?

I recommend filezilla as an ftp client, but I assume you're trying to connect to a remote site, not ftp to your own computer on your own computer.

---

### Post by Master_Taco on 2011-06-01
> **ikt said:**
> /etc/www?

I thought the default www directory was /var/www/ ?

I recommend filezilla as an ftp client, but I assume you're trying to connect to a remote site, not ftp to your own computer on your own computer.
I'm sorry, you are correct, it is /var/www. I wasn't looking at it and took a shot in the dark. I have filezilla as a client on my PC, I'm looking for server software. Keep in mind I'm not using a GUI. My server is on my network, so it is technically local, but it's not the same machine, no.

---

### Post by Lars Noodén on 2011-06-01
> **Master_Taco said:**
> How do I configure/use SSH to transfer files? 

You don't.  File transfer is already set up for you.  Try connecting using FileZilla and be sure to use SFTP instead of FTP by pointing it to port 22.

---

### Post by satanselbow on 2011-06-01
> **Lars Noodén said:**
> You don't.  File transfer is already set up for you.  Try connecting using FileZilla and be sure to use SFTP instead of FTP by pointing it to port 22.

+1 for Filezila. 

gFTP is another gui alternative - although no longer actively maintained ;)

As suggested above - if you set up an FTP account that has the public html folder of your webserver pointed to root you will always be uploading files to the correct place ;)

---

### Post by satanselbow on 2011-06-01
> **Master_Taco said:**
> Keep in mind I'm not using a GUI. My server is on my network, so it is technically local, but it's not the same machine, no.

Sorry - your question is more about correcting the permission problem rather than what software to use really so more and more recommendations for FTP software aren't really helping :$

Think you are looking to change the permissions on your /var/www or create a user with the required writable permissions with FTP access on your server machine ;)

You could also move your serveroot to a publicly available folder (under $HOME) on the server machine and just cut n paste through nautilus ;)

---

### Post by Master_Taco on 2011-06-01
> **Lars Noodén said:**
> You don't.  File transfer is already set up for you.  Try connecting using FileZilla and be sure to use SFTP instead of FTP by pointing it to port 22.
Thank you, I will try that.
> **satanselbow said:**
> +1 for Filezila. 

gFTP is another gui alternative - although no longer actively maintained ;)

As suggested above - if you set up an FTP account that has the public html folder of your webserver pointed to root you will always be uploading files to the correct place ;)
I'm using Windows, just from the name I'm assuming gFTP is designed for Linux (Gnome)?
> **satanselbow said:**
> Sorry - your question is more about correcting the permission problem rather than what software to use really so more and more recommendations for FTP software aren't really helping :$

Think you are looking to change the permissions on your /var/www or create a user with the required writable permissions with FTP access on your server machine ;)

You could also move your serveroot to a publicly available folder (under $HOME) on the server machine and just cut n paste through nautilus ;)
Yes, it was about what software to use, what server software to use. I tried vsftpd, and the server software its self screwed up the permissions. However, if using SSH works, it won't even be relevant. Also, I don't have a GUI on the server, so using Nautilus is not possible without installing GDM and X11.

---

### Post by Maheriano on 2011-06-01
I used to use gFTP until it crashed consistently when I tried to open multiple tabs so now I use Filezilla without any issues. My workspace 3 is dedicated to FTP!

---

### Post by Master_Taco on 2011-06-01
> **HermanAB said:**
> Use SSH.

FTP servers work out of the box with ZERO configuration.  People only run into trouble when they attempt to change it.  The secret to NOT changing anything is to create a FTP user account with the home directory pointing to where you want to have access to!
Thank you, sir, this works perfectly!

---

