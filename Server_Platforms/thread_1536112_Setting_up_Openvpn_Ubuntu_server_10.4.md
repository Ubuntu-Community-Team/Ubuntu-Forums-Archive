---
title: "Setting up Openvpn Ubuntu server 10.4"
date: 2010-07-21
forum: Server Platforms
---

### Post by duceduc on 2010-07-21
I am following this [guide]("http://library.linode.com/networking/vpn-services/openvpn-ubuntu-10.04-lucid) on setting up an Openvpn but having a little issue with permission denied. 

I am at this step 'Initialize the Public Key Infrastructure (PKI)'
```
cd /etc/openvpn/easy-rsa/2.0/
. /etc/openvpn/easy-rsa/2.0/vars
. /etc/openvpn/easy-rsa/2.0/clean-all
. /etc/openvpn/easy-rsa/2.0/build-ca
``` 
I am getting a permission denied after this input. 
```
. /etc/openvpn/easy-rsa/2.0/clean-all
```
Need some assistance. Thank you.

---

### Post by jbrown96 on 2010-07-22
Prefix all commands with "sudo."

---

### Post by duceduc on 2010-07-22
Thank you for your reply.
I have tried this command. 
```
sudo ./clean-all
```
I get this message.
```
Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.
```
I have edited the /vars file per the tutorial.

Edited.
I found my solution. I needed to be in root
```
sudo su
```

---

### Post by noway2 on 2010-07-22
I didn't go through the tutorial in detail, but by the sound of it, something is messed up in your vars creation process.  It could be as simple as needing to sudo the creation of your a permission location problem.

Being an Ubuntu forum, here are a couple of links to installing openVPN on Ubuntu,   I know from personal experience that they work.

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
[http://ubuntuforums.org/showthread.php?t=1021592](http://ubuntuforums.org/showthread.php?t=1021592)

---

### Post by duceduc on 2010-07-23
I have finished setting up my openvpn using the original [guide]("http://library.linode.com/networking/vpn-services/openvpn-ubuntu-10.04-lucid") in the first post. I did ALL the steps. 
Upon testing it with a client computer not connected to the same network, I am getting a 'cannot connect to the server' message when browsing the net. Looking at the log files, it seems I am almost fully connected to my server. I have forward my 1194 ports on my router as well. I don't know where else to look for my mistakes. I have enclosed my client log, server.conf, and client.conf in a [zip file]("http://ducsu.com/stuff/log.zip") for someone to look it. Thank you.

---

### Post by xls on 2010-07-23
could you post your client config and server config?  (use a fake ip/port/file names).  is this a bridged or routed vpn?

n/m just saw the zip now... thanks for not making it easy:

server.conf
```

local 192.168.1.135
port 1194
proto udp
dev tap
dev tun
ca /etc/openvpn/easy-rsa/2.0/keys/ca.crt
cert /etc/openvpn/easy-rsa/2.0/keys/server.crt
key /etc/openvpn/easy-rsa/2.0/keys/server.key  # This file should be kept secret
dh /etc/openvpn/easy-rsa/2.0/keys/dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1"
push "dhcp-option DNS 10.8.0.1"
keepalive 10 120
tls-auth ta.key 0 # This file is secret
comp-lzo
persist-key
persist-tun
status openvpn-status.log
verb 3
```

first you have two dev entries, not sure if that is OK.  i think you should comment out the "dev tap" line

---

### Post by xls on 2010-07-23
client log says you are connected (Initialization Sequence Completed).  the server log would be more interesting but if your client is connected... it should all be good.

i don't think this is a vpn problem.  maybe firewall?

---

### Post by duceduc on 2010-07-23
> **xls said:**
> client log says you are connected (Initialization Sequence Completed).  the server log would be more interesting but if your client is connected... it should all be good.

i don't think this is a vpn problem.  maybe firewall?

Thanks for your help. I have spent quite a few of hours on this and I hate to quit now since I have made some progress. After searching the net some more, I think I may need to setup an iptables. 

My main purpose on this openvpn is to have my iphone (guzimovpn) connected to my squid/privoxy server via openvpn to browse the net from the iphone. Blocking popup ads.

I have tried setting up this iptables 
```
iptables -t nat -A PREROUTING -i tun0 -p tcp --dport 80 -j REDIRECT --to-port 3128
```
but it is still not working. I may not did it correctly either. I inputed that line in my /etc/rc.local dir and rebooted the server.

I also tried to ping the connection with 10.8.0.6 from the server but I am not getting any response. I believe that was the ip address openvpn assigned to the client computer. 

I did comment out dev tap by the way.

Where is the server log located at?

I don't know if this maybe my problem. In the log, I see the netmask is set to 255.255.255.255. Shouldn't it be 255.255.255.0? I don't know how to set it for the later.
```
Fri Jul 23 19:31:59 2010 /sbin/ifconfig ppp0 10.8.0.6 10.8.0.5 mtu 1500 netmask 255.255.255.255 up
Add a route to 172.24.132.84 with gateway [edited]
add net 172.24.132.84: gateway [edited]
Setting DNS to /Network/Service/7876D6C3-BB6C-4AB5-A762-1F995FEFBE01/DNS (10.8.0.1 172.24.132.84)
Fri Jul 23 19:32:01 2010 /sbin/route add -net 180.2.92.33 126.251.162.221 255.255.255.255
add net 180.2.92.33: gateway [edited]
Fri Jul 23 19:32:01 2010 /sbin/route add -net 0.0.0.0 10.8.0.5 128.0.0.0
add net 0.0.0.0: gateway 10.8.0.5
Fri Jul 23 19:32:01 2010 /sbin/route add -net 128.0.0.0 10.8.0.5 128.0.0.0
add net 128.0.0.0: gateway 10.8.0.5
Fri Jul 23 19:32:01 2010 /sbin/route add -net 10.8.0.1 10.8.0.5 255.255.255.255
add net 10.8.0.1: gateway 10.8.0.5
Fri Jul 23 19:32:02 2010 Initialization Sequence Completed
```

---

### Post by duceduc on 2010-07-25
After a of days of searching around trying to get this Openvpn working, I am 95% there. Since I was able to connect to my Openvpn but I couldn't browse the internet was in fact a firewall issue. I emailed the dev over at Openvpn and he was very helpful in getting me squared away. He uploaded a .sh file with basic firewall settings and instructed me to symlink it to my rcS.d folder.

I am now connected to my server but I get a **access denied** message from my squid server when I browse the net. I am using Guizmovpn on my iphone to connect to my server and it doesn't allow me to authenticate my proxy, hence, the error message.
Any suggestions on how to get my Internet working?

Here is the firewall settings I used.
```
#!/bin/bash

# IPTables executable
IPT=/sbin/iptables

# Interfaces definitions
INTERNAL_IF=eth0
EXTERNAL_IF=eth1
VPN=tun0

case "$1" in
   start)
        # Kernel configuration to authorise forwarding and make this machine as a router
        echo 1 > /proc/sys/net/ipv4/ip_forward
        echo 1 > /proc/sys/net/ipv4/tcp_syncookies
        echo 1 > /proc/sys/net/ipv4/ip_dynaddr
        echo 0 > /proc/sys/net/ipv4/tcp_ecn
        echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
        echo 1 > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses
        for f in /proc/sys/net/ipv4/conf/*/rp_filter; do
                echo 1 > $f
        done
        for f in /proc/sys/net/ipv4/conf/*/accept_redirects; do
                echo 1 > $f
        done
        for f in /proc/sys/net/ipv4/conf/*/send_redirects; do
                echo 1 > $f
        done
        for f in /proc/sys/net/ipv4/conf/*/accept_source_route; do
                echo 1 > $f
        done
        for f in /proc/sys/net/ipv4/conf/*/log_martians; do
                echo 0 > $f
        done

        # Cleaning previous rules
        $IPT -F
        $IPT -t nat -F
        $IPT -t filter -F
        $IPT -t mangle -F
        $IPT -X

        # Default policies
        $IPT -P OUTPUT ACCEPT
        $IPT -P INPUT DROP
        $IPT -P FORWARD DROP

        # Accept everything from local
        $IPT -A INPUT -i lo -j ACCEPT

        # Accept everything from Internal and VPN
        $IPT -A INPUT -i $INTERNAL_IF -j ACCEPT
        $IPT -A INPUT -i $VPN -j ACCEPT

        # Accept return packets
        $IPT -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

        # Route what is coming from inside
        $IPT -A FORWARD -i $INTERNAL_IF -s 192.168.0.0/24 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

        # Autorisation des packets de retour venant de l'exterieur
        $IPT -A FORWARD -i $EXTERNAL_IF -m state --state ESTABLISHED,RELATED -j ACCEPT

        # VPN
        $IPT -A INPUT -i $EXTERNAL_IF -p udp --dport 1194 -j ACCEPT
        $IPT -A FORWARD -i $VPN -j ACCEPT

        # Route port 80 through the proxy
        $IPT -t nat -A PREROUTING -i $VPN -p tcp --dport 80 -j REDIRECT --to-port 3128
        ;;
   stop)
        # Efface les tables
        $IPT -t nat -F
        $IPT -F

        ;;
   restart)
        $0 start
        ;;
   *)
        echo "Usage: $0 {start|stop|restart}"
esac

exit


```

---

