---
title: "postfix help...."
date: 2008-01-06
forum: Server Platforms
---

### Post by hockey97 on 2008-01-06
I have postfix up and running. I have mysql communicating with postfix and a couple databses for domain,mailbox/users and alias which I don't use.

it worked somewhat I can get e-mails but can't send them to wellknown e-mail providers.  I also  config the user to have the maildir to be in /home/user/domian/user      but postfix still send's the main in the default area at /var/mail/user  .

 I  mainly want to know how I can config postfix so that I can make the user and user's e-mail address. and also to using php or mysql to be able to automaticly add new users mailboxes ect.

do I need  COURIER IMAP to do this?

I have so far been working on this for a week. and havent gotten anywhere.

the latest thing I am look at is :[http://www.postfixvirtual.net/postfixconf.html#mysql](http://www.postfixvirtual.net/postfixconf.html#mysql)

that's mainly it. I specified in main.cf for postfix the base mail and virtuial mail which in the database holds the maildir for the user yet postfix still send's e-mail to the default area the /var/mail/user.

I really need some kind of advice. I am really struggleing here.

---

### Post by hockey97 on 2008-01-07
How can I in postfic config my user's  and their mail box directory??

and how can I find out their e-mail address?

---

