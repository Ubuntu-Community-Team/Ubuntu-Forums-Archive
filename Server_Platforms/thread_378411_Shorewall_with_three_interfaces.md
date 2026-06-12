---
title: "Shorewall with three interfaces"
date: 2007-03-07
forum: Server Platforms
---

### Post by ton80 on 2007-03-07
I have just set up Ubuntu 6.10 on a system.  Initial configuration was with a two-interface setup.  This worked fine and I was able to us Webmin to configure shorewall.  I then went for the three-interface setup to add a DMZ for a web server.  On the server machine, all configuration went well.  
I have two issues:
1)  I now cannot access the firewall machine via Webmin from a client machine on the network. I get server connection errors.  If I start the firewall from the router/firewall machine, all works well and it appears the router and firewall are working properly.  So why can I not make use of Webmin when configured this way?

2)  I have a dynamic IP assigned by my ISP.  The guide I followed to setup shorewall for the three-interface configuration stated that to handle the dynamic IP, use a variable in the rules to get the current IP of the NIC connected to the cable modem.  A script was provided and it said to place the script in the /etc/shorewall/params file.  This file did not exist so I created it and added the script.  I then configured the shorewall rules file as directed.  When I did this...shorewall would not start.  So if this is not the right way to do this...as directed by the howto....how can I do this?  Configuring the rule with the static internal IP of the web server works fine.  But when the IP address changes dynamically, I am going to have problems...I think!??  Maybe??

Any ideas?

Thanks,
Mike

---

