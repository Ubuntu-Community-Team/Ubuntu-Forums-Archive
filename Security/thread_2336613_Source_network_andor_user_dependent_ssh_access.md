---
title: "Source network and/or user dependent ssh access"
date: 2016-09-09
forum: Security
---

### Post by marco2g on 2016-09-09
Hello everyone!

I am in the process of bringing my home network to a more professional level. As such, I have created a VLAN to house my torrent server and SSH tunnel endpoint for browser traffic.

Now I have a little problem: To work on this server (a VM) I use ssh with putty. At the same time, I have, so far, used Bitvise SSH on a windows machine to tunnel in from work (and thus working around a pesky proxy).

I would like to know if it is possible to allow access for User A only from a local network, not necessarily the one the server resides in, and access for the other user B only for tunneling purposes, so without opening a shell.

As a gateway I have an untangle VM. WAN resides in VLAN4, my workstation in VLAN2 and the ssh server in VLAN3.

If my intentions should be confusing or otherwise unclear, I'll be glad to clarify.

Thanks.

---

### Post by TheFu on 2016-09-10
Not sure, but use tcp-wrappers to limit access by subnet for most services.
Then you can limit each userid access in the sshd_config file.

Might be easier to use a VPN from the WAN to limit access (control the per-userid-keys) and don't allow ssh in directly.

OTOH, I haven't a clue about Windows. Stopped letting Windows have general internet access about 9 yrs ago. Just couldn't sleep at night with that machine connected.

---

