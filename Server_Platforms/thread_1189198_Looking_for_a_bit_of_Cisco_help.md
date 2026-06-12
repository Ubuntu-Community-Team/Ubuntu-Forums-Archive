---
title: "Looking for a bit of Cisco help"
date: 2009-06-16
forum: Server Platforms
---

### Post by Lukas1 on 2009-06-16
I am trying to program my Cisco 831 series router to connect my Ubuntu dns server/web server to the internet. I can ping from inside the router terminal, but am unable to ping from the regular terminal and can't connect to the internet. I have attached my configuration file and an error message that I get when I do the "test connection" through SDM on my LAN ports. Thank you for your help.

---

### Post by wirelessmonkey on 2009-06-16
I'm not familiar with the 831, but don't you need to specify a default vlan, and place the FE port on that Vlan??

int FE0/1 
switchport access vlan 1

or somesuch?

---

### Post by rshprd on 2009-06-16
Not specifically versed on the 831.  However.... 

First, not sure if you put the xx.xx.150.146 literally or to hide your actual network in the example.  If not the latter, that would be a problem.

Also, you should not necessarily have to define a static route, espcially since you appear to be using the Cisco as DHCP.  It may be that your static route definition is conflicting with the default gateway assignment you have specific in the DHCP.  

I might be reading the config file incorrectly, but you seem to have DHCP saying the default gateway is the 10.0.1.6 address but your static route statement is saying that everything not on the internal network should go to xx.xx.150.146.





> **Lukas1 said:**
> I am trying to program my Cisco 831 series router to connect my Ubuntu dns server/web server to the internet. I can ping from inside the router terminal, but am unable to ping from the regular terminal and can't connect to the internet. I have attached my configuration file and an error message that I get when I do the "test connection" through SDM on my LAN ports. Thank you for your help.

---

### Post by Lukas1 on 2009-06-16
hahaha thanks, I blocked out the first two numbers. 

I don't know what vlans are, but nothing in my research thus far has mentioned anything about that. 



I want to use dhcp, but for network addresses ranging from 10.0.1.7-10.0.1.254
My ISP (T1 provider & VOIP) has a gateway IAD unit with an IP of 10.0.1.1
my DNS/webserver is at 10.0.1.2 and so I set my router at 10.0.1.6.
They also gave me a public IP address of xx.xx.150.146

I want my incoming requests to be forwarded on to my DNS/webserver. 

Which static statement are you referring to?

---

