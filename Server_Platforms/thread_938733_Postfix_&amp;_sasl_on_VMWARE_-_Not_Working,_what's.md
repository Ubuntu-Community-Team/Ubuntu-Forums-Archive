---
title: "Postfix &amp; sasl on VMWARE - Not Working, what's wrong?"
date: 2008-10-05
forum: Server Platforms
---

### Post by lopes_andre on 2008-10-05
Hi,

I'am trying to configure a Postfix server to send e-mails by SMTP using the SMTP server of my ISP. I have made a Postfix installation as "Internet with Smarthost".

I'am using a domain in Godaddy, I have point "A (Host) Record" to my IP and the "MX Record" is also pointing to my IP. I have tested sending e-mail from my gmail.com account to my server, the server receive e-mails from gmail.com to my /home/andre/mbox successfully.



So... I have installed Ubuntu server with Postfix and I installed also libsasl2-modules.

In my configuration to get my Postfix sending e-mails by SMTP using my ISP SMTP(my ISP SMTP requires authentication), my guide was: [http://newbiedoc.berlios.de/wiki/Mail_-_sending](http://newbiedoc.berlios.de/wiki/Mail_-_sending)

I have tested "telnet mydomain.com 25" from another computer with another IP address on the Internet and I get:

220 mydomain.com ESMTP Postfix (Ubuntu) 



After doing the changes related in this tutorial, [http://newbiedoc.berlios.de/wiki/Mail_-_sending](http://newbiedoc.berlios.de/wiki/Mail_-_sending) (I don't have configurated SSL Support)

After all this, here is my /var/log/mail.log

Oct  5 12:43:52 myhost postfix/anvil[4979]: statistics: max connection rate 1/60s for (smtp:74.125.92.24) at Oct  5 12:40:00
Oct  5 12:43:52 myhost postfix/anvil[4979]: statistics: max connection count 1 for (smtp:74.125.92.24) at Oct  5 12:40:00
Oct  5 12:43:52 myhost postfix/anvil[4979]: statistics: max cache size 1 at Oct  5 12:40:00
Oct  5 12:44:48 myhost postfix/qmgr[4456]: 6F5A0678C: from=<andre@mydomain.com>, size=324, nrcpt=1 (queue active)
Oct  5 12:45:18 myhost postfix/smtp[4995]: connect to relay.netvisao.pt[213.228.128.59]:25: Connection timed out
Oct  5 12:45:18 myhost postfix/smtp[4995]: 6F5A0678C: to=<vicgood@hotmail.com>, relay=none, delay=479, delays=449/0/30/0, dsn=4.4.1, status=deferred (connect to relay.netvisao.pt[213.228.128.59]:25: Connection timed out)


What you see as clue here in mail.log? Whats wrong?

Best Regards, Andre.

---

### Post by MJN on 2008-10-05
Is relay.netvisao.pt your ISP's SMTP server?

Can you connect to it via telnet? If so, what do you see? Does it work?

Mathew

---

### Post by lopes_andre on 2008-10-05
My ISP SMTP is: mail.netvisao.pt

When I "telnet mail.netvisao.pt 25" I get:

220 av-front2.netvisao.pt ESMTP



I have configured my "relayhost = mail.netvisao.pt" in my /etc/postfix/main.cf, why in the mail.log appears relay.netvisao.pt?


Best Regards.

---

### Post by MJN on 2008-10-05
> **lopes_andre said:**
> why in the mail.log appears relay.netvisao.pt?Good question. Have you restarted/reloaded Postfix since making that configuration?

Note that you ought to wrap the host server name in brackets to force an A record lookup (otherwise it will query for MX records which you likely don't want). Hence, enter it is as **relayhost = [mail.netvisao.pt]**

Mathew

---

### Post by lopes_andre on 2008-10-05
Great!!!

relayhost = [mail.netvisao.pt]

Solved the problem!!!

Thanks, Thanks a lot MJN!


Best Regards, Andre.

---

### Post by MJN on 2008-10-05
Nice one. It's a common problem with that directive - indeed I am surprised that the default behaviour without brackets is the way it is as it is rarely the outcome you want.

Mathew

---

