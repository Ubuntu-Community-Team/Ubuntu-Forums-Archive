---
title: "Setting up FTP the way I want it.."
date: 2005-06-21
forum: Server Platforms
---

### Post by lozzd on 2005-06-21
I currently have two servers running. Originally, everything was handled by my outdated Windows XP server, with Apache, FTP server, and an email server.

Apache has been fine on my new Ubuntu box for a while now, with FTP still going to the old server and then accessing the users directories via Samba (e.g. home dir: \\zebedee\www\example\)

I run a hosting company, so the GUI interface is very convinient and simple for me, I just created a new directory on the server, created a new user in the FTP program, and then set the user a password and full read and write on the directory \\zebedee\www\username
This has worked brilliantly but I need to move the FTP functionality onto my new server. I've played around with some servers, or tried to but they all seem so complex, and involve creating new users on the actual system etc which is all too dodgy for me. 
Is there such a server that allows the setup I have described above? Where each user (assigned in a config file perhaps) has their own directory in /var/www/ which only they have access to?

Thanks in advance

Laurie

---

### Post by deBaas on 2005-06-21
Your looking for pure-ftpd. And if you want a nice GUI for it install the webmin module.

---

### Post by lozzd on 2005-06-22
[QUOTE=deBaas]Your looking for pure-ftpd. And if you want a nice GUI for it install the webmin module.[/QUOTE]


Thanks for the suggestion! 
The webmin module confused me greatly, then I discovered it was way out of date! 
So I found another third party interface, using PHP, and used the MySQL version of pure-ftpd. I
Its working a treat! Thanks!

Laurie

---

