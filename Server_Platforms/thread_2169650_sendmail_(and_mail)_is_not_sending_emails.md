---
title: "sendmail (and mail) is not sending emails"
date: 2013-08-22
forum: Server Platforms
---

### Post by d6tr6tr on 2013-08-22
I've been trying to get sendmail to work but have a lot of problems. It  was hanging for 60 seconds every time I tried to use it, so I followed  suggestions from others ( [The sendmail 60 second delay | Symbiotix]("http://symbiotix.net/articles/sendmail-60-second-delay")  ) and changed "/etc/hostname" to have a FQDN and "/etc/hosts" to map  the server's IP to that FQDN. This eliminated the 60 second hang, but it  still does not send the emails!

I looked at my "/etc/sendmail.cf" and it has only:
```
0wlocalhost 

```
I tried changing the "localhost" part to the FQDN from /etc/hostname" but this still does not work.

When I restart sendmail, I get:

```
$ sudo /etc/init.d/sendmail restart 
 * Restarting Mail Transport Agent (MTA) sendmail                                                                                            hostname: Name or service not known                                                                                                                                       [ OK ] 


```

I then installed postfix, but that still did not fix the problem. What happens now when I do an ```
echo "test" | sendmail someemail@someplace.com
``` is that it returns without error but the email account never receives anything. I *believe* all necessary ports are open on the server, and I opened a port forwarding on port 25 in the router. What could be wrong?

---

### Post by TheFu on 2013-08-23
I don't know the answer. Sorry.  I have a few ideas, however.

Many ISPs block output email except through their email gateways. This is to reduce spam.

I stopped using sendmail (the top 2 most-hacked program on UNIX) around 1997 and have been using postfix since.   Sendmail is extremely complex, extremely capable, so if you outgrow what easier to use MTAs can do, then sendmail is what you need ... have you outgrown exim or postfix?

I have **never** attempted to send email directly with sendmail before. I use a small CLI client all the time - mail or Mail can be installed on Ubuntu easily. Try:
```
$ echo "test" | Mail -s "test subject" someemail\@someplace.com
```
Notice the escape is needed for the "TO" address.

You have DNS MX records setup for your domain too? Just asking.

It is hard to know how much email system you want from the question. Sendmail is usually for organization with extremely complex email needs. If you are an end user that just wants to leverage the ISP's email system, there are easier ways.  Please describe the server network connection a little and if this is on a residential connection, you'll never receive outside email through sendmail (or any MTA). You might want an MTA for your internal systems to send email to. however.

Anyway, I'd rather know that you really want a full email server and have the infrastructure for it, before trying to troubleshoot any more. Thanks for understanding.

---

### Post by d6tr6tr on 2013-08-23
> **TheFu said:**
> I don't know the answer. Sorry.  I have a few ideas, however.

Many ISPs block output email except through their email gateways. This is to reduce spam.

I stopped using sendmail (the top 2 most-hacked program on UNIX) around 1997 and have been using postfix since.   Sendmail is extremely complex, extremely capable, so if you outgrow what easier to use MTAs can do, then sendmail is what you need ... have you outgrown exim or postfix?

I have **never** attempted to send email directly with sendmail before. I use a small CLI client all the time - mail or Mail can be installed on Ubuntu easily. Try:
```
$ echo "test" | Mail -s "test subject" someemail\@someplace.com
```
Notice the escape is needed for the "TO" address.

You have DNS MX records setup for your domain too? Just asking.

It is hard to know how much email system you want from the question. Sendmail is usually for organization with extremely complex email needs. If you are an end user that just wants to leverage the ISP's email system, there are easier ways.  Please describe the server network connection a little and if this is on a residential connection, you'll never receive outside email through sendmail (or any MTA). You might want an MTA for your internal systems to send email to. however.

Anyway, I'd rather know that you really want a full email server and have the infrastructure for it, before trying to troubleshoot any more. Thanks for understanding.

I'm trying to get PHP to be able to send email (i.e. user submits contact form and PHP sends the email). By default this uses sendmail. I installed postfix but still cannot send email. I am not sure how to tell if it's my ISP that is blocking it or not. How would I check that?

---

