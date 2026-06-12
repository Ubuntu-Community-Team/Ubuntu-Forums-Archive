---
title: "Proftpd jailed users can get out ?"
date: 2008-01-11
forum: Server Platforms
---

### Post by TheNTW on 2008-01-11
I need help. Jailed users can get out easy.

I read from this tutorial, and well - Success. Only problem now is with users.

I Did:

sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false
sudo useradd userftp2 -p your_password -d /home/FTP-shared2 -s /bin/false

See I need userftp to access /home/FTP-shared and Only FTP Shared, but I Need userftp2 to use FTP-Shared2 and only that dir. 
How do i limit that ? haven't found anything :(

---

### Post by HermanAB on 2008-01-11
Did you read the proftpd manual on the project web site?  It has an enormous number of options, including allowing and hiding directories.

Cheers,

Herman

---

### Post by TheNTW on 2008-01-12
I tried the DefaultRoot ~ etc., nothing worked. Maybe you could tell me one of working option of the several you have in mind...

---

### Post by TheNTW on 2008-01-16
*Bump*
Come on, is it so hard to tell me how ? I've read all the manuals tutuorials etc. haven't spotted anything. I just don't understad how to do it, had big troubles installing. Well - been there done that, but now still problems with jailing users. DefaultRoot ~ doesn't work. It just won't let user out of DefaultRoot /var/www/ , but will allow access to other www folders...
Is there a way to change DefaultRoot for each user ? Help me please.

---

