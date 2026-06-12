---
title: "Hardening my mail server"
date: 2008-10-19
forum: Security
---

### Post by ngmachado on 2008-10-19
Hi all,

Finally I got a mail server (Postfix, SASL, MySQL, Courier) running on my Ubuntu 8.04 LTS.

I've already run some tests and there're no open relays, Postfix does a pretty job here. I also use SASL so I think it prevents unauthorised mail sending.

I'll be the only user of the system so I've blocked IMAP ports in my firewall. I also blocked POP3, only leaving POP3 SSL open (in the future I might get a certificate).

1. May I change the POP3 SSL port number, in order to increase security? I'm the only user of the system.

In my mail log this message keeps appearing:

```

Oct 19 10:10:11 mailserver postfix/smtpd[2807]: connect from 118-167-137-38.dynamic.hinet.net[118.167.137.38]
Oct 19 10:10:12 mailserver postfix/smtpd[2807]: NOQUEUE: reject: RCPT from 118-167-137-38.dynamic.hinet.net[118.167.137.38]: 554 5.7.1 <s2288@mail2000.com.tw>: Relay access denied; from=<p5.p5@hotmail.com> to=<s2288@mail2000.com.tw> proto=SMTP helo=<xxx.xxx.xxx.xxx>
Oct 19 10:10:12 mailserver postfix/smtpd[2807]: lost connection after RCPT from 118-167-137-38.dynamic.hinet.net[118.167.137.38]
Oct 19 10:10:12 mailserver postfix/smtpd[2807]: disconnect from 118-167-137-38.dynamic.hinet.net[118.167.137.38]
Oct 19 10:10:58 mailserver postfix/smtpd[2807]: connect from 118-167-137-248.dynamic.hinet.net[118.167.137.248]
Oct 19 10:11:01 mailserver postfix/smtpd[2807]: NOQUEUE: reject: RCPT from 118-167-137-248.dynamic.hinet.net[118.167.137.248]: 554 5.7.1 <support@microsoft.com>: Relay access denied; from=<support@microsoft.com> to=<support@microsoft.com> proto=SMTP helo=<xxx.xxx.xxx.xxx>
Oct 19 10:11:02 mailserver postfix/smtpd[2807]: lost connection after RCPT from 118-167-137-248.dynamic.hinet.net[118.167.137.248]
Oct 19 10:11:02 mailserver postfix/smtpd[2807]: disconnect from 118-167-137-248.dynamic.hinet.net[118.167.137.248]
Oct 19 10:12:05 mailserver postfix/smtpd[2807]: connect from 118-167-137-38.dynamic.hinet.net[118.167.137.38]
Oct 19 10:12:05 mailserver postfix/smtpd[2807]: NOQUEUE: reject: RCPT from 118-167-137-38.dynamic.hinet.net[118.167.137.38]: 554 5.7.1 <s2288@mail2000.com.tw>: Relay access denied; from=<p5.p5@hotmail.com> to=<s2288@mail2000.com.tw> proto=SMTP helo=<xxx.xxx.xxx.xxx>
Oct 19 10:12:05 mailserver postfix/smtpd[2807]: lost connection after RCPT from 118-167-137-38.dynamic.hinet.net[118.167.137.38]
Oct 19 10:12:05 mailserver postfix/smtpd[2807]: disconnect from 118-167-137-38.dynamic.hinet.net[118.167.137.38]
Oct 19 10:12:45 mailserver postfix/smtpd[2807]: connect from 118-167-137-248.dynamic.hinet.net[118.167.137.248]
Oct 19 10:12:46 mailserver postfix/smtpd[2807]: NOQUEUE: reject: RCPT from 118-167-137-248.dynamic.hinet.net[118.167.137.248]: 554 5.7.1 <support@microsoft.com>: Relay access denied; from=<support@microsoft.com> to=<support@microsoft.com> proto=SMTP helo=<xxx.xxx.xxx.xxx>
Oct 19 10:12:46 mailserver postfix/smtpd[2807]: lost connection after RCPT from 118-167-137-248.dynamic.hinet.net[118.167.137.248]
Oct 19 10:12:46 mailserver postfix/smtpd[2807]: disconnect from 118-167-137-248.dynamic.hinet.net[118.167.137.248]
Oct 19 10:14:03 mailserver postfix/smtpd[2807]: connect from 118-167-137-38.dynamic.hinet.net[118.167.137.38]
Oct 19 10:14:04 mailserver postfix/smtpd[2807]: NOQUEUE: reject: RCPT from 118-167-137-38.dynamic.hinet.net[118.167.137.38]: 554 5.7.1 <s2288@mail2000.com.tw>: Relay access denied; from=<p5.p5@hotmail.com> to=<s2288@mail2000.com.tw> proto=SMTP helo=<xxx.xxx.xxx.xxx>
Oct 19 10:14:04 mailserver postfix/smtpd[2807]: lost connection after RCPT from 118-167-137-38.dynamic.hinet.net[118.167.137.38]
Oct 19 10:14:04 mailserver postfix/smtpd[2807]: disconnect from 118-167-137-38.dynamic.hinet.net[118.167.137.38]
Oct 19 10:14:52 mailserver postfix/smtpd[2807]: connect from 118-167-137-248.dynamic.hinet.net[118.167.137.248]
Oct 19 10:14:52 mailserver postfix/smtpd[2807]: NOQUEUE: reject: RCPT from 118-167-137-248.dynamic.hinet.net[118.167.137.248]: 554 5.7.1 <support@microsoft.com>: Relay access denied; from=<support@microsoft.com> to=<support@microsoft.com> proto=SMTP helo=<xxx.xxx.xxx.xxx>
Oct 19 10:14:52 mailserver postfix/smtpd[2807]: lost connection after RCPT from 118-167-137-248.dynamic.hinet.net[118.167.137.248]
Oct 19 10:14:52 mailserver postfix/smtpd[2807]: disconnect from 118-167-137-248.dynamic.hinet.net[118.167.137.248]
Oct 19 10:15:54 mailserver postfix/smtpd[2807]: connect from 118-167-137-38.dynamic.hinet.net[118.167.137.38]
Oct 19 10:15:54 mailserver postfix/smtpd[2807]: NOQUEUE: reject: RCPT from 118-167-137-38.dynamic.hinet.net[118.167.137.38]: 554 5.7.1 <s2288@mail2000.com.tw>: Relay access denied; from=<p5.p5@hotmail.com> to=<s2288@mail2000.com.tw> proto=SMTP helo=<xxx.xxx.xxx.xxx>
Oct 19 10:15:55 mailserver postfix/smtpd[2807]: lost connection after RCPT from 118-167-137-38.dynamic.hinet.net[118.167.137.38]
Oct 19 10:15:55 mailserver postfix/smtpd[2807]: disconnect from 118-167-137-38.dynamic.hinet.net[118.167.137.38]
Oct 19 10:16:30 mailserver postfix/smtpd[2807]: connect from 118-167-137-248.dynamic.hinet.net[118.167.137.248]
Oct 19 10:16:31 mailserver postfix/smtpd[2807]: NOQUEUE: reject: RCPT from 118-167-137-248.dynamic.hinet.net[118.167.137.248]: 554 5.7.1 <support@microsoft.com>: Relay access denied; from=<support@microsoft.com> to=<support@microsoft.com> proto=SMTP helo=<xxx.xxx.xxx.xxx>
Oct 19 10:16:31 mailserver postfix/smtpd[2807]: lost connection after RCPT from 118-167-137-248.dynamic.hinet.net[118.167.137.248]
Oct 19 10:16:31 mailserver postfix/smtpd[2807]: disconnect from 118-167-137-248.dynamic.hinet.net[118.167.137.248]

```

