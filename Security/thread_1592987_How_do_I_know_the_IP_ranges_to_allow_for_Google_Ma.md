---
title: "How do I know the IP ranges to allow for Google Mail in moblock?"
date: 2010-10-11
forum: Security
---

### Post by mr_luksom on 2010-10-11
Hi,

I'm currently using moblock for ap2p guarding, and I have but one nusiance issue. How do I whitelist Gmail imap and smtp servers?

Gmail seems to changes its IP address for the servers often, and it seems like everyday I need to get the latest servers and allow them.

Surely there is a better way? Is there a range of google-only IPs? Or a big list of gmail IPs?

---

### Post by jre on 2010-10-11
I don't know a google-IP-list.

The best solution is to add every IP separately, e.g. in mobloquer whenever you have problems. Of course that is annoying.

So you may add
```
IP_REMOVE="google"
```
to /etc/blockcontrol/blockcontrol.conf to remove all ranges that contain the keyword "google". Be warned that there might be some excess ranges that would be removed that way. You will see which ranges are removed from your blocklist in /var/log/blockcontrol.log.

Alternatively you may add the imap and smtp ports to WHITE_TCP_OUT.
Most people do this, but it's a bit a security risk, because you'll allow outgoing traffic to ALL IPs on these ports then.

---

