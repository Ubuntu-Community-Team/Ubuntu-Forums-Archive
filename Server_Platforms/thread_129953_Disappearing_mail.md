---
title: "Disappearing mail?"
date: 2006-02-15
forum: Server Platforms
---

### Post by catfox on 2006-02-15
Hi All,
I've got a server set up with ldap and exim. The ldap server has a group with some members, and I want to send mail to the group.

When sending mail to the group address, /var/log/messages says this about the message:
```

Feb 15 07:26:08 morecambe spamd[5895]: Can't call method "bind" on an undefined value at /usr/lib/perl5/vendor_perl/5.8.7/Mail/SpamAssassin/Conf/LDAP.pm line 14 2, <GEN60> line 2.
Feb 15 07:26:08 morecambe spamd[5895]: failed to load user scores from LDAP serv er, ignored
Feb 15 07:26:08 morecambe spamd[5895]: processing message <e8d80da90602142326x41 e06e56wa5f8002c38d9b0d5@mail.gmail.com> for everton.fans@min.mydomain.com:0.
Feb 15 07:26:08 morecambe spamd[5895]: clean message (2.2/5.0) for everton.fans@ min.mydomain.com:0 in 0.7 seconds, 1810 bytes.
Feb 15 07:26:08 morecambe spamd[5895]: result: .  2 - HTML_50_60,HTML_MESSAGE,HT ML_SHORT_LENGTH,RCVD_BY_IP,SUB_HELLO scantime=0.7,size=1810,mid=<e8d80da90602142 326x41e06e56wa5f8002c38d9b0d5@mail.gmail.com>,autolearn=no
Feb 15 07:26:08 morecambe mailinglist: OK message posted to everton.fans@min.my domain.com

```
that last line includes the space in the delivery address for some reason?

also, the exim log produces this
```

2006-02-15 07:26:08 1F9H3A-0007vs-2j <= paul@gmail.com H=xproxy.gmail.com [66.249.82.205] P=esmtp S=1755 id=e8d80da90602142326x41e06e56wa5f8002c38d9b0d5@mail.gmail.com
2006-02-15 07:26:09 1F9H3A-0007vs-2j ** everton.fans@min.mydomain.com R=virtual_domain_group T=group_expansion: Child process of group_expansion transport returned 1 from command: /data/config/exim/group-expander
2006-02-15 07:26:09 1F9H3B-0007w4-4L <= <> R=1F9H3A-0007vs-2j U=mail P=local S=2592
2006-02-15 07:26:09 1F9H3A-0007vs-2j Completed
2006-02-15 07:26:10 1F9H3B-0007w4-4L => paul@gmail.com R=dnslookup T=remote_smtp H=gmail-smtp-in.l.google.com [72.14.205.27]
2006-02-15 07:26:10 1F9H3B-0007w4-4L Completed

```

but no mail actually arrives at the addresses specified in the ldap group.
does anyone have any ideas where I might look to help solve this?

---

