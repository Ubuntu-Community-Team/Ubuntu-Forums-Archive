---
title: "Problems with DHCP Server"
date: 2015-12-05
forum: Server Platforms
---

### Post by marciobacci on 2015-12-05
I have the follow problem with my DHCP Server

My Printers are unable to get IP dynamically. Windows and Linux stations are getting IP correctly. Thus, this problem only occurs with printers.

 I have installed DHCP (isc-dhcp-server) on Ubuntu Server 14.04.3 LTS.

Follow my dhcpd.conf

```

ddns-update-style none;

option domain-name "empresa.com.br";
option domain-name-servers 192.168.1.25, 192.168.1.10;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

subnet 192.168.1.0 netmask 255.255.252.0 {
}

subnet 192.168.1.0 netmask 255.255.255.128 {
  range 192.168.1.95 192.168.1.126;
  option routers 192.168.1.13;
  option broadcast-address 192.168.1.127;
}

subnet 192.168.1.128 netmask 255.255.255.128 {
  range 192.168.1.129 192.168.1.253;
  option routers 192.168.1.254;
  option broadcast-address 192.168.1.255;
}


subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.2 192.168.2.254;
  option routers 192.168.2.1;
  option broadcast-address 192.168.2.255;

  
    host CHEFE { 
        hardware ethernet 04:00:06:62:10:42;
        fixed-address 192.168.2.240;
     }


    #IMPRESSORAS

    host SEC30CDA76526C1 { 
        hardware ethernet BC:CD:A7:65:00:C1;
        fixed-address 192.168.2.41;
     } 

    #IMPRESSORA DP
    host RNP474CB6 { 
        hardware ethernet 00:26:73:47:4C:B6;
        fixed-address 10.133.85.15;
    }

}


subnet 192.168.3.0 netmask 255.255.255.0 {
  range 192.168.3.2 192.168.3.254;
  option routers 192.168.3.1;
  option broadcast-address 192.168.3.255;    

    host DKBB-PC { 
        hardware ethernet 00:F9:DD:3E:DB:83;
        fixed-address 192.168.3.32;
     } 


    host SECRETARIA { 
        hardware ethernet 00:A0:74:B6:DA:33;
        fixed-address 192.168.3.240;
     } 
    #IMPRESSORAS 
    host SAMSUNG-1 { 
        hardware ethernet 30:CD:A7:AD5:EE:BB;
        fixed-address 192.168.3.123;
     } 

    host RNP00D06B { 
        hardware ethernet 30:26:73:E0:D0:6B;
        fixed-address 192.168.3.230;
     } 
    
    
    host RNP48F5F1 { 
        hardware ethernet 30:26:73:48:e5:e1;
        fixed-address 192.168.3.247;
     } 
    
    
    host IMPRESSORA-SEC { 
        hardware ethernet 00:26:73:00:DD:A9;
        fixed-address 192.168.3.204;
     }

}    


subnet 192.168.40.0 netmask 255.255.255.128 {
  range 192.168.40.2 192.168.40.127;
  option routers 192.168.40.1;
  option broadcast-address 192.168.40.128;    
}

```

Regards,

Márcio

---

### Post by matt_symes on 2015-12-05
Thread moved to **Server Platforms**

You're more likely to get a response to your query in this forum.

I've added code tags for your first post. Please use them in future.

---

### Post by matt_symes on 2015-12-05
Hi

You may want to supply some more information if you want useful help.

What printers are they ? Make and model. Are they configured to acquire an IP address via DHCP ?

What IP addresses do you expect them to be assigned ? In which subnet ? Should they be assigned one of the DHCP static addresses ?

The more information you supply, the more likely you'll get useful help.

Kind regards

---

### Post by marciobacci on 2015-12-05
Hi, 

Apparently this is happening only with the Samsung brand printers. These printers were getting the IP correctly, but now are not more. They are configured to receive IP via DHCP. In the DHCP server configuration file the IP for these printers are reserved as below:

host SAMSUNG-IMP { 
        hardware ethernet 30:CD:A7:65:26:88;
        fixed-address 192.168.3.94;
     }
The computers are getting IP OK. I put a computer in the network point where was the printer and IP is delivered correctly for that computer.

Still, I set the printer time, because I thought that this could be causing the problem.

I have 5 subnets and in all this subnets have printers configured in DHCP mode.

Thanks,

Márcio

---

### Post by SeijiSensei on 2015-12-05
In general I would use static IP addresses for shared resources like printers and file servers.  Is it not possible to set the IP manually on the printer?

---

### Post by marciobacci on 2015-12-06
Hi SeijiSensei

Is possible, but I have 80 printers in my network, thus I would like to use DHCP mode. Before was working properly.

---

