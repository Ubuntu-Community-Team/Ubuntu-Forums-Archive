---
title: "Getting mail server to receive from ISPs mailhost"
date: 2009-10-14
forum: Server Platforms
---

### Post by Musicalgibbon on 2009-10-14
Hi all,

I'm using a combination of Postfix, Dovecot and Squirrelmail to run a mailserver locally. At the moment everything is working fine (can send mails outside, can send mail to others internally, can log into squirrelmail). 
The only issue I now have is getting Postfix to fetch emails from the ISP mailhost where they're currently stored. I looked up how to do this and found a guide that instructed me to add:
```

relayhost = mailhost.example.co.uk
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
and
smtpd_sasl_authenticated_header = yes
```to my /etc/postfix/main.cf file

it also instructed me to create a file called:
[I]
/etc/postfix/sasl_passwd[/I]

which has:
```
mailhost.example.co.uk user.name:password
```within it.
So far it has fetched no emails, and has produced nothing in any logs.

Any ideas?
thanks

-UPDATE

Okay, so I've got Getmail, I've configured it to retrieve emails from my ISP and set it up to distribute them through Dovecot's deliver. The problem now is that deliver is placing them in the wrong place entirely, and not seperating them by user. It's putting them is:

/home/$User/Maildir/new - where $User is the person who runs getmail.

my getmail config is:
```

[retriever]
type = SimplePOP3Retriever
server = mailhost.example.co.uk
username = user.name
password = pass.word

[destination]
type = MDA_external
path = /usr/lib/dovecot/deliver

```

---

### Post by yknivag on 2009-10-15
Most ISPs don't allow this.  However you can fetch your email into dovecot from any POP/IMAP account very easily using fetchmail.

```
sudo apt-get install fetchmail
``` will install it and then there are some really helpful howto guides around.

Essentially you create a file called /etc/fetchmailrc which contains all the configuration (they're written in a very "chatty" format which is really easy to understand).

The finished solution is then fetchmail-dovecot-squirrelmail with postfix for sending only.

---

### Post by Musicalgibbon on 2009-10-16
Thanks very much, that's precisely what I needed. For some reason I'd kind of assumed that function was carried in Postfix. :P

I did a bit a research and went with Getmail in the end, but they both look to be much of a muchness.

---

