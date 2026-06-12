---
title: "my domain name was spammed"
date: 2020-03-01
forum: The Cafe
---

### Post by Skaperen on 2020-03-01
a few months ago i registered an 8 character domain name.  i set up email reception on it that takes every possible user name the sender might use.  i set up the MX in DNS along with an A record.  that is the only setup.  there is no web site.  i never mentioned the name to anyone or anywhere.  it has received 5 spams, so far.  it looks like some spammer(s) has access to a list of new domain registrations.  4 of the spams look like they are from the same spammer.

---

### Post by sdsurfer on 2020-03-02
Do you have access to BoxTrapper, SpamAssassin, anything like that? The combination of the two stops most of this stuff. First I would trim down the email accounts to just what you need and configure anything else to just be refused. Don't bounce it, that's how some spammers send their crap - set the "from" to their target, send it to you, it "returns" to the target, using your domain as the actual sender. 

Then you can add an email verification filter, that is, the mail goes into a queue until the user registers/verifies the email. Nothing stops it completely, but these are great tools to slow it down.

---

### Post by EuclideanCoffee on 2020-03-02
Are you receiving all email with that domain name? If so, someone can simply send an email to any address on your domain and hit you. I would filter all email and only receive it on certain addresses such as "euclid" or whatever.

---

### Post by SeijiSensei on 2020-03-03
Yes, there are spammers who watch for new domain registrations and mail to [email]someone@newdomain.net[/email], often offering web design or app development services.

Are you in control of the server that receives mail for this domain? Then I'd recommend [MailScanner]("https://www.mailscanner.info/"), a comprehensive virus and spam scanning package that works with most SMTP exchangers like Postfix and sendmail. But first, I'd configure the mail server to only accept mail for designated account names as EucideanCoffee suggests.

---

### Post by QIII on 2020-03-03
I still get the occasional "Hi!  We are the best web programmers in Mumbai!" emails at my business email address on my company website.  A hazard you have to deal with if you leave an email address for potential clients to reach you.  It has gotten rarer and rarer.  Down to one or two a month.

If you control your mail server, add the spam filtering suggested.  If you don't, ask your provider.  If you don't have an email link(since you don't have a page), consider hiding your web registry information so they can't get a contact address from that.

Spammers can generate billions of possible combinations on a domain and spam every possible permutation of recipients -- all they need is one hit.

---

### Post by SeijiSensei on 2020-03-04
> **QIII said:**
> Spammers can generate billions of possible combinations on a domain and spam every possible permutation of recipients -- all they need is one hit.
Once in a while I get "dictionary attacks" against my public POP3 server.  A remote host will try to log in with dozens of likely account names like "jim" and "jessie" and "admin."  I've thwarted those to some degree by using xinetd's ability to refuse connections from hosts that make too many connection attempts in a short period of time. I believe you can do the same thing with iptables.

---

### Post by Skaperen on 2020-03-04
> **SeijiSensei said:**
> Yes, there are spammers who watch for new domain registrations and mail to [EMAIL="someone@newdomain.net"]someone@newdomain.net[/EMAIL], often offering web design or app development services.

Are you in control of the server that receives mail for this domain? Then I'd recommend [MailScanner]("https://www.mailscanner.info/"), a comprehensive virus and spam scanning package that works with most SMTP exchangers like Postfix and sendmail. But first, I'd configure the mail server to only accept mail for designated account names as EucideanCoffee suggests.

indeed, 4 out of 5 were for web design.  the 5th was in Chinese and included a huge blob.

the server is AWS SES.  i have it configured to drop all mail into an S3 bucket which i download from. i do this with 3 older domains, too.  i'm not really trying to block spam, yet.  i'm just curious about what they are doing these days.

one of the other domains is one which i added fake email addresses to Usenet posts some 20-ish years ago.  they spammed 'em pretty fast (once as fast as 26 minutes after it was first posted).  many of those are still being spammed, today.

---

### Post by lisati on 2020-03-05
Be careful if you're using "catch all" email addresses - a lot more unwanted email is likely to be allowed in.

As others have suggested, take a look at spam filtering options. When I ran my own postfix server a few years ago, I used a combination of DNSBLs (blacklists) and tools such as SpamAssasin. I configured the system to reject outright IP addresses listed in blacklists, and to modify the subject of the email to flag spammy emails identified by SpamAsssain. Emails flagged by either method can also be moved to your spam/junk folder, so they not only don't clutter up your inbox but can also be reviewed later and reported (e.g. by [SpamCop]("http://spamcop.net")) if necessary.

Whatever you do, DON'T blindly accept emails for delivery and then decide to "bounce" the rogue emails - because sender addresses are easily forged, this has a nasty tendency to hassle people who didn't send the email, and makes it harder to submit reports to the real sender's provider. It can also have the unintended consequences of making you look like a spammer.

---

### Post by Skaperen on 2020-03-06
it's a "catch all" because i want to catch all the spam.  that is the whole reason for setting this up.  there are no genuine email addresses in that domain, so i don't even have a real mail server running.  if i did have genuine email addresses in that domain, then i would most likely run a real mail server (probably Postfix) and run the anti-spam through that.  i still might front-end port 25 with my own process(es) to "play" with spammers, such as hanging their connection (blocking all IP traffic to and from their IP for a while before dropping the connection on my side).

---

