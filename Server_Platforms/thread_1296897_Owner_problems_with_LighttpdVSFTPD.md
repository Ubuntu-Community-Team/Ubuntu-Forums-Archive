---
title: "Owner problems with Lighttpd/VSFTPD"
date: 2009-10-21
forum: Server Platforms
---

### Post by Hoox on 2009-10-21
When 9.10 is released I plan on replacing my current Debian Apache/Proftpd with a Ubuntu Lighttpd/VSFTPD setup.

I installed Ubuntu 9.10 beta server on my test machine.
Lighttpd is being run by the default user www-data:www-data. 
The problem is, that the files uploaded by users in VSFTPD is owned by that user and Lighttpd is only able to serve files owned by www-data:www-data.

How do I get around this without having to do a chown -R www-data:www-data every time a user has uploaded new files?

---

### Post by Lars Noodén on 2009-10-21
Are you sure it is an ownership issue and not a matter of missing read privileges? 

How about setting the umask for the vsftpd users to be 0022, or anything ending in "2"?  That way the files created by the users are readable by everyone, as it should be for web pages.

---

### Post by Hoox on 2009-10-22
Lars Noodén, you were absolutely right. I overlooked that one. Thanks alot!

I got another small vsftpd problem. Maybe someone know the answer to that too...
I'd like to create my ftp users for my lighttpd vhosts like this:
```
sudo useradd -d /var/www/domain.com -s /usr/sbin/nologin username
```
That way they can only use ftp and not login from ssh etc.

To enable the users to login from vsftpd I would add check_shell=NO to my vsftpd.conf. 
Problem is, that it doesn't help. Users are still not able to log in. 
 
If I add users like this:
```
sudo useradd -d /var/www/domain.com -s /bin/bash username
```
They are able to login from ftp but also from ssh...

---

### Post by Lars Noodén on 2009-10-25
I'm hesitant to encourage FTP accounts, the usernames and passwords get passed unencrypted and if valid for other parts of the system allow unwanted 'guests'.  

If you have the openssh server already installed, as you say, then you also already have its sftp subsystem available.  Using that instead of ftp, would eliminate the need for maintaining so many extra services and configurations.  And setting up sftp-only accounts is very easy.  

Just as a safety, make the sftp accounts like you did above, but perhaps with /bin/false as the shell.  Make them members of a special group to designate them as being restricted to sftp.

```

sudo useradd --home /var/www/domain.com/ --shell /bin/false \
     --groups sftp-only username

```


```

# from tail end of /etc/ssh/sshd_config
Match Group sftp-only
   ChrootDirectory /var/www/domain.com/
   AllowTCPForwarding no
   X11Forwarding no
   ForceCommand internal-sftp

```

---

### Post by Hoox on 2009-11-05
Lars, sorry about the late reply.

Sounds like a good idea with the sftp solution instead.
I'm gonna try out on that option.

Thanks alot for your help!

---

### Post by dutislt on 2009-11-05
I have also one solution for you. Run vsftpd as normal(secure is you need chroot, set allowed ftp users(don't let users like root to login!)). Then edit your sshd_config (/etc/ssh/sshd_config) and add following:

AllowUsers allowed_user_names_that_you_let_ssh

then restart sshd with:

sudo /etc/init.d/ssh restart

I like to control users who connects to my server :) I add them manually :D

---

### Post by Lars Noodén on 2009-11-05
> **Hoox said:**
> Lars, sorry about the late reply.

Sounds like a good idea with the sftp solution instead.
I'm gonna try out on that option.

Thanks alot for your help!

No worries.  SFTP surprisingly configurable and can allow some things for some groups but not for others.  It turns out that SFTP is also the back-end for SSHFS, so if you have a setup you like using SFTP, you can then mount it as a folder and access it the same as you would local files.  Both methods even work with keys.

---

