---
title: "Postfix dovecot unable to receive messages in Outlook"
date: 2009-10-08
forum: Server Platforms
---

### Post by deepakdeshp on 2009-10-08
Hi Gurus,

I am unable to get  messages into my Outlook INBOX from my Ubuntu 9.04 Postfix mail server. I can telnet to port 25 of the mail server from my Windows client. When I telnet I get:-  220 ubuntuserver ESMTP Postfix (Ubuntu)

The mail.log entries are:-

Oct  8 13:11:09 ubuntu postfix/smtpd[2749]: lost connection after CONNECT from unknown[59.95.39.147]
Oct  8 13:11:09 ubuntu postfix/smtpd[2749]: disconnect from unknown[59.95.39.147]


 I am working on this problem for more than a week but am no where near the solution.

Thanks in anticipation.

Regards,
Deepak

---

### Post by diesch on 2009-10-08
Postfix is for sending mail. To access your inbox you have to use IMAP or POP3 (dovecot can provide this).

---

### Post by deepakdeshp on 2009-10-08
If I have to set up dovecot, can I know what are the minimum directives in dovecot.conf file? Right now I am not bothered about ssl etc.

Thanks,
Deepak

---

### Post by diesch on 2009-10-08
Setting "protocols" and "listen" should be enough if there are already some mails in your mailbox and your mail aren't stored on a unusual location (otherwise you need to set "mail_location").

What does```
telnet localhost imap
```on your server say (replace "imap" with "pop3" if you want to use pop3)?

---

### Post by deepakdeshp on 2009-10-08
Hello diesch,

Thank you for your response.

When I telnrt from my windows client :- telnet ubuntuserver imap 

The output is ok dovecot ready.


The code in the dovecot.conf file is:-

[I]protocol imap {
     listen = *:10143
     ssl_listen = *:10943
#     ..
   }
   protocol pop3 {
     listen = *:10100
#     ..
   }


#disable_plaintext_auth = yes

[/I]Commenting or uncommenting the above line does not make any difference and I get the same output as given below.[B]

When I restart dovecot I get [/B][I]:-

Warning: There is no way to login to this server: disable_plaintext_auth=yes, ssl-disable=yes, no non-plaintext auth mechanisms.
Warning: There is no way to login to this server: disable_plaintext_auth=yes, ssl-disable=yes, no non-plaintext auth mechanisms.
Info: If you have trouble with authentication failures,
enable auth_debug setting.


[/I]**The mail.log contents are:-**[I]

Oct  8 22:42:32 ubuntu postfix/smtpd[9615]: connect from unknown[59.95.17.135]
Oct  8 22:42:33 ubuntu postfix/smtpd[9615]: 26DEB16160B: client=unknown[59.95.17.135]
Oct  8 22:42:33 ubuntu postfix/cleanup[9619]: 26DEB16160B: message-id=<000a01ca488a$2a06b5d0$7e142170$@domain>
Oct  8 22:42:33 ubuntu postfix/qmgr[3583]: 26DEB16160B: from=<deepak@ubuntu.domain>, size=2549, nrcpt=1 (queue active)
Oct  8 22:42:33 ubuntu postfix/local[9620]: 26DEB16160B: to=<deepak@ubuntu.domain>, relay=local, delay=0.35, delays=0.34/0/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
Oct  8 22:42:33 ubuntu postfix/qmgr[3583]: 26DEB16160B: removed
Oct  8 22:42:35 ubuntu postfix/smtpd[9615]: disconnect from unknown[59.95.17.135]


[/I]

---

### Post by nandemonai on 2009-10-09
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html) ;)

---

### Post by deepakdeshp on 2009-10-09
I have referred to the 9.04 server guide but still stuck up.

Thanks,

Deepak

---

### Post by deepakdeshp on 2009-10-10
Any clue for the above problem?

Regards,
Deepak

---

