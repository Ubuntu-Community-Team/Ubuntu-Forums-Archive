---
title: "FTP user and group to Apache?"
date: 2010-06-13
forum: Security
---

### Post by spongypants23 on 2010-06-13
Hi gang,

What would be the effect of setting ProFTPd's user and group to the same user and group that Apache use? Are there any security risks in doing this, or is this safe to do?

---

### Post by Bachstelze on 2010-06-13
[img]http://iori.fkraiem.org/stuff/why.jpg[/img]

Can't really tell without knowing what you intend to do this for.

---

### Post by Ryan Dwyer on 2010-06-14
The files Apache reads are by default owned by root. Apache can only read them unless you change the permissions.

If you upload something and make it owned by www-data, Apache will be able to change the contents of it. If you have exploits in your code this could lead to a compromise.

Doing what you suggested isn't recommended. Apache should have readonly access to what it needs to read, and write access ONLY to what it needs to write (eg. dynamic files like cache).

---

### Post by spongypants23 on 2010-06-14
> **Bachstelze said:**
> Can't really tell without knowing what you intend to do this for.

I want to set up so that I'm a web host for some friends, where they have a virtual user in ProFTPd (in MySQL), and are chroot jailed to their virtual homedir, in the Apache folder (which is /home/web/www/). I want the home dirs to be accessible by apache, as well as any files uploaded bia FTP. Which is why I figured I'd set the FTP user to the same as apache.

---

### Post by Ryan Dwyer on 2010-06-14
Enable the userdir module for Apache (sudo a2enmod userdir). Create the users on your system so they have folders in /home. Create a public_html directory inside each user's home directory. Put a test index.html file in one of them.

Then browse to [http://servername/~username/](http://servername/~username/). The index page should load.

For chrooting FTP, I have PureFTPd installed. echo "yes" > /etc/pure-ftpd/conf/ChrootEveryone.

---

