---
title: "Unable to access postfix smtp via Thunderbird"
date: 2011-03-19
forum: Server Platforms
---

### Post by kanjimaster on 2011-03-19
I have a postfix install achieved by following [these really helpful instructions]("https://help.ubuntu.com/community/Postfix"), and a dovecot installation based on [these equally great guidelines]("https://help.ubuntu.com/community/Dovecot") on a 64bit 10.10 VPS.

Everything seems to be working fine. I can send and receive emails from the from server and access them remotely via IMAP. But Thunderbird doesn't recognize the SMTP. When I try to create an account in it, it recognizes the IMAP only, cycling through the SMTP possibilities before giving up.

I can telnet remotely from my desktop to the server's port 25 and and confirm that STARTTLS and AUTH are running, and the mail.log shows only the following entries> Mar 19 22:23:30 mailserver dovecot: imap-login: Aborted login (no auth attempts): rip=81.86.233.198, lip=82.113.147.226
Mar 19 22:23:32 mailserver postfix/smtpd[7750]: connect from 81-86-233-198.dsl.pipex.com[81.86.233.198]
Mar 19 22:23:32 mailserver postfix/smtpd[7750]: disconnect from 81-86-233-198.dsl.pipex.com[81.86.233.198]
Mar 19 22:23:33 mailserver postfix/smtpd[7750]: connect from 81-86-233-198.dsl.pipex.com[81.86.233.198]
Mar 19 22:23:33 mailserver postfix/smtpd[7750]: disconnect from 81-86-233-198.dsl.pipex.com[81.86.233.198]suggesting that the SMTP server is being communicated with, but giving no clues as to why Thunderbird doesn't like it.

Thunderbird is normally so good at account setup, that I suspect it's something in how I've configured this that's causing the problem. Hoping that somebody out there will have more of a clue, or at least be able to guide me as to where to look next.

---

