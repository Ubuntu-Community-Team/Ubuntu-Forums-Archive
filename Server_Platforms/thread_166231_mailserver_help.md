---
title: "mailserver help"
date: 2006-04-26
forum: Server Platforms
---

### Post by dphipps on 2006-04-26
I am trying to set up a mailserver but I have some questions.  I have used Linux some but know nothing about mailservers.  I have set up a webserver and ftp server but mailservers seem a lot more complicated.

What I want to be able to do is have this.   Have a server accept mail for [email]username@mydomain.com[/email] and then access it using Thunderbird (with POP) from a second computer.

I am thinking of using Exim.  What other programs would I need to install with it to make this work.

What ports am I going to have to open on my router.

What do I need to do to configure this.

---

### Post by souki on 2006-04-26
I'm not sure to understand,
- do you allready have a mailserver for this domain?
- do you want a pop server on your local network ?
- do you want all your domain handled by this mail server ?

if you want some accounts on your local network, fetchmail + exim
you don't have to port-forward since fetchmail is pulling from external pop server

if you want a mail server for the whole domain, that's much more complicated

---

### Post by Brocco on 2006-04-26
In addition to Exim you need a POP server.  No configuration should be necessary for the POP server; just install it.  It looks like I've been using the "qpopper" package for this on one of my servers.

You'll need to open two ports on your router: one for the mailserver (SMTP, or 25/tcp) and one for POP (pop3, or 110).

Things get more complicated if you want to get your mail securely from Thunderbird (I recommend this).  This entails either routing it through a VPN or encrypting the connection with SSL so that no one can eavesdrop on your password.  POP with SSL is called POPS.

I wrestled with Exim for a long time trying to configure seemingly common use cases such as these and finally switched to Postfix, which is installed by default in Ubuntu.  Postfix is much easier to configure than Exim, IMHO.

Brocco

---

### Post by alamba on 2006-04-26
It gets further complicated if u're looking at spam control and web interface access for your hosted mail accounts. I have a exim+courier-imap+spam assasin+uebimiau setup running for my domain.

A

---

### Post by R.Bucky on 2008-04-29
I am currently using Google Apps as my [email]mark@buckyspalace.net[/email] mailbox. It is free. why not?

---

