---
title: "ADSL Client"
date: 2010-04-14
forum: Server Platforms
---

### Post by expatCM on 2010-04-14
I have just set up (still in the process really)  a server and want to use DHCP on the server.  I have two nics, one for the lan and the other faces a Linksys ADSL router / modem.

When I turn off the integrated DHCP server in the Linksys I do not find the ISP's DNS on the nic connected to the Linksys.

So ...  I was wondering why not....

I have been using Webmin to configure this and I see that there is an ADSL Client module there.  Sadly I cannot read up about his since I cannot find any documentation.

Does anyone know what this module does?  I am just wondering if it could be used to access the ADSL account from the nic and so get the public DNS ...

---

### Post by dalitso on 2010-04-14
Do you want to run DHCP on the LAN or you want the NIC connected to the router to get an address through DHCP in the router?

---

### Post by terazen on 2010-04-14
I'd manually configure opendns ip addresses for dns and not even worry about using your isp's dns.  The opendns servers are faster and I've never actually known them to be down.

---

### Post by expatCM on 2010-04-14
dalitso - DHCP on the lan.  The router only to access the Internet and take the public DNS.  The router DHCP will be turned off per the settings ...

terazen - opendns or isp dns is one and the same.  The real challenge is how to configure when using an ADSL service ...

---

### Post by dalitso on 2010-04-14
You can still achieve this without turning off DHCP on your router.
Like in my setup, my ADSL subscription offers dynamic IP for my internet connection. 
The router's DHCP is still on but my server has static IP addresses on both NICs. My DHCP services are set on the server and LAN pcs get  IP addresses from the server and also get internet as the server is also set as a gateway.

---

### Post by expatCM on 2010-04-14
I understand what you say and will certainly consider this as the course of action.

I cannot help but wonder though two things - 

1.  What is the purpose of the ADSL Client module in Webmin.

2.  What is the reason why you would switch off the DHCP server in an integrated modem / router since this does not at first sight allow the unit to work as a modem ...

---

