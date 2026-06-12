---
title: "Ununtu server 8.0.4.1 question regarding web server"
date: 2008-09-08
forum: Server Platforms
---

### Post by Jasonko on 2008-09-08
Hi,

I have the desktop version installed, Ubuntu 8.0.4.1
When reading about the server version, it looks like it has a web server, mail server, ftp server etc.. all installed with the package. Is this right?

I am asking because i chose Ubuntu server 8.0.4.1 as my Linode.com distro, and there is nothing there. No web server, no ftp server. Nothing. I was hoping when i opened a Linode account that the Ubuntu server edition would be all ready to go.

Is there something I'm missing?.
I'm just new to Linux. 


Jason.
---

---

### Post by tinny on 2008-09-08
Hi

A Ubuntu server install will just provide you with a server quality operating system install. The FTP, mail etc... functionality that you are looking for must be setup in addition to your standard install.

Have a look at the Ubuntu server documentation.

[Web servers]("https://help.ubuntu.com/8.04/serverguide/C/web-servers.html")
[mail server]("https://help.ubuntu.com/8.04/serverguide/C/email-services.html")
[File servers]("https://help.ubuntu.com/8.04/serverguide/C/file-servers.html")
etc...

---

### Post by jerome1232 on 2008-09-08
sudo tasksel will give you an easy way to install a few services (ftp, lamp, openssh, mail) but you will still have to configure them.

---

### Post by Jasonko on 2008-09-08
Thanks alot for your help guys!.
Now i understand alot better.
I will try this install in the morning :)

Just one more question, what do you think of 'XAMPP Linux 1.6.7' ([www.apachefriends.org](www.apachefriends.org)) it has everything all in the one install.
Is this safe to install ?. 

Thanks again,
Jason.
---

---

### Post by tinny on 2008-09-08
I personally dont like installing beta software on servers.

All the XAMPP components can be installed individually on Ubuntu. You will learn alot by going through the process of installing each of these.

TIP: Dont avoid learning how to install these components properly ;) Will will gain valuable knowledge. :)

---

### Post by jerome1232 on 2008-09-08
Doesn't lamp have all of that anyways...

---

### Post by tinny on 2008-09-08
> **jerome1232 said:**
> Doesn't lamp have all of that anyways...

Pretty much. The LAMP "P" is usually for PHP.

The XAMPP "PP" is for PHP and Perl. Also I believe the XAMPP gives you phpMyAdmin.

I don't see the point personally. Just install them the standard way!

---

### Post by Jasonko on 2008-09-09
Ok thanks for all that.
I will use the Ubuntu repositories to install all the software.

Thanks again for your help! =D>:grin:

---

### Post by Iowan on 2008-09-09
I downloaded the 8.04.1 server version.  The LAMP installation was almost too easy.  I also installed the SAMBA server... just in case.  The old HP NetServer LC II is no speed demon, but a $5 trainer ain't bad.

---

