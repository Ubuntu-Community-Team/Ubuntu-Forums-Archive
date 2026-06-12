---
title: "Running two SSH servers simultaneously"
date: 2006-09-08
forum: Server Platforms
---

### Post by Randomskk on 2006-09-08
I'm currently looking at setting up a second, somewhat more accessible SSH server. My current SSH server, that runs in the normal init.d fashion, is really locked down - only one user allowed, only with key authentication, all that.
It's also not exposed to anything further than my firewall, and only one computer is allowed to connect - and even then, that IP's allowed to be used with my MAC.

Thing is, I want to be able to connect to SSH for an entirely different purpose - SOCKS forwarding. I plan on using puTTY plus SSH's -D option to allow me to have a quick SOCKS server wherever I go. This plus portable firefox = encrypted web browsing.

Anyway, I need to setup SSH so that, basically, users connecting are chrooted to their (empty!) home directory, again only keys allowed, but mainly I need it to be running at the same time as the main SSHd, and preferably NOT running as root. I'll happily make a remote access user to run the SSHd, but I'd rather not expose an SSHd that's being run by root to the world, no matter how secure it is.

So, then: how can I have two copies of SSH running at the same time, one non-root, and how can I have all users on the second be chrooted home?

Thanks for any help

---

### Post by rastilin on 2006-09-08
Well I see a technical difficulty there. I suspect there IS a way to run two ssh servers at once as long as you accept that one of them will be using a different port. But can a non-root account use chroot?

Chrooting might be the best way to get this running actually. Untar a gentoo stagefile into a directory, chroot into that and start it's ssh server seprately and with different settings. That's the only way I can think of.

---

### Post by Randomskk on 2006-09-08
I've managed to start sshd with the remote user easily enough - I generated DSA and RSA public/private keys, copied my normal SSH config file and changed a few lines (key locations and ports, basically).
Then, with the "remote" account:
/usr/sbin/sshd -f.ssh/sshd_config

At which point the SSHd starts up, and I can connect to it using my key on port 13000.
However the connected user's able to easily move around the filesystem, and I'd rather they not be able to move out of /home/remote.

Rastilin: I'm guessing stagefiles are kinda like filesystem images or something? Haven't spent much time with gentoo really.

---

