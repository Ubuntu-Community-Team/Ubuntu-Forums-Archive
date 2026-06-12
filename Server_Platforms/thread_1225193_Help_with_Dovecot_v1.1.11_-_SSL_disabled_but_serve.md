---
title: "Help with Dovecot v1.1.11 - SSL disabled but server still moans"
date: 2009-07-28
forum: Server Platforms
---

### Post by crunchbytes on 2009-07-28
:confused:
Dear All,
 
I'm pulling my hair out!
 
Ubuntu 9.04 (desktop edition, sorry).
Dovecot v1.1.11
 
SSL is disabled in dovecot.conf, along with 
disable_plaintext_auth = no
 
Dovecot restarted (PC restarted several times) but when connecting from the Internet (work connection), my Windows Live Mail client (IMAP) displays:
 
Plaintext authentication disallowed on non-secure (SSL/TLS) connections.
 
And refuses to logon.
 
The same for a POP3 connection.
 
mail.log shows:
tried to use disabled plaintext auth
Which, afaik, it isn't disabled!
 
Any pointers, please?
 
Thanks, Richard

---

### Post by mikeossur on 2011-03-06
Good luck getting a answer here.  I have the same issue and am not sharp enough to understand how to get around this problem.

---

