---
title: "Openssh restrict portforwarding"
date: 2006-10-24
forum: Server Platforms
---

### Post by tall-male on 2006-10-24
To restrict port forwarding on
[http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config]("http://www.openbsd.org/cgi-bin/man.cgi?query=sshd_config")
[I] a nice option is mentioned to limit the ports allowed to be forwarded.

**PermitOpen**
Specifies the destinations to which TCP port forwarding is per-
mitted.  The forwarding specification must be one of the follow-
ing forms:

PermitOpen host: port
PermitOpen IPv4_addr: port
PermitOpen [IPv6_addr]: port

Multiple forwards may be specified by separating them with
whitespace.  An argument of ``any'' can be used to remove all re-
strictions and permit any forwarding requests.  By default all
[/I]

Sadly, the manual page (Dapper) doesn't mention this option, it doesn't work either. It would be nice however being able to restrict portforwarding without completely disabling it.

Currently I use *permitopen="localhost:5901"* in the authorized_keys file. The file is immutable (chattr +i authorized_keys) so users cannot change the file.:twisted:  Nevertheless, I like a global option.
Did I miss something of isn't it possible? Anyone knows about Edgy?

---

