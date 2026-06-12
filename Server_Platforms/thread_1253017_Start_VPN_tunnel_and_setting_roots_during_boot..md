---
title: "Start VPN tunnel and setting roots during boot."
date: 2009-08-29
forum: Server Platforms
---

### Post by pwpeterson on 2009-08-29
Hello, All

I am trying to  get my vpn tunnel(s) started  and route(s) set on boot,

Here is my /etc/network/interfaces:
 
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 74.xx.xx.xx
        netmask 255.255.255.0
        network 74.xx.xx.xx
        broadcast 74.xx.xx.255
        gateway 74.xx.xx.xx
        # dns-* options are implemented by the resolvconf package, if
installed
        dns-nameservers 74.112.xx.1
        dns-search jadase.com
        pre-up iptables-restore < /etc/network/iptables.rules

auto eth0:1
iface eth0:1 inet static
        address 74.xx.xx.xx
        netmask 255.255.255.0
        network 74.xx.xx.xx
        broadcast 74.xx.xx.255
        gateway 74.xx.xx.1
        # dns-* options are implemented by the resolvconf package, if
installed
        #dns-nameservers 74.xx.xx.x
        #dns-search jadase.com
        pre-up iptables-restore < /etc/network/iptables.rules

# I got the followong idea here: [http://pptpclient.sourceforge.net/howto-ubuntu.phtml ]("http://pptpclient.sourceforge.net/howto-ubuntu.phtml")
# however it is meant for a debian system. It does work to start the tunnel at boot

auto tnl_polfus
iface tnl_polfus inet ppp
                provider vpn_polfus
                # If I include the following line neither the tunnel will start nor the route get set.
                post-up route add -net 10.81.104.0 netmask 255.255.255.0 dev ppp0

Any idea what I am doing wrong??

 ========================================================================

Another Idea I found was to create script '/etc/init.d/vpn' that will run during boot:

Here's its content:

#!/bin/sh
#
echo

show_vpn(){
        ps aux | grep ppp  | grep -v grep
}


vpn_start(){
        echo "starting vpn tunnels and setting routes.."
       pon vpn_polfus
       route add -net 10.81.xx.xx netmask 255.255.255.0 dev ppp0
       echo
       show_vpn
       route
}

vpn_stop(){
        echo "stopping vpn tunnels.."
        poff vpn_polfus
        show_vpn
}


case $1 in
        start)
                vpn_start
        ;;

        stop)
                vpn_stop
        ;;

        restart)
                vpn_stop
                vpn_start
        ;;

        status)
                show_vpn
        ;;

        *)
                echo "Usage: /etc/init.d/vpn
{start|stop|restart|status}"
        ;;
esac

This does start vpn_polfus but does not set the route.

Would some have something that will start the vpn tunnel AND set the route during boot?

Thx 

Paul Peterson

---

### Post by pwpeterson on 2009-08-29
Correction:

auto tnl_polfus
iface tnl_polfus inet ppp
                       provider vpn_polfus

Does not start the vpn tunnel at boot.

I can get ist started with the script but can the route to  set.

pwp

---

