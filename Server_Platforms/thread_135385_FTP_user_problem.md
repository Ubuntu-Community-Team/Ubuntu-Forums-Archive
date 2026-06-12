---
title: "FTP user problem"
date: 2006-02-23
forum: Server Platforms
---

### Post by Darkfoxx on 2006-02-23
Hey everyone, so far Ubuntu has been a great distro to use. 

I am using PureFTPd and PureAdmin and I'm having a problem logging into a user account I made which connects to the "/var/www/" directory, so that I can upload files to the web server from another pc.

I get this when connecting:
```
USER web
331 User web OK. Password required
PASS (hidden)
530 Authentication failed, sorry
Connection failed
```

I triple checked that I put the password in right (in PureAdmin and in my ftp client), and I did....so I know it isn't that.

I also set up the server using this guide:
[https://wiki.ubuntu.com/PureFTP](https://wiki.ubuntu.com/PureFTP)

Instead of "joe" I used "upload", but this is for another account, which works fine. However, it seems that I can't make a user account which logs into any dir outside of the "/home/ftpusers" folder, such as the /var/www/ folder.

Any help is appreciated!

---

### Post by pestilence4hr on 2006-02-23
I would highly advise against using ftp if you have to enter your user password.  There is absolutely no reason to do so -- if openssh-server is not installed apt-get install it and use sftp.  I'm sure there are some decent gui's out there if that floats your boat.  It really is a one line setup, though:  sudo apt-get install openssh-server, and you're done.

---

### Post by Darkfoxx on 2006-02-24
Alright, so I installed it. Now how do I set it up? I never used ssh so I'm pretty new to it.

EDIT: Nevermind, I found a program and then I just connected to the server ip and used my login. Thanks again!!!!

---

