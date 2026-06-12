---
title: "dhcp server on boot"
date: 2014-05-07
forum: Server Platforms
---

### Post by jcarson99 on 2014-05-07
Hi,

I installed ubuntu server 14.04 with maas and I am having a problem with the isc-dhcp-server. 

When my system boots up the dhcp instance of maas starts but I have to login and run "sudo service isc-dhcp-server start" so my local network can connect and get an ip address.

Anyone know how I can get isc-dhcp-server to start on boot in addition to the maas instance?

Thanks

---

### Post by stmiller on 2014-05-07
Edit post: 

Check out this [http://ubuntuforums.org/showthread.php?t=2186287&p=12841552#post12841552](http://ubuntuforums.org/showthread.php?t=2186287&p=12841552#post12841552)

Sounds similar?

---

### Post by jcarson99 on 2014-05-08
Thanks for the link. I tried modifying /etc/init/isc-dhcp-server.conf but had no luck.

I'm going to do more reading on maas to find out if I can use the maas instance of dhcp to provide ip's to my network.

If all else fails I'll reinstall without maas. I don't really need it, just wanted to check it out. A dhcp server that will start automatically is more important.

---

### Post by pqwoerituytrueiwoq on 2014-05-08
i made a script that runs via /etc/rc.local that makes it start with a delay, by delay i mean after a ip address has been assigned to eth0 and the virtual nic (eth0.1) has been created
you can probably use [FONT=courier new]sh -c 'sleep 30;service isc-dhcp-server start' &[/FONT] and it work, but this is what i did
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo 1 > /proc/sys/net/ipv4/ip_forward
while [ 0`pidof NetworkManager` -eq 0 ]; do
    sleep 1
done
while [ "`ifconfig eth1 | grep 'inet addr:'`" = "" ]; do
    sleep 2
done
while [ "`ifconfig eth1:1 | grep 'inet addr:'`" = "" ]; do
    sleep 2
    ifconfig eth1:1 10.0.0.1 netmask 255.255.0.0
done
#iptables -t nat -A PREROUTING -o eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.0.0.75:80
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
iptables -P FORWARD ACCEPT
service isc-dhcp-server start
#ifconfig eth1:2 192.168.100.2 netmask 255.255.255.0
#notify-send --icon=info "Other computers can now use the internet"
exit 0
```

---

### Post by jcarson99 on 2014-05-08
I was reading through your script and decided to try just "service isc-dhcp-server start". I rebooted and everything seems to be working fine. Thanks

---

