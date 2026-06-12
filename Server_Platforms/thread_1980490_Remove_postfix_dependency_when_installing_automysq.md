---
title: "Remove postfix dependency when installing automysqlbackup"
date: 2012-05-15
forum: Server Platforms
---

### Post by baraboom on 2012-05-15
Hi,

I'm trying to ```
apt-get install automysqlbackup
``` on an ubuntu 10.10 server that is also running zimbra. However, it wants to install postfix, which I'd like to avoid.

I've updated the alternatives to point at the zimbra sendmail binary ```
update-alternatives --install /usr/sbin/sendmail mta-sendmail \
/opt/zimbra/postfix/sbin/sendmail 25
``` but apt-get still wants to install postfix.

I know I can install nullmailer or similar and the postfix requirement will go away - which I'd also like to avoid. 

How I can manually tell apt-get that there is an MTA already available on the system?

Thanks in advance,
b

---

