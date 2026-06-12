---
title: "Can I Limit Ftp User Access Or Navigation"
date: 2007-06-26
forum: Server Platforms
---

### Post by green-12 on 2007-06-26
*NEWB HERE, THANKS*

I have created a user to proftp like the following

sudo useradd userftp -p your_password -d /home/FTP-shared -s /bin/false

Next I had to set the password again like this:

sudo passwd userftp
(then i entered the password twice)

After theses steps I was able to gain access but I can see all the files of my system(including all the root directories) and I was wondering if there is a way to only see the ftp folder and not be able to navigate around with certain users?

---

### Post by dantrevino on 2007-10-04
[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-Chroot.html)

dan

---

