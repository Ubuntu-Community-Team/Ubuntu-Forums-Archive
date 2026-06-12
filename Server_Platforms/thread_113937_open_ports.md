---
title: "open ports"
date: 2006-01-07
forum: Server Platforms
---

### Post by Marshall2day on 2006-01-07
Hi All,

I've performed a portscan on my desktop pc and noticed 2 ports of which I have no idea which service or program depends on it.

TCP 609 npmp-trap
TCP 752 qrh

Does anyone know anything more about this?

---

### Post by tcwitte on 2006-01-07
Hi,

[QUOTE=Marshall2day]2 ports of which I have no idea which service or program depends on it.[/QUOTE]

I don't directly know the answer, but you can do a
```
sudo netstat -tuxap
```
to determine what program has what port (this is better than doing a portscan because this is complete). The x in the command is probably not interesting BTW.

---

### Post by Marshall2day on 2006-01-07
Thanks, that cleared things up for me!

---

