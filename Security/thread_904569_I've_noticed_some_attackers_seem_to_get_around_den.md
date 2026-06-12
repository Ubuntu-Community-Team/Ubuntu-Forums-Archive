---
title: "I've noticed some attackers seem to get around deny hosts"
date: 2008-08-29
forum: Security
---

### Post by jerome1232 on 2008-08-29
This is a normal attack
```
Aug 24 17:28:31 tss2 sshd[12521]: Invalid user trash from 62.43.191.28
Aug 24 17:28:33 tss2 sshd[12523]: Invalid user aaron from 62.43.191.28
Aug 24 17:28:36 tss2 sshd[12525]: Invalid user gt05 from 62.43.191.28
Aug 24 17:28:39 tss2 sshd[12527]: Invalid user william from 62.43.191.28
Aug 24 17:28:42 tss2 sshd[12529]: Invalid user stephanie from 62.43.191.28
Aug 24 17:28:44 tss2 sshd[12531]: User root from 62.43.191.28.static.user.ono.co
m not allowed because none of user's groups are listed in AllowGroups
Aug 24 17:28:45 tss2 sshd[12538]: refused connect from 62.43.191.28.static.user.ono.com (::ffff:62.43.191.28)
```

and this is one where they get alot of authentication attempts before denyhosts seemed to actually deny them
```

Aug 24 21:36:28 tss2 sshd[12609]: warning: /etc/hosts.deny, line 51: host name/name mismatch: db4217209.aspadmin.net != hit-nxdomain.opendns.com
Aug 24 21:36:28 tss2 sshd[12609]: Did not receive identification string from 71.6.217.209
Aug 24 21:41:59 tss2 sshd[12610]: warning: /etc/hosts.deny, line 51: host name/name mismatch: db4217209.aspadmin.net != hit-nxdomain.opendns.com
Aug 24 21:41:59 tss2 sshd[12610]: Address 71.6.217.209 maps to db4217209.aspadmin.net, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
Aug 24 21:41:59 tss2 sshd[12610]: Invalid user admin from 71.6.217.209
Aug 24 21:41:59 tss2 sshd[12611]: input_userauth_request: invalid user admin
Aug 24 21:41:59 tss2 sshd[12612]: warning: /etc/hosts.deny, line 51: host name/name mismatch: db4217209.aspadmin.net != hit-nxdomain.opendns.com
Aug 24 21:42:00 tss2 sshd[12612]: Address 71.6.217.209 maps to db4217209.aspadmin.net, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!
:
```
goes on for a very long time and finally denyhosts refused them, has anyone seen this before? Looks like a way to work around deny hosts to me. Unless this is just because revers dns isn't working and so denyhosts freaks out?

---

### Post by CaptSaltyJack on 2008-08-30
Sounds like just a DNS screw-up, I wouldn't blame it on someone attacking (though I wouldn't rule it out).  I'd also recommend adding this line to your /etc/ssh/sshd_config file:

UseDNS no

I've got denyhosts installed, had it running perfectly for months now, no problems.  I do not use hostnames, ever.  Everything is strictly IP-based on my system.  My hosts.deny file just has a bunch of IP addresses in it ("ALL: aaa.bbb.ccc.ddd").

---

### Post by jerome1232 on 2008-08-30
Thanks I will make that change based on the comments above the ALL:PARANOID option in hosts.deny looks like setting it might resolve the issue too.

edit:I'm going to give you your first thanks

---

