---
title: "Dovecot SSL/TLS"
date: 2012-03-14
forum: Server Platforms
---

### Post by Jay89 on 2012-03-14
Hello,
   Would anyone know how to go about configuring dovecot to use port 465 or 587 for outgoing email? Right now I can connect to my server using imaps 993 and outgoing port 25 with Normal Password authentication and STARTTLS security.. It may be my inexperience but this doesn't seem that secure. Would someone be able to explain how to config dovecot to use SSL/TLS and port 465?

The server is running Ubuntu 11.10 with postfix and dovecot.

Thanks
If you need any log/config posts from me please let me know.

---

### Post by Jay89 on 2012-03-26
Has anyone else seen this before?

---

### Post by ausome on 2012-12-14
Hopefully you solved this by now... but I'll add this to the "info pool" as this thread has been left hanging...


I'm using ubuntu 12.10 Server

To get port 587 working you need to add in a line into
/etc/postfix/master.cf

587 inet - - - - smtpd


I've not had any joy with SSL/TLS on port 465, which I did the same thing ( added a line into the master.cf) but I ended up getting the ole "relay access denied"... So it's not a biggy for me.

So like yourself, I'm using SSL/TLS IMAP 993 and STARTTLS SMTP 587 running on two systems bouncing emails around with "happy" abandon... After a Lot of deciphering and a few AHA moments I might add.

I'll be going back to STARTTLS on both so my IMAP will be 143. From my reading STARTTLS is as good as either choice.

Only the persistent get these things working and probably go slightly mad in the process!

Cheers
Tim

---

