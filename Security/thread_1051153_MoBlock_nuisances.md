---
title: "MoBlock nuisances"
date: 2009-01-26
forum: Security
---

### Post by SqRt7744 on 2009-01-26
After installing MoBlock from the homepage:
[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

I noticed that it was interfering with many internet related activities. Specifically Ekiga, Pidgin (MSN, GoogleTalk, ICQ), Transmission, evolution with googlemail imap/smtp, pulseaudio...

I found that adding a few things to the defaults file has helped restore my connectivity

the file /etc/default/moblock should contain (after the header):
WHITE_TCP_OUT="http https 465 587 993 1863 5190 5222"
WHITE_UDP_IN="5000:5100 5353 7070 16382"
WHITE_UDP_OUT="3478:3479 5353 5000:5100"


After making the changes, a simple sudo moblock-control restart or sudo /etc/init.d/moblock restart did NOT help, a full reboot of the computer was necessary.

I hope this info is useful to somebody...  It might also be overkill, so if somebody knows a better way I'd appreciate it.

explanation of the ports
465, 587, 993 gmail imap/smtp
1863-MSN,5190-ICQ,5222-XMPP(google chat)
[51413-Transmission (not recommended, see next post)]
5000:5100 7070 16382 SIP
3478:3479 also SIP stuff
5353 pulseaudio (actually Zeroconf/Avahi)

---

### Post by jre on 2009-01-27
> **SqRt7744 said:**
> 51413-Transmission
Err, I doubt you want to allow this traffic. Most people install Moblock because they want to check MoBlock's traffic, so that they don't connect to bad peers.

I don't know why restarting should have been necessary. But unless you can reproduce this behaviour I think I will ignore it.

Otherwise, yes, you handled your problems correctly. Is 587 really needed? I will add your port mentionings to the wiki at [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

---

### Post by SqRt7744 on 2009-01-28
thanks! I wasn't too sure about 51413, although it seems moblock is still bocking certain IPs when transmission is running, so I guessed it was ok. I'll remove it from my list. 
I had added it in an (unsuccessful) attempt to get the listening port to read 'open' instead of closed. I've forwarded the port from the router to the computer, so that shouldn't be the problem. It's still reporting "closed". Does this matter?

re. the full restart: if I didn't restart, I couldn't access the web (port 80), transmission still seemed to be working. The same behavior occurred on my laptop as well.

re. gmail: it can use port 465 *or* 587 for smtp, it depends which one you picked in your setup (or which one your service provider hasn't blocked)
see: [http://mail.google.com/support/bin/answer.py?answer=78799](http://mail.google.com/support/bin/answer.py?answer=78799)

---

