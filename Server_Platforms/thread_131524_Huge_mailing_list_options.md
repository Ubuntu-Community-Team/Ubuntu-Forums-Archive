---
title: "Huge mailing list options"
date: 2006-02-16
forum: Server Platforms
---

### Post by jfdill_2 on 2006-02-16
I have shall we say "inherited" a mail server with a ~45,000 subscriber mailing list currently on mailman.  This is an announce-only newslettery type mailing list.  The server also gets whacked with ridiculous amounts of spam, which I have managed to cut down somewhat.  The hardware is a few years old PowerEdge server with P4 2.4 GHz (single processor) and 1 GB RAM.  I have tweaked postfix to the max and played with mailman settings, mailman versions, Python versions and so on.  Performance is getting down to unacceptable levels.  SO I am looking at a few options:

1. see if I can add a second processor and more RAM (will probably have to replace the first processor as it is a straight P4 and not a Xeon, if the mobo will even support it)

2. think about migrating to a different list manager eg. dada mail

3. convince them to buy a new server

Is it really worth it to look at #1 and #2 or am I trying to squeeze lemon juice out of a penny at this point?

#3 is really my preference, I think there is a lot that I can do in terms of designing a better arrangement eg. have the new box handle SMTP and the mailing list, and use the old box for IMAP and POP, or something like that.

Overall, I'm looking for design ideas and device, what have other people already done and so on.

---

### Post by Glut on 2006-02-16
In my experience migrating between applications is often more hassle than it's worth. The most cost-effective upgrade would probably be to stick a faster p4 cpu in - but this very much depends on what the motherboard can handle. If the FSB is only 533mhz you may have an issue getting a decent processor. 

I've got a similar situation where we've moved from slower (2ish ghz) Xeons to newer dual core Opterons. Well worth the move - although our mailing lists are only internal, so about 10% of yours.

---

### Post by jfdill_2 on 2006-02-16
[QUOTE=Glut]In my experience migrating between applications is often more hassle than it's worth. The most cost-effective upgrade would probably be to stick a faster p4 cpu in - but this very much depends on what the motherboard can handle. If the FSB is only 533mhz you may have an issue getting a decent processor. 

I've got a similar situation where we've moved from slower (2ish ghz) Xeons to newer dual core Opterons. Well worth the move - although our mailing lists are only internal, so about 10% of yours.[/QUOTE]
I've determined that it's a Dell PowerEdge 600SC that was purchased in 2003, so it can definitely only handle the single P4 processor.  It has only 533mhz FSB, so it may be hard to find a suitable upgrade processor, unless I could swap one from another box.

Most of the mailing list options seem to be based on interpreted languages whether Python, Perl, or PHP, so switching might not make much difference.  Recently, I've had to turn on VERP due to the stupid AOL "client TOS notifications" otherwise I have no way to tell which idiot subscribed to the mailing list, confirmed his subscription, and is now complaining to AOL about being "spammed" by us so I can take them off the mailing list before AOL blacklists us again (I'm using VERP to put the recipient's e-mail address into the message).  Otherwise, the AOL messages have no information at all about who the message was sent to.  At least the AOL complaints have dropped off to only a few from each newsletter vs. 100-200 at the beginning.  If I had my druthers, I'd just stop sending newsletters to anyone with an AOL address and put up a notice to that effect, but it's not my decision.  Although that may change once AOL starts charging for bulk e-mail.

---

