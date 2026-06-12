---
title: "Ubuntu 14.04.2 and Nagios"
date: 2015-06-01
forum: Server Platforms
---

### Post by David_Cummings on 2015-06-01
Hello All,
I am new to Linux (well other than some Raspberry Pi usage) and I have been asked by my boss to setup Nagios. Has anyone here had dealings with Nagios on  a fairly big network. we have approx. 50 servers, countless switches and several websites we need to monitor (as well as certificates). can anyone point me in the right direction?

---

### Post by dino99 on 2015-06-01
here is a recent howto  [http://tecadmin.net/install-nagios-monitoring-server-on-ubuntu/](http://tecadmin.net/install-nagios-monitoring-server-on-ubuntu/)
and an other guide [https://www.digitalocean.com/community/tutorials/how-to-install-nagios-4-and-monitor-your-servers-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-nagios-4-and-monitor-your-servers-on-ubuntu-14-04)

---

### Post by tgalati4 on 2015-06-02
Nagios/Cacti are an older monitoring framework.  There are others that you may want to look at:

[http://www.infoworld.com/article/2683857/network-monitoring/article.html](http://www.infoworld.com/article/2683857/network-monitoring/article.html)

I would pick two and set them up on separate machines (could be virtual machines) and run them for a while and then downselect after 6 months depending on your needs and what management wants to see.

---

