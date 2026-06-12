---
title: "Pure Ftpd Mysql"
date: 2017-08-21
forum: Server Platforms
---

### Post by patdundee on 2017-08-21
Hi Guys
I have been using Pure Ftpd Mysql for some time now. 
I have just completed a fresh install of Ubuntu Server 16.04 on a new server. I am having problems with Pure Ftpd Mysql running as a standalone with the mysql database

Pure Ftpd installed correctly, ftp config for DB set correctly, Mysql Database correct. added a user with password. No Quota limit and No Bandwidth Limit (Do not use them)

Start up the ftpd server and I can connect via command line in SSH as my root username and password

Try to connect from a remote ftp client and i get one of two errors.
1) The server refused the connection
2) when it allows the connection it fails on the password 

I can connect to the mysql seerver from a remote script on a different server so I know Mysql is allowing connections

For some reason i beleive that Ftpd server is not running and authenticating via the mysql database and i cannot see to find out why.

Has anyone else had this issue

pure-ftpd-mysql and pure-ftpd-common have been installed via apt with no issues

all php amd mysql files are all installed and correct.

Many thanks

P

---

