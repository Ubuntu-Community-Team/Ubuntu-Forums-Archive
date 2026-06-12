---
title: "Unable to access internet after connect to my VPN server"
date: 2015-06-18
forum: Server Platforms
---

### Post by 6-me-g on 2015-06-18
Hello 

I'm using ubuntu server as VPN server..
I've setup the vpn server using this tutorial:

[http://linuxhostingsupport.net/blog/how-to-install-and-configure-pptp-vpn-in-linux](http://linuxhostingsupport.net/blog/how-to-install-and-configure-pptp-vpn-in-linux)

But after connecting successfully to the server through windows 7 client, there is no internet access on the client behalf..!  
I tried to disable "use default gateway on remote network" and I gain internet access but lost the connection to the server network (which I want)

I think there is a problem with the command for iptables to add MASQUERADE to the interface..

ANY IDEA??

---

### Post by darkod on 2015-06-19
That iptables command looks like adding the rules temporary. Did you save them so that they are loaded after reboot? Did you check if the rules exist after reboot?

Also the iptables forward rules use the interfaces as per his blog. Did you verify if your interfaces are named the same?

I see yum is being used which means redhat based and you are posting on ubuntu forum. Did you do this on ubuntu? Are the packages identical, interface names, etc?

---

