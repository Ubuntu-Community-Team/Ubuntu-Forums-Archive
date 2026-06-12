---
title: "apache webserver"
date: 2008-05-13
forum: Server Platforms
---

### Post by gishaust on 2008-05-13
Hi everyone,

I have a friend that uses my web server for their web page. I am sick of putting pages in is directory for him. I need to know how to create a situation so that he can http or https access to is directory with a user name and password or something equivalent? 

All I want to do is research this but I don't now what terms I am looking for. 


Gishaust

---

### Post by johnwillis on 2008-05-13
The easiest way to do this in my experience is to set up FTP access on your server. (Or SFTP for secure transfer)

You can then create a user account on your server, grant r+w privilages to the directory and set that as his home folder.

Look into VSFTP and once you've installed it edit /etc/vsftpd/vsftpd.conf

Make sure 

WRITE-ENABLED = TRUE/YES

LOCAL-ENABLED = TRUE/YES

Otherwise he will not be able to log in or write files.

If you need any further help just ask.

-J

---

### Post by gishaust on 2008-05-13
thanks for your help and direction.

---

### Post by windependence on 2008-05-14
An alternative (maybe a bit more secure) would be to create him an account and have him use WinSCP to push the files. That's how I do mine. he can have his dev files on his Windows machine and just drag them to the server directory.

-Tim

---

