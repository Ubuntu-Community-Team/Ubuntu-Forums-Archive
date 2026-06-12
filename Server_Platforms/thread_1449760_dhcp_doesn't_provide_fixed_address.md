---
title: "dhcp doesn't provide fixed address"
date: 2010-04-08
forum: Server Platforms
---

### Post by newnik on 2010-04-08
Please, help solve the following trouble:
 
Ubuntu LTS 8.04 + DHCP. Works fine except for fixed addresses. I mean all devices which need to get fixed IP according to their MACs don't get them and keep to receive random IPs from the range (almost everytime all machines receive the same IP they got from DHCP for the first time).
 
ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;
log-facility local7;
subnet 10.0.0.0 netmask 255.255.255.0 {
authoritative;
default-lease-time 259200;
max-lease-time 259200;
option netbios-name-servers 10.0.0.2;
option domain-name-servers 10.0.0.2;
option broadcast-address 10.0.0.255;
option subnet-mask 255.255.255.0;
option routers 10.0.0.1;
range 10.0.0.100 10.0.0.199;
 
# myacer
host acer {
hardware ethernet 00:16:D3:E0:89:46;
fixed-address 10.0.0.196;
}
}
 
Thank you very much in advance

---

### Post by stefangr1 on 2010-04-08
You have to specify options for specific hosts outside the section with the general options for the subnet.

So:

subnet {
}

host {
}

---

### Post by newnik on 2010-04-08
Thanks, but didn't help. I've just carry the host description out of the subnet description. And got the following :
 
Just before now (and now I have static .61) I had automatically get .140. After again configuring getting IP automatically I got again .140 :(
 
Of course I've restarted DHCP on the server
 
And by the way that configuration file was formed by Webmin tool.

---

