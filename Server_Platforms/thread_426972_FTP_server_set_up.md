---
title: "FTP server set up"
date: 2007-04-29
forum: Server Platforms
---

### Post by ACF1 on 2007-04-29
OK, I am sorry if this has already been posted, but I have searched and searched and read more stuff, and still haven't figured out how to set an FTP server up.  So if I could get some help, that wound be great.  Probably something step-by-step. because right now, I am not feeling to smart on the whole thing... *smile*  Thanks everyone!

---

### Post by chalex on 2007-04-29
You can type "sudo apt-get install vsftpd" and then put some files into /var/ftp

You can read the documentation in /usr/share/doc/vsftpd and edit the file vsftpd.conf in /etc

---

### Post by nix4me on 2007-04-29
Try a search on the howto forum.  Plenty of howto's for ftp servers.

I recommend proftpd.

nix4me

---

### Post by nonewmsgs on 2007-04-29
thanks for the recomend.

---

### Post by Aberrix on 2007-04-30
+1 for proftpd

---

### Post by coxy on 2007-05-01
vsftpd is a good ftp server. There is a good howto on the Gentoo wiki.

[http://gentoo-wiki.com/HOWTO_vsftpd](http://gentoo-wiki.com/HOWTO_vsftpd)

As said above, you just need to install the software first.

```

sudo apt-get install vsftpd

```

vsftpd is very fast and very secure.

---

### Post by kathe on 2007-05-01
want to setup FTP Server thn go through the link

[http://linuxera.com/content/view/235/2/](http://linuxera.com/content/view/235/2/)


kathe

---

