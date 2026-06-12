---
title: "How to connect Ubuntu 16 (as client) to a Fortinet VPN?"
date: 2020-04-30
forum: Server Platforms
---

### Post by riveravaldez on 2020-04-30
Hi, I'm on an Ubuntu 16 laptop and need to connect (as client) to the VPN of an employer that uses FortiClient VPN.

Right now the official FortiClient available for Linux lacks precisely VPN functionality...

What should I do, or what can I do, or which are my options (or the preferred/proper one)?

Thanks a lot, really, !

---

### Post by QIII on 2020-04-30
Hello.

16.04 or 16.10?

---

### Post by ActionParsnip on 2020-05-01
[https://www.forticlient.com/repoinfo](https://www.forticlient.com/repoinfo)

They have a repository. Have you tried that?

---

### Post by riveravaldez on 2020-05-02
16.04, afaik.

Thanks a lot!

---

### Post by riveravaldez on 2020-05-02
> **QIII said:**
> Hello.

16.04 or 16.10?

16.04, afaik.

Thanks a lot.

---

### Post by riveravaldez on 2020-05-02
> **ActionParsnip said:**
> [https://www.forticlient.com/repoinfo](https://www.forticlient.com/repoinfo)

They have a repository. Have you tried that?

Yes, I've installed the FortiClient for Linux from there, following those instructions.

That's the official FortiClient for Linux, and it lacks VPN funcitonality...

I don't know what should I do in order to stablish a client VPN-connection from my Ubuntu box...

Thanks a lot.

---

### Post by wildmanne39 on 2020-05-02
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by volkswagner on 2020-05-03
It appears you are correct. The Linux version "Forticlient" does not
include VPN function.

You'll need to get VPN information from your employer and
set the connection up manually. 

Depending on your employer's server (L2TP, IKEv2 or something else) or
if they are using certificates and/or secrets your choice of set up may vary.

---

### Post by riveravaldez on 2020-05-05
> **volkswagner said:**
> It appears you are correct. The Linux version "Forticlient" does not
include VPN function.

You'll need to get VPN information from your employer and
set the connection up manually. 

Depending on your employer's server (L2TP, IKEv2 or something else) or
if they are using certificates and/or secrets your choice of set up may vary.

So, there's no way to install any official Fortinet-VPN client on Ubuntu 16.04?

On the other hand, there's no alternative (some unofficial client) that works?

Thanks a lot.

---

### Post by aljames2 on 2020-05-05
No way, as just said.  Your employer will need to provide the setup & credentials needed.  Call IT support.

---

