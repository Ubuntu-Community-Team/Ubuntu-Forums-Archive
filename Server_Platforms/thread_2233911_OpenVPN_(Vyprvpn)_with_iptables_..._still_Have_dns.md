---
title: "OpenVPN (Vyprvpn) with iptables ... still Have dns issues"
date: 2014-07-11
forum: Server Platforms
---

### Post by zizounet on 2014-07-11
Hi Guy (*and Girls ;-)*)


i'll try to do this from several weeks but doesn't find a way so maybe someone can help me ?
I have an VyprVPN account and a linux server so i try to send only some traffic throw my VPN
with trafic rules base on group ID. And i not want the default gateway the vpn one.
i fallow this tutorial : [http://blog.dantesk.net/post/2010/04/23/Routage-d-une-application-sp%C3%A9cifique-a-travers-un-r%C3%A9seau-VPN](http://blog.dantesk.net/post/2010/04/23/Routage-d-une-application-sp%C3%A9cifique-a-travers-un-r%C3%A9seau-VPN)


[COLOR=#008000]**TRY WITH GOOGLE IP ADRESSE**[/COLOR]
 **traceroute 173.194.70.94**
     traceroute to 173.194.70.94  (173.194.70.94), 30 hops max, 60 byte packets
       1  88-191-190-1.poneytelecom.eu (88.191.190.1)  0.627 ms  0.680 ms  0.741 ms   [COLOR=#0000FF]<-- this is my default route[/COLOR]
       2  195.154.1.72 (195.154.1.72)  0.952 ms  1.259 ms  1.299 ms
       .... snip result ok ....
 **sudo -g vpn traceroute 173.194.70.94**     [COLOR=#0000FF]*   <-- if i use the group vpn (id 1002) it must be use the vpn gateway *[/COLOR]
      traceroute to 173.194.70.94 (173.194.70.94), 30 hops max, 60 byte packets
         1  10.25.0.1 (10.25.0.1)  13.062 ms  13.068 ms  13.059 ms  [COLOR=#0000FF]<-- this is my vpn route[/COLOR]
         2  192.168.32.1 (192.168.32.1)  13.051 ms  13.272 ms  13.224 ms
         .... snip result ok ....


This is cool by this way i can chose witch application send traffic throw my VPN ! but ...


[COLOR=#FF0000]**TRY WITH GOOGLE DNS NAME** [/COLOR]
 **traceroute [http://www.google.fr](http://www.google.fr)**
     traceroute to [http://www.google.fr](http://www.google.fr)  (173.194.70.94), 30 hops max, 60 byte packets
       1  88-191-190-1.poneytelecom.eu (88.191.190.1)  0.627 ms  0.680 ms  0.741 ms   [COLOR=#0000FF]<-- this is my default route[/COLOR]
       2  195.154.1.72 (195.154.1.72)  0.952 ms  1.259 ms  1.299 ms
       .... snip result ok ....
 
**sudo -g vpn traceroute [http://www.google.fr](http://www.google.fr)**
[http://www.google.fr:](http://www.google.fr:) Name or service not known [COLOR=#0000FF]<-- Oups problem ![/COLOR]
Cannot handle "host" cmdline arg `[www.google.fr]("http://www.google.fr")' on position 1 (argc 1)


So this is a DNS problem but i cant find a way to solve this




My Interfaces are UP :


> em1       Link encap:Ethernet  HWaddr d4:ae:52:c9:31:3b
          inet addr:62.210.208.38  Bcast:62.210.208.255  Mask:255.255.255.0
          inet6 addr: fe80::d6ae:52ff:fec9:313b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:902040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:946400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:88101497 (88.1 MB)  TX bytes:116427614 (116.4 MB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.25.0.115  P-t-P:10.25.0.115  Mask:255.255.0.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)





That's my config : 


**\etc\openvpn\vpn.conf**
```

client
dev tun
proto udp
remote de1.vpn.giganews.com 1194
resolv-retry infinite
nobind
route-nopull                  #<-- this permit to not change the default gateway
persist-key
persist-tun
persist-remote-ip
ca /etc/openvpn/ca.vyprvpn.com.crt
tls-remote de1.vpn.giganews.com
auth-user-pass /etc/openvpn/vyprvpn.pas
comp-lzo
verb 3
script-security 2
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf

```


This script handle start stop and routes


**\etc\openvpn\update-resolv-conf**
```

[ -x /sbin/resolvconf ] || exit 0
[ "$script_type" ] || exit 0
[ "$dev" ] || exit 0


split_into_parts()
{
        part1="$1"
        part2="$2"
        part3="$3"
}


case "$script_type" in
  up)


        TUNDEV=$1
        TUNIP=$4
        VPNNET="10.25.0.0/16"
        VPNGW="10.25.0.1"
        EXTIF=em1
        VPNNAME=1002
        MARK=100 
        echo "- Flushing iptables"
        iptables -t mangle -D OUTPUT -o $EXTIF -m owner --uid-owner $VPNNAME -j MARK --set-mark $MARK
        iptables -t nat -D POSTROUTING -m mark --mark $MARK -j MASQUERADE
        iptables -t nat -D POSTROUTING -m mark --mark $MARK -j SNAT --to-source $TUNIP
        echo "- Flushing iproutes"
        ip route flush table $VPNNAME
        ip rule del fwmark $MARK
        echo "- Flushing rp_filter"
        for f in all $TUNDEV
        do echo 1 > /proc/sys/net/ipv4/conf/$f/rp_filter ; done
        echo "+ adding iptables"
        iptables -t mangle -A OUTPUT -o $EXTIF -m owner --gid-owner $VPNNAME -j MARK --set-mark $MARK
        iptables -t nat -A POSTROUTING -m mark --mark $MARK -j MASQUERADE
        iptables -t nat -A POSTROUTING -m mark --mark $MARK -j SNAT --to-source $TUNIP
        echo "+ adding iproutes"
        echo " + net ${NET} on main table"
        ip route add $VPNNET dev $TUNDEV proto kernel scope link src $TUNIP
        echo " + net ${NET} on ${VPNNAME} table"
        ip route add $VPNNET dev $TUNDEV proto kernel scope link src $TUNIP table ${VPNNAME}
        echo " + gw"
        ip route add default via $VPNGW dev $TUNDEV table ${VPNNAME}
        ip rule add fwmark $MARK table ${VPNNAME}
        ip route flush cache table ${VPNNAME}
        ip route flush cache
        echo "+ adding rp_filter" # ca c'est la commande magique
        for f in all $TUNDEV
        do echo 0 > /proc/sys/net/ipv4/conf/$f/rp_filter ; done
        NMSRVRS=""
        SRCHS=""
        for optionvarname in ${!foreign_option_*} ; do
                option="${!optionvarname}"
                echo "$option"
                split_into_parts $option
                if [ "$part1" = "dhcp-option" ] ; then
                        if [ "$part2" = "DNS" ] ; then
                                NMSRVRS="${NMSRVRS:+$NMSRVRS }$part3"
                        elif [ "$part2" = "DOMAIN" ] ; then
                                SRCHS="${SRCHS:+$SRCHS }$part3"
                        fi
                fi
        done
        R=""
        [ "$SRCHS" ] && R="search $SRCHS"
        for NS in $NMSRVRS ; do
                R="${R}nameserver $NS"
        done
        echo -n "$R" | /sbin/resolvconf -a "${dev}.openvpn"
        ;;
  down)
        TUNDEV=$1
        TUNIP=$4
        VPNNET="10.25.0.0/16"
        VPNGW="10.25.0.1"
        EXTIF=em1
        VPNNAME=1002
        MARK=100 
        echo "- Flushing iptables"
        iptables -t mangle -D OUTPUT -o $EXTIF -m owner --gid-owner $VPNNAME -j MARK --set-mark $MARK
        iptables -t nat -D POSTROUTING -m mark --mark $MARK -j MASQUERADE
        iptables -t nat -D POSTROUTING -m mark --mark $MARK -j SNAT --to-source $TUNIP
        echo "- Flushing iproutes"
        ip route flush table $VPNNAME
        ip rule del fwmark $MARK
        echo "- Flushing rp_filter"
        for f in all $TUNDEV
        do echo 1 > /proc/sys/net/ipv4/conf/$f/rp_filter ; done
        /sbin/resolvconf -d "${dev}.openvpn"
        ;;
esac

```

---

