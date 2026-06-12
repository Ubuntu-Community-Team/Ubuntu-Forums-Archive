---
title: "copying files from FTP to server but get permission denied"
date: 2007-12-18
forum: Server Platforms
---

### Post by kustomjs on 2007-12-18
Hi Guys
I am getting this error when I try to copy my files from cd to my webserver and I am using WinSCP to transfer files over to my server
"Copying files to remote side failed. index.php: Permission denied"

---

### Post by kustomjs on 2007-12-18
can somebody please help!

---

### Post by kustomjs on 2007-12-25
I take it there is NO HELP WHAT SO EVER IN THIS FORUM?

---

### Post by freebeer on 2007-12-25
I suspect that you haven't received a reply because it's not quite clear what you're trying to do, exactly.

Are you copying files off of a CD on a Windows machine to an Ubuntu web server via FTP?  You're running Apache?  and an FTP server on Ubuntu?

Typically an FTP user belongs to a different group (say "ftp-user") than the permissions set up for Apache (say, "var-www").  So basically, your FTP user doesn't have permission to write to the folders under Apache.  Or at least that's what appears to be the problem.

---

### Post by kustomjs on 2007-12-25
then how do I fix that problem? and yes I am running LAMP on my Ubuntu 7.10 and when I login to FTP I am already login as a SU

---

### Post by kustomjs on 2007-12-30
can somebody please help me to get this issue fixed?

---

