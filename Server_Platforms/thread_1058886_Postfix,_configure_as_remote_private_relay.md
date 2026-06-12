---
title: "Postfix, configure as remote private relay"
date: 2009-02-03
forum: Server Platforms
---

### Post by batfastad on 2009-02-03
Hi everyone
Fairly new to Ubuntu and postfix - only used postfix to configure a local mail relay.

But we're looking to get a dedicated server to act as a remote private relay for our email newsletter service... about 3,000 subscribers per day.
We already have an Exchange server which handles all our incoming mail.

1) Does anyone have suggestions at what config directives I need to look at?
So far I think I need to set:
mynetworks = 127.0.0.0/8, our-static-ip
myhostname = mail2.domain.com
mydomain = domain.com

2) How do I convert our office's WAN static IP to the CNID notation required by the mynetworks directive?

3) Is it adequate to just use mynetworks with our static ip, or should I also enable SMTP auth/TLS per this guide... [http://ubuntuforums.org/showthread.php?t=990582](http://ubuntuforums.org/showthread.php?t=990582)?

4) We send the newsletters from [email]noreply@domain.com[/email]
Do I need to specify any settings to control the bounce backs/undeliverable msgs?
Or will the bounces just find their way to our main mail server by looking at the MX records for the domain?

5) DNS
We just want this server to handle outgoing mail, so guess I don't add the new dedicated server as an MX record.
I just need to add an A and CNAME for mail2.domain.com to point to the server's IP.
But will the server provider have to change the hostname or set up a PTR record or anything?

6) Anyone recommend a provider of ubuntu virtual private servers?
I've been looking into layershift so far and they provide CentOS which I've never used before.

I'd really appreciate it if someone could help me out with these basic Qs ;)

Thanks, B

---

### Post by batfastad on 2009-02-03
Anyone?
I'd really appreciate some advice on this!

Cheers, B

---

### Post by HermanAB on 2009-02-03
Use nullmailer as a mail relay.  That one is as simple as it gets.

Cheers,

Herman

---

### Post by batfastad on 2009-02-03
Hi Herman
Thanks for the suggestion, from this info though ([http://packages.ubuntu.com/dapper/nullmailer](http://packages.ubuntu.com/dapper/nullmailer)) it seems nullmailer is only designed to send to "a fixed set of smart relays"

I'm looking to have a remote postfix installation sending our email newsletters out directly to the internet.
Would nullmailer be able to do that?

Cheers, B

---

### Post by HermanAB on 2009-02-03
OK, then you need either a full Postfix, Qmail or Citadel mail server.  Installing Postfix/Qmail can be painful, while Citadel takes about 20 minutes using the Easy Install script and is zero maintenance.

For a mail server to work, you need proper A, PTR and MX records and a FQDN.  In your case, you can eliminate the MX record, since it is outgoing only, unless you want to get rid of the Exchange server and let Citadel handle it all. (You can literally replace dozens of Exchange servers with a single Citadel server and the users will be none the wizer).

So, you can do battle with Postfix for the next week or two, or you can install Citadel and have it working in a jiffy - your choice!

Cheers,

Herman

---

