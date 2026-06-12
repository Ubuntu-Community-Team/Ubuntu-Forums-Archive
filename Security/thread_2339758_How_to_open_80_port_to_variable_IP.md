---
title: "How to open 80 port to variable IP"
date: 2016-10-12
forum: Security
---

### Post by kuribo93 on 2016-10-12
Hi Ubuntu team.
I have specify queation.
I use Iptables for security and I open port 80 for static IP. Now I want open port for another IP but that IP changed every 24 hours. If I use that IP today and put in firewall tumorrow that Ip is expired and I must put again and so over and over again.

whether there any software for this.
Thy a lot

---

### Post by SeijiSensei on 2016-10-12
If the address is always within the same subnet, an easy solution to is permit the entire subnet:
```
/sbin/iptables -A INPUT -p tcp -d 10.10.10.0/24 --dport 80 -j ACCEPT
```

If it's not, then you have to run a script to grab the address from the interface once each day.  Suppose it's eth1.  I would use something like this:
```
#!/bin/bash
EXT_INT=eth1
EXT_IP=$(ifconfig $EXT_INT | grep 'inet addr' | awk '{print $2}' | sed 's/addr://g')
/sbin/iptables -I INPUT -i $EXT_INT -p tcp -d $EXT_IP --dport 80 -j ACCEPT
```
That stores the address in the environment variable EXT_IP then adds an iptables rule to the top of the chain (-I) with the new address.  As written, it will not delete the rule for the prior day's address.  You could write the contents of EXT_IP to a file, read that in, then delete the matching rule before adding the new one.

You'll have to run this from cron with the time set to insure it runs after the IP changes.

---

### Post by papibe on 2016-10-12
Hi kuribo93.

The standard for a machine providing services/access is to have a fixed IP. My first suggestion would be to set the machine with a DHCP reservation, or an static IP.

In case that is not possible...

If you have a working local DNS, you can use the LAN hostname of the target machine in your rule, and then simple re run your rules every 24hrs.

You can also set up a broadcasting service like avahi (Zeroconf), so that you can get the IP by using a domain like .local

I hope that helps. Let us know if you need more suggestions on one of those topics.
Regards.

---

### Post by SeijiSensei on 2016-10-13
My guess is that the dynamic IP is coming from an ISP and not under his control.

---

### Post by kevdog on 2016-10-14
If he wants to dynamically control the firewall -- meaning selectively allow access to the server but have the ability to change the firewall properties from the outside, I think a great solution would be to use a port knocker as fwknop.  This particular port knocker can be configured to alter the firewall and change the firewall with the properties you want.  It just isn't a simple port knocker that opens the port for any IP address.

---

