---
title: "Find FTP login details for my VPS server (with vsftpd)"
date: 2015-01-17
forum: Server Platforms
---

### Post by Dale_P on 2015-01-17
Hello,

I've got a new computer and have lost the FTP login details that were saved by Filezilla on the old computer.

I didn't write the login details down and now I'm trying to find out what the login details are from the command line (logging in via SSH).  It seems vsftp is installed, and there is a file in /etc/vsftpd.conf (but no  /etc/vsftpd folder).  As I set up the server in June, I may have used another FTP program, but not sure what this would have been?

I've searched for ages on Google to 'list FTP users' but no luck (despite the fact this would surely be a common problem?!).  Should I just remove vsftpd, then reinstall and start again from scratch?  Or is there a way to list FTP users - assuming I did use vsftpd ?

Many thanks for your help in advance...

---

### Post by Dale_P on 2015-01-17
This post helped... I'm now able to log-in as a root user: [http://askubuntu.com/questions/354178/what-is-ftp-username-and-password-for-vsftpd](http://askubuntu.com/questions/354178/what-is-ftp-username-and-password-for-vsftpd)

---

