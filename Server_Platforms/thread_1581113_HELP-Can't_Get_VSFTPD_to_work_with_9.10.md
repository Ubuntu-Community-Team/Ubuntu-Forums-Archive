---
title: "HELP-Can't Get VSFTPD to work with 9.10"
date: 2010-09-24
forum: Server Platforms
---

### Post by mu2pilot on 2010-09-24
I am building a new server on Rackspace Cloud.  When they create an instance, it is a raw install.  I have several other instances running Ubuntu 10.04 with vsftpd running just fine.  But I have an app that doesn't like php 5.3 so I created a new server instance with Ubuntu 9.1 and php 5.2.

Here is my problem...  I install vsftpd EXACTLY the same way I've installed it dozens of times on Ubuntu 10.04.  But when I try to access it, I get an ERROR 500 "vsftpd: cannot locate user specified in 'ftp_username':ftp.  I'm SURE I'm using a valid username & password.

I've been trying to figure this out for several hours.  PLEASE HELP!

TIA.

mu2pilot

---

### Post by mu2pilot on 2010-09-24
Ok, I figured out the problem.  In the fresh Ubuntu installation with no user accts (besides root), I was adding the user acct "ftpadmin" before installing vsftpd.  It didn't like that.  When I installed vsftpd and THEN create the ftpadmin acct, it works.

At least it works on 10.04.  I had other issues installed vsftpd on 9.1.  I decided to go with 10.04 and downgrade php5.

---

