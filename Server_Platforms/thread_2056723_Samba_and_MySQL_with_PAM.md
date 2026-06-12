---
title: "Samba and MySQL with PAM"
date: 2012-09-12
forum: Server Platforms
---

### Post by bradhawk08 on 2012-09-12
I have been trying for two days to get a mysql database set up that can be used for authenticating users for accessing samba shares.

I have attempted to use the following two methods and neither seems to work:

[http://www.freebsddiary.org/samba-pam.php]("http://www.freebsddiary.org/samba-pam.php")
[http://www.gentoo-wiki.info/HOWTO_Samba_with_Mysql]("http://www.gentoo-wiki.info/HOWTO_Samba_with_Mysql")

Can someone please guide me as to how I can get this to work?

Thanks so much for any help in advance!!

EDIT (9/14): So I figured out that the libpam-msyql module was not installed and also that I think my pam configuration needs to be in /etc/pam.d/samba instead of /etc/pam.conf. But I still cannot get it to work. Now I get an error that says something like "Server requested LM password but "client plaintext auth = no" or "client nvtlm2 auth = yes".

Thanks!

---

### Post by SeijiSensei on 2012-09-14
Try adding "client plaintext auth = yes" to the [global] section of smb.conf and restarting Samba.  Any better?

---

### Post by bradhawk08 on 2012-09-25
That did not fix it. I think the issue has something to do with the difference between authorization and authentication. 

I started down this path:

[http://www.spencerstirling.com/computergeek/mysqluser.html]("http://www.spencerstirling.com/computergeek/mysqluser.html")

But stopped mainly because I did not have these two files:
/etc/nss-mysql.conf
/etc/nss-mysql-root.conf

Can anyone here tweak that step by step instructions to work for samba and Ubuntu?

It talks about putting changes in the common-* files, but I thought these should go in /etc/pam.d/samba.

But there is also a /etc/pam_mysql.conf file along with /etc/pam.conf...  How do I know what everything is doing? I can't seem to get any of the pam_mysql debugging/logging to happen or at least I can't find it.

This is really frustrating! Has anyone ever tried to do this or does everyone just use the /etc/passwd and /etc/shadow files? 

I like the idea of using mysql because I understand that much more than having to remember commands to add, edit, remove system users and system groups. Plus mysql seems like an easy way to understand which users have access to which services and directories. 

I can use mysql for controlling access to web server pages and also FTP and both those methods are straight forward why is samba so much more difficult?

Thanks in advance!

---

### Post by redmk2 on 2012-09-25
> **bradhawk08 said:**
> That did not fix it. I think the issue has something to do with the difference between authorization and authentication. 

I started down this path:

[http://www.spencerstirling.com/computergeek/mysqluser.html]("http://www.spencerstirling.com/computergeek/mysqluser.html")

But stopped mainly because I did not have these two files:
/etc/nss-mysql.conf
/etc/nss-mysql-root.conf

Can anyone here tweak that step by step instructions to work for samba and Ubuntu?

It talks about putting changes in the common-* files, but I thought these should go in /etc/pam.d/samba.

But there is also a /etc/pam_mysql.conf file along with /etc/pam.conf...  How do I know what everything is doing? I can't seem to get any of the pam_mysql debugging/logging to happen or at least I can't find it.

This is really frustrating! Has anyone ever tried to do this or does everyone just use the /etc/passwd and /etc/shadow files? 

I like the idea of using mysql because I understand that much more than having to remember commands to add, edit, remove system users and system groups. Plus mysql seems like an easy way to understand which users have access to which services and directories. 

I can use mysql for controlling access to web server pages and also FTP and both those methods are straight forward why is samba so much more difficult?

Thanks in advance!

It appears you have confused the local user databases (passwd and shadow) with the Samba (remote) user database (tdbsam or ldapsam.  These are separate and distinct.

The passwd and shadow files authenticate the local Linux user while the tdbsam or ldapsam databases only authenticate the Samba user.  You do not have to be a Samba user on the local system,  but *you must be a local user **[I]and*** a samba user to be authenticated to as a Samba user (remote user).[/I]  Only then will you have access to the Samba share.

---

