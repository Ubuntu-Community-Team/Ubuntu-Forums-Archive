---
title: "Upgrade from 12 to 14, postfix/dovecot issue"
date: 2014-10-04
forum: Server Platforms
---

### Post by DigiAngel on 2014-10-04
So...had to put my dev box in production as the production box power supply died.  I have postfix running, and messages say they are getting delivered:

Oct  4 11:31:00 gateway postfix/local[15108]: B584A2440C5: to=<my@domain>, relay=local, delay=0.2, delays=0.12/0/0/0.07, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")

However when I check email using pop or imap (dovecot) list shows 0 messages.  Did the default mail location change from 12 to 14?  Any help would be wonderful..thank you.

---

### Post by JKyleOKC on 2014-10-04
Double check your /etc/postfix/main.cf file; if possible, compare it to the same file that worked on the previous production unit (from a backup, if one is available). If you're using dovecot as a delivery agent, the log entry for the "delivered to command" should read
> (delivered to command: /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -m "${EXTENSION}") rather than > (delivered to command: procmail -a "$EXTENSION")
If you're really using procmail as your delivery agent, then ignore this message -- but in that case, I wouldn't expect dovecot to do anything at all!

---

### Post by DigiAngel on 2014-10-05
Confirmed...'mailbox_command = procmail -a "$EXTENSION"' is in the default configuration after an Ubuntu 12 install.  Dovecot is acting as the pop/imap server in this case.

---

