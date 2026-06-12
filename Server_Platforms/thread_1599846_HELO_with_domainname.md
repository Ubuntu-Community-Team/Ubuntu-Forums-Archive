---
title: "HELO with domainname"
date: 2010-10-18
forum: Server Platforms
---

### Post by iaw4 on 2010-10-18
Dear ubuntu experts---I want to send an email from my ubuntu server 10.04 install.  vanilla.  

in /etc/postfix/main.cf, I have put in myhostname = [www.econ.brown.edu](www.econ.brown.edu).

in /etc/mailname, I have put in the same.

# dnsdomainname returns the domain, econ.brown.edu, as it should.

# domainname returns (none).

unfortunately, some mailers at other hosts are rejecting my emails.  They are telling my mailer

Diagnostic-Code: SMTP; 504 <www>: Helo command rejected: need fully-qualified hostname

how do I get the domain name into the HELO command?

help appreciated.

/iaw

---

### Post by James78 on 2010-10-18
HELO there. ;)

Did you add your domainname to myorigin and mydestination? That would usually be a problem when sending mail. So either you should add your domainname to those, or use VirtualDomains*

* Don't add your domainname to myorigin and mydestination if you're using VirtualDomains, as that would specify stuff twice, and give you a trivial rewrite error.

P.S. If you're using a dynamic IP (it doesn't look like you are though), you shouldn't send email from it, because it's almost always likely to be rejected by major email providers (Hotmail, Yahoo...). Also, dynamic IP's are commonly on email blacklists (like spamhaus), even if they've never sent spam before, because they shouldn't be sending mail in the first place. This can be solved by using a static IP. Just a little FYI in case. :)

---

