---
title: "dhcp server guide"
date: 2008-09-25
forum: Server Platforms
---

### Post by fouadk on 2008-09-25
hi everyone...

i am trying for now to setup a dhcp server...i am searching the net and all i get is plenty of mini how-to...what i am searching for is a complete guide to setup a dhcp server on a debian like distribution(ubuntu)....

dhcpd contains a lot of directives and i need to know what each one does in order to decide if i need to add to my conf file or not...

does anyone know about any complete yet easy guide to setup dhcp server under ubuntu ???

thanks in advance

---

### Post by jamesrfla on 2008-09-25
If you are a beginner try webmin. This is a web based administration utility that should allow you to configure dhcp. [http://sourceforge.net/project/downloading.php?groupname=webadmin&filename=webmin_1.430_all.deb&use_mirror=voxel](http://sourceforge.net/project/downloading.php?groupname=webadmin&filename=webmin_1.430_all.deb&use_mirror=voxel)

---

### Post by kpatz on 2008-09-25
I have mine set up with a conf file similar to this.

```


# These are optional and cause your DHCP server to hand out
# DNS info to your clients.
option domain-name "YOUR_LOCAL_DOMAIN_HERE";
option domain-name-servers YOUR_DNS_SERVER_IP_ADDRESSES_HERE;

option subnet-mask 255.255.255.0;
default-lease-time 86400;   # 1 day lease (86400 seconds)
max-lease-time 172800;      # should be twice the default

# This assumes your network is 192.168.0.0/24 and doles out IPs
# between 192.168.0.100 and 192.168.0.200
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.200;
#  option broadcast-address 192.168.0.255;  #broadcast IP
  option routers 192.168.0.1;   # your gateway IP
}

```

---

### Post by iansane on 2008-09-28
I need some help here too please.

Just to make sure, is that gateway ip the ip of the router connected to the modem where the internet is coming from?

I'm trying to set up dhcp to give out IP's on one nic with a different subnet, and get internet from another nic, is why I'm asking.

Will the above work or do I need to set up dns with look up zone and static route too?

With that set up, machines on the subnet can ping the bridge and can ping the host nic but can't ping the router. The host nic is wireless by the way.

---

### Post by lykwydchykyn on 2008-09-28
> **iansane said:**
> I need some help here too please.

Just to make sure, is that gateway ip the ip of the router connected to the modem where the internet is coming from?

I'm trying to set up dhcp to give out IP's on one nic with a different subnet, and get internet from another nic, is why I'm asking.

Will the above work or do I need to set up dns with look up zone and static route too?

With that set up, machines on the subnet can ping the bridge and can ping the host nic but can't ping the router. The host nic is wireless by the way.

Basically what you're doing is setting up your server to be the router, it sounds like.  In that situation, what you need to do is this:
 - Tell the clients that the server is their gateway (using the dhcp server)
 - Configure the server to forward traffic, using IP tables 
 - You don't need to set up DNS, just tell the clients to use the same DNS the server is using.

---

### Post by iansane on 2008-09-29
So would that be the same as setting up static routes? I've done that with windows before (long time ago), and I can use webmin to do it in ubuntu through the dhcp server settings.

Can you help me with this some?

Here's what I have.

internet router: 10.0.0.101
host IP:         10.0.0.104
netmask:         255.255.255.0

eth0:            0.0.0.0
bridge to eth0:  10.0.1.1
dhcp subnet:     10.0.1.0
netmask:         255.255.255.224
IP range:        10.0.1.2 - 10.0.1.30

Tried setting up static route:

interface  network     netmask        gateway
br0        10.0.1.0    255.255.255.0  10.0.0.104

That's how it is in webmin.

Maybey an explaination of setting it up manually will help.

I need to route the bridge (br0 10.0.1.1) to the dhcp server (10.0.0.104) right?

Then 10.0.0.104 should forward to the router on it's own?

Thanks a lot for any help in understanding how this works.

---

### Post by iansane on 2008-09-29
I should clarify in my case, there is only one physical machine in this scenario.

I found that bridging doesn't work with wireless for virtual box host interfacing. Tried several work arounds that aren't working, including NATing the wireless to eth0. So, I'm trying to use dhcp on the host which is working for the subnet of vm's. It took me a while to figure out but now it's assigning IP's to the vm's.

They can ping each other and can ping the hosts wireless nic.

They just can't get past the wireless to get internet access. Can't ping the wireless router. I think it's as simple as setting up a static route like I would in a physical environment for subnets but I'm not sure what I'm doing.

dhcp, eth0, wlan0, and the bridge seem to be all working fine. Just no internet to the subnet.

---

### Post by koenn on 2008-09-29
> **fouadk said:**
> hi everyone...

i am trying for now to setup a dhcp server...i am searching the net and all i get is plenty of mini how-to...what i am searching for is a complete guide to setup a dhcp server on a debian like distribution(ubuntu)....

dhcpd contains a lot of directives and i need to know what each one does in order to decide if i need to add to my conf file or not...

does anyone know about any complete yet easy guide to setup dhcp server under ubuntu ???

thanks in advance
The reason you only find mini-howtos is that there isn't really that much to say about the setup itself. You edit dhcpd.conf and restart the daemon, and that's it.
As for what to put in your dhcpd.conf, that depends on what your network looks like and which network properties of your hosts you want configured through dhcp (eg default gateway, hostname, dns servers, ...). These are "options". 
Here's a list : [http://www.networksorcery.com/enp/protocol/bootp/options.htm](http://www.networksorcery.com/enp/protocol/bootp/options.htm)

---

### Post by thefekete on 2008-09-29
Another vote for Webmin...

I used this tutorial with great success...

[http://coroketon.wordpress.com/2008/01/20/setup-your-computer-to-be-a-router/](http://coroketon.wordpress.com/2008/01/20/setup-your-computer-to-be-a-router/)

It covers webmin installation, IP Masquerading (NAT), and DHCP.

If you are still having trouble, I also wrote a step by step guide for Ubuntu Server 8.04 for work. I need to reformat it and post it (its on my company's intranet right now), so let me know if the tutorial doesn't make sense, or is not complete enough...


I also found this ubuntu howto on the subject. I didn't read the whole thing so YMMV, but here it is:
[http://ubuntuforums.org/showthread.php?t=926001](http://ubuntuforums.org/showthread.php?t=926001)

And here's a hardcore command line method (again, didn't really read it, but looks useful):
[http://www.stanford.edu/~fenn/linux/](http://www.stanford.edu/~fenn/linux/)


-dan

---

### Post by iansane on 2008-09-30
fouadk,

I hope you got yours set up and running.

I just wanted to thank everyone who posted links and helped explain things.

I didn't understand that iptables is more than just a wall to block or allow. I thought if it allows by default then why aren't packets going through? Thanks to thfekete and the wordpress link about webmin I was able to set up the right rules and now my host is a router/dhcp server for my virtual subnet of vm's and I have internet!!!:-) All I had to do to finish it off in windows vm was set the dns server as my physical router which will be fun in my ubuntu vm's with terminal.

This will be very helpful when I get to do it physically or virtually in a office inviroment. And I think I could actually do it all without webmin if I had to.

Thanks a lot you guys! I so happy, I do the dance of joy!!

---

