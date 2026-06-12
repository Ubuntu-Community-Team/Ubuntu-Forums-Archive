---
title: "Machine name not showing in router attached devices list"
date: 2010-11-17
forum: Server Platforms
---

### Post by cbarron on 2010-11-17
As the title says the machine name is not showing up in the attached devices list on my router. Is there a file where I need to add the name? Or is this an issue with the router? The router finds all the other machine names on the network except my 3 servers.
Ubuntu Server 10.04 Lts
Ubuntu Server 10.10 Lts

---

### Post by craigp84 on 2010-11-17
Hi,

In your dhclient.conf:

```

send host-name "my.host.name.com";

```

Hope this helps

---

### Post by cbarron on 2010-11-17
ok thanks, is that file under /etc ?

I guess I should also point out that all 3 servers have static ip's set to them if that makes a diffrence

---

### Post by cbarron on 2010-12-28
bump

---

