---
title: "Suggestions for securing server P2P traffic"
date: 2010-08-10
forum: Server Platforms
---

### Post by tnine on 2010-08-10
Hi all,
  I'm working on creating for Chef recipes for installing and configuring Apache Cassandra on Ubuntu 10 servers.  The installation and P2P discovery so far is pretty straight forward, however I'm running into a wall and I could use some help.  Our instances will be hosted in the cloud, so I can't guarantee where they'll be.  By default Cassandra uses Thrift, so it communicates with no security on the network layer.  I need traffic between each node to be secured.  I'm a bit unsure how to go about this, so some guidance would be appreciated.

Each node can connect to any other node.  As a result, I need the ability to secure traffic between nodes.  My initial thought was ssh port forwarding, but this is far too difficult to manage across large clusters.  Does anyone have any suggestions for packages I can try?

Thanks,
Todd

---

### Post by jbrown96 on 2010-08-10
Openvpn is the other alternative, but it's not going to be much easier than ssh forwarding.

It should be more reliable, though. SSH forwarding has problems with interrupted connections, and if you lose the SSH connection and P2P comes back up, then you could be sharing clear-text. Since you would be sharing LAN addresses on a VPN, if you lose the VPN you can't reach the peers.

You will still need to know your IP addresses or have host names. That's something that you will have to work out with your provider, but they should have a method.


Why are you doing this? It doesn't make any sense to have separate nodes because you will be paying a higher flat rate and network use still costs. Torrents won't be any faster, so I don't know what the advantage of this is. If you really need separate nodes for some other purpose, then use some type of networked data store.

---

