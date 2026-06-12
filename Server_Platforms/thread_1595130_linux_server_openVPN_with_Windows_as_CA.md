---
title: "linux server openVPN with Windows as CA"
date: 2010-10-12
forum: Server Platforms
---

### Post by Linux&amp;Gsus on 2010-10-12
Hi all.

We are merging 2 office into 1 but we'll continue to have different groups of people connecting to different servers from outside via VPN. Right now there are 2 VPNs existing and we would like to reduce that since the traffic can be routed internally to the correct server.

So far I have openVPN running on the Linux server with its own Certificate Authority (CA). So, I create the needed certificates right there. People connecting to that one are pretty much only Mac and Linux users.
Though, in (near) future we want to have the certificates created by a Windows box.

Now, my question is, and I didn't find any info on the openVPN website about that, is that possible to do? Can I have Windows as CA and then create the certificates from there and make it work with openVPN?

Has anyone done that before? Is there a how-to available somewhere? Maybe I'm missing the obvious on the openVPN website.
Do I assume correctly that the Windows box needs to create a new Master Certificate for that server?

Any help is appreciated.
Cheers,
L&G

---

### Post by Linux&amp;Gsus on 2010-10-15
Bump

---

