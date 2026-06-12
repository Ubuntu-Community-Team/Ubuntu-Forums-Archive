---
title: "How can I setup whitelist delivery only with postfix?"
date: 2010-06-21
forum: Server Platforms
---

### Post by 3rods on 2010-06-21
I am using this config: [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.0]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu-10.04").

I'm looking to create a white-list of email addresses that are allowed to send mail to my son's email address. Basically, I'm trying to do this:

if from not in ('dad@home.net','mom@home.net','unclebill@work.org')
then deliver to 'dad@home.net'

Or deliver to /dev/null or something.

This would be only for his account/domain, not server-wide.

The configuration above uses MySQL for forwarding and authentication. I'm not sure if that is a plus or minus for what I'm trying to do.

Any help is appreciated.

---

