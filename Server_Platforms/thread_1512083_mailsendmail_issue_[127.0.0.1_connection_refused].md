---
title: "mail/sendmail issue [127.0.0.1 connection refused]"
date: 2010-06-17
forum: Server Platforms
---

### Post by tituspurdin on 2010-06-17
I have sendmail running (quite well) on my ubuntu box.  It works
fine with Thunderbird locally.  It runs fine with a few other MUAs
on (allowed) remote machines.  It has one small problem I have not
been able to clear up: it will not send mail that is initiated by
the 'mail' program locally.  It gives me a "[127.0.0.1 connection
refused] error in the logs.  The /etc/hosts file is fine (as far
as I know). The sendmail.cf file has been rebuilt from sendmeil.mc.
'hostname' and 'dnsdomainname' return proper values.  Okay, I'm
stumped and looking for another set of eyes on the problem.

Titus sends

---

### Post by neilevan814 on 2010-06-27
I have the same problem in lucid 10.04.  I have once purged and reinstalled sendmail with a little luck, but today, it's not working again.

---

### Post by clrg on 2010-06-27
Does sendmail bind itself to a particular interface or IP address? I know some services can do that, for example SSH. If you configure them to do so, they will refuse connections from any interface but the one you specified. 

Since local connections are made through lo, not eth0, that might be the problem. Applications like Thunderbird probably look up your server's IP address through DNS, and then communicate with it trough its outside interface (although the packets won't leave your box) instead of 127.0.0.1.

---

