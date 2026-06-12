---
title: "ubuntu server &amp; vsftpd"
date: 2009-03-13
forum: Server Platforms
---

### Post by subfire91 on 2009-03-13
im trying to install vsftpd on my ubuntu server machine. i downloaded and installed the program but i couldnt find any straight forward documentation so am asking a little bit help:

1)i want a secure ftp server. in the internet i found the commands i have to add to vsftpd.conf file. Users that posted the instructions enable both TLS and SSL. What should i enable TLS or SSL or both? 

2)Adding users. I found out that i have to edit the passwd file to add users. what to write??? What are the default user accounts that vsftpd has upon installation. i want to remove them and add my own.

3)User permissions. How to add admin account that has both read write access and a user account that has only read access.

4) Port redirection. How to do port redirection? Incoming connection from port 21 for example and redirecting to another port on the server.

5)I have two hdds in my server. A small one for the os and another with my data. i want only the one hdd with the data to be shared from the server with the other one not being visible. what is the default dir that vsftpd is set to and how i change it.


i know is big post but i would appreciate any help. Thnx for ur time :)

---

### Post by HermanAB on 2009-03-13
Well, FTP is insecure by design, since the username and password is transmitted in plain text for all the world to see.  Vsftpd is a decent server, but it is not any more secure than any other. However, FTP is good for use on a LAN, since it is nice and simple, or as an Anonymous download only server on the internet.

If you want SFTP then you need to install the ssh-server package.

Cheers,

Herman

---

### Post by subfire91 on 2009-03-13
> **HermanAB said:**
> Well, FTP is insecure by design, since the username and password is transmitted in plain text for all the world to see.  Vsftpd is a decent server, but it is not any more secure than any other. However, FTP is good for use on a LAN, since it is nice and simple, or as an Anonymous download only server on the internet.

If you want SFTP then you need to install the ssh-server package.

Cheers,

Herman

basically i dont want any anonymous users to be able to login. as i said i have 2 hdds a small one for the os and another for data. i want all users to be see only the data hdd with read-only access except one account with read+write access and that is the admin (me). i dont have a clue how i do this!!

---

### Post by hyper_ch on 2009-03-13
I'd also vote for openssh-server

with MySecureShell to chroot people and deny shell access.

---

### Post by subfire91 on 2009-03-13
hi thnx for the reply but the last thing that im looking now is security. im looking to configure it first up and running and then apply security. im looking to set the user permissions and hdd access as i want first

---

### Post by HermanAB on 2009-03-13
The trick to making a secure Anonymous FTP server, is to set the anonymous user account such that it has no shell (use /bin/false as the 'shell'), then those users cannot log in or use any other services.

Cheers,

Herman

---

### Post by subfire91 on 2009-03-14
anyone???

---

