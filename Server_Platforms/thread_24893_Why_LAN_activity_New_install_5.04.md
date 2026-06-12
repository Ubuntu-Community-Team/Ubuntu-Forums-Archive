---
title: "Why LAN activity? New install 5.04"
date: 2005-04-08
forum: Server Platforms
---

### Post by pape on 2005-04-08
Just installed Kubuntu 5.04 final

My LAN led is blinking hysterically all the time. What is going on?

I've installed following programs:

-allowed all repositories (along wiki guidelines, inlcuding this gpg key thing)
-Emacs, Firefox, flash, java, realplayer, acrobat, kuickshow, ksynaptics (KDE touchpad config)

I'm on a DHCP network in a university (is it that?)

Best regards,

Mr. Neurotic

---

### Post by valthonis on 2005-04-08
[QUOTE=pape]My LAN led is blinking hysterically all the time. What is going on?[/QUOTE]

This is very common on large networks.  If your machine is directly plugged into the wall (rather than through a home router or hub), it sees a large volume of traffic on your local segment of the network.  All those packets aren't necessarily for you; depending on the sophisitcation of your university network, your computer may be on a large switch or hub that broadcasts packets meant for one machine to ALL the machines attached to it. If your university community is primarily Windows based, many of these packets will be related to the Windows file sharing protocol (Samba/NetBIOS).  Also, if there a lot of P2P filesharing clients on your network (as is common in a university setting), that would account for a heavy volume of traffic as well.  The point is that this usually isn't something to worry about on a college campus.

If you are concerned about your computer's security, I heartily advise you install Firestarter to manage the iptables firewall built into the Linux kernel, and the *ethereal* network protocol analyzer.  Firestarter will ensure that the university network will only see what you allow them to see, and ethereal will allow you to see exactly what those flashes of light represent and where they come from.

Hope this helps!

-V

---

### Post by pape on 2005-04-08
Thanks a lot for such a good answer.

It may be what you suggest, as it does the same if I log on to winXP (I haven't been on this network much, so I was surprised). Anyhow, nothing to do with Ubuntu it seems.

---

