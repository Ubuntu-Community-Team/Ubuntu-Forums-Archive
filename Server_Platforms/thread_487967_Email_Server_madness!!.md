---
title: "Email Server madness!!"
date: 2007-06-29
forum: Server Platforms
---

### Post by TorchlightJay on 2007-06-29
So ya, I have an Ubuntu Feisty system that I made into a mail server. It is currently running postfix, dovecot and hoepfully squirrelmail, by running, I mean they are installed and work. I configure using Webmin1.350 but it's driving me crazy. I don't know where to start, I've read a lot of tutorials nd I don't know how to set it up to where I can get an email sent to [email]user@blah.net[/email] and have them send mail. Also, how do you name the server mail.blah.net so that it shows up as [email]user@blah.net[/email] when you email something rather than user@localhost? Thanks all. Regads,

---

### Post by DDuong on 2007-06-29
Hi Torch,

I hope my reply here can help you out.  I also created a mail server at home but instead of Ubuntu I'm using Debian (sarge) it's somewhat the same anyways.

First thing, you need to register your domain on GoDaddy (you can choose another one other than GoDaddy of course but I'm using GoDaddy and I love it), so for this example we will use "blah.net".  I only pay like 5 bucks a year to register my domain so it's pretty cheap.

Second, you will need a DNS server (which you can also install on the same box as your mail server).  I myself, use BIND.  So you can look around the internet to read up on how DNS works because you will need to know about DNS records such as A and MX (mail) records. 

Basically you setup GoDaddy to point to your ip address which is your DNS server.  At that point, the records will do it's job

Here is a pretty good HowTo on DNS:

[http://www.howtoforge.com/traditional_dns_howto](http://www.howtoforge.com/traditional_dns_howto)

Not sure how your mail server is setup but for me I have it setup using virtual users and domains with postfix (so this involves with MySQL).

I hope this helps.  And if anyone else is reading this, correct me if I'm wrong :)

Thanks!

---

### Post by crazyjx23 on 2007-06-29
Look at Meldware server. It works pretty nicely for me.

---

### Post by TorchlightJay on 2007-07-01
Cool, I have GoDaddy right now for my "blah.net" domain. What in the MX and DNS records do I need to change/setup in order to make this work for mail.blah.net? Is there anything else I need to change as well?

Also, I want to host like a few domains like blah.net, example.com and sample.org on one server. currently I have virtual domains running on apache so I don't see any reason why I shouldn't do it with say Meldware. Is this possible?

---

### Post by DDuong on 2007-07-01
> **TorchlightJay said:**
> Cool, I have GoDaddy right now for my "blah.net" domain. What in the MX and DNS records do I need to change/setup in order to make this work for mail.blah.net? Is there anything else I need to change as well?

The link I gave you in my previous post will give you a basic understand how it works and it should answer all of your questions.

> **TorchlightJay said:**
> Also, I want to host like a few domains like blah.net, example.com and sample.org on one server. currently I have virtual domains running on apache so I don't see any reason why I shouldn't do it with say Meldware. Is this possible?

This part I have no idea since I've never used Meldware before.

---

### Post by TorchlightJay on 2007-07-02
I see. Well I was looking at my DNS server and a lot of it looks familiar to GoDaddy, do I need to set settings in my domain server and GoDaddy or do I just refer GoDaddy to my own DNS server? I am just wondering if I may be duplicating stuff

---

### Post by VorDesigns on 2007-07-02
DNS:  In order to maintain your own DNS, you must have two DNS servers running to be authoritative for your domain; while I don't know anything about GoDaddy, several of my colleagues use and recommend GoDaddy as their DNS provider.  Unless you are willing to maintain the necessary equipment, let a third party like GoDaddy handle your DNS.  If you need to make regular changes to a large volume of pointers, it may be worth considering direct DNS management but for small, generally static domains, it isn't worth the maintenance requirements to do it yourself.  I maintain about thirty domains using more than two DNS servers spread out to multiple locations for redundance.
rDNS:  Once you have established your DNS pointers for the server and the MX record, the next step is to get your revers DNS record set.  The reverse DNS record is simply the opposite of what DNS is.  When you enter server.blah.net, DNS resolves to the IP address.  reverse DNS does just the opposite, when you enter the IP address, reverse DNS resolves to the server.blah.net FQDN name.
Why would I care you ask?  Many legitimately run/configured mail servers will reject mail from smtp connections with names different than their rDNS resolution.  Also, many BlackHole system automatically assume SPAM from dynamic residential IP addresses.
Once you have that handled; if you are providing SMTP relay to your users outside of your private network, consider spending the time to configure a secure authentication mechanism; I have been working on this in another thread [Postfix Dovecot on Ruby Rails.]("http://ubuntuforums.org/showthread.php?t=398866")  I will caveat that with the fact that I don't know for sure that I have the SASL/TLS authentication working correctly but at least I have tried.  There are mechanisms in Dovecot available for providing hooks into postfix for the user authentication.  It wouldn't do to get Black Holed.
While you are at it, you might consider pop3s for those users needing to obtain their mail outside of your local network as well.  Dovecot handlles that well.

---

### Post by DDuong on 2007-07-02
> **TorchlightJay said:**
> I see. Well I was looking at my DNS server and a lot of it looks familiar to GoDaddy, do I need to set settings in my domain server and GoDaddy or do I just refer GoDaddy to my own DNS server? I am just wondering if I may be duplicating stuff

How I have it setup is the following:

1) I have GoDaddy point to *my* DNS server's IP address (which is my home IP address)

2) Then setup BIND on the DNS server

After you have all the records in place, and to test to make sure everything is fine, you do the following:

1) Open 2 terminals

2) 1 terminal will tail the /var/log/syslog so it'll tell you if there are any errors

3) The other terminal you will be restarting the named process or use RNDC or whatever.

And just keep playing with it.

The reason why I host my own DNS server is because it's a great learning experience, took me a month to actually get the hang of it and how all of it works.  I read so much information that I feel like my head is about to explode but it was well worth it.

---

