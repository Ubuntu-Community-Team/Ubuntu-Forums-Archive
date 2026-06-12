---
title: "exim4 clamav and spamassassin"
date: 2008-01-25
forum: Server Platforms
---

### Post by jasonfissure on 2008-01-25
Hello.  I've been running an smtp mail gateway for a while now on Debian using Exim4, Clamav, and Spamassassin.  I built a new box using Gutsy and I can't, for the life of me, get Exim4 to pass messages to clamav or spamassassin.  I have exim4-daemon-heavy installed along with clamav-daemon and spamassassin.  I have av_scanner = clamd;/var/run/clamav/clamd.clt and spamd_address set to 127.0.0.1 783 and I have CHECK_DATA_LOCAL_ACL_FILE set to a file that contains these lines:

 deny message = This message contains a virus: ($malware_name) please scan your system.
     demime = *
     malware = */defer_ok

warn message = X-Filter-Spam-Score: $spam_score ($spam_bar)
     condition = ${if <{$message_size}{80k}{1}{0}}
     spam = Debian-exim:true

warn message = X-Filter-Spam-Report: $spam_report
     condition = ${if <{$message_size}{80k}{1}{0}}
     spam = Debian-exim:true

deny message = Spam score too high ($spam_score)
     !acl = acl_whitelist_local_deny
     condition = ${if <{$message_size}{80k}{1}{0}}
     spam = Debian-exim:true/defer_ok
     condition = ${if >{$spam_score_int}{50}{1}{0}}

This is the same setup I've been using on  Debian box.  Does anyone know why exim4 would not pass messages to clamav or spamassassin in this case?  I've run exim4 -bV and it shows support for content scanning.  I can see that spamd and clamd are running, but, no log entries are generated showing that the messages are being scanned and no headers are being added.  Any advice would be appreciated.  Thanks

Jason

---

