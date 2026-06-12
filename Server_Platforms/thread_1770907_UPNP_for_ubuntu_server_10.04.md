---
title: "UPNP for ubuntu server 10.04"
date: 2011-05-29
forum: Server Platforms
---

### Post by elico on 2011-05-29
i am using ubuntu as a router and got some problems with port forwarding...
i wanted to use UPNP but the linux-igd from UBUNTU repository didnt worked.
so i had to install:
[http://http.us.debian.org/debian/pool/main/libu/libupnp4/libupnp4_1.8.0~svn20100507-1_amd64.deb]("http://http.us.debian.org/debian/pool/main/libu/libupnp4/libupnp4_1.8.0%7Esvn20100507-1_amd64.deb")
and then
[http://ftp.us.debian.org/debian/pool/main/l/linux-igd/linux-igd_1.0+cvs20070630-3_amd64.deb](http://ftp.us.debian.org/debian/pool/main/l/linux-igd/linux-igd_1.0+cvs20070630-3_amd64.deb)

in order to make it work.
if you want to know more you can try read a bit in:
[http://www.gentoo-wiki.info/HOWTO_Setup_UPnP_with_IPTables](http://www.gentoo-wiki.info/HOWTO_Setup_UPnP_with_IPTables)

the main thing is to config the file:
/etc/default/linux-igd

and to set the external interface...
internatl interface..
to "ALLOW_MULTICAST" or not...
and in the file:
/etc/upnpd.conf
make sure that 
```
create_forward_rules = yes
```is present
change the 
```
forward_chain_name = UPNP_FORWARD
```and 
```
prerouting_chain_name = UPNP_PREROUTING
```change the 
```
upnp_log_filename = "";
```to a valid one like"
```
upnp_log_filename = "/var/log/upnp.log";
```if your internal interface is eth1 these iptables rules should be added.
```

iptables -t filter -I INPUT 1 -i eth1 -d 240.0.0.0/240.0.0.0 -j ACCEPT
iptables -t filter -I INPUT 2 -i eth1 -p tcp --dport 49152 -j ACCEPT
iptables -t filter -I INPUT 3 -i eth1 -p udp --dport 1900 -j ACCEPT
iptables -t filter -I INPUT 4 -i eth1 -p tcp -m tcp --dport 2869 -j ACCEPT

iptables -t filter -N UPNP_FORWARD
iptables -t filter -I FORWARD 1 -j UPNP_FORWARD

iptables -t nat -N UPNP_PREROUTING
iptables -t nat -I PREROUTING 1 -j UPNP_PREROUTING
```

---

