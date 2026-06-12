---
title: "Sarg Permissions"
date: 2007-12-22
forum: Server Platforms
---

### Post by expatCM on 2007-12-22
Running Sarg I get the error which others have seen along the lines of -

Now generating Sarg report from Squid log file /var/log/squid/access.log and all rotated versions ..
sarg -l /var/log/squid/access.log.1 
SARG: (html11) Cannot open file: /var/www/squid-reports/2007Dec14-2007Dec14/users
.. Sarg failed! See the output above for details.

Fine ... it is a permissions error.  So I went to /var/www/squid-reports and changed all the permissions to user and user group from root / root.  Fine again,  ls –l confirmed this.

But it seems this must be the wrong place to change the permissions since as soon as I tried to generate a report the same thing happened and I looked at the files again and the permissions had changed back to root / root.

So how do I set Sarg so that it can generate a report from the Squid logs?

Or is a better question to ask how can I set the user rather than root to run Sarg?

---

