---
title: "any package for ldap key auth?"
date: 2023-12-18
forum: Ubuntu, Linux and OS Chat
---

### Post by solarflow99 on 2023-12-18
I just wondered why there wasn't any package for looking up a users key in ldap for sshd?  Currently the only way I see is to pip install ssh-ldap-pubkey andthen edit sshd_config like this:

AuthorizedKeysCommand /usr/local/bin/ssh-ldap-pubkey-wrapper

I don't see a package for ssh-ldap-pubkey, surely there has to be a better way than installing thru pip?

---

### Post by TheFu on 2023-12-18
Not quite what you want - doesn't use LDAP, but does delegate ssh-cert validation to an ACME server.
Google found this answer: [https://smallstep.com/blog/use-ssh-certificates/](https://smallstep.com/blog/use-ssh-certificates/)
Of course, that guy made a tool for general x.509 cert management (and use for ssh-certs): [https://github.com/smallstep/certificates](https://github.com/smallstep/certificates)  I've not used it.  Looks interesting. He has a dockerfile, since something like this is an ideal use for a Linux Container.  Hardly any data at all.

I'm not a Docker fan, but if I can figure out what he really is doing, putting this into an LXC container would better align with my infrastructure.

---

### Post by solarflow99 on 2023-12-19
These seem to deal with cert management, I was just looking for a native way to enable sshd to use key authentication when the key is stored in ldap.

---

