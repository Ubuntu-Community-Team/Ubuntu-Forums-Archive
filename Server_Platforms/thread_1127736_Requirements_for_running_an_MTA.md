---
title: "Requirements for running an MTA"
date: 2009-04-16
forum: Server Platforms
---

### Post by cjauvin on 2009-04-16
Hi everyone,

I'd like to run an MTA so that I can basically send messages from programs (PHP or Python). I don't mind not being able to receive messages though.

I know that there are many configuration options and things to consider, but while I've been googling for a couple hours, I have not been able to find satisfying answers to my basic questions.

First I'd like to know if my server setup basically allows for such a thing. My machine is an Ubuntu 8.04 web server that has a static IP and a domain name associated to it. This server has only two ports open: 22 (ssh) and 80 (web). The MTA I've been testing is Exim4, and I've been configuring it (with dpkg-configure) as an "internet site" (ie. not using a smarhost).

So a first question would be: is it possible to use an MTA (in outgoing mode only), if port 25 is not open inbound?. Exim does not seem to complain too much about it, but then I see in its log that the connection to my Gmail account (for instance) has timed out, after a couple of minutes.

While googling, I also see a lot of references to MX records, that can be associated to a domain name, and that point to a mail server. I don't know if my domain name has an MX configured, but if not, is it mandatory for a successful MTA-to-MTA transaction?

Finally if what I have in mind is not possible, I would need help understanding how a smarhost can act as an alternative solution.

I know this is asking a lot of questions.. but if someone could kindly help with all those uncertainties, it would be much appreciated!

Christian

---

### Post by Masuran on 2009-04-17
Running an MTA (basically just sending messages), doesn't require anything 'special'. 

No MX records, no open ports, nothing but a working internet connection.

I don't know why exim would complain about a timed out connection to your gmail account, basically an MTA connects to a mail server (by finding the server IP from MX records) and transmits a message.

To illustrate this, you can be an MTA using the telnet program: [http://www.rdpslides.com/webresources/FAQ00035.htm](http://www.rdpslides.com/webresources/FAQ00035.htm)

So in short, unless you want to setup a mail server that **receives** email, you don't need open ports, static IP or MX records for your domain.

---

### Post by Bachstelze on 2009-04-17
> **cjauvin said:**
> I'd like to run an MTA so that I can basically send messages from programs (PHP or Python). I don't mind not being able to receive messages though.

If you just want to send email, it's much simpler than you seem to think. ;) You don't even neet a full-fledged MTA, there is a great tool called [font="monospace"]ssmtp[/font] for this.

[http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/outgoing-only.html](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/outgoing-only.html)

> **Masuran said:**
> So in short, unless you want to setup a mail server that **receives** email, you don't need open ports, static IP or MX records for your domain.

You *do* need a static IP if you want to send out e-mail directly. As a measure against spam, most mailservers won't accept e-mail that comes from a dynamic IP.

---

