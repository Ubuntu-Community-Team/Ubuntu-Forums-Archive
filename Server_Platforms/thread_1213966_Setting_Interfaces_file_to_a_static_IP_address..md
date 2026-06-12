---
title: "Setting Interfaces file to a static IP address."
date: 2009-07-15
forum: Server Platforms
---

### Post by UbuKunubi on 2009-07-15
Hello,

Im learning how to build my own simple web server.
So far I have assembled the hardware, installed 8.04 LTS server edition, and am currently trying to configure the /etc/network/interfaces file.

When, on the server, I type sudo ifconfig eth0 I get the following information:
DHCPDISCOVER on eth0 to 255.255.255.255
DHCPOFFER of 192.168.1.12
DHCPREQUEST of 192.168.1.12
DHCPACK of 192.168.1.12 from 192.168.1.1
bound to 192.168.1.12

But I'm unsure on which of these elements relates to the information needed in the interfaces file?
I've spent a lot of time and effort searching and reading via google, but I have yet to find a clear answer to my question.

Thanks in advance,
Ubu

---

### Post by spynappels on 2009-07-15
Hi Ubu,

Check towards the end of your last question, I answered the question there earlier today. As to which DNS servers to use, you could put your gateway as the first DNS server and use some free ones such as 4.2.2.1 through to 4.2.2.6. Pick any 2 from in this range, giving you 3 DNS entries in total and you should be good to go. Select an IP from the 192.168.1.x range where x is a number between 2 and 254, but not within the dhcp range. I would suggest a high number such as 220 as you dhcp scope seems to start fairly low, offering you 12 in the example above.
Netmask is 255.255.255.0 and gateway 192.168.1.1

Let me know how you got on.

---

### Post by UbuKunubi on 2009-07-15
spynappels,

Thank you for your patience.
I simply iterated the addresses I discovered via ifconfig and rebooted the system. I can now ping a site so is it safe to consider the current setup correct?

---

### Post by spynappels on 2009-07-16
Hi Ubu,

What IP address did you use for your static IP in the end?

---

### Post by IMadhavan on 2009-07-16
Hi 
I used the last Ip address is
192.168.0.253
You can you use the ip address up to 254

---

