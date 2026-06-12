---
title: "Postfix"
date: 2008-04-23
forum: Server Platforms
---

### Post by Hungry Snail on 2008-04-23
Hi Guys,

Accounts on our Postfix/Dovecot email server are getting lots of delivery failure notice emails coming in.

These are coming from external servers which suggests that spammers are spoofing the return address on spam mails.

Is there anyway I can get posfix to reject delivery failure emails from emails that didnt originate from our server?

Cheers

---

### Post by zazuge on 2008-04-24
I'm not sure.
you can restrict the what subnet you're relaying from
mynetworks_style = subnet
mynetworks = 192.168.1.0/24 192.168.0.0/24
or use this
relay_domains =
(never relay mail from strangers)
and I'm not sure about the second answer yet
hope that helps

---

### Post by MJN on 2008-04-25
There's not much you can do about so-called 'backscatter'. Have a read of [this](http://www.postfix.org/BACKSCATTER_README.html) for some ideas.

You will like find it comes in waves, with riding it out being the best solution until they move onto the next domain to spoof.

Mathew

---

