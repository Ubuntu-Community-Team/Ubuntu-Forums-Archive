---
title: "Restrict outgoing relay by ip address"
date: 2008-11-07
forum: Server Platforms
---

### Post by bsgcic on 2008-11-07
I am moving our email server from MS Exchange to Exim on Ubuntu 8.04.1. Version of Exim is 4.68.
As one of our security layers, we restrict authorization to send/relay email via our mail server from approved IP networks only. Whether this is a perfect method or not is irrelevant as it is but one of our security layers and we do not need to allow relaying from the world.
I need to be able to restrict the sending of outgoing email via our servers by IP but need to allow the receipt and delivery of inbound email from any IP.
I have spent over 2 weeks scouring the web, reading through the Exim specs and doc and other resources and have tried many many ways to achieve this goal but to no success yet and am becoming very desperate. I will need to give up on Exim if I cannot achieve this and have already invested a huge amount of time into this.
In summary:
* Restrict ability to relay outgoing email from our servers by IP (Normal encrypted TLS username/password also required of course)
* Allow inbound delivery of email from any IP
Does anyone know whether this can be done and if so how?
I would truly appreciate any help on this.
Regards,
Jeff

---

### Post by kidders on 2008-11-09
Hi there,

I'm not an exim user (I tend to use postfix), but from what I can tell, your exact situation seems to be covered in the documentation ... [http://docs.exim.org/current/spec_html/ch40.html#SECTrelaycontrol](http://docs.exim.org/current/spec_html/ch40.html#SECTrelaycontrol).

I hope that helps.

---

