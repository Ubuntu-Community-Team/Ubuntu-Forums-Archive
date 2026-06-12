---
title: "UEC in existing network"
date: 2011-07-05
forum: Ubuntu Cloud and Juju
---

### Post by nstrydom on 2011-07-05
Hi there

If I would like to setup a private UEC in our existing network, what would be the best solution?
I need all users in the current network to be able to connect to the images that are launched by eucalyptus cloud (i.e. 10.0.1.xx)
Currently our DHCP server is a windows 2003 server.

Do I install the cloud into its own subnet (e.g. 10.0.2.xx) - if so, would it still be accessible from the current network?
Do I install in current subnet and just run as "static" mode?

So, how do I install a new cloud into an existing network that already has a configured DHCP server?

I have my instance setup at the moment with 3 machines:
1 clc
1 nc
1 ubuntu client (kvm enabled)

Currently everything starts up, and runs. Images run too, however I cannot ping or access any of the running instances.
My default security group does allow icmp traffic and ssh trafic.

I really need a solution for my problem. Been spending about 4 days now with this problem 

Your help would be appreciated!

---

