---
title: "SFTP Chroot / AD Auth solution?"
date: 2009-06-04
forum: Server Platforms
---

### Post by ksudbury on 2009-06-04
I need a secure way to transfer files over the Internet, my original idea was Proftpd & TLS SSL in a chroot which was working fine with stand Linux users... However... My server authenticates against a Windows 2003 Active Directory server for it's system-auth accounts (rank, I know but it works), it does with with winbind. But Proftpd does not seem to want to work with it... 

The only option  I can see is to use Proftpd mod_ldap which I have tried to do but I have to admit I am failing to make it work (which is frustrating!). 

So if anyone else has any ideas on how I can get this to work I am open to suggestions. 

My requirements are: 

- Secure / uses encryption 
- Chroot / jails users into home dir's 
- Will authenticate using system-auth or will auth against LDAP/Active Directory 


Thanks in advance!

---

### Post by Zeon100 on 2011-03-10
Hey there,
I run a similar setup with a Ubuntu 10.10 SFTP server authenticating against Active Directory. The best way to do this is to use Likewise Open, it makes it a breeze. Then everything else is like setting up a normal Chroot jail as Open SSH and ProFTPd just see users authenticating via AD details as local users thanks to Likewise.

---

### Post by Lars Noodén on 2011-03-11
You can get SSH to work with Pluggable Authentication Modules (PAM).  Those should authenticate to legacy SSO. 

From there, SSH / SFTP can provide the [chroot SFTP environment](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Chrooted_SFTP-Only_Accounts) you need, with almost no effort.

---

### Post by oneloveamaru on 2011-11-02
Only problem is, when using SFTP and Likewise, you can't chroot. Likewise doesn't like it.

[http://www.likewise.com/community/index.php/forums/viewthread/1056/](http://www.likewise.com/community/index.php/forums/viewthread/1056/)

---

