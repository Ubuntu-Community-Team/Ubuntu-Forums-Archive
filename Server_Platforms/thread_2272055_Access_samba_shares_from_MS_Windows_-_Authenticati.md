---
title: "Access samba shares from MS Windows - Authentication via MYSQL"
date: 2015-04-03
forum: Server Platforms
---

### Post by rainer8 on 2015-04-03
Hi @ all.

I am new to this board and hope you can help me.

I am setting up a new Ubuntu server 14.04.2 x64 and have a problem, I don't get solved by myself.

I installed Apache2, MySQL, PHP, phpMyadmin and samba. I created a SQL database and a table which includes usernames and encrypted passwords. 

These login accounts I am using for authentication access to a website (require valid-user etc). Now I want to" connect" samba with this sql database.

I don't want to create unix users on my systems. I just want that samba check if the (on the Windows system) entered username and password belongs together and than the user should be able to get access to the samba shares. No changing password via Windows ect. should be possible. So (I think) I don't need to use PAM, but I might be wrong

I found some links in the internet describing using libnss-mysql-bg, but they don't work. Other tutorials use "passdb backend = mysql" ect but they don't work either.

Is there a chance how I can realize what I described above?

Best regards,

Rainer

---

### Post by bab1 on 2015-04-04
> **rainer8 said:**
> Hi @ all.

I am new to this board and hope you can help me.

I am setting up a new Ubuntu server 14.04.2 x64 and have a problem, I don't get solved by myself.

I installed Apache2, MySQL, PHP, phpMyadmin and samba. I created a SQL database and a table which includes usernames and encrypted passwords. 

These login accounts I am using for authentication access to a website (require valid-user etc). Now I want to" connect" samba with this sql database.

I don't want to create unix users on my systems. I just want that samba check if the (on the Windows system) entered username and password belongs together and than the user should be able to get access to the samba shares. No changing password via Windows ect. should be possible. So (I think) I don't need to use PAM, but I might be wrong

I found some links in the internet describing using libnss-mysql-bg, but they don't work. Other tutorials use "passdb backend = mysql" ect but they don't work either.

Is there a chance how I can realize what I described above?

Best regards,

RainerThe Samba user database for share authentication is limited to tdb or ldap.  The libnss databases (e.g mysql) are used for Linux user authentication.  Any references you may see are for earlier versions of Samba (v2 and v3).   Ubuntu 14.04 and later uses Samba v4.

The Samba server uses a tdb database to authenticate access the share only.  The local passwd/shadow files are for authentication  of the Linux user.  Samba does not provide Linux permissions authorization.  You need both for Samba to work correctly.  PAM authentication can use the local user mechanism or a DC LDAP database.  The PAM Samba module manages the Linux to Samba user password coordination.

Most of what is written about LDAP and Samba is for Domain Control not for a single machine (standalone) Samba file server.  You would need 2 hosts to use LDAP for Samba authentication as Samba v4 LDAP will not work with Samba v4 file servers (shares) at this time.

You will find much more information about these issues at [samba.org ]("https://www.samba.org/") or the [Samba mailing list]("https://lists.samba.org/").

---

### Post by rainer8 on 2015-04-04
Hello BAB1,

thank you very much for your fast reply. This is not the answer I wanted to hear, but now I kno that I was working into the wrong direction.

Best regards,

Rainer

---

### Post by LHammonds on 2015-04-06
I know you said you don't want to create users on your system but you might be able to setup a bash scripts that creates the users in the operating system from what is in your database but configure them in such a way that they cannot login via SSH/Telnet if that is what you are worried about.

---

### Post by bab1 on 2015-04-06
> **LHammonds said:**
> I know you said you don't want to create users on your system but you might be able to setup a bash scripts that creates the users in the operating system from what is in your database but configure them in such a way that they cannot login via SSH/Telnet if that is what you are worried about.
I believe that if the user that has no login shell (e.g. /bin/false or /usr/sbin/nologin set in the passwd file) the user will not be able to use ssh or telnet.  For sure you can't log in locally.

---

### Post by amerinde on 2015-04-07
here, look here...  [https://www.samba.org/samba/docs/man/manpages/smbpasswd.8.html](https://www.samba.org/samba/docs/man/manpages/smbpasswd.8.html)

---

### Post by rainer8 on 2015-04-12
Thank you to all of you.

I have spent this weekend with creating a shell script to create a linux user and a samba user and build a little php backend which start this script.

This is not the way I usually wanted to have, but I can handle everything I need with it.

Best regards,

Rainer

---

