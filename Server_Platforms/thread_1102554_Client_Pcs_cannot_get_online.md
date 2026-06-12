---
title: "Client Pcs cannot get online"
date: 2009-03-21
forum: Server Platforms
---

### Post by MikeyPooh on 2009-03-21
Hi Everyone,

I Have Setup Ubuntu Server 8.04 as a Router/Gateway/Fileserver

The Server is giving ip addresses to the client machines but the client machines cannot get online.

Anyone Have Any Ideas?;)

Thanks

Mike

---

### Post by Whiskerburn on 2009-03-21
It may be helpful if you post your dhcpd.cong file so we can look at it..

---

### Post by MikeyPooh on 2009-03-21
# extra options
# RFC3442 routes
option rfc3442-classless-static-routes code 121 = array of integer 8;
# MS routes
option ms-classless-static-routes code 249 = array of integer 8;

ddns-update-style none;

option domain-name-servers 63.64.9.12, 63.64.9.20;


default-lease-time 1800;
max-lease-time 7200;

---

### Post by Whiskerburn on 2009-03-21
Do you have the following in the file?

option routers

---

### Post by MikeyPooh on 2009-03-21
no cuz it gets its ip directly from the switch

---

### Post by MikeyPooh on 2009-03-21
ok i missed part of the dhcpd.conf file

Here it is 


# extra options
# RFC3442 routes
option rfc3442-classless-static-routes code 121 = array of integer 8;
# MS routes
option ms-classless-static-routes code 249 = array of integer 8;

ddns-update-style none;

option domain-name-servers 63.64.9.12, 63.64.9.20;


default-lease-time 1800;
max-lease-time 7200;




shared-network eth1 {

	option routers 192.168.1.1;
	option domain-name "wow-stargate.net";
	option domain-name-servers 63.64.9.12, 63.64.9.20;

        default-lease-time 1800;
        max-lease-time 7200;



	subnet 192.168.1.0 netmask 255.255.255.0 {
		range 192.168.1.100 192.168.1.150;
        }


}

Thanks

Mike

---

### Post by Whiskerburn on 2009-03-22
Looks like you have two lines feeding DNS info.  Try commenting out one or the other, the dual reporting my be messing the clients up. You have other dups that you may want to comment out as well.


# extra options
# RFC3442 routes
option rfc3442-classless-static-routes code 121 = array of integer 8;
# MS routes
option ms-classless-static-routes code 249 = array of integer 8;

ddns-update-style none;

**option domain-name-servers 63.64.9.12, 63.64.9.20;**


default-lease-time 1800;
max-lease-time 7200;




shared-network eth1 {

option routers 192.168.1.1;
option domain-name "wow-stargate.net";
[B]option domain-name-servers 63.64.9.12, 63.64.9.20;
[/B]
default-lease-time 1800;
max-lease-time 7200;



subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.100 192.168.1.150;
}


}

Thanks

---

### Post by MikeyPooh on 2009-03-23
well the server is assigning ip addresses, However when i boot the server i get this error

dnsmasq Failed To Create Listening Socket: address already in use


Any Ideas?

Thanks

Mike

---

### Post by Whiskerburn on 2009-03-24
Are you using dhcp3 for dhcp services or are you using dnsmasq?  The config file you posted looks like a dhcp3 file..  If thats the case you have 2 different dhcp server softwares attempting to grab the same port..

---

### Post by BkkBonanza on 2009-03-24
Yes, definitely port conflict. Post the output of "ps -afx".
You're going to need to disable one or the other. Maybe the other one has incorrect router values.

---

### Post by MikeyPooh on 2009-03-24
thats part of what is confusing me

i dont have a router

so what would the router values be;)

i thought i have to have dnsmasq and dhcp both running:o

Thanks

Mike

---

