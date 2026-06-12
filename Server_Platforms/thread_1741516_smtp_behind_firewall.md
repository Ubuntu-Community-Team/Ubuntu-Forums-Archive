---
title: "smtp behind firewall"
date: 2011-04-28
forum: Server Platforms
---

### Post by gerapcik on 2011-04-28
Hi all,

i have installed Ubuntu Server 10.04 behind firewall. I have installed vTiger crm on it and i would like to use the server also as a smtp server to send some mail from crm.

how can i configure postfix in the way that mail will not be considered as a spam?

thanks in advance

---

### Post by elico on 2011-04-28
you can use a relayhost of your isp or your domain email service server.
use the following commands:
(it's like configuring the server to be an smtp client such as outlook or thunderbird
so the server user and password should be the one from the mail client software settings
no space between the ":" and the password)

> postconf -e relayhost=[mail.server.xroot_domain]:25
postconf -e smtp_sasl_auth_enable=yes
postconf -e smtp_sasl_password_maps=hash:/etc/postfix/sasl_passwd
echo "[mail.server.xroot_domain]:25   username: password">>/etc/postfix/sasl_passwd
postmap /etc/postfix/sasl_passwd
postfix check
postfix reload


---

