---
title: "Network config problem"
date: 2007-12-29
forum: Server Platforms
---

### Post by dim_hyder on 2007-12-29
I've have just completed a clean installed of ubuntu server 7.10

The problem I'm having is this. I've configured the network settings as I require them in the /etc/networks/interfaces file.

restarted networking

When I try and ping another host via IP address I get destination unreachable. The host does not have a firewall and replies to ping requested from other hosts.

Here is the strange bit. If I ping the ubuntu server from the host I was trying to ping the from ubuntu server it replies and straight after this the ubuntu server can ping the original host.

I hope I'm explaing this well.

The server has dual NICs only eth0 is enabled and connected.

Anyone any ideas?

Cheers,

Dim Hyder

---

### Post by andol on 2007-12-29
Are they on the same subnet? Settings for netmask and default gateway?

---

### Post by dim_hyder on 2007-12-29
yes - on the same subnet.

netmask 255.255.255.0
they're on the same subnet so the default gateway shouldn't matter
but it's192.168.2.254.

Cheers,

Dim Hyder

---

### Post by andol on 2007-12-29
Well, in case you don't come up with anything else I guess you could always try to temporary physically remove the second NIC in the server.

---

### Post by dim_hyder on 2007-12-29
The server is an IBM xseries 3250 with 2 onboard NICs.

Is IPv6 on by default on a ubuntu server 7.10 install?

Is there a way I can disable to eth1 through the interfaces file?

Cheers,

Dim Hyder

---

### Post by koenn on 2007-12-29
hm, could be something with the 2 nics and the server sending on the wrong one first, or so. 

do (and post output of)
```
ifconfig
```
to see which NIC's are configured, and how. 

you can disable one with
```
ifconfig eth1 down    ## replace eth1 with appropriate device 
# or
ifdown eth1 
```

you can disable a NIC in 'interfaces' by commenting it (put # in front of all relevant lines), 
```
#auto eth0
#iface eth0 inet static
#       address 192.168.2.20
#  ...
#
```

do 
```
/etc/init.d/networking restart
```
to make it effective

---

### Post by dim_hyder on 2007-12-29
thanks koenn.

The server is at work so can't give the outputs at present.

ifconfig only displays info from eth0 and lo

the interfaces file does not contain any entries relating to eth1.

---

