---
title: "How to send emails target on to Inbox and not smap?"
date: 2018-12-03
forum: Server Platforms
---

### Post by juanferaviles on 2018-12-03
Hi, i´m using sendmail on xampp to send email from my website app, but it seems to be targeting to spam and not to Inbox ... i know i have to put something like txt or spf where is hosted the domain but dont remember well.
My email is pointing to GSuite, and i´m using Ubuntu Server 18.04 with xampp as webserver. Tks.
I mean, when i tested my webapp and check the receiving mail i add my email as not spam, but...what about my users when try to get that emails (are for the forrgot email thing) these emails are going to go to spam.

---

### Post by TheFu on 2018-12-03
If the static IP for your server is on a spammer IP list, you'll need to get that cleaned up first. I was on 1 list for an ISP for 6 yrs because one of their customers SENT me an email and I responded back to the person to let them know their account had been hacked.

Next, implement both SPF and DKIM DNS records.  The SPF is pretty easy.  It tells everyone that email for your domain can only originate from a few IPs and nowhere else.  You can provide absolute requirements for definitely good IPs. This is stronger that saying "usually" which the SPF spec supports.  There are web-tools that will generate the SPF information for your DNS txt record. Of course, there are millions of examples inside public DNS records that you can look at for ideas.   **dig  gmail.com txt**, for example. Mine works differently than gmails. I specify a subnet with IPs spelled out explicitly.

I haven't needed to implement DKIM.

Of course, I'm assuming the server isn't located inside a spammer-friendly data center or at the end of a residential internet connection.  There's basically no way to get those types of places off the spammer list.  

I should mention that from time to time, my email servers block gmail when they get really spammy for an hour or so.  I'm pretty aggressive against spam and block huge spammy subnets in some parts of the world totally.  Not all businesses can do that.  My country has sanctions against a number of others, so we block them by policy.

---

### Post by juanferaviles on 2018-12-04
Tks for answer: Look, i´ve searched and im not in a blacklist. By the other side it seems to be different ways to made SPF configuration.
In my actual configuration my web site has a domain (lets call it domain1), my server has no defined domain, still has the localhost and i´m sending the emails (it is a php website who is sendind mails to restore password) and that email is using my company email (domain3). As you can see, im not in the professional configuration right now but the emails are sending but obiously im telling to my users in the send script that the have to look for my email in the spam folder. Actualliy from my script, emails are sendng by domain3 because thats the configuration in my script php, but is not by my domain 3 that emails are targeting on spam folder, its for the server, who appear in the emails when are received with the name of the server for example "dc07" and "localhost".
So i would like to configure all this as easyer possible way, if its possible with domain 1 for example. Thks. I appreciate if you can give a stronger ligh for where to start. Tks.

---

### Post by juanferaviles on 2018-12-04
Duplicate.

---

### Post by TheFu on 2018-12-04
We cannot control what any remote email server does.  We can only provide suggestions for our domain that email from it comes from some exact IPs and should never come from anywhere else.  

If you are forced to use some email/SMTP-gateway by the data center AND that relay changes the FROM to their domain, there isn't much you can do besides contact them and ask for help.  They should be able to allow your server to directly send/receive email without going through their gateware or they might be able to allow your domain to be in their whitelist for passthru.

I don't think there are any other options within the constraints.

---

### Post by SeijiSensei on 2018-12-04
0) You cannot send mail as someone@localhost.  It must come from a real domain.  See (3) below as well. 

1) Make sure forward and reverse DNS resolution for your server match exactly.  Both addresses need to registered in the public DNS.

2) SPFv1 is very easy to implement.  Add a TXT record to the domain section of your DNS (where the NS and MX records reside) like this:

```
		IN	TXT	"v=spf1 a:server.example.com ~all"
```

replacing "server.example.com" with the fully-qualified name of your server.  Like The Fu, I don't use DKIM either.

3) Make sure the sender address comes from a fully-qualified domain.  Also avoid using "root" as the sender's name.  Something like "bounces@example.com" is a better SMTP envelope address than "root@example.com."  Examine the headers of one of the messages you sent.  What is in the "Return-Path" field at the top of the message?

4) After all of this figure out how to incorporate the correct sender address into the software you are using.  Mail sent to that address should be routed to a real mailbox.  That is the address to which non-delivery notices are sent by temote mail servers.

---

### Post by juanferaviles on 2018-12-04
> **SeijiSensei said:**
> 0) You cannot send mail as someone@localhost.  It must come from a real domain.  See (3) below as well. 

1) Make sure forward and reverse DNS resolution for your server match exactly.  Both addresses need to registered in the public DNS.

2) SPFv1 is very easy to implement.  Add a TXT record to the domain section of your DNS (where the NS and MX records reside) like this:

```
        IN    TXT    "v=spf1 a:server.example.com ~all"
```

replacing "server.example.com" with the fully-qualified name of your server.  Like The Fu, I don't use DKIM either.

3) Make sure the sender address comes from a fully-qualified domain.  Also avoid using "root" as the sender's name.  Something like "bounces@example.com" is a better SMTP envelope address than "root@example.com."  Examine the headers of one of the messages you sent.  What is in the "Return-Path" field at the top of the message?

4) After all of this figure out how to incorporate the correct sender address into the software you are using.  Mail sent to that address should be routed to a real mailbox.  That is the address to which non-delivery notices are sent by temote mail servers.

This is more understandable to me but...look: I want to know as in my atachedd image if there is right. Where are the grey space is my domain name.
[IMG]https://imgur.com/DIZOiHs[/IMG]
[IMG]https://imgur.com/DIZOiHs[/IMG]

---

### Post by TheFu on 2018-12-04
The setting of your /etc/hosts file with a hostname doesn't matter to remote systems.  It is helpful only on _this_ machine.  Other machines have to know the LAN IP or public DNS IP depending on where they are coming from.

postfix has  a "myhostname" option in the main.cf that needs to say the public hostname.domainname you are using for outbound email.

 If you aren't certain, the DNS stuff would be easier to validate if we knew the name at least for a few hours. Then you can edit the post to remove it, if you like.

---

### Post by juanferaviles on 2018-12-04
> **TheFu said:**
> The setting of your /etc/hosts file with a hostname doesn't matter to remote systems.  It is helpful only on _this_ machine.  Other machines have to know the LAN IP or public DNS IP depending on where they are coming from.

postfix has  a "myhostname" option in the main.cf that needs to say the public hostname.domainname you are using for outbound email.

 If you aren't certain, the DNS stuff would be easier to validate if we knew the name at least for a few hours. Then you can edit the post to remove it, if you like.

Well i have not problem with that but, first i woulld like to go forward a little bit more... i´m not using Postfix, i´m using Sendmail.

---

### Post by SeijiSensei on 2018-12-06
Regardless of what you're using, remote mail servers cannot send messages to you unless you have a fully-qualified public domain like ubuntuforums.org.  For that, you need to come up with a domain name, then sign up with a registrar and pay the fee.  These days it can cost only $5-15/year to register a name.  After that you would need to create an "MX" record that points incoming mail to your server.

Even if you only want to send outbound mail, these days you still need a domain to pass the checks at most major mail services.  A SPF record helps here, too.

I use directnic.com myself.  A little more expensive than places like GoDaddy but very responsive to support requests.  They survived hurricane Katrina.

---

