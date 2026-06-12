---
title: "Ubuntu DHCP Server with Web Interface"
date: 2006-04-17
forum: Server Platforms
---

### Post by pofa on 2006-04-17
Hey All,

I want to let you all know first off I am a Linux newbie and I have searched for my answer elsewhere in the forums but can't seem to find anything. I want to set up a Ubuntu DHCP/File Server for my home. I have found extensive documentation on how to set this up and kudos and thanks to those who took the time to share such information. I, however, have housemates who live with me and are avid gamers, but are not very computer savvy. As a result I need to have a simple web interface for some basic gateway settings i.e. - Port Forwarding that they can access and modify without me. Any help with this dilemma is greatly appreciated.

-Chris

---

### Post by fdoving on 2006-04-18
Sounds like you want something like Webmin with the firewall module. 
[http://www.ubuntuforums.org/showthread.php?t=161774](http://www.ubuntuforums.org/showthread.php?t=161774)

- Frode

---

### Post by sgla1 on 2006-04-27
Please post with a description of *what* you want to achieve.  Ie who connects to what.  Then we can give you detailed recommendations.

FWIW, dhcp and port forwarding are not related--dhcp passes IP info to your local clients; port forwarding has to do with an outward-facing firewall.  They're different.  Once port forwarding is set up, you probably don't want your monkeys, er, roomates to touch it.

Cheers

---

### Post by LordHunter317 on 2006-04-27
Actually, that's exactly what he wants, for gaming.

Webmin is one way.  A firewall based distro or OS might suit you better for this, though.  I'm a m0n0wall fan myself.

---

### Post by behemot on 2006-04-27
Ipcop does all this magic for me and more.
[www.ipcop.org](www.ipcop.org)

If you really want hassle-free setup have a look at Linksys WRT54GL.
The firmware could be flashed with some great linux bits.
Google for "hyperwrt".

---

