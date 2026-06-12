---
title: "Help wanted setting up an email project"
date: 2007-08-10
forum: Server Platforms
---

### Post by strangetpwn on 2007-08-10
Hi all. A complete beginner here looking for help on an email project I want to set up. I've read lots of guides and How Tos on how to set up various email servers, but I'm running into problems setting them up, or they all seem to be far more advanced than I need (Mysql virtual mail boxes for example).

I'm hoping if I can explain what I want to do, someone here can point me in the right direction, or help me fill in the gaps that are preventing me from following the other guides.

Basically I want to set up an email system (I'm tying to avoid calling it a server or proxy as I don't think that's what it is) that will do the following:

[LIST]
[*]Periodically fetch emails from various mail boxes on the net using pop3 (eg personal website, gmail etc)
[*]Virus scan the emails (using ClamAV or something)
[*]Anti-spam score each email (using SpamAssassin or something)
[*]Put the mails in an IMAP maildir based format filtered into folders, gmail, myemail, spam etc
[*]Allow access to the IMAP mailbox from PCs on the local network
[/LIST]

The system will be hosted on a dynamic IP to the www, I don't want it associated with an MX record and don't need to be able to relay sent emails through the system (I can use my ISP for that) so my first issue in following any of the common email server tutorials is that to set up Postfix or I have to provide something for:

"server1.example.com"

What can I put here that will be valid if I'm on a dynamic IP without a hostname?
Do I even need Postfix as I'm not sending out any emails, and if I do how do I secure if from actually trying to send messages anywhere, or at least beyond the local network, and do I need to set up TSL?

There reasons I want to do all this and can't say for example use the plug-ins with Evolution directly are:
[LIST]
[*]I wouldn't learn anything if I just did that
[*]I believe this will give me an easy way to consolidate/backup all may email locally
[*]I access the email addresses from several systems including a Pocket PC which can't do virus/spam filtering so I want to set up this system to do the leg work
[/LIST]

One final point is I'm currently trying to do this on Ubuntu 7.4 Desktop, I know I should probably be using 7.4 Server, but as I said I'm a beginner and still need my GUI.

Thanks for reading

---

### Post by syadnom on 2007-08-11
I have a couple things here i can tell you about.

first thing is to install webmin.  just go to [http://webmin.com]("http://webmin.com")
and install the debian package.

webmin will help you configure all the mail stuff MUCH more easily.

one problem you *might* come accross is having to have a user on the linux system for each user that uses this "email proxy" type system. if you are the only one then it wont be too bad.

as far as domain name, just make up something like mailproxy.local, this wont be a problem because you are not receiving email on this system, just having it check mail.

get your imap working.  if you use webmin you just need to choose which server you want, dovecot is quite easy with webmin and handles pop3 and imap connections with optional SSL and IP6

you can use fetchmail to retrieve all of your pop3 mail  with a .fetchmailrc file OR through webmin.

and finally, you can use procmail and spamassasin and clamav to filter spam and virri. 

you will need to set up an MTA as it is not just sending but also receiving mail and some of this software will require and MTA or freak  out without one.

---

### Post by strangetpwn on 2007-08-12
Thanks for replying.

I'll give it a try and get back to you.

---

