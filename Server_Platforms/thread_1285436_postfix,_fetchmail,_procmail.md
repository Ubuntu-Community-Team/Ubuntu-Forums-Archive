---
title: "postfix, fetchmail, procmail"
date: 2009-10-07
forum: Server Platforms
---

### Post by Luise on 2009-10-07
Hi List,

With the systems I used before installing xubuntu 0.04 I let my MUA (pine) do the filtering into the various folders - well, it did do it, after a fashion but not all that competently. On those systems there was only fetchmail and postfix.

So now  I have also installed postfix and fetchmail, and so far they are delivering all the mail to the INBOX, i. e. to /var/mail/user, and leaving it there:(. I am trying to use procmail as a filter instead of configuring the MUA, now alpine, to filter it.

I have found information on procmail, on postfix, on fetchmail - but I cannot find anything on how to use the three together. In the debian config of postfix there is no "instruction" for postfix to do anything. Would there have to be such instruction or can I configure the .fetchmailrc to "hand the mail on" to procmail?

In the ,ailsin the net there is also, off and on, mention of a file .forward in the home directory - but all I can find on that file in the net is that it forwards to a different mail address.

Luise

---

