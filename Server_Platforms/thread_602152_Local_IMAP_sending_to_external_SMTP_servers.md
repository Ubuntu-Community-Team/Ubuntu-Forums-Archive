---
title: "Local IMAP sending to external SMTP servers"
date: 2007-11-03
forum: Server Platforms
---

### Post by passbe on 2007-11-03
This is my situation, i would like to retrieve 4 POP3 email accounts to a local imap server. This server is running an installation of roundcube, which allows me to interface with the local imap server. 

I currently have running

fetchmail > procmail > dovecot. 

Thus i have no problems with the local imap. However i need to find a solution whereby i can use roundcube (or alternative) to send emails via the pop3 smtp servers, instead of the local imap server (or singular smtp server). This is to ensure that an email that was sent to [email]passbe@domain.com[/email], allows i can reply by the same email accounts smtp server.

Any help is greatly appreciated.

---

