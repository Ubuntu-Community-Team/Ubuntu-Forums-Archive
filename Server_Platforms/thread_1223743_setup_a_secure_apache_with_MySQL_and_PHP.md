---
title: "setup a secure apache with MySQL and PHP"
date: 2009-07-26
forum: Server Platforms
---

### Post by cazz on 2009-07-26
Hi
to install Apache, MySQL and PHP is very easy but I trying to find a good step by step that secure it.

I dont know if they are so good secure after they have install.

I dont like to have done something wrong and some hole that make someone can send or even take over the server.


so can someone tell me a good guide or even tell me what I have to think about.

I have work with Apache before but never use it in public just a private network.

---

### Post by cariboo on 2009-07-26
Did you check out the [sticky]("http://ubuntuforums.org/showthread.php?t=1046738") at the top of the page?

---

### Post by hessiess on 2009-07-26
With PHP you rilly need to get it running scripts as seperate users to be sccure (espetily if you are going to heve outher people using the server), Running PHP as CGI with suexec is the easiest way to do this, and the proformance hit isnt that noricable.

---

### Post by cazz on 2009-07-26
well yes I have. I have found some information in "Ubuntu 8.04 Server Guide" and that was nice to read how easy it is to install a Apache server and a little information about security.

I have not found so much information more then file rights and that and I think maybe Apache 2 is very good secure at start.

so I think I going to try install from the guide and the other things I like to have.

---

### Post by cazz on 2009-07-26
> **hessiess said:**
> With PHP you rilly need to get it running scripts as seperate users to be sccure (espetily if you are going to heve outher people using the server), Running PHP as CGI with suexec is the easiest way to do this, and the proformance hit isnt that noricable.

yes that sound intresting.

Is only I that going to use the server but I maybe going to install some script (like a CMS system or something) that have some security problem that I dont know about.

so that you did write about "suexec" is something I going to read a little about.

---

### Post by hessiess on 2009-07-26
> **cazz said:**
> yes that sound intresting.

Is only I that going to use the server but I maybe going to install some script (like a CMS system or something) that have some security problem that I dont know about.

so that you did write about "suexec" is something I going to read a little about.

This blog covers the problem (down at the bottom) and the ways of fixing it: [http://blog.stuartherbert.com/php/category/the-web-platform/](http://blog.stuartherbert.com/php/category/the-web-platform/)

Personally I run my own test server which I am the only user of, however it is on-line and is set up similar to a a shared hosting server with PHP running as separate users (to minimise the damage should one web root be compromised). However I am using Subversion instead of ftp/sftp for web root management.

---

### Post by cazz on 2009-07-26
> **hessiess said:**
> With PHP you rilly need to get it running scripts as seperate users to be sccure (espetily if you are going to heve outher people using the server), Running PHP as CGI with suexec is the easiest way to do this, and the proformance hit isnt that noricable.

> **hessiess said:**
> This blog covers the problem (down at the bottom) and the ways of fixing it: [http://blog.stuartherbert.com/php/category/the-web-platform/](http://blog.stuartherbert.com/php/category/the-web-platform/)

Personally I run my own test server which I am the only user of, however it is on-line and is set up similar to a a shared hosting server with PHP running as separate users (to minimise the damage should one web root be compromised). However I am using Subversion instead of ftp/sftp for web root management.

Thanks, I going to read a little about it.

---

