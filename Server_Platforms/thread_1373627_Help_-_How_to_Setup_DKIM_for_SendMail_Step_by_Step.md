---
title: "Help - How to Setup DKIM for SendMail Step by Step - Ubuntu Server 9"
date: 2010-01-05
forum: Server Platforms
---

### Post by Taurian on 2010-01-05
**Take a look at this:**

[http://www.howtoforge.com/quick-and-easy-setup-for-domainkeys-using-ubuntu-postfix-and-dkim-filter](http://www.howtoforge.com/quick-and-easy-setup-for-domainkeys-using-ubuntu-postfix-and-dkim-filter)

**Well i'm not using postfix, i'm using SendMail. **

I get as fas as adding the DNS Entry, but i'm at a loss as to what to do next for SendMail. Can anyone help me out?

DKIM Milter is installed and should be running. I did find this article:

[http://www.elandsys.com/resources/sendmail/dkim.html](http://www.elandsys.com/resources/sendmail/dkim.html)

**However, i'm not entirely sure if some of the steps are necessary**

So to recap, DKIM is running, I created the keys, updated my DNS records, how do I get sendmail to realize it?

Thanks!

---

### Post by mlissner on 2010-04-23
Would love to hear if you found a solution for this.

---

### Post by gruadp on 2010-12-19
I've just installed dkim at my server and wrote a small howto that also explains how to "add" the dkim-filter to sendmail. Its a quick and dirty howto, but maybe it helps.
[URL="http://www.goldfisch.at/knowwiki/howtos/dkim-filter"]
http://www.goldfisch.at/knowwiki/howtos/dkim-filter[/URL]

best,
p

---

