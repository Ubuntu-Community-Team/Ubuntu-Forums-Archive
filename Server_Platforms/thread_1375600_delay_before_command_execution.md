---
title: "delay before command execution"
date: 2010-01-08
forum: Server Platforms
---

### Post by kylegio on 2010-01-08
Problem started after installing a new firewall in my network. originally after installing the firewall there would be a 10 second delay after entering a command before it was processed, the command would be executed however there would be an error, i forget what it said, something about not being able to resolve my domain name (and it would give my domain name). i realized this was a problem with my NAT, so i configured DNS forwarding on my firewall so that any attempt to access my server using my domain name from inside the network would point back at my server.
   after setting up the DNS forwarding i no longer receive the error about my domain name being unreachable, however there is approximately a 30s delay between entering a command and its execution. 

the problem is hardly critical i do not see any more serious problems, it is just a pain to do any work when every time i try to do something i have to wait for it to execute. 

anyone have any suggestions?

thanks

---

### Post by HermanAB on 2010-01-08
Hmowdy, have a look at /etc/hosts and ensure that localhost and your domain name are defined in it.

---

### Post by BkkBonanza on 2010-01-08
Sounds like you still have a problem in how your DNS is resolving. Typically when you get long delays it's because of timeout periods before it re-tries a working DNS route. More details on your /etc/resolv.conf, dhcp, and nat settings may help solve that.

Edit: HermanAB is right. Fastest way to resolve a fixed name is to add it to /etc/hosts

---

### Post by kylegio on 2010-01-08
yes he was correct i added my domain name to 127.0.0.1and the problem was immediately solved.

as to the more information to help fix how my DNS is resolving
resolv.conf
```

domain mydomain.ca
search mydomain.ca
nameserver 192.168.1.1

```
where mydomain is my domain name.

my firewall is PfSense, the NAT is set to forward common ports (ssh, mail, http,etc), firewall rules are allowing incoming trafic on those ports, outgoing traffic is not restricted at this time.

as to my network connection  it is DHCP with a static lease from the firewall.


thank you very much for your timely help, any more information on the problem i was having would be welcomed.

---

### Post by BkkBonanza on 2010-01-08
Those are typical setting for resolve.conf. I don't have the search and domain lines in mine and I believe they aren't strictly required, though likely not a problem.

That nameserver line tells your machine to resolve using 192.168.1.1 - which presumably is your gateway/router. It's common for routers to run dnsmasq or similar software to handle both dhcp and dns caching. If you aren't restricting outbound traffic at all then I'd expect your DNS resolution isn't being hindered by the firewall or nat. 

So I would check on your router what DNS server it is configured to use because most likely your machine is forwarding DNS requests to your ISP provided server given to your router when it gets it's IP assignment. This may be fine if it works well but in my experience ISP provided DNS servers are sometimes wonky. I've had issues that I solved by telling my router to use another DNS server instead of the one my ISP provides. Also ISP provided servers sometimes do nasty filtering.

Good candidates for DNS not provided by your ISP that are worth trying are OpenDNS (at 208.67.222.222 or 208.67.220.220) and Google at (8.8.8.8 or 8.8.4.4). Adding settings for combinations of these is ok as well and gives more redundancy.

As an initial test you can try changing your /etc/resolv.conf so that the nameserver points to 8.8.8.8. If that makes a big difference in speed then it's worth looking at your router so that it uses one of the better servers. Doing it on your router will improve it for your whole LAN rather than just your system. But if you do change your router settings be sure to point your system back to the router again.

Hope this helps somewhat.

---

### Post by kylegio on 2010-01-08
thank you, i will try what you have said when i am back on my network. i know i have my router set up to use the dns servers provided by my isp, i believe however that i have configured it not to give those dns servers to clients on DHCP, i know i have done it both ways in the past, one way if you checked dns servers on any client connected using DHCP (lets say your in windows and you just checked "status" of a connection) it would say 192.168.1.1 as primary DNS , the other way if you checked it would give you the DNS servers provided by my isp. i will try telling my firewall to use a public DNS like the ones you have mentioned, i believe DynDNS provides dns servers i can use, which would probably be easiest because i use DynDNS nameservers/etc for my domain anyway.


thanks

EDIT:
i added the line 
nameserver 208.67.222.222  to my resolv.conf file before the nameserver 192.168.1.1, 
then ran the command "dnsdomainname"  before the addition of this nameserver it would take about 30 seconds then come up with my domain name, after the addition it would be near instantaneous. 

if i am going to add these DNS servers to my firewalls configuration should i remove the line "nameserver 208.67.222.22"  from my resolv.conf file, or put it after 192.168.1.1? i assume that the computer uses them in sequential order. my thoughts were that it would be a good idea to add one from OpenDNS or DynDns as well as one from google to my firewalls settings to provide redundancy by using separate servers, can i also add them (or multiple others) to my resolv.conf file after using my local 192.168.1.1 (which should use the opendns/google once these are entered into my firewall)?

i appreciate the help very much you have improved my understanding of how this works greatly

---

### Post by BkkBonanza on 2010-01-08
Mostly it doesn't matter much which way you decide to set resolv.conf as long as it has a clear path to some DNS server. Setting your router is a more hierarchical approach but going direct works too. It's only a problem when you tell it to use a server that isn't functioning correctly.

You can add up to 3 nameserver statements for redundancy. I'm not sure it works with multiple addresses on the same line. You can use "man resolv.conf" to read the manual for how that file works. It may clarify some things.

Anyway, glad I could help and it works better now.

---

