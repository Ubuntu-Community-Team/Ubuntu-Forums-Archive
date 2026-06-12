---
title: "Install a FTP srever / other upload method"
date: 2008-11-01
forum: Server Platforms
---

### Post by dethredic on 2008-11-01
So, I have a basic LAMP server installed, and I want people to be able to upload files to 1 of about 10 directories.

What is the best way / easiest way to do this?

I only want them to have access to those 10 directories, but I want them to be able to make sub directories and such inside there, and upload the files only to those directories.

---

### Post by Thirtysixway on 2008-11-02
You may want to do this with something like a PHP script.  FTP would work but would take a lot more configuration.

Be sure to watch your permission/security issues with something setup like this.  Remember to never trust the user.

---

### Post by doogy2004 on 2008-11-03
If you have OpenSSH installed, by default it will accept SFTP connections, using port 22 or whatever port you are using for ssh.

---

