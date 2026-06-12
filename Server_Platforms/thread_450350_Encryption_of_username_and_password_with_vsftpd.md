---
title: "Encryption of username and password with vsftpd?"
date: 2007-05-21
forum: Server Platforms
---

### Post by fyl2u on 2007-05-21
I've got my vsftpd server working on the internet now, but currently my username and password aren't encrypted.

I've been told I should use SSL for this but I'm clueless as to how to go about this.

There will be many users using this ftp site - will they all need to install ssl too?

will they still be able to access the server in their browsers or will they need ftp client software to use ssl?


Thanks in advance.

Phil

---

### Post by Wim Sturkenboom on 2007-05-21
See [http://www.brennan.id.au/14-FTP_Server.html](http://www.brennan.id.au/14-FTP_Server.html) for a guide how to set it up.

I don't know if a browser can handle it (doubt it, to be honest). At the bottom of given page are two ftp clients that can be used. I use a third one, *filezilla* (under windows).

---

### Post by fyl2u on 2007-05-21
> **Wim Sturkenboom said:**
> See [http://www.brennan.id.au/14-FTP_Server.html](http://www.brennan.id.au/14-FTP_Server.html) for a guide how to set it up.

I don't know if a browser can handle it (doubt it, to be honest). At the bottom of given page are two ftp clients that can be used. I use a third one, *filezilla* (under windows).

Ah, OK, that's done it, but the .pem file is in my ftp directory for my main user, but not any of the other ftp user folders. (I have 11 different FTP users, each with their own FTP directory).

Do I need to do these steps 11 times to secure all 11 of the users?

---

### Post by Wim Sturkenboom on 2007-05-21
Never thought about it; but with my understanding of 'how it works', I don't see a reason why. 
I'm usually the only user on my system, so can't remember if I ever checked it.

My pem-file is in /etc/somewhere.

---

### Post by random_mike on 2007-05-21
Users can use Firefox with plugin FireFTP [http://fireftp.mozdev.org/](http://fireftp.mozdev.org/)
It supports ssl.

---

### Post by Wim Sturkenboom on 2007-05-22
> **Wim Sturkenboom said:**
> Never thought about it; but with my understanding of 'how it works', I don't see a reason why. 
I'm usually the only user on my system, so can't remember if I ever checked it..Just verified with a second user. As I expected, there is no problem.

---

