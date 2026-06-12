---
title: "integration of sympa with postfixadmin"
date: 2011-11-20
forum: Server Platforms
---

### Post by husky69 on 2011-11-20
Hi forum,
I setup a mailserver on my local machine to serve me some things and found a very nice howto (located [here]("http://wiki.nefarius.at/linux/der_perfekte_mail-server"), in german) and so far it utilizes postfix, postfixadmin, dovecot and roundcube. Basic system is an up-to-date Lucid server installation.
Now I need to integrate some mailinglists and I decided to use sympa ([homepage]("http://www.sympa.org/")).
OK - installation of the sympa package from natty went smoothly and the webinterface works nicely.
Unfortunately when sending a mail to an existing list from my mail client I get an error:

```
<list@example.com>: host localmail.example.com[xxx.xxx.xxx.xxx]
     said: 550 5.1.1 <list@example.com>: Recipient address     
rejected: User unknown in virtual mailbox table (in reply to RCPT TO     
command)
```

Looks like postfixadmin has taken complete control over handling mail and doesn't know nothing about the existence of sympa.

Any ideas anyone? So far I couldn't find some suitable information on the net :(

---

### Post by husky69 on 2011-11-20
OK, some more infos I found in the meantime:

Sympa puts its aliases for mailinglists into /etc/mail/sympa.aliases

Because of this I made that file an alias source by adding it to alias_maps in /etc/postfix/main.cf:
```
alias_maps = hash:/etc/aliases,hash:/etc/mail/sympa.aliases
```and similarly to virtual_alias_maps

But - this does not help :( The file holds info about LOCAL aliases and does not allow to modify them to be non-local. And as they don't tell postfixadmin to which domain they apply PFa keeps ignoring them.

As far as I can tell PFa does not allow to define aliases that hand mails over to a script.


Any hints anyone?

---

