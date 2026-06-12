---
title: "Postfix &amp; external mail server for same domain"
date: 2009-12-14
forum: Server Platforms
---

### Post by aschlosberg on 2009-12-14
I have a web server set up for domain.com but have the MX record for domain.com pointed at a different server. If I try and send mail from the web server (using mail or PHP) it does not let me because Postfix believes that the mail should be delivered locally.

I get this message in the logs:

> Dec 15 15:27:15 www2 postfix/smtp[5402]: 014A977828F: to=<user@domain.com>, relay=none, delay=0.04, delays=0.03/0/0.01/0, dsn=5.4.6, status=bounced (mail for domain.com loops back to myself)I edited /etc/postfix/main.cf to remove mydomain from mydestination but it still doesn't work:

> #mydestination = $mydomain, localhost.$mydomain, localhost
mydestination = localhost.$mydomain, localhost

---

### Post by aschlosberg on 2009-12-15
Bump... anyone? Please :)

---

### Post by chipper_farley on 2009-12-16
If I understand you correctly, you have two servers...one is a web server and one is a mail server.  You have a web app or something on the web server trying to send email but it is never leaving the web server.  What is your web server using for an SMTP, itself or is it relaying through the mail server?

---

### Post by aschlosberg on 2009-12-17
That's correct chipper. It is using itself for outgoing mail.

If it is relevant; the mail server is provided by a third party and I do not have any control over it.

---

### Post by chipper_farley on 2009-12-17
I'd try making the mydestination=localhost only.  That should make it to where the only mail the server would accept was local mail.  I'm not positive on that though.  My experience in the past with relaying has been that it's a pain due to spam filtering on the receiving end of emails.  Because of that, I usually try to relay through a different machine that's already successfully working for me.  If this doesn't work, you might configure your web server to either relay through your email server or an SMTP server provided by your ISP. 

Hope this helps.

---

### Post by aschlosberg on 2009-12-17
Thanks chipper. Much appreciated.

I'll give both a try. I've been trying to avoid putting another step in the process by including a relay server but it may just be inevitable.

---

### Post by oneloveamaru on 2009-12-17
You should use a mail relay for a few good reasons. Postfix is super super easy to configure to use a mail relay.

If you set mydestination=localhost, that is exactly what you want to avoid, the mail server trying to deliver mail to the "localhost".

There should be a relayhost= in the conf file somewhere. Use it.

---

### Post by aschlosberg on 2009-12-23
Solution:

The error "loops back to myself" is caused by two simultaneous scenarios. mydestination does not include domain.com while at the same time the MX record for domain.com does point at the web server.

Thus PostFix looks at the MX record and then tries to deliver the mail locally. When it does not find domain.com in mydestination it would look at the MX record again and cause the loop.

Note: this was not my fault - I had checked the MX records and they pointed to the mail server. However when the web host installed Ubuntu they configured it to use their own name servers. Their name servers had records for our domain despite the fact that they shouldn't have because they were not the authoritative server. To check for this:

> dig domain.com mxDo this from the server itself and check what is returned. If this is not correct:

> dig domain.com nsAnd check that it is the correct name server. If not you should change the name server in /etc/resolv.conf and flush the DNS cache using:

> /etc/init.d/dns-clean start

---

