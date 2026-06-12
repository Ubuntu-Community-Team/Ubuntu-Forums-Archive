---
title: "nic not detected in jaunty"
date: 2009-04-24
forum: Server Platforms
---

### Post by jeremyphares on 2009-04-24
I have a nic card that is not detected in Jaunty. I know that it works and is compatible with Linux and Ubuntu. I was using the server, however I needed to reinstall to get rid of alot of cruft I had installed on it and thought it would be best to wait till Jaunty came out. I downloaded Jaunty earlier and when it was install it said that it could not configure the network with dhcp. I just set it to a static ip and finished the install. Now after I started the computer the NIC is not showing up at all. Any guidence would be useful.

- Running 9.04 Basic setup with LAMP and OpenSSH configurations applied
- NIC isn't being detected
- Worked in 8.10 JeOS not even 10 minutes before I started the new install

---

### Post by jeremyphares on 2009-04-24
Ok, so I went back and ran 2 commands.

```

modprobe -r e100
modprobe e100

```

Now when I run *lspci | grep net* it shows my NIC, Intel 82562EZ if your wondering. Here's the kicker. When I run *ifconfig -a* I see the card, it has the correct MAC, but will not get on the network.

---

