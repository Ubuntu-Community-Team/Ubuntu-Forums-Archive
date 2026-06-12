---
title: "Mail server works - but I have further questions"
date: 2009-07-30
forum: Server Platforms
---

### Post by DaveAK on 2009-07-30
I set up an IMAP mail server on my home network last night using fetchmail / postfix / dovecot / amavisd-new / spamassassin / clamav using documentation from the Ubuntu site for 9.04.  It all seems to be working fine, (although I haven't checked ClamAV), but now I want to extend it and I'm looking for suggestions.

First thing - web mail.  Squirrelmail seems to be popular, (and my ISP obviously uses it having looked at some screenshots).  On my local email client I have several individual accounts set up, (not several accounts going into one mailbox, but separate mailboxes).  Is it possible to get a web mail client to have one login account and see multiple accounts/inboxes?  If so can Squirrelmail do this or is there another client that does?

Address books.  I'd like to set up some kind of shared address book that's server based and so could be accessed/edited from different clients, local and remote.  What's the best way to do this?  Does IMAP have the capability, or should I look at doing LDAP, and how would that integrate with what I already have, (server as described above - Outlook and Thunderbird local clients), and with a web mail client?

I set up what I've done so far with a self-signed SSL certificate.  Would this certificate be sufficient to use https with a web mail client?

What else should I be considering to make this an effective personal/home office system?  So far it's been relatively straightforward. I'm not looking for a full blown corporate production system, but I'm enjoying the learning experience and would like to take it a little further.

---