### Post by TheFu on 2013-08-23
> **d6tr6tr said:**
> I'm trying to get PHP to be able to send email (i.e. user submits contact form and PHP sends the email). By default this uses sendmail. I installed postfix but still cannot send email. I am not sure how to tell if it's my ISP that is blocking it or not. How would I check that?

Postfix is a drop-in replacement for sendmail for 99.999999% of the uses.  In fact, on every Linux server that I know, postfix installs a /usr/sbin/sendmail binary that links to postfix. The MTA/SMTP interface to all outside programs is the same.
Even the local manpage says:
```
sendmail - Postfix to Sendmail compatibility interface
```

It really would help if you described your server's internet connection before we try anything else. 
Residential or business? 
Web-hosting or VPS or physical server in a cage?  
It is inside a commercial data center or out of a house?  
DSL, cable, T1, DS3, 100base-tx direct connections ... what?

Do you want to receive any email for this domain or just send?

---

### Post by d6tr6tr on 2013-08-23
> **TheFu said:**
> Postfix is a drop-in replacement for sendmail for 99.999999% of the uses.  In fact, on every Linux server that I know, postfix installs a /usr/sbin/sendmail binary that links to postfix. The MTA/SMTP interface to all outside programs is the same.
Even the local manpage says:
```
sendmail - Postfix to Sendmail compatibility interface
```

It really would help if you described your server's internet connection before we try anything else. 
Residential or business? 
Web-hosting or VPS or physical server in a cage?  
It is inside a commercial data center or out of a house?  
DSL, cable, T1, DS3, 100base-tx direct connections ... what?

Do you want to receive any email for this domain or just send?

Residential.
LAMP setup inside VirtualBox (Ubuntu)
Cable connection (50mps up, 10+ down)
Router: dd-wrt

I do not need to receive email, only send it. I'm not looking to send a lot of emails, I just need to be able to test PHP code that sends emails from contact forms.

---

### Post by TheFu on 2013-08-23
> **d6tr6tr said:**
> Residential.
LAMP setup inside VirtualBox (Ubuntu)
Cable connection (50mps up, 10+ down)
Router: dd-wrt

I do not need to receive email, only send it. I'm not looking to send a lot of emails, I just need to be able to test PHP code that sends emails from contact forms.

Thanks. That tells me more than you can imagine.

