---
title: "Need suggestions for vsftpd setup"
date: 2009-12-31
forum: Server Platforms
---

### Post by gyzer on 2009-12-31
I've just setup my first home ubuntu server. Its main use is running as a samba file server but I also want to setup a ftp server. The reason why I want to setup the ftp server is for my friends and family to be able to download pictures and videos of my family. Now I was wanting to have this secure, with each person having their own logon and password, but I was wanting them all to be able to access the same root directory that would have the pictures and videos. Now looking at some articles I found on google concerning setting up vsftpd.

 I saw that its easy to create a virtual user and set them to access their own folder, or lock them down into their home directory. Should I go ahead and setup each virtual user and setup up their own directories, and then do a symbolic link from their directories to the main directory that would have all the pictures and videos?

Any help or insight into this would be appreciated. I'm not looking for someone to flat out do this for me, I'm more of just wanting to know the best way on how to do this.

Thanks

---

### Post by hessiess on 2009-12-31
Unless you have a lot of upstream bandwidth, I would advise against hosting anything besides the simplest of websites, or a personal web development server on a home DSL connection. It will be VERRY slow, especially with large files such as videos.

Secondly if you still want to try it, don't use FTP, use SFTP (SSH file transfer protocol) instead, it is a lot newer and much more secure.

You could create a shared directory (chmod 777) then create new users and set there home directory to the shared directory.
```

sudo useradd -d /path-to-dir/ username

```
(you will be prompted for your sudo password, then the new users password)

Though creating a global shared directory like this is an extremely bad idea because any user could, deliberately or accidentally, delete everything in it. If you want to create shared data like this, a version control system would be a much better option.

Make sure you chmod anything you do not want to be public, i.e. your home directory, to 700.

---

### Post by gyzer on 2009-12-31
Thank you for your suggestions hessiess. 

The videos I will be having on the ftp server are quite small, so not allot of bandwidth is needed. This is just going to be used by my family and a few friends, nothing crazy.

I want this to be as easy for the end users to use. Pretty much I'm going to send them a link like [ftp://mysite.com](ftp://mysite.com) and give them their user name and password and thats it. I don't want them to be able to do anything in the directory other than download, and I want them all to be able to download the same files.

From what you said though, couldn't you just give the users in your scenario only read access to the directory and the files within it, instead of giving them total control through chmod 777?

Thanks again for the reply

---

### Post by hessiess on 2010-01-01
Ah, so you want it to be read-only, that wasn't clear from your original post. Yes, that could be achieved by setting the directory permissions to read only for the user, however that would require that you always remember to change the permissions on all new files that you add. You could set write_enable=NO in the VSFTPD configuration file.

Alternately you could just use an Appache HTTP server which would always be read only, be simple for the end user (no FTP client needed) and work anywhere, as the HTTP protocol is almost never blocked. At the expense of being a bit harder to set up. Hares a link to the Apache page describing HTTP authentication: [http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)

---

### Post by gyzer on 2010-01-01
Thanks again hessiess. I'm sorry I wasn't clear before. I've got Apache already installed, so I'll take a look at that link and set that all up.

Thank you so much for the help.

---

