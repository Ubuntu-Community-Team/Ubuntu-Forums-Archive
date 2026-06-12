---
title: "Backscatter, Amavisd-new, Spamassassin, Postfix"
date: 2008-04-06
forum: Server Platforms
---

### Post by tester321 on 2008-04-06
Would appreciate some guidance...  Running: Amavisd, Spamassassin, Postfix, ClamAV, Rules Du Jour, etc.

Have an incredible amount of "backscatter" (even if set ALL Virus/Spam/BadHeader handling to "D_DISCARD").

The Spamfilter appliance relays mail to another "actual" mail server internally so I don't believe it "knows" who the valid User addresses are at SMTP time (no LDAP in use).  

The backscatter appears to be happening when an Email from a  spoofed addr comes in (i.e., destined for [email]somefakename@myrealdomain.com[/email]) that makes it through the  SPAMfiltering.  The internal final destination mailserver then rejects the invalid email addr with a 550 and the Spamfilter/postfix tries to deliver the failure back (to what is obviously a fake "from" addr).

How can I get the Spamfilter/Postfix  to just DISCARD the failed Email?

*PS:  All Spam scoring/virus handling etc. is working great otherwise; it is just this ONE problem I can't figure out after reading every Howto known to mankind.  And yes, in a perfect world it would be great to find a rule to catch these dictionary-attack like Emails at SMTP time, but haven't found one yet.  Would be happy to just silently dump the failures.*

Thanks in advance for any help!

---

