---
title: "Imap issues"
date: 2008-08-03
forum: Server Platforms
---

### Post by hvc123 on 2008-08-03
Hi all,

i have created a mail server but i cannot connect to it via outlook (on another machine) or squirrel webmail. the smtp imap and pop3 ports are open.

it does however receive mail to the correct /var/mail/folders. i just cant connect a client. i have routed through the mail logs but i cant find anything wrong 
i can telnet to 993,143 and 25 no problems and get the correct responses

the client connects and then disconects in mail.log with no definitive error however it is delevering the mail to the correct maildrop

.... help please

---

### Post by Vishal Agarwal on 2008-08-03
if every thing is OK, squirrel webmail should work.have you configure the dovecot ?

Can u check the mail from server itself ?

---

### Post by hvc123 on 2008-08-03
when i telnet to pop3 it logs in but i dont see any folders (maybe i need to enter a command) there is a mail folder in my home area with dovecote files in

i can also telnet to all mail ports on and off my network

squirrel web mail just say "ERROR: Connection dropped by IMAP server."
and in my mail.log i see 
"imapd-ssl: authentication error: No such file or directory"

ok new error i changed the port in squirrelmail-config from 993 to 143 and now i get "Error connecting to IMAP server: tls://localhost.
0 : " in squirrelmail web window.
also when i use mutt -f imap://myuser@localhost/INBOX ihave a certificate error

"WARNING: Server hostname does not match certificate" how can i re-do / edit my certificate

---

