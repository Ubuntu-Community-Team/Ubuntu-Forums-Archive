---
title: "Redirect UDP multicast signal over ssh tunnel"
date: 2011-08-11
forum: Server Platforms
---

### Post by simonjoerg on 2011-08-11
Hi

I have been trying to reach a UDP video stream on a remote network through a SSH tunnel, it has however showed to be more difficult than i thought.

the setup is like this

#############
#windows machine#
#############
10.10.1.X| Eth0 22
###########
#Ubuntu server#
###########
10.49.X.X| Eth1 UDP 5501
################
# UDP Multicast server #
################

I can create the tunnel from the windows machine to the ubuntu server and access other servers on the 10.10.1.X network, aswell as the internet.

On the 10.49.X.X i have multiple UDP multicast servers and the idea is that in the end to reach each one of them through SSH tunnels, this network is not connected to the internet, only the ubuntu server.

I been looking around on different forums and various how to sites and some suggest i need to convert the TCP stream into UDP stream with ncat, but i dont want to send any data from the windows machine to the UDP multicast servers, just reach a multicast signal on eth1 and redirect it down the tunnel to the windows machine attached on eth0.

Anyone has any ideas how to accomplish this ?

Regards
Simon

---

