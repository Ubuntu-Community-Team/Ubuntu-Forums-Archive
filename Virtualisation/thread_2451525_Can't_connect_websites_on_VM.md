---
title: "Can't connect websites on VM"
date: 2020-10-06
forum: Virtualisation
---

### Post by satimis on 2020-10-06
Hi all

Host OS - Ubuntu 20.04 desktop
VM OS - Ubuntu 20.04 desktop

I have WordPress sites created on VM sometimes ago. At time of their building the LAN Address of the VM was 192.168.0.101. The WP sites are on;
/var/www/html/site1
/var/www/html/site2
/var/www/html/site3
/var/www/html/site3
etc.

To browse the WP sites just on browser ran;
/192.168.0.101/site1
/192.168.0.101/site2
/192.168.0.101/site3
/192.168.0.101/site4
etc.

Now the router IP address has been changed to 192.168.1.1. I have changed the VM IP address to 192.168.1.101, replacing 0 with 1

ifconfig shows IP address correct.

But websites can't be login to admin

Running
192.168.1.101/site1/wp-login.php

It took prolonged time and finally failed with warning;```

The connection has timed out

The server at 192.168.0.216 is taking too long to response
.......

```

It shows IP address 192.168.0.216.

Please advise how to fix the problem? Which file I have to edit? Thanks

Regards

---

### Post by TheFu on 2020-10-06
Which hypervisor is being used?  Are the guest VM connections setup as bridged for that VM?
Does the web server configuration specify an IP address?  They don't need to, but you may have set one in the sites-enabled/ config files.  
I just specify the port, no IP, in my configs so this isn't an issue.

You can use telnet to visit the website
**telnet     192.168.1.101     80**
Type "GET" if that connects. The top page HTML should be returned. 

If no connection is made, check that 
[LIST]
[*]the web server is on port 80, 
[*]the IP address used from outside is correct,
[*]the firewall allows connections from your client to the server
[/LIST]
The web server logs should show any connection. Check there first. If nothing shows up, then that is the first issue to fix.  We've all done this.


With VMs, if the networking is set to be bridged, then it is unlikely any inbound connections will be allowed. Host-only, NAT, and one other I can't remember the name of don't allow inbound connections.  But it depends on the hypervisor used.

---

### Post by satimis on 2020-10-06
> **TheFu said:**
> Which hypervisor is being used?  Are the guest VM connections setup as bridged for that VM?
Does the web server configuration specify an IP address?  They don't need to, but you may have set one in the sites-enabled/ config files.  
I just specify the port, no IP, in my configs so this isn't an issue.

- snip - 
Hi

Thanks for your advice.

The problem is caused by database, mariadb, in my case.  I almost forgot. Please see my following posting on WordPress Org about 4 weeks ago;
[https://wordpress.org/support/topic/duplicator-how-to-change-local-ip-address-of-a-cloned-site/](https://wordpress.org/support/topic/duplicator-how-to-change-local-ip-address-of-a-cloned-site/)
post - 3 weeks, 2 days ago

There are 35 websites on this VM.  It'll take me lengthy time to correct the problem on all of them.  I'm considering whether it would be easier to clone all of them on a new VM?  I have their Duplicator packages on my database.

Regards

---

### Post by ActionParsnip on 2020-10-13
What are you using to virtualise? VMWare? Virtualbox? QEmu?

---

