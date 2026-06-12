---
title: "Frontend Controllers Not Registering"
date: 2011-05-14
forum: Ubuntu Cloud and Juju
---

### Post by Sum Guy on 2011-05-14
I've recently installed UEC on 2 computers, and am having problems with one of them. Despite following the installation instructions, the Walrus controller, Storage controller and Cluster controller are not registering as they should be. I tried using euca_conf to register them, with no effect. I have no idea how to apply the manual instructions for registering the controllers, as these appear to apply to multiple frontend setups. The frontend is an Athlon 64 3000+, and seems to have load averages between 1 and 2, which I would think would merely cause lag, rather than failure of a critical stage of installation. Any ideas?

EDIT: Note that I am NOT running a DNS server, instead I provided the IP address as the FQDN during installation. Is it possible to run UEC without a DNS server, and if so, have I set this up correctly?

EDIT 2: The node is also not registering, through euca_conf or automatically.

Thanks.

---

### Post by obino on 2011-05-19
Hello,

you cannot mix and match auto-registration and manual registration. If you want to switch to manual registration, it is better to disable auto-registration alltogether (I think [http://fnords.wordpress.com/2010/02/21/ubuntu-enterprise-cloud-autoregistration-features/](http://fnords.wordpress.com/2010/02/21/ubuntu-enterprise-cloud-autoregistration-features/) got a good article about it).

Can you get to the webUI ([https://localhost:8443)?](https://localhost:8443)?) If so, can you see the cluster, storage clontroller and/or the walrus? 

Can you also tell us more about your network configuration and how did you configure your servers?

cheers
graziano

---

### Post by Sum Guy on 2011-06-15
Hi, sorry for the late response, but I've managed to solve this problem, and now have [this]("http://ubuntuforums.org/showthread.php?t=1772899") problem instead.

For the sake of reference, I upgraded to a higher power frontend, and immediately after installation installed and configured bind9 to serve the domain name I set during installation. I'm not sure which change fixed it, but it seems that the lack of DNS before adding bind9 was the problem, just because it seems to be a weird problem to be caused by lack of power. My network topology is just an all in one frontend and one NC on one network, with no separate subnet for the nodes, as it is not yet a production set up.

---

