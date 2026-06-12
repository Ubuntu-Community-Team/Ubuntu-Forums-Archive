---
title: "vpn access to ubuntu hosted samba share"
date: 2008-10-13
forum: Server Platforms
---

### Post by kadil on 2008-10-13
Maybe someone can point me in the right direction. I have an internet server, which also hosts samba shares for my home network , obviously with firewall rules so samba is not exposed to the net. Is there a way that I can set up a vpn over the internet so I can access these shared drives over the internet in a secure way. I am not looking for a remote desktop solution, but secure file access over the internet. Am I asking for too much?

Regards,
Kim

---

### Post by sonicb00m on 2008-10-13
It really depends on what you want to do, there are many solutions.

The simplest way is to connect via ssh to your server. I use a bookmark from Nautilus when mounts the drive as soon as enter the bookmark

Add

```

ssh://user@domain:port/path

```

in the the nautilus url bar and type in your password. It can remember it for you.

Another, more complex way is to set up a trusted SSH link between the two computers. You can generate trusted keys and write a script to mount the SSH drive immediately, connecting you without a password to your server. This is a bit harder and requires a little searching on the forums for it.

I always move the SSH port away from 22 which stops random attempts at accessing your server (since most script hackers only check common service ports to target).
You can also continue to firewall it but for me it's not a good solution because of the dynamic nature of the client ips.

You can also set up VPN but I have no idea how to do that yet.

---

