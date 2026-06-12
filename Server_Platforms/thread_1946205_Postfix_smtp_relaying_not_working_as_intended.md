---
title: "Postfix smtp relaying not working as intended"
date: 2012-03-24
forum: Server Platforms
---

### Post by Jungleboss on 2012-03-24
I am setting up a mail server and I've a question about smtp relay.

I want to act as my own relay host and I've configured Postfix's main.cf like this:

relayhost =

But when I send a mail to a gmail address gmail is used as relay it seems:

....relay=gmail-smtp-in.l.google.com....

What am I doing wrong?

---

### Post by sanderj on 2012-03-24
> **Jungleboss said:**
> I am setting up a mail server and I've a question about smtp relay.

I want to act as my own relay host and I've configured Postfix's main.cf like this:

relayhost =

But when I send a mail to a gmail address gmail is used as relay it seems:

....relay=gmail-smtp-in.l.google.com....

What am I doing wrong?

You also have to point your mail client SMTP's server to your system running postfix.

---

### Post by Jungleboss on 2012-03-24
Perhaps I use the wrong terminology. I do want to send outgoing mail myself. But I don't want others to be able to send though my server.

When I tested and sent a mail (from my server) with telnet to a gmail address shouldn't "relay=" in postfix log be "127.0.0.1"? It is gmail-smtp-in.l.google.com now as mentioned.

Or am I confused about something :)

---

### Post by sanderj on 2012-03-24
> **Jungleboss said:**
> Perhaps I use the wrong terminology. I do want to send outgoing mail myself. But I don't want others to be able to send though my server.

When I tested and sent a mail (from my server) with telnet to a gmail address shouldn't "relay=" in postfix log be "127.0.0.1"? It is gmail-smtp-in.l.google.com now as mentioned.

Or am I confused about something :)

So the setup & route should be:

mailcient -> localhost -> relayhost (of ISP) -> other mailservers

... have you checked all parts?

---

### Post by collisionystm on 2012-03-25
deleted this reply

---

### Post by collisionystm on 2012-03-25
Here is the way I always do it....

First purge postfix

sudo apt-get purge postfix

re-install

sudo apt-get install postfix

durring setup you will presented with the blue and grey setup screen. Choose to setup with an Internet Host ( I think...not at work =) )

Name your domain. YourDomain.com

try to test send a message

echo "Test message" | mail -s "This is a test email." [email]admin@domain.com[/email]

---

### Post by Jungleboss on 2012-03-30
I think I misinterpreted the log. Everything works as I'd like now :) Thanks for all your support.

---

