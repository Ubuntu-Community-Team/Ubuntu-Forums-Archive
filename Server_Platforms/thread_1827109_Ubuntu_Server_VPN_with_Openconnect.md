---
title: "Ubuntu Server: VPN with Openconnect"
date: 2011-08-17
forum: Server Platforms
---

### Post by jonathanmotes on 2011-08-17
I am trying to connect a Ubuntu 10.04 Server 64-bit VM to a network with openconnect, but having trouble.

I am currently using Network Manager to make the VPN connection on a Desktop VM, so I know it has nothing to do with the VPN server.

I am running

```
sudo openconnect http://vpn.domain-name.com
```

Then:

1. Complete prompts for the group, username, and passcode
2. Says Established DTLS connection
3. Hit CTRL-Z, then type bg to send the process to the background
4. Try to ping a server on the network I'm trying to connect to - but get nothing.

Anyone know what I'm doing wrong?

Thanks!

---

