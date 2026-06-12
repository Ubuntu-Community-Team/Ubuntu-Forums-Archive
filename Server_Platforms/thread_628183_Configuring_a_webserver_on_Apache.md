---
title: "Configuring a webserver on Apache"
date: 2007-12-01
forum: Server Platforms
---

### Post by molimo140 on 2007-12-01
Hello all,

I am somewhat new to linux but I know my way around a little bit.  I am however completely new to webhosting and have a few questions.

I have installed ubuntu 7.10-server and have configured my LAMP server and have all the bits working.  

After some install troubles with attempting to get a GUI on top of it, I am now administrating my server via Webmin and my laptop.

My questions are:

1) Since I have no GUI and am somewhat new to the whole command line interface, how do I go about actually adding website documents (html/xml/etc...) to my apache webserver so I can direct a browser to them?
2) How can I edit my files and folders remotely through another computer? ssh?

Essentially I need a way to use my ubuntu computer without installing a GUI directly on it.  I want to have near to all of the features that having X installed would give me though...without actually installing X.  

I have attempted to install ubuntu-desktop with all its packages and such and my video card has a heart attack and general badness occurs.  In short X won't start.

Sorry if my questions are somewhat vague and I am sorry if this is in the wrong section.  If it is in the wrong section if I could be directed to the right section that'd be great as well.

Thanks.

---

### Post by freebeer on 2007-12-01
There's lots of ways to do things, of course, but the most common way of updating a web server is through ftp I would think.  That's how I update mine, anyway.

---

### Post by molimo140 on 2007-12-01
Alright well how would I go about doing that?

---

### Post by gpredrag on 2007-12-01
There are (I believe) HOWTOs about installing vsftpd on ubuntu, since FTP is popular way of uploading content to your web server.
But, since you probably already have ssh installed on that server, you are already good to go with sftp (and have encrypted communication as a bonus),
You can connect to your server trough Nautilus "Connect to server.." and choose SSH.
For editing your apache config you can ssh to webserver and use editor.

---

### Post by molimo140 on 2007-12-01
Alright thanks for the replies everyone.

I'm now doing file administration via PuTTY on my laptop (forgot to mention it's running windows)  and successfully have use of its ftp functions.

I am however having trouble logging in as root -- mainly speaking I do not have write privileges to the folders I really need privileges to (/var/www/ for example)  So I've supplemented by copying to the /home/ folder and doing a sudo cp from the actual server computer.

This however is very inconvenient as I'd like to administrate remotely when I'm not sitting at home as well.  

So my new question is:  How do I log in with root access?  My normal sudo password doesn't work when logging in as root@my-server.

Thanks in advance.

---

### Post by gpredrag on 2007-12-02
There are several ways to do that.
You can set password for root so you could be able to login trough ssh as root and copy anything anywhere.

or, to stay on the safe side, you can change ownership of /var/www to your user account (check man chown, and do not blindly copy commands from forum posts), so you would be able to update web server's home directory.
Also check filezilla ftp/ftp(ssl) and sftp client for windows.

---

### Post by ruibernardo on 2007-12-03
It is not good to set a root password if you are connecting through the Internet. If you are using FTP, the root password will be sent in clear text over the net and the root account will be enabled. If you use SSH, anybody with that password will be able to login as root. 

You can type "sudo -i" in SSH to have a root prompt without enabling a root account.

Use a non admin account to use FTP or use virtual users in vsftpd to use a non-shell password with a virtual user with your username, or enable FTPS in vsftpd to encrypt the connections. 

Take a look at my signature to do one or all this options.

---

