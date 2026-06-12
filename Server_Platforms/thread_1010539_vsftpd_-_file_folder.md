---
title: "vsftpd - file folder"
date: 2008-12-13
forum: Server Platforms
---

### Post by Mechina on 2008-12-13
I have set up a FTP server with vsftpd on a 32 bit Ubuntu Server 8.10 and it works fine however, the folder where all the files are stored is "/home/ftp" (default) and there's only 69gb of space at "/home" so I want to make that folder be on a external hd ("/media/ext").
I've tried binding the hd to that folder:
```
sudo mount --bind /media/ext /home/ftp
```
But when I try connect to the server (from a browser) I get a prompt for a username and password and even if I enter the root user/pass I get an error saying "child died" and the browser loads an empty blank page.
I've also tried to add this to "/etc/vsftpd.conf"
```

anon_root=/media/ext

```
But I get the same thing as when I try and bind it. :( 

Anyone have an idea on how to make this work? Thank.

---

