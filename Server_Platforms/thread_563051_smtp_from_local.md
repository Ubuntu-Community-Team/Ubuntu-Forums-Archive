---
title: "smtp from local"
date: 2007-09-29
forum: Server Platforms
---

### Post by acidjuice on 2007-09-29
dear all,

i'm currently running an ubuntu server which hosts quite a big social network.

the portal running this social network needs to send out notification emails when things happen: 'you have received a new private email', ...

now, until today i've been using an external SMTP server, which has kindly been provided to me by a friend. however, volume of email being sent is just too high, so i figured i'd set up an smtp server instead.

what i need:

- an smtp server able to send out email ONLY by localhost: i do not want people to connect to it from the outside, i just need it to be accessible from the python scripts of the portal;

- i do not care about email itself, since the POP email is being managed by another server -> i just need to be able to send out email.

..what would you suggest?

thank you for your time, this is really important to me.

cheers,

aj.

---

### Post by HermanAB on 2007-09-29
Here you go:
[http://www.postfix.org](http://www.postfix.org)

Cheers,

Herman

---

### Post by acidjuice on 2007-09-29
i was hoping on some more justifications than providing a link to a well known smtp server.. not even sure i do need such a full featured smtp server.

still, thanks for your time.

aj.

---

### Post by HermanAB on 2007-09-29
Sorry about the blunt reply, but that is likely the best way - read a few of the howtos on the postfix web site and take it from there.  Getting a MTA up and running is kinda painful.

There are some simpler mailers, for example 'nullmailer', but you are bound to run into problems with the simple mailers being unable to suppress misuse by spammers.

The only other easy alternative I know of is to install a full fledged self contained system, for example [http://www.citadel.org](http://www.citadel.org).  Citadel is without doubt the easiest mail system to set up.  Using their Easy Install script it only takes about 20 minutes, but while this is *much* easier than setting up a simple MTA, it is far more than you apparently want - check it out anyway, you may change your mind.

Cheers,

Herman

---

### Post by acidjuice on 2007-09-30
thank you for your time, herman. i'll definitely look right now into what you suggested.

cheers,

aj.

---

