---
title: "POP Email Server Error"
date: 2007-07-06
forum: Server Platforms
---

### Post by Jixxon on 2007-07-06
I set up an email server with the Postfix and Dovecot tutorials from the Ubuntu Documentation pages (In version 7.04). I tested both per the tutorials and they seem to be working. I used POP3 and IMAP over POP3S/IMAPS. I am also using maildir over mbox.

I set everything up in Evolution to send and get email. Side note - everything on the mail.mydomain.com side is working fine. I created a new user in Ubuntu and used that for my email address (i.e. [email]newuser@mydomain.com[/email]).

My port 25 is blocked so I use an outside SMTP server to send mail. That seems to be working just fine. It is on the receiving POP3 side that I get an error. Here is the message I get when I hit the send/receive button in Evolution:

*****
Unable to connect to POP server mail.mydomain.com.
Error sending username: -ERR Plaintext authentication disallowed on non-secure connections.
Please enter the POP password for *userid* on host mail.mydomain.com
*****

I try to enter the password I created for my new user, but the error message keeps coming up and I can't receive anything. I am a newbie at this email thing, so I assume I am missing a setting in the .conf file somewhere.

Any help would be appreciated. Thank you.

---

### Post by Mr. C. on 2007-07-07
When you say "over", you mean "instead of", right ?

Why choose to use POP instead of POP3S ?

POP is a plain text protocol.  Your dovecot installation appears to be requiring secure POP connections (i.e. POP3S on port 995 instead of POP on 110). 

MrC

---

### Post by Jixxon on 2007-07-16
Thank you for the assistance. It turns out I was messing around with my config files to much and brought down more than just the email server I was trying to set up. If anything it was a great learning experience. I reinstalled the OS and will attempt to do it the correct way this time :)

---

