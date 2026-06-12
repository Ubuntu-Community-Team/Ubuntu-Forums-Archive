---
title: "Need to configure FTP server with only one ip for multiple domains"
date: 2012-06-11
forum: Server Platforms
---

### Post by piine on 2012-06-11
Hi, I am using pure-ftpd-mysql on one server and proftpd-mysql on another and I need to be able to configure at least one of them to login per-domain. Ex. [EMAIL="johndoe@example.com"]johndoe@example.com[/EMAIL] and [EMAIL="johndoe@example2.com"]johndoe@example2.com[/EMAIL] with ip 1.2.3.4...

Right now, I can only have 1 johndoe in the db. For now, I have to setup my users as johndoe.example.com and johndoe.example2.com if two domains have the same username. 

I have search for days to find a tutorial that will allow me to do this, but as of this point, all I have found are per ip logins using multiple dbs or tables. I would much rather all my users be store in the same domain and be able to find a way to get the requested domain and login that way. If that makes since. Pls, pls, pls help....!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by sanderj on 2012-06-11
You could have a different port per domain. The user must then specify the port to access its domain.

Something like:
[ftp://ftp.xs4all.nl:21/pub/](ftp://ftp.xs4all.nl:21/pub/)
[ftp://ftp.xs4all.nl:22/pub/](ftp://ftp.xs4all.nl:22/pub/)


Otherwise I don't think it's possible: with the same IP, same port and same username, there is no way for a FTP server to distinguish a domain.

With HTTP it *is* possible, as (since HTTP 1.1?) the HTTP-client will specify the domain within the protocol, and thus you can put different webservers on the same IP:port. 
Alas that does not happen within FTP (AFAIK).

---

### Post by piine on 2012-06-12
Well, that just sucks... I guess I will have to keep like I have... I thought that I would be able to the ftp server like the email  server, where I could just use a db be able to auth per domain... 

I wish someone would/could fix that...

---

### Post by sanderj on 2012-06-12
> **piine said:**
> Well, that just sucks... I guess I will have to keep like I have... I thought that I would be able to the ftp server like the email  server, where I could just use a db be able to auth per domain... 

I wish someone would/could fix that...

Just checking: this is the login sequence you want:

ftp ftp.example2.com

user: joe
pass: xxx


Right? My answer was based on the above.


Or do you want this:


ftp ftp.example2.com

user: [email]joe@example2.com[/email]
pass: xxx

---

