---
title: "How To: Setup SFTP with OpenSSH"
date: 2008-04-06
forum: Server Platforms
---

### Post by doogy2004 on 2008-04-06
[LIST=1]
[*]Install OpenSSH
```
sudo apt-get update
sudo apt-get install ssh
```
[*]Open your favorite FTP Client (I used FileZilla)
[*]Enter the Address of your server, your username & password, and set the port number to 22
[/LIST]

---

### Post by kevdog on 2008-04-06
What if I wanted to connect with keys rather than passwords?

---

### Post by doogy2004 on 2008-04-06
> **kevdog said:**
> What if I wanted to connect with keys rather than passwords?

Using this method SFTP authenticates on the same credentials that SSH authenticates on.  I would imagine that you would need an SFTP client that supports the use of keys.

---

### Post by doogy2004 on 2008-04-07
[http://wiki.filezilla-project.org/Howto](http://wiki.filezilla-project.org/Howto)

here is a link that explains how to get keys to work with filezilla

---

