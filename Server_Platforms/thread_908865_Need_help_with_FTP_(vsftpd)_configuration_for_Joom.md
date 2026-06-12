---
title: "Need help with FTP (vsftpd) configuration for Joomla"
date: 2008-09-02
forum: Server Platforms
---

### Post by notquitehere188 on 2008-09-02
I am trying to set up FTP on my server for Joomla! access, and I found this post 

> I started my server from scratch and I managed to get joomla 1.5.3 working with the ftp layer.

install proftpd or vsftpd and create a username and password and assign the working directory to be the one that you will have joomla installed.

in the username field put [email]username@yourserver.com[/email]
passwd : your password, working directory you can put slash (/) since its on joomla directory already and the host would be ftp.yourserver.com , port 21 and you will be good to go. no more permission issues.. dirs are 755 and files 644. 
if you are concerned about security, disable bash login for the ftp and move files such as configuration.php one directory up. there are more tricks in joomla forums.

Adam

Which is exactly what I need to do, but I don't understand.

I have vsftpd installed, but how do I assign a working directory for a user account.  Rather, what does that mean?

Also, how can I restrict ftp access to local connections.

---

### Post by CuraHack on 2008-11-07
and what if I don't have a domain and I use the no-ip service?:(

---

