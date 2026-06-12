---
title: "Mail Server"
date: 2005-01-16
forum: Server Platforms
---

### Post by icerogue on 2005-01-16
I am just wondering what you would suggest for a mail server. I have a domain name and i want to run an email server but I am not sure which one to go with.
Thanks in advance

---

### Post by albersag on 2005-01-16
This article could help you.

Its a step by step guide to install a serious mail server,, with spamassasing, antivirus,etc...

[http://www.idealog.us/2004/10/helpful_guide_t.html](http://www.idealog.us/2004/10/helpful_guide_t.html)

I hope this help

---

### Post by albersag on 2005-01-16
If you desist on create a mail server ;)

try using [www.cdmon.com](www.cdmon.com) as a dns host. They accept freely forwarding mail to an existing account.

But the other possibility is enjoyable and cheaper :)

---

### Post by JackDog on 2005-01-21
If you want to setup your own....
[http://www.gentoo.org/doc/en/virt-mail-howto.xml](http://www.gentoo.org/doc/en/virt-mail-howto.xml)

---

### Post by anund on 2005-01-25
[QUOTE=icerogue]I am just wondering what you would suggest for a mail server. I have a domain name and i want to run an email server but I am not sure which one to go with.[/QUOTE]

I'm using exim for my mail server. Running on Debian Sarge (waiting and waiting for it to get 'Stable' status...). Imho, exim is a very nice and configurable server. I've set it up as an imap server which coexists perfectly with Squirrelmail on my box.

---

### Post by mendicant on 2005-01-25
I like the configuration of postfix a little better than exim, and postfix is the default mail server for ubuntu (so you might get a little better support for it when you ask).

---

### Post by nocturn on 2005-01-26
My server is running Postfix and Cyrus Imap on Gentoo (will soon switch to either Sarge or Ubuntu).

Both are very cool, I have integrated spam and virus checking *and* got the holy grale of authentication working: kerberos (although it is a shame that Ubuntu packages Evolution without krb5 support), this means only entering a password at login, yet have all connections authenticated.

I really recommend this combination, although the Kerberos thing is optional and quite hard to get working.

---

### Post by crm on 2005-01-26
Hi,

Don't mean to be thick, but why's Cyrus AND Postfix installed?  I thought Postfix was a mta? - where as you could just setup an imap connection to it.. or am I wrong here?

Does Cyrus allow the pop/imap connections, and postfix act as the send-server?

---

### Post by nocturn on 2005-01-26
[QUOTE=crm]Hi,

Don't mean to be thick, but why's Cyrus AND Postfix installed?  I thought Postfix was a mta? - where as you could just setup an imap connection to it.. or am I wrong here?

Does Cyrus allow the pop/imap connections, and postfix act as the send-server?[/QUOTE]

Postfix is an SMTP server AFAIK.  It handles outgoing and incoming mail, but not the actual mail delivery to clients.

Cyrus is a POP3/Imap server, it does not handle sending/receiving mail, but presenting it to clients.

Technically speaking, if I'm correct, Postfix is a Mail Transport Agent, while Cyrus is a Mail Delivery Agent.

---

### Post by Rottweiler on 2005-02-02
Postfix and Dovecot.
 
 Easy as pie.

---

### Post by thewanderer on 2005-02-03
As Rottweiler said: -

MTA - Postfix
IMAP - Dovecot
Webmail - Squirrelmail

apt-get it all - easy.  :grin: 

If i find some spare time i will try and make up a guide to all of the above plus amavis, spam assassin and clamav.

---

### Post by spinnekop on 2005-04-26
"If i find some spare time i will try and make up a guide to all of the above plus amavis, spam assassin and clamav."

Please do so and post it here - I would really appreciate that!

---

