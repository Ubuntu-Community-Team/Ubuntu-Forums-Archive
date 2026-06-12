---
title: "[SOLVED] New server setup"
date: 2008-03-13
forum: Server Platforms
---

### Post by CyberDean on 2008-03-13
Hi everyone.  First server setup with Ubuntu "Gutsy" 7.10, 64 bit, and first in about 30 years.  So, needless to say, at this point, I don't know what I'm doing.  I have been reading and researching the Ubuntu Forums, the "HowTo's" and everything else I could find for the last 2 1/2 weeks, and think I have just confused myself even more.  :confused:

Here is what I have done.

     1.  Installed the server software to include everything except the mail server package.

     2.  I want to start the server as a "file server".  First, within my local network at home with 2 PC's dual booting Gutsy and XP, 1 PC single boot Gutsy.  I have a DSL modem/router attached to the server, I can have 1 or 2 connections.  The DSL modem is also connected to a Linksys WRT54G wireless router where the PC's are connected.

What needs to be done to allow file transfers from the PC's, in Gutsy and XP, to the server and back?

What needs to be done to allow the file transfers across the internet?

What I need now is more generalized steps that I can use to search the forums, "HowTo's", and internet to get each step completed.

I am at work right now, but will read all responses this evening or tomorrow.

Thanks in advance.

---

### Post by HermanAB on 2008-03-13
Essentially, there are three ways to serve files:
1. FTP
2. NFS
3. SMB

FTP is by far the easiest.
NFS is almost as easy and requires only about two lines of configuration, but you need to specially install NFS support in Windows - it is not part of the default install.
SMB is "Windows Networking" and is by far the most difficult method.

For information on Samba, go to [http://samba.org](http://samba.org) and read the Official Howto.

Hope that helps!

Herman

---

