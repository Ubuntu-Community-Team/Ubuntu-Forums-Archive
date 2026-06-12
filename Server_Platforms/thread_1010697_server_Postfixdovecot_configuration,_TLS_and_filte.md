---
title: "server Postfix/dovecot configuration, TLS and filtering issues"
date: 2008-12-14
forum: Server Platforms
---

### Post by jrdecastro on 2008-12-14
I have run into a few problems with the mail section of Ubuntu Server documentation and have some questions.
I am trying to set up a mail server using Postfix, Dovecot, Amavis, clamAV, Spamassassin etc… just like the Ubuntu Server Guide explains, using Maildir/ storage format and IMAP server based storage, with SASL authentication and TLS certificates for server and client authentication. Users are local not virtual (all have accounts on the server) for simplicity.

Problem/question 1)
In /etc/postfix/main.cf
The recommended default contains the line:
mailbox_command = procmail -a "$EXTENSION"
As set out in the guide, and with the guide only as guidance, this does not work. Mails simply don’t get delivered at all. I think $EXTENSION is undefined (maybe there needs to be some further entries in /etc/postfix/master.cf which have not yet made it into the documentation to set up the user .procmailrc files etc..), and there are no instructions on how to configure procmail which can be a whole new subject in itself.
However, if I replace the line with :
mailbox_command = /usr/lib/dovecot/deliver
then mails do get delivered. Is there any reason why the procmail line is there – maybe relating to spam filtering etc.? If yes, what is that reason and how should it be configured? If not, please let me know and I will stop worrying about it!

Problem 2) Multiplication of certificates.
The Postfix installation routine goes through creating an smtpd.crt certificate and smtpd.key pair to use for authenticating the server, which then get referenced in the /etc/postfix/main.cf file. This is presumably a TLS server certificate.
The Dovecot configuration does the same but with a ssl-cert-snakeoil certificate and key pair, which do its SSL authentication.
Am I correct in thinking that we could (and probably should) use the same certificate and key pair for both functions?
OR, is there a clear reason why Postfix and Dovecot SHOULD be using different server cert/key pairs, and if so, what is this reason?

Problem 3) TLS certificates.
I have been unable so far with the provided instructions in the Server guide to set up TLS client authentication. If I set Evolution to use SSL for receiving emails it works, if I choose “TLS” it says “connection refused”. When it does work using SSL, the full message header says “the client did not present a certificate”. I suspect this whole class of symptoms could be to do with the required x509v3 extensions for the CA, server cert, and client certs somehow not playing nice with each other.
Could someone please let me know which extensions are needed for each type of certificate (CA cert, server cert, and client certs) so that it all works together without problems?

Problem 4) Mail filtering.
I have followed to the letter the instructions for setting up amavis, clamav, spamassasin, pyzor-razor etc. and tested it, and the full header of received messages (from inside our local network) shows an X-entry referring to antivirus scanning having been done, but nothing relating to spam like the guide says I should be seeing. I have not yet opened this server to the external internet as it doesn’t seem ready for prime time yet. As there is no entry in the header referring to spam scoring etc.. I am beginning to think that the spam filtering side is not working. Why could this be? Does it depend on procmail being up, in which case Problem 1) above could be related?
Also, where does one see filtered spam and how does this get configured? The Server Guide is silent on the subject, and it should perhaps mention ‘configuration file X sets out the path / folder / whatever where Spamassasin will drop suspected spam’, and ‘if any non-spam message gets tagged as spam, this (file Y) is how you tell Spamassasin about it so that it doesn’t do it again’

Request 1)
Could someone send me a set of /etc/postfix main.cf and master.cf, plus /etc/dovecot/dovecot.conf that has been configured in line with the Server Guide instructions and recommendations and which are known to work together for Maildir/, IMAP with SASL and TLS, and Amavis/ClamAV/Spamassasin?

Request 2) 
Could someone please send me the required extensions for 1) the CA certificate, 2) the server certificate, 3) the client certificates? Also, what should the Common Name be for the client certificates? Should it be “user1” or [email]user1@example.com[/email] ?

Hope this is all clear and look forward to hearing back soon!

Thanks in advance

James R de Castro

---

