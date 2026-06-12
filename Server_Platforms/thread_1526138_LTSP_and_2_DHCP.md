---
title: "LTSP and 2 DHCP"
date: 2010-07-07
forum: Server Platforms
---

### Post by wurzzero on 2010-07-07
Hi, i have a Mandriva DHCP server and install another DHCP server in my Ubuntu 10.04 with LTSP, with some modifications in Ubuntu dhcp.conf

The LTSP client works.

I want to know if i could use the Mandriva DHCP and only LTSP in my Ubuntu, without DHCP.

Tanks...

---

### Post by astbis on 2010-07-10
Yes. Look at the "next-server" option in dhcp.

---

### Post by wurzzero on 2010-07-10
Tanks, i'll make some tests.

---

### Post by John Waller on 2011-01-02
Dis you get this to work? If yes, how?

Can you copy your config file here?

---

