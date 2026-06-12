---
title: "Need FTP help"
date: 2013-07-20
forum: Server Platforms
---

### Post by jbguydude on 2013-07-20
I have looked everywhere to figure out how to restrict users to their directories.

All the things I have tried either broke my server to where I could no longer login to SSH or just did not do what it was suppose to.

What I need is help creating FTP users and only allowing them to look into a specific directory. 
The directory does not have to be /home/user I just need it so they can not leave that directory.

I have Ubuntu 12.04 LTS 64-bit

I am on a fresh install. Only thing I have done is install java and some game server files.

---

### Post by Mouldy_19 on 2013-07-30
which ftp server are you using? if its vsftpd then take a look at  [https://help.ubuntu.com/10.04/serverguide/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/ftp-server.html)

> Securing FTP
There are options in /etc/vsftpd.conf to help make vsftpd more secure. For example users can be limited to their home directories by uncommenting:

chroot_local_user=YES
You can also limit a specific list of users to just their home directories:

chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
After uncommenting the above options, create a /etc/vsftpd.chroot_list containing a list of users one per line. Then restart vsftpd:

sudo /etc/init.d/vsftpd restart

---

### Post by CyberCam on 2013-07-31
I suggest you use proftpd and webmin. It's very simple to do!

---

### Post by LHammonds on 2013-07-31
I have a step-by-step tutorial on how to setup FTP over SSL using vsftpd and covers how to confine users to their upload folders.

Here is the link, which is also in my sig: [How to Install an FTP over SSL Server (FTPS)]("http://www.hammondslegacy.com/forum/viewtopic.php?f=40&t=197")

---

### Post by JoshUK on 2013-07-31
nice tutorial, how do you add FXP?

---

