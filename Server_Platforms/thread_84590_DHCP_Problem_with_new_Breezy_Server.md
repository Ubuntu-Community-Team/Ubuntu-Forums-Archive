---
title: "DHCP Problem with new Breezy Server"
date: 2005-10-31
forum: Server Platforms
---

### Post by Kremlin on 2005-10-31
My old Hoary Server crashed and burned due to a power outage, and when I finally recovered files from the burnt husk of the old hard drive, I reinstalled Breezy onto the new hard drive and am trying to get things set up again.

My first snag is with DHCP. I set up the DHCP server and copied over the old configuration (it is not corrupted). I even compared it against the default dhcpd.conf with breezy to make sure there weren't any new options I should be worrying about. Then I tried (with a Windows XP machine) to get a dynamic IP address.

Now, while my server was down, I was using a modem/router as DHCP server, and it was working fine. The windows box also worked fine with the old hoary server. However, it does not get an IP address now. 

The output of /var/log/daemon.log has this to say:

```

Nov  1 03:18:59 localhost dhcpd: DHCPDISCOVER from 00:0f:1f:1b:43:f3 via eth0
Nov  1 03:19:00 localhost dhcpd: DHCPOFFER on 192.168.1.100 to 00:0f:1f:1b:43:f3 (whatever) via eth0
Nov  1 03:19:03 localhost dhcpd: DHCPDISCOVER from 00:0f:1f:1b:43:f3 via eth0
Nov  1 03:19:03 localhost dhcpd: DHCPOFFER on 192.168.1.99 to 00:0f:1f:1b:43:f3 (whatever) via eth0
Nov  1 03:19:11 localhost dhcpd: DHCPDISCOVER from 00:0f:1f:1b:43:f3 via eth0
Nov  1 03:19:12 localhost dhcpd: DHCPOFFER on 192.168.1.98 to 00:0f:1f:1b:43:f3 (whatever) via eth0

```

As can be seen, it is going down through it's list of available IP addresses and offering them to the machine (whatever), but they are not being accepted. It is also worth noting that the machine is not making a DHCPREQUEST. Once it has offered the 3rd address, the DHCP server starts going crazy writing /var/lib/dhcp3/dhcpd.leases (which can get quite large), all redundant data. At this point I have to stop dhcpd, delete the leases file, and restart it - after killing the dhcp request on the client machine.

My dhcpd.conf looks like this:

```

#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.4.2.2 2002/07/10 03:50:33 peloy Exp $
#

# option definitions common to all supported networks...

ddns-updates on;
ddns-update-style interim;
ddns-domainname "splinter.lan";

zone splinter.lan. {
        primary 192.168.1.1;
}
zone 1.168.192.in-addr.arpa. {
        primary 192.168.1.1;
}
#zone sifnt.lan. {
#       primary 192.168.0.1;
#}
#zone 0.168.192.in-addr.adpa. {
#       primary 192.168.0.1;
#}

option domain-name "splinter.lan";
option domain-name-servers 192.168.1.1;
#option domain-name-servers 192.168.0.1;
one-lease-per-client on;
option subnet-mask 255.255.255.0;
default-lease-time 43200;
max-lease-time 172800;
authorittive;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option netbios-name-servers 192.168.1.1, 192.168.0.1;

subnet 192.168.1.0 netmask 255.255.255.0 {
   range 192.168.1.20 192.168.1.100;
}

host kestrel {
  hardware ethernet 00:40:F4:71:03:BE;
  fixed-address 192.168.1.2;
}

host printer {
  hardware ethernet 00:80:77:35:74:5F;
  fixed-address 192.168.1.18;
}

```

I'm stumped. I don't know what is at fault, the windows box or the server, but I know that the only thing has changed is the server. Please help me fix this problem :)

krem.

---

### Post by godlike on 2005-10-31
This may be a stupid question but have ya tried using dnsmasq? It works great for me but i only have a smaller network...

---

### Post by Kremlin on 2005-10-31
No question is stupid :)

I haven't tried DNS masq, but because my server died I'm trying to get it all working perfectly as before.

I have no problems with DNS using bind (that much works - I just copied over my named.conf.local and my zone files and restarted bind). The problem is with DHCPD which doesn't appear to be leasing an IP address properly.

---

### Post by Kremlin on 2005-10-31
Well, this is stupid.

I apt-get remove dhcp3-server dhcp3-client --purge'd,
then reinstalled dhcp3-server.

Edited the dhcpd.conf by hand to re set up the information, and it works now. I hope this is the end of it, anyway. :)

---

### Post by dbee on 2005-10-31
I'm just gonna throw this out here  .... but the problem wouldn't have anything to do with the fact that authoritative was spelt wrong in dhcp.conf would it ?? :p

---

### Post by Kremlin on 2005-10-31
Naah, because it wasn't working when that line wasn't there, either (I added it as an afterthought when I compared the old and new conf files). DHCPD should work without the "authoritative" directive in place. 

I suppose it might be a factor ... but anyway, it's working now. :) I blame dhclient - because it was plugged into the network with the temporary dhcp server active when I was installing ubuntu, it decided that the server should have a dynamic IP address, so I had to edit /etc/networking/interfaces to make it static again.

---

### Post by LordHunter317 on 2005-10-31
[QUOTE=Kremlin]Naah, because it wasn't working when that line wasn't there, either (I added it as an afterthought when I compared the old and new conf files). DHCPD should work without the "authoritative" directive in place. [/quote]No, dhcpd3 will not work correctly without it.

---

