---
title: "vsFTPd and user permissions."
date: 2006-03-02
forum: Server Platforms
---

### Post by Xenom on 2006-03-02
Hello,

I've installed vsFTPd and got it running. I created a system user named xenom, and the user is able to connect to the FTP server.

But, how/where do i set the user permissions?
I want xenom to use the home directory /var/user1/
and the user must be locked in that directory (chrooted?), in this directory the user has all priveleges, upload, write, edit etc. etc. (chmod? chown?)

If i login now, i am in /home/xenom and have no privileges to do anything, only read.

I've played with this a couple of days now, and can't get it working.

Thanks in advance!
Xenom.

---

### Post by colo on 2006-03-02
Read the manpage of vsftpd.conf for your chroot-related questions, and those regarding write-permissions.

To change the initial directory vsftpd places "xenom" after he logs in, you've got to edit /etc/passwd accordingly - you need to assign a new home-directory for "xenom", in your case "/var/user1". Of course, you need to make sure that this home-directory is set up to allow xenom to write and read it. He should also be owner of the directory.

---

### Post by Xenom on 2006-03-03
Yes, got it working just fine now.

I used the moduser command to set the home directory.
Then chown, to give the user his permissions.

And i forgot to enable the option 'write access' in vsftpd.conf

---