It seems there's no problem because Postfix is not sending the message. But I want to prevent someone filling my logs.

How can I say to my firewall (ufw) to block an IP for 5 hours after 3 failed attempts to use my mail server?

I thought about changing SMTP port number but that way, I won't receive my mail.

Thank you for your help.

---

### Post by Drezard on 2008-10-19
Sorry, I'll stop trying to login, thought it was my mail server. Kidding...

I would use netfilter (iptables) or ufw to block that host completely. I'm not quite sure how to do this but, I'm sure a simple ufw tutorial should teach you how. 

Just checking my postfix server to see if I can find how to change POP's port. I'll post results if I find it. But once you change it remember to unblock the new port in ufw.

Daniel

---

### Post by HermanAB on 2008-10-19
Put this rule in /etc/rc.d/rc.local or some such:
iptables -A INPUT -p tcp -m state --state NEW \
-m limit --limit 30/minute --limit-burst 3 -j ACCEPT

That will protect your server against almost all abuse.

Cheers,

Herman

---

### Post by cdenley on 2008-10-20
I use fail2ban to block those attacks.

---

### Post by ngmachado on 2008-10-27
Hi,

Thank you for your help. I'm now using fail2ban to block abusive attempts for 24h. If they keep trying for a week I'll create a firewall rule to deny the ip range. :)

Now I'm trying to change the POP3 port. I'm the only user of the system so since my Mail application allows me to use a port different than the default (110) I think everything will be alright.

Does anyone know how to do that?

Thanks.

---

### Post by ngmachado on 2008-10-27
Hey,

It seems quite uncommon to change the default pop3 port, but I managed to find what I was looking for.

In /etc/courier folder you'll find 4 daemon files: pop3d, pop3d-ssl, imapd, imapd-ssl.

On these files there are a PORT=XXX option. Just change to the port you want and restart the daemon.

```

sudo /etc/init.d/courier-imap restart
sudo /etc/init.d/courier-imap-ssl restart
sudo /etc/init.d/courier-pop restart
sudo /etc/init.d/courier-pop-ssl restart

```

Please note: if you're not using IMAP or SSL connections you also have the option to disable these services. Perhaps it'll save some memory. :)

---

