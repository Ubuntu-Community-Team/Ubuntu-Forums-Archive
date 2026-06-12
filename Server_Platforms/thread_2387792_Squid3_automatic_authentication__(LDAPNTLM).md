---
title: "Squid3 automatic authentication  (LDAP/NTLM)"
date: 2018-03-23
forum: Server Platforms
---

### Post by avidpontoon on 2018-03-23
So I have setup a squid proxy on a Ubuntu server and now want to setup user targeting with my domain.
I would like to be able to set acl's for security groups within AD, is this possible and how can I do this?

The users also need to authenticate with the proxy as it is wide open at the moment, I have set the proxy with group policy. I want the proxy to be linked to AD so that users login and get specific acl's. All the tutorials I've seen are pop-up messages asking for the username and password. I would like this to happen automatically so when the user logs in they automatically authenticate. How would I achieve this? I thought NTLM would play a part in this? And then the security groups that the user is part of will have a set of blocked websites that squid enforces


Thanks in advance

---

