---
title: "Virtualbox with ubuntu server edition. interfaces address questions."
date: 2011-05-06
forum: Server Platforms
---

### Post by relic70 on 2011-05-06
I've installed Lucid server edition in VirtualBox in an attempt to learn how to use php and mysql with apache server.

Host system is Lucid.

Following some tutorials I've managed to install the server in VirtualBox. At this point the tutorials indicate address entries that must be included in /etc/network/interfaces file.

That is where I have questions regarding which addresses to use in the file with the entries following the tutorial example

auto eth0

iface eth0 inet static
address ??
netmask ??
network ??
broadcast ??
gateway ??

Which ?? addresses come from the host and which come from the server installed in VirtualBox?

I can find addresses from ifconfig, netstat -nr, and in the resolve.conf files for both machines.

Thanks for any guidance on this.

---

### Post by YesWeCan on 2011-05-06
Hi. I some some ideas that might help.
By default, VB effectively puts a virtual router between the host's ethernet and the guests ethernet. That is, when the "Network Adapter" settings in VB are set to "NAT". I think you can set the adaptor to "Bridged" to bridge the two of them.

I am guessing but I assume you want to do everything in the guest. So you can run ifconfig to see how the guest eth0 is set up. You may need to refer to the VB User Manual. Then you need to adjust the virtual router as you would a real router, by adding a port forward to it so your guest server can listen for externally initiated connections. I assume you want to be able to access your guest's web-server from the internet.

My knowledge is a little limited, but hope this either helps or sparks some ideas. :)

---

### Post by relic70 on 2011-05-06
Thanks YesWeCan for the "bridged" settings hint for for VB Network Adapter.

When I did that I found the various addresses required for the virtual machine and host machine to be almost identical except for the IP of course.

I inserted the pertinent addresses into the 'interfaces' file and successfully restarted the network without error.

Now, on to playing in my VB sandbox.

---

