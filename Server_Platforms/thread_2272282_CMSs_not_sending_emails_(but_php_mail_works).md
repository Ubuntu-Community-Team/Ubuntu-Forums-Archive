---
title: "CMSs not sending emails (but php mail works)"
date: 2015-04-05
forum: Server Platforms
---

### Post by sylvaticus on 2015-04-05
Hello I have a Ubuntu 14.04 VPS with a few sites.
If I run ```
php -r "mail('mytest@emailaddress.org, 'test', 'test');"
``` this goes delivered, but I have a couple of CMS (Drupal and dokuwiki) that doesn't send any emails, including basic password reminder/registration.
I have checked and I am not blacklisted.
Where should I look to start debugging ?

Edit: it seems the problem is that I have the incoming emails using a third party while postfix try to deliver the email locally (maybe looking at the alias file?).
How can I force postfix to NOT try to deliver the email locally ?

---

### Post by sylvaticus on 2015-04-05
The solution is to remove $mydomain (or "myownservername.xxx" if set explicitly) from mydestination variable in /etc/postfix/main.cf.

See also: [http://serverfault.com/questions/249561/configure-postfix-to-use-external-mx-servers-for-delivery-of-local-mail-if-user?newreg=418587ca2fe940d0b139d4194bea7fd7](http://serverfault.com/questions/249561/configure-postfix-to-use-external-mx-servers-for-delivery-of-local-mail-if-user?newreg=418587ca2fe940d0b139d4194bea7fd7)

---

