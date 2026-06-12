---
title: "How to add users to vsftpd without making local accounts?"
date: 2010-12-03
forum: Server Platforms
---

### Post by nLinked on 2010-12-03
I'm using vsftpd as my FTP server. I have set it up so I can access my home directory via FTP, requiring my login.

But I want to make a folder in my documents (or anywhere really), which only my colleague can access. But I don't want to make a local Ubuntu user account. He just needs to be able to send files to this folder, connecting remotely, using his own login details.

Is there any way?

---

### Post by Strega on 2010-12-03
Hello,

This can be done with Virtual Users for vsftpd. I don't know exactly how to set them up, maby someone else does :D ?

Regards,
Strega

---

### Post by inphektion on 2010-12-04
yea virtual users.  you should be able to google it pretty easily.  I use the db4.6-utils for the local password file for users. 
ok i googled for you, this seems to be pretty close to what i did: [http://linuxforfun.net/2008/04/05/vsftpd-virtual-users/](http://linuxforfun.net/2008/04/05/vsftpd-virtual-users/)

---

### Post by lykwydchykyn on 2010-12-04
pure-ftpd does this out of the box without much fiddling, you may want to look into that.  There's even a webmin module out there for it if you like webmin.

---

### Post by Return Privacy on 2012-07-02
I have the same problem. I am trying to setup virtual users in vsftpd. I tried the tutorial in the above link, and it does not work at all. Can someone PLEASE explain how to add virtual users to vsftpd? Please explain it in a way that we can understand? I've found several tutorials online, but I still can't get virtual users setup. I do have vsftpd setup correctly and working. I can connect to it by using the Ubuntu main user account, but I don't want to use that. I need to setup 2 virtual users, and restrict them to a specific folder, locking them out of the rest of the ubuntu computer.
Thanks

---

