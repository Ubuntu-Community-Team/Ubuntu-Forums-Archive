---
title: "netplan and dhcp server"
date: 2018-10-31
forum: Server Platforms
---

### Post by diman.maharjan on 2018-10-31
I get this issue of ethernet interface not being up unless it is connected to some other device.In my Ubuntu 18.04 server, I installed isc-dhcp-server but the dhcp server doesn't work unless its connected. After researching a bit more I think it may be because the interface had not been up unless its connected. After assigning static ip with netplan , static ip  is not shown with ipconfig unless the ethernet is connected to some other networkable client machine. After connecting to other device , the dhcp server starts after restarting the isc-dhcp-server. In summary, dhcp server is working only when the client devices are already pre-connected. Otherwise i have to restart dhcp-server manually. What might be the problem? Thanks in advance.

---

### Post by slickymaster on 2018-10-31
Thread moved to **Server Platforms** for a better fit

---

### Post by darkod on 2018-10-31
I didn't understand anything...

You set up dhcp server but it doesn't work unless the server machine is connected to the network? That makes sense for me. If you plan to have your server NOT connected to the network, how do you plan to offer dhcp leases to clients?

---

