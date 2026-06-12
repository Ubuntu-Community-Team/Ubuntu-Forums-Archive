---
title: "proFTPd: help with proftpd.conf"
date: 2010-12-29
forum: Server Platforms
---

### Post by nats463 on 2010-12-29
I have to make an ftp server for a client.  I was ordered the first time  to use a GUI, and make it easy for the client to manage.  I ran into  problem after problem, and blew out the server, redoing it entirely  command line.  Now, the FTP works fine, and how I want it. 

My problem is this, I need to add a "superuser" so the client can log  into the FTP server, and add/delete files or make/remove directories as  needed.  I am not sure how to do this.  I have not added "users" to the  proftpd.conf file itself, and all of my FTP clients are users on the  system, without a shell.  

Any suggestions?

---

### Post by Whyzer on 2011-01-01
You can configure the /etc/proftpd/proftpd.conf to create a user who has access to the folders you want them to and give them read / write permissions to do so within their ftp client program like Filezilla. 
The only hiccup I see with this is file ownership, and that may be solved by adding the group name for proftpd (nogroup, or whatever you have specified in proftpd.conf) to the directories in which they need to work using the chown command.
I'm still somewhat a noobie at linux, but I think that's how i'd approach it.

---

### Post by jgedeon on 2011-01-01
> **nats463 said:**
> I have to make an ftp server for a client.  I was ordered the first time  to use a GUI, and make it easy for the client to manage.  I ran into  problem after problem, and blew out the server, redoing it entirely  command line.  Now, the FTP works fine, and how I want it. 

My problem is this, I need to add a "superuser" so the client can log  into the FTP server, and add/delete files or make/remove directories as  needed.  I am not sure how to do this.  I have not added "users" to the  proftpd.conf file itself, and all of my FTP clients are users on the  system, without a shell.  

Any suggestions?


Look into proftpd limits to achieve what you need.  Adding users is just the same as adding user to the system.

groupadd ftpusers
useradd -md /ftp/dir/ -s /bin/false -G ftpusers superftpusername
useradd -md /ftp/dir/sub -s /bin/false -G ftpusers normalftpusername

---

