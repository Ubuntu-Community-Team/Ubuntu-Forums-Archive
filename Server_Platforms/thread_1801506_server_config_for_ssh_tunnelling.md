---
title: "server config for ssh tunnelling"
date: 2011-07-10
forum: Server Platforms
---

### Post by brighty22 on 2011-07-10
Hi,
I'm running Ubuntu Server 11.04 with OpenSSH, trying to create an ssh tunnel (for web traffic) to it from my (also Ubuntu) laptop. This is the command I'm using to create the tunnel:

```
ssh -ND localhost:8080 george@192.168.1.20
```

I had it all working on a virtual machine.. which was deleted :mad:

What settings/lines do I need to change/add from the default OpenSSH config files to get tunnelling to work? I've Googled and AllowTcpForwarding is set to yes, as is X11Forwarding.. but it still doesn't work. Chrome can connect to the server, but says the connection was closed before any data was sent.

Thanks for any help :)

---

### Post by rudelgurke on 2011-07-11
Is the connection made successfully ? Server side it logs something about a new SSH connection.
Oh - for a simple tunnel - you won't need X11 forwarding. ;)

Well - simple config - server side:

```

AllowTcpForwarding yes
Match user example
 ForceCommand true

```

And client side - $HOME/.ssh/config

```

Host your_server.com
 User example
 ...
 authentication like pubkey etc.
 ...
 LocalForward 8080 127.0.0.1:3128

```

Would forward the port 3128 from a proxy server listening on 127.0.0.1 on your server to your local machine on port 8080.

---

### Post by brighty22 on 2011-07-12
yep it connects... otherwise I doubt it could 'close' the connection :/

I turned x11 off and it didn't work.. and even with the client config (which I didn't use before) still no joy :(

---

### Post by brighty22 on 2011-07-14
It wasn't Ubuntu at all.. nor my client machine; it was my own stupidity. I was putting the address of the server into Chrome settings as an HTTP rather than SOCKS proxy. All good now, with X11Forwarding off :)

---

