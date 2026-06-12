---
title: "Please Help about dynamic ip with IPTABLES"
date: 2012-04-26
forum: Server Platforms
---

### Post by iyas120 on 2012-04-26
I have setup a gateway server  with ubuntu 10.04 and using this to port forward to a machine behind the wall

$sudo iptables -t nat -A PREROUTING -p tcp --dport 3389 -d 118.99.93.64 -j DNAT --to-destination 192.168.0.4:3389

$sudo iptables -I INPUT -p tcp -d 118.99.93.64 --dport 3389 -j DROP

$sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

The problem is my isp changing my ip public/dynamic ip.

Can some one modify those iptables so i don't have to change the ip every time it's change.

Any help is huge appreciated from me

Sorry for my bad english.

---

### Post by SeijiSensei on 2012-04-26
Replace "-d 118.99.93.64" with "-i eth0" or "-i eth1" depending on which interface faces the Internet.

---

### Post by iyas120 on 2012-04-26
Thanks for your suggestion but some how when i change to :

$sudo iptables -t nat -A PREROUTING -p tcp --dport 3389 -i eth0 -j DNAT --to-destination 192.168.0.4:3389

$sudo iptables -I INPUT -p tcp -i eth0 --dport 3389 -j DROP

$sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

Those configuration effect is not the same with the previous one.. 
Please some one have an explanation

---

### Post by darkod on 2012-04-27
One reason might be if you have a mix with previous rules. You might wanna flush the iptables both the filter and nat chains.
sudo iptables -F
sudo iptables -t nat -F

Just make sure you don't lock yourself out, depending what your setup is. :)

Otherwise, using -i eth0 is the correct way to go because it is IP independent.

The difference with -d <IP> is that that rule catches the traffic directed specifically at that IP. The -i eth0 catches everything coming in on eth0.

Double check how the traffic gets to that machine, if everything is working fine.

EDIT PS: Since we are talking about forwarded traffic, you actually need to work with the FORWARD chain, not INPUT. If the forward policy is DROP, your PREROUTING won't work. But I guess it's set to ACCEPT. You might wanna set that to DROP  and allow only traffic you want to allow. The INPUT rule has no effect on the forwarding, it is an accept rule for the gateway machine.

---

### Post by a2j on 2012-04-27
```
EXTIP="`/sbin/ifconfig eth0 | grep 'inet addr' | awk '{print $2}' | sed -e 's/.*://'`"
INTIF="eth1"
EXTIF="eth0"
```

Put this in your iptables script, change to fit your needs. Works for me.

---

### Post by SeijiSensei on 2012-04-27
That works as long as the ISP's DHCP server doesn't change his address between reboots.  If the ISP uses short leases, like a few hours duration, he'd need to run the script out of cron on a more frequent basis than when the address changes.

If you look at the ruleset with "sudo iptables -L -nv" you'll see that rules that specify only an interface will have 0.0.0.0 as the corresponding IP address.  That's the default address iptables uses in this situation; the 0.0.0.0 address matches any address.

---

