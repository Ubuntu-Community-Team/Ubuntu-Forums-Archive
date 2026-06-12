---
title: "SHA512 password hashing for FTP servers using mysql database"
date: 2015-01-14
forum: Server Platforms
---

### Post by cyclobs on 2015-01-14
Hi guys,

I'm currently trying to set up an ftp server that uses virtual user accounts which are shared with an web login. I currently have vsftpd set up and it is working fine with the test database but i would like to use sha512 hashing for the passwords instead of the default MD5. As far as i know pem_mysql supports sha512 but i can't find how to make it hash the passwords.

Could i use pem_exec to run my own hashing script and then send the hashed password back to pem_mysql? This is more so i can make sure both services will be able to use the same password hashes plus any salts i add to the script.

I also had a look into configuring pro-ftp thinking it might have better support for this kind of thing but i haven't had much luck with this also.

thanks

---

### Post by TheFu on 2015-01-15
FTP sends passwords as plain text without any encryption, so why bother?
[Better to dump FTP and use sftp.]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp")

---

### Post by cyclobs on 2015-01-19
why? Because you can encrypt FTP with SSL. The devices that will be logging into the server doesn't support SFTP, and i rather not have a web facing database with plain text passwords in it.

Either way looks like i'm going to have to build my own pam module that will dump the password to a script

---

### Post by Habitual on 2015-01-20
> **cyclobs said:**
> why? Because you can encrypt FTP with SSL. The devices that will be logging into the server doesn't support SFTP, and i rather not have a web facing database with plain text passwords in it.

Either way looks like i'm going to have to build my own pam module that will dump the password to a script

sftp = ftp over ssh
If the devices  can ssh into the server, the server supports sftp.

---

