---
title: "can't communicate the 2 guest OS even using vde"
date: 2007-12-04
forum: Virtualisation
---

### Post by herbert tamayo on 2007-12-04
Hi, I'm using qemu+vde+dnsmasq to connect to guest OS -xp and freeBSD- ok, both guest can ping to the gateway ip but they can't ping between them, the procedure I follow is the next:

#vde_switch -hub -tap tap0 -daemon -sock /tmp/vde.ctl
#ifconfig tap0 192.168.30.254 netmask 255.255.255.0
#chmod 755 /tmp/vde.ctl
#echo "1" > /proc/sys/net/ipv4/ip_forward
#iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

vdeqemu -hda xpsp2.cow -m 256 -boot c (ip 192.168.30.12)
vdeqemu -hda fbsd.cow -n 128 -boot c (ip 192.168.30.13)

between 192.168.30.12 and 192.168.30.13 can't do ping, so I need that the guests can communicate, can you give some advice?

thanks

---

