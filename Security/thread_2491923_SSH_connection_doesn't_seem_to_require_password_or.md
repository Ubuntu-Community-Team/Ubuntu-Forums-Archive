---
title: "SSH connection doesn't seem to require password or key to connect"
date: 2023-10-25
forum: Security
---

### Post by lucienfradet on 2023-10-25
I have uncommented `PermitRootLogin no` in /etc/ssh/sshd_config and now it seems like I can connect to my ubuntu server with any computer without ever being asked a password. I feel like I don't have any keys. my ~/.ssh/ is empty on the server side and looking at ssh -T it shows, that password authentication is set to yes and key set to no. I don't feel like any of the changes I make to the config files hace any effect. I have also restarted ssh and sshd as well as the whole server.

---

### Post by lucienfradet on 2023-10-25
Ok I think the fact that I'm using Tailscale is bypassing the default configurations and using Tailscale authentication instead

---

