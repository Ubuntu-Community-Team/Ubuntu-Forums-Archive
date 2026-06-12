---
title: "Ventrilo server network interface trouble"
date: 2011-08-07
forum: Server Platforms
---

### Post by teslamad on 2011-08-07
Here is an interesting problem. The server that runs  this vent daemon has two physical interfaces. When I just have one  interface configured in the /etc/network/interfaces file and I boot up  the server, the vent server starts up (automatically via init.d script)  just fine. However if I go and configure the second interface and reboot  the server, the vent daemon still starts fine according to process list  (ps -aux) however the client sits at the "MSG: Contacting server."  state. Its almost as if the vent server doesn't know which IP to use so  it doesn't start properly. Any thoughts here? I'd ultimately like to  have dual Ethernet attached to this server in case of failure. I just  need both IP's to be potentially available. Thanks in advance.

I'm running Ubuntu Server 10 LTS 32 Bit

---

