---
title: "Using OpenVPN between two firewalled machines?"
date: 2014-06-22
forum: Ubuntu, Linux and OS Chat
---

### Post by Cubytus on 2014-06-22
Hi UF community, 

I was told, a while ago, to use OpenVPN to connect to a fire walled machine for remote access. However, no detail was ever provided.

The question is pretty simple here, how would I have the remote, firewalled machine establish an OpenVPN connection automatically toward another fire walled machine, the local one? I could make the local machine accessible on the Internet, but not the remote one. Would it be secure to have the remote machine periodically attempt establishing the tunnel toward the local one? If so, how should they be configured? Or is it a far too greater security risk?

The overall strategy revolves around NAT traversal where the remote firewall can't be manually configured.

---

