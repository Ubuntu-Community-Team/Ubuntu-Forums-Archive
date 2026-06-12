---
title: "openssh server instead of an FTP server?"
date: 2007-09-14
forum: Server Platforms
---

### Post by bone2006 on 2007-09-14
Just recently I got the ubuntu server up and running and I'm loving it.  I was going to install VSFTPD for an FTP server, but I've been using filezilla and selecting SFTP and I'm able to transfer files just fine.

I'm not sure if there's any downfalls of just using the openssh as an SFTP server?  But I wanted to give access to one other person, in which they can upload/download and do what they want in their home directory, but I do not want them to have sudo/root access. Is this possible and if so how?

Thanks in advance

---

### Post by bone2006 on 2007-09-14
I was thinking about doing something like this [http://tinyurl.com/2ozwvj](http://tinyurl.com/2ozwvj) , but wanted to make sure the person doesn't have access to other directories.  It doesn't matter if they can see them, but want to make sure that important directories that requires root that they would have access.

---

### Post by ruibernardo on 2007-09-14
Hi bone2006,

> **bone2006 said:**
> Just recently I got the ubuntu server up and running and I'm loving it.  I was going to install VSFTPD for an FTP server, but I've been using filezilla and selecting SFTP and I'm able to transfer files just fine.

I'm not sure if there's any downfalls of just using the openssh as an SFTP server?  But I wanted to give access to one other person, in which they can upload/download and do what they want in their home directory, but I do not want them to have sudo/root access. Is this possible and if so how?

Thanks in advance

You can use VSFTPD (or proftpd) to do it. To use VSFTPD with [FTPS]("http://en.wikipedia.org/wiki/FTPS"), you can take a look at [Howto: Easy FTP with vsftpd]("http://ubuntuforums.org/showthread.php?t=518293"), you can chroot the user and use [FTPS]("http://en.wikipedia.org/wiki/FTPS") to login.

If you will use openssh as a file server and want to upload files through [SFTP]("http://en.wikipedia.org/wiki/SSH_file_transfer_protocol") in ssh, with chroot users (no shell, no ssh console to those users), take a look at [Howto: Easy SFTP and chroot SFTP with Scponly]("http://ubuntuforums.org/showthread.php?t=451510").

But there might be other options out there :popcorn:

EDIT: I was erroneously calling SFTP to FTPS. Both use encryption, but with different protocols.

---

