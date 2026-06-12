---
title: "Postfix and virtual domains"
date: 2011-05-30
forum: Server Platforms
---

### Post by zerobravo83 on 2011-05-30
Hi all,

I have a problem with postfix configuration with two domains on one machine;

This was postfix **main.conf** looks like:

```
smtpd_delay_reject = yes
disable_vrfy_command = yes
mydestination = localhost.localdomain, localhost
virtual_alias_domains = domena1.com, domena2.hr
virtual_alias_maps = hash:/etc/postfix/virtual
mynetworks = 127.0.0.1/32 ip_stroja/32
mailbox_size_limit = 70000
recipient_delimiter = +
inet_protocols = all
alias_database = hash:/etc/aliases
```

**"/etc/postfix/virtual"**

```
pero@domain1.com pero_temp
marko@domain1.com marko_temp
jadranka@domain1.com jadranka_temp

pero@domain2.com pero_temp
marko@domain2.com marko_temp
#I do not want to have mail jadranka@domain2.com
```

**"/etc/aliases"**

```
pero_temp: pero_accaunt_on_machine,pero@gmail.com
marko_temp: marko_accaunt_on_machine,marko@gmail.com
jadranka_temp: jadranka_accaunt_on_machine,jadranka@gmail.com

```

Now I want to achieve that certain users have a certain Accaunt have mail on both domains. Also, I would achieve that mail sent to say [email]pero@domain1.com[/email] remain on the server so I could read it through Outlook, and to me a copy of Share on gmail.

I tried to modify /etc/mailname in [email]name_of_machine@domain1.com[/email], but then my mail gets stuck in the que says:

"pero_temp@name_of_machine@domain1.com (expanded from [email]pero@domain1.com[/email]>): User unknown in virtual alias table

Can someone tell me where the mistake and send the right path

In /etc/mailname me now enrolled only domain1.com, the machine is Ubuntu 9.10 karmic.


Advance greatly appreciated.

---

