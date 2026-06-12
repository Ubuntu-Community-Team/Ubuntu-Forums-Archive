---
title: "Set up Socks Server"
date: 2009-04-21
forum: Server Platforms
---

### Post by lord_raptor on 2009-04-21
Hello,
I want to install a Socks5 Server (Or Socks4, but I really would like to have an access control beside using IP ranges) on my Ubuntu Server.

Until now I have tried SS5 and Delegate, but I didn't get either of them to work. Does someone know of a good HOWTO about setting up a Socks5 server with authentification (and how to set up the authentification)?

SS5 seems to be the best package out there, but the documentation is very limited.

Greetings
Lord Raptor

---

### Post by Dr Small on 2009-04-21
I just use OpenSSH as a SOCKS server.

---

### Post by BkkBonanza on 2009-04-21
Yup, with SSH you can use keys for authentication. Read the man on the -D option.

```
ssh -D 8080 myname@myserver.com -N
```

Will open a SOCKS5 tunnel from your local machine to the server. Any type of local requests told to use socks proxy at port 8080 will get sent to the server and be issued from there. You can get fancier as well with reverse tunnels and stuff. It's very easy, already installed and powerfull.

---

### Post by lord_raptor on 2009-04-21
It works, thank you.

Is there a way to minize the speedloss?
When I tested the downloadspeed, I only got a fraction of the server's capabilities.
But I don't know if the problem is client or server-side (I think it's on the server-side because I already tried with multiple PCs)

---

