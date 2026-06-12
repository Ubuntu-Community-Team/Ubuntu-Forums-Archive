---
title: "Webmail Alternatives"
date: 2010-04-04
forum: The Cafe
---

### Post by Yuki_Nagato on 2010-04-04
What alternatives do I have to webmail?

As far as personal e-mail use that is.  It would be nice to have a way to keep separate work and personal accounts, and webmail (GMail) has filled this role for a while.

I am looking to break free from that, and gain more control over my e-mail.

What options do I have?

Can I do anything with a registered domain name?

The only ISP in my area blocks outbound port 25.  Now what?

---

### Post by lovinglinux on 2010-04-04
The only alternative to web mail is a mail client. There is Evolution, Thunderbird, Kmail and others.

There is also [SimpleMail](https://addons.mozilla.org/en-US/firefox/search/?q=SimpleMail) extension for Firefox, which is what I use, in conjunction with Gmail imap.

If you are looking for an alternative address that does make you look like using a free e-mail account, then you can register a domain and get a server. You will be able to setup various mail accounts. I guess you could also register a domain and get a service to forward the e-mails to a different address, without spending on web hosting.

> **Yuki_Nagato said:**
> The only ISP in my area blocks outbound port 25.  Now what?

Modern mail services like Gmail don't use port 25 for SMTP. They use a ssl port like 465.

---

### Post by Yuki_Nagato on 2010-04-04
Thank you.

I plan on scrapping Google's service for something else.  I was planning on registering a domain name, with a mailbox attached to it.  My server would then POP3 the mail and I would read it from my server.

But I am just kicking around ideas at this point.  The purpose?  I am trying to store my email somewhere that is less accessible to the rest of the world (law enforcement, advertisers, etc.).

I understand that copies of emails are potentially made at every relay in the 'mailing' process.  However, it appears too easy to monitor me if I store everything with a large e-mail provider (GMail, Yahoo, Hotmail, etc.).

---

### Post by juancarlospaco on 2010-04-04
*Da Squirrel...*

---

### Post by lisati on 2010-04-04
If you run your own web server and your ISP blocks port 25, there are options. The one I chose was ask my ISP to unblock port 25. I also had to set up port forwarding on my router. The catch was that for the unblocking to work, I had to arrange for a static IP address with them and pay an extra fee on my monthly bill for the privilege.
Other options include using fetchmail for incoming mail, and using your ISP's servers for outgoing mail from your server.

---

### Post by Bachstelze on 2010-04-04
> **lisati said:**
> 
Other options include using fetchmail for incoming mail, and using your ISP's servers for outgoing mail from your server.

Another option is to use No-IP's Mail Reflector service ($40/year).

---

### Post by Yuki_Nagato on 2010-04-04
lisati

I had not considered contacting my ISP about this.

Bachstelze

Good to know there are services to patch certain holes.

Thanks both of you.  This is what I was looking for.

---

