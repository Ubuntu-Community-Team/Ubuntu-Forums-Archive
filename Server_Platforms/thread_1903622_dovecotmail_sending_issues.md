---
title: "dovecot/mail sending issues"
date: 2012-01-02
forum: Server Platforms
---

### Post by jperz09 on 2012-01-02
[COLOR=green]
 
 
[COLOR=black][FONT=Verdana]Ok so I’m getting pretty frustrated, and I’ve probably been working on this for too long. But anyway, I have dovecot and postfix set up on my server (11.10) I can send a receive mail when I do it directly from the server. But when I set up a client (outlook) it goes through all the sets for setting it up successfully, even "sends" a test message. Now when I’m in outlook, I can get messages all day, but when I actually try to reply to them, it never gets to the other email address. There is no error message in outlook, according to outlook it sends just fine. [/FONT][/COLOR]
[COLOR=#000000][/COLOR] 

[COLOR=black][FONT=Verdana]So I looked in the mail.log file, this is what it says....[/FONT][/COLOR]
 

[COLOR=green][FONT=Verdana]Jan 2 22:47:03 jpfile postfix/smtpd[21592]: connect from unknown[192.168.1.1][/FONT][/COLOR]
[FONT=Verdana][COLOR=green]Jan 2 22:47:03 jpfile postfix/smtpd[21592]: D5630260033: client=unknown[192.168.1.1][/COLOR][/FONT]
[FONT=Verdana][COLOR=green]Jan 2 22:47:03 jpfile postfix/cleanup[21627]: D5630260033: message-id=<>[/COLOR][/FONT]
[FONT=Verdana][COLOR=green]Jan 2 22:47:03 jpfile postfix/qmgr[21477]: D5630260033: from=<jon@per-tech.com>, size=543, nrcpt=1 (queue active)[/COLOR][/FONT]
[FONT=Verdana][COLOR=green]Jan 2 22:47:03 jpfile postfix/smtpd[21592]: disconnect from unknown[192.168.1.1][/COLOR][/FONT]
[FONT=Verdana][COLOR=green]Jan 2 22:47:03 jpfile postfix/local[21628]: D5630260033: to=<jon@per-tech.com>, relay=local, delay=0.15, delays=0.11/0.02/0/0.01, dsn=2.0.0, status=sent (delivered to maildir)[/COLOR][/FONT]
[FONT=Verdana][COLOR=green]Jan 2 22:47:03 jpfile postfix/qmgr[21477]: D5630260033: removed[/COLOR][/FONT]
[FONT=Verdana][COLOR=green]Jan 2 22:47:27 jpfile postfix/smtpd[21592]: connect from unknown[192.168.1.1][/COLOR][/FONT]
[FONT=Verdana][COLOR=green]Jan 2 22:47:27 jpfile postfix/smtpd[21592]: NOQUEUE: reject: RCPT from unknown[192.168.1.1]: 554 5.7.1 <jperz09@gmail.com>: Relay access denied; from=<jon@per-tech.com> to=<jperz09@gmail.com> proto=ESMTP helo=<Jon6530b>[/COLOR][/FONT]
[FONT=Verdana][COLOR=green]Jan 2 22:47:29 jpfile postfix/smtpd[21592]: disconnect from unknown[192.168.1.1][/COLOR][/FONT]
[FONT=Verdana][COLOR=green]Jan 2 22:47:30 jpfile dovecot: imap-login: Login: user=<jon>, method=PLAIN, rip=192.168.1.1, lip=192.168.1.115, mpid=21630, TLS[/COLOR][/FONT]
[COLOR=black][FONT=Verdana]Not sure what I’m doing wrong, any help would be awesome! If you need any extra info, please let me know.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks!![/FONT][/COLOR]
 
[/COLOR]

---

### Post by HermanAB on 2012-01-03
<jperz09@gmail.com>: Relay access denied; from=<jon@per-tech.com> to=<jperz09@gmail.com> proto=ESMTP helo=<Jon6530b>

You need to install some sort of a POPbeforeSMTP kludge:
[http://www.bluelavalamp.net/pop-before-smtp/](http://www.bluelavalamp.net/pop-before-smtp/)

---

### Post by jperz09 on 2012-01-03
Thanks for the replay, but i have to use IMAP because my ISP is blocking the ports i was trying to use for pop, unless i had it set up wrong, which is very possible

---

### Post by HermanAB on 2012-01-03
Same thing. You got to authenticate before you can use SMTP. Google is your friend.

---

