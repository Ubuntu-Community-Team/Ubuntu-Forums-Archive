---
title: "Missing X-Spam header"
date: 2008-12-30
forum: Server Platforms
---

### Post by otx on 2008-12-30
I have a server(8.10) with virtual mail accounts and spamassassin, clamav enabled. The problem is that i don't have the X-Spam header in the mails. The spam filter is working, if i send a test message with the Gtube string the mail is rejected (or bounced per the setting in the \etc\amavis\conf.d\21-ubuntu_defaults), but i want to  deliver the mail normaly and filter later based on the X-Spam status. 

In the \etc\spamassassin\local.cf i have enabled the rewrite rule (rewrite_header Subject *****SPAM***** ) but this doesn't help. 

Here is the content of the \etc\spamassassin\local.cf

```
#dcc
use_dcc 1
dcc_path /usr/bin/dccproc

#pyzor
use_pyzor 1
pyzor_path /usr/bin/pyzor

#razor
use_razor2 1
razor_config /etc/razor/razor-agent.conf

#bayes
use_bayes 1
use_bayes_rules 1
bayes_auto_learn 1

#Add *****SPAM***** to the Subject header of spam e-mails
#
rewrite_header Subject *****SPAM*****
```

And this is the content of the \etc\amavis\conf.d\21-ubuntu_defaults

```
use strict;

#
# These are Ubuntu specific defaults for amavisd-new configuration
#
# DOMAIN KEYS IDENTIFIED MAIL (DKIM)
$enable_dkim_verification = 1;
# Don't be verbose about sending mail:
@whitelist_sender_acl = qw( .$mydomain );
$final_virus_destiny      = D_DISCARD; # (defaults to D_BOUNCE)
$final_banned_destiny     = D_BOUNCE;  # (defaults to D_BOUNCE)
$final_spam_destiny       = D_REJECT;  # (defaults to D_REJECT)
$final_bad_header_destiny = D_PASS;  # (defaults to D_PASS), D_BOUNCE suggested

$warnbannedsender = 1;
$warnbadhsender = 1;
$virus_admin = undef;
$spam_admin = undef;

#------------ Do not modify anything below this line -------------
1;  # insure a defined return
```

If a spam is blocked i can see this in the mail.log:

```
...amavis[18069]: (18069-01) Blocked SPAM,...
```

but if i let to pass, the mail doesn't have any X-Spam header, even if the system know it is a spam (in this case i have passed SPAM in the mail.log)

Any ideas?

---

### Post by Ubunt2u on 2009-03-04
I'm having the same issue. Have you found a solution yet?

---

### Post by gecka on 2009-04-09
Same for me ....

---

### Post by gecka on 2009-04-10
@local_domains_acl = ( "." );

in /etc/amavis/conf.d/50-user solved it

---

### Post by MauriceColon on 2009-04-23
I had the same setup and the same problem and that has cured it first time.  Thanks for sharing, much appreciated.  :)
 
Cheers,
 
Morgan

---

### Post by venol on 2011-04-24
I'm having the  same issue. Have you found a solution yet?

---

### Post by venol on 2011-04-24
I'm find solution, amavis insert X-Spam header on email if recipient listed on @local_domain_maps. maybe this s useful for someone.:o

---

