---
title: "[SOLVED] Securing postfix as sendmail relay only"
date: 2008-11-19
forum: Server Platforms
---

### Post by batfastad on 2008-11-19
Hi everyone

I've been configuring a new intranet server using Ubuntu Server 8.04, with Apache2 MySQL5 PHP5.
I wanted to have the ability to send email using the most excellent SwiftMailer PHP class, and the most reliable way of sending our email newsletters has been through sendmail and our ISPs mail relay.

I installed sendmail, but could not get our ISPs mail server configured as a smarthost. So following several other recommendations I removed sendmail, and installed postfix instead.
It seems postfix offers a drop-in replacement binary for sendmail - so I just tell SwiftMailer to act as if sendmail is installed and it all works fine. Configuring a smarthost in postfix was much easier as well.

On to my question:
I want to make sure that postfix on this particular server, doesn't accept any external connection requests.
So that only localhost can access postfix services.
I guess I should also disable POP/IMAP protocols in postfix as well, as the only task I want postfix installed for is to allow PHP to send mail through our ISPs SMTP server.

What config changes do I need to make to secure postfix on this server?
Or is it already sorted out "of the box"?

Thanks, B

---

### Post by HermanAB on 2008-11-19
You can drop all incoming packets on port 25 using iptables, using something like this in /etc/rc.d/rc.local:
iptables -I INPUT -p tcp -i eth0 -j DROP

Then, even if you configure Postfix wrong, the system will still be safe and your machine cannot become a Spam relay.

Cheers,

Herman

---

### Post by hictio on 2008-11-19
> **HermanAB said:**
> You can drop all incoming packets on port 25 using iptables, using something like this in /etc/rc.d/rc.local:
iptables -I INPUT -p tcp -i eth0 -j DROP

Then, even if you configure Postfix wrong, the system will still be safe and your machine cannot become a Spam relay.

Cheers,

Herman

One thing, tho, if you apply the iptables rules above, you'll loose not only access to your server's SMTP port, but any other service as well that might be listening on the eth0 NIC as well, so, if you apply that, be sure to have console or physical access to the server.

---

### Post by HermanAB on 2008-11-19
Heh, nice catch!

It should be this way:
iptables -I INPUT -p tcp --dport smtp -i eth0 -j DROP

---

### Post by MJN on 2008-11-19
> **batfastad said:**
> I guess I should also disable POP/IMAP protocols in postfix as wellThose services aren't provided by Postfix.

> [...] the only task I want postfix installed for is to allow PHP to send mail through our ISPs SMTP server.If that's your only requirement then you'd be better off going with [Nullmailer](http://untroubled.org/nullmailer/). It's in the repos, is binary-compatible (pretty much) with Sendmail and acts as a simple mail relay to other host(s).

The beauty of it is its simplicity which, given it satisfies your requirements, makes it ideal.

Mathew

---

