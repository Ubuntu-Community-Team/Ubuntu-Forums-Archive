---
title: "What is the easiest way to create POP/SMTP server"
date: 2008-12-14
forum: Server Platforms
---

### Post by ttallos on 2008-12-14
What is the easiest way to create POP/SMTP server I am running Apache2. Do I need to install some type of DNS and create an A record and A MX record? Is it easy to set up a single user?

---

### Post by hictio on 2008-12-14
- You don't need Apache to run a mail server (unless you want to have a web mail, like [Squirrelmail](http://www.squirrelmail.org/), for instance).

- You need to register the IP address of the mail server as the MX for that domain (there might be more than one, but with one you are done).

- You need the SMTP port open, accessible over the internet, on the box that its going to have the MX record, so you can receive emails for that domain.

- You need to install, start, configure a couple of services on the server:

 - an MTA (Mail Transport Agent), to receive email from the internet, and move that mail to your INBOX -there might be others involved, but the main one is this one-.
On Ubuntu server, the MTA is [Postfix](http://en.wikipedia.org/wiki/Postfix_(software)), another one might be [Sendmail](http://en.wikipedia.org/wiki/Sendmail).

 - run a POP server, on Ubuntu Server, [Dovecot](http://en.wikipedia.org/wiki/Dovecot_(software)) is popular, secure and pretty easy to setup.

If this is a test project, you can start by creating the MX record for the domain; if this is a live system, with users complaining, that has to be the last step, after you have enabled all the services on the server (and tested those).

Don't forget to read: [Ubuntu Server Guide](https://help.ubuntu.com/8.10/serverguide/C/index.html), specially, the [Chapter 13. Email Services](https://help.ubuntu.com/8.10/serverguide/C/email-services.html)

---

### Post by ttallos on 2008-12-14
Thank you for the help I have been working carefully following all the directions for setting up postfix. I need Apache2 to server my website and I am happy it is up and running fine. The main question is how so I turn this machine into a DNS server so I can use it to set up an MX record?

---

### Post by hictio on 2008-12-14
Ok, a question, is this server going to be a public DNS & email server?

By public I mean that its going to serve as the master DNS for a domain that anyone can lookup over the internet, or just be going to be used as an internal DNS server on your LAN.

The same goes for the email server, is it going to receive emails over the internet for your domain?

Regarding the DNS setup, once again, take a look at this: [Chapter 7. Domain Name Service (DNS)](https://help.ubuntu.com/8.10/serverguide/C/dns.html).
The instructions are pretty straight forward, post back any question that you might have.

---

### Post by HermanAB on 2008-12-15
Definitely the easiest mail system is Citadel: [http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

You can have it up and running in about 20 minutes.  It is maintenance free, does every mail protocol ever invented and it Just Works (TM).

I have run Sendmail and Postfix for many years, but since the Citadel easy install script was created, it just blows their socks off.  Citadel is very old actually - dates back to the early 80s - and consequently very stable and mature.

Cheers,

Herman

---

### Post by gtdaqua on 2008-12-15
[Zimbra]("http://www.zimbra.com/") is quite easy to setup. It comes with Anit-Spam and Anti-virus automatically and has an excellent Web-based Admin UI. This is an enterprise-class production-grade app that can be used by smaller segments too. With each month, the product is defintely getting better.

It supports POP,IMAP etc with malware content checking.

Install the dependencies and run the Zimbra installer. Administer via Web Console. As easy as that.

---

### Post by ttallos on 2008-12-15
>Ok, a question, is this server going to be a public DNS & email >server?

>By public I mean that its going to serve as the master DNS for >a domain that anyone can lookup over the internet, or just be >going to be used as an internal DNS server on your LAN.

This is a public domain with a domain name anytime someone types in  mydomain.com they see my site. On the site I have a contact me page with a form that will send me an email.

>The same goes for the email server, is it going to receive >emails over the internet for your domain?

Yes this domain is going to recieve emails over the internet and send too.

Thanks for the citidel idea. I followed the directions exactilly and it didnt work for some reason on the postfix. I only have 1 email address that I want to set up anyway. It is easy to set up an MX record and I just might get to that today.

---

### Post by Ferret-Simpson on 2008-12-16
Please, for the love of all the gods! Don't use Pop3.

Every email client and mobile device in he last 15 years supports IMAP. POP3 is a byproduct of the days of low bandwidth, and has negligible practical use these days. For your own sakes (When you get a blackberry, iphone, WM6 Mobile or even just a second desktop/laptop) use IMAP.

---

### Post by HermanAB on 2008-12-16
Note that Citadel has a bunch of security checks built in, so if your server is not configured properly, then Citadel will refuse to send email.  Notably, your hostname must be a FQDN and it must resolve in DNS with A, MX and PTR records.

Citadel is very efficient and can be used to handle from a single user, up to tens of thousands of users.  You can literally replace dozens of MS Exchange servers with a single Citadel server.  For demo purposes, I have installed Citadel on an Eee PC 701!

Cheers,

Herman

---

### Post by ttallos on 2008-12-17
Thats great information! I got Postfix up and running to recieve but it wont send mail or reply . Dovecott is a pain I keep getting no socket errors when I try to get my email client to download email?? I am able to send email from my email client just cant recieve. I will keep trying till I get it. Unfortunatelly I am a novice.

---

### Post by Dr Small on 2008-12-17
Yeah, why POP3? Definitely go with IMAP.

---

### Post by Ferret-Simpson on 2008-12-20
Are you using SSL on your SMTP outgoing? I think that may be the same issue I'm having. As soon as I have any idea of a fix, I'll let you know. Check out the "Ubuntu Server Guide" for great howto's on setting up this stuff. :)

---

### Post by albinootje on 2008-12-20
> **ttallos said:**
> Thats great information! I got Postfix up and running to recieve but it wont send mail or reply . Dovecott is a pain I keep getting no socket errors when I try to get my email client to download email?? I am able to send email from my email client just cant recieve. I will keep trying till I get it. Unfortunatelly I am a novice.

Did you follow a certain howto ?
If so, can you tell us which one ?

---

