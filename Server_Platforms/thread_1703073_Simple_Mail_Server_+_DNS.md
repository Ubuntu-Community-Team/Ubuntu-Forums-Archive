---
title: "Simple Mail Server + DNS"
date: 2011-03-08
forum: Server Platforms
---

### Post by jmacgowan on 2011-03-08
I have set up a simple mail server on an Ubuntu Server 10.10 machine that is hosted by a hosting company.

First, a little about my setup:
hostname of "mail.example.com"
Single server at IP "xx.yy.xx.yy"
Domain Name of "example.com" registered with GoDaddy that I would like to use for this server

Okay, now here's what I have done:
I pointed my domain name at my server's IP of xx.yy.xx.yy and I am able to see the same apache server at [http://xx.yy.xx.yy/](http://xx.yy.xx.yy/) and [http://example.com/](http://example.com/) so I would like to conclude that GoDaddy's DNS settings are working.

I've set up Postfix, Dovecot, and SquirrelMail.  From squirrelmail, I am able to log in as a UNIX user and send mail from my domain. (I can send an e-mail to my personal e-mail address and it will say that it's from "user@example.com") but emails sent back to [email]user@example.com[/email] are not delivered.  

First they were bounced back, then I changed the MX records at GoDaddy to "example.com." (including the period) and they no longer bounce back, but they are not delivered either.

In a stroke of genius I tried to send an e-mail to [email]user@[xx.yy.xx.yy[/email]] in an attempt to make sure the server itself was working, but that bounced back with the error "No A or MX record found at xx.yy.xx.yy
[SIZE=2]
So here is my question.  What is it going to take for emails sent to [email]user@example.com[/email] to actually be delivered to my server?

I would imagine that I would need some DNS records on my server, but I don't know the first thing about that, and all the guides I have found seem to be for setting up a local service only.

Any help is greatly appreciated, I understand it takes time to explain stuff like this.  Thanks in advance.
[/SIZE]

---

### Post by HermanAB on 2011-03-09
Howdy,

To run a mail server, you absolutely MUST have A, MX and PTR records in your DNS.

The best way to do that, is to buy a domain name from a registrar that also offers DNS service - most do, but not all - then you literally just use their web site to configure it.  They are all different, so I cannot tell you how.

BTW, I use Godaddy - reasonable combination of price and service.

---

### Post by Iker Etxebarria on 2011-03-09
Hi 
I'm not an expert but I get my mail server working after reading logs and googling.
So maybe reading /var/log/mail.log can be helpfull for you and us to see what is happening.

---

### Post by jmacgowan on 2011-03-09
Thank you for the replies, I finally resolved it a few hours after I posted this.

I actually do have a domain at GoDaddy, and I thought I set the DNS settings up correctly but it just wouldn't work.

Turns out, the problem was that my hostname on the machine was incorrect.  A simple change from mail.example.com to just example.com and BAM, you've got mail.

Thanks again!

---

