---
title: "How to enable remote logins on a server?"
date: 2010-03-11
forum: Server Platforms
---

### Post by poltr1 on 2010-03-11
I'm in the process of deploying an Ubuntu (Karmic) server to my organization.  it's replacing a Windows 2003 server.  

I'd like to set up the server so that I can remotely login to perform server management, instead of having an attached monitor and keyboard to the server.  I want to use ssh, rlogin,and ftp.

What configuration files do I need to tweak, and what needs to be tweaked?

Thanks in advance.

---

### Post by koenn on 2010-03-11
you install openssh-server on the server, it will give you a remote shell and you can do file transfers with it

---

### Post by undecim on 2010-03-11
rlogin and ftp both have serious security flaws (namely the fact that they both send passwords in clear text)

SSH will do just as well and is far more secure. You can also use FTP securely over SSH (with a client like filezilla)

---

### Post by Jive Turkey on 2010-03-11
If you want to have access like rdp on windows you can either use some flavor of VNC. The standard implementation is not very secure however.  The company nomachine has a free version available of thier nx client/server that is better than anything in the repositories. You should check the license before installing for an organization though. 

proftp is probably the best option if you want to use ftp.  If you want to do standard windows file sharing you'll want to use samba.

ssh supports sftp which is much more secure than regular ftp.  If you have ubuntu on your client machine you can bookmark links to the server using sftp and transfer files that way.  From a windows client I reccomend filezilla which can do sftp from windows.

---

### Post by Samatva on 2010-03-11
I always use Webmin for most server admin tasks - it's web-based, so reduces the number of errors and and delays from command line. There's also a "Usermin" module if you need to give well-controlled access to others. You can set it to require SSL, which is good enough security for my purposes...

---

