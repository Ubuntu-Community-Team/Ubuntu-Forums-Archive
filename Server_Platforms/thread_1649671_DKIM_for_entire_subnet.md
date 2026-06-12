---
title: "DKIM for entire subnet"
date: 2010-12-20
forum: Server Platforms
---

### Post by maximCH on 2010-12-20
Hi,

I want to setup a mailserver for my home subnet and also have it sign all mails that it receives from the subnet using DKIM.

Internally I use 10.0.0.0/8 for IPv4 but also have a IPv6 /48 net. For illustration purposes I will use 2001:db8:c0d3::/48.

Hence in /etc/mail/dkim-InternalHosts.txt I have the following entries:

```
# cat dkim-InternalHosts.txt 
127.0.0.1/8
10.0.0.0/8
::ffff:10.0.0.0/104
::1
[2001:db8:c0de::]/48

```

It seems that dkim-filter is trying to resolve the hostname though and really expects an exact match in the dkim-InternalHosts.txt file. So regardless where I send mail from dkim-filter tries to verify instead of signing the e-mail.

Is there a way to achieve what I want to do?

regards,

Maxim

---