If you are on Comcast, TWC or Cox, then you'll need to use their email relay.  Some will require authentication, others will just trust the "from" address provided you are on their network.  In the postfix config, look to setup a smart-relay - **relayhost** is one of the settings in the main.cf file.  I use IP addresses to avoid non-matching domain errors.  I don't recall of the top of my head how to do the authentication - google "ubuntu postfix authentication ISP".  You will need to lookup the normal email sending settings for your ISP and translate those into what postfix ... /etc/postfix/main.cf needs.  Shouldn't be too hard, provided you aren't trying to spoof outbound email FROM addresses.  Use the ISP email address to start. After that works, you can try using other FROM addresses - it will probably work fine. The instructions here seem perfect - [http://jaredrobinson.com/blog/postfix-on-ubuntu-12-04/](http://jaredrobinson.com/blog/postfix-on-ubuntu-12-04/) 

For your virtualbox, the network settings (bridge or NAT) shouldn't matter for outbound much ... if you can surf from the VM, that should be good enough to use a relay.

Clear?

---

### Post by d6tr6tr on 2013-08-23
> **TheFu said:**
> Thanks. That tells me more than you can imagine.

If you are on Comcast, TWC or Cox, then you'll need to use their email relay.  Some will require authentication, others will just trust the "from" address provided you are on their network.  In the postfix config, look to setup a smart-relay - **relayhost** is one of the settings in the main.cf file.  I use IP addresses to avoid non-matching domain errors.  I don't recall of the top of my head how to do the authentication - google "ubuntu postfix authentication ISP".  You will need to lookup the normal email sending settings for your ISP and translate those into what postfix ... /etc/postfix/main.cf needs.  Shouldn't be too hard, provided you aren't trying to spoof outbound email FROM addresses.  Use the ISP email address to start. After that works, you can try using other FROM addresses - it will probably work fine. The instructions here seem perfect - [http://jaredrobinson.com/blog/postfix-on-ubuntu-12-04/](http://jaredrobinson.com/blog/postfix-on-ubuntu-12-04/) 

For your virtualbox, the network settings (bridge or NAT) shouldn't matter for outbound much ... if you can surf from the VM, that should be good enough to use a relay.

Clear?

Thank you. I will try the link you sent, but I already tried this: [http://devnul.9c0.com/POSTFIX_Configure_Postfix_Relay.html](http://devnul.9c0.com/POSTFIX_Configure_Postfix_Relay.html) and it did not work. Do you know how I can undo everything in that? I am unable to list the certs/ca's in the openssl database and as a result unable to revoke the cert I created. Do oyu know how to do that? I want to start from scratch.

---

### Post by SeijiSensei on 2013-08-23
> **d6tr6tr said:**
> I'm trying to get PHP to be able to send email (i.e. user submits contact form and PHP sends the email). By default this uses sendmail. I installed postfix but still cannot send email. I am not sure how to tell if it's my ISP that is blocking it or not. How would I check that?

First of all, use either Postfix or sendmail and purge the other package if you have not done so already.  I believe Ubuntu automatically deletes sendmail when Postfix is installed, but I'd check and make sure.

The sendmail.cf file you posted is clearly not the one included with the sendmail-cf package or created via the m4 method that package enables.  I use sendmail, and my sendmail.cf is over 1,100 lines long without comments.

As for testing, the simplest solution is to try and connect to a known SMTP server on port 25.  You can use the telnet client included with Ubuntu for this like so:

```
$ telnet gmail-smtp-in.l.google.com 25
```

If you can connect successfully the server will reply as follows:
```

Trying 173.194.68.27...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP h5si338677qcz.54 - gsmtp

```

If telnet times out, you cannot send to SMTP servers and need to work out how to do this with your ISP.  If your server is connected using a residential Internet account, be prepared to hear the ISP's representative tell you that servers are forbidden on your connection under your Terms of Service.

---

### Post by TheFu on 2013-08-23
> **d6tr6tr said:**
> Thank you. I will try the link you sent, but I already tried this: [http://devnul.9c0.com/POSTFIX_Configure_Postfix_Relay.html](http://devnul.9c0.com/POSTFIX_Configure_Postfix_Relay.html) and it did not work. Do you know how I can undo everything in that? I am unable to list the certs/ca's in the openssl database and as a result unable to revoke the cert I created. Do oyu know how to do that? I want to start from scratch.

Definitely remove **any** non-postfix MTA using the package manager.  All of them will try to setup a listener on port 25. Only 1 of them will succeed and you only want 1 MTA, postfix, doing that.

Having an email server sending outbound email from a home address for testing really isn't that big of a deal. For a long time, setting up an MTA was the ONLY way to get outbound email to work at all.  UNIX email clients assumed a sendmail-like MTA was installed on any system where outbound email was desired.

To start over with any package install, use purge and just install again.
```
$ sudo apt-get purge sendmail postfix exim
$ sudo apt-get install postfix
```

Thanks to SeijiSensei for reminding us to remove all MTAs that we aren't using. We have different opinions about the best MTA, but if your postfix main.cf is over 25 lines, I think you did something wrong. Much easier than sendmail, IMHO and much less likely to be misconfigured, misused by outsiders and more than powerful enough for anyone except an email-specific business (as in a business that handles email as their primary income).  If you have less than 20 domains and 20 locations, postfix can easily handle email for you. Of course, there will be other opinions for you to consider.

In the future, when reading instructions from blogs on the internet ... watch out when people say it took them a long time to figure something out that should be relatively simple if the instructions seem complicated.  Also - unless you are completely desperate, it is probably best to avoid non-debian-based instructions.  The gentoo folks seem to do things the hard way. ;)  If you really, really want to understand Linux, definitely install gentoo. You will learn a bunch.

Always, always check the **Ubuntu Community** and **Ubuntu Help** pages first for instructions. For servers, things don't change that much over time. The GUI stuff can be wildly different from release to release, however.

Sometimes it is hard to know what search terms to use - we've all been there. In general, I use "ubuntu" and the most specific terms for what I'm trying to accomplish possible.  "ubuntu postfix relay ISP" are the terms I used. "Relay" might not have been a term you knew about email servers, but if you are on a residential connection, you will need to relay all your outbound email thru their email gateway(s).

Anyway, hope this helps in some way and that I'm not misunderstanding your needs.

---

