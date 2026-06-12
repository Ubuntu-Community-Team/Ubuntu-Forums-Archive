---
title: "Wireless network on server"
date: 2008-09-27
forum: Server Platforms
---

### Post by frodemt on 2008-09-27
Hi.

Does anyone know of a good guide on how to set up a wireless connection on a ubuntu server?

---

### Post by jamesrfla on 2008-09-27
This might help after a Google search.
[http://beginlinux.com/desktop_training/ubuntu/ubnet_m/ub_wirless](http://beginlinux.com/desktop_training/ubuntu/ubnet_m/ub_wirless)
Are you trying to connect to a wireless network using Ubuntu or create a wireless network using Ubuntu?

---

### Post by frodemt on 2008-09-28
Hi again and thanks for the link. I am trying to connect the server to a wireless network configured on my router.

As I have no GUI on the server, the guide in the link you gave me wont help me mutch.

---

### Post by windependence on 2008-09-28
This might help you get going:

[http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html](http://www.stoltenow.com/archives/2006/12/ubuntu_configur.html)

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

Kudos to you for NOT using a GUI on a server. :)

-Tim

---

### Post by lykwydchykyn on 2008-09-28
I think iwconfig is the command you need.  I say "I think" because I'm not sure to what extent network-manager is extant in server edition; in the days before network-manager, iwconfig was the command to use, but I believe it conflicts with network manager on desktop editions.  What sort of security is the WAP using?  WPA?

---

