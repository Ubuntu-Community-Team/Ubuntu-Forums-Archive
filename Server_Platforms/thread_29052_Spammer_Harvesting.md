---
title: "Spammer Harvesting?"
date: 2005-04-22
forum: Server Platforms
---

### Post by nautilus on 2005-04-22
I was curious if such a thing exists, and what software I could easily set this up with?

Basically, I have several servers, and on one of which I would run a daemon which listens on port 25 (smtp).

In various places, I'll poison spam lists with some e-mail addresses which are on domains which, consequently, point all MXs to this particular server.

This server would then accept the connection and act appropriately, going through all the motions of a successful spammery, except it will add the ip to a list (in a database) of a 'spammer' ip.

This way, my other server (my REAL mailserver) will reference this list, comparing incoming connections to the database list of 'spammers' and reject them accordingly, as would the spam-catching server, to save bandwidth.

What would one call this?  Is there a name for such a method of anti-spam?  Does software exist for it?  If not, I can write it, but I'd rather not re-invent the wheel.

---

### Post by nautilus on 2005-04-22
ooooookay, well, seems i help everybody, but still no love for naughtylus.. :(

no problem, i have i figured anyhow.  it's even easier; i have a fake user which i pseudo-publish in a hidden div on our website's contact-us page, which uses a couple methods to break the spam;

[http://www.hardline.org/kb/SpamHoneypot](http://www.hardline.org/kb/SpamHoneypot) <- best method, hard to find in the obfued exim4 splitfile config system...

[http://dspam.nuclearelephant.com/dspam-users/6359.html](http://dspam.nuclearelephant.com/dspam-users/6359.html) <- dspam training method, i dig this one :)

---

