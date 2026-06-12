---
title: "mail server - internal imap connecting to external pop"
date: 2006-08-11
forum: Server Platforms
---

### Post by probablydrew on 2006-08-11
Is it possible (within reason) to have a server on your lan that acts as a mail server that clients on the lan can connect to and check their mail via imap, but the mail on that lan server gets there by the lan server checking pop account over the internet periodically rather than having mail delivered directly to it?

The reason I ask is I have a lan setup with a few workstations and one server.  The server is running Ubuntu and acting as a simple file/printer/dhcp/squid machine for all of the workstations.
What I would like is for all the mail for a few different email account to be stored on one machine to make backups and management easier.  As opposed to using pop and having mail on every workstations, which also makes the mail inaccessible via webmail.
I am aware that you can buy commercial mail service that allows imap access but this typically is very limited with regards to disk space per account, on the other hand commercial pop accounts are cheap and easy.  I am also aware that I could just run my own mail server, unfortunately all of the available isp's prohibit this.

So that is my question, can I use regular pop mail service, set up a few accounts, have a local mail server which checks all those accounts periodically and pulls down everything, and have the users connect to that lan machine to check their mail.  And also send mail through the lan server which will then forward it through the pop service but retain a copy which they could view locally through imap.

This may be an obvious question but it's one of those things that is difficult to search for because all of the terminology are commonly used words found in lots of combinations.

---

