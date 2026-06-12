---
title: "Ubuntu Server - sendmail &quot;stat=deferred connection refused by mailq2.eurobell.net&quot;"
date: 2011-01-27
forum: Server Platforms
---

### Post by Jabbs on 2011-01-27
**_Using Ubuntu Server 10.04 - sendmail _**

Error: > "stat=deferred connection refused by mailq2.eurobell.net"

Hi there, here's hoping an expert here can help :-)

I have set up **Ubuntu server** which hosts our website (or will do very soon) but I am seeing the above error appearing in **mail.log** for email addresses whose destination is our company email domain (applebywestward.co.uk). 

The web server is in our DMZ and therefore any traffic goes out (should) to Eurobell first and one presumes that Eurobell then send on emails to the relevant domains (such as hotmail.com and applebywestward.co.uk)

This problem is happening on a php website and using contact forms on the site.

Other email addresses (such as [email]someone@hotmail.com[/email]) go through fine without error.

When I try and force the queue to go with > 'sendmail -q -v', I see:

> Connecting to mail.applebywestward.co.uk via esmtp....

which 'seems' to fail (nothing happens, no log recorded) and then I see:

> Connection to mailq1.eurobell.net via esmtp....

and then:

> Deferred: Connection refused by mailq1.eurobell.net

Here's hoping someone can put their finger on this easily :-)

Many thanks

Jonathan

---

