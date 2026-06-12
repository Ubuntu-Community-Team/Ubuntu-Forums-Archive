---
title: "How to configure an Ubuntu VPN and File Server for small office"
date: 2009-02-11
forum: Server Platforms
---

### Post by madklaus on 2009-02-11
Hi everyone,

I'm new to Ubuntu so please excuese my eventual stupid questions :)

I want to configure a File and VPN Server for my small office to be able to work from home and to always have secured, backed up and updated files.

Recommended by a friend, I installed Ubuntu on the computer and now I want to know how to do things right so that I don't have to worry about the server for the next year or so :)

Note that at the office we use Windows XP Pro PCs and Apple MacBooks (with Leopard) so the server should be configured for both user types.


Thanks in advance!!!

---

### Post by JeppeM on 2009-02-11
Hey,

First of all, a few starting questions. What computer have you installed ubuntu on? And how is the infrastrucure in the office you're talking about - for example, do you have a gateway/firewall mashine? If you don't know this, then try to figure out where the internet line is plugged in, and how that router/server gives out the internet connection to the rest of the office... Also, what version of ubuntu have you installed (Desktop or server, 8.04 or 8.10?)

With these questions asked, i think the best place for you start is the ubuntu server guide ([https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html) for 8.10, [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html) for 8.04). You should look into Samba File Server from those guides, and then openvpn from here: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

hope this helps a bit on your way :)

---

### Post by yknivag on 2009-02-11
I'm trying to do something very similar (see [my thread, here]("http://ubuntuforums.org/showthread.php?t=1064282"). It, rather surprisingly, seems to be something very few people know about.  Or at least are prepared to share opinions on.

I'd be most interested to see how you do it.

---

