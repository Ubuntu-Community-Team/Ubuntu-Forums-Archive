---
title: "WinXP remote desktop management via Linux?"
date: 2008-02-03
forum: The Cafe
---

### Post by mips on 2008-02-03
Hi,

I need to find a way to have a SECURE connection over the internet in order to control a remote WinXP machine from my linux box.

It does not seem like FreeNX can do this as there is only a windows client available from nomachine.

My adsl connection is only 384kb/s down & 192kb/s down so keep this in mind.

The only possible solution I can think of right now is TightVNC, Stunnel & OpenSSL on the windows server and TightVNC on my linux pc.

Anyone got any ideas?

---

### Post by Ardrias on 2008-02-03
Tunnel TightVNC over SSH?

---

### Post by mips on 2008-02-03
> **Ardrias said:**
> Tunnel TightVNC over SSH?

Yes ;)

---

### Post by UbuWu on 2008-02-04
Ultravnc has several encryption plugins, so you wouldn't need ssh or any additional software.

---

