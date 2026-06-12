---
title: "Which devices, which update themselves over the internet, represent a security risk?"
date: 2014-02-18
forum: Security
---

### Post by Odyssey1942 on 2014-02-18
In the thread "Is this PC Hacked?" 3rdalbum made a very interesting post (#11) regarding port security. Since this is a slightly different topic, thought best to start another thread.

My question is which devices that are commonly found on home LAN's, an example of which might be a TIVO box, or a SlingBox, or an internet enabled TV, or a Nest, etc, might need special attention to mitigate security risks.

If I understand it, if a device is listening for incoming connections, it is risky. Perhaps all of these initiate all of their updates by outgoing request?

What about TeamViewer or another program that allows you to reach your home computer from another computer outside your LAN?

---

### Post by SeijiSensei on 2014-02-18
If the devices are behind a firewall router, they shouldn't be any more vulnerable than PCs.  These devices operate as clients making requests to remote servers for content.  They need not have any open ports to do this. This is the "client/server" model which underlies most content delivery on the Internet.

Enabling remote access is a different matter entirely.  There the target machine must be visible over the Internet.  The simplest solution in these cases is to write firewalling rules that limit access to just a small set of pre-determined IP addresses.  Another option is to use a tunnel like OpenVPN and force all connections over the tunnel.  Without the appropriate ciphers, connecting to the VPN port would be pretty useless.

---

### Post by Odyssey1942 on 2014-02-26
SeijiSensei's reply was interesting, but I don't feel that my question has been directly answered, so will request the mod to move it to the "Security Discussions" forum.

I am a bit nervous about venturing outside the Beginner's forum, so please be patient with me. Thanks.

---

