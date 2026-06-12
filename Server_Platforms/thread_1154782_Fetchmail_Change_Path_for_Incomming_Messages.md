---
title: "Fetchmail: Change Path for Incomming Messages?"
date: 2009-05-10
forum: Server Platforms
---

### Post by lightnb on 2009-05-10
Fetchmail is sucking my mail down from the Gmail server, and placing it in an MBOX file in ```
/var/mail/[UserName]
```

I have dovecot setup as an IMAP server on our local network, serving mail for each user from ```
/home/[UserName]/Mail
``` ...Where "Mail" is a folder holding messages in the maildir format.

I've been pulling my hair out the last several hours trying to find a way to configure Fetchmail to put the mail in the user's "/home/[UserName]/Mail" folder instead of "/var/mail/[UserName]", but can't seem to find any clear documentation on how this is done.

How can I change Fetchmail's path (and format) for Incoming Messages?

---

### Post by lightnb on 2009-05-12
A few days later, the only clue I've been able to find is the mysterious "procmail".

I've installed procmail via apt-get and I *think* I've set fetchmail to route messages through it.... but what next?

I'm supposed to create a "recipe" and put it somewhere, but the syntax is cryptic and the documentation is lacking...

Here's /etc/fetchmailrc:

```

set daemon 60
set syslog
set postmaster "[username]"

poll pop.gmail.com with proto POP3
user "myemail@gmail.com" there with password "[secret]" is [username] here
options keep ssl sslcertck sslcertpath /etc/ssl/certs
mda "/usr/bin/procmail -d %T"

```

1. Where do I put the "recipe" and
2. How do I make a "recipe" that says "put everything in /home/[username]/mail in maildir format"?

Thanks,

Nick

---

### Post by a9k3d on 2009-05-12
Fetchmail normally fetches mail with with POP and resends to the localhost SMTP port with the "here" username. So if you have say postfix setup for local delivery to your dovecot mailboxes, everything works fine. Fetchmail doesn't need to know about the mailboxes/maildir format. Let postfix handle that.

You'd delete the "mda" clause from your fetchmailrc to let postfix handle the delivery to mailboxes.

I have several servers setup that way for companies. They fetch their "external" email with fetchmail into dovecot mailboxes. They can send to [email]name@company.fake[/email] or [email]name@company.com[/email] - if they use fake, their email says completely in house. That way their company email continues to work when their DSL connection goes down. All thanks to the power of postfix+fetchmail+dovecot.

---

### Post by lightnb on 2009-05-12
Thanks, a9k3d!

I removed procmail and set-up postfix. Messages now magically show up in my IMAP client as soon as fetchmail pulls them down.

For anyone else with this problem, I set-up postfix using the guide here:
[https://help.ubuntu.com/8.10/serverguide/C/postfix.html](https://help.ubuntu.com/8.10/serverguide/C/postfix.html)

The only difference from the guide is, I choose "no" to procmail for local delivery.

Thanks again,

Nick

---

