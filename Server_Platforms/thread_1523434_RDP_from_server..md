---
title: "RDP from server."
date: 2010-07-03
forum: Server Platforms
---

### Post by Xeneth on 2010-07-03
I can SSH to my server from anywhere in the world, but it has no GUI in it.  Now my Question is, 2 fold.

1. How do I look at the leases for DHCP3-server to see the current IP of my desktop?

2. How do I open a RDP tunnel so I can view my home PC through my SSH connection?

Thanks

---

### Post by HermanAB on 2010-07-04
1. Enable X forwarding in /etc/ssh/ssh_config

2. Use rdesktop.

---

