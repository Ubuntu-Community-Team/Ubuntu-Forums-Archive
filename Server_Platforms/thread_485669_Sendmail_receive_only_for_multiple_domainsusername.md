---
title: "Sendmail receive only for multiple domains/username combinations"
date: 2007-06-27
forum: Server Platforms
---

### Post by pnmcosta on 2007-06-27
Hi,

I'm fairly new to server installation on Ubunto, i'm trying to set the following up:

1 - an SMTP server that will only receive emails, no relay/outbound necessary
2 - is able to receive all emails to N number of domains without having to specify them on sendmail. e.g. receive from inbound.domain.com and inbound.other-domain.com if their MX records are pointing to sendmail's box.
3 - filter emails by their to username, e.g. main_{account}_{ref}@inbound.domain.com would add the message to the mail_{account} mailbox, where {account} is a digit, and if the mailbox does not exist create it.

We basically have N number of domains, their inbound subdomain MX record is pointing to my sendmail box. We really didn't want the trouble of having to setup sendmail every time we add a new domain so if the domain/username combination meets our requirements.

Is it possible to achieve something like this? 

Kind Regards
Pedro

---

### Post by piers on 2007-06-27
Have you looked at setting up Postfix and Dovecot (i'm assuming your users want collect their mail via POP3 or IMAP) instead of sendmail, their are plenty of tuturials out there.

Also consider ooking at ISPConfig, this will set up mail servers and user management for you aswell as being able to set up web/ftp hosting if you wanted it to.

---

### Post by pnmcosta on 2007-06-27
> **piers said:**
> Have you looked at setting up Postfix and Dovecot (i'm assuming your users want collect their mail via POP3 or IMAP) instead of sendmail, their are plenty of tuturials out there.

Also consider ooking at ISPConfig, this will set up mail servers and user management for you aswell as being able to set up web/ftp hosting if you wanted it to.
Hi Piers,

Umm maybe i wasn't clear enough, we won't actually have this available to humanoids! We are an ESP and this will work as the server to store bounces and replies from our campaigns, we just need to analyse the incoming emails, first to check it their origin is correct, and split the emails per account.

We would have a automated system to read these emails either by pop or imap and process them accordingly.

The main 2 points is that we can have this automated on a domain level and email address. Our crawler will handle the reading of the messages.

I've had a look at Postfix and i didn't see much diference to sendmail. Since sendmail was already installed on my machine, i decided to use it, but do you think Postfix will be able to handle what i want better?

Thanks,
P.

---

### Post by piers on 2007-06-27
Personaly I would have tackled this with Postfix and its 'virtual' module [http://www.postfix.org/virtual.8.html]("http://www.postfix.org/virtual.8.html")
I'm sure it wouldn't be too hard to get a script to run on reciept of a new email.

I hope that helps.

---

### Post by pnmcosta on 2007-06-28
Hi Piers,

Thanks for your help, but we dropped this solution alltogether, thanks for your time do..

All the best,
Pedro

---

