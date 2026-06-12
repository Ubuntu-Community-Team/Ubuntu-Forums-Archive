---
title: "FTP script"
date: 2011-09-16
forum: Server Platforms
---

### Post by asai on 2011-09-16
Hi

I'm trying to make a script that downloads all jpg files from my FTP server.
Want to use ncftp command for this.

Anyone knows of the command for doing this?

---

### Post by asai on 2011-09-17
No suggestions??

---

### Post by HermanAB on 2011-09-17
Here is an exaple of FTP scripting:
[http://www.aeronetworks.ca/howtos/windows-backup.html](http://www.aeronetworks.ca/howtos/windows-backup.html)

---

### Post by asai on 2011-09-17
That example is for DOS, I'm obviously running Ubuntu.
When I run ftp -h there is no -s option...

---

### Post by konsole on 2011-09-18
wget is a better tool to download jpgs from your webserver using a script. very easy to use, check out the manpage.

---

### Post by asai on 2011-09-18
I solved it using ncftpget. :p

---

