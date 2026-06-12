---
title: "Receiving Mail Externally w/ closed Port 25"
date: 2011-10-07
forum: Server Platforms
---

### Post by pteri498 on 2011-10-07
I'm noticing I can't receive e-mail from an external source (like gmail) while I have smtp turned off in /etc/postfix/master.cf

Is this entirely by design? I prefer to have that part of the postfix service off/commented out to discourage users from trying to log into their email through a non-TSL interface.

Is there a way to get email externally while still having smtp off? Port forwarding, something?

Thanks.

---

### Post by Ceyx on 2011-10-09
From what I understand, SMTP on port 25 is for sending (not receiving) mail from your email server to your upstream ISP or mail relay.  Something else must be going on....

---

### Post by ian dobson on 2011-10-10
Hi,

The server listens on port 25 for connections from other email servers that want to send an email to the domain the the listening server is responsible for.

Maybe your email server have a pop3 fetcher of some sort. The server kicks the pop3 fetcher, that pulls all the emails from the remote server (gmail for example) and then passes them onto the local email server for processing/storing in the users mailbox.

Hope this helps
Regards
Ian Dobson

---

### Post by SeijiSensei on 2011-10-10
If you want remote servers to send you mail, you need to have an SMTP server listening on port 25.

You can set up a process to download mail from a remote server using the [fetchmail]("https://help.ubuntu.com/community/GmailPostfixFetchmail") program.

---

