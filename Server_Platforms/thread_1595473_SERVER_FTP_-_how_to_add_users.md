---
title: "SERVER FTP - how to add users?"
date: 2010-10-13
forum: Server Platforms
---

### Post by Apolyonn on 2010-10-13
hey all,

I set up a server using Ubuntu Server (newest version).  The server is synchronized with a dynamic DNS domain (DynDns.org) and I got Apache set up and running without any issues.  I downloaded and installed vsftpd and set the configuration file to match my needs (guest mode is disabled).  Now, I need to create a users list, but I don't know where to go or how to add them.  

How do I add one user, so I can access this server via FTP from a remote location?

---

### Post by sp0nge on 2010-10-13
This [link]("http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/") should help:

---

### Post by ERIC H on 2010-10-13
Don't know if you're married to vsftpd or not, but you could try pureftp using mysql to manage users and their quotas.

[http://www.howtoforge.com/virtual-hosting-with-pureftpd-and-mysql-incl-quota-and-bandwidth-management-on-ubuntu-9.10](http://www.howtoforge.com/virtual-hosting-with-pureftpd-and-mysql-incl-quota-and-bandwidth-management-on-ubuntu-9.10)

This is for 9.10 but still applies to 10.04 and probably 10.10.

---

### Post by Apolyonn on 2010-10-13
> **sp0nge said:**
> This [link]("http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/") should help:

I looked it up, got down to the "configuration" section and typed the htpasswd /etc/vsftpd/passwd myname, and this was the response:
```

"htpasswd: cannot create file /etc/vsftpd/passwd myname"
```Tried with a sudo prefix, made "/vsftpd/passwd" directory in the home folder, and tried the command "htpasswd /home/vsftpd/passwd myname".  Got that command no matter what.

any suggestions?

EDIT

I feel really, really stupid now, but I figured out the solution I was looking for on my own.  I used my dns host, server username, and server password, and got in through Filezilla.  That's basically all I needed.  Thanks for the good pages tho!

---

### Post by itsols on 2011-12-26
Hi,

You may have solved your NEED for file transfer but this does NOT solve the problem of adding users. I am trying to create multiple accounts on my LAN server so that different users can be given restricted access to folders in /var/www.

As far as I see, this problem is NOT solved :(

Has anyone found a way to fix the error below?

htpasswd: cannot create file /etc/vsftpd/passwd

Any ideas are really appreciated.

FYI, the following link does not work:
[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/)

Thanks!

---

