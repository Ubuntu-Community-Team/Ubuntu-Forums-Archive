---
title: "VFTPS help"
date: 2009-04-02
forum: Server Platforms
---

### Post by jigglywiggly on 2009-04-02
Here is what I want to do: Use FTPS to access a folder located in /home/administrator/webroot/warkid
I want this to be accessible under the account "warkid" with a password of my choice. So to first make an account for this user and I want him locked into that warkid folder... I did and put his account into that folder ok done with that.
sudo useradd warkid
sudo passwd hispasswd



Next part uhm what next part I got confused D:

So I went into the config file by sudo gedit /etc/vsftpd.conf
I disabled anonymous access and I thought that should be it?
Well when I try to connect under the account of warkid with that password I set under port 22 it just says connection timed out on filezilla, then I also tried 21, and 20. I want to connect using ftps and I don't want any unsecure ftp if possible.
 Howcome it won't connect? What am I doing wrong D: (PS why is there no gui under webmin or something? I mean setting a ftp server in IIS or filezilla is 100000x times easier)

---

### Post by jigglywiggly on 2009-04-03
Anyone?

---

### Post by jigglywiggly on 2009-04-03
Ok I connected on the local machine via 127.0.0.1 HOWEVER howcome I made an account that has all the boxes unchecked and stuff, but it can BROWSE TO ANY DIRECTORY??!??! WTF? and I can't write files anywhere even in the folder it's supposed to be able to.

---

### Post by jigglywiggly on 2009-04-04
Meh screw it, I just put the webserver files shared and the windows pc handles the FTPS.

---

