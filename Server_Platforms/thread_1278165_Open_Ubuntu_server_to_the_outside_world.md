---
title: "Open Ubuntu server to the outside world"
date: 2009-09-29
forum: Server Platforms
---

### Post by virtuoosi on 2009-09-29
Hello,

I have an ubuntu server box, and I can access it from the local area network. I would like to SSH into it from the outside, but I am having some problems configuring the network.

This is my current setup:

WAN<---->TeleWell EA510 V2 (Modem/Router/Firewall/NAT/DHCP)<---->Buffalo WHR-HP-G54 (Wireless router)<---->My server which I would like to access.

The connection between the Buffalo and my server is wired, and my other computers are connected wirelessly to the Buffalo router. All of my computers @home can connect the server normally. 
 
The TeleWell modem has

[LIST]
[*]DHCP on, it has assigned an address (192.168.0.100) to the Buffalo router
[*]The port 22 forwarded to my servers internal IP (192.168.11.6). This IP is provided by the Buffalo.
[/LIST]

The Buffalo router has

[LIST]
[*]Also DHCP Function on (?). Does this mean it is handing out the internal IP addresses to the local computers?
[*]NAT: Address Translation is enabled. What does this mean?
[*]There is an entry on the NAT table:
[/LIST]
           AirStation&#8217;s WAN IP Address                             SSH (TCP Port:22) <-> 192.168.11.6       SSH (TCP Port:22)


All of my computers in the LAN have an static internal IP address (including the server box). 

My system responds to ping requests from the outside. This doesnt mean it is my server box responding, right? 

Both Buffalo & TeleWell got thousands of different settings and advanced settings pages in their configuration. NAT, DNS, DHCP, DMZ, Firewall, Port Mapping and the list goes on. I would be pleased if someone could explain what I should do, even in short terms. 

Should I forward the port 22 from the TeleWells settings to my Buffalo router's IP, and then forward it on to the server from the Buffalo?

Or should I connect the server to the TeleWell modem? I think it would be a bit more simple, because then I wouldn't have to configure the Buffalo's settings at all.

---

### Post by undecim on 2009-09-29
The TeleWell should have port 22 forwarded to the IP address of the Buffalo router. (unless, of course, the Buffalo router is configured to act solely as an access point, but that doesn't seem to be the case, because the TeleWell network starts 192.168.0, while the Buffalo network starts 192.168.11)

From the admin page of the Buffalo IP address (should be 192.168.11.1 when connected to the buffalo router) there should be a status tab/page that has a WAN IP address (or something of that nature... its different for every vendor) This should be something like 192.168.0.X; That is the IP address that the TeleWell should be forwarding to.

Also, if its possible, it would be much simpler to connect your server to the TeleWell router. Then you only have to set up one port forward.

EDIT: ahh... missed the part about the buffalo having IP address 192.168.0.100... That appears to be a DHCP assigned address, so if you keep your server connected to the buffalo router, you may want to assign a static IP to the buffalo router (by changing the settings on the buffalo) so that if your network ever gets reset, you won't have to reconfigure port forwarding.

Also, you should be able to configure your Buffalo to act solely as an access point, which will make your network much simpler. I think that all that needs to be done for this is turning off NAT? My router just has an option to turn it into an access point, so im not 100% sure on that... NAT (Network Address Translation) is what allows several IP addresses to act as a single IP address (for example, the IP address given to you by your ISP)

---

### Post by joebeasley on 2009-09-29
Do the port forwarding on the Telewell to your server connected to the buffalo router.

---

### Post by virtuoosi on 2009-09-29
I turned the Buffalo into an access point, lets see where this gets me.

EDIT1: Huge thanks, the port 22 seems open && forwarded properly now. I will truly test it tomorrow, by trying to access the server via SSH from school. 

It was simply a matter of turning the Buffalo into an access point instead of router mode. After I had done this, I realised that TeleWell was now handing out the IP addresses, and I just forwarded the port 22 to my server box via TeleWell settings.

Thanks undecim.

---

### Post by Iowan on 2009-09-29
I think I read it somewhere in the thread: If the DHCP server is capable, you may want to issue a static lease to your server - so it's IP address isn't a moving target.

---

### Post by brian mcgee on 2009-09-30
A note about security. If you forward port 22 to your computer, expect tons of brute-force attempts. You might consider changing the exposed port to something above 1024, like 22391. If your router supports it, you can use port translation so you don't have to make changes to the SSH config. Otherwise, tell SSH to listen on a different port by editing /etc/ssh/sshd_config

And changing the line "Port 22" to "Port 22391" or something similar, then restart SSH:

```
/etc/init.d/ssh restart
```Keep an eye on /var/log/auth.log and make sure you have good passwords.

---

### Post by virtuoosi on 2009-10-02
> **brian mcgee said:**
> A note about security. If you forward port 22 to your computer, expect tons of brute-force attempts. You might consider changing the exposed port to something above 1024, like 22391.

Yeah I knew about this stuff before I opened my server, so I have allready changed the port. :) Thanks for the note anyways. So far I've gotten zero login attempts.

---

