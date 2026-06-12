---
title: "Network IDS/NMAP"
date: 2011-09-22
forum: Security
---

### Post by pcarlos853 on 2011-09-22
Hi,

I am running an Ubuntu 10.04 server in our offices. Its main purpose right now is as a Nagios3 server. I was wondering if it was possible to make Ubuntu scan all the devices on the network and send an email to me if there is a unauthorized device on the network. For example if someone cracks our wifi and gets on out network I would like to be notified so that I can take measures to secure the network.

Thanks!
Carlos

---

### Post by Beacon11 on 2011-09-22
What is an "authorized device?" Do you maintain a list of MAC addresses? If so, why not just add a MAC address whitelist to your router as added protection? Then the only way to get onto the network is to crack the wifi and clone an authorized MAC address, at which point your nifty nmap scan wouldn't catch them anyway. Why the extra work?

---

### Post by pcarlos853 on 2011-09-22
Beacon11,

If I had the router maintain a white-list of authorized mac addresses then the attacker would know that MAC address filtering is turned on when they cant access network resources, then the attacker would spoof his/her mac and they would be in. However if the attacker successfully connects to the network after cracking the wifi then they have no logical reason to change their mac address to a "authorized" one thus the ubuntu server running network IDS would alert me and I would disable the wifi.

Back to my original question. Is this possible? If so how?

Thanks,
Carlos

---

### Post by Dangertux on 2011-09-22
> **pcarlos853 said:**
> Beacon11,

If I had the router maintain a white-list of authorized mac addresses then the attacker would know that MAC address filtering is turned on when they cant access network resources, then the attacker would spoof his/her mac and they would be in. However if the attacker successfully connects to the network after cracking the wifi then they have no logical reason to change their mac address to a "authorized" one thus the ubuntu server running network IDS would alert me and I would disable the wifi.

Back to my original question. Is this possible? If so how?

Thanks,
Carlos

Short answer - yes. However the actual answer is much more complicated than that. 

Since you threw in the Wireless Access Point , might I suggest you ensure that the Wireless access point is secure. Meaning enterprise WPA etc, if it's not already that should be your top priority.

But let's get back to the original question, can your network devices alert you if someone inside your network (either via access to wifi or say a compromised workstation) is scanning. The answer is yes and no.

If the ONLY IDS you are running is on the Ubuntu machine, the Ubuntu  machine would have to have an interface sitting on a mirrored port, or  somewhere in the path of all the other network traffic. However, since  there are obviously multiple points of entry (WAP, The server itself,  and compromised workstations) if your network has any type of separation  to it you're going to have a lot of configuration ahead of you. Also,  if the server has any other purpose monitoring this much traffic would  bog it down quickly.

Alternatively if you are running SNMP on your devices you could utilize this as well however it would not likely be as reliable.

Now if you have a bunch of "dumb" hardware, networked printers etc this might get a little bit more complicated. So what you are actually probably looking for is a Network Access Control appliance. These don't come cheap, however they are highly configurable and do what you want.

In this particular case I would highly recommend a Sophos product, they sell very good ones, again they don't come cheap, but they are worth every penny if properly configured.

[http://www.sophos.com/en-us/products/endpoint/nac-advanced.aspx?utm_source=Non-campaign&utm_medium=AdWords&utm_campaign=NA-AW-NetworkSecurity](http://www.sophos.com/en-us/products/endpoint/nac-advanced.aspx?utm_source=Non-campaign&utm_medium=AdWords&utm_campaign=NA-AW-NetworkSecurity)

Also this link

[http://www.sophos.com/en-us/products/network.aspx](http://www.sophos.com/en-us/products/network.aspx)

So to sum it all up, I don't think you're going to be able to do what you want with the hardware on hand depending on what type of other systems are on the network.

EDIT : After reading your original post again. Yes you should just be able to do it with SNMP strings off of whatever Access Point or routing equipment is present. If you just want to know that a device is present. Now if you want to see what the device is doing you will probably want something more complicated.

---

