---
title: "Unified user access control"
date: 2011-10-21
forum: Server Platforms
---

### Post by Mr.Carramba on 2011-10-21
Hi,

I have come to some productivity issues. Consider you have a server with several users, then you have a restricted web directories, svn, ssh, ftp, trac etc... 
Some of them can be managed with the unix user name, other don't (or probably I just don't know how).

So my question would by is it possible to set up a unified user management control? For example if I have local user lazy, his/her log in to unix could be used to control access to the web directories and svn.

I realize that it is convenient to have separate user access files to svn and http, but it would be much  more easy to handle if it would be possible to set up above described way. I guess I am not firs lazy sysadmin so there should be so solution, but I have not managed to find it. 

Looking forward to your responses 

Mr.C

---

### Post by Lars Noodén on 2011-10-21
> **Mr.Carramba said:**
> So my question would by is it possible to set up a unified user management control? 

One way might be to use [Kerberos](http://www.google.com/search?hl=en&q=kerberos+-site%3Amicrosoft.com&btnG=Search) for authentication.  For some services, it is very easy to tie in.  I don't know what's available in that regard for Ubuntu, but I've done Kerberos before with Debian, OS X and OpenBSD.  For the software, there are two variants, MIT and Heimdal, but both support the same protocol and thus are interoperable.  Apache used to have an authentication module for it and for Linux there is PAM.

---

### Post by Mr.Carramba on 2011-10-21
> **Lars Noodén said:**
> One way might be to use [Kerberos]("http://www.google.com/search?hl=en&q=kerberos+-site%3Amicrosoft.com&btnG=Search") for authentication.  For some services, it is very easy to tie in.  I don't know what's available in that regard for Ubuntu, but I've done Kerberos before with Debian, OS X and OpenBSD.  For the software, there are two variants, MIT and Heimdal, but both support the same protocol and thus are interoperable.  Apache used to have an authentication module for it and for Linux there is PAM.

I thought about it but kerberos is intended (at least considering the ammount of work needed to set up...) for big groups. Therefore, it is quite strange that there is no some simpler way to manage system.

---

