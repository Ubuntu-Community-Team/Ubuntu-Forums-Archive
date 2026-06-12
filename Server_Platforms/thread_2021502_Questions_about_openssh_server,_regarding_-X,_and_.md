---
title: "Questions about openssh server, regarding -X, and domain forwarding"
date: 2012-07-09
forum: Server Platforms
---

### Post by Sansari on 2012-07-09
Ignore this -X problem, found out it was a client error not a server error.
> First of all, I've got a server running Ubuntu 12.04 (not server, but I don't think that should matter). I installed openssh server and config'd it, and I was able to connect to it just fine from an ubuntu laptop using both ssh [host] and ssh -X [host] for when I wanted to use graphical applications. Both took only a couple of seconds to connect. All of a sudden today when I tried to connect with -X it stopped working - it just hangs and times out. If I don't use the -X command I can still connect. Any idea why this might be happening? I don't think I've changed anything but I did try following ubuntu's vnc guide for "Logging in from another Ubuntu PC" here:

[https://help.ubuntu.com/community/VNC#Accessing_your_PC_over_the_Internet](https://help.ubuntu.com/community/VNC#Accessing_your_PC_over_the_Internet)


I still would like to know this:
> Also, I normally connect to my server with the command ssh user@[ip address]. I use a key, so it normally connects immediately. When I connect using a domain forwarded to the same ip, like ssh user@[domain], it tells me "The authenticity of host '[domain]: port ([ip]: port)' can't be established" then lists an ECDSA fingerprint. I use an RSA key, though. My question is, am I making an ssh connection to the domain server first? Is it insecure? I was kind of expecting to directly communicate with my server and not have anything to do with the domain.

---

### Post by HermanAB on 2012-07-09
"-X it stopped working"

What kind of system are you connecting from?  You must have an X server running on that machine.  If it is Windows, then you need Cygwin running before you try to connect to the remote machine.

---

### Post by Sansari on 2012-07-09
Nope it's ubuntu. Like I said it was working fine yesterday, and just doesn't today.

the full command is ssh -X -p [port] user@[ipaddress]

EDIT

Found out it was a client error not a server error. The domain question still stands.

---

