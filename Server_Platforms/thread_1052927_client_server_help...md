---
title: "client server help.."
date: 2009-01-28
forum: Server Platforms
---

### Post by ubhi on 2009-01-28
Hi,

i am trying to adding my ubuntu client to my Active Directory Domain using likewise,
but i faced the following error while joining the domain.

Manual configuration required

The configuration stage 'open ports to DC' cannot be completed automatically. Please manually perform the following steps and rerun the domain join:

Some required ports on the domain controller could not be contacted. Please update your firewall settings to ensure that the following ports are open to 'domain.com':

88 UDP
137 UDP
389 UDP
464 UDP
123 UDP
88 TCP
464 TCP
Details

Error code: (null) (0x00080043)
Backtrace:
main.c:310
djmodule.c:248
djmodule.c:211

Now, i don't understand either this want to be open all ports on client site or at server site,,, because i already try once by opening all required port on server.
but i am not successful.
if i need to open port on client at ubuntu machine then how it happens.

Please Help..

---

