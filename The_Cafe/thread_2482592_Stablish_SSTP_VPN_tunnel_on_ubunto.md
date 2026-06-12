---
title: "Stablish SSTP VPN tunnel on ubunto"
date: 2023-01-05
forum: The Cafe
---

### Post by rezaaim on 2023-01-05
hi everyone, how to establish sstp tunnel between ubunto ver 22 and mikrotik router, ? What commands are written?

---

### Post by TheFu on 2023-01-05
> **rezaaim said:**
> hi everyone, how to establish sstp tunnel between ubunto ver 22 and mikrotik router, ? What commands are written?

Does the microtik support running commands like that?  The router would need to support it.
Most routers support ssh, which can be used for tunnels.  There are lots and lots of how-to guides for ssh-tunnels, but they boil down to this command:
```
  /usr/bin/ssh  -f -C -D $PORT  $SSH_SRV  -NT &
```

where:
PORT=64000
SSH_SRV=vpn.domain.com

change those as needed.

The tunnel on the local machine into the router would be accessed by a web browser:
```
echo "Starting Firejail chromium with private & proxy "
export http_proxy="socks5://localhost:$PORT ";
  /usr/bin/firejail  --private chromium-browser \
               --proxy-server="socks5://localhost:$PORT " &
```

---

