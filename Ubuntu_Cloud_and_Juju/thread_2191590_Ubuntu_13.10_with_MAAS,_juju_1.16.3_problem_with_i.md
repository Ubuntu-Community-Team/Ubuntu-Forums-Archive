---
title: "Ubuntu 13.10 with MAAS, juju 1.16.3 problem with installing nodes, lxc, mongodb, juju"
date: 2013-12-03
forum: Ubuntu Cloud and Juju
---

### Post by bjorne2 on 2013-12-03
Hello!

I have some problem, im try to understand if I have do something wrong or that is some thing else that is the problem.

1. I have install MAAS with dns and dhcp.
2. I have nodes and they starts up 1-3 nodes.
3. Here is the problem. some of the nodes installs lxc, mongodb plus jujud and run a dist-upgrade on ONE node not all.
    Im get only juju status for one node not all.
  3.1 should lxc, mongodb plus jujud be installed with some scripts and that is autorun? is that scripts fails? what is the name for this script?
  3.2 or should i do i manual on every node? or how i do that? like apt-get install lxc mongodb-server juju-core? like that?
  3.3 or should this script run on every node so that is be installed so i can see all nodes in juju status?
  3.4 or need im setup landscape for this or what is the problem im doing?


Im have try to google this and dont find any information about this? mayne im looking after wrong things?  

Can someone help me so im understand the problem, or what i do wrong? 

//bjorne

---

