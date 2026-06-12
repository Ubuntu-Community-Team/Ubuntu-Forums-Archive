---
title: "Business pack"
date: 2008-03-12
forum: Server Platforms
---

### Post by Blempis on 2008-03-12
I'd like to do two things:

- to start a small business for the first time.
- to get rid of all MS connections.

Yes, there are office programs for word processing, but accounting is needed as well etc. I also need to share huge video files (several gigs ) to my customers and both email and skype have their limitations. Skype would do fine, but it would be better if my customers can get their files when ever they want - not just when I'm available. Like with skype, the solution should be secure. Of course, each file should be addressed to certain customer(s) so that not everybody can have the access to all files.

It is easy to say that use a server for that, but that is only a part of the solution. So, if anybody here has made all of this through, I'd appreciate for any help.

- What programs to get?
- Is there any linux (ubuntu) solution which is as comprehensive as possible to fulfill these needs?
- To accomplish all of this, is there a need to use some professional help?  If so, what should I do next?

P.S.  I'm not sure whether this server category is the right place for all of this but at least here should be the knowledge to solve the file sharing problem.

---

### Post by HermanAB on 2008-03-12
SQL Ledger is probably best: 
[http://www.sql-ledger.org/](http://www.sql-ledger.org/)

I also need to share huge video files:
An FTP server is very efficient for sharing data since the client machines that do most of the work, not the server.
Eg. proftpd

Citadel also has a concept of Directory Folders and it can do collaboration though email. chat and discussion forums.

- Is there any linux (ubuntu) solution which is as comprehensive as possible to fulfill these needs?
Linux is Linux is Linux...  
However, if you want to have wizards for clickety-click management of everything, then Mandriva is probably better, since Ubuntu is mainly geared towards desktop users, and the Ubuntu server wizards are limited/non-existent.

- To accomplish all of this, is there a need to use some professional help? If so, what should I do next?
Probably - send me a private message - it is what I do.

Cheers,

Herman

---

### Post by Harlequin on 2008-03-13
> **Blempis said:**
>  but accounting is needed as well etc.

Accounting caused me the most headaches - To being with my bookkeeper had her own windows system - but that meant she couldn't access out in house database (all other desktops run 7.10).  Next I ran a windows machine and used the rc1 hack and seamless rdp to give her access to myob on a ubuntu machine - then finally I discovered winehacks - which rather nicely allowed me to run myob under wine - be very careful which accounting package you choose - essentially you are tied into it from there on in (assuming you start to do decent amounts of business)

> **Blempis said:**
> 
 I also need to share huge video files (several gigs ) to my customers 


FTP server - I would recommend looking at clark connect as it will give you all of the server processess running on one machine easily - so FTP, FTPS, Mail server, authentication etc.  Simply create a user (unlimited in the free version of clark) for each one of your clients.

> **Blempis said:**
> 
- Is there any linux (ubuntu) solution which is as comprehensive as possible to fulfill these needs?
- To accomplish all of this, is there a need to use some professional help?  If so, what should I do next?


Don't tie yourself to one particular distro as each has advantages and disadvanteges.  

Citadel which HermanAB recommended is a very good system but has a limitation when it comes to sharing user credentials with other systems in your network.  It makes an excellent mail server and collaboration system but not alot else.  It also loses out by not having a better LDAP intergration (PAM_Auth is too limiting) .

Professional help would help but certainly isn't mandatory.  Again have a look at clark connect as a pretty good out of the box complete server package.  It will contain pretty much everything you would need to meet your stated requirements.

---

