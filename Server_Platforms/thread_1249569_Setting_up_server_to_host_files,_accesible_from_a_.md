---
title: "Setting up server to host files, accesible from a browser"
date: 2009-08-25
forum: Server Platforms
---

### Post by bramming on 2009-08-25
Hey :) I'm trying to set up my own server. So far i have ubuntu 9.04 server edition installed with a LAMP server, SAMBA, and vsftpd set up, along with SSH for connection. I am, however very confused when it comes to the following: 

I would like to set up a website, that asks users to log in first. When they are logged in they can see 2 directories. Their own private directory and a public one, to share files with others. So they will have read/write access to both, but only those 2 folders, not other peoples private folders, or the servers root dir. I want it set up so people can easily just go to whateverdomain.com, log in, and upload their notes or download some. I've been looking at FTP and Samba but i just cant seem to get it right

I'm not asking for a complete solution, but a point in the right direction of which technology i should use (FTP? SAMBA? something else? :) ) would be awesome! :) thanks in advance! :)

---

### Post by k33bz on 2009-08-25
sound like the first thing you need to do is use some java or HTML.

---

### Post by hessiess on 2009-08-25
If you have a shaired storage airia, you need to use a version controal system to prevent users messing up each outers files. Subversion works well for this, and it can be used with DAV and HTTPS, so can be used from within a network where everything except http is blocked. And it has SSL encryption, so is far more secure than the outdated FTP protocol.

if you want to block all access to the server root you need to set up a chroot jail, using svn would also fix this as it uses a different model (check out a local working copy, edit local, upload the diff to the server).

SVN can also be viewed in a web browser.

---

### Post by bramming on 2009-08-25
The server is only to be used by a few persons (max 10) so i dont really need to bother about people messing up other peoples stuff, since all both have a public folder and private. So if they dont want their things changed/deleted they can just upload it in their private directory. But i'll still take a look at SVN. Thanks :)

---

