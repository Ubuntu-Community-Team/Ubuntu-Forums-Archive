---
title: "Blocking incomming ports to outside world only on firewall/gateway router box"
date: 2009-06-09
forum: Server Platforms
---

### Post by verbose mustafa on 2009-06-09
I am currently running Ubuntu Server 8.04. My machine is configured as a firewall/gateway router. I am running webmin as well to configure it. I also have a couple  services for computers on the local network I would like to block from the outside world. Currently it is setup where Eth0 is connected to the internet and Eth1 is connected to my local network.

My question is in setting up the firewall, I have been trying to block some ports to the outside world, but keep them open on the local network. So far I have not been able to configure this in Webmin. I have made sure the rules are setup in the right order.

Is is possible to configure this functionality through Webmin?

Thanks for taking the time to read this.

---

### Post by HermanAB on 2009-06-09
Howdy,

Well, in so far as Webmin having a console function, yes you can do anything...

You probably need a command like this:
iptables -I INPUT -i eth0 -p tcp --dport 1234 -j DROP

---

### Post by LepeKaname on 2009-06-09
I agree with HermanAB, its very easy doing so by console:

```
sudo ufw allow from 192.168.0.0/24 to any port 22
```

This will allow anyone inside your local network to the port 22 and it will not be possible to access it from outside.

That's it.

Check this page, in case you need more info:
[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by verbose mustafa on 2009-06-10
Thanks for your help! I've been dreading learning IPTables but I've needed to master the command line for everything else thats good in life :mrgreen:.

Cheers!

---

### Post by verbose mustafa on 2009-06-10
Herman,

That got me pointed in the right direction. Works like a charm.

thanks,

phil

---

