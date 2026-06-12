---
title: "Mail Server"
date: 2007-12-10
forum: Server Platforms
---

### Post by poisonmushroom on 2007-12-10
Hello,

today i have experimented with mail server, i installed all the programs mentioned in this tutorial ```
https://help.ubuntu.com/7.10/server/C/email-services.html
``` 

everything went ok, it looks working and everything but i have some serious questions.

Since i have a dynamic ip, i registered for a dynamic DNS service in [www.dy.fi](www.dy.fi) to create a domain for my server, i called it mushroom.gurut.be

if you go to this addres using your browser you'll see an Apache2 page and everything.

now my question is, i don't exactly know what to do after my mail server is set up? i mean, how do i make it work to send and recieve e-mail, create accounts for people and such?

in many configuration files i don't really know what to type as host-name, do i use mushroom? mushroom.gurut.be? mail.mushroom.gurut.be? i really have no clue, please if there are any professionals with this that can help me i would greatly appreciate it.

Huge thanks!

P.S: if i'm asked for a hostname, is it mushroom only or with .gurut.be? and if asked for domain what do i usually type?

---

### Post by kidders on 2007-12-11
Hi there,

> **poisonmushroom said:**
> If i'm asked for a hostname, is it mushroom only or with .gurut.be? and if asked for domain what do i usually type?Your hostname is the name of the mail server, but you should avoid explicitly stating it where possible, unless you're confident about your DNS configuration both inside and outside your LAN. Your domain name is normally whatever your MX record points to.

Since you have a dynamic IP, your next step should be to find someone to relay your mail for you. This is essential for a variety of reasons, including ...

**I - Incoming mail**
Should your mail server go offline or change IP, you will need some way of preventing email bouncing, or being delivered to the wrong place. Consider, for example, what might happen if ...[LIST]
[*]You acquire 12.34.56.78 from your ISP.
[*]A day or two later, you lose that address, and your ISP assigns it to someone else.
[*]The new owner of 12.34.56.78 is also running an SMTP server.
[*]Over the next few hours, as your DNS update propagates, your email is delivered to the wrong machine. This can happen for several hours, even if the TTL on your DNS records is very short, because (very annoyingly) many mail servers flout the caching rules.[/LIST]Best case scenario: Mail bounces.
Worst case scenario: Mail intended for you gets accepted by some stranger's mail server.

**II - Outgoing mail**
Very few SMTP servers will deliver mail relayed by IPs in well-known dynamic pools. Your address also has an inconsistent reverse lookup (mushroom.gurut.be -> 88.114.147.160 -> a88-114-147-160.elisa-laajakaista.fi), which is another red flag for mail servers. Again, the best case scenario is lots and lots of bouncing mail. The worst case scenario is where the target SMTP server accepts your mail, only to filter it later on for having a very high spam probability. Unfortunately, the latter is very common.

---

Anyhow, that's step 1. The other question you asked was about setting up mail accounts. In broad strokes, there are essentially two approaches ...

**Virtual hosting**
You hard-wire your box to consider itself the final destination for a variety of mailboxes (possibly a variety of domains too), none of which is in any way related to your network's domain, or the Linux user accounts set up on the mail server. Many people like this approach, because it's very flexible.

**"Normal" hosting**
If, for example, you have a machine called mushroom.gurut.be with a user account called "poisonmushroom", the email address poisonmushroom@mushroom.gurut.be actually *means* something, so a mail server running on that machine will happily accept mail & deliver it into that user's home directory. Normally, people would configure their mail server to accept mail for poisonmushroom@gurut.be as well ... but it only works because the user "poisonmushroom", and the domain "gurut.be" really exist.

Either approach may well work great for you, but it's still important to be aware of the distinction, because different HOWTOs take different approaches ... it's easy to get confused, when one person tells you to do one thing, and another suggests something completely different.

In general terms, virtual hosting requires more maintenance, but would be too impractical for organisations with multiple domains, or hundreds of user accounts.

I hope that helps.

---

