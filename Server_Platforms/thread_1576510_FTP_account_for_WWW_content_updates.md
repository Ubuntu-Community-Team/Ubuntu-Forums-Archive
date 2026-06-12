---
title: "FTP account for WWW content updates"
date: 2010-09-17
forum: Server Platforms
---

### Post by tzok on 2010-09-17
Hi, it's my first post on this forum.

I don't have much experience in Linux administration, but I needed to create a simple www server. It's is installed on a dedicated machine running Ubuntu Server 10.04.1 x64.

I've got a problem with creating and setting ftp account to access /var/www.

I've read that I shall not change the owner nor the access permissions to that folder.

I've also tried changing /var/www permissions but even when I had access I could not modify/overwrite nor delete files which I've uploaded (I could upload and download/view).

Currently it seems to work, but I've chown'ed /var/etc to my wwwuser user account (as I remember originally it was owned by root).

It works but wwwuser must have a shell assigned (/bin/sh or /bin/bash), without it (/bin/false) he cannot log on to the ftp account.

So here goes my question - who should own /var/www, what permission should this folder have and how to make it work using vsftpd? What is local_umask=022 in vsftpd.conf?

---

### Post by Bachstelze on 2010-09-17
> **tzok said:**
> 
I've read that I shall not change the owner nor the access permissions to that folder.

Who told you that? You can very well do it, and there's no problem in doing so.

> So here goes my question - who should own /var/www

It is normally owned by root, and there should be no need to change that. There's no problem with doing it if you want, though.

> what permission should this folder have

It's probably a bad idea to make it world-writable, so either 755 or 775 depending on whether or not you need it to be group-writable.

> What is local_umask=022 in vsftpd.conf?

It means that all uploaded fies will be read- and writable only by their owner (generally theuser who uploaded them). All other users will have read-only access to them.

Now tell us more about your setup. ow many sites? How many FTP accounts? What should they be able and not be able to do? Also, FTP normally sends the passwords in clear text. Have you thought about that?

---

### Post by tzok on 2010-09-17
Server is only for my personal use (at least for now) - mainly for testing new sites, and only its port 80 is exposed to the Internet. So security is not a top-most issue, but I'd like to do this right to learn something.

My personal computer is running on Windows 7 and the server, as mentioned before, runs Ubuntu Server 10.04.1. Server has no console (keyboard nor display), so I have to have an easy way to upload new files to it's www directory from Windows machine.

Server runs standard LAMP Server and additionally has vsftpd for file upload and sshd for bash access.

I feel quite comfortable in administering Windows Server, but Linux is a "black magic" for me, especially if it has only text console.

Could someone tell me - step by step - how to create an user account for ftpd to access /var/www and its subdirectories but not allow to go "above", and uploaded files have "right" permissions for apache.

What group shall 'wwwuser' belong to? And one more thing - I don't want the wwwuser to be able to log in to the shell.

Now when I upload a file via ftp it is owned by wwwuser and has access permissions 644 (why not 755?).

***

And something different - how can I configure a new virtual host, listening on different than standard port 80 and move phpmyadmin and phppgadmin to that vhost?

---

### Post by Bachstelze on 2010-09-17
If you are the only user, the best thing to do it probably to have your website stored in your home directory (e.g. in /home/foo/www) instead of /var/www. Then you can use your normal account to connect via FTP or SFTP.

For virtual hosts, see [https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

---

### Post by tzok on 2010-09-17
OK, but now I've got wwwuser whose home directory is /var/www is something wrong about that?

And three more things:
- how to allow this user only to connect via ftp, without shell access?
- why files uploaded by this user via ftp have access permissions 644 instead of 755?
- how to (where) bind phpMyAdmin to a different vhost?

P.S.
phpMyAdmin is installed from repository via apt-get and automatically configured by the installation script.

---

### Post by Bachstelze on 2010-09-17
> **tzok said:**
> OK, but now I've got wwwuser whose home directory is /var/www is something wrong about that?

No.
> 
- how to allow this user only to connect via ftp, without shell access?

Set /bin/false as its shell and add it to /etc/shells.

> - why files uploaded by this user via ftp have access permissions 644 instead of 755?

Because fies have default permissions of 666, so that you have to explicitly make a file executable if you want to execute it. For a web server, you don't need it.

> - how to (where) bind phpMyAdmin to a different vhost?


You have to create a vhost with the DocumentRoot set to the directory where pma is installed.

---

### Post by tzok on 2010-09-17
Thanks, I didn't know that I need to add /bin/false to /etc/shells.

One more question about permissions - is 644 OK for uploaded files? Shouldn't it be 655?

I disallowet to go wwwuser above /var/www by uncommenting chroot_local_user=YES and chroot_list_file=/etc/vsftpd.chroot_list and I've added my account name to this vsftpd.chroot_list so my user still have ability to go above his home directory, while all other users - don't.

---

### Post by Bachstelze on 2010-09-17
> **tzok said:**
> 
One more question about permissions - is 644 OK for uploaded files? Shouldn't it be 655?

644 is OK, why would you want 655? As I said, you don't need the executable bit.

> I disallowet to go wwwuser above /var/www by uncommenting chroot_local_user=YES and chroot_list_file=/etc/vsftpd.chroot_list and I've added my account name to this vsftpd.chroot_list so my user still have ability to go above his home directory, while all other users - don't.

You don't need chroot_list_file. WIth just chroot_local_user, all users will be chrooted.

---

