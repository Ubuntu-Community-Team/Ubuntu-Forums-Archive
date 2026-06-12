---
title: "OpenVPN routing"
date: 2010-02-04
forum: Server Platforms
---

### Post by magikid on 2010-02-04
Ok, I've looked high and low to solve this.  My problem is that I'm migrating from my old server (oldie) to a new one (theprofessor).

I have installed the same version of OpenVPN on the new one and I have copied the config file from the old to the new.  On theprofessor, I can connect to the VPN and access resources on it and surf the web through it from my laptop.  On theprofessor, I can connect to the VPN and access resources on it but I can't surf the web through it.

My first thought was maybe a firewall issue so on my laptop and theprofessor I ran ```
sudo iptables -F
``` and I also made sure that my laptop was in the DMZ of my router.  It didn't make any difference.  I started looking through the log on theprofessor and it turns out that it's being flooded with this:
```
Thu Feb  4 23:10:57 2010 philipjfry/[ext IP addr]:57064 MULTI: bad source address from client [192.168.1.101], packet dropped
```

Note: philipjfry is my laptop and 192.168.1.101 is the IP assigned to me by my router.

Can anyone help me figure out why it's dropping all my packets?

Here's the server config:

```
    dev tun
    proto udp
    port 1194

    ca /etc/openvpn/easy-rsa/2.0/keys/ca.crt
    cert /etc/openvpn/easy-rsa/2.0/keys/theprofessor.crt
    key /etc/openvpn/easy-rsa/2.0/keys/theprofessor.key
    dh /etc/openvpn/easy-rsa/2.0/keys/dh2048.pem

    user nobody
    group nogroup
    server 10.8.0.0 255.255.255.0

    persist-key
    persist-tun

    status openvpn-status.log
    verb 3
    client-to-client

    push "redirect-gateway def1"

    log-append /var/log/openvpn
    comp-lzo 
    #management localhost 7505


    push "dhcp-option DNS 208.67.222.222"
    push "dhcp-option DNS 208.67.220.220"

    ping 10
    ping-restart 120 

```

There is no client config.  I'm connecting with the NetworkManager.

---

### Post by amauk on 2010-02-04
I think you may need to enable IP forwarding on the server
(it's disabled by default. I did think it was automatically enabled once you installed anything like a VPN server, but maybe not)

Check the output of this
```
cat /proc/sys/net/ipv4/ip_forward
```

0 = disabled
1 = enabled

If it's disabled,
then edit /etc/sysctl.conf
and uncomment the line
net.ipv4.ip_forward=1

reboot the server, and hopefully IP forwarding will work

---

### Post by magikid on 2010-02-05
I made sure that it was enabled and rebooted the server.  It didn't seem to change anything.  I'm still seeing my server log flooded with: 
```
Fri Feb  5 18:10:28 2010 philipjfry/[ext ip]:41400 MULTI: bad source address from client [192.168.1.101], packet dropped

```

---

### Post by amauk on 2010-02-05
quick google brought this up
[http://openvpn.net/archive/openvpn-users/2005-01/msg00091.html](http://openvpn.net/archive/openvpn-users/2005-01/msg00091.html)

---

### Post by koenn on 2010-02-05
can't say what is wrong with this, cause I don't really onderstand  what you mean with

 - "On theprofessor, I can connect to the VPN and access resources on it and surf the web through it from my laptop." 


 - "On the professor, I can connect to the VPN and access resources on it but I can't surf the web through it." 

It's not clear what you're trying to accomplish with your VPN.
Maybe you need to elaborate a bit.


Nonetheless, I noticed a couple of things that are peculiar

1/ you have "client-to-client" in your conf - that means you just want a tunnel between two hosts, right ? So I don't understand why you're asking about 'routing'

2/ you hace CA, certs and keys in your server conf - doesn't that also reqsuire you have a cert or a key on your client ? But you say "there's no client setup"

3/ "philipjfry/[**ext IP addr**]:57064 MULTI: bad source address from client [192.168.1.101], packet dropped"
This suggests philipjfry connects to theprofessor through the internet (via A NAT router, giving it your router's external address, I assume ?) but the packets it sends have source address 192.168.1.101. I can think of two reasons your system complains aboput this
1- this looks like spoofing, and theprofessor refuses to handle it 
2- theprofessor doesn't know how to route towards that address - in that case, the tunnel interface might have not come up, or there's a (default ?) route missing.

EDIT amauk's post seems to confirm this, so you may want to look at your routing table.

---

### Post by magikid on 2010-02-05
So, it turns out all of my problems were caused by the fact that my server is a OpenVZ instance and therefore ```
iptables -t nat -A POSTROUTING -o $IFACE -j MASQUERADE
``` was failing and not allowing the packets to be properly routed.  I solved the problem by running this instead:
```
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o venet0 -j SNAT --to [ext ip of server]
```

A few other clarifications:
```
1/ you have "client-to-client" in your conf
```
This option just allows clients to see and connect to each other.

```
2/ you hace CA, certs and keys in your server conf
```
I just meant that I was using NetworkManager on my client to handle the connection and hadn't specifically installed OpenVPN on it.

Thanks for all of your help with this.

---

