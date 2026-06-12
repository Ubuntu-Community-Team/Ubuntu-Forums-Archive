---
title: "dhcp server configuration"
date: 2011-07-06
forum: Server Platforms
---

### Post by Rakeshvijayan on 2011-07-06
Hi friends I installed dhcp server and edit files sudo nano /etc/default/dhcp3-server


> # Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"

**/etc/dhcp3/dhcpd.conf**.

I got message after i restart the dhcpd service

---

### Post by Lars Noodén on 2011-07-06
You might also look at [dnsmasq](http://packages.ubuntu.com/natty/dnsmasq).  It is a lot easier to set up.

---

### Post by headvampyre@hotmail.co.uk on 2011-07-06
Keep this thread up, im currently at work so i cant post any config now, but stick with the isc-dhcp server :)

---

### Post by linuchsan on 2011-07-06
Try this:

```

ddns-update-style none;
subnet 192.168.1.0 netmask 255.255.255.0
{
    option broadcast-address    192.168.1.255;
    option domain-name  "mydomain.example";
    option domain-name-servers  192.168.1.1, 192.168.1.199;
    default-lease-time          600;
    max-lease-time              7200;
    option subnet-mask          255.255.255.0;
    range 192.168.1.10 192.168.1.100;
    range 192.168.1.150 192.168.1.200;
    option routers 192.168.1.254;
}

```

---

### Post by headvampyre@hotmail.co.uk on 2011-07-07
you wanna add:

authoritive;

before the subnet aswell :)

---

### Post by collisionystm on 2011-07-07
administrator@trash:~$ cat /etc/dhcp3/dhcpd.conf 
# DHCP server is authoritative for all networks
authoritative;

# extra options
# RFC3442 routes
option rfc3442-classless-static-routes code 121 = array of integer 8;
# MS routes
option ms-classless-static-routes code 249 = array of integer 8;

pid-file-name "/var/run/dhcp3-server/dhcpd.pid";

ddns-update-style none;

option domain-name-servers 127.0.0.1, 64.83.0.10;


default-lease-time 1800;
max-lease-time 7200;


shared-network eth0 {

	subnet 172.16.64.0 netmask 255.255.224.0 {
                
            option routers 172.16.64.1;
	        option domain-name "trash";
            option domain-name-servers 172.16.64.15, 8.8.8.8;
                option ntp-servers 172.16.64.15;
                option netbios-name-servers 172.16.64.15;
                option netbios-node-type 8;
                default-lease-time 1800;
                max-lease-time 7200;


            pool {
                

                

                range 172.16.69.100 172.16.69.200;
            }
        }

        group {
           
            option routers 172.16.64.1;
	        option domain-name "trash";
            option domain-name-servers 172.16.64.15, 8.8.8.8;
                option ntp-servers 172.16.64.15;
                option netbios-name-servers 172.16.64.15;
                option netbios-node-type 8;
                default-lease-time 1800;
                max-lease-time 7200;


        }




}


This is mine

> shared-network eth0

---

### Post by Rakeshvijayan on 2011-07-07
I think this error message that I got because I had installed ltsp service installed on with this server .after configur ltsp server file and set range on there and restart the dhcpd it give OK message .my thread not yet  I have doubt ...

---

### Post by headvampyre@hotmail.co.uk on 2011-07-08
LTSP changes the directory of the DHCPD config to /etc/ltsp , and are you wanting to run an LTSP server? The DHCP config will get a bit messy if you do.

---

### Post by Rakeshvijayan on 2011-07-11
yes  thats why I got that error message .I have a doubt in dhcp lease with mac address 

[how its work ] how can I set this settings ? I want secure my network by no one can't plug into my network with out my permission is it possible by this method


Thanks

---

### Post by Rakeshvijayan on 2011-07-11
I have a doubt in dhcp lease with mac address 

[how its work ] how can I set this settings ? I want secure my network  by no one can't plug into my network with out my permission is it  possible by this method

---

### Post by Rakeshvijayan on 2011-07-12
up

---

