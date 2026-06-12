---
title: "Server Postfix Install"
date: 2012-08-09
forum: Server Platforms
---

### Post by LinuxBill on 2012-08-09
I have installed postfix with dovecot for my mail server. Both dovecot and Postfix seem to be operational when I Telnet to them. 

But when I try to send a mail from the command line I get this error in the mail.log

```
proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf lookup error for "sales@XXXXXXX.co.uk"
```

```
 virtual_alias_maps map lookup problem for sales@XXXXXXX.co.uk -- deferring delivery
```

I looked into this file and its all correct 

```
user = xxxxx
password = xxxxx
dbname = mail
query = SELECT destination FROM forwardings WHERE source='%s'
hosts = 127.0.0.1

```

Not sure where I stand with this? Any help would be great. Can provide any information if needed.

Thanks
William

---

